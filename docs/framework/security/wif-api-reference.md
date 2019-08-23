---
title: Referenční dokumentace k rozhraní API WIF
ms.date: 03/30/2017
ms.assetid: a027d902-9314-4bfd-b172-4e81847b1d68
author: BrucePerlerMS
ms.openlocfilehash: 17a1da0a3b0ea6567fd805e7273f793ace35ae69
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69958348"
---
# <a name="wif-api-reference"></a>Referenční dokumentace k rozhraní API WIF
Třídy Windows Identity Foundation (WIF) jsou rozdělené mezi následující sestavení: `mscorlib` (mscorlib. dll), `System.IdentityModel` (System. IdentityModel. dll), `System.IdentityModel.Services` (System. IdentityModel. Services. dll) a `System.ServiceModel` ( System. ServiceModel. dll). Toto téma obsahuje odkazy na obory názvů WIF a stručné vysvětlení tříd, které obsahují jednotlivé obory názvů.  
  
> [!IMPORTANT]
> Následující `System.IdentityModel` obory názvů obsahují třídy, které implementují model identity založené na deklaracích <xref:System.IdentityModel.Policy?displayProperty=nameWithType>identity WCF <xref:System.IdentityModel.Selectors?displayProperty=nameWithType>: <xref:System.IdentityModel.Claims?displayProperty=nameWithType>, a. Počínaje .NET Framework 4,5 se model identity založený na deklaracích identity WCF nahrazuje WIF. Při sestavování řešení založených na WIF byste neměli v těchto třech oborech názvů používat třídy.  
  
 <xref:System.IdentityModel?displayProperty=nameWithType>  
 Obsahuje třídy, které reprezentují transformační soubory souborů cookie, služby tokenů zabezpečení a specializované čtečky slovníku XML.  
  
 <xref:System.IdentityModel.Configuration?displayProperty=nameWithType>  
 Obsahuje třídy, které poskytují konfiguraci pro aplikace a služby sestavené pomocí rozhraní Windows Identity Foundation (WIF). Třídy v tomto oboru názvů reprezentují nastavení v rámci [ \<elementu IdentityConfiguration >](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) .  
  
 <xref:System.IdentityModel.Metadata?displayProperty=nameWithType>  
 Obsahuje třídy, které reprezentují elementy v dokumentu federačních metadat.  
  
 <xref:System.IdentityModel.Protocols.WSTrust?displayProperty=nameWithType>  
 Obsahuje třídy, které reprezentují artefakty WS-Trust.  
  
 <xref:System.IdentityModel.Services?displayProperty=nameWithType>  
 Obsahuje třídy, které se používají v pasivních scénářích (WS-Federation). Obsahuje také některé třídy, které reprezentují nastavení pod [ \<> element System. IdentityModel. Services](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel-services.md) . Nastavení pod tímto prvkem konfigurují pro aplikace WS-Federation. `System.IdentityModel.Services.Configuration` Obor názvů obsahuje většinu tříd, které se používají ke konfiguraci WS-Federation.  
  
 <xref:System.IdentityModel.Services.Configuration?displayProperty=nameWithType>  
 Obsahuje třídy, které poskytují konfiguraci pro aplikace WIF používající protokol WS-Federation. Třídy v tomto oboru názvů reprezentují nastavení v rámci [ \<prvku System. IdentityModel. Services >](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel-services.md) . `System.IdentityModel.Services` Obor názvů také obsahuje některé třídy, které se používají ke konfiguraci protokolu WS-Federation.  
  
 <xref:System.IdentityModel.Services.Tokens?displayProperty=nameWithType>  
 Obsahuje obslužné rutiny specializovaného tokenu zabezpečení pro scénáře webové farmy.  
  
 <xref:System.IdentityModel.Tokens?displayProperty=nameWithType>  
 Obsahuje třídy, které reprezentují tokeny zabezpečení, obslužné rutiny tokenů zabezpečení a další artefakty tokenů zabezpečení.  
  
 <xref:System.Security.Claims?displayProperty=nameWithType>  
 Obsahuje třídy, které reprezentují deklarace identity, identity založené na deklaracích, objekty zabezpečení založené na deklaracích a další artefakty modelu identity založené na deklaracích.  
  
 <xref:System.ServiceModel.Security?displayProperty=nameWithType>  
 Obsahuje třídy, které představují kontrakty WCF, kanály, hostitele služeb a jiné artefakty, které se používají ve scénářích aktivních (WS-Trust). Tento obor názvů obsahuje také třídy, které jsou specifické pro Windows Communication Foundation (WCF) a které nepoužívá WIF.  
  
## <a name="see-also"></a>Viz také:

- [Referenční dokumentace ke konfiguraci WIF](../../../docs/framework/security/wif-configuration-reference.md)
- [Mapování oborů názvů mezi WIF 3.5 a WIF 4.5](../../../docs/framework/security/namespace-mapping-between-wif-3-5-and-wif-4-5.md)
