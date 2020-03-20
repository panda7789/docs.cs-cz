---
ms.openlocfilehash: 9678c077e278a9d76ffd5c2ce10e63ebe3ad09f7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "68235526"
---
### <a name="x509certificateclaimsetfindclaims-considers-all-claimtypes"></a>X509CertificateClaimSet.FindClaims bere v úvahu všechny claimTypes

|   |   |
|---|---|
|Podrobnosti|V aplikacích, které cílí na rozhraní .NET Framework 4.6.1, pokud je sada deklarací X509 inicializována z certifikátu, který má více položek DNS ve svém poli SAN, <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims(System.String,System.String)?displayProperty=name> metoda se pokusí porovnat argument claimType se všemi položkami DNS. U aplikací, které cílí na předchozí <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims(System.String,System.String)?displayProperty=name> verze rozhraní .NET Framework, se metoda pokusí porovnat argument claimType pouze s poslední položkou DNS.|
|Návrh|Tato změna se týká pouze aplikací zaměřených na rozhraní .NET Framework 4.6.1. Tato změna může být zakázána (nebo povolena, pokud targetting pre-4.6.1) s [přepínačem kompatibility DisableMultipleDNSEntries.](~/docs/framework/migration-guide/mitigation-x509certificateclaimset-findclaims-method.md#mitigation)|
|Rozsah|Vedlejší|
|Version|4.6.1|
|Typ|Změna cílení|
|Ovlivněná rozhraní API|<ul><li><xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims(System.String,System.String)?displayProperty=nameWithType></li></ul>|
