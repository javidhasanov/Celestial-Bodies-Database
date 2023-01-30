# Celestial-Bodies-Database

--
-- PostgreSQL database dump
--

-- Dumped from database version 12.9 (Ubuntu 12.9-2.pgdg20.04+1)
-- Dumped by pg_dump version 12.9 (Ubuntu 12.9-2.pgdg20.04+1)

SET statement_timeout = 0;
SET lock_timeout = 0;
SET idle_in_transaction_session_timeout = 0;
SET client_encoding = 'UTF8';
SET standard_conforming_strings = on;
SELECT pg_catalog.set_config('search_path', '', false);
SET check_function_bodies = false;
SET xmloption = content;
SET client_min_messages = warning;
SET row_security = off;

DROP DATABASE universe;
--
-- Name: universe; Type: DATABASE; Schema: -; Owner: freecodecamp
--

CREATE DATABASE universe WITH TEMPLATE = template0 ENCODING = 'UTF8' LC_COLLATE = 'C.UTF-8' LC_CTYPE = 'C.UTF-8';


ALTER DATABASE universe OWNER TO freecodecamp;

\connect universe

SET statement_timeout = 0;
SET lock_timeout = 0;
SET idle_in_transaction_session_timeout = 0;
SET client_encoding = 'UTF8';
SET standard_conforming_strings = on;
SELECT pg_catalog.set_config('search_path', '', false);
SET check_function_bodies = false;
SET xmloption = content;
SET client_min_messages = warning;
SET row_security = off;

SET default_tablespace = '';

SET default_table_access_method = heap;

--
-- Name: galaxy; Type: TABLE; Schema: public; Owner: freecodecamp
--

CREATE TABLE public.galaxy (
    name character varying(40) NOT NULL,
    galaxy_id integer NOT NULL,
    star_name character varying(40),
    ageinbilyears numeric(12,10),
    areainbilkm numeric(15,10),
    canbeobserved boolean NOT NULL
);


ALTER TABLE public.galaxy OWNER TO freecodecamp;

--
-- Name: galaxy_galaxy_id_seq; Type: SEQUENCE; Schema: public; Owner: freecodecamp
--

CREATE SEQUENCE public.galaxy_galaxy_id_seq
    AS integer
    START WITH 1
    INCREMENT BY 1
    NO MINVALUE
    NO MAXVALUE
    CACHE 1;


ALTER TABLE public.galaxy_galaxy_id_seq OWNER TO freecodecamp;

--
-- Name: galaxy_galaxy_id_seq; Type: SEQUENCE OWNED BY; Schema: public; Owner: freecodecamp
--

ALTER SEQUENCE public.galaxy_galaxy_id_seq OWNED BY public.galaxy.galaxy_id;


--
-- Name: moon; Type: TABLE; Schema: public; Owner: freecodecamp
--

CREATE TABLE public.moon (
    name character varying(40) NOT NULL,
    moon_id integer NOT NULL,
    ageinbilyears integer,
    areainbilkm numeric(15,0),
    description text,
    planet_id integer,
    has_life boolean
);


ALTER TABLE public.moon OWNER TO freecodecamp;

--
-- Name: moon_moon_id_seq; Type: SEQUENCE; Schema: public; Owner: freecodecamp
--

CREATE SEQUENCE public.moon_moon_id_seq
    AS integer
    START WITH 1
    INCREMENT BY 1
    NO MINVALUE
    NO MAXVALUE
    CACHE 1;


ALTER TABLE public.moon_moon_id_seq OWNER TO freecodecamp;

--
-- Name: moon_moon_id_seq; Type: SEQUENCE OWNED BY; Schema: public; Owner: freecodecamp
--

ALTER SEQUENCE public.moon_moon_id_seq OWNED BY public.moon.moon_id;


--
-- Name: planet; Type: TABLE; Schema: public; Owner: freecodecamp
--

CREATE TABLE public.planet (
    name character varying(40) NOT NULL,
    planet_id integer NOT NULL,
    ageinbilyears integer,
    radiusinkm numeric(15,0),
    description text,
    star_id integer,
    has_life boolean
);


ALTER TABLE public.planet OWNER TO freecodecamp;

--
-- Name: planet_planet_id_seq; Type: SEQUENCE; Schema: public; Owner: freecodecamp
--

CREATE SEQUENCE public.planet_planet_id_seq
    AS integer
    START WITH 1
    INCREMENT BY 1
    NO MINVALUE
    NO MAXVALUE
    CACHE 1;


ALTER TABLE public.planet_planet_id_seq OWNER TO freecodecamp;

--
-- Name: planet_planet_id_seq; Type: SEQUENCE OWNED BY; Schema: public; Owner: freecodecamp
--

