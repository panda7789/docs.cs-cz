---
ms.openlocfilehash: 1d9a5bbea49730ee6cf99eaae6b20a0035e70b97
ms.sourcegitcommit: 8b02d42f93adda304246a47f49f6449fc74a3af4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/24/2020
ms.locfileid: "82135594"
---
### <a name="begin-trusted-certificate-syntax-no-longer-supported-for-root-certificates-on-linux"></a>Syntaxe příkazu BEGIN TRUSTED CERTIFICATE již není podporována pro kořenové certifikáty v systému Linux

Kořenové certifikáty pro Linux a další systémy podobné platformě UNIX (ale ne macOS) se dají prezentovat ve dvou formách: standardní `BEGIN CERTIFICATE` hlavička PEM a hlavička PEM pro OpenSSL specifickou `BEGIN TRUSTED CERTIFICATE` pro. Druhá syntaxe umožňuje další konfiguraci, která způsobila problémy s kompatibilitou <xref:System.Security.Cryptography.X509Certificates.X509Chain?displayProperty=fullName> třídy .NET Core. `BEGIN TRUSTED CERTIFICATE`obsah kořenového certifikátu již není načítán modulem řetězení, který začíná v .NET Core 3,0.

#### <a name="change-description"></a>Popis změny

Dříve byly použity syntaxe `BEGIN CERTIFICATE` i `BEGIN TRUSTED CERTIFICATE` k naplnění seznamu důvěryhodných kořenových certifikátů. Pokud byla `BEGIN TRUSTED CERTIFICATE` použita syntaxe a v souboru byly zadány další možnosti, <xref:System.Security.Cryptography.X509Certificates.X509Chain> mohou být hlášeny, že vztah důvěryhodnosti řetězu byl explicitně zakázán (<xref:System.Security.Cryptography.X509Certificates.X509ChainStatusFlags.ExplicitDistrust?displayProperty=nameWithType>). Pokud byl však certifikát také zadán se `BEGIN CERTIFICATE` syntaxí v dříve načteném souboru, byl povolen vztah důvěryhodnosti řetězu.

Počínaje platformou .NET Core 3,0 `BEGIN TRUSTED CERTIFICATE` se už obsah nepřečetl. Pokud se certifikát nezadá taky pomocí standardní `BEGIN CERTIFICATE` syntaxe, <xref:System.Security.Cryptography.X509Certificates.X509Chain> hlásí, že kořenový adresář není důvěryhodný (<xref:System.Security.Cryptography.X509Certificates.X509ChainStatusFlags.UntrustedRoot?displayProperty=nameWithType>).

#### <a name="version-introduced"></a>Představená verze

3.0

#### <a name="recommended-action"></a>Doporučená akce

Tato změna nemá vliv na většinu aplikací, ale aplikace, které neobsahují zdrojový kořenový certifikát, můžou při upgradu dojít k neočekávaným `UntrustedRoot` chybám v důsledku problémů s oprávněními.

Mnoho distribucí systému Linux (nebo distribuce) zápis kořenových certifikátů do dvou umístění: adresář s jedním souborem certifikátu a zřetězení jednoho souboru. V některých distribuce adresář s jedním certifikátem používá `BEGIN TRUSTED CERTIFICATE` syntaxi, zatímco zřetězení souboru používá standardní `BEGIN CERTIFICATE` syntaxi. Zajistěte, aby byly všechny vlastní kořenové `BEGIN CERTIFICATE` certifikáty přidány jako alespoň v jednom z těchto umístění a aby mohla vaše aplikace číst obě umístění.

Typický adresář je */etc/SSL/certs/* a typický zřetězený soubor je */etc/SSL/CERT.pem*. Pomocí příkazu `openssl version -d` určete kořenový adresář specifický pro platformu, který se může lišit od */etc/SSL/*. Například v Ubuntu 18,04 je adresář */usr/lib/SSL/certs/* a soubor je */usr/lib/SSL/CERT.pem*. */Usr/lib/SSL/certs/* je ale symlink na */etc/SSL/certs/* a */usr/lib/SSL/CERT.pem* neexistuje.

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

### <a name="category"></a>Kategorie

Kryptografie

### <a name="affected-apis"></a>Ovlivněná rozhraní API

- <xref:System.Security.Cryptography.X509Certificates.X509Chain?displayProperty=fullName>

<!--

### Affected APIs

- `T:System.Security.Cryptography.X509Certificates.X509Chain`

-->
