# 📡 DNS over HTTPS

## 📖 Overview
DNS over HTTPS (DoH) represents a modern evolution in DNS communication, sending DNS queries over encrypted HTTPS connections instead of traditional plaintext DNS.

## 🔧 Technical Implementation
**Method**: DNS queries sent over HTTPS connections
- 📤 DNS requests encrypted via HTTPS
- 📥 DNS responses encrypted via HTTPS
- 🌐 Routed through DNS providers (e.g., cloudflare-dns.com)

## ✅ Operational Benefits

### 🛡️ Security Advantages
- 🔒 End-to-end encryption like HTTPS
- 🔐 All DNS resolution over encrypted channel
- 🥷 Difficult to monitor or intercept

### 🚫 Detection Evasion
- ✅ **Bypasses**: Traditional network monitoring systems
- 🔍 **Challenges**: Corporate networks may struggle to analyze
- 📊 **Blending**: Appears as normal HTTPS traffic

## ⚠️ Operational Considerations

### 🚧 Potential Limitations
- 🚫 Some corporate networks block nonstandard DNS requests
- 📡 May impact communication reliability
- ⏰ Potential latency considerations

### 🎯 Best Practices
- 🧪 Test in target environment before engagement
- 🔄 Have backup communication methods
- 📊 Monitor for blocking or filtering

## 🔗 Related Topics
- [[Infrastructure Evolution]] - Modern communication methods
- [[C2 Communication Channels]] - Alternative communication methods
- [[DNS over HTTPS Communication]] - Detailed implementation

## ⬅️ Navigation
← Back to [[Infrastructure Evolution]]
