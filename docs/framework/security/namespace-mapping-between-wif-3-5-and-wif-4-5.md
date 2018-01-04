---
title: "Namespace mapování mezi WIF 3.5 a WIF 4.5"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a092d98c-444d-4336-a644-63c2e11e96c8
caps.latest.revision: "4"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: b8d27385a08c58c61983315da41f27f4dcb29368
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="namespace-mapping-between-wif-35-and-wif-45"></a>Namespace mapování mezi WIF 3.5 a WIF 4.5
Od verze rozhraní .NET 4.5, Windows Identity Foundation (WIF) byla plně integrována do rozhraní .NET Framework. Tato integrace očekávaným na změny názvu a některé konsolidace WIF obory názvů a prostor pro rozhraní API. Toto téma obsahuje některé pokyny a obecné mapování mezi obory názvů WIF 3.5 a obory názvů WIF 4.5. Rozhraní není určeno vyčerpávající, ale místo poskytují některé obecné informace o tom, kde najít známé třídy WIF 3.5 v WIF 4.5. Podrobné informace o rozdílech mezi WIF 3.5 a WIF 4.5, najdete v části [co je nového ve Windows Identity Foundation 4.5](../../../docs/framework/security/whats-new-in-wif.md). Informace o tom, jak migrovat aplikace sestavené pomocí WIF 3.5 na verzi WIF 4.5, najdete v části [pokyny pro migraci aplikaci vytvořené pomocí WIF 3.5 na verzi WIF 4.5](../../../docs/framework/security/guidelines-for-migrating-an-application-built-using-wif-3-5-to-wif-4-5.md).  
  
## <a name="wif-35-to-wif-45-namespace-map"></a>WIF 3.5 WIF 4.5 Namespace mapy  
 WIF třídy, které byly shromážděny v části `Microsoft.IdentityModel` obory názvů v WIF 3.5, jsou teď rozdělené mezi následujících oborů názvů: `System.Security.Claims`, `System.ServiceModel.Security`a `System.IdentityModel` obory názvů v WIF 4.5. Kromě toho některé obory názvů WIF 3.5 byly konsolidovány nebo vyřadit zcela v WIF 4.5.  
  
> [!IMPORTANT]
>  Následující `System.IdentityModel` obory názvů obsahuje třídy, které implementují modelu WCF na základě deklarace identity: <xref:System.IdentityModel.Claims?displayProperty=nameWithType>, <xref:System.IdentityModel.Policy?displayProperty=nameWithType>, a <xref:System.IdentityModel.Selectors?displayProperty=nameWithType>. Model deklarovaných identit technologie WCF je nahrazen technologií WIF. Při sestavování řešení založená na verzi WIF byste neměli používat třídy v tyto tři obory názvů.  
  
 Následující tabulka obsahuje informace o kde třídy WIF 3.5 najdete v WIF 4.5.  
  