ALTER SEQUENCE public.planet_planet_id_seq OWNED BY public.planet.planet_id;


--
-- Name: satellite; Type: TABLE; Schema: public; Owner: freecodecamp
--

CREATE TABLE public.satellite (
    satellite_id integer NOT NULL,
    name character varying(20) NOT NULL,
    stillactive boolean
);


ALTER TABLE public.satellite OWNER TO freecodecamp;

--
-- Name: satellite_satellite_id_seq; Type: SEQUENCE; Schema: public; Owner: freecodecamp
--

CREATE SEQUENCE public.satellite_satellite_id_seq
    AS integer
    START WITH 1
    INCREMENT BY 1
    NO MINVALUE
    NO MAXVALUE
    CACHE 1;


ALTER TABLE public.satellite_satellite_id_seq OWNER TO freecodecamp;

--
-- Name: satellite_satellite_id_seq; Type: SEQUENCE OWNED BY; Schema: public; Owner: freecodecamp
--

ALTER SEQUENCE public.satellite_satellite_id_seq OWNED BY public.satellite.satellite_id;


--
-- Name: star; Type: TABLE; Schema: public; Owner: freecodecamp
--

CREATE TABLE public.star (
    name character varying(40) NOT NULL,
    star_id integer NOT NULL,
    ageinbilyears integer,
    dminkm numeric(15,0),
    description text,
    galaxy_id integer
);


ALTER TABLE public.star OWNER TO freecodecamp;

--
-- Name: star_star_id_seq; Type: SEQUENCE; Schema: public; Owner: freecodecamp
--

CREATE SEQUENCE public.star_star_id_seq
    AS integer
    START WITH 1
    INCREMENT BY 1
    NO MINVALUE
    NO MAXVALUE
    CACHE 1;


ALTER TABLE public.star_star_id_seq OWNER TO freecodecamp;

--
-- Name: star_star_id_seq; Type: SEQUENCE OWNED BY; Schema: public; Owner: freecodecamp
--

ALTER SEQUENCE public.star_star_id_seq OWNED BY public.star.star_id;


--
-- Name: galaxy galaxy_id; Type: DEFAULT; Schema: public; Owner: freecodecamp
--

ALTER TABLE ONLY public.galaxy ALTER COLUMN galaxy_id SET DEFAULT nextval('public.galaxy_galaxy_id_seq'::regclass);


--
-- Name: moon moon_id; Type: DEFAULT; Schema: public; Owner: freecodecamp
--

ALTER TABLE ONLY public.moon ALTER COLUMN moon_id SET DEFAULT nextval('public.moon_moon_id_seq'::regclass);


--
-- Name: planet planet_id; Type: DEFAULT; Schema: public; Owner: freecodecamp
--

ALTER TABLE ONLY public.planet ALTER COLUMN planet_id SET DEFAULT nextval('public.planet_planet_id_seq'::regclass);


--
-- Name: satellite satellite_id; Type: DEFAULT; Schema: public; Owner: freecodecamp
--

ALTER TABLE ONLY public.satellite ALTER COLUMN satellite_id SET DEFAULT nextval('public.satellite_satellite_id_seq'::regclass);


--
-- Name: star star_id; Type: DEFAULT; Schema: public; Owner: freecodecamp
--

ALTER TABLE ONLY public.star ALTER COLUMN star_id SET DEFAULT nextval('public.star_star_id_seq'::regclass);


--
-- Data for Name: galaxy; Type: TABLE DATA; Schema: public; Owner: freecodecamp
--

INSERT INTO public.galaxy VALUES ('Milky Way', 1, NULL, 5.1234450000, 146.2343430000, true);
INSERT INTO public.galaxy VALUES ('Andromeda', 2, NULL, 2.1234500000, 126.2343430000, true);
INSERT INTO public.galaxy VALUES ('Black Eye', 3, NULL, 11.1234500000, 526.2343430000, true);
INSERT INTO public.galaxy VALUES ('Butterfly', 4, NULL, 7.1234500000, 56.2343430000, true);
INSERT INTO public.galaxy VALUES ('Comet', 5, NULL, 3.1234500000, 156.2343430000, true);
INSERT INTO public.galaxy VALUES ('Sunflower', 6, NULL, 7.1234500000, 86.2343430000, true);


--
-- Data for Name: moon; Type: TABLE DATA; Schema: public; Owner: freecodecamp
--

