# Portfolio-website
A Portfolio website for the developers which is using html CSS & Javascript.


What happened?
I try to open an URL through Selenium, after Google Chrome opened and it showed a blank page.

But when I copied this URL to a new TAB and opened it, it could be displayed normally.

How can we reproduce the issue?
This scene is sporadic，most of the time it doesn't happened.
Relevant log output
here is my code:


server_path = '../browsermob-proxy-2.1.4/bin/browsermob-proxy.bat'
server_opetion = {'prot':8080,'use-littleproxy':False}
server = Server(path=server_path,options=server_options)
server.start()
proxy = server.create_proxy()
options = webdriver.ChromeOptions()
options.add_argument('--ignore-certificate-errors')
options.add_argument('--proxy-server={0}.format(proxy.proxy))
options.add_experimental_option('excludeSwitches',['enable-automation'])
options.add_experimental_option('excludeSwitches',['enable-logging'])

try:
    driver = webdriver.Chrome(executable_path='/chrome_driver/chromedriver.exe',options=options)
except Exception as e:
    latest_driver = ChromeDriverManager().install()
    driver = webdriver.Chrome(latest_driver,options = options)

driver.maximize_window()
wait = WebDriverWait(driver,10)
proxy.new_bar('google',options={'captureHeaders':True,'captureContent':True})
driver.get('url')
Operating System
windows 10

Selenium version
4.9.0

What are the browser(s) and version(s) where you see this issue?
115.0.5790.171

What are the browser driver(s) and version(s) where you see this issue?
ChromeDriverManager().install()

Are you using Selenium Grid?
no
