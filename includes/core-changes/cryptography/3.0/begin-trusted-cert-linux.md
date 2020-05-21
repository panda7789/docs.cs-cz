---
ms.openlocfilehash: 3c6142fd536bad5676f02570fecd4eb0605db829
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721718"
---
### <a name="begin-trusted-certificate-syntax-no-longer-supported-for-root-certificates-on-linux"></a><span data-ttu-id="32b1c-101">Syntaxe příkazu BEGIN TRUSTED CERTIFICATE již není podporována pro kořenové certifikáty v systému Linux</span><span class="sxs-lookup"><span data-stu-id="32b1c-101">"BEGIN TRUSTED CERTIFICATE" syntax no longer supported for root certificates on Linux</span></span>

<span data-ttu-id="32b1c-102">Kořenové certifikáty pro Linux a další systémy podobné platformě UNIX (ale ne macOS) se dají prezentovat ve dvou formách: standardní `BEGIN CERTIFICATE` Hlavička PEM a hlavička PEM pro OpenSSL specifickou pro `BEGIN TRUSTED CERTIFICATE` .</span><span class="sxs-lookup"><span data-stu-id="32b1c-102">Root certificates on Linux and other Unix-like systems (but not macOS) can be presented in two forms: the standard `BEGIN CERTIFICATE` PEM header, and the OpenSSL-specific `BEGIN TRUSTED CERTIFICATE` PEM header.</span></span> <span data-ttu-id="32b1c-103">Druhá syntaxe umožňuje další konfiguraci, která způsobila problémy s kompatibilitou třídy .NET Core <xref:System.Security.Cryptography.X509Certificates.X509Chain?displayProperty=fullName> .</span><span class="sxs-lookup"><span data-stu-id="32b1c-103">The latter syntax allows for additional configuration that has caused compatibility issues with .NET Core's <xref:System.Security.Cryptography.X509Certificates.X509Chain?displayProperty=fullName> class.</span></span> <span data-ttu-id="32b1c-104">`BEGIN TRUSTED CERTIFICATE`obsah kořenového certifikátu již není načítán modulem řetězení, který začíná v .NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="32b1c-104">`BEGIN TRUSTED CERTIFICATE` root certificate contents are no longer loaded by the chain engine starting in .NET Core 3.0.</span></span>

#### <a name="change-description"></a><span data-ttu-id="32b1c-105">Popis změny</span><span class="sxs-lookup"><span data-stu-id="32b1c-105">Change description</span></span>

<span data-ttu-id="32b1c-106">Dříve `BEGIN CERTIFICATE` `BEGIN TRUSTED CERTIFICATE` byly použity syntaxe i k naplnění seznamu důvěryhodných kořenových certifikátů.</span><span class="sxs-lookup"><span data-stu-id="32b1c-106">Previously, both the `BEGIN CERTIFICATE` and `BEGIN TRUSTED CERTIFICATE` syntaxes were used to populate the root trust list.</span></span> <span data-ttu-id="32b1c-107">Pokud `BEGIN TRUSTED CERTIFICATE` byla použita syntaxe a v souboru byly zadány další možnosti, <xref:System.Security.Cryptography.X509Certificates.X509Chain> mohou být hlášeny, že vztah důvěryhodnosti řetězu byl explicitně zakázán ( <xref:System.Security.Cryptography.X509Certificates.X509ChainStatusFlags.ExplicitDistrust?displayProperty=nameWithType> ).</span><span class="sxs-lookup"><span data-stu-id="32b1c-107">If the `BEGIN TRUSTED CERTIFICATE` syntax was used and additional options were specified in the file, <xref:System.Security.Cryptography.X509Certificates.X509Chain> may have reported that the chain trust was explicitly disallowed (<xref:System.Security.Cryptography.X509Certificates.X509ChainStatusFlags.ExplicitDistrust?displayProperty=nameWithType>).</span></span> <span data-ttu-id="32b1c-108">Pokud byl však certifikát také zadán se `BEGIN CERTIFICATE` syntaxí v dříve načteném souboru, byl povolen vztah důvěryhodnosti řetězu.</span><span class="sxs-lookup"><span data-stu-id="32b1c-108">However, if the certificate was also specified with the `BEGIN CERTIFICATE` syntax in a previously loaded file, the chain trust was allowed.</span></span>

<span data-ttu-id="32b1c-109">Počínaje platformou .NET Core 3,0 se `BEGIN TRUSTED CERTIFICATE` už obsah nepřečetl.</span><span class="sxs-lookup"><span data-stu-id="32b1c-109">Starting in .NET Core 3.0, `BEGIN TRUSTED CERTIFICATE` contents are no longer read.</span></span> <span data-ttu-id="32b1c-110">Pokud se certifikát nezadá taky pomocí standardní `BEGIN CERTIFICATE` syntaxe, <xref:System.Security.Cryptography.X509Certificates.X509Chain> hlásí, že kořenový adresář není důvěryhodný ( <xref:System.Security.Cryptography.X509Certificates.X509ChainStatusFlags.UntrustedRoot?displayProperty=nameWithType> ).</span><span class="sxs-lookup"><span data-stu-id="32b1c-110">If the certificate is not also specified via a standard `BEGIN CERTIFICATE` syntax, the <xref:System.Security.Cryptography.X509Certificates.X509Chain> reports that the root is not trusted (<xref:System.Security.Cryptography.X509Certificates.X509ChainStatusFlags.UntrustedRoot?displayProperty=nameWithType>).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="32b1c-111">Představená verze</span><span class="sxs-lookup"><span data-stu-id="32b1c-111">Version introduced</span></span>

