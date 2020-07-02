---
ms.openlocfilehash: abef47c64a7cfd99c5b50bf2100401a2d5fcc5c3
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614493"
---
### <a name="x509certificateclaimsetfindclaims-considers-all-claimtypes"></a>X509CertificateClaimSet. FindClaims se považuje za všechny claimTypes

#### <a name="details"></a>Podrobnosti

Pokud se v aplikacích, které cílí na .NET Framework 4.6.1, inicializuje sada deklarací x509 z certifikátu, který má ve svém poli SAN více položek DNS, <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims(System.String,System.String)?displayProperty=fullName> metoda se pokusí porovnat s argumentem ClaimType se všemi položkami DNS. U aplikací, které cílí na předchozí verze .NET Framework, se <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims(System.String,System.String)?displayProperty=fullName> Metoda pokusí porovnat argument ClaimType jenom s poslední položkou DNS.

#### <a name="suggestion"></a>Návrh

Tato změna ovlivní pouze aplikace, které cílí na .NET Framework 4.6.1. Tato změna může být vypnutá (nebo povolená, pokud cílíte na předběžnou 4.6.1) s přepínačem [DisableMultipleDNSEntries](~/docs/framework/migration-guide/mitigation-x509certificateclaimset-findclaims-method.md#mitigation) Compatibility.

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   | Vedlejší       |
| Verze | 4.6.1       |
| Typ    | Změna cílení |

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

- <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims(System.String,System.String)?displayProperty=nameWithType>
