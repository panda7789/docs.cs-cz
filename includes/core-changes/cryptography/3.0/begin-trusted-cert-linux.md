---
ms.openlocfilehash: 3c6142fd536bad5676f02570fecd4eb0605db829
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721718"
---
### <a name="begin-trusted-certificate-syntax-no-longer-supported-for-root-certificates-on-linux"></a>Syntaxe příkazu BEGIN TRUSTED CERTIFICATE již není podporována pro kořenové certifikáty v systému Linux

Kořenové certifikáty pro Linux a další systémy podobné platformě UNIX (ale ne macOS) se dají prezentovat ve dvou formách: standardní `BEGIN CERTIFICATE` Hlavička PEM a hlavička PEM pro OpenSSL specifickou pro `BEGIN TRUSTED CERTIFICATE` . Druhá syntaxe umožňuje další konfiguraci, která způsobila problémy s kompatibilitou třídy .NET Core <xref:System.Security.Cryptography.X509Certificates.X509Chain?displayProperty=fullName> . `BEGIN TRUSTED CERTIFICATE`obsah kořenového certifikátu již není načítán modulem řetězení, který začíná v .NET Core 3,0.

#### <a name="change-description"></a>Popis změny

Dříve `BEGIN CERTIFICATE` `BEGIN TRUSTED CERTIFICATE` byly použity syntaxe i k naplnění seznamu důvěryhodných kořenových certifikátů. Pokud `BEGIN TRUSTED CERTIFICATE` byla použita syntaxe a v souboru byly zadány další možnosti, <xref:System.Security.Cryptography.X509Certificates.X509Chain> mohou být hlášeny, že vztah důvěryhodnosti řetězu byl explicitně zakázán ( <xref:System.Security.Cryptography.X509Certificates.X509ChainStatusFlags.ExplicitDistrust?displayProperty=nameWithType> ). Pokud byl však certifikát také zadán se `BEGIN CERTIFICATE` syntaxí v dříve načteném souboru, byl povolen vztah důvěryhodnosti řetězu.

Počínaje platformou .NET Core 3,0 se `BEGIN TRUSTED CERTIFICATE` už obsah nepřečetl. Pokud se certifikát nezadá taky pomocí standardní `BEGIN CERTIFICATE` syntaxe, <xref:System.Security.Cryptography.X509Certificates.X509Chain> hlásí, že kořenový adresář není důvěryhodný ( <xref:System.Security.Cryptography.X509Certificates.X509ChainStatusFlags.UntrustedRoot?displayProperty=nameWithType> ).

#### <a name="version-introduced"></a>Představená verze

3.0

#### <a name="recommended-action"></a>Doporučená akce

Tato změna nemá vliv na většinu aplikací, ale aplikace, které neobsahují zdrojový kořenový certifikát, můžou při upgradu dojít k neočekávaným chybám v důsledku problémů s oprávněními `UntrustedRoot` .

Mnoho distribucí systému Linux (nebo distribuce) zápis kořenových certifikátů do dvou umístění: adresář s jedním souborem certifikátu a zřetězení jednoho souboru. V některých distribuce adresář s jedním certifikátem používá `BEGIN TRUSTED CERTIFICATE` syntaxi, zatímco zřetězení souboru používá standardní `BEGIN CERTIFICATE` syntaxi. Zajistěte, aby byly všechny vlastní kořenové certifikáty přidány jako `BEGIN CERTIFICATE` alespoň v jednom z těchto umístění a aby mohla vaše aplikace číst obě umístění.

Typický adresář je */etc/SSL/certs/* a typický zřetězený soubor je */etc/SSL/CERT.pem*. Pomocí příkazu `openssl version -d` Určete kořenový adresář specifický pro platformu, který se může lišit od */etc/SSL/*. Například v Ubuntu 18,04 je adresář */usr/lib/SSL/certs/* a soubor je */usr/lib/SSL/CERT.pem*. */Usr/lib/SSL/certs/* je ale symlink na */etc/SSL/certs/* a */usr/lib/SSL/CERT.pem* neexistuje.

```bash
$ openssl version -d
OPENSSLDIR: "/usr/lib/ssl"
$ ls -al /usr/lib/ssl
total 12
drwxr-xr-x  3 root root 4096 Dec 12 17:10 .
drwxr-xr-x 73 root root 4096 Feb 20 15:18 ..
lrwxrwxrwx  1 root root   14 Mar 27  2018 certs -> /etc/ssl/certs
drwxr-xr-x  2 root root 4096 Dec 12 17:10 misc
lrwxrwxrwx  1 root root   20 Nov 12 16:58 openssl.cnf -> /etc/ssl/openssl.cnf
lrwxrwxrwx  1 root root   16 Mar 27  2018 private -> /etc/ssl/private
```

#### <a name="category"></a>Kategorie

Kryptografie

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

- <xref:System.Security.Cryptography.X509Certificates.X509Chain?displayProperty=fullName>

<!--

#### Affected APIs

- `T:System.Security.Cryptography.X509Certificates.X509Chain`

-->
