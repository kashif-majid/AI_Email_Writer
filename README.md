# Content:
  A. Email Writer - AI-Powered Email Reply Generator (Backend Part)
  B. Email Reply Generator -(Frontend Part)
  C. Email Writer Assistant -(Extension Part)

# A.Email Writer - AI-Powered Email Reply Generator (Backend Part)

A Spring Boot application that uses Google's Gemini AI to generate professional email replies based on input content and desired tone.

## 🚀 Features

- **AI-Powered Email Generation**: Uses Google Gemini AI to generate contextual email replies
- **Tone Customization**: Specify the desired tone for your email (professional, friendly, formal, etc.)
- **RESTful API**: Clean REST API for easy integration
- **Cross-Origin Support**: CORS enabled for frontend integration
- **Reactive Programming**: Built with Spring WebFlux for better performance

## 🛠️ Tech Stack

- **Java 21**
- **Spring Boot 3.5.4**
- **Spring WebFlux** (Reactive Web)
- **Lombok** (Reduces boilerplate code)
- **Maven** (Dependency management)
- **Google Gemini AI API**

## 📋 Prerequisites

- Java 21 or higher
- Maven 3.6+
- Google Gemini API key

## 🔧 Setup & Installation

### 1. Clone the Repository
```bash
git clone <your-repository-url>
cd email-writer-sb
```