|**WIF 3.5 Namespace**|**WIF 4.5 Namespace**|**Komentáře**|  
|-|-|-|  
|`Microsoft.IdentityModel`|<xref:System.IdentityModel?displayProperty=nameWithType>|-Nejsou implementované Většina tříd, které představují konstanty.<br />-Třídy, které se používají k vytvoření služby tokenů zabezpečení byly přesunuté z `Microsoft.IdentityModel.SecurityTokenService` k <xref:System.IdentityModel?displayProperty=nameWithType>.<br />-Třídy v `Microsoft.IdentityModel.Threading` byl přesunut do <xref:System.IdentityModel?displayProperty=nameWithType>.<br />-Na `ExceptionMapper` a `MruSecurityTokenCache` nejsou implementované třídy.|  
|`Microsoft.IdentityModel.Claims`|<xref:System.Security.Claims?displayProperty=nameWithType>|-Na `IClaimsPrincipal` a `IClaimsIdentity` rozhraní nejsou implementované v WIF 4.5. Místo toho <xref:System.Security.Claims.ClaimsPrincipal?displayProperty=nameWithType> a <xref:System.Security.Claims.ClaimsIdentity?displayProperty=nameWithType> jsou teď základní třídy, ze které většina .NET hlavní a odvození třídy identity. To znamená, že není nutné specializované deklarací identity zabezpečení a identity třídy jako `Microsoft.IdentityModel.Claims.WindowsClaimsPrincipal` a `Microsoft.IdentityModel.Claims.WindowsClaimsIdentity` v WIF 4.5, použijte <xref:System.Security.Principal.WindowsPrincipal?displayProperty=nameWithType> a <xref:System.Security.Principal.WindowsIdentity?displayProperty=nameWithType> místo. Totéž platí pro ostatní pro jiné specializované deklarací identity zabezpečení a identity třídy, které existovalo v WIF 3.5.<br />-Na `Microsoft.IdentityModel.Claims.ClaimsCollection` třída není implementována v WIF 4.5. Místo toho kolekce deklarace identity jsou zveřejněné jako vyčíslitelná kolekce typu <xref:System.Security.Claims.Claim?displayProperty=nameWithType>.<br />-   <xref:System.Security.Claims.ClaimsPrincipal?displayProperty=nameWithType>a <xref:System.Security.Claims.ClaimsIdentity?displayProperty=nameWithType> poskytují metody, které teď plně podporují LINQ.|  
|`Microsoft.IdentityModel.Configuration`|<xref:System.IdentityModel.Configuration?displayProperty=nameWithType>|Některé elementy a třídy prošly změny názvu a některé byla vyřazena v WIF 4.5; například `Microsoft.IdentityModel.Configuraiton.ServiceConfiguration` je nyní <xref:System.IdentityModel.Configuration.IdentityConfiguration?displayProperty=nameWithType>.|  
|`Microsoft.IdentityModel.Protocols`|<xref:System.IdentityModel.Services?displayProperty=nameWithType>|-|  
|`Microsoft.IdentityModel.Protocols.WSFederation`|<xref:System.IdentityModel.Services?displayProperty=nameWithType>|-|  
|`Microsoft.IdentityModel.Protocols.WSFederation.Metadata`|<xref:System.IdentityModel.Metadata?displayProperty=nameWithType>|-|  
|`Microsoft.IdentityModel.Protocols.WSIdentity`|Není implementováno v WIF 4.5|V WIF 3.5 obsahuje třídy pro podporu CardSpace, není implementována v WIF 4.5.|  
|`Microsoft.IdentityModel.Protocols.WSTrust`|Rozdělit <xref:System.IdentityModel.Protocols.WSTrust?displayProperty=nameWithType> a <xref:System.ServiceModel.Security?displayProperty=nameWithType> obory názvů.|Třídy, které představují WS-Trust artefakty jsou v <xref:System.IdentityModel.Protocols.WSTrust?displayProperty=nameWithType> obor názvů, například <xref:System.IdentityModel.Protocols.WSTrust.RequestSecurityToken> třídy. Třídy, které představují kontraktů služby WCF, hostitelé služeb a kanály, které umožňují služby WCF na komunikaci pomocí protokolu WS-Trust jsou v <xref:System.ServiceModel.Security?displayProperty=nameWithType> obor názvů, například <xref:System.ServiceModel.Security.WSTrustServiceHost> třídy.|  
|`Microsoft.IdentityModel.Protocols.WSTrust.Bindings`|Není implementováno v WIF 4.5|-|  
|`Microsoft.IdentityModel.Protocols.XmlEncryption`|Není implementováno v WIF 4.5|Obsahuje třídy, které představují konstanty XML – šifrování v WIF 3.5. Tyto konstanty nejsou implementované v WIF 4.5.|  
|`Microsoft.IdentityModel.Protocols.XmlSignature`|<xref:System.IdentityModel?displayProperty=nameWithType>|`EnvelopingSignature` Nejsou implementované třídy a třídy představující konstanty.|  
|`Microsoft.IdentityModel.SecurityTokenService`|Rozdělit <xref:System.IdentityModel?displayProperty=nameWithType>, <xref:System.IdentityModel.Protocols.WSTrust?displayProperty=nameWithType>, a <xref:System.IdentityModel.Tokens?displayProperty=nameWithType> obory názvů.|-|  
|`Microsoft.IdentityModel.Threading`|<xref:System.IdentityModel?displayProperty=nameWithType>|-|  
|`Microsoft.IdentityModel.Tokens`|<xref:System.IdentityModel.Tokens?displayProperty=nameWithType>|-|  
|`Microsoft.IdentityModel.Tokens.Saml11`|<xref:System.IdentityModel.Tokens?displayProperty=nameWithType>|-|  
|`Microsoft.IdentityModel.Tokens.Saml2`|<xref:System.IdentityModel.Tokens?displayProperty=nameWithType>|-|  
|`Microsoft.IdentityModel.Web`|<xref:System.IdentityModel.Services?displayProperty=nameWithType>|-|  
|`Microsoft.IdentityModel.Web.Configuration`|<xref:System.IdentityModel.Services.Configuration?displayProperty=nameWithType>|Třídy, které poskytují konfiguraci pro scénáře pasivní (WS-Federation), z velké části byly přesunuty do <xref:System.IdentityModel.Services.Configuration?displayProperty=nameWithType>, nicméně některé z těchto tříd jsou v <xref:System.IdentityModel.Services?displayProperty=nameWithType>.|  
|`Microsoft.IdentityModel.Web.Controls`|Není implementováno v WIF 4.5|Třídy v `Microsoft.IdentityModel.Web.Controls` implementována federovaný pasivní přihlášení ovládací prvek, který neexistuje v WIF 4.5.|  
|`Microsoft.IdentityModel.WindowsTokenService`|Není implementováno v WIF 4.5|-|  
  
## <a name="see-also"></a>Viz také  
 [Novinky ve Windows Workflow Foundation 4.5](../../../docs/framework/security/whats-new-in-wif.md)  
 [Pokyny k migraci aplikace sestavené pomocí WIF 3.5 na WIF 4.5](../../../docs/framework/security/guidelines-for-migrating-an-application-built-using-wif-3-5-to-wif-4-5.md)
