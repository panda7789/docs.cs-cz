---
ms.openlocfilehash: 9678c077e278a9d76ffd5c2ce10e63ebe3ad09f7
ms.sourcegitcommit: 4d8efe00f2e5ab42e598aff298d13b8c052d9593
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/16/2019
ms.locfileid: "68235526"
---
### <a name="x509certificateclaimsetfindclaims-considers-all-claimtypes"></a>Bere v úvahu všechny claimTypes X509CertificateClaimSet.FindClaims

|   |   |
|---|---|
|Podrobnosti|V aplikacích, které jsou cíleny rozhraní .NET Framework 4.6.1, pokud x X509 sady deklarací se inicializuje z certifikátu, který má několik záznamů DNS v jeho poli SAN <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims(System.String,System.String)?displayProperty=name> metoda se pokusí porovnat argument typu deklarace identity se všechny záznamy DNS. Pro aplikace, které cílí na předchozí verze rozhraní .NET Framework <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims(System.String,System.String)?displayProperty=name> metoda se pokusí porovnat argument typu deklarace identity jenom poslední položka DNS.|
|Doporučení|Tato změna ovlivní pouze aplikace, které cílí na rozhraní .NET Framework 4.6.1. Tato změna může být zakázaná (nebo povolit, pokud budou zaměřovat pre-4.6.1) se [DisableMultipleDNSEntries](~/docs/framework/migration-guide/mitigation-x509certificateclaimset-findclaims-method.md#mitigation) přepínače kompatibility.|
|Scope|Vedlejší|
|Version|4.6.1|
|type|Změna cílení|
|Ovlivněná rozhraní API|<ul><li><xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims(System.String,System.String)?displayProperty=nameWithType></li></ul>|
