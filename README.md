Лабораторна робота № 1.

Ознайомлення з базовими операціями СУБД PostgreSQL

КП-71 Перегуда Ярослав Іванович

Варіант(14): Книгарня

Сутності:

1)Автор

CREATE TABLE public."Authors"
(
    "AuthorID" integer NOT NULL DEFAULT nextval('"Authors_AuthorID_seq"'::regclass),
    "Name" text COLLATE pg_catalog."default" NOT NULL,
    "CompletedBooks" text COLLATE pg_catalog."default" NOT NULL,
    "Biography" text COLLATE pg_catalog."default" NOT NULL,
    CONSTRAINT "AuthorIDPK" PRIMARY KEY ("AuthorID")
)

2)Книга

CREATE TABLE public."Books"
(
    "BookID" integer NOT NULL DEFAULT nextval('"Book_BookID_seq"'::regclass),
    "BookAuthor" integer NOT NULL,
    "Name" text COLLATE pg_catalog."default" NOT NULL,
    "Genre" text COLLATE pg_catalog."default" NOT NULL,
    "Year" text COLLATE pg_catalog."default" NOT NULL,
    CONSTRAINT "BookIDPK" PRIMARY KEY ("BookID"),
    CONSTRAINT "BookAuthorFK" FOREIGN KEY ("BookAuthor")
        REFERENCES public."Authors" ("AuthorID") MATCH FULL
        ON UPDATE CASCADE
        ON DELETE CASCADE
)

3)Читач

CREATE TABLE public."Readers"
(
    "ReaderID" integer NOT NULL DEFAULT nextval('"Readers_ReaderID_seq"'::regclass),
    "Name" text COLLATE pg_catalog."default" NOT NULL,
    "AlreadyRead" text[] COLLATE pg_catalog."default",
    "ReadingNow" text[] COLLATE pg_catalog."default",
    "PhoneNumber" text COLLATE pg_catalog."default",
    "Adress" text COLLATE pg_catalog."default",
    CONSTRAINT "ReaderIDPK" PRIMARY KEY ("ReaderID")
)
