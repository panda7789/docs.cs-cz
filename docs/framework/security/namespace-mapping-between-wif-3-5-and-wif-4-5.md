---
title: Mapování oborů názvů mezi WIF 3.5 a WIF 4.5
ms.date: 03/30/2017
ms.assetid: a092d98c-444d-4336-a644-63c2e11e96c8
author: BrucePerlerMS
ms.openlocfilehash: d967ce931e81ca14645e7464943e1411264d6ca2
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71045407"
---
# <a name="namespace-mapping-between-wif-35-and-wif-45"></a>Mapování oborů názvů mezi WIF 3.5 a WIF 4.5

Počínaje platformou .NET 4,5 se Windows Identity Foundation (WIF) plně integruje do .NET Framework. Tato integrace engendered změny názvu a některé konsolidace oborů názvů WIF a povrchu rozhraní API. Toto téma poskytuje některé doprovodné materiály a obecné mapování mezi obory názvů WIF 3,5 a obory názvů WIF 4,5. Není určena k vyčerpávajícímu použití, ale místo toho poskytuje obecné informace o tom, kde najít známé třídy WIF 3,5 v WIF 4,5. Podrobnější informace o rozdílech mezi WIF 3,5 a WIF 4,5 najdete v tématu [co je nového v systému Windows Identity Foundation 4,5](whats-new-in-wif.md). Pokyny, jak migrovat aplikace sestavené pomocí WIF 3,5 na WIF 4,5, najdete v tématu [pokyny pro migraci aplikace vytvořené pomocí WIF 3,5 na WIF 4,5](guidelines-for-migrating-an-application-built-using-wif-3-5-to-wif-4-5.md).

## <a name="wif-35-to-wif-45-namespace-map"></a>Mapování oboru názvů WIF 3,5 na WIF 4,5

Třídy WIF, které byly `Microsoft.IdentityModel` shromážděny pod obory názvů v WIF 3,5, jsou nyní distribuovány mezi následující obory názvů: `System.Security.Claims`, `System.IdentityModel` `System.ServiceModel.Security`a obory názvů v WIF 4,5. Kromě toho byly některé obory názvů WIF 3,5 konsolidovány nebo vyřazeny zcela v WIF 4,5.

> [!IMPORTANT]
> Následující `System.IdentityModel` obory názvů obsahují třídy, které implementují model identity založené na deklaracích <xref:System.IdentityModel.Policy?displayProperty=nameWithType>identity WCF <xref:System.IdentityModel.Selectors?displayProperty=nameWithType>: <xref:System.IdentityModel.Claims?displayProperty=nameWithType>, a. Model deklarovaných identit technologie WCF je nahrazen technologií WIF. Při sestavování řešení založených na WIF byste neměli v těchto třech oborech názvů používat třídy.

Následující tabulka poskytuje informace o tom, kde lze třídy WIF 3,5 najít v WIF 4,5.

