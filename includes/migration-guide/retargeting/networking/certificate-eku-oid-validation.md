---
ms.openlocfilehash: c996dafcf65b1fd428be908be346de603ead6e0b
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85615678"
---
### <a name="certificate-eku-oid-validation"></a><span data-ttu-id="dee5f-101">Ověřování IDENTIFIKÁTORu klíče EKU certifikátu</span><span class="sxs-lookup"><span data-stu-id="dee5f-101">Certificate EKU OID validation</span></span>

#### <a name="details"></a><span data-ttu-id="dee5f-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="dee5f-102">Details</span></span>

<span data-ttu-id="dee5f-103">Počínaje .NET Framework 4,6 <xref:System.Net.Security.SslStream> <xref:System.Net.ServicePointManager> třídy nebo provádějí ověřování identifikátoru objektu (OID) pomocí rozšířeného použití klíče (EKU).</span><span class="sxs-lookup"><span data-stu-id="dee5f-103">Starting with .NET Framework 4.6, the <xref:System.Net.Security.SslStream> or <xref:System.Net.ServicePointManager> classes perform enhanced key use (EKU) object identifier (OID) validation.</span></span> <span data-ttu-id="dee5f-104">Rozšíření rozšířené použití klíče (EKU) je kolekce identifikátorů objektů (OID), které označují aplikace, které klíč používají.</span><span class="sxs-lookup"><span data-stu-id="dee5f-104">An enhanced key usage (EKU) extension is a collection of object identifiers (OIDs) that indicate the applications that use the key.</span></span> <span data-ttu-id="dee5f-105">Ověřování OID rozšířeného použití klíče používá zpětná volání vzdáleného certifikátu, aby se zajistilo, že vzdálený certifikát má správné identifikátory OID pro zamýšlený účel.</span><span class="sxs-lookup"><span data-stu-id="dee5f-105">EKU OID validation uses remote certificate callbacks to ensure that the remote certificate has the correct OIDs for the intended purpose.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="dee5f-106">Návrh</span><span class="sxs-lookup"><span data-stu-id="dee5f-106">Suggestion</span></span>

<span data-ttu-id="dee5f-107">Pokud je tato změna nežádoucí, můžete ověření IDENTIFIKÁTORu klíče rozšířeného použití certifikátu zakázat přidáním následujícího přepínače do [\<AppContextSwitchOverrides>](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) [\`](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) konfiguračního souboru aplikace:</span><span class="sxs-lookup"><span data-stu-id="dee5f-107">If this change is undesirable, you can disable certificate EKU OID validation by adding the following switch to the [\<AppContextSwitchOverrides>](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) in the [\`](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) of your app configuration file:</span></span>

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.Net.DontCheckCertificateEKUs=true" />
</runtime>
```

> [!IMPORTANT]
> <span data-ttu-id="dee5f-108">Toto nastavení je k dispozici pouze pro zpětnou kompatibilitu.</span><span class="sxs-lookup"><span data-stu-id="dee5f-108">This setting is provided for backward compatibility only.</span></span> <span data-ttu-id="dee5f-109">Jeho použití není jinak doporučeno.</span><span class="sxs-lookup"><span data-stu-id="dee5f-109">Its use is otherwise not recommended.</span></span>

| <span data-ttu-id="dee5f-110">Name</span><span class="sxs-lookup"><span data-stu-id="dee5f-110">Name</span></span>    | <span data-ttu-id="dee5f-111">Hodnota</span><span class="sxs-lookup"><span data-stu-id="dee5f-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="dee5f-112">Rozsah</span><span class="sxs-lookup"><span data-stu-id="dee5f-112">Scope</span></span>   | <span data-ttu-id="dee5f-113">Vedlejší</span><span class="sxs-lookup"><span data-stu-id="dee5f-113">Minor</span></span>       |
| <span data-ttu-id="dee5f-114">Verze</span><span class="sxs-lookup"><span data-stu-id="dee5f-114">Version</span></span> | <span data-ttu-id="dee5f-115">4.6</span><span class="sxs-lookup"><span data-stu-id="dee5f-115">4.6</span></span>         |
| <span data-ttu-id="dee5f-116">Typ</span><span class="sxs-lookup"><span data-stu-id="dee5f-116">Type</span></span>    | <span data-ttu-id="dee5f-117">Změna cílení</span><span class="sxs-lookup"><span data-stu-id="dee5f-117">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="dee5f-118">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="dee5f-118">Affected APIs</span></span>

- <xref:System.Net.Security.SslStream?displayProperty=nameWithType>
- <xref:System.Net.ServicePointManager?displayProperty=nameWithType>
- <xref:System.Net.Http.HttpClient?displayProperty=nameWithType>
- <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>
- <xref:System.Net.HttpWebRequest?displayProperty=nameWithType>
- <xref:System.Net.FtpWebRequest?displayProperty=nameWithType>
