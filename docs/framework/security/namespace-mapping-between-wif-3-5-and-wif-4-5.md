---
title: Namespace mapování mezi WIF 3.5 a WIF 4.5
ms.date: 03/30/2017
ms.assetid: a092d98c-444d-4336-a644-63c2e11e96c8
author: BrucePerlerMS
ms.openlocfilehash: ef5801ccfdda22b1c89c22ea9c2b14ea0855ed26
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57352786"
---
# <a name="namespace-mapping-between-wif-35-and-wif-45"></a>Namespace mapování mezi WIF 3.5 a WIF 4.5

Od verze rozhraní .NET 4.5, Windows Identity Foundation (WIF) má jsou plně integrované do rozhraní .NET Framework. Tato integrace očekávaným změn názvů a některé konsolidace oborech názvů WIF a rozhraní API. Toto téma obsahuje pokyny a obecné mapování mezi v oborech názvů WIF 3.5 a WIF 4.5 obory názvů. Není určena být důkladní, ale místo toho poskytuje některé obecné informace o tom, kde najít známé třídy technologie WIF 3.5 v technologie WIF 4.5. Podrobnější informace o rozdílech mezi verzemi WIF 3.5 a WIF 4.5 naleznete v tématu [co je nového ve Windows Identity Foundation 4.5](../../../docs/framework/security/whats-new-in-wif.md). Informace o tom, jak migrovat aplikace sestavené pomocí WIF 3.5 to WIF 4.5 naleznete v tématu [pokyny k migraci Application Built Using WIF 3.5 to WIF 4.5](../../../docs/framework/security/guidelines-for-migrating-an-application-built-using-wif-3-5-to-wif-4-5.md).

## <a name="wif-35-to-wif-45-namespace-map"></a>WIF 3.5 na WIF 4.5 Namespace mapy

Třídy technologie WIF, které byly shromážděny v části `Microsoft.IdentityModel` oborech názvů WIF 3.5, jsou nyní rozloženy mezi následující obory názvů: `System.Security.Claims`, `System.ServiceModel.Security`a `System.IdentityModel` obory názvů v technologie WIF 4.5. Kromě toho byly některé obory názvů WIF 3.5 konsolidovat nebo vyřadit zcela v technologie WIF 4.5.

> [!IMPORTANT]
> Následující `System.IdentityModel` obory názvů obsahují třídy, které implementují model deklarovaných identit WCF: <xref:System.IdentityModel.Claims?displayProperty=nameWithType>, <xref:System.IdentityModel.Policy?displayProperty=nameWithType>, a <xref:System.IdentityModel.Selectors?displayProperty=nameWithType>. Model deklarovaných identit technologie WCF je nahrazen technologií WIF. Při vytváření řešení založených na technologii WIF byste neměli používat třídy v těchto třech oborech názvů.

Následující tabulka obsahuje informace o třídy technologie WIF 3.5 kde lze nalézt v technologie WIF 4.5.

