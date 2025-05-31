# HexDNS = HNS
It is open source easily use it for change DNS

import sys
import os
from PyQt5 import QtWidgets, QtGui, QtCore

THEMES = {
    "Dark": """
        QWidget {
            background-color: #23272e;
            color: #f5f6fa;
            font-family: Segoe UI;
            font-size: 15px;
        }
        QComboBox, QLineEdit {
            background: #2d333b;
            color: #f5f6fa;
            border-radius: 8px;
            padding: 4px 8px;
        }
        QPushButton {
            background: qlineargradient(x1:0, y1:0, x2:1, y2:1, stop:0 #21c87a, stop:1 #1fa76a);
            color: #fff;
            border-radius: 16px;
            padding: 8px 0;
            font-weight: bold;
            cursor: pointer;
        }
        QPushButton#danger {
            background: qlineargradient(x1:0, y1:0, x2:1, y2:1, stop:0 #ff5e57, stop:1 #e04a44);
        }
        QPushButton#back {
            background: #444c56;
            color: #fff;
        }
        QPushButton#danger:hover, QPushButton#back:hover {
            border: 2px solid #fff;
            background: #23272e;
            color: #21c87a;
        }
        QPushButton:hover,
        QPushButton#apply:hover,
        QPushButton#refresh:hover {
            background: #1fa76a;
            border: 2px solid #21c87a;
            color: #fff;
        }
        QLabel#title {
            font-size: 18px;
            font-weight: bold;
            color: #21c87a;
        }
    """,
    "Light": """
        QWidget {
            background-color: #f5f6fa;
            color: #23272e;
            font-family: Segoe UI;
            font-size: 15px;
        }
        QComboBox, QLineEdit {
            background: #fff;
            color: #23272e;
            border-radius: 8px;
            padding: 4px 8px;
        }
        QPushButton {
            background: qlineargradient(x1:0, y1:0, x2:1, y2:1, stop:0 #21c87a, stop:1 #1fa76a);
            color: #fff;
            border-radius: 16px;
            padding: 8px 0;
            font-weight: bold;
            cursor: pointer;
        }
        QPushButton#danger {
            background: qlineargradient(x1:0, y1:0, x2:1, y2:1, stop:0 #ff5e57, stop:1 #e04a44);
        }
        QPushButton#back {
            background: #d1d1d1;
            color: #23272e;
        }
        QPushButton#danger:hover, QPushButton#back:hover {
            border: 2px solid #21c87a;
            background: #fff;
            color: #21c87a;
        }
        QPushButton:hover,
        QPushButton#apply:hover,
        QPushButton#refresh:hover {
            background: #1fa76a;
            border: 2px solid #21c87a;
            color: #fff;
        }
        QLabel#title {
            font-size: 18px;
            font-weight: bold;
            color: #21c87a;
        }
    """,
    "Blue": """
        QWidget {
            background-color: #eaf6fb;
            color: #222f3e;
            font-family: Segoe UI;
            font-size: 15px;
        }
        QComboBox, QLineEdit {
            background: #d0e6f6;
            color: #222f3e;
            border-radius: 8px;
            padding: 4px 8px;
        }
        QPushButton {
            background: qlineargradient(x1:0, y1:0, x2:1, y2:1, stop:0 #0099ff, stop:1 #005fa3);
            color: #fff;
            border-radius: 16px;
            padding: 8px 0;
            font-weight: bold;
            cursor: pointer;
        }
        QPushButton#danger {
            background: qlineargradient(x1:0, y1:0, x2:1, y2:1, stop:0 #ff5e57, stop:1 #e04a44);
        }
        QPushButton#back {
            background: #8395a7;
            color: #fff;
        }
        QPushButton#danger:hover, QPushButton#back:hover {
            border: 2px solid #0099ff;
            background: #eaf6fb;
            color: #0099ff;
        }
        QPushButton:hover,
        QPushButton#apply:hover,
        QPushButton#refresh:hover {
            background: #005fa3;
            border: 2px solid #0099ff;
            color: #fff;
        }
        QLabel#title {
            font-size: 18px;
            font-weight: bold;
            color: #0099ff;
        }
    """,
    "Purple": """
        QWidget {
            background-color: #f3e9ff;
            color: #4b3869;
            font-family: Segoe UI;
            font-size: 15px;
        }
        QComboBox, QLineEdit {
            background: #e0d0f6;
            color: #4b3869;
            border-radius: 8px;
            padding: 4px 8px;
        }
        QPushButton {
            background: qlineargradient(x1:0, y1:0, x2:1, y2:1, stop:0 #a259e6, stop:1 #6d38a1);
            color: #fff;
            border-radius: 16px;
            padding: 8px 0;
            font-weight: bold;
            cursor: pointer;
        }
        QPushButton#danger {
            background: qlineargradient(x1:0, y1:0, x2:1, y2:1, stop:0 #ff5e57, stop:1 #e04a44);
        }
        QPushButton#back {
            background: #b39ddb;
            color: #fff;
        }
        QPushButton#danger:hover, QPushButton#back:hover {
            border: 2px solid #a259e6;
            background: #f3e9ff;
            color: #a259e6;
        }
        QPushButton:hover,
        QPushButton#apply:hover,
        QPushButton#refresh:hover {
            background: #6d38a1;
            border: 2px solid #a259e6;
            color: #fff;
        }
        QLabel#title {
            font-size: 18px;
            font-weight: bold;
            color: #a259e6;
        }
    """,
    "Orange": """
        QWidget {
            background-color: #fff6e5;
            color: #7a4f01;
            font-family: Segoe UI;
            font-size: 15px;
        }
        QComboBox, QLineEdit {
            background: #ffe0b2;
            color: #7a4f01;
            border-radius: 8px;
            padding: 4px 8px;
        }
        QPushButton {
            background: qlineargradient(x1:0, y1:0, x2:1, y2:1, stop:0 #ffb347, stop:1 #ff8300);
            color: #fff;
            border-radius: 16px;
            padding: 8px 0;
            font-weight: bold;
            cursor: pointer;
        }
        QPushButton#danger {
            background: qlineargradient(x1:0, y1:0, x2:1, y2:1, stop:0 #ff5e57, stop:1 #e04a44);
        }
        QPushButton#back {
            background: #ffcc80;
            color: #7a4f01;
        }
        QPushButton#danger:hover, QPushButton#back:hover {
            border: 2px solid #ff8300;
            background: #fff6e5;
            color: #ff8300;
        }
        QPushButton:hover,
        QPushButton#apply:hover,
        QPushButton#refresh:hover {
            background: #ff8300;
            border: 2px solid #ff8300;
            color: #fff;
        }
        QLabel#title {
            font-size: 18px;
            font-weight: bold;
            color: #ff8300;
        }
    """,
    "Green": """
        QWidget {
            background-color: #e8f5e9;
            color: #1b5e20;
            font-family: Segoe UI;
            font-size: 15px;
        }
        QComboBox, QLineEdit {
            background: #c8e6c9;
            color: #1b5e20;
            border-radius: 8px;
            padding: 4px 8px;
        }
        QPushButton {
            background: qlineargradient(x1:0, y1:0, x2:1, y2:1, stop:0 #43ea7a, stop:1 #1b5e20);
            color: #fff;
            border-radius: 16px;
            padding: 8px 0;
            font-weight: bold;
            cursor: pointer;
        }
        QPushButton#danger {
            background: qlineargradient(x1:0, y1:0, x2:1, y2:1, stop:0 #ff5e57, stop:1 #e04a44);
        }
        QPushButton#back {
            background: #a5d6a7;
            color: #1b5e20;
        }
        QPushButton#danger:hover, QPushButton#back:hover {
            border: 2px solid #43ea7a;
            background: #e8f5e9;
            color: #43ea7a;
        }
        QPushButton:hover,
        QPushButton#apply:hover,
        QPushButton#refresh:hover {
            background: #1b5e20;
            border: 2px solid #43ea7a;
            color: #fff;
        }
        QLabel#title {
            font-size: 18px;
            font-weight: bold;
            color: #43ea7a;
        }
    """,
    "Pink": """
        QWidget {
            background-color: #fff0f6;
            color: #ad1457;
            font-family: Segoe UI;
            font-size: 15px;
        }
        QComboBox, QLineEdit {
            background: #f8bbd0;
            color: #ad1457;
            border-radius: 8px;
            padding: 4px 8px;
        }
        QPushButton {
            background: qlineargradient(x1:0, y1:0, x2:1, y2:1, stop:0 #ff80ab, stop:1 #ad1457);
            color: #fff;
            border-radius: 16px;
            padding: 8px 0;
            font-weight: bold;
            cursor: pointer;
        }
        QPushButton#danger {
            background: qlineargradient(x1:0, y1:0, x2:1, y2:1, stop:0 #ff5e57, stop:1 #e04a44);
        }
        QPushButton#back {
            background: #f8bbd0;
            color: #ad1457;
        }
        QPushButton#danger:hover, QPushButton#back:hover {
            border: 2px solid #ff80ab;
            background: #fff0f6;
            color: #ff80ab;
        }
        QPushButton:hover,
        QPushButton#apply:hover,
        QPushButton#refresh:hover {
            background: #ad1457;
            border: 2px solid #ff80ab;
            color: #fff;
        }
        QLabel#title {
            font-size: 18px;
            font-weight: bold;
            color: #ff80ab;
        }
    """,
    "Gray": """
        QWidget {
            background-color: #e0e0e0;
            color: #222;
            font-family: Segoe UI;
            font-size: 15px;
        }
        QComboBox, QLineEdit {
            background: #f5f5f5;
            color: #222;
            border-radius: 8px;
            padding: 4px 8px;
        }
        QPushButton {
            background: qlineargradient(x1:0, y1:0, x2:1, y2:1, stop:0 #bdbdbd, stop:1 #757575);
            color: #fff;
            border-radius: 16px;
            padding: 8px 0;
            font-weight: bold;
            cursor: pointer;
        }
        QPushButton#danger {
            background: qlineargradient(x1:0, y1:0, x2:1, y2:1, stop:0 #ff5e57, stop:1 #e04a44);
        }
        QPushButton#back {
            background: #bdbdbd;
            color: #222;
        }
        QPushButton#danger:hover, QPushButton#back:hover {
            border: 2px solid #757575;
            background: #e0e0e0;
            color: #757575;
        }
        QPushButton:hover,
        QPushButton#apply:hover,
        QPushButton#refresh:hover {
            background: #757575;
            border: 2px solid #bdbdbd;
            color: #fff;
        }
        QLabel#title {
            font-size: 18px;
            font-weight: bold;
            color: #757575;
        }
    """,
    "Yellow": """
        QWidget {
            background-color: #fffde7;
            color: #7a6000;
            font-family: Segoe UI;
            font-size: 15px;
        }
        QComboBox, QLineEdit {
            background: #fff9c4;
            color: #7a6000;
            border-radius: 8px;
            padding: 4px 8px;
        }
        QPushButton {
            background: qlineargradient(x1:0, y1:0, x2:1, y2:1, stop:0 #ffe082, stop:1 #ffd600);
            color: #fff;
            border-radius: 16px;
            padding: 8px 0;
            font-weight: bold;
            cursor: pointer;
        }
        QPushButton#danger {
            background: qlineargradient(x1:0, y1:0, x2:1, y2:1, stop:0 #ff5e57, stop:1 #e04a44);
        }
        QPushButton#back {
            background: #ffe082;
            color: #7a6000;
        }
        QPushButton#danger:hover, QPushButton#back:hover {
            border: 2px solid #ffd600;
            background: #fffde7;
            color: #ffd600;
        }
        QPushButton:hover,
        QPushButton#apply:hover,
        QPushButton#refresh:hover {
            background: #ffd600;
            border: 2px solid #ffe082;
            color: #fff;
        }
        QLabel#title {
            font-size: 18px;
            font-weight: bold;
            color: #ffd600;
        }
    """
}

