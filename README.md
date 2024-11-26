# ⭐️ Stargazer Analytics

> Transform your GitHub stars into meaningful connections. Analyze, understand, and engage with your repository's stargazers.

## 🎯 What is this?

Stargazer Analytics is a powerful tool that helps you understand and connect with the developers who star your GitHub repositories. Instead of treating stars as just numbers, we help you discover the developers behind them.

## ✨ Features

- 🔍 **Deep Analysis**: Understand who's interested in your project
- 🎯 **Interest Discovery**: Find what other repos your stargazers love
- 📊 **Smart Scoring**: Auto-score how well each stargazer fits your project
- 📧 **Email Discovery**: Get contact information for potential collaborators (you can get email of around 20% of your stargazers)
- 💌 **AI-Powered Intros**: Generate personalized outreach messages

## 🚀 Quick Start

### 1. Setup
```bash
# Clone the repository
git clone https://github.com/YOUR_USERNAME/stargazers.git
cd stargazers

# Initialize Go module
go mod init github.com/YOUR_USERNAME/stargazers
go mod tidy
```

### 2. Configure GitHub Token
1. Visit GitHub.com → Settings → Developer Settings → Personal Access Tokens
2. Generate new token (classic)
3. Select scopes: `public_repo`, `read:user`
4. Copy your token

### 3. Customize Analysis

Choose your analysis mode in `fetch/query.go`:

#### Deep Analysis Mode (get repos your stargazers are interested in)
```go
const (
    maxStarred    = 100  // Starred repos per user
    maxSubscribed = 100  // Subscribed repos per user
    minStargazers = 300  // Popularity threshold
    minForks      = 30   // Fork threshold
    minOpenIssues = 3    // Activity threshold
)
```

#### Quick Email Mode (get only your stargazers' profils like email addresses)
```go
const (
    maxStarred    = 0
    maxSubscribed = 0
    minStargazers = 0
    minForks      = 0
    minOpenIssues = 0
)
```

### 4. Run Analysis
```bash
go build
./stargazers fetch --repo=OWNER/REPO --token=YOUR_TOKEN
```

## 🛠 Advanced Options

```bash
Options:
  -r, --repo string        GitHub repository (format: owner/repo)
  -t, --token string       GitHub access token
  -c, --cache string       Cache directory (default: "./stargazer_cache")
      --verbosity          Log level for verbose output
      --no-color          Disable colored output
```

### 5. Analysis Tools

- **Data Visualization**: Plotting scripts in `/utils`
- **Email Generation**: AI-powered personalized intro generator in `/emails`

### 6. Email Sending Recommendations

For sending emails, I used Instantly. Do not send more than 30 emails per email address per day to avoid being flagged as spam.

## 📊 Stats

- Scraped over 2 days 140k stargazers of related repos
- Got 20k unique email addresses with profiles
- Scored them between 0 and 1
- Started sending for top 1k emails
- 6% booked a 15 min call for user interviews

## 📜 License

Big thanks to [spencerkimball](https://github.com/spencerkimball) for the initial implementation from 2019. 
I updated the code for the current api - and integrated everything around emails. 

Apache License 2.0 - See [LICENSE](LICENSE) for details

---

<p align="center">
Made with ❤️ for the open source community
</p>
