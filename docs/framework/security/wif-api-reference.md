---
title: Referenční dokumentace rozhraní API WIF
ms.date: 03/30/2017
ms.assetid: a027d902-9314-4bfd-b172-4e81847b1d68
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: f5a38420cf5ddb0a76946d5e44e98e1f39118236
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="wif-api-reference"></a>Referenční dokumentace rozhraní API WIF
Třídy Windows Identity Foundation (WIF) jsou rozdělit do následujících sestavení: `mscorlib` (mscorlib.dll), `System.IdentityModel` (System.IdentityModel.dll), `System.IdentityModel.Services` (System.IdentityModel.Services.dll), a `System.ServiceModel` () System.ServiceModel.dll). Toto téma obsahuje odkazy na obory názvů WIF a stručné vysvětlení tříd, které obsahuje každý obor názvů.  
  
> [!IMPORTANT]
>  Následující `System.IdentityModel` obory názvů obsahuje třídy, které implementují modelu WCF na základě deklarace identity: <xref:System.IdentityModel.Claims?displayProperty=nameWithType>, <xref:System.IdentityModel.Policy?displayProperty=nameWithType>, a <xref:System.IdentityModel.Selectors?displayProperty=nameWithType>. Od verze rozhraní .NET Framework 4.5, je WIF nahrazen modelu WCF na základě deklarace identity. Při sestavování řešení založená na verzi WIF byste neměli používat třídy v tyto tři obory názvů.  
  
 <xref:System.IdentityModel?displayProperty=nameWithType>  
 Obsahuje třídy, které představují transformace souborů cookie, služby tokenů zabezpečení a specializované slovník čtečky XML.  
  
 <xref:System.IdentityModel.Configuration?displayProperty=nameWithType>  
 Obsahuje třídy, které poskytují konfiguraci pro aplikace a služby vytvořená s využitím Windows Identity Foundation (WIF). Nastavení v části představují třídy v tomto oboru názvů [ \<identityConfiguration >](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) element.  
  
 <xref:System.IdentityModel.Metadata?displayProperty=nameWithType>  
 Obsahuje třídy, které představují prvky v dokument federačních metadat.  
  
 <xref:System.IdentityModel.Protocols.WSTrust?displayProperty=nameWithType>  
 Obsahuje třídy, které představují WS-Trust artefakty.  
  
 <xref:System.IdentityModel.Services?displayProperty=nameWithType>  
 Obsahuje třídy, které se používají ve scénářích pasivní (WS-Federation). Také obsahuje některé třídy, které představují nastavení v části [ \<system.identityModel.services >](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel-services.md) element. Nastavení v části Tento element konfigurace služby WS-Federation pro aplikace. `System.IdentityModel.Services.Configuration` Obor názvů obsahuje třídy, které se používají ke konfiguraci služby WS-Federation.  
  
 <xref:System.IdentityModel.Services.Configuration?displayProperty=nameWithType>  
 Obsahuje třídy, které poskytují konfiguraci pro WIF aplikace, které používají protokol WS-Federation. Nastavení v části představují třídy v tomto oboru názvů [ \<system.identityModel.services >](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel-services.md) element. `System.IdentityModel.Services` Obor názvů obsahuje také některé třídy, které se používají ke konfiguraci služby WS-Federation.  
  
 <xref:System.IdentityModel.Services.Tokens?displayProperty=nameWithType>  
 Obsahuje tokenů obslužné rutiny specializované zabezpečení pro webové farmy scénáře.  
  
 <xref:System.IdentityModel.Tokens?displayProperty=nameWithType>  
 Obsahuje třídy, které představují tokeny zabezpečení, obslužné rutiny tokenu zabezpečení a artefaktů tokenu zabezpečení.  
  
 <xref:System.Security.Claims?displayProperty=nameWithType>  
 Obsahuje třídy, které představují deklarace identity, na základě deklarace identity, na základě deklarace objektů a artefaktů modelu na základě deklarace identity.  
  
 <xref:System.ServiceModel.Security?displayProperty=nameWithType>  
 Obsahuje třídy, které představují WCF kontrakty, kanály, hostitelé služeb a jiných artefaktů, které se používají ve scénářích active (WS-Trust). Tento obor názvů také obsahuje třídy, které jsou specifické pro Windows Communication Foundation (WCF) a které nejsou používána WIF.  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace ke konfiguraci WIF](../../../docs/framework/security/wif-configuration-reference.md)  
 [Mapování oborů názvů mezi WIF 3.5 a WIF 4.5](../../../docs/framework/security/namespace-mapping-between-wif-3-5-and-wif-4-5.md)