|**Obor názvů WIF 3,5**|**Obor názvů WIF 4,5**|**Komentáře**|
|-|-|-|
|`Microsoft.IdentityModel`|<xref:System.IdentityModel?displayProperty=nameWithType>|-Většina tříd, které představují konstanty, není implementována.<br />– Třídy, které se používají k sestavení služeb tokenů zabezpečení, se přesunuly <xref:System.IdentityModel?displayProperty=nameWithType>z `Microsoft.IdentityModel.SecurityTokenService` na.<br />-Třídy v `Microsoft.IdentityModel.Threading` byly přesunuty do <xref:System.IdentityModel?displayProperty=nameWithType>.<br />– Třídy `MruSecurityTokenCache` a nejsou implementovány. `ExceptionMapper`|
|`Microsoft.IdentityModel.Claims`|<xref:System.Security.Claims?displayProperty=nameWithType>|– Rozhraní `IClaimsIdentity` a nejsou implementovaná v WIF 4,5. `IClaimsPrincipal` Místo <xref:System.Security.Claims.ClaimsPrincipal?displayProperty=nameWithType> toho <xref:System.Security.Claims.ClaimsIdentity?displayProperty=nameWithType> a jsou nyní základní třídy, ze kterých je odvozena většina objektů zabezpečení a třídy identity rozhraní .NET. To znamená, že nepotřebujete specializované objekty zabezpečení deklarací identity a třídy `Microsoft.IdentityModel.Claims.WindowsClaimsPrincipal` identity `Microsoft.IdentityModel.Claims.WindowsClaimsIdentity` , jako jsou a v <xref:System.Security.Principal.WindowsPrincipal?displayProperty=nameWithType> WIF <xref:System.Security.Principal.WindowsIdentity?displayProperty=nameWithType> 4,5, použijte a místo toho. Totéž platí pro jiné specializované objekty zabezpečení deklarací identity a třídy identit, které existovaly v WIF 3,5.<br />`Microsoft.IdentityModel.Claims.ClaimsCollection` – Třída není implementována v WIF 4,5. Místo toho se kolekce deklarací zveřejňují jako vyčíslitelné kolekce typu <xref:System.Security.Claims.Claim?displayProperty=nameWithType>.<br />-   <xref:System.Security.Claims.ClaimsPrincipal?displayProperty=nameWithType>a <xref:System.Security.Claims.ClaimsIdentity?displayProperty=nameWithType> poskytněte metody, které teď plně podporují LINQ.|
|`Microsoft.IdentityModel.Configuration`|<xref:System.IdentityModel.Configuration?displayProperty=nameWithType>|Některé prvky a třídy prošly změnami názvů a některé z nich byly vyřazeny v WIF 4,5; například `Microsoft.IdentityModel.Configuration.ServiceConfiguration` je nyní <xref:System.IdentityModel.Configuration.IdentityConfiguration?displayProperty=nameWithType>.|
|`Microsoft.IdentityModel.Protocols`|<xref:System.IdentityModel.Services?displayProperty=nameWithType>|-|
|`Microsoft.IdentityModel.Protocols.WSFederation`|<xref:System.IdentityModel.Services?displayProperty=nameWithType>|-|
|`Microsoft.IdentityModel.Protocols.WSFederation.Metadata`|<xref:System.IdentityModel.Metadata?displayProperty=nameWithType>|-|
|`Microsoft.IdentityModel.Protocols.WSIdentity`|Není implementováno v WIF 4,5|V WIF 3,5 obsahovalo třídy, které podporují službu CardSpace, není implementována v WIF 4,5.|
|`Microsoft.IdentityModel.Protocols.WSTrust`|Rozdělení mezi <xref:System.IdentityModel.Protocols.WSTrust?displayProperty=nameWithType> obory <xref:System.ServiceModel.Security?displayProperty=nameWithType> názvů a.|Třídy, které představují artefakty WS-Trust <xref:System.IdentityModel.Protocols.WSTrust?displayProperty=nameWithType> <xref:System.IdentityModel.Protocols.WSTrust.RequestSecurityToken> , jsou v oboru názvů, například třída. Třídy, které představují kontrakty služby WCF, hostitele služeb a kanály, které umožňují službě WCF komunikovat pomocí protokolu WS-Trust, jsou v <xref:System.ServiceModel.Security?displayProperty=nameWithType> oboru názvů, například <xref:System.ServiceModel.Security.WSTrustServiceHost> třída.|
|`Microsoft.IdentityModel.Protocols.WSTrust.Bindings`|Není implementováno v WIF 4,5|-|
|`Microsoft.IdentityModel.Protocols.XmlEncryption`|Není implementováno v WIF 4,5|Obsažené třídy, které reprezentují šifrovací konstanty XML v WIF 3,5. Tyto konstanty nejsou implementované v WIF 4,5.|
|`Microsoft.IdentityModel.Protocols.XmlSignature`|<xref:System.IdentityModel?displayProperty=nameWithType>|`EnvelopingSignature` Třída a třídy, které představují konstanty, nejsou implementovány.|
|`Microsoft.IdentityModel.SecurityTokenService`|Rozdělení mezi <xref:System.IdentityModel?displayProperty=nameWithType>obory <xref:System.IdentityModel.Protocols.WSTrust?displayProperty=nameWithType>názvů, <xref:System.IdentityModel.Tokens?displayProperty=nameWithType> a.|-|
|`Microsoft.IdentityModel.Threading`|<xref:System.IdentityModel?displayProperty=nameWithType>|-|
|`Microsoft.IdentityModel.Tokens`|<xref:System.IdentityModel.Tokens?displayProperty=nameWithType>|-|
|`Microsoft.IdentityModel.Tokens.Saml11`|<xref:System.IdentityModel.Tokens?displayProperty=nameWithType>|-|
|`Microsoft.IdentityModel.Tokens.Saml2`|<xref:System.IdentityModel.Tokens?displayProperty=nameWithType>|-|
|`Microsoft.IdentityModel.Web`|<xref:System.IdentityModel.Services?displayProperty=nameWithType>|-|
|`Microsoft.IdentityModel.Web.Configuration`|<xref:System.IdentityModel.Services.Configuration?displayProperty=nameWithType>|Třídy, které poskytují konfiguraci pro pasivní scénáře (WS-Federation), jsou do značné <xref:System.IdentityModel.Services.Configuration?displayProperty=nameWithType>míry přesunuty do; Nicméně některé z těchto <xref:System.IdentityModel.Services?displayProperty=nameWithType>tříd jsou v.|
|`Microsoft.IdentityModel.Web.Controls`|Není implementováno v WIF 4,5|Třídy v `Microsoft.IdentityModel.Web.Controls` rozhraní implementovaly federované pasivní ovládací prvek přihlášení, který v WIF 4,5 neexistuje.|
|`Microsoft.IdentityModel.WindowsTokenService`|Není implementováno v WIF 4,5|-|

## <a name="see-also"></a>Viz také:

- [Novinky ve Windows Workflow Foundation 4.5](whats-new-in-wif.md)
- [Pokyny k migraci aplikace sestavené pomocí WIF 3.5 na WIF 4.5](guidelines-for-migrating-an-application-built-using-wif-3-5-to-wif-4-5.md)
