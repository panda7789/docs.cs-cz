---
ms.openlocfilehash: 23e278d38d6904d8afe927e6b54c388d443e41f5
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85616044"
---
### <a name="signedxmlgetpublickey-returns-rsacng-on-net462-or-lightup-without-retargeting-change"></a><span data-ttu-id="068f9-101">SignedXml. GetPublicKey vrátí algoritmem RSACng na net462 (nebo Lightup) bez změny cílení.</span><span class="sxs-lookup"><span data-stu-id="068f9-101">SignedXml.GetPublicKey returns RSACng on net462 (or lightup) without retargeting change</span></span>

#### <a name="details"></a><span data-ttu-id="068f9-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="068f9-102">Details</span></span>

<span data-ttu-id="068f9-103">Počínaje .NET Framework 4.6.2 se konkrétní typ objektu vráceného <xref:System.Security.Cryptography.Xml.SignedXml.GetPublicKey%2A?displayProperty=nameWithType> metodou změnil (bez Quirk) z implementace CryptoServiceProvider pro implementaci CNG.</span><span class="sxs-lookup"><span data-stu-id="068f9-103">Starting with the .NET Framework 4.6.2, the concrete type of the object returned by the <xref:System.Security.Cryptography.Xml.SignedXml.GetPublicKey%2A?displayProperty=nameWithType> method changed (without a quirk) from a CryptoServiceProvider implementation to a Cng implementation.</span></span> <span data-ttu-id="068f9-104">Důvodem je to, že implementace se změnila z použití `certificate.PublicKey.Key` na použití interního, `certificate.GetAnyPublicKey` které je předáno <xref:System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPublicKey%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="068f9-104">This is because the implementation changed from using `certificate.PublicKey.Key` to using the internal `certificate.GetAnyPublicKey` which forwards to <xref:System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPublicKey%2A?displayProperty=nameWithType>.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="068f9-105">Návrh</span><span class="sxs-lookup"><span data-stu-id="068f9-105">Suggestion</span></span>

<span data-ttu-id="068f9-106">Počínaje aplikacemi, které běží na .NET Framework 4.7.1, můžete použít implementaci CryptoServiceProvider použitou ve výchozím nastavení v .NET Framework 4.6.1 a starších verzích přidáním následujícího konfiguračního přepínače do oddílu [runtime](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) konfiguračního souboru aplikace:</span><span class="sxs-lookup"><span data-stu-id="068f9-106">Starting with apps running on the .NET Framework 4.7.1, you can use the CryptoServiceProvider implementation used by default in the .NET Framework 4.6.1 and earlier versions by adding the following configuration switch to the [runtime](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) section of your app config file:</span></span>

```xml
<AppContextSwitchOverrides value="Switch.System.Security.Cryptography.Xml.SignedXmlUseLegacyCertificatePrivateKey=true" />
```

| <span data-ttu-id="068f9-107">Name</span><span class="sxs-lookup"><span data-stu-id="068f9-107">Name</span></span>    | <span data-ttu-id="068f9-108">Hodnota</span><span class="sxs-lookup"><span data-stu-id="068f9-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="068f9-109">Rozsah</span><span class="sxs-lookup"><span data-stu-id="068f9-109">Scope</span></span>   | <span data-ttu-id="068f9-110">Edge</span><span class="sxs-lookup"><span data-stu-id="068f9-110">Edge</span></span>        |
| <span data-ttu-id="068f9-111">Verze</span><span class="sxs-lookup"><span data-stu-id="068f9-111">Version</span></span> | <span data-ttu-id="068f9-112">4.6.2</span><span class="sxs-lookup"><span data-stu-id="068f9-112">4.6.2</span></span>       |
| <span data-ttu-id="068f9-113">Typ</span><span class="sxs-lookup"><span data-stu-id="068f9-113">Type</span></span>    | <span data-ttu-id="068f9-114">Změna cílení</span><span class="sxs-lookup"><span data-stu-id="068f9-114">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="068f9-115">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="068f9-115">Affected APIs</span></span>

- <xref:System.Security.Cryptography.Xml.SignedXml.CheckSignatureReturningKey(System.Security.Cryptography.AsymmetricAlgorithm@)?displayProperty=nameWithType>