INSERT INTO public.moon VALUES ('Moon', 1, 2342342, 12314, NULL, 1, true);
INSERT INTO public.moon VALUES ('Phobos', 2, 2342342, 12314, NULL, 4, true);
INSERT INTO public.moon VALUES ('Deimos', 3, 2342342, 12314, NULL, 4, false);
INSERT INTO public.moon VALUES ('Lol', 4, 2342342, 12314, NULL, 5, false);
INSERT INTO public.moon VALUES ('Europe', 5, 2342342, 12314, NULL, 5, false);
INSERT INTO public.moon VALUES ('Asia', 6, 2342342, 12314, NULL, 5, false);
INSERT INTO public.moon VALUES ('Bigboy', 7, 2342342, 12314, NULL, 5, false);
INSERT INTO public.moon VALUES ('FarBigboy', 8, 2342342, 12314, NULL, 5, false);
INSERT INTO public.moon VALUES ('CloseBigboy', 9, 2342342, 12314, NULL, 3, false);
INSERT INTO public.moon VALUES ('WhiteMountain', 10, 2342342, 12314, NULL, 3, false);
INSERT INTO public.moon VALUES ('SandMountain', 11, 2342342, 12314, NULL, 3, false);
INSERT INTO public.moon VALUES ('JustMountain', 12, 2342342, 12314, NULL, 3, false);
INSERT INTO public.moon VALUES ('Mountain', 13, 2342342, 12314, NULL, 3, false);
INSERT INTO public.moon VALUES ('Neverreach', 14, 2342342, 12314, NULL, 4, false);
INSERT INTO public.moon VALUES ('Maybe', 15, 2342342, 12314, NULL, 4, false);
INSERT INTO public.moon VALUES ('NotNow', 16, 2342342, 12314, NULL, 4, false);
INSERT INTO public.moon VALUES ('Goal', 17, 2342342, 12314, NULL, 4, false);
INSERT INTO public.moon VALUES ('Silkpath', 18, 2342342, 12314, NULL, 4, false);
INSERT INTO public.moon VALUES ('Whitepath', 19, 2342342, 12314, NULL, 1, false);
INSERT INTO public.moon VALUES ('Theend', 20, 2342342, 12314, NULL, 1, false);


--
-- Data for Name: planet; Type: TABLE DATA; Schema: public; Owner: freecodecamp
--

INSERT INTO public.planet VALUES ('Earth', 1, 5000, 80000, 'My planet', 1, true);
INSERT INTO public.planet VALUES ('Mercury', 2, 55000, 80000, 'Neighbor', 1, true);
INSERT INTO public.planet VALUES ('Venus', 3, 55000, 80000, 'Neighbor', 1, true);
INSERT INTO public.planet VALUES ('Neptun', 4, 155000, 80000, 'FarNeighbor', 1, true);
INSERT INTO public.planet VALUES ('Mars', 6, 155000, 80000, 'Hot', 2, true);
INSERT INTO public.planet VALUES ('Jupiter', 5, 155000, 80000, 'Hot', 2, true);
INSERT INTO public.planet VALUES ('Jupiter2', 7, 155000, 80000, 'Hot', 2, true);
INSERT INTO public.planet VALUES ('Pluton', 8, 1355000, 80000, 'Cold', 3, true);
INSERT INTO public.planet VALUES ('Pluton2', 9, 1355000, 80000, 'Cold', 3, true);
INSERT INTO public.planet VALUES ('Pluton3', 10, 1355000, 80000, 'Cold', 3, true);
INSERT INTO public.planet VALUES ('NoPlanet', 11, 13000, 80000, 'Cold', 3, true);
INSERT INTO public.planet VALUES ('NnoPlanet', 12, 13000, 80000, 'Cold', 3, true);


--
-- Data for Name: satellite; Type: TABLE DATA; Schema: public; Owner: freecodecamp
--

INSERT INTO public.satellite VALUES (1, 'StarLink', true);
INSERT INTO public.satellite VALUES (2, 'Eye', true);
INSERT INTO public.satellite VALUES (3, 'Old', true);


--
-- Data for Name: star; Type: TABLE DATA; Schema: public; Owner: freecodecamp
--

INSERT INTO public.star VALUES ('Sun', 1, 522000, 115222, 'Bloody Hot', 1);
INSERT INTO public.star VALUES ('Sun2', 2, 5232000, 115222, 'Bloody Hot', 2);
INSERT INTO public.star VALUES ('TwiceSun', 3, 5232000, 1115222, 'Bloody Hot', 2);
INSERT INTO public.star VALUES ('TrippleSun', 4, 5232000, 1115222, 'Bloody bloody Hot', 2);
INSERT INTO public.star VALUES ('QuadrapleSun', 5, 5232000, 1115222, 'Bloody bloody Hot', 2);
INSERT INTO public.star VALUES ('QuadrapleSun2', 6, 5232000, 1115222, 'Bloody bloody Hot', 3);


