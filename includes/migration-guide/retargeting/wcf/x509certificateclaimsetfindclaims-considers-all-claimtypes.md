---
ms.openlocfilehash: abef47c64a7cfd99c5b50bf2100401a2d5fcc5c3
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614493"
---
### <a name="x509certificateclaimsetfindclaims-considers-all-claimtypes"></a><span data-ttu-id="4d5ab-101">X509CertificateClaimSet. FindClaims se považuje za všechny claimTypes</span><span class="sxs-lookup"><span data-stu-id="4d5ab-101">X509CertificateClaimSet.FindClaims Considers All claimTypes</span></span>

#### <a name="details"></a><span data-ttu-id="4d5ab-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="4d5ab-102">Details</span></span>

<span data-ttu-id="4d5ab-103">Pokud se v aplikacích, které cílí na .NET Framework 4.6.1, inicializuje sada deklarací x509 z certifikátu, který má ve svém poli SAN více položek DNS, <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims(System.String,System.String)?displayProperty=fullName> metoda se pokusí porovnat s argumentem ClaimType se všemi položkami DNS. U aplikací, které cílí na předchozí verze .NET Framework, se <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims(System.String,System.String)?displayProperty=fullName> Metoda pokusí porovnat argument ClaimType jenom s poslední položkou DNS.</span><span class="sxs-lookup"><span data-stu-id="4d5ab-103">In apps that target the .NET Framework 4.6.1, if an X509 claim set is initialized from a certificate that has multiple DNS entries in its SAN field, the <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims(System.String,System.String)?displayProperty=fullName> method attempts to match the claimType argument with all the DNS entries.For apps that target previous versions of the .NET Framework, the <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims(System.String,System.String)?displayProperty=fullName> method attempts to match the claimType argument only with the last DNS entry.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="4d5ab-104">Návrh</span><span class="sxs-lookup"><span data-stu-id="4d5ab-104">Suggestion</span></span>

<span data-ttu-id="4d5ab-105">Tato změna ovlivní pouze aplikace, které cílí na .NET Framework 4.6.1.</span><span class="sxs-lookup"><span data-stu-id="4d5ab-105">This change only affects applications targeting the .NET Framework 4.6.1.</span></span> <span data-ttu-id="4d5ab-106">Tato změna může být vypnutá (nebo povolená, pokud cílíte na předběžnou 4.6.1) s přepínačem [DisableMultipleDNSEntries](~/docs/framework/migration-guide/mitigation-x509certificateclaimset-findclaims-method.md#mitigation) Compatibility.</span><span class="sxs-lookup"><span data-stu-id="4d5ab-106">This change may be disabled (or enabled if targeting pre-4.6.1) with the [DisableMultipleDNSEntries](~/docs/framework/migration-guide/mitigation-x509certificateclaimset-findclaims-method.md#mitigation) compatibility switch.</span></span>

| <span data-ttu-id="4d5ab-107">Name</span><span class="sxs-lookup"><span data-stu-id="4d5ab-107">Name</span></span>    | <span data-ttu-id="4d5ab-108">Hodnota</span><span class="sxs-lookup"><span data-stu-id="4d5ab-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="4d5ab-109">Rozsah</span><span class="sxs-lookup"><span data-stu-id="4d5ab-109">Scope</span></span>   | <span data-ttu-id="4d5ab-110">Vedlejší</span><span class="sxs-lookup"><span data-stu-id="4d5ab-110">Minor</span></span>       |
| <span data-ttu-id="4d5ab-111">Verze</span><span class="sxs-lookup"><span data-stu-id="4d5ab-111">Version</span></span> | <span data-ttu-id="4d5ab-112">4.6.1</span><span class="sxs-lookup"><span data-stu-id="4d5ab-112">4.6.1</span></span>       |
| <span data-ttu-id="4d5ab-113">Typ</span><span class="sxs-lookup"><span data-stu-id="4d5ab-113">Type</span></span>    | <span data-ttu-id="4d5ab-114">Změna cílení</span><span class="sxs-lookup"><span data-stu-id="4d5ab-114">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="4d5ab-115">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="4d5ab-115">Affected APIs</span></span>

- <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims(System.String,System.String)?displayProperty=nameWithType>
