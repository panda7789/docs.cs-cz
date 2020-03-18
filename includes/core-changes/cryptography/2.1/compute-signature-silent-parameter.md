---
ms.openlocfilehash: 9583d868ee01117d7bd6e465e7d89a734489d1a8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "77449211"
---
### <a name="boolean-parameter-of-signedcmscomputesignature-is-respected"></a><span data-ttu-id="73e84-101">Logický parametr SignedCms.ComputeSignature je respektován</span><span class="sxs-lookup"><span data-stu-id="73e84-101">Boolean parameter of SignedCms.ComputeSignature is respected</span></span>

<span data-ttu-id="73e84-102">V .NET Core je `silent` respektován <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType> logický parametr metody.</span><span class="sxs-lookup"><span data-stu-id="73e84-102">In .NET Core, the Boolean `silent` parameter of the <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType> method is respected.</span></span> <span data-ttu-id="73e84-103">Pokud je tento parametr nastaven na `true`hodnotu , nezobrazí se výzva kódu PIN.</span><span class="sxs-lookup"><span data-stu-id="73e84-103">A PIN prompt is not shown if this parameter is set to `true`.</span></span>

#### <a name="change-description"></a><span data-ttu-id="73e84-104">Popis změny</span><span class="sxs-lookup"><span data-stu-id="73e84-104">Change description</span></span>

<span data-ttu-id="73e84-105">V rozhraní .NET `silent` Framework <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType> je parametr metody ignorován a výzva pin ukázne vždy, pokud to vyžaduje zprostředkovatel.</span><span class="sxs-lookup"><span data-stu-id="73e84-105">In .NET Framework, the `silent` parameter of the <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType> method is ignored, and a PIN prompt is always shown if required by the provider.</span></span> <span data-ttu-id="73e84-106">V .NET Core `silent` je parametr respektován a `true`pokud je nastavena na , výzva PIN se nikdy nezobrazí, i když je vyžadována zprostředkovatelem.</span><span class="sxs-lookup"><span data-stu-id="73e84-106">In .NET Core, the `silent` parameter is respected, and if set to `true`, a PIN prompt is never shown, even if it's required by the provider.</span></span>

<span data-ttu-id="73e84-107">Podpora zpráv CMS/PKCS #7 byla zavedena do rozhraní .NET Core ve verzi 2.1.</span><span class="sxs-lookup"><span data-stu-id="73e84-107">Support for CMS/PKCS #7 messages was introduced into .NET Core in version 2.1.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="73e84-108">Zavedená verze</span><span class="sxs-lookup"><span data-stu-id="73e84-108">Version introduced</span></span>

<span data-ttu-id="73e84-109">2.1</span><span class="sxs-lookup"><span data-stu-id="73e84-109">2.1</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="73e84-110">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="73e84-110">Recommended action</span></span>

<span data-ttu-id="73e84-111">Chcete-li zajistit, aby se v <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType> případě potřeby zobrazila výzva s kódem PIN, měly by aplikace klasické pracovní plochy volat a nastavit logický parametr na `false`hodnotu .</span><span class="sxs-lookup"><span data-stu-id="73e84-111">To ensure a PIN prompt appears if required, desktop applications should call <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType> and set the Boolean parameter to `false`.</span></span> <span data-ttu-id="73e84-112">Výsledné chování je stejné jako na rozhraní .NET Framework bez ohledu na to, zda je zakázán tichý kontext.</span><span class="sxs-lookup"><span data-stu-id="73e84-112">The resulting behavior is the same as on .NET Framework regardless of whether the silent context is disabled there.</span></span>

### <a name="category"></a><span data-ttu-id="73e84-113">Kategorie</span><span class="sxs-lookup"><span data-stu-id="73e84-113">Category</span></span>

<span data-ttu-id="73e84-114">Kryptografie</span><span class="sxs-lookup"><span data-stu-id="73e84-114">Cryptography</span></span>

### <a name="affected-apis"></a><span data-ttu-id="73e84-115">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="73e84-115">Affected APIs</span></span>

- <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType>

<!--

### Affected APIs

- `M:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)`

-->