--
-- Name: galaxy_galaxy_id_seq; Type: SEQUENCE SET; Schema: public; Owner: freecodecamp
--

SELECT pg_catalog.setval('public.galaxy_galaxy_id_seq', 1, false);


--
-- Name: moon_moon_id_seq; Type: SEQUENCE SET; Schema: public; Owner: freecodecamp
--

SELECT pg_catalog.setval('public.moon_moon_id_seq', 1, false);


--
-- Name: planet_planet_id_seq; Type: SEQUENCE SET; Schema: public; Owner: freecodecamp
--

SELECT pg_catalog.setval('public.planet_planet_id_seq', 1, false);


--
-- Name: satellite_satellite_id_seq; Type: SEQUENCE SET; Schema: public; Owner: freecodecamp
--

SELECT pg_catalog.setval('public.satellite_satellite_id_seq', 1, false);


--
-- Name: star_star_id_seq; Type: SEQUENCE SET; Schema: public; Owner: freecodecamp
--

SELECT pg_catalog.setval('public.star_star_id_seq', 1, false);


--
-- Name: galaxy galaxy_id_pk; Type: CONSTRAINT; Schema: public; Owner: freecodecamp
--

ALTER TABLE ONLY public.galaxy
    ADD CONSTRAINT galaxy_id_pk PRIMARY KEY (galaxy_id);


--
-- Name: galaxy galaxy_name; Type: CONSTRAINT; Schema: public; Owner: freecodecamp
--

ALTER TABLE ONLY public.galaxy
    ADD CONSTRAINT galaxy_name UNIQUE (name);


--
-- Name: moon moon_id_pk; Type: CONSTRAINT; Schema: public; Owner: freecodecamp
--

ALTER TABLE ONLY public.moon
    ADD CONSTRAINT moon_id_pk PRIMARY KEY (moon_id);


--
-- Name: moon moon_name; Type: CONSTRAINT; Schema: public; Owner: freecodecamp
--

ALTER TABLE ONLY public.moon
    ADD CONSTRAINT moon_name UNIQUE (name);


--
-- Name: satellite namee; Type: CONSTRAINT; Schema: public; Owner: freecodecamp
--

ALTER TABLE ONLY public.satellite
    ADD CONSTRAINT namee UNIQUE (name);


--
-- Name: planet planet_id_pk; Type: CONSTRAINT; Schema: public; Owner: freecodecamp
--

ALTER TABLE ONLY public.planet
    ADD CONSTRAINT planet_id_pk PRIMARY KEY (planet_id);


--
-- Name: planet planet_name; Type: CONSTRAINT; Schema: public; Owner: freecodecamp
--

ALTER TABLE ONLY public.planet
    ADD CONSTRAINT planet_name UNIQUE (name);


--
-- Name: satellite satellite_idd; Type: CONSTRAINT; Schema: public; Owner: freecodecamp
--

ALTER TABLE ONLY public.satellite
    ADD CONSTRAINT satellite_idd UNIQUE (satellite_id);


--
-- Name: satellite satellite_iid; Type: CONSTRAINT; Schema: public; Owner: freecodecamp
--

ALTER TABLE ONLY public.satellite
    ADD CONSTRAINT satellite_iid PRIMARY KEY (satellite_id);


--
-- Name: star star_id_pk; Type: CONSTRAINT; Schema: public; Owner: freecodecamp
--

ALTER TABLE ONLY public.star
    ADD CONSTRAINT star_id_pk PRIMARY KEY (star_id);


--
-- Name: star star_name; Type: CONSTRAINT; Schema: public; Owner: freecodecamp
--

ALTER TABLE ONLY public.star
    ADD CONSTRAINT star_name UNIQUE (name);


--
-- Name: moon moon_planet_id; Type: FK CONSTRAINT; Schema: public; Owner: freecodecamp
--

ALTER TABLE ONLY public.moon
    ADD CONSTRAINT moon_planet_id FOREIGN KEY (planet_id) REFERENCES public.planet(planet_id);


--
-- Name: planet planet_star_id; Type: FK CONSTRAINT; Schema: public; Owner: freecodecamp
--

ALTER TABLE ONLY public.planet
    ADD CONSTRAINT planet_star_id FOREIGN KEY (star_id) REFERENCES public.star(star_id);


--
-- Name: star stargalaxy__id; Type: FK CONSTRAINT; Schema: public; Owner: freecodecamp
--

ALTER TABLE ONLY public.star
    ADD CONSTRAINT stargalaxy__id FOREIGN KEY (galaxy_id) REFERENCES public.galaxy(galaxy_id);


--
-- PostgreSQL database dump complete
--


