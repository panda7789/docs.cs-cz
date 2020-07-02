---
ms.openlocfilehash: c1e85941c8c6c31c7d937d0671ad955fa6490783
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614437"
---
### <a name="rsacng-now-correctly-loads-rsa-keys-of-non-standard-key-size"></a><span data-ttu-id="3f49d-101">Algoritmem RSACng nyní správně načítá klíče RSA nestandardní velikosti klíče.</span><span class="sxs-lookup"><span data-stu-id="3f49d-101">RSACng now correctly loads RSA keys of non-standard key size</span></span>

#### <a name="details"></a><span data-ttu-id="3f49d-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="3f49d-102">Details</span></span>

<span data-ttu-id="3f49d-103">V .NET Framework verzích starších než 4.6.2 zákazníci, kteří mají nestandardní velikosti klíčů pro certifikáty RSA, nemůžou získat přístup k těmto klíčům prostřednictvím <xref:System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPublicKey(System.Security.Cryptography.X509Certificates.X509Certificate2)?displayProperty=fullName> <xref:System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPrivateKey(System.Security.Cryptography.X509Certificates.X509Certificate2)?displayProperty=fullName> rozšiřujících metod a.</span><span class="sxs-lookup"><span data-stu-id="3f49d-103">In .NET Framework versions prior to 4.6.2, customers with non-standard key sizes for RSA certificates are unable to access those keys via the <xref:System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPublicKey(System.Security.Cryptography.X509Certificates.X509Certificate2)?displayProperty=fullName> and <xref:System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPrivateKey(System.Security.Cryptography.X509Certificates.X509Certificate2)?displayProperty=fullName> extension methods.</span></span>  <span data-ttu-id="3f49d-104">A <xref:System.Security.Cryptography.CryptographicException?displayProperty=fullName> se zprávou &quot; , že požadovaná velikost klíče není podporována, &quot; je vyvolána.</span><span class="sxs-lookup"><span data-stu-id="3f49d-104">A <xref:System.Security.Cryptography.CryptographicException?displayProperty=fullName> with the message &quot;The requested key size is not supported&quot; is thrown.</span></span> <span data-ttu-id="3f49d-105">V .NET Framework 4.6.2 Tento problém byl vyřešen.</span><span class="sxs-lookup"><span data-stu-id="3f49d-105">In .NET Framework 4.6.2 this issue has been fixed.</span></span> <span data-ttu-id="3f49d-106">Podobně <xref:System.Security.Cryptography.RSA.ImportParameters(System.Security.Cryptography.RSAParameters)> a <xref:System.Security.Cryptography.RSACng.ImportParameters(System.Security.Cryptography.RSAParameters)> teď můžete pracovat s nestandardními velikostmi klíčů bez vyvolání <xref:System.Security.Cryptography.CryptographicException?displayProperty=fullName> .</span><span class="sxs-lookup"><span data-stu-id="3f49d-106">Similarly, <xref:System.Security.Cryptography.RSA.ImportParameters(System.Security.Cryptography.RSAParameters)> and <xref:System.Security.Cryptography.RSACng.ImportParameters(System.Security.Cryptography.RSAParameters)> now work with non-standard key sizes without throwing a <xref:System.Security.Cryptography.CryptographicException?displayProperty=fullName>.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="3f49d-107">Návrh</span><span class="sxs-lookup"><span data-stu-id="3f49d-107">Suggestion</span></span>

<span data-ttu-id="3f49d-108">Pokud je k dispozici logika zpracování výjimek, která spoléhá na předchozí chování, kde <xref:System.Security.Cryptography.CryptographicException?displayProperty=fullName> je vyvolána při použití nestandardních velikostí klíčů, zvažte odebrání logiky.</span><span class="sxs-lookup"><span data-stu-id="3f49d-108">If there is any exception handling logic that relies on the previous behavior where a <xref:System.Security.Cryptography.CryptographicException?displayProperty=fullName> is thrown when non-standard key sizes are used, consider removing the logic.</span></span>

| <span data-ttu-id="3f49d-109">Name</span><span class="sxs-lookup"><span data-stu-id="3f49d-109">Name</span></span>    | <span data-ttu-id="3f49d-110">Hodnota</span><span class="sxs-lookup"><span data-stu-id="3f49d-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="3f49d-111">Rozsah</span><span class="sxs-lookup"><span data-stu-id="3f49d-111">Scope</span></span>   | <span data-ttu-id="3f49d-112">Edge</span><span class="sxs-lookup"><span data-stu-id="3f49d-112">Edge</span></span>        |
| <span data-ttu-id="3f49d-113">Verze</span><span class="sxs-lookup"><span data-stu-id="3f49d-113">Version</span></span> | <span data-ttu-id="3f49d-114">4.6.2</span><span class="sxs-lookup"><span data-stu-id="3f49d-114">4.6.2</span></span>       |
| <span data-ttu-id="3f49d-115">Typ</span><span class="sxs-lookup"><span data-stu-id="3f49d-115">Type</span></span>    | <span data-ttu-id="3f49d-116">Změna cílení</span><span class="sxs-lookup"><span data-stu-id="3f49d-116">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="3f49d-117">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="3f49d-117">Affected APIs</span></span>

- <xref:System.Security.Cryptography.RSA.ImportParameters(System.Security.Cryptography.RSAParameters)?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.RSACng.ImportParameters(System.Security.Cryptography.RSAParameters)?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPrivateKey(System.Security.Cryptography.X509Certificates.X509Certificate2)?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPublicKey(System.Security.Cryptography.X509Certificates.X509Certificate2)?displayProperty=nameWithType>