class TrayApp(QtWidgets.QWidget):
    THEME_FILE = "theme.cfg"

    def __init__(self):
        super().__init__()
        self.setWindowTitle("HNS")
        self.setFixedSize(500, 320)
        self.current_theme = self.load_theme()
        self.setStyleSheet(THEMES[self.current_theme])

        #set logo for program
        self.setWindowIcon(QtGui.QIcon("Logo.ico"))

        self.dns_options = {
            "Electro": ["78.157.42.100", "78.157.42.101"],
            "Online": ["10.202.10.202", "10.202.10.102"],
            "Begzar": ["185.55.225.25", "185.55.226.26"],
            "Shatel": ["85.150.1.14", "85.150.1.15"],
            "Shecan": ["78.22.122.100", "185.51.200.2"],
            "Radar": ["10.202.10.10", "10.202.10.11"],
            "Mokhaberat": ["4.2.2.4", "5.200.200.200"],
            "Yandex": ["77.88.8.1", "77.88.8.8"],
            "Shelter 1": ["94.103.125.157", "94.103.125.158"],
            "Shelter 2": ["91.92.250.185", "91.92.244.233"],
            "Cloud Flare": ["1.1.1.1", "1.0.0.1"],
            "Rocket 1": ["10.202.10.10", "78.157.42.101"],
            "Rocket 2": ["78.157.42.100", "10.202.10.11"],
            "Pishgaman": ["5.202.100.100", "5.202.100.101"],
            "Rigester": ["91.148.245.34", "78.157.42.101"],
            "Pay": ["78.47.119.102", "78.47.119.102"],
            "Google": ["8.8.8.8", "8.8.4.4"],
            "Next DNS": ["45.90.28.190", "45.90.30.190"],
            "Open DNS": ["208.67.220.222", "208.67.222.222"],
            "NTT": ["129.250.35.250", "129.250.35.251"],
            "SprintLink": ["204.117.214.10", "199.2.252.10"],
        }

        self.init_ui()
        self.init_tray()

    def load_theme(self):
        if os.path.exists(self.THEME_FILE):
            with open(self.THEME_FILE, "r", encoding="utf-8") as f:
                theme = f.read().strip()
                if theme in THEMES:
                    return theme
        return "Dark"

    def save_theme(self, theme_name):
        with open(self.THEME_FILE, "w", encoding="utf-8") as f:
            f.write(theme_name)

    def init_ui(self):
        layout = QtWidgets.QVBoxLayout(self)
        layout.setContentsMargins(30, 20, 30, 20)
        layout.setSpacing(18)

        title = QtWidgets.QLabel("HNS DNS Changer", self)
        title.setObjectName("title")
        title.setAlignment(QtCore.Qt.AlignCenter)
        layout.addWidget(title)

        #DNS Label
        self.dns_label = QtWidgets.QLabel(self)
        self.dns_label.setAlignment(QtCore.Qt.AlignCenter)
        layout.addWidget(self.dns_label)
        self.refresh_dns_label()

        self.combo = QtWidgets.QComboBox(self)
        self.combo.addItems(self.get_sorted_dns_options())
        self.combo.setCursor(QtGui.QCursor(QtCore.Qt.PointingHandCursor))
        layout.addWidget(self.combo)
        
        #Apply Button
        btn_layout = QtWidgets.QHBoxLayout()
        self.apply_btn = QtWidgets.QPushButton("Apply DNS", self)
        self.apply_btn.setCursor(QtGui.QCursor(QtCore.Qt.PointingHandCursor))
        self.apply_btn.setObjectName("apply")
        self.apply_btn.clicked.connect(self.apply_dns)
        btn_layout.addWidget(self.apply_btn)

        #Delete Button
        self.delete_btn = QtWidgets.QPushButton("Delete DNS", self)
        self.delete_btn.setObjectName("danger")
        self.delete_btn.setCursor(QtGui.QCursor(QtCore.Qt.PointingHandCursor))
        self.delete_btn.clicked.connect(self.delete_dns)
        btn_layout.addWidget(self.delete_btn)
        layout.addLayout(btn_layout)

        #Refresh Button
        nav_layout = QtWidgets.QHBoxLayout()
        self.refresh_btn = QtWidgets.QPushButton("Refresh", self)
        self.refresh_btn.setCursor(QtGui.QCursor(QtCore.Qt.PointingHandCursor))
        self.refresh_btn.setObjectName("refresh")
        self.refresh_btn.clicked.connect(self.refresh_dns_label)
        nav_layout.addWidget(self.refresh_btn)
        
        # Theme switcher (ComboBox for theme selection)
        self.theme_combo = QtWidgets.QComboBox(self)
        self.theme_combo.addItems(list(THEMES.keys()))
        self.theme_combo.setCurrentText(self.current_theme)
        self.theme_combo.setCursor(QtGui.QCursor(QtCore.Qt.PointingHandCursor))
        self.theme_combo.currentTextChanged.connect(self.set_theme)
        nav_layout.addWidget(self.theme_combo)

        self.back_btn = QtWidgets.QPushButton("Exit", self)
        self.back_btn.setObjectName("back")
        self.back_btn.setCursor(QtGui.QCursor(QtCore.Qt.PointingHandCursor))
        self.back_btn.clicked.connect(QtWidgets.qApp.quit)
        nav_layout.addWidget(self.back_btn)

        layout.addLayout(nav_layout)

    def set_theme(self, theme_name):
        self.current_theme = theme_name
        self.setStyleSheet(THEMES[self.current_theme])
        self.save_theme(theme_name)

    def get_sorted_dns_options(self):
        keys = list(self.dns_options.keys())
        keys.remove("Electro")
        keys_sorted = sorted(keys)
        return ["Electro"] + keys_sorted

    def get_formatted_current_dns(self):
        import subprocess
        try:
            command = 'powershell -Command "Get-DnsClientServerAddress -InterfaceAlias \'Wi-Fi\' | Select-Object -ExpandProperty ServerAddresses"'
            result = subprocess.check_output(command, shell=True, text=True)
            dns_list = result.strip().split("\n")
            current_dns = ", ".join(dns_list) if dns_list else "No DNS set"
            for name, addresses in self.dns_options.items():
                if current_dns == ", ".join(addresses):
                    return f"{name} ({current_dns})"
            return f"Custom DNS ({current_dns})"
        except Exception:
            return "Unable to fetch DNS"

    def apply_dns(self):
        selected = self.combo.currentText()
        if selected in self.dns_options:
            command = f'powershell -Command "Set-DnsClientServerAddress -InterfaceAlias \'Wi-Fi\' -ServerAddresses {self.dns_options[selected][0]}, {self.dns_options[selected][1]}"'
            try:
                import subprocess
                subprocess.run(command, shell=True, check=True)
                QtWidgets.QMessageBox.information(self, "Success", f"DNS changed to {selected}!")
                self.refresh_dns_label()
            except Exception as e:
                QtWidgets.QMessageBox.critical(self, "Error", f"Failed to change DNS: {e}")
        else:
            QtWidgets.QMessageBox.warning(self, "Warning", "Please select a valid option.")

    def delete_dns(self):
        command = 'powershell -Command "Set-DnsClientServerAddress -InterfaceAlias \'Wi-Fi\' -ResetServerAddresses"'
        try:
            import subprocess
            subprocess.run(command, shell=True, check=True)
            QtWidgets.QMessageBox.information(self, "Success", "DNS settings have been cleared!")
            self.refresh_dns_label()
        except Exception as e:
            QtWidgets.QMessageBox.critical(self, "Error", f"Failed to clear DNS settings: {e}")

    def refresh_dns_label(self):
        self.dns_label.setText("Current DNS: " + self.get_formatted_current_dns())

    def closeEvent(self, event):
        event.ignore()
        self.hide()

    def show_window(self):
        self.showNormal()
        self.activateWindow()
        self.raise_()

    def on_tray_activated(self, reason):
        if reason == QtWidgets.QSystemTrayIcon.Trigger:  # Left click
            self.show_window()

    def init_tray(self):
        self.tray_icon = QtWidgets.QSystemTrayIcon(self)
        #use Logo.ico
        tray_icon = QtGui.QIcon("Logo.ico")
        self.tray_icon.setIcon(tray_icon)
        self.tray_icon.setToolTip("GameP")
 
        menu = QtWidgets.QMenu()
        show_action = menu.addAction("Open")
        quit_action = menu.addAction("Exit")
        show_action.triggered.connect(self.show_window)
        quit_action.triggered.connect(QtWidgets.qApp.quit)
        self.tray_icon.setContextMenu(menu)
        self.tray_icon.activated.connect(self.on_tray_activated)
        self.tray_icon.show()

if __name__ == "__main__":
    app = QtWidgets.QApplication(sys.argv)
    window = TrayApp()
    window.show()
    sys.exit(app.exec_())
