📄 MOCK SENDER README - COPY THIS ENTIRE BLOCK:

# Tive Mock Sender

A testing application that generates realistic Tive IoT sensor payloads and sends them to the Integration API for validation.

## 🚀 Live Demo

**URL:** `https://tive-mock-sender.vercel.app`

## 📋 Features

- Generates valid Tive webhook payloads
- Realistic sensor data (temperature, humidity, GPS)
- Configurable device parameters
- Real-time API response display
- Error handling and validation
- Clean, responsive UI

## 🛠️ Tech Stack

- **Framework:** Next.js 16 (App Router)
- **Language:** TypeScript
- **Styling:** Tailwind CSS
- **Deployment:** Vercel

## 📦 Installation

Clone repository
git clone https://github.com/arpip01/tive-mock-sender.git
cd tive-mock-sender

Install dependencies
npm install

Setup environment variables
cp .env.example .env

Edit .env with your Integration API URL and key


## 🔐 Environment Variables

Integration API
NEXT_PUBLIC_INTEGRATION_URL="https://tive-integration-api.vercel.app/api/webhook/tive"
NEXT_PUBLIC_WEBHOOK_API_KEY="your-secret-key-here"



## 🚀 Local Development

Start development server
npm run dev

Open browser
open http://localhost:3001



## 🎯 How It Works

### 1. Payload Generation
The app generates realistic Tive payloads with:
- Random device IDs and names
- Current timestamp
- Realistic temperature (0-30°C)
- Humidity (20-80%)
- GPS coordinates (configurable)
- Battery level (0-100%)
- Cellular signal strength
- Light levels

### 2. Data Flow
User Input → Generate Payload → Send to API → Display Response



### 3. Response Handling
- ✅ Success: Shows sensor and location event IDs
- ⚠️ Warnings: Displays timestamp warnings
- ❌ Errors: Shows validation errors with details

## 📡 Usage

### Basic Usage
1. Open the app
2. (Optional) Customize device parameters
3. Click "Send Webhook"
4. View the response

### Advanced Configuration
- **Device ID:** Custom IMEI number
- **Device Name:** Custom device name
- **Location:** Latitude/Longitude coordinates
- **Temperature:** Celsius value
- **Humidity:** Percentage (0-100)
- **Battery:** Percentage (0-100)

## 🧪 Sample Payload

{
"DeviceId": "863257063350583",
"DeviceName": "A571992",
"EntryTimeEpoch": 1739215646000,
"Temperature": {
"Celsius": 10.078125
},
"Location": {
"Latitude": 40.810562,
"Longitude": -73.879285,
"FormattedAddress": "114 Hunts Point Market, Bronx, NY 10474, USA",
"LocationMethod": "wifi",
"Accuracy": {
"Meters": 23
},
"WifiAccessPointUsedCount": 5
},
"Humidity": {
"Percentage": 38.70000076293945
},
"Light": {
"Lux": 0
},
"Battery": {
"Percentage": 65
},
"Cellular": {
"Dbm": -100
}
}



## 📊 Testing Scenarios

### Test Case 1: Normal Operation
Temperature: 20°C
Humidity: 50%
Battery: 80%
Expected: Success with event IDs



### Test Case 2: Extreme Temperature
Temperature: -20°C or 50°C
Expected: Success (valid range)



### Test Case 3: Invalid Coordinates
Latitude: 95 (invalid)
Expected: Error - "Invalid latitude"



### Test Case 4: Future Timestamp
EntryTimeEpoch: Date.now() + 48 hours
Expected: Success with warning



### Test Case 5: Low Battery
Battery: 5%
Expected: Success (monitoring alert)



## 🎨 UI Features

- **Real-time Validation:** Client-side validation before sending
- **Response Display:** Formatted JSON response
- **Error Highlighting:** Clear error messages
- **Loading States:** Visual feedback during API calls
- **Responsive Design:** Works on mobile and desktop

## 🚢 Deployment

Deploy to Vercel
vercel --prod

Set environment variables in Vercel dashboard
NEXT_PUBLIC_INTEGRATION_URL
NEXT_PUBLIC_WEBHOOK_API_KEY



## 🔍 Debugging

### Check API Connection
curl -X POST https://tive-integration-api.vercel.app/api/webhook/tive
-H "Content-Type: application/json"
-H "x-api-key: your-key"
-d '{"DeviceId":"test","DeviceName":"test",...}'



### Common Issues

1. **CORS Error**
   - Check Integration API CORS settings
   - Verify API URL in environment variables

2. **401 Unauthorized**
   - Verify API key is correct
   - Check key is set in environment variables

3. **400 Bad Request**
   - Check payload format
   - Validate required fields

## 📝 Design Decisions

### 1. Client-Side Generation
- Generates payloads in browser for simplicity
- No backend needed for mock sender
- Easy to modify and test

### 2. Realistic Data
- Uses random values within valid ranges
- Mimics real IoT sensor behavior
- Helpful for stress testing

### 3. Environment Variables
- API URL and key configurable
- Easy to switch between dev/prod
- Secure credential management

## 🔮 Future Enhancements

- [ ] Bulk payload generation
- [ ] Scheduled/automated sending
- [ ] Historical data replay
- [ ] Multiple device simulation
- [ ] Payload templates library
- [ ] Response history tracking
- [ ] Export test results

## 📄 License

MIT

## 👤 Author

Arpit Patel - Phase 2 Take-Home Exercise

## 🔗 Related

**Integration API:** [Link to Integration API repo]