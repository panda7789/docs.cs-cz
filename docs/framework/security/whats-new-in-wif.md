---
title: Novinky ve Windows Identity Foundation 4.5
ms.date: 03/30/2017
ms.assetid: 3b381f04-593b-471f-bd33-0362be1aade5
author: BrucePerlerMS
ms.openlocfilehash: 93631c1171f81ec8b8d94b56a56012343f6c3220
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71045282"
---
# <a name="whats-new-in-windows-identity-foundation-45"></a>Novinky ve Windows Identity Foundation 4.5
První verze technologie Windows Identity Foundation (WIF) byla uvedena na trh jako samostatný produkt ke stažení a je známa pod označením WIF 3.5, protože byla uvedena ve stejném období jako technologie .NET 3.5 SP1. Počínaje verzí .NET 4.5 je technologie WIF součástí rozhraní .NET Framework. Třídy WIF přímo dostupné v rozhraní umožňují mnohem hlubší integraci identity založené na deklaracích v rozhraní .NET, což usnadňuje používání deklarací identity. Aplikace napsané pro WIF 3,5 se musí upravit, aby mohli využívat nový model. informace najdete v tématu [pokyny pro migraci aplikace sestavené pomocí WIF 3,5 na WIF 4,5](guidelines-for-migrating-an-application-built-using-wif-3-5-to-wif-4-5.md).  
  
 Následuje přehled některých hlavních změn.  
  
## <a name="wif-is-now-part-of-the-net-framework"></a>Technologie WIF je nyní součástí rozhraní .NET Framework  
 Třídy WIF `mscorlib`jsou nyní rozloženy mezi několik sestavení, hlavní objekty jsou, `System.IdentityModel`, `System.IdentityModel.Services`a. `System.ServiceModel` Podobně třídy WIF jsou rozloženy mezi několik oborů názvů: <xref:System.Security.Claims?displayProperty=nameWithType>, několika obory názvů [System. IdentityModel](https://go.microsoft.com/fwlink/?LinkId=272004) a <xref:System.ServiceModel.Security?displayProperty=nameWithType>. Obor názvů obsahuje nové <xref:System.Security.Claims.ClaimsPrincipal> třídy a <xref:System.Security.Claims.ClaimsIdentity> (viz níže). <xref:System.Security.Claims?displayProperty=nameWithType> Všechny objekty zabezpečení v rozhraní .NET jsou nyní <xref:System.Security.Claims.ClaimsPrincipal>odvozeny od. Podrobnější informace o oborech názvů WIF a typech tříd, které obsahují, najdete v tématu [Reference k rozhraní WIF API](wif-api-reference.md). Informace o tom, jak se obory názvů mapují mezi WIF 3,5 a WIF 4,5, najdete v tématu [mapování oboru názvů mezi WIF 3,5 a WIF 4,5](namespace-mapping-between-wif-3-5-and-wif-4-5.md).  
  
## <a name="new-claims-model-and-principal-object"></a>Nový model a objekt zabezpečení založený na deklaracích  
 Deklarace jsou v samotném jádru rozhraní .NET Framework 4.5. Základní třídy deklarace identity (<xref:System.Security.Claims.Claim>, <xref:System.Security.Claims.ClaimsIdentity>, <xref:System.Security.Claims.ClaimsPrincipal> <xref:System.Security.Claims.ClaimTypes>, a <xref:System.Security.Claims.ClaimValueTypes>) jsou všechny přímo v `mscorlib` <xref:System.Security.Claims?displayProperty=nameWithType> oboru názvů. Už nemusíte používat rozhraní, aby bylo možné zasílat deklarace do systému identit .NET: <xref:System.Security.Principal.WindowsPrincipal>, <xref:System.Security.Principal.GenericPrincipal>a <xref:System.Security.Principal.WindowsIdentity> <xref:System.Web.Security.FormsIdentity> <xref:System.Web.Security.RolePrincipal> teď dědí z <xref:System.Security.Claims.ClaimsPrincipal>, a teď dědí <xref:System.Security.Principal.GenericIdentity>. z <xref:System.Security.Claims.ClaimsIdentity>. Stručně řečeno, všechny třídy objektů zabezpečení nyní budou poskytovat deklarace. Rozhraní a integrační třídy WIF 3,5`WindowsClaimsIdentity`(, `WindowsClaimsPrincipal`, `IClaimsPrincipal`, `IClaimsIdentity`) byly proto odebrány. Kromě toho <xref:System.Security.Claims.ClaimsIdentity> třída nyní zveřejňuje metody, které usnadňují dotazování kolekce deklarací identity.  
  
## <a name="changes-to-the-wif-45-visual-studio-experience"></a>Změny v používání technologie WIF 4.5 v prostředí sady Visual Studio  
  
- **Přidat odkaz na STS...** Funkce Visual studia (cmdline Utility soubor FedUtil) už neexistuje. místo toho můžete použít nový **Nástroj identita a přístup k rozšíření sady Visual Studio pro Visual studio 2012**. To umožňuje federaci s existující službou tokenů zabezpečení (STS). Svá řešení můžete také testovat s použitím místní služby tokenů zabezpečení LocalSTS. Po instalaci rozšíření můžete kliknout pravým tlačítkem na projekt a vyhledat **identitu a přístup** v místní nabídce.  
  
- Šablony technologie ASP.NET a služby STS již nejsou k dispozici, protože deklarace je možné používat přímo v existujících šablonách projektů pro technologii ASP.NET, weby a technologii WCF.  
  
- Ovládací prvky v `Microsoft.IdentityModel.Web.Controls` oboru názvů (`SignInControl`, `FederatedPassiveSignInControl` `FederatedPassiveSignInStatus`a) nejsou převedené do WIF 4,5.  
  
## <a name="changes-to-the-wif-45-api"></a>Změny v rozhraní API technologie WIF 4.5  
  
- Obecně platí, že <xref:System.Security.Claims?displayProperty=nameWithType> třídy související s deklaracemi jsou v oboru názvů; Třídy související s WCF – kontrakty služby, kanály, továrny kanálů a hostitelé služeb, které se používají pro scénáře WS-Trust – jsou <xref:System.ServiceModel.Security?displayProperty=nameWithType>v nástroji a všechny ostatní třídy WIF jsou rozdělené mezi různé obory názvů [System. IdentityModel](https://go.microsoft.com/fwlink/?LinkId=272004) – patří mezi ně například třídy, které reprezentují artefakty WS-* a SAML, obslužné rutiny tokenů a související třídy a třídy používané ve scénářích WS-Federation. Další informace najdete v tématu [mapování oboru názvů mezi WIF 3,5 a](namespace-mapping-between-wif-3-5-and-wif-4-5.md) [referenční informace k rozhraní API](wif-api-reference.md)WIF 4,5 a WIF.  
  
- Bylo povoleno používání klíče počítače v souborech cookie relací při používání webových farem. Další informace najdete v tématu [WIF and Web Farms](wif-and-web-farms.md).  
  
- Nyní můžete deklarativně nakonfigurovat WIF v rámci [ \<> prvků System. IdentityModel >](../configure-apps/file-schema/windows-identity-foundation/system-identitymodel.md) a [ \<System. IdentityModel. Services](../configure-apps/file-schema/windows-identity-foundation/system-identitymodel-services.md) . Další informace o konfiguraci WIF najdete v článku [referenční informace o konfiguraci WIF](wif-configuration-reference.md).  
  
## <a name="other-notable-net-changes-or-features-that-are-caused-by-the-integration-of-wif-into-net"></a>Další významné změny technologie .NET nebo funkce způsobené začleněním technologie WIF do technologie .NET  
  
- Možnost autorizace na základě deklarované identity (CBAC) je nyní součástí rozhraní .NET Framework. Můžete nakonfigurovat <xref:System.Security.Claims.ClaimsAuthorizationManager> objekt a potom <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> použít třídy a <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> k provedení imperativních a deklarativních kontrol přístupu ve vašem kódu. Autorizace CBAC poskytuje větší flexibilitu a přesnost než tradiční kontroly přístupu na základě rolí (RBAC). Umožňuje taky větší oddělení zásad autorizace od obchodní logiky, protože obchodní logika může založit kontrolu přístupu u konkrétní deklarace identity nebo sady deklarací identity a zásady autorizace pro tyto deklarace se dají konfigurovat deklarativně v rámci [ claimsAuthorizationManager\<prvek >](../configure-apps/file-schema/windows-identity-foundation/claimsauthorizationmanager.md) .  
  
## <a name="wcf-changes-as-a-result-of-wif-integration"></a>Změny v technologii WCF v důsledku integrace technologie WIF:  
  
- Model deklarovaných identit technologie WCF je nahrazen technologií WIF. To znamená, že třídy v <xref:System.IdentityModel.Claims?displayProperty=nameWithType>oborech názvů <xref:System.IdentityModel.Selectors?displayProperty=nameWithType> , <xref:System.IdentityModel.Policy?displayProperty=nameWithType>a by měly být vyřazeny z použití tříd WIF.  
  
- Služba WIF je nyní povolena ve službě WCF zadáním `useIdentityConfiguration` atributu `<system.serviceModel>` `<behaviors>` / `<serviceBehaviors>` / / v prvku jako v následujícím kódu XML: `<serviceCredentials>`  
  
    ```xml  
    <serviceCredentials useIdentityConfiguration="true">  
        <!--Certificate added by Identity And Access VS Package.  Subject='CN=localhost', Issuer='CN=localhost'. Make sure you have this certificate installed. The Identity and Access tool does not install this certificate.-->  
        <serviceCertificate findValue="CN=localhost" storeLocation="LocalMachine" storeName="My" x509FindType="FindBySubjectDistinguishedName" />  
    </serviceCredentials>  
    ```  
  
     Použijete-li **Nástroj identity and Access Tool for Visual Studio 2012** (viz **změny v prostředí sady Visual Studio** výše), `<serviceCredentials>` nástroj přidá prvek s `useIdentityConfiguration` atributem nastaveným na konfigurační soubor. Také přidá odpovídající [ \<prvek System. IdentityModel >](../configure-apps/file-schema/windows-identity-foundation/system-identitymodel.md) , který obsahuje nastavení konfigurace WIF, a přidá vazbu a další nastavení, která jsou nutná pro externí ověřování u zvolené služby STS.  
  
## <a name="see-also"></a>Viz také:

- [Pokyny k migraci aplikace sestavené pomocí WIF 3.5 na WIF 4.5](guidelines-for-migrating-an-application-built-using-wif-3-5-to-wif-4-5.md)
- [Mapování oborů názvů mezi WIF 3.5 a WIF 4.5](namespace-mapping-between-wif-3-5-and-wif-4-5.md)
- [Referenční dokumentace k rozhraní API WIF](wif-api-reference.md)
- [Referenční dokumentace ke konfiguraci WIF](wif-configuration-reference.md)
