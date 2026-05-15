# Hackathon App

A Rails 7 app for creating and sharing `Home` posts with built-in authentication and automatic QR code generation for each record.

## What this app does

- User sign up/sign in with Devise
- CRUD for `Home` resources
- Ownership-based authorization with CanCanCan
- Generates a QR code image after each `Home` is created
- Uses Hotwire + Tailwind for the frontend stack

## Stack

- Ruby `3.2.0`
- Rails `~> 7.0.8`
- PostgreSQL (`pg` gem)
- Devise
- CanCanCan
- Active Storage
- RQRCode
- Tailwind CSS

## Quick Start (macOS / zsh)

1. Install dependencies
2. Create and migrate the database
3. Start the app

```bash
bundle install
bin/rails db:create
bin/rails db:migrate
bin/dev
```

Then open:

- `http://localhost:3000`

## Database setup

To seed local data (if needed):

```bash
bin/rails db:seed
```

To fully reset:

```bash
bin/rails db:drop db:create db:migrate db:seed
```

## Run tests

```bash
bin/rails test
```

System tests:

```bash
bin/rails test:system
```

## Main routes

- Root: `homes#index`
- Auth: `devise_for :users`
- Resources: `homes`

See `config/routes.rb` for details.

## Key files

- `app/models/home.rb` - `Home` model + QR code generation callback
- `app/controllers/homes_controller.rb` - `Home` CRUD
- `app/models/ability.rb` - authorization rules
- `app/models/user.rb` - Devise user model

## Notes

- QR code URLs are currently generated with `host: 'localhost:3000'` in `app/models/home.rb`.
- If you deploy, update URL generation to use your production host.

## Handy commands

```bash
bin/rails console
bin/rails routes
bin/rails test
```

## Contributing

1. Create a branch
2. Make focused changes
3. Run tests
4. Open a pull request
