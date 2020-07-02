---
ms.openlocfilehash: e2ae329d027d605e6331afe422e550990fab1042
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614538"
---
### <a name="default-signedxml-and-signedxms-algorithms-changed-to-sha256"></a><span data-ttu-id="e9b15-101">Výchozí algoritmy SignedXML a SignedXMS se změnily na SHA256</span><span class="sxs-lookup"><span data-stu-id="e9b15-101">Default SignedXML and SignedXMS algorithms changed to SHA256</span></span>

#### <a name="details"></a><span data-ttu-id="e9b15-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="e9b15-102">Details</span></span>

<span data-ttu-id="e9b15-103">V .NET Framework 4,7 a starších verzích SignedXML a SignedCMS jako výchozí SHA1 pro některé operace. Počínaje .NET Framework 4.7.1 je SHA256 ve výchozím nastavení povolen pro tyto operace.</span><span class="sxs-lookup"><span data-stu-id="e9b15-103">In the .NET Framework 4.7 and earlier, SignedXML and SignedCMS default to SHA1 for some operations.Starting with the .NET Framework 4.7.1, SHA256 is enabled by default for these operations.</span></span> <span data-ttu-id="e9b15-104">Tato změna je nezbytná, protože SHA1 již není považována za zabezpečenou.</span><span class="sxs-lookup"><span data-stu-id="e9b15-104">This change is necessary because SHA1 is no longer considered to be secure.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="e9b15-105">Návrh</span><span class="sxs-lookup"><span data-stu-id="e9b15-105">Suggestion</span></span>

<span data-ttu-id="e9b15-106">Existují dvě nové hodnoty přepnutí kontextu, které určují, jestli se ve výchozím nastavení používá SHA1 (nezabezpečené) nebo SHA256:</span><span class="sxs-lookup"><span data-stu-id="e9b15-106">There are two new context switch values to control whether SHA1 (insecure) or SHA256 is used by default:</span></span>

- <span data-ttu-id="e9b15-107">Switch.System.Security.Cryptography.Xml. UseInsecureHashAlgorithms</span><span class="sxs-lookup"><span data-stu-id="e9b15-107">Switch.System.Security.Cryptography.Xml.UseInsecureHashAlgorithms</span></span>
- <span data-ttu-id="e9b15-108">Switch.System. Security. Cryptography. PKCS. UseInsecureHashAlgorithms pro aplikace cílené na .NET Framework 4.7.1 a novějších verzích, pokud je použití SHA256 nežádoucí, můžete obnovit výchozí hodnotu SHA1 přidáním následujícího konfiguračního přepínače do oddílu [runtime](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) konfiguračního souboru aplikace:</span><span class="sxs-lookup"><span data-stu-id="e9b15-108">Switch.System.Security.Cryptography.Pkcs.UseInsecureHashAlgorithms For applications that target the .NET Framework 4.7.1 and later versions, if the use of SHA256 is undesirable, you can restore the default to SHA1 by adding the following configuration switch to the [runtime](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) section of your app config file:</span></span>

```xml
<AppContextSwitchOverrides value="Switch.System.Security.Cryptography.Xml.UseInsecureHashAlgorithms=true;Switch.System.Security.Cryptography.Pkcs.UseInsecureHashAlgorithms=true" />
```

<span data-ttu-id="e9b15-109">Pro aplikace, které cílí na .NET Framework 4,7 a starší verze, se můžete přihlásit k této změně přidáním následujícího konfiguračního přepínače do oddílu [runtime](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) konfiguračního souboru aplikace:</span><span class="sxs-lookup"><span data-stu-id="e9b15-109">For applications that target the .NET Framework 4.7 and earlier versions, you can opt into this change by adding the following configuration switch to the [runtime](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) section of your app config file:</span></span>

```xml
<AppContextSwitchOverrides value="Switch.System.Security.Cryptography.Xml.UseInsecureHashAlgorithms=false;Switch.System.Security.Cryptography.Pkcs.UseInsecureHashAlgorithms=false" />
```

| <span data-ttu-id="e9b15-110">Name</span><span class="sxs-lookup"><span data-stu-id="e9b15-110">Name</span></span>    | <span data-ttu-id="e9b15-111">Hodnota</span><span class="sxs-lookup"><span data-stu-id="e9b15-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="e9b15-112">Rozsah</span><span class="sxs-lookup"><span data-stu-id="e9b15-112">Scope</span></span>   | <span data-ttu-id="e9b15-113">Vedlejší</span><span class="sxs-lookup"><span data-stu-id="e9b15-113">Minor</span></span>       |
| <span data-ttu-id="e9b15-114">Verze</span><span class="sxs-lookup"><span data-stu-id="e9b15-114">Version</span></span> | <span data-ttu-id="e9b15-115">4.7.1</span><span class="sxs-lookup"><span data-stu-id="e9b15-115">4.7.1</span></span>       |
| <span data-ttu-id="e9b15-116">Typ</span><span class="sxs-lookup"><span data-stu-id="e9b15-116">Type</span></span>    | <span data-ttu-id="e9b15-117">Změna cílení</span><span class="sxs-lookup"><span data-stu-id="e9b15-117">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="e9b15-118">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="e9b15-118">Affected APIs</span></span>

- <xref:System.Security.Cryptography.Pkcs.CmsSigner?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.Xml.SignedXml?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.Xml.Reference?displayProperty=nameWithType>
