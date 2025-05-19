Importazione di dns.resolver
argaparse d'importazione

#Emoji
spia = "🕵️"
check = "✅"
croce = "❌"
cloud = "☁️"

def check_dns (dominio, dns_server):
    risolutore = dns.resolver. Risolutore ()
    risolutore.nameservers = [dns_server]
        provare:
        risultato = risolutore.risolvere (dominio, 'A')
        ips = []ip.indirizzo per IP in risultato]
        Ritorno ips
        ad eccezione di Eccezione come e:
        print (f"{cross} Errore con {dns_server}: {e}")
        Ritorno []

def principale ():
    parser = argparse. ArgumentParser (description="DNS Spoof Checker 🛡️")
    parser.add_argument ("dominio", help="Dominio da controllare")
    args = parser.parse_args ()

    dns_list = {
        "Google": "8.8.8.8",
        "Cloudflare": "1.1.1.1",
        "Quad9": "9.9.9.9",
        "OpenDNS": "208.67.222.222",
        "DNS Locale": None # Usa resolver predefinito
    }

    risultati = {}

    print (f"{spy} Controllo DNS per: {args.domain}\n")

    per nome, server in dns_list.items ():
        se server:
            ips = check_dns (args.domain, server)
        altrimenti:
            provare:
                risultato = dns.resolver.resolve (args.domain, 'A')
                ips = [ip.address for ip in result]
            Ad eccezione di Eccezione come e:
                print (f"{cross} DNS locale errore: {e}")
                ips = []

        stampa (f"{cloud} {nome}: {ips}")
        risultati[nome] = ips

    print ("\n🧠 Confronto IP tra i DNS:")
    base = elenco (risultati.valori ()) [0]
    per nome, ips in results.items ():
        se ips == base:
            stampa (f"{check} {nome} > IP corrispondenti")
        altrimenti:
            stampa (f"{cross} {nome} > IP DIVERSI ⚠️")

":
    principale)
