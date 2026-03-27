# Architecture

Framework: Laravel

Backend:
- Controllers handle HTTP
- Services contain business logic
- Models use Eloquent ORM
- Form Requests handle validation

Frontend:
- Blade templates for layouts
- Livewire components for interactive UI
- Filament for admin dashboard

Folder structure:

app/
 ├── Http/Controllers
 ├── Livewire
 ├── Services
 ├── Models
 └── Policies

database/
 ├── migrations
 └── seeders

resources/
 └── views