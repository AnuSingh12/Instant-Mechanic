# Instant Mechanic 🚗🔧

Instant Mechanic is a simple Android application that helps users find mechanics and request vehicle services.

Users can browse available mechanics, view detailed information about a mechanic, select a required service, and submit a vehicle service request.

## Features

- Browse available mechanics
- View garage name, rating, distance and location
- View available services
- Check mechanic open/closed status
- View complete mechanic details
- View address, working hours and phone number
- Request vehicle service
- Select service from a dropdown
- Enter customer and vehicle details
- Add problem description
- Form validation
- Loading states
- Error handling
- Retry failed API requests
- Success confirmation after service request submission

## Tech Stack

- Kotlin
- Android Studio
- Jetpack Compose
- Material 3
- Retrofit
- Kotlin Serialization
- Hilt
- Kotlin Coroutines
- Navigation 3
- MVVM Architecture
- MockAPI

## Application Flow

Home Screen
↓
Select Mechanic
↓
Mechanic Details
↓
Request Service
↓
Fill Service Form
↓
Submit Request
↓
Success Confirmation

## Screens

### Home Screen

The Home Screen displays a list of mechanics with:

- Garage name
- Rating
- Distance
- Location
- Available services
- Open/Closed status

### Mechanic Details

The Mechanic Details screen displays:

- Garage name
- Rating
- Location
- Address
- Available services
- Working hours
- Phone number
- Request Service button

### Request Service

The Request Service screen contains:

- Customer name
- Phone number
- Vehicle number
- Service selection
- Problem description
- Submit Request button

After successful submission, the user receives a confirmation message.

## 🏗️ Architecture

The application follows the MVVM architecture with separate data, repository, API, UI, and navigation layers.

### Project Structure

com.example.instantmechanic
│
├── data
│   ├── model
│   │   ├── Mechanic.kt
│   │   └── ServiceRequest.kt
│   │
│   ├── remote
│   │   └── MechanicApi.kt
│   │
│   └── repository
│       └── MechanicRepository.kt
│
├── di
│   └── Module.kt
│
├── navigation
│   └── navKeys.kt
│
├── ui
│   ├── component
│   │   ├── HomeComponent.kt
│   │   ├── MechanicDetailsComponent.kt
│   │   └── RequestServiceComponent.kt
│   │
│   └── screen
│       ├── home
│       │   ├── HomeScreen.kt
│       │   ├── HomeUiState.kt
│       │   └── HomeViewModel.kt
│       │
│       ├── mechanicDetails
│       │   ├── MechanicDetailsScreen.kt
│       │   ├── MechanicDetailsUiState.kt
│       │   └── MechanicDetailsViewModel.kt
│       │
│       └── requestService
│           ├── RequestServiceScreen.kt
│           ├── RequestServiceUiState.kt
│           └── RequestServiceViewModel.kt
│
├── MainActivity.kt
├── MainApp.kt
└── InstantMechanicApplication.kt

### Data Flow

UI
↓
ViewModel
↓
Repository
↓
Retrofit API
↓
MockAPI

The UI communicates with the ViewModel. The ViewModel uses the Repository to access the REST API. API responses are converted into Kotlin data models using Kotlin Serialization and exposed to the UI using StateFlow.

## REST API

The application uses MockAPI as the backend.

### Base URL

https://6a97c6db0e3240db90620f1f.mockapi.io/

### Get All Mechanics

GET /mechanics

This endpoint is used to fetch the list of available mechanics displayed on the Home Screen.

### Get Mechanic Details

GET /mechanics/{id}

This endpoint is used to fetch the details of a selected mechanic.

### Submit Service Request

POST /service-requests

This endpoint is used to submit a vehicle service request.

### Service Request Body

```json
{
  "customerName": "John Doe",
  "phoneNumber": "9876543210",
  "vehicleNumber": "UP78AB1234",
  "service": "Engine Repair",
  "problemDescription": "Engine making unusual noise"
}
