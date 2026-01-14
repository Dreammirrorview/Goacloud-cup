# Cloud File Manager - Installation Guide

## 📋 System Requirements

### Minimum Requirements
- **Browser**: Chrome 60+, Firefox 55+, Safari 11+, Edge 79+
- **JavaScript**: Enabled
- **Storage**: At least 1GB free space
- **Internet**: Stable connection for file operations

### Recommended Requirements
- **Browser**: Latest version of Chrome, Firefox, Safari, or Edge
- **Screen Resolution**: 1920x1080 or higher
- **RAM**: 4GB or more
- **Processor**: Dual-core 2GHz or faster

## 🚀 Installation Methods

### Method 1: Direct Download (Easiest)

1. **Download the File**
   - Download `index.html` from the repository
   - Save to your desired location

2. **Open in Browser**
   - Double-click `index.html`
   - Or right-click → Open with → Choose your browser

3. **Start Using**
   - Login with admin credentials
   - Begin managing files

### Method 2: Local Web Server

#### Using Python

**Python 3:**
```bash
# Navigate to directory containing index.html
cd /path/to/cloud-file-manager

# Start HTTP server
python -m http.server 8080

# Access at: http://localhost:8080
```

**Python 2:**
```bash
# Start HTTP server
python -m SimpleHTTPServer 8080

# Access at: http://localhost:8080
```

#### Using Node.js

**Install http-server:**
```bash
npm install -g http-server
```

**Start server:**
```bash
cd /path/to/cloud-file-manager
http-server -p 8080

# Access at: http://localhost:8080
```

#### Using PHP

```bash
# Start PHP built-in server
php -S localhost:8080

# Access at: http://localhost:8080
```

### Method 3: Docker Installation

**Create Dockerfile:**
```dockerfile
FROM nginx:alpine
COPY index.html /usr/share/nginx/html/
EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]
```

**Build and Run:**
```bash
# Build image
docker build -t cloud-file-manager .

# Run container
docker run -d -p 8080:80 cloud-file-manager

# Access at: http://localhost:8080
```

### Method 4: Traditional Web Server

#### Apache Configuration

1. **Copy File to Web Directory**
```bash
# Debian/Ubuntu
sudo cp index.html /var/www/html/

# CentOS/RHEL
sudo cp index.html /var/www/html/
```

2. **Set Permissions**
```bash
sudo chown www-data:www-data /var/www/html/index.html
sudo chmod 644 /var/www/html/index.html
```

3. **Restart Apache**
```bash
# Debian/Ubuntu
sudo systemctl restart apache2

# CentOS/RHEL
sudo systemctl restart httpd
```

#### Nginx Configuration

1. **Copy File to Web Directory**
```bash
sudo cp index.html /usr/share/nginx/html/
```

2. **Set Permissions**
```bash
sudo chown nginx:nginx /usr/share/nginx/html/index.html
sudo chmod 644 /usr/share/nginx/html/index.html
```

3. **Restart Nginx**
```bash
sudo systemctl restart nginx
```

## 🔧 Configuration

### Initial Setup

1. **Change Admin Credentials**
   - Open `index.html` in a text editor
   - Find the `ADMIN_CREDENTIALS` object
   - Update username and password:
   ```javascript
   const ADMIN_CREDENTIALS = {
       username: 'your-secure-username',
       password: 'your-secure-password'
   };
   ```

2. **Customize Storage Limits**
   - Find the storage display section
   - Update the total storage value:
   ```javascript
   document.getElementById('storageTotal').textContent = '10 GB';
   ```

3. **Configure Theme Colors** (Optional)
   - Edit CSS variables in the `<style>` section
   ```css
   :root {
       --primary-color: #0066cc;
       --secondary-color: #004499;
       --accent-color: #ff9900;
   }
   ```

### Advanced Configuration

#### Enable HTTPS (Locally)
```bash
# Generate self-signed certificate
openssl req -x509 -newkey rsa:4096 -keyout key.pem -out cert.pem -days 365 -nodes

# Start server with SSL
python -m http.server 8443 --bind 0.0.0.0 --certfile cert.pem --keyfile key.pem
```

#### Configure Custom Port
```bash
# Using Python
python -m http.server 3000

# Using Node.js
http-server -p 3000

# Access at: http://localhost:3000
```

## 🧪 Testing Installation

### Basic Functionality Test

1. **Open Application**
   - Navigate to your URL
   - Verify page loads correctly

2. **Test Login**
   - Enter admin credentials
   - Verify successful login
   - Check dashboard appears

3. **Test File Upload**
   - Click upload button
   - Select a small test file
   - Verify file appears in file list

4. **Test File Download**
   - Right-click on uploaded file
   - Select download
   - Verify file downloads correctly

5. **Test File Editor**
   - Right-click on text file
   - Select edit
   - Make changes and save
   - Verify changes saved

### Performance Test

1. **Load Time**
   - Open browser DevTools (F12)
   - Go to Network tab
   - Refresh page
   - Check load time should be < 2 seconds

