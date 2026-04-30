CREATE TABLE cursos (
	ID SERIAL PRIMARY KEY,
	codigo VARCHAR(10) not null unique,
	nombre VARCHAR(50) not null,
	docente_responsable varchar(100) not null unique
);

CREATE TABLE estudiantes (
	ID SERIAL PRIMARY KEY,
	rut VARCHAR(12) not null unique,
	nombre VARCHAR(50) not null,
	correo VARCHAR(100) unique
);


CREATE TABLE matriculas (
	ID SERIAL PRIMARY KEY,
	fecha_inscripcion DATE DEFAULT CURRENT_DATE,
	anio INT,
	rut_estudiante VARCHAR(12),
	codigo_curso VARCHAR(10),
	FOREIGN KEY (rut_estudiante) references estudiantes(rut) on delete cascade,
	FOREIGN KEY (codigo_curso) references cursos(codigo) on delete cascade
);
