# 🤖 CodeGuard AI ML Service

**Here is the Link : https://ml-service-a9l2.onrender.com
**
Enhanced pattern-based code analysis service with SystemError protection and comprehensive vulnerability detection.

## 🚀 Quick Start

### 1. **Setup Files**
Create these files in your project directory:

```bash
mkdir codeguard-ai
cd codeguard-ai
# Copy detector.py (the enhanced pattern-based version)
# Copy requirements.txt

```

### 2. **Simple Installation & Run**

```bash
# Install dependencies
pip install -r requirements.txt


```

**That's it! 🎉** The service will be running on `http://localhost:8000`

---

## 📋 Setup Options

### **Option A: Quick Start (Recommended)**
```bash
pip install -r requirements.txt
python detector.py
```

### **Option B: Using Smart Startup Script**
```bash
python start.py
```
*Automatically handles dependencies and chooses the best server*

### **Option C: Complete Build Process**
```bash
python build.py
cd dist
python start.py
```
*Creates a complete distribution with all deployment files*

---

## 📦 File Structure

```
codeguard-ai/
├── detector.py           # Main application (enhanced pattern-based)
├── requirements.txt      # Dependencies            
└── README.md            # This file
```

---

## 🔧 Dependencies

### **Required (Core)**
- `Flask==2.3.3` - Web framework
- `Flask-CORS==4.0.0` - CORS support

### **Optional (ML - with SystemError protection)**
- `numpy==1.24.3` - Scientific computing
- `scikit-learn==1.3.0` - Machine learning

### **Production (Recommended)**
- `gunicorn==21.2.0` - Production WSGI server

**Note:** The service works perfectly even if ML dependencies fail due to SystemError!

---

## 🧪 Testing the Service

### **1. Health Check**
```bash
curl http://localhost:8000/health
```

### **2. Test Analysis**
```bash
curl -X POST http://localhost:8000/test-analysis
```

### **3. Analyze Code**
```bash
curl -X POST http://localhost:8000/analyze/complete \
  -H "Content-Type: application/json" \
  -d '{
    "code": "query = \"SELECT * FROM users WHERE id = \" + user_id",
    "language": "python"
  }'
```

---

## 🔍 Detection Capabilities

### **🛡️ Security Vulnerabilities**
- ✅ **SQL Injection** - Dynamic query construction
- ✅ **Cross-Site Scripting (XSS)** - DOM manipulation
- ✅ **Command Injection** - System command execution
- ✅ **Hardcoded Secrets** - Passwords, API keys, tokens
- ✅ **Path Traversal** - Directory traversal attacks

### **⚡ Performance Issues**
- ✅ **Nested Loops** - O(n²) complexity detection
- ✅ **Inefficient Operations** - Slow algorithms
- ✅ **Memory Issues** - Memory-inefficient patterns

### **📋 Best Practices**
- ✅ **Missing Error Handling** - Unprotected operations
- ✅ **Long Functions** - Code maintainability
- ✅ **Magic Numbers** - Hardcoded constants

---

## 🌐 API Endpoints

| Method | Endpoint | Description |
|--------|----------|-------------|
| `GET` | `/` | Service information |
| `GET` | `/health` | Health check |
| `GET` | `/system-status` | Detailed system status |
| `POST` | `/analyze/complete` | Complete code analysis |
| `POST` | `/analyze/vulnerabilities` | Security analysis only |
| `POST` | `/analyze/performance` | Performance analysis only |
| `POST` | `/test-analysis` | Test analysis with samples |
| `GET` | `/debug-environment` | Debug information |

---

## 🚀 Deployment

### **Local Development**
```bash
python detector.py
# Runs on http://localhost:8000
```

### **Production (Gunicorn)**
```bash
gunicorn --bind 0.0.0.0:8000 --workers 2 detector:app
```

### **Docker**
```bash
# Build process creates Dockerfile
python build.py
cd dist
docker-compose up --build
```

### **Cloud Deployment**
Set environment variables:
- `PRODUCTION=true`
- `PORT=8000` (or your desired port)

---

## 🛠️ Troubleshooting

### **SystemError with numpy/scikit-learn**
```bash
# Fix 1: Use compatible versions
pip uninstall numpy scikit-learn -y
pip install numpy==1.24.3 scikit-learn==1.3.0

# Fix 2: Alternative versions
pip install numpy==1.21.6 scikit-learn==1.1.3

# Fix 3: Just use core dependencies (still works great!)
pip install Flask==2.3.3 Flask-CORS==4.0.0
```

**The service works perfectly even without ML dependencies!**

### **Port Already in Use**
```bash
# Change port
export PORT=8001
python start.py
```

### **Missing Dependencies**
```bash
# Install minimal required
pip install Flask Flask-CORS
```

---

## ✨ Features

- 🛡️ **SystemError Protection** - Graceful fallback if ML fails
- 🔍 **Enhanced Pattern Detection** - Comprehensive security patterns
- ⚡ **Fast Analysis** - No ML overhead in fallback mode
- 📊 **Detailed Reports** - Line numbers, severity, confidence scores
- 🌐 **RESTful API** - Easy integration
- 🐳 **Docker Ready** - Complete deployment package
- 📱 **CORS Enabled** - Frontend integration ready

---

## 🎯 Example Response

```json
{
  "vulnerabilities": [
    {
      "id": 1,
      "type": "Sql Injection",
      "severity": "High",
      "line": 1,
      "description": "Potential SQL injection vulnerability detected",
      "suggestion": "Use parameterized queries or prepared statements",
      "cweId": "CWE-89",
      "confidence": 0.85
    }
  ],
  "score": 80,
  "analysis_method": "Enhanced Pattern-Based Detection",
  "summary": {
    "totalIssues": 1,
    "criticalIssues": 0,
    "highIssues": 1
  }
}
```

---

## 📞 Support

If you encounter any issues:

1. **Check system status**: `GET /system-status`
2. **View debug info**: `GET /debug-environment`
3. **Test functionality**: `POST /test-analysis`

The service is designed to work reliably even with dependency issues! 🚀
