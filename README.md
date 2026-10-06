# Decision Support

Decision Support is a Laravel application that helps a decision maker compare alternatives. A problem is defined by named criteria, a weight for each criterion, and numeric ranges that turn a raw measurement into a score. Each alternative is then ranked with the Weighted Sum Method (WSM): every score is multiplied by its criterion weight, and those products are added together. The highest total is the preferred alternative.

## Features

- Admin login for the decision-maker workspace
- Create a problem with a name and at least two criteria
- Set each criterion’s name, weight, and score ranges
- Enter alternatives and calculate a weighted-sum score from their measured values
- Review saved problems, then update or delete their parameters

## Requirements

- PHP 8.2 or newer
- Composer
- Node.js and npm
- MySQL

## Setup

```bash
composer install
cp .env.example .env
php artisan key:generate
```

Create a MySQL database named `decision_support`, then run:

```bash
php artisan migrate
php artisan db:seed --class=AdminSeeder
npm install
npm run dev
```

In another terminal:

```bash
php artisan serve
```
For demonstration purposes: 
Open [http://localhost:8000](http://localhost:8000) and sign in with the seeded admin account:

- Email: `admin@example.com`
- Password: `password`

Change that password before using the app anywhere other than your own machine.

## How a decision is scored

1. Name the problem and choose how many criteria it has.
2. For each criterion, enter a name, a weight, and ten boundary values. Those boundaries form the ranges used to convert a measured value into a score.
3. Add alternatives. Each measured value is matched to a range, and the resulting scores are combined with the weights into one WSM total.
4. Compare the totals. The alternative with the highest total ranks first.

Saved problems can be opened again from **Criteria Tables** or edited from **Edit Problems Parameters**.
