<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Payment Izalmodz</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }
        
        body {
            background: linear-gradient(135deg, #6a11cb 0%, #2575fc 100%);
            color: #fff;
            min-height: 100vh;
            display: flex;
            flex-direction: column;
            align-items: center;
            padding: 20px;
            position: relative;
        }
        
        body::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-image: url('https://files.catbox.moe/y3a7u7.jpg');
            background-size: cover;
            background-position: center;
            opacity: 0.2;
            z-index: -1;
        }
        
        .container {
            width: 100%;
            max-width: 600px;
            background: rgba(44, 16, 81, 0.85);
            border-radius: 20px;
            padding: 30px;
            box-shadow: 0 15px 35px rgba(0, 0, 0, 0.5);
            margin-top: 30px;
            backdrop-filter: blur(10px);
            border: 1px solid rgba(255, 255, 255, 0.1);
        }
        
        header {
            text-align: center;
            margin-bottom: 30px;
        }
        
        .logo {
            width: 100px;
            height: 100px;
            margin: 0 auto 15px;
            background: linear-gradient(135deg, #8a2be2 0%, #9370db 100%);
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 40px;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.3);
        }
        
        header h1 {
            font-size: 2.2rem;
            margin-bottom: 10px;
            background: linear-gradient(to right, #ff7eee, #ffcc70);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            text-shadow: 0 2px 5px rgba(0, 0, 0, 0.3);
        }
        
        header p {
            font-size: 1.1rem;
            color: #d8bfd8;
        }
        
        .payment-grid {
            display: grid;
            grid-template-columns: repeat(2, 1fr);
            gap: 15px;
            margin-bottom: 25px;
        }
        
        .payment-option {
            background: rgba(255, 255, 255, 0.1);
            border-radius: 15px;
            padding: 20px;
            transition: all 0.3s ease;
            cursor: pointer;
            text-align: center;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            border: 1px solid rgba(255, 255, 255, 0.1);
        }
        
        .payment-option:hover {
            transform: translateY(-5px);
            background: rgba(255, 255, 255, 0.15);
            box-shadow: 0 8px 20px rgba(0, 0, 0, 0.3);
        }
        
        .payment-icon {
            width: 50px;
            height: 50px;
            margin-bottom: 12px;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 24px;
            background: rgba(255, 255, 255, 0.1);
            border-radius: 50%;
            color: #e0b3ff;
        }
        
        .payment-details h3 {
            font-size: 1.1rem;
            margin-bottom: 8px;
            color: #ffccff;
        }
        
        .payment-details p {
            color: #d8bfd8;
            font-size: 0.9rem;
            word-break: break-all;
        }
        
        .copy-btn {
            background: linear-gradient(to right, #8a2be2, #6a5acd);
            color: white;
            border: none;
            padding: 8px 15px;
            border-radius: 20px;
            cursor: pointer;
            margin-top: 10px;
            transition: all 0.3s;
            font-size: 0.9rem;
        }
        
        .copy-btn:hover {
            background: linear-gradient(to right, #6a5acd, #8a2be2);
            transform: scale(1.05);
        }
        
        .action-buttons {
            display: flex;
            flex-direction: column;
            gap: 15px;
        }
        
        .action-btn {
            display: flex;
            align-items: center;
            justify-content: center;
            padding: 15px;
            background: linear-gradient(to right, #8a2be2, #6a5acd);
            color: white;
            text-align: center;
            border-radius: 15px;
            text-decoration: none;
            font-weight: bold;
            font-size: 1.1rem;
            transition: all 0.3s;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.2);
        }
        
        .action-btn:hover {
            background: linear-gradient(to right, #6a5acd, #8a2be2);
            transform: translateY(-3px);
            box-shadow: 0 8px 20px rgba(0, 0, 0, 0.3);
        }
        
        .action-btn i {
            margin-right: 10px;
        }
        
        footer {
            text-align: center;
            margin-top: 30px;
            color: #d8bfd8;
            font-size: 0.9rem;
        }
        
        .notification {
            position: fixed;
            top: 20px;
            right: 20px;
            padding: 15px 20px;
            background: linear-gradient(to right, #8a2be2, #6a5acd);
            color: white;
            border-radius: 10px;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.3);
            transform: translateX(100%);
            transition: transform 0.3s;
            z-index: 1000;
            display: flex;
            align-items: center;
        }
        
        .notification i {
            margin-right: 10px;
            font-size: 20px;
        }
        
        .notification.show {
            transform: translateX(0);
        }
        
        @media (max-width: 768px) {
            .payment-grid {
                grid-template-columns: 1fr;
            }
            
            .container {
                padding: 20px;
            }
            
            header h1 {
                font-size: 1.8rem;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <header>
            <div class="logo">
                <i class="fas fa-wallet"></i>
            </div>
            <h1>PAYMENT IZALMODZ</h1>
            <p>Pilih metode pembayaran yang Anda inginkan</p>
        </header>
        
        <div class="payment-grid">
            <div class="payment-option" onclick="copyToClipboard('087840418101', 'DANA')">
                <div class="payment-icon">
                    <i class="fas fa-money-bill-wave"></i>
                </div>
                <div class="payment-details">
                    <h3>DANA</h3>
                    <p>087840418101</p>
                    <button class="copy-btn">Salin Nomor</button>
                </div>
            </div>
            
            <div class="payment-option" onclick="copyToClipboard('087817757895', 'GOPAY')">
                <div class="payment-icon">
                    <i class="fab fa-google-wallet"></i>
                </div>
                <div class="payment-details">
                    <h3>GOPAY</h3>
                    <p>087817757895</p>
                    <button class="copy-btn">Salin Nomor</button>
                </div>
            </div>
            
            <div class="payment-option" onclick="copyToClipboard('087817757895', 'OVO')">
                <div class="payment-icon">
                    <i class="fas fa-mobile-alt"></i>
                </div>
                <div class="payment-details">
                    <h3>OVO</h3>
                    <p>087817757895</p>
                    <button class="copy-btn">Salin Nomor</button>
                </div>
            </div>
            
            <div class="payment-option" onclick="showQRISNotification()">
                <div class="payment-icon">
                    <i class="fas fa-qrcode"></i>
                </div>
                <div class="payment-details">
                    <h3>QRIS</h3>
                    <p>Hubungi kami di Telegram untuk QRIS</p>
                </div>
            </div>
        </div>
        
        <div class="action-buttons">
            <a href="https://t.me/Izalmodz" class="action-btn" target="_blank">
                <i class="fab fa-telegram"></i> Jasa Order Murband via Telegram
            </a>
            
            <a href="https://wa.me/6287817757895" class="action-btn" target="_blank">
                <i class="fab fa-whatsapp"></i> Hubungi Kami via WhatsApp
            </a>
        </div>
    </div>
    
    <footer>
        <p>© 2023 Payment Izalmodz. Semua hak cipta dilindungi.</p>
    </footer>
    
    <div class="notification" id="notification">
        <i class="fas fa-check-circle"></i>
        <span id="notification-text">Nomor berhasil disalin ke clipboard!</span>
    </div>

    <script>
        function copyToClipboard(text, method) {
            const textArea = document.createElement('textarea');
            textArea.value = text;
            document.body.appendChild(textArea);
            textArea.select();
            document.execCommand('copy');
            document.body.removeChild(textArea);
            
            const notification = document.getElementById('notification');
            const notificationText = document.getElementById('notification-text');
            notificationText.textContent = `Nomor ${method} berhasil disalin!`;
            notification.classList.add('show');
            
            setTimeout(() => {
                notification.classList.remove('show');
            }, 3000);
        }
        
        function showQRISNotification() {
            const notification = document.getElementById('notification');
            const notificationText = document.getElementById('notification-text');
            notificationText.textContent = 'Silakan hubungi kami di Telegram untuk mendapatkan QRIS';
            notification.classList.add('show');
            
            setTimeout(() => {
                notification.classList.remove('show');
            }, 3000);
        }
    </script>
</body>
</html>
