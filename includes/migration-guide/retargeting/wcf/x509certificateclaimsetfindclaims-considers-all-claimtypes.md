---
ms.openlocfilehash: fe5dfa0b8866debd8a6091a264e251f2fd2e4dca
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59234411"
---
### <a name="x509certificateclaimsetfindclaims-considers-all-claimtypes"></a>X509CertificateClaimSet.FindClaims Considers All claimTypes

|   |   |
|---|---|
|Podrobnosti|V aplikacích, které jsou cíleny rozhraní .NET Framework 4.6.1, pokud x X509 sady deklarací se inicializuje z certifikátu, který má několik záznamů DNS v jeho poli SAN <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims(System.String,System.String)?displayProperty=name> metoda se pokusí porovnat argument typu deklarace identity se všechny záznamy DNS. Pro aplikace, které cílí na předchozí verze rozhraní .NET Framework <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims(System.String,System.String)?displayProperty=name> metoda se pokusí porovnat argument typu deklarace identity jenom poslední položka DNS.|
|Doporučení|Tato změna ovlivní pouze aplikace, které cílí na rozhraní .NET Framework 4.6.1. Tato změna může zakázat (nebo povolit cílení pre-4.6.1) se [DisableMultipleDNSEntries](~/docs/framework/migration-guide/mitigation-x509certificateclaimset-findclaims-method.md#mitigation) přepínače kompatibility.|
|Rozsah|Vedlejší|
|Version|4.6.1|
|Type|Změna cílení|
|Ovlivněná rozhraní API|<ul><li><xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims(System.String,System.String)?displayProperty=nameWithType></li></ul>|
