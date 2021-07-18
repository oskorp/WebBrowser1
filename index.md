## Welcome to GitHub Pages

You can use the [editor on GitHub](https://github.com/oskorp/WebBrowser1/edit/gh-pages/index.md) to maintain and preview the content for your website in Markdown files.

Whenever you commit to this repository, GitHub Pages will run [Jekyll](https://jekyllrb.com/) to rebuild the pages in your site, from the content in your Markdown files.

### Markdown

Markdown is a lightweight and easy-to-use syntax for styling your writing. It includes conventions for

```markdown
from PyQt5.QtWidgets import *
from PyQt5.QtCore import *
from PyQt5.QtWebEngineWidgets import *
import sys

class MainWindow(QMainWindow):
    def __init__(self):
        super(MainWindow, self).__init__()
        self.browser = QWebEngineView()
        self.browser.setUrl(QUrl("https://www.google.com/"))
        self.setCentralWidget(self.browser)
        self.showMaximized()

        navbar = QToolBar()
        self.addToolBar(navbar)

        back = QAction('<Back', self)
        back.triggered.connect(self.browser.back)
        navbar.addAction(back)

        forward=QAction('Forward>', self)
        forward.triggered.connect(self.browser.forward)
        navbar.addAction(forward)

        reload=QAction('Reload', self)
        reload.triggered.connect(self.browser.reload)
        navbar.addAction(reload)

        home=QAction('Home',self)
        home.triggered.connect(self.nav_home)
        navbar.addAction(home)

        self.url_bar = QLineEdit()
        self.url_bar.returnPressed.connect(self.nav_url)
        navbar.addWidget((self.url_bar))

        self.browser.urlChanged.connect(self.update_url)


    def nav_home(self):
           self.browser.setUrl(QUrl("https://www.google.com/"))

    def nav_url(self):
        url = self.url_bar.text()
        self.browser.setUrl(QUrl(url))

    def update_url(self, q):
        self.url_bar.setText(q.toString( ))



app = QApplication(sys.argv)
QApplication.setApplicationName("MyBrowser")
window = MainWindow()

app.exec_()
```

For more details see [GitHub Flavored Markdown](https://guides.github.com/features/mastering-markdown/).

### Jekyll Themes

Your Pages site will use the layout and styles from the Jekyll theme you have selected in your [repository settings](https://github.com/oskorp/WebBrowser1/settings/pages). The name of this theme is saved in the Jekyll `_config.yml` configuration file.

### Support or Contact

Having trouble with Pages? Check out our [documentation](https://docs.github.com/categories/github-pages-basics/) or [contact support](https://support.github.com/contact) and we’ll help you sort it out.
