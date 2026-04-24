# Vital Signs Service

Real-time monitoring of patient vital signs with automated alerting and pediatric growth chart generation for the Nephro Platform.

## Tech Stack

- Java 17, Spring Boot 4.0.2
- MySQL 8 (database: `monitoring_db`)
- iText (PDF report generation)
- Spring Cloud Netflix Eureka Client
- Spring Cloud Config Client

## Port

`8086`

## API Endpoints

### Vital Signs

| Method | Path | Description |
|---|---|---|
| GET | `/vital-signs/patient/{patientId}` | Get vital signs for a patient |
| POST | `/vital-signs` | Record new vital sign measurement |
| GET | `/vital-signs/{id}` | Get measurement by ID |
| DELETE | `/vital-signs/{id}` | Delete measurement |

### Alerts

| Method | Path | Description |
|---|---|---|
| GET | `/vital-signs/alerts` | List all active alerts |
| GET | `/vital-signs/alerts/patient/{patientId}` | Alerts for a patient |
| POST | `/vital-signs/alerts` | Create manual alert |
| PUT | `/vital-signs/alerts/{id}` | Update alert status |

### Alert Thresholds

| Method | Path | Description |
|---|---|---|
| GET | `/vital-signs/thresholds` | List all thresholds |
| POST | `/vital-signs/thresholds` | Set threshold for a vital sign |
| PUT | `/vital-signs/thresholds/{id}` | Update threshold |
| DELETE | `/vital-signs/thresholds/{id}` | Delete threshold |

### Growth Charts

| Method | Path | Description |
|---|---|---|
| GET | `/vital-signs/growth/{patientId}` | Get growth chart data |
| GET | `/vital-signs/growth/{patientId}/pdf` | Download growth chart PDF |

### Medical Notes

| Method | Path | Description |
|---|---|---|
| GET | `/vital-signs/notes/patient/{patientId}` | Get notes for a patient |
| POST | `/vital-signs/notes` | Add medical note |

### PDF Reports

| Method | Path | Description |
|---|---|---|
| GET | `/vital-signs/reports/patient/{patientId}` | Generate full patient PDF report |

## Environment Variables

| Variable | Description |
|---|---|
| `MYSQL_ROOT_PASSWORD` | MySQL root password |

## Features

- **Real-time monitoring** — track blood pressure, heart rate, temperature, SpO2, and other vital signs
- **Threshold alerts** — automatic alerts when measurements exceed configured limits
- **Pediatric growth charts** — age/weight/height tracking with WHO percentile references
- **Medical notes** — attach clinical observations to patient records
- **PDF reports** — generate printable vital sign summary reports

## Running Locally

```bash
mvn spring-boot:run
```

## Docker

```bash
docker build -t azizos07/vital-signs-service:latest .
docker run -p 8086:8086 \
  -e MYSQL_ROOT_PASSWORD=rootpassword \
  azizos07/vital-signs-service:latest
```
