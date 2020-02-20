---
ms.openlocfilehash: 9583d868ee01117d7bd6e465e7d89a734489d1a8
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/19/2020
ms.locfileid: "77449211"
---
### <a name="boolean-parameter-of-signedcmscomputesignature-is-respected"></a><span data-ttu-id="5af18-101">Je respektován logický parametr SignedCms. ComputeSignature.</span><span class="sxs-lookup"><span data-stu-id="5af18-101">Boolean parameter of SignedCms.ComputeSignature is respected</span></span>

<span data-ttu-id="5af18-102">V rozhraní .NET Core je respektován logický `silent` parametr <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="5af18-102">In .NET Core, the Boolean `silent` parameter of the <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType> method is respected.</span></span> <span data-ttu-id="5af18-103">Pokud je tento parametr nastaven na `true`, nezobrazuje se výzva k zadání kódu PIN.</span><span class="sxs-lookup"><span data-stu-id="5af18-103">A PIN prompt is not shown if this parameter is set to `true`.</span></span>

#### <a name="change-description"></a><span data-ttu-id="5af18-104">Změnit popis</span><span class="sxs-lookup"><span data-stu-id="5af18-104">Change description</span></span>

<span data-ttu-id="5af18-105">V .NET Framework se parametr `silent` <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType> metody ignoruje a výzva k zadání kódu PIN je vždy zobrazená, pokud to vyžaduje poskytovatel.</span><span class="sxs-lookup"><span data-stu-id="5af18-105">In .NET Framework, the `silent` parameter of the <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType> method is ignored, and a PIN prompt is always shown if required by the provider.</span></span> <span data-ttu-id="5af18-106">V rozhraní .NET Core je dodržen parametr `silent` a pokud je nastavená `true`, výzva k zadání kódu PIN se nikdy nezobrazuje, i když ho poskytovatel požaduje.</span><span class="sxs-lookup"><span data-stu-id="5af18-106">In .NET Core, the `silent` parameter is respected, and if set to `true`, a PIN prompt is never shown, even if it's required by the provider.</span></span>

<span data-ttu-id="5af18-107">Podpora pro zprávy CMS/PKCS #7 byla představena do .NET Core ve verzi 2,1.</span><span class="sxs-lookup"><span data-stu-id="5af18-107">Support for CMS/PKCS #7 messages was introduced into .NET Core in version 2.1.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="5af18-108">Představená verze</span><span class="sxs-lookup"><span data-stu-id="5af18-108">Version introduced</span></span>

<span data-ttu-id="5af18-109">2.1</span><span class="sxs-lookup"><span data-stu-id="5af18-109">2.1</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="5af18-110">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="5af18-110">Recommended action</span></span>

<span data-ttu-id="5af18-111">Aby se v případě potřeby zobrazila výzva k zadání kódu PIN, aplikace klasické pracovní plochy by měly volat <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType> a nastavit parametr Boolean na `false`.</span><span class="sxs-lookup"><span data-stu-id="5af18-111">To ensure a PIN prompt appears if required, desktop applications should call <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType> and set the Boolean parameter to `false`.</span></span> <span data-ttu-id="5af18-112">Výsledné chování je stejné jako u .NET Framework bez ohledu na to, jestli je v tichém kontextu zakázaný kontext.</span><span class="sxs-lookup"><span data-stu-id="5af18-112">The resulting behavior is the same as on .NET Framework regardless of whether the silent context is disabled there.</span></span>

### <a name="category"></a><span data-ttu-id="5af18-113">Kategorie</span><span class="sxs-lookup"><span data-stu-id="5af18-113">Category</span></span>

<span data-ttu-id="5af18-114">Kryptografie</span><span class="sxs-lookup"><span data-stu-id="5af18-114">Cryptography</span></span>

### <a name="affected-apis"></a><span data-ttu-id="5af18-115">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="5af18-115">Affected APIs</span></span>

- <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType>

<!--

### Affected APIs

- `M:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)`

-->
