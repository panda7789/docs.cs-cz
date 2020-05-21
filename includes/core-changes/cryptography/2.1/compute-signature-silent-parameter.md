---
ms.openlocfilehash: b861dbaa02c97a03c015fdf4e63d25c40c90ea0a
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721710"
---
### <a name="boolean-parameter-of-signedcmscomputesignature-is-respected"></a><span data-ttu-id="2eb87-101">Je respektován logický parametr SignedCms. ComputeSignature.</span><span class="sxs-lookup"><span data-stu-id="2eb87-101">Boolean parameter of SignedCms.ComputeSignature is respected</span></span>

<span data-ttu-id="2eb87-102">V .NET Core `silent` <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType> je respektován parametr Boolean metody.</span><span class="sxs-lookup"><span data-stu-id="2eb87-102">In .NET Core, the Boolean `silent` parameter of the <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType> method is respected.</span></span> <span data-ttu-id="2eb87-103">Pokud je tento parametr nastaven na hodnotu, není zobrazena výzva k zadání kódu PIN `true` .</span><span class="sxs-lookup"><span data-stu-id="2eb87-103">A PIN prompt is not shown if this parameter is set to `true`.</span></span>

#### <a name="change-description"></a><span data-ttu-id="2eb87-104">Popis změny</span><span class="sxs-lookup"><span data-stu-id="2eb87-104">Change description</span></span>

<span data-ttu-id="2eb87-105">V .NET Framework `silent` parametr <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType> metody je ignorován a výzva k zadání kódu PIN je vždy zobrazena, pokud to vyžaduje poskytovatel.</span><span class="sxs-lookup"><span data-stu-id="2eb87-105">In .NET Framework, the `silent` parameter of the <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType> method is ignored, and a PIN prompt is always shown if required by the provider.</span></span> <span data-ttu-id="2eb87-106">V .NET Core je `silent` parametr dodržen a pokud je nastaven na `true` , výzva k zadání kódu PIN se nikdy nezobrazuje, i když ho poskytovatel požaduje.</span><span class="sxs-lookup"><span data-stu-id="2eb87-106">In .NET Core, the `silent` parameter is respected, and if set to `true`, a PIN prompt is never shown, even if it's required by the provider.</span></span>

<span data-ttu-id="2eb87-107">Podpora pro zprávy CMS/PKCS #7 byla představena do .NET Core ve verzi 2,1.</span><span class="sxs-lookup"><span data-stu-id="2eb87-107">Support for CMS/PKCS #7 messages was introduced into .NET Core in version 2.1.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="2eb87-108">Představená verze</span><span class="sxs-lookup"><span data-stu-id="2eb87-108">Version introduced</span></span>

<span data-ttu-id="2eb87-109">2.1</span><span class="sxs-lookup"><span data-stu-id="2eb87-109">2.1</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="2eb87-110">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="2eb87-110">Recommended action</span></span>

<span data-ttu-id="2eb87-111">Aby se v případě potřeby zobrazila výzva k zadání kódu PIN, aplikace klasické pracovní plochy by měla zavolat <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType> a nastavit parametr Boolean na `false` .</span><span class="sxs-lookup"><span data-stu-id="2eb87-111">To ensure a PIN prompt appears if required, desktop applications should call <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType> and set the Boolean parameter to `false`.</span></span> <span data-ttu-id="2eb87-112">Výsledné chování je stejné jako u .NET Framework bez ohledu na to, jestli je v tichém kontextu zakázaný kontext.</span><span class="sxs-lookup"><span data-stu-id="2eb87-112">The resulting behavior is the same as on .NET Framework regardless of whether the silent context is disabled there.</span></span>

#### <a name="category"></a><span data-ttu-id="2eb87-113">Kategorie</span><span class="sxs-lookup"><span data-stu-id="2eb87-113">Category</span></span>

<span data-ttu-id="2eb87-114">Kryptografie</span><span class="sxs-lookup"><span data-stu-id="2eb87-114">Cryptography</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="2eb87-115">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="2eb87-115">Affected APIs</span></span>

- <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)`

-->
