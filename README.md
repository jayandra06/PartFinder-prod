# PartFinder MSIX Host

This repository hosts the MSIX package for PartFinder application, providing a direct HTTPS URL for Microsoft Store submission.

## Project Structure

```
PartFinder-prod/
├── public/
│   └── v1.0.1/
│       └── PartFinder-1.0.1.0.msix
├── vercel.json
└── README.md
```

## Deployment

### Step 1: GitHub Repository
✅ Repository already exists: [PartFinder-prod](https://github.com/jayandra06/PartFinder-prod.git)

### Step 2: Deploy to Vercel
1. Go to [Vercel](https://vercel.com)
2. Click "New Project" → Import your GitHub repository
3. Set framework preset to "Other" (static files only)
4. Click "Deploy"

### Step 3: Access Your MSIX
After deployment, your MSIX will be available at:
```
https://<your-vercel-project>.vercel.app/v1.0.1/PartFinder-1.0.1.0.msix
```

## Features
- ✅ Direct HTTPS URL
- ✅ Correct MIME type (`application/msix`)
- ✅ Versioned releases
- ✅ No query strings or temporary tokens
- ✅ Ready for Microsoft Store submission

## Future Versions

For new versions (e.g., v1.0.2):

1. Create a new versioned folder:
   ```bash
   mkdir -p public/v1.0.2
   ```

2. Add the new MSIX file:
   ```bash
   cp /path/to/PartFinder-1.0.2.0.msix public/v1.0.2/
   ```

3. Update `vercel.json` to include the new version:
   ```json
   {
     "headers": [
       {
         "source": "/v1.0.1/(.*).msix",
         "headers": [
           { "key": "Content-Type", "value": "application/msix" }
         ]
       },
       {
         "source": "/v1.0.2/(.*).msix",
         "headers": [
           { "key": "Content-Type", "value": "application/msix" }
         ]
       }
     ]
   }
   ```

4. Commit and push:
   ```bash
   git add .
   git commit -m "Add MSIX for v1.0.2"
   git push origin main
   ```

5. Vercel will automatically redeploy with the new version.

## MIME Type Configuration

The `vercel.json` file ensures that MSIX files are served with the correct MIME type (`application/msix`), which is required by Microsoft Store for package downloads.

## Repository Information

- **GitHub Repository**: [jayandra06/PartFinder-prod](https://github.com/jayandra06/PartFinder-prod.git)
- **Current Version**: v1.0.1
- **MSIX File**: PartFinder-1.0.1.0.msix