|**Technologie WIF 3.5 Namespace**|**Technologie WIF 4.5 Namespace**|**Komentáře**|
|-|-|-|
|`Microsoft.IdentityModel`|<xref:System.IdentityModel?displayProperty=nameWithType>|-Většina tříd, které představují konstanty nejsou implementovány.<br />-Tříd, které se používají k vytvoření služby tokenů zabezpečení byly přesunuté z `Microsoft.IdentityModel.SecurityTokenService` k <xref:System.IdentityModel?displayProperty=nameWithType>.<br />-Třídy v `Microsoft.IdentityModel.Threading` se přesunuly do <xref:System.IdentityModel?displayProperty=nameWithType>.<br />– `ExceptionMapper` a `MruSecurityTokenCache` třídy nejsou implementovány.|
|`Microsoft.IdentityModel.Claims`|<xref:System.Security.Claims?displayProperty=nameWithType>|– `IClaimsPrincipal` a `IClaimsIdentity` rozhraní implementovaná v technologie WIF 4.5. Místo toho <xref:System.Security.Claims.ClaimsPrincipal?displayProperty=nameWithType> a <xref:System.Security.Claims.ClaimsIdentity?displayProperty=nameWithType> jsou nyní základních tříd, z které většinu .NET objektu zabezpečení a identita třídy odvozovat. To znamená, že není nutné specializované deklarací identity objektu zabezpečení a identita třídy typu `Microsoft.IdentityModel.Claims.WindowsClaimsPrincipal` a `Microsoft.IdentityModel.Claims.WindowsClaimsIdentity` v technologie WIF 4.5, použijte <xref:System.Security.Principal.WindowsPrincipal?displayProperty=nameWithType> a <xref:System.Security.Principal.WindowsIdentity?displayProperty=nameWithType> místo. Totéž platí pro ostatní pro další specializované deklarace identity objektu zabezpečení a identita třídy, které existovaly ve technologie WIF 3.5.<br />– `Microsoft.IdentityModel.Claims.ClaimsCollection` Třída není implementovaná v technologie WIF 4.5. Místo toho kolekce deklarací, které jsou vystaveny jako vyčíslitelné kolekce typu <xref:System.Security.Claims.Claim?displayProperty=nameWithType>.<br />-   <xref:System.Security.Claims.ClaimsPrincipal?displayProperty=nameWithType> a <xref:System.Security.Claims.ClaimsIdentity?displayProperty=nameWithType> poskytují metody, které teď plně podporují LINQ.|
|`Microsoft.IdentityModel.Configuration`|<xref:System.IdentityModel.Configuration?displayProperty=nameWithType>|Některé elementy a třídy prošly změn názvů a některé byla vyřazena v technologie WIF 4.5; například `Microsoft.IdentityModel.Configuration.ServiceConfiguration` je nyní <xref:System.IdentityModel.Configuration.IdentityConfiguration?displayProperty=nameWithType>.|
|`Microsoft.IdentityModel.Protocols`|<xref:System.IdentityModel.Services?displayProperty=nameWithType>|-|
|`Microsoft.IdentityModel.Protocols.WSFederation`|<xref:System.IdentityModel.Services?displayProperty=nameWithType>|-|
|`Microsoft.IdentityModel.Protocols.WSFederation.Metadata`|<xref:System.IdentityModel.Metadata?displayProperty=nameWithType>|-|
|`Microsoft.IdentityModel.Protocols.WSIdentity`|Není implementováno technologie WIF 4.5|Technologie WIF 3.5 obsažené třídy pro podporu služby CardSpace, není implementován v technologie WIF 4.5.|
|`Microsoft.IdentityModel.Protocols.WSTrust`|Rozdělit mezi <xref:System.IdentityModel.Protocols.WSTrust?displayProperty=nameWithType> a <xref:System.ServiceModel.Security?displayProperty=nameWithType> obory názvů.|Třídy, které představují artefakty WS-Trust jsou v <xref:System.IdentityModel.Protocols.WSTrust?displayProperty=nameWithType> obor názvů, třeba <xref:System.IdentityModel.Protocols.WSTrust.RequestSecurityToken> třídy. Jsou třídy, které představují kontrakty služeb WCF, obsluha hostitelů a kanály, které umožňují komunikaci pomocí protokolu WS-Trust ve službě WCF <xref:System.ServiceModel.Security?displayProperty=nameWithType> obor názvů, třeba <xref:System.ServiceModel.Security.WSTrustServiceHost> třídy.|
|`Microsoft.IdentityModel.Protocols.WSTrust.Bindings`|Není implementováno technologie WIF 4.5|-|
|`Microsoft.IdentityModel.Protocols.XmlEncryption`|Není implementováno technologie WIF 4.5|Obsahuje třídy, které představují konstanty šifrování XML v technologie WIF 3.5. Tyto konstanty nejsou implementované v technologie WIF 4.5.|
|`Microsoft.IdentityModel.Protocols.XmlSignature`|<xref:System.IdentityModel?displayProperty=nameWithType>|`EnvelopingSignature` Třídy a třídy, které představují konstanty nejsou implementovány.|
|`Microsoft.IdentityModel.SecurityTokenService`|Rozdělit mezi <xref:System.IdentityModel?displayProperty=nameWithType>, <xref:System.IdentityModel.Protocols.WSTrust?displayProperty=nameWithType>, a <xref:System.IdentityModel.Tokens?displayProperty=nameWithType> obory názvů.|-|
|`Microsoft.IdentityModel.Threading`|<xref:System.IdentityModel?displayProperty=nameWithType>|-|
|`Microsoft.IdentityModel.Tokens`|<xref:System.IdentityModel.Tokens?displayProperty=nameWithType>|-|
|`Microsoft.IdentityModel.Tokens.Saml11`|<xref:System.IdentityModel.Tokens?displayProperty=nameWithType>|-|
|`Microsoft.IdentityModel.Tokens.Saml2`|<xref:System.IdentityModel.Tokens?displayProperty=nameWithType>|-|
|`Microsoft.IdentityModel.Web`|<xref:System.IdentityModel.Services?displayProperty=nameWithType>|-|
|`Microsoft.IdentityModel.Web.Configuration`|<xref:System.IdentityModel.Services.Configuration?displayProperty=nameWithType>|Třídy, které poskytují konfiguraci pro pasivní scénáře (WS-Federation), do značné míry byly přesunuty do <xref:System.IdentityModel.Services.Configuration?displayProperty=nameWithType>, nicméně některé z těchto tříd jsou v <xref:System.IdentityModel.Services?displayProperty=nameWithType>.|
|`Microsoft.IdentityModel.Web.Controls`|Není implementováno technologie WIF 4.5|Třídy v `Microsoft.IdentityModel.Web.Controls` implementované federované pasivní přihlášení ovládacího prvku, který neexistuje v technologie WIF 4.5.|
|`Microsoft.IdentityModel.WindowsTokenService`|Není implementováno technologie WIF 4.5|-|

## <a name="see-also"></a>Viz také:

- [Novinky ve Windows Workflow Foundation 4.5](../../../docs/framework/security/whats-new-in-wif.md)
- [Pokyny k migraci aplikace sestavené pomocí WIF 3.5 na WIF 4.5](../../../docs/framework/security/guidelines-for-migrating-an-application-built-using-wif-3-5-to-wif-4-5.md)