2. **File Operations**
   - Test with various file sizes
   - Monitor response times
   - Verify no memory leaks

## 🔍 Troubleshooting

### Common Issues

**Issue: Page won't load**
- **Solution**: Check file is in correct directory
- **Solution**: Verify server is running
- **Solution**: Check browser console for errors

**Issue: Can't login**
- **Solution**: Verify admin credentials
- **Solution**: Check JavaScript is enabled
- **Solution**: Clear browser cache and cookies

**Issue: File upload fails**
- **Solution**: Check file size (max 1GB)
- **Solution**: Verify browser compatibility
- **Solution**: Check network connection

**Issue: Editor not working**
- **Solution**: Check browser console for errors
- **Solution**: Verify file permissions
- **Solution**: Try different browser

**Issue: Terminal not showing logs**
- **Solution**: Refresh page
- **Solution**: Check JavaScript console
- **Solution**: Verify internet connection

### Browser-Specific Issues

**Chrome:**
- Enable JavaScript: Settings → Privacy and security → Site Settings → JavaScript
- Clear cache: Ctrl+Shift+Delete

**Firefox:**
- Enable JavaScript: Options → Privacy & Security → Permissions
- Clear cache: Ctrl+Shift+Delete

**Safari:**
- Enable JavaScript: Safari → Preferences → Security
- Clear cache: Safari → Clear History

**Edge:**
- Enable JavaScript: Settings → Cookies and site permissions → JavaScript
- Clear cache: Ctrl+Shift+Delete

## 📱 Mobile Installation

### iOS (iPhone/iPad)

1. **Download File**
   - Download `index.html` to your device
   - Use Files app or email

2. **Open in Browser**
   - Tap on `index.html`
   - Choose "Open in Safari"

3. **Add to Home Screen** (Optional)
   - Tap Share button
   - Select "Add to Home Screen"
   - App icon will be created

### Android

1. **Download File**
   - Download `index.html` to your device
   - Use Chrome or Files app

2. **Open in Browser**
   - Tap on `index.html`
   - Chrome will open the file

3. **Add to Home Screen** (Optional)
   - Tap menu (three dots)
   - Select "Add to Home screen"
   - App shortcut will be created

## 🔒 Security Hardening

### Initial Security Steps

1. **Change Default Password**
   - Immediately change admin password
   - Use strong password (min 12 characters)
   - Include uppercase, lowercase, numbers, symbols

2. **Enable HTTPS**
   - Install SSL certificate
   - Force HTTPS redirect
   - Update any hardcoded URLs

3. **Restrict Access**
   - Use firewall rules
   - Implement IP whitelisting
   - Set up authentication

### Ongoing Security

1. **Regular Updates**
   - Keep browser updated
   - Monitor for security patches
   - Update dependencies

2. **Access Logs**
   - Monitor terminal logs
   - Review login attempts
   - Track file operations

3. **Backup Strategy**
   - Regular file system backups
   - Store backups securely
   - Test restoration process

## 📊 Performance Optimization

### Browser Optimization

1. **Enable Hardware Acceleration**
   - Chrome: Settings → System → Use graphics acceleration
   - Firefox: Options → General → Performance

2. **Clear Cache Regularly**
   - Remove old cached files
   - Clear cookies
   - Reset browser settings

3. **Disable Extensions**
   - Test without extensions
   - Enable only necessary ones
   - Monitor performance impact

### Server Optimization

1. **Enable Compression**
   - Use gzip compression
   - Configure caching headers
   - Optimize static assets

2. **Load Balancing**
   - Use CDN for static files
   - Distribute server load
   - Implement caching

## 📈 Monitoring Setup

### Basic Monitoring

1. **Browser DevTools**
   - Monitor network requests
   - Check console for errors
   - Analyze performance

2. **Terminal Logs**
   - Review system messages
   - Track user activity
   - Monitor file operations

### Advanced Monitoring

1. **Google Analytics**
   - Add tracking code
   - Monitor user behavior
   - Analyze traffic patterns

2. **Uptime Monitoring**
   - Use external services
   - Set up alerts
   - Track availability

## ✅ Installation Verification Checklist

After installation, verify:

- [ ] Application loads successfully
- [ ] Admin login works
- [ ] File upload functional
- [ ] File download working
- [ ] Editor operates correctly
- [ ] Terminal displays logs
- [ ] Network monitor active
- [ ] Storage tracking accurate
- [ ] Mobile responsive
- [ ] SSL/HTTPS configured
- [ ] Browser compatibility verified
- [ ] Performance acceptable

## 🎉 Installation Complete!

Your Cloud File Manager is now installed and ready to use!

**Next Steps:**
1. Read the User Guide in README.md
2. Configure your settings
3. Start managing your files
4. Explore all features

**Need Help?**
- Check Troubleshooting section
- Review README.md documentation
- Contact support: support@superninja.ai

---

**Happy File Managing!** 🚀