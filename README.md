# Animal Farm

[![CI](https://github.com/sushilduseja/devops-test/actions/workflows/test.yml/badge.svg)](https://github.com/sushilduseja/devops-test/actions/workflows/test.yml)
![Node](https://img.shields.io/badge/node-%3E%3D22-brightgreen)
![License](https://img.shields.io/badge/license-MIT-blue)

A lightweight Express.js web server that serves randomized animal sounds — a DevOps demonstration project with CI/CD, containerization, and dependency management.

## Architecture

```
GET /     → HTML page with a random animal sound (Old MacDonald parody)
GET /api  → JSON mapping of all animals to their sounds
```

The application maintains an in-memory registry of animal–sound pairs. On each request to the root endpoint, `underscore` randomly selects one entry to render into the response. The `/api` endpoint returns the full registry as JSON.

## Endpoints

### `GET /`

Returns an HTML page with a randomly selected animal and its sound.

**Response `200 OK`**
```html
George Orwell had a farm.<br />
E-I-E-I-O<br />
And on his farm he had a lion.<br />
E-I-E-I-O<br />
With a roar-roar here.<br />
And a roar-roar there.<br />
Here a roar, there a roar.<br />
Everywhere a roar-roar.<br />
```

### `GET /api`

Returns the complete animal–sound registry as JSON.

**Response `200 OK`**
```json
{
  "cat": "meow",
  "dog": "bark",
  "eel": "hiss",
  "bear": "growl",
  "small-bear": "growl",
  "frog": "croak",
  "lion": "roar",
  "big-lion": "roar"
}
```

## Quick Start

### Prerequisites

- [Node.js](https://nodejs.org/) >= 22
- [Yarn](https://yarnpkg.com/) (classic)

### Install

```shell
yarn install
```

### Run

```shell
yarn start
```

The server starts on port `8080` by default. Override with the `PORT` environment variable:

```shell
PORT=3000 yarn start
```

### Test

```shell
yarn test
```

Runs the Mocha test suite with Istanbul code coverage (HTML report written to `coverage/`).

## Docker

```shell
docker build -t animal-farm .
docker run -p 8080:8080 animal-farm
```

## Development Stack

| Layer | Technology |
|---|---|
| Runtime | Node.js 22 |
| Framework | Express 4 |
| Utility | Underscore |
| Tests | Mocha + Supertest |
| Coverage | nyc (Istanbul) |
| CI | GitHub Actions |
| Container | Docker |

## Project Structure

```
.
├── app.js                          # Application entry point
├── test/
│   └── test.js                     # Test suite
├── .github/workflows/test.yml      # CI pipeline
├── Dockerfile                      # Container definition
├── package.json                    # Dependency manifest
├── yarn.lock                       # Dependency lockfile
└── .gitignore
```

## License

MIT
