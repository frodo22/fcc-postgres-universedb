# fcc-postgres-universedb
a database for universe project
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
    galaxy_id integer NOT NULL,
    name character varying(30) NOT NULL,
    magnitude numeric(3,2),
    has_black_holes boolean,
    number_stars integer,
    galaxy_type character varying(30) NOT NULL,
    distance_to_earth integer,
    type_galaxy character varying(20),
    description text
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
    moon_id integer NOT NULL,
    planet_id integer,
    diameter_km integer,
    mass_kg integer,
    distance_to_earth integer,
    description text,
    name character varying(30) NOT NULL
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
-- Name: oddity; Type: TABLE; Schema: public; Owner: freecodecamp
--

CREATE TABLE public.oddity (
    oddity_id integer NOT NULL,
    name character varying(30) NOT NULL,
    diameter_km integer,
    mass_kg integer,
    has_black_matter boolean,
    type_oddity character varying(20),
    description text
);


ALTER TABLE public.oddity OWNER TO freecodecamp;

--
-- Name: oddity_oddity_id_seq; Type: SEQUENCE; Schema: public; Owner: freecodecamp
--

CREATE SEQUENCE public.oddity_oddity_id_seq
    AS integer
    START WITH 1
    INCREMENT BY 1
    NO MINVALUE
    NO MAXVALUE
    CACHE 1;


ALTER TABLE public.oddity_oddity_id_seq OWNER TO freecodecamp;

--
-- Name: oddity_oddity_id_seq; Type: SEQUENCE OWNED BY; Schema: public; Owner: freecodecamp
--

ALTER SEQUENCE public.oddity_oddity_id_seq OWNED BY public.oddity.oddity_id;


--
-- Name: planet; Type: TABLE; Schema: public; Owner: freecodecamp
--

