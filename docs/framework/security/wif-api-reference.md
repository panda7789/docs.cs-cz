---
title: Referenční dokumentace k rozhraní API WIF
ms.date: 03/30/2017
ms.assetid: a027d902-9314-4bfd-b172-4e81847b1d68
author: BrucePerlerMS
ms.openlocfilehash: c94ccd3f25be576c57fda798c6b2b8cc25357022
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59172208"
---
# <a name="wif-api-reference"></a>Referenční dokumentace k rozhraní API WIF
Třídy technologie Windows Identity Foundation (WIF) se rozdělit mezi následující sestavení: `mscorlib` (mscorlib.dll) `System.IdentityModel` (System.IdentityModel.dll) `System.IdentityModel.Services` (System.IdentityModel.Services.dll), a `System.ServiceModel` () System.ServiceModel.dll). Toto téma obsahuje odkazy na obory názvů WIF a stručné vysvětlení tříd, které obsahuje každý obor názvů.  
  
> [!IMPORTANT]
>  Následující `System.IdentityModel` obory názvů obsahují třídy, které implementují model deklarovaných identit WCF: <xref:System.IdentityModel.Claims?displayProperty=nameWithType>, <xref:System.IdentityModel.Policy?displayProperty=nameWithType>, a <xref:System.IdentityModel.Selectors?displayProperty=nameWithType>. Od verze rozhraní .NET Framework 4.5, model deklarovaných identit WCF je nahrazen technologií WIF. Při vytváření řešení založených na technologii WIF byste neměli používat třídy v těchto třech oborech názvů.  
  
 <xref:System.IdentityModel?displayProperty=nameWithType>  
 Obsahuje třídy, které představují transformace souborů cookie, služby tokenu zabezpečení a specializované čtenáře slovníku XML.  
  
 <xref:System.IdentityModel.Configuration?displayProperty=nameWithType>  
 Obsahuje třídy, které poskytují konfiguraci aplikací a služeb vytvořených pomocí technologie Windows Identity Foundation (WIF). Nastavení v části představují třídy v tomto oboru názvů [ \<identityConfiguration >](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) elementu.  
  
 <xref:System.IdentityModel.Metadata?displayProperty=nameWithType>  
 Obsahuje třídy představující prvky v dokumentu federačních metadat.  
  
 <xref:System.IdentityModel.Protocols.WSTrust?displayProperty=nameWithType>  
 Obsahuje třídy, které reprezentují artefakty WS-Trust.  
  
 <xref:System.IdentityModel.Services?displayProperty=nameWithType>  
 Obsahuje třídy, které se používají ve scénářích pasivní (WS-Federation). Obsahuje také některé třídy, které představují v nastavení [ \<system.identityModel.services >](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel-services.md) elementu. Nastavení v části Tento prvek konfigurace WS-Federation pro aplikace. `System.IdentityModel.Services.Configuration` Obor názvů obsahuje třídy, které se používají ke konfiguraci WS-Federation.  
  
 <xref:System.IdentityModel.Services.Configuration?displayProperty=nameWithType>  
 Obsahuje třídy, které poskytují konfiguraci technologie WIF aplikace, které používají protokol WS-Federation. Nastavení v části představují třídy v tomto oboru názvů [ \<system.identityModel.services >](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel-services.md) elementu. `System.IdentityModel.Services` Obor názvů také obsahuje některé třídy, které se používají ke konfiguraci WS-Federation.  
  
 <xref:System.IdentityModel.Services.Tokens?displayProperty=nameWithType>  
 Obsahuje obslužné rutiny tokenů zabezpečení specializované webových farem.  
  
 <xref:System.IdentityModel.Tokens?displayProperty=nameWithType>  
 Obsahuje třídy, které představují tokeny zabezpečení, obslužné rutiny tokenů zabezpečení a další artefakty tokenu zabezpečení.  
  
 <xref:System.Security.Claims?displayProperty=nameWithType>  
 Obsahuje třídy, které představují deklarace identity, založené na deklaracích identity, objekty zabezpečení založené na deklaracích a další artefakty model deklarovaných identit.  
  
 <xref:System.ServiceModel.Security?displayProperty=nameWithType>  
 Obsahuje třídy, které představují WCF kontrakty, kanály, obsluha hostitelů a další artefakty, které se používají ve scénářích aktivní (WS-Trust). Tento obor názvů také obsahuje třídy, které jsou specifické pro Windows Communication Foundation (WCF) a které nejsou používány technologie WIF.  
  
## <a name="see-also"></a>Viz také:

- [Referenční dokumentace ke konfiguraci WIF](../../../docs/framework/security/wif-configuration-reference.md)
- [Mapování oborů názvů mezi WIF 3.5 a WIF 4.5](../../../docs/framework/security/namespace-mapping-between-wif-3-5-and-wif-4-5.md)