### 2. Get Google Gemini API Key
1. Visit [Google AI Studio](https://makersuite.google.com/app/apikey)
2. Create a new API key
3. Note down your API key

### 3. Configure Environment Variables
Create a `.env` file in the root directory or set environment variables:

```bash
# Required environment variables
GEMINI_URL=https://generativelanguage.googleapis.com/v1beta/models/gemini-pro:generateContent
GEMINI_KEY=your_gemini_api_key_here
```

### 4. Build and Run
```bash
# Build the project
mvn clean install

# Run the application
mvn spring-boot:run
```

The application will start on `http://localhost:8080`

## 📚 API Documentation

### Generate Email Reply

**Endpoint:** `POST /api/email/generate`

**Request Body:**
```json
{
    "emailContent": "Your email content here...",
    "tone": "professional" // optional: professional, friendly, formal, casual, etc.
}
```

**Response:**
```json
"Generated email reply content..."
```

**Example Request:**
```bash
curl -X POST http://localhost:8080/api/email/generate \
  -H "Content-Type: application/json" \
  -d '{
    "emailContent": "Hi, I would like to schedule a meeting to discuss the project timeline.",
    "tone": "professional"
  }'
```

**Example Response:**
```
Thank you for reaching out regarding the project timeline. I would be happy to schedule a meeting to discuss this further. 

Could you please let me know your availability for the upcoming week? I have some flexibility in my schedule and would like to find a time that works well for both of us.

Looking forward to our discussion.

Best regards,
[Your Name]
```

## 🏗️ Project Structure

```
src/
├── main/
│   ├── java/com/email/writer/
│   │   ├── app/
│   │   │   ├── EmailGeneratorController.java    # REST Controller
│   │   │   ├── EmailGeneratorService.java       # Business Logic
│   │   │   └── EmailRequest.java                # Request DTO
│   │   └── EmailWriterSbApplication.java        # Main Application Class
│   └── resources/
│       └── application.properties               # Configuration
└── test/
    └── java/com/email/writer/
        └── EmailWriterSbApplicationTests.java   # Test Classes
```

## 🔧 Configuration

The application uses the following configuration properties:

- `spring.application.name`: Application name
- `gemini.api.url`: Google Gemini API endpoint
- `gemini.api.key`: Your Gemini API key

## 🧪 Testing

Run the test suite:
```bash
mvn test
```

## 🚀 Deployment

### Using Maven
```bash
mvn clean package
java -jar target/email-writer-sb-0.0.1-SNAPSHOT.jar
```

### Using Docker (Optional)
Create a `Dockerfile`:
```dockerfile
FROM openjdk:21-jdk-slim
COPY target/email-writer-sb-0.0.1-SNAPSHOT.jar app.jar
EXPOSE 8080
ENTRYPOINT ["java", "-jar", "/app.jar"]
```

Build and run:
```bash
docker build -t email-writer-sb .
docker run -p 8080:8080 -e GEMINI_KEY=your_key email-writer-sb
```

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add some amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## 📝 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🆘 Troubleshooting

### Common Issues

1. **API Key Issues**: Ensure your Gemini API key is correctly set in environment variables
2. **Port Conflicts**: If port 8080 is in use, change it in `application.properties`:
   ```properties
   server.port=8081
   ```
3. **Java Version**: Ensure you're using Java 21 or higher

### Getting Help

- Check the [Issues](https://github.com/your-username/email-writer-sb/issues) page
- Create a new issue if you encounter problems

===============================================================================================================================================================
===============================================================================================================================================================


# B.Email Reply Generator (Frontend Part)

A modern React application that generates intelligent email replies using AI. This frontend application connects to a Spring Boot backend to provide users with contextual and tone-appropriate email responses.

## 🚀 Features

- **Smart Email Reply Generation**: Input any email content and get AI-generated replies
- **Tone Customization**: Choose from various tones including professional, friendly, casual, apologetic, enthusiastic, and more
- **Modern UI**: Built with Material-UI for a clean and responsive user experience
- **Copy to Clipboard**: Easy copying of generated replies
- **Real-time Loading States**: Visual feedback during reply generation
- **Error Handling**: Graceful error handling with user-friendly messages

## 🛠️ Tech Stack

- **Frontend**: React 19.1.1
- **Build Tool**: Vite 7.1.2
- **UI Framework**: Material-UI (MUI) 7.3.1
- **HTTP Client**: Axios 1.11.0
- **Styling**: Emotion (CSS-in-JS)
- **Linting**: ESLint 9.33.0

## 📋 Prerequisites

Before running this application, make sure you have:

- Node.js (version 16 or higher)
- npm or yarn package manager
- The corresponding Spring Boot backend running on `http://localhost:8080`

## 🚀 Getting Started

### 1. Clone the Repository

```bash
git clone <your-repository-url>
cd email-writer-react
```

### 2. Install Dependencies

```bash
npm install
```

### 3. Start the Development Server

```bash
npm run dev
```

The application will be available at `http://localhost:5173` (or the next available port).

### 4. Start the Backend

Make sure your Spring Boot backend is running on `http://localhost:8080` with the following endpoint:
- `POST /api/email/generate` - Accepts email content and tone, returns generated reply

## 📖 Usage

1. **Enter Email Content**: Paste or type the original email content in the text area
2. **Select Tone (Optional)**: Choose from the dropdown menu:
   - Professional
   - Friendly
   - Casual
   - Apologetic
   - Enthusiastic
   - Formal
   - Informal
   - Urgent
   - Appreciative
   - Persuasive
3. **Generate Reply**: Click the "Generate Reply" button
4. **Copy Result**: Use the "Copy to Clipboard" button to copy the generated reply

## 🏗️ Project Structure

```
src/
├── App.jsx          # Main application component
├── App.css          # Application styles
├── main.jsx         # Application entry point
├── index.css        # Global styles
└── assets/          # Static assets
```

## 🎨 Available Scripts

- `npm run dev` - Start development server
- `npm run build` - Build for production
- `npm run preview` - Preview production build
- `npm run lint` - Run ESLint

## 🔧 Configuration

The application is configured to connect to the backend at `http://localhost:8080`. To change this:

1. Update the axios base URL in `src/App.jsx`:
```javascript
const response = await axios.post("http://your-backend-url/api/email/generate", {
  emailContent,
  tone
});
```

## 🚀 Deployment

### Build for Production

```bash
npm run build
```

The built files will be in the `dist` directory.

### Deploy to Static Hosting

The application can be deployed to any static hosting service like:
- Vercel
- Netlify
- GitHub Pages
- AWS S3 + CloudFront

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add some amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## 📝 API Integration

The frontend expects the backend to provide the following API:

**Endpoint**: `POST /api/email/generate`

**Request Body**:
```json
{
  "emailContent": "string",
  "tone": "string"
}
```

**Response**:
```json
"Generated email reply as string"
```

## 🐛 Troubleshooting

### Common Issues

1. **Backend Connection Error**: Ensure the Spring Boot backend is running on port 8080
2. **CORS Issues**: Make sure the backend has CORS configured to allow requests from the frontend
3. **Build Errors**: Clear node_modules and reinstall dependencies

### Getting Help

If you encounter any issues:
1. Check the browser console for error messages
2. Verify the backend is running and accessible
3. Ensure all dependencies are properly installed

## 📄 License

This project is licensed under the MIT License - see the LICENSE file for details.

## 🙏 Acknowledgments

- Built with [React](https://reactjs.org/)
- UI components from [Material-UI](https://mui.com/)
- Bundled with [Vite](https://vitejs.dev/)

================================================================================================================================================================
===============================================================================================================================================================

# C.Email Writer Assistant (Extension Part)

An AI-powered Chrome extension that helps you generate professional email replies directly within Gmail. Simply click the "AI Reply" button in your compose window to get intelligent, context-aware email responses.

## Features

- 🤖 **AI-Powered Replies**: Generate professional email responses using AI
- 📧 **Gmail Integration**: Seamlessly integrates with Gmail's compose interface
- ⚡ **One-Click Generation**: Single button click to generate and insert replies
- 🎯 **Context-Aware**: Analyzes the original email content to generate relevant responses
- 🔧 **Professional Tone**: Generates responses with a professional tone by default

## How It Works

1. **Email Analysis**: The extension reads the content of the email you're replying to
2. **AI Processing**: Sends the email content to a local AI service for analysis
3. **Response Generation**: The AI generates a professional reply based on the email context
4. **Auto-Insertion**: The generated reply is automatically inserted into your compose box

## Installation

### Prerequisites

- Chrome browser (or Chromium-based browser)
- Local AI service running on `http://localhost:8080`

### Setup

1. **Clone the repository**:
   ```bash
   git clone <repository-url>
   cd email-writer-ext
   ```

2. **Load the extension in Chrome**:
   - Open Chrome and navigate to `chrome://extensions/`
   - Enable "Developer mode" in the top right corner
   - Click "Load unpacked" and select the `email-writer-ext` folder
   - The extension should now appear in your extensions list

3. **Start your AI service**:
   - Ensure your AI service is running on `http://localhost:8080`
   - The service should have an endpoint at `/api/email/generate` that accepts POST requests

## Usage

1. **Open Gmail** in your Chrome browser
2. **Open an email** you want to reply to
3. **Click "Reply"** to open the compose window
4. **Look for the "AI Reply" button** in the compose toolbar (it appears as the first button)
5. **Click "AI Reply"** to generate a professional response
6. **Review and edit** the generated reply as needed
7. **Send your email** as usual

## API Integration

The extension communicates with a local AI service that should provide the following endpoint:

### POST `/api/email/generate`

**Request Body**:
```json
{
  "emailContent": "The original email content to reply to",
  "tone": "professional"
}
```

**Response**: Plain text containing the generated email reply

## File Structure

```
email-writer-ext/
├── manifest.json          # Extension configuration
├── content.js            # Main extension logic
├── content.css           # Styling (currently empty)
└── README.md            # This file
```

## Technical Details

### Manifest Configuration
- **Manifest Version**: 3 (latest Chrome extension standard)
- **Permissions**: 
  - `activeTab`: Access to the current Gmail tab
  - `storage`: For potential future data storage
- **Host Permissions**: 
  - `*://mail.google.com/*`: Access to Gmail
  - `http://localhost:8080/*`: Access to local AI service

### Content Script Features
- **Dynamic Button Injection**: Automatically detects Gmail's compose interface
- **Email Content Extraction**: Intelligently extracts email content using multiple selectors
- **Mutation Observer**: Watches for Gmail's dynamic content changes
- **Error Handling**: Graceful error handling with user feedback

## Development

### Local Development Setup

1. **Make changes** to the extension files
2. **Reload the extension** in `chrome://extensions/`
3. **Test in Gmail** to ensure functionality

### Key Functions

- `createAIButton()`: Creates the AI Reply button with Gmail styling
- `getEmailContent()`: Extracts email content using multiple selectors
- `findComposeToolbar()`: Locates Gmail's compose toolbar
- `injectButton()`: Injects the AI button into the compose interface

## Troubleshooting

### Common Issues

1. **"AI Reply" button not appearing**:
   - Ensure you're in Gmail's compose window
   - Check that the extension is enabled in `chrome://extensions/`
   - Try refreshing the Gmail page

2. **"Failed to generate reply" error**:
   - Verify your AI service is running on `http://localhost:8080`
   - Check the browser console for detailed error messages
   - Ensure the AI service endpoint `/api/email/generate` is accessible

3. **Generated text not appearing**:
   - Make sure you're in a compose window (not just viewing an email)
   - Try clicking in the compose box before generating a reply

### Debug Mode

Open Chrome DevTools (F12) and check the Console tab for detailed logging from the extension.

## Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add some amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## License

This project is licensed under the MIT License - see the LICENSE file for details.

## Support

If you encounter any issues or have questions:

1. Check the [Troubleshooting](#troubleshooting) section
2. Open an issue on GitHub
3. Check the browser console for error messages

## Future Enhancements

- [ ] Multiple tone options (casual, formal, friendly)
- [ ] Custom AI service configuration
- [ ] Email template suggestions
- [ ] Multi-language support
- [ ] Keyboard shortcuts
- [ ] Settings panel for customization

---

**Note**: This extension requires a local AI service to function. Make sure your AI service is properly configured and running before using the extension.

===============================================================================================================================================================
===============================================================================================================================================================
## 🔮 Future Enhancements

- [ ] Add email template support
- [ ] Implement email history storage
- [ ] Add user authentication
- [ ] Support for multiple AI providers
- [ ] Email validation and formatting
- [ ] Batch email processing

## 📞 Contact

For questions or support, please open an issue in the repository.

---

**Happy Email Writing! 📧✨**