CREATE TABLE public.planet (
    planet_id integer NOT NULL,
    star_id integer,
    name character varying(30) NOT NULL,
    diameter_km integer,
    mass_kg integer,
    number_moons integer,
    planet_type character varying(30) NOT NULL,
    distance_to_earth integer,
    planet_age integer,
    description text
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
-- Name: star; Type: TABLE; Schema: public; Owner: freecodecamp
--

CREATE TABLE public.star (
    star_id integer NOT NULL,
    galaxy_id integer,
    name character varying(30) NOT NULL,
    color character varying(20),
    number_planets integer,
    star_type character varying(30) NOT NULL,
    distance_to_earth integer,
    star_age integer,
    description text
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
-- Name: oddity oddity_id; Type: DEFAULT; Schema: public; Owner: freecodecamp
--

ALTER TABLE ONLY public.oddity ALTER COLUMN oddity_id SET DEFAULT nextval('public.oddity_oddity_id_seq'::regclass);


--
-- Name: planet planet_id; Type: DEFAULT; Schema: public; Owner: freecodecamp
--

ALTER TABLE ONLY public.planet ALTER COLUMN planet_id SET DEFAULT nextval('public.planet_planet_id_seq'::regclass);


--
-- Name: star star_id; Type: DEFAULT; Schema: public; Owner: freecodecamp
--

ALTER TABLE ONLY public.star ALTER COLUMN star_id SET DEFAULT nextval('public.star_star_id_seq'::regclass);


--
-- Data for Name: galaxy; Type: TABLE DATA; Schema: public; Owner: freecodecamp
--

INSERT INTO public.galaxy VALUES (1, 'Milky Way', NULL, NULL, NULL, 'elliptical', NULL, NULL, NULL);
INSERT INTO public.galaxy VALUES (2, 'Andromeda', NULL, NULL, NULL, 'elliptical', NULL, NULL, NULL);
INSERT INTO public.galaxy VALUES (3, 'Centaurus A', NULL, NULL, NULL, 'spiral', NULL, NULL, NULL);
INSERT INTO public.galaxy VALUES (4, 'Sculptors Galaxy', NULL, NULL, NULL, 'spiral', NULL, NULL, NULL);
INSERT INTO public.galaxy VALUES (5, 'Triangulum Galaxy', NULL, NULL, NULL, 'spiral', NULL, NULL, NULL);
INSERT INTO public.galaxy VALUES (6, 'Bodes Galaxy', NULL, NULL, NULL, 'irregular', NULL, NULL, NULL);


--
-- Data for Name: moon; Type: TABLE DATA; Schema: public; Owner: freecodecamp
--

INSERT INTO public.moon VALUES (1, 3, NULL, NULL, NULL, NULL, 'Moon');
INSERT INTO public.moon VALUES (2, 4, NULL, NULL, NULL, NULL, 'Deimos');
INSERT INTO public.moon VALUES (3, 4, NULL, NULL, NULL, NULL, 'Phobos');
INSERT INTO public.moon VALUES (4, 5, NULL, NULL, NULL, NULL, 'Ganymede');
INSERT INTO public.moon VALUES (5, 5, NULL, NULL, NULL, NULL, 'Io');
INSERT INTO public.moon VALUES (6, 5, NULL, NULL, NULL, NULL, 'Callisto');
INSERT INTO public.moon VALUES (7, 5, NULL, NULL, NULL, NULL, 'Europa');
INSERT INTO public.moon VALUES (8, 6, NULL, NULL, NULL, NULL, 'Pan');
INSERT INTO public.moon VALUES (9, 6, NULL, NULL, NULL, NULL, 'Thetys');
INSERT INTO public.moon VALUES (10, 6, NULL, NULL, NULL, NULL, 'Titan');
INSERT INTO public.moon VALUES (11, 6, NULL, NULL, NULL, NULL, 'Phoebe');
INSERT INTO public.moon VALUES (12, 6, NULL, NULL, NULL, NULL, 'Iapetus');
INSERT INTO public.moon VALUES (13, 7, NULL, NULL, NULL, NULL, 'Miranda');
INSERT INTO public.moon VALUES (14, 7, NULL, NULL, NULL, NULL, 'Ariel');
INSERT INTO public.moon VALUES (15, 7, NULL, NULL, NULL, NULL, 'Titania');
INSERT INTO public.moon VALUES (16, 7, NULL, NULL, NULL, NULL, 'Oberon');
INSERT INTO public.moon VALUES (17, 8, NULL, NULL, NULL, NULL, 'Cycloid');
INSERT INTO public.moon VALUES (18, 8, NULL, NULL, NULL, NULL, 'Mermaid');
INSERT INTO public.moon VALUES (19, 8, NULL, NULL, NULL, NULL, 'Triton');
INSERT INTO public.moon VALUES (20, 9, NULL, NULL, NULL, NULL, 'Plutito');


--
-- Data for Name: oddity; Type: TABLE DATA; Schema: public; Owner: freecodecamp
--

INSERT INTO public.oddity VALUES (1, 'SGR 0525-66', NULL, NULL, NULL, 'magnetar', NULL);
INSERT INTO public.oddity VALUES (2, 'LGM-1', NULL, NULL, NULL, 'neutron star', NULL);
INSERT INTO public.oddity VALUES (3, 'Sgr A*', NULL, NULL, NULL, 'black hole', NULL);


--
-- Data for Name: planet; Type: TABLE DATA; Schema: public; Owner: freecodecamp
--

INSERT INTO public.planet VALUES (1, NULL, 'Mercury', NULL, NULL, NULL, 'solid', NULL, NULL, NULL);
INSERT INTO public.planet VALUES (2, NULL, 'Venus', NULL, NULL, NULL, 'solid', NULL, NULL, NULL);
INSERT INTO public.planet VALUES (3, NULL, 'Earth', NULL, NULL, NULL, 'solid', NULL, NULL, NULL);
INSERT INTO public.planet VALUES (4, NULL, 'Mars', NULL, NULL, NULL, 'solid', NULL, NULL, NULL);
INSERT INTO public.planet VALUES (5, NULL, 'Jupiter', NULL, NULL, NULL, 'gas', NULL, NULL, NULL);
INSERT INTO public.planet VALUES (6, NULL, 'Saturn', NULL, NULL, NULL, 'gas', NULL, NULL, NULL);
INSERT INTO public.planet VALUES (7, NULL, 'Uranus', NULL, NULL, NULL, 'ice', NULL, NULL, NULL);
INSERT INTO public.planet VALUES (8, NULL, 'Neptune', NULL, NULL, NULL, 'ice', NULL, NULL, NULL);
INSERT INTO public.planet VALUES (9, NULL, 'Pluto', NULL, NULL, NULL, 'dwarf', NULL, NULL, NULL);
INSERT INTO public.planet VALUES (10, NULL, 'Ceres', NULL, NULL, NULL, 'dwarf', NULL, NULL, NULL);
INSERT INTO public.planet VALUES (11, NULL, 'Vesta', NULL, NULL, NULL, 'dwarf', NULL, NULL, NULL);
INSERT INTO public.planet VALUES (12, NULL, 'Pallas', NULL, NULL, NULL, 'dwarf', NULL, NULL, NULL);


--
-- Data for Name: star; Type: TABLE DATA; Schema: public; Owner: freecodecamp
--

INSERT INTO public.star VALUES (1, NULL, 'Sun', NULL, NULL, 'solar_type', NULL, NULL, NULL);
INSERT INTO public.star VALUES (2, NULL, 'Orion', NULL, NULL, 'Hot Blue', NULL, NULL, NULL);
INSERT INTO public.star VALUES (3, NULL, 'Sirius', NULL, NULL, 'Hot Blue', NULL, NULL, NULL);
INSERT INTO public.star VALUES (4, NULL, 'Altair', NULL, NULL, 'Red Dwarf', NULL, NULL, NULL);
INSERT INTO public.star VALUES (5, NULL, 'Pollux', NULL, NULL, 'White Dwarf', NULL, NULL, NULL);
INSERT INTO public.star VALUES (6, NULL, 'Castor', NULL, NULL, 'White Dwarf', NULL, NULL, NULL);


--
-- Name: galaxy_galaxy_id_seq; Type: SEQUENCE SET; Schema: public; Owner: freecodecamp
--

SELECT pg_catalog.setval('public.galaxy_galaxy_id_seq', 6, true);


--
-- Name: moon_moon_id_seq; Type: SEQUENCE SET; Schema: public; Owner: freecodecamp
--

SELECT pg_catalog.setval('public.moon_moon_id_seq', 20, true);


--
-- Name: oddity_oddity_id_seq; Type: SEQUENCE SET; Schema: public; Owner: freecodecamp
--

SELECT pg_catalog.setval('public.oddity_oddity_id_seq', 3, true);


--
-- Name: planet_planet_id_seq; Type: SEQUENCE SET; Schema: public; Owner: freecodecamp
--

SELECT pg_catalog.setval('public.planet_planet_id_seq', 12, true);


--
-- Name: star_star_id_seq; Type: SEQUENCE SET; Schema: public; Owner: freecodecamp
--

SELECT pg_catalog.setval('public.star_star_id_seq', 6, true);


--
-- Name: galaxy galaxy_name_key; Type: CONSTRAINT; Schema: public; Owner: freecodecamp
--

ALTER TABLE ONLY public.galaxy
    ADD CONSTRAINT galaxy_name_key UNIQUE (name);


--
-- Name: galaxy galaxy_pkey; Type: CONSTRAINT; Schema: public; Owner: freecodecamp
--

ALTER TABLE ONLY public.galaxy
    ADD CONSTRAINT galaxy_pkey PRIMARY KEY (galaxy_id);


--
-- Name: moon moon_name_key; Type: CONSTRAINT; Schema: public; Owner: freecodecamp
--

ALTER TABLE ONLY public.moon
    ADD CONSTRAINT moon_name_key UNIQUE (name);


--
-- Name: moon moon_pkey; Type: CONSTRAINT; Schema: public; Owner: freecodecamp
--

ALTER TABLE ONLY public.moon
    ADD CONSTRAINT moon_pkey PRIMARY KEY (moon_id);


--
-- Name: oddity oddity_name_key; Type: CONSTRAINT; Schema: public; Owner: freecodecamp
--

ALTER TABLE ONLY public.oddity
    ADD CONSTRAINT oddity_name_key UNIQUE (name);


--
-- Name: oddity oddity_pkey; Type: CONSTRAINT; Schema: public; Owner: freecodecamp
--

ALTER TABLE ONLY public.oddity
    ADD CONSTRAINT oddity_pkey PRIMARY KEY (oddity_id);


--
-- Name: planet planet_name_key; Type: CONSTRAINT; Schema: public; Owner: freecodecamp
--

ALTER TABLE ONLY public.planet
    ADD CONSTRAINT planet_name_key UNIQUE (name);


--
-- Name: planet planet_pkey; Type: CONSTRAINT; Schema: public; Owner: freecodecamp
--

ALTER TABLE ONLY public.planet
    ADD CONSTRAINT planet_pkey PRIMARY KEY (planet_id);


--
-- Name: star star_name_key; Type: CONSTRAINT; Schema: public; Owner: freecodecamp
--

ALTER TABLE ONLY public.star
    ADD CONSTRAINT star_name_key UNIQUE (name);


--
-- Name: star star_pkey; Type: CONSTRAINT; Schema: public; Owner: freecodecamp
--

ALTER TABLE ONLY public.star
    ADD CONSTRAINT star_pkey PRIMARY KEY (star_id);


--
-- Name: moon moon_planet_id_fkey; Type: FK CONSTRAINT; Schema: public; Owner: freecodecamp
--

ALTER TABLE ONLY public.moon
    ADD CONSTRAINT moon_planet_id_fkey FOREIGN KEY (planet_id) REFERENCES public.planet(planet_id);


--
-- Name: planet planet_star_id_fkey; Type: FK CONSTRAINT; Schema: public; Owner: freecodecamp
--

ALTER TABLE ONLY public.planet
    ADD CONSTRAINT planet_star_id_fkey FOREIGN KEY (star_id) REFERENCES public.star(star_id);


--
-- Name: star star_galaxy_id_fkey; Type: FK CONSTRAINT; Schema: public; Owner: freecodecamp
--

ALTER TABLE ONLY public.star
    ADD CONSTRAINT star_galaxy_id_fkey FOREIGN KEY (galaxy_id) REFERENCES public.galaxy(galaxy_id);


--
-- PostgreSQL database dump complete
--