<span data-ttu-id="32b1c-112">3.0</span><span class="sxs-lookup"><span data-stu-id="32b1c-112">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="32b1c-113">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="32b1c-113">Recommended action</span></span>

<span data-ttu-id="32b1c-114">Tato změna nemá vliv na většinu aplikací, ale aplikace, které neobsahují zdrojový kořenový certifikát, můžou při upgradu dojít k neočekávaným chybám v důsledku problémů s oprávněními `UntrustedRoot` .</span><span class="sxs-lookup"><span data-stu-id="32b1c-114">Most applications are unaffected by this change, but applications that cannot see both root certificate sources because of permissions problems may experience unexpected `UntrustedRoot` errors after upgrading.</span></span>

<span data-ttu-id="32b1c-115">Mnoho distribucí systému Linux (nebo distribuce) zápis kořenových certifikátů do dvou umístění: adresář s jedním souborem certifikátu a zřetězení jednoho souboru.</span><span class="sxs-lookup"><span data-stu-id="32b1c-115">Many Linux distributions (or distros) write root certificates into two locations: a one-certificate-per-file directory, and a one-file concatenation.</span></span> <span data-ttu-id="32b1c-116">V některých distribuce adresář s jedním certifikátem používá `BEGIN TRUSTED CERTIFICATE` syntaxi, zatímco zřetězení souboru používá standardní `BEGIN CERTIFICATE` syntaxi.</span><span class="sxs-lookup"><span data-stu-id="32b1c-116">On some distros, the one-certificate-per-file directory uses the `BEGIN TRUSTED CERTIFICATE` syntax while the file concatenation uses the standard `BEGIN CERTIFICATE` syntax.</span></span> <span data-ttu-id="32b1c-117">Zajistěte, aby byly všechny vlastní kořenové certifikáty přidány jako `BEGIN CERTIFICATE` alespoň v jednom z těchto umístění a aby mohla vaše aplikace číst obě umístění.</span><span class="sxs-lookup"><span data-stu-id="32b1c-117">Ensure that any custom root certificates are added as `BEGIN CERTIFICATE` in at least one of these locations, and that both locations can be read by your application.</span></span>

<span data-ttu-id="32b1c-118">Typický adresář je */etc/SSL/certs/* a typický zřetězený soubor je */etc/SSL/CERT.pem*.</span><span class="sxs-lookup"><span data-stu-id="32b1c-118">The typical directory is */etc/ssl/certs/* and the typical concatenated file is */etc/ssl/cert.pem*.</span></span> <span data-ttu-id="32b1c-119">Pomocí příkazu `openssl version -d` Určete kořenový adresář specifický pro platformu, který se může lišit od */etc/SSL/*.</span><span class="sxs-lookup"><span data-stu-id="32b1c-119">Use the command `openssl version -d` to determine the platform-specific root, which may differ from */etc/ssl/*.</span></span> <span data-ttu-id="32b1c-120">Například v Ubuntu 18,04 je adresář */usr/lib/SSL/certs/* a soubor je */usr/lib/SSL/CERT.pem*.</span><span class="sxs-lookup"><span data-stu-id="32b1c-120">For example, on Ubuntu 18.04, the directory is */usr/lib/ssl/certs/* and the file is */usr/lib/ssl/cert.pem*.</span></span> <span data-ttu-id="32b1c-121">*/Usr/lib/SSL/certs/* je ale symlink na */etc/SSL/certs/* a */usr/lib/SSL/CERT.pem* neexistuje.</span><span class="sxs-lookup"><span data-stu-id="32b1c-121">However, */usr/lib/ssl/certs/* is a symlink to */etc/ssl/certs/* and */usr/lib/ssl/cert.pem* does not exist.</span></span>

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

#### <a name="category"></a><span data-ttu-id="32b1c-122">Kategorie</span><span class="sxs-lookup"><span data-stu-id="32b1c-122">Category</span></span>

<span data-ttu-id="32b1c-123">Kryptografie</span><span class="sxs-lookup"><span data-stu-id="32b1c-123">Cryptography</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="32b1c-124">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="32b1c-124">Affected APIs</span></span>

- <xref:System.Security.Cryptography.X509Certificates.X509Chain?displayProperty=fullName>

<!--

#### Affected APIs

- `T:System.Security.Cryptography.X509Certificates.X509Chain`

-->
