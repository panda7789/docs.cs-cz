---
title: Co&#39;s ve Windows Identity Foundation 4.5
ms.date: 03/30/2017
ms.assetid: 3b381f04-593b-471f-bd33-0362be1aade5
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 0a5bc7d53405966bcb86750780473c4060d7ced3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="what39s-new-in-windows-identity-foundation-45"></a>Co&#39;s ve Windows Identity Foundation 4.5
První verze technologie Windows Identity Foundation (WIF) byla uvedena na trh jako samostatný produkt ke stažení a je známa pod označením WIF 3.5, protože byla uvedena ve stejném období jako technologie .NET 3.5 SP1. Počínaje verzí .NET 4.5 je technologie WIF součástí rozhraní .NET Framework. S přímo k dispozici v rámci třídy WIF umožňuje mnohem hlubší integrace založené na deklaracích identity v rozhraní .NET, což usnadňuje používat deklarace identity. Aplikace napsané pro WIF 3.5 bude nutné upravit, aby bylo možné využívat výhod nového modelu; informace najdete v tématu [pokyny pro migraci aplikaci vytvořené pomocí WIF 3.5 na verzi WIF 4.5](../../../docs/framework/security/guidelines-for-migrating-an-application-built-using-wif-3-5-to-wif-4-5.md).  
  
 Následuje přehled některých hlavních změn.  
  
## <a name="wif-is-now-part-of-the-net-framework"></a>Technologie WIF je nyní součástí rozhraní .NET Framework  
 WIF třídy jsou nyní rozloženy několik sestavení, hlavní těm, které jsou právě `mscorlib`, `System.IdentityModel`, `System.IdentityModel.Services`, a `System.ServiceModel`. Podobně WIF třídy jsou rozloženy několik oborů názvů: <xref:System.Security.Claims?displayProperty=nameWithType>, několik [System.IdentityModel](http://go.microsoft.com/fwlink/?LinkId=272004) obory názvů, a <xref:System.ServiceModel.Security?displayProperty=nameWithType>. <xref:System.Security.Claims?displayProperty=nameWithType> Obor názvů obsahuje nové <xref:System.Security.Claims.ClaimsPrincipal> a <xref:System.Security.Claims.ClaimsIdentity> třídy (viz níže). Všechny objekty zabezpečení v rozhraní .NET jsou odvozeny od <xref:System.Security.Claims.ClaimsPrincipal>. Podrobné informace o WIF obory názvů a typy tříd, které obsahují, najdete v části [referenční dokumentace rozhraní API WIF](../../../docs/framework/security/wif-api-reference.md). Informace o tom, jak obory názvů mapování mezi WIF 3.5 a WIF 4.5 najdete v tématu [Namespace mapování mezi WIF 3.5 a WIF 4.5](../../../docs/framework/security/namespace-mapping-between-wif-3-5-and-wif-4-5.md).  
  
## <a name="new-claims-model-and-principal-object"></a>Nový model a objekt zabezpečení založený na deklaracích  
 Deklarace jsou v samotném jádru rozhraní .NET Framework 4.5. Základní deklarace třídy (<xref:System.Security.Claims.Claim>, <xref:System.Security.Claims.ClaimsIdentity>, <xref:System.Security.Claims.ClaimsPrincipal>, <xref:System.Security.Claims.ClaimTypes>, a <xref:System.Security.Claims.ClaimValueTypes>) všechny live přímo v `mscorlib` v <xref:System.Security.Claims?displayProperty=nameWithType> oboru názvů. Již není nutné k použití rozhraní, aby bylo možné zařadit deklarace identity do systému identity rozhraní .NET: <xref:System.Security.Principal.WindowsPrincipal>, <xref:System.Security.Principal.GenericPrincipal>, a <xref:System.Web.Security.RolePrincipal> nyní dědí <xref:System.Security.Claims.ClaimsPrincipal>; a <xref:System.Security.Principal.WindowsIdentity>, <xref:System.Security.Principal.GenericIdentity>, a <xref:System.Web.Security.FormsIdentity> nyní dědí. z <xref:System.Security.Claims.ClaimsIdentity>. Stručně řečeno, všechny třídy objektů zabezpečení nyní budou poskytovat deklarace. WIF 3.5 integrace třídy a rozhraní (`WindowsClaimsIdentity`, `WindowsClaimsPrincipal`, `IClaimsPrincipal`, `IClaimsIdentity`) proto byly odebrány. Kromě toho <xref:System.Security.Claims.ClaimsIdentity> třída teď zpřístupňuje metody, které usnadňují dotaz identitu deklarací kolekce.  
  
## <a name="changes-to-the-wif-45-visual-studio-experience"></a>Změny v používání technologie WIF 4.5 v prostředí sady Visual Studio  
  
-   **Přidat odkaz na službu tokenů zabezpečení...** Funkci Visual Studio (nástroj cmdline FedUtil) již existuje; Místo toho můžete použít nové rozšíření sady Visual Studio **identita a přístup pro sadu Visual Studio 2012**. To umožňuje federaci s existující službou tokenů zabezpečení (STS). Svá řešení můžete také testovat s použitím místní služby tokenů zabezpečení LocalSTS. Po instalaci rozšíření můžete kliknout pravým tlačítkem na projekt a vyhledejte **identit a přístupu** v místní nabídce.  
  
-   Šablony technologie ASP.NET a služby STS již nejsou k dispozici, protože deklarace je možné používat přímo v existujících šablonách projektů pro technologii ASP.NET, weby a technologii WCF.  
  
-   Ovládací prvky v `Microsoft.IdentityModel.Web.Controls` obor názvů (`SignInControl`, `FederatedPassiveSignInControl`, a `FederatedPassiveSignInStatus`) nejsou přenášejí do WIF 4.5.  
  
## <a name="changes-to-the-wif-45-api"></a>Změny v rozhraní API technologie WIF 4.5  
  
-   Obecně platí, související třídy deklarace identity jsou v <xref:System.Security.Claims?displayProperty=nameWithType> obor názvů; WCF související třídy – – služba měnící, kanály, objekty factory kanálu a hostitelé služeb, které se používají pro scénáře WS-Trust – <xref:System.ServiceModel.Security?displayProperty=nameWithType>; a všech ostatních WIF třídy jsou rozloženy různé [System.IdentityModel](http://go.microsoft.com/fwlink/?LinkId=272004) obory názvů – patří, například tříd, které představují WS-* a artefaktů SAML token obslužné rutiny a související třídy a třídy používané ve scénářích WS-Federation. Další informace najdete v tématu [Namespace mapování mezi WIF 3.5 a WIF 4.5](../../../docs/framework/security/namespace-mapping-between-wif-3-5-and-wif-4-5.md) a [referenční dokumentace rozhraní API WIF](../../../docs/framework/security/wif-api-reference.md).  
  
-   Bylo povoleno používání klíče počítače v souborech cookie relací při používání webových farem. Další informace najdete v tématu [WIF a webových farem](../../../docs/framework/security/wif-and-web-farms.md).  
  
-   Teď deklarativně nakonfigurovat WIF pod [ \<system.identityModel >](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel.md) a [ \<system.identityModel.services >](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel-services.md) elementy. Další informace o konfiguraci WIF najdete v tématu [referenci na konfigurační WIF](../../../docs/framework/security/wif-configuration-reference.md).  
  
## <a name="other-notable-net-changes-or-features-that-are-caused-by-the-integration-of-wif-into-net"></a>Další významné změny technologie .NET nebo funkce způsobené začleněním technologie WIF do technologie .NET  
  
-   Možnost autorizace na základě deklarované identity (CBAC) je nyní součástí rozhraní .NET Framework. Můžete nakonfigurovat <xref:System.Security.Claims.ClaimsAuthorizationManager> objekt a potom pomocí <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> a <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> třídy k provádění kontrol imperativní a deklarativní přístup do vašeho kódu. Autorizace CBAC poskytuje větší flexibilitu a přesnost než tradiční kontroly přístupu na základě rolí (RBAC). Umožňuje také větší oddělení zásad autorizace od obchodní logiky, protože obchodní logiky můžete základní kontrola přístupu na konkrétní deklarace identity nebo sadu deklarací identity a zásady autorizace pro tyto deklarace identity, lze nastavit deklarativně pod [ \<claimsAuthorizationManager >](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/claimsauthorizationmanager.md) element.  
  
## <a name="wcf-changes-as-a-result-of-wif-integration"></a>Změny v technologii WCF v důsledku integrace technologie WIF:  
  
-   Model deklarovaných identit technologie WCF je nahrazen technologií WIF. To znamená, že třídy v <xref:System.IdentityModel.Claims?displayProperty=nameWithType>, <xref:System.IdentityModel.Policy?displayProperty=nameWithType>, a <xref:System.IdentityModel.Selectors?displayProperty=nameWithType> obory názvů by se měly zahodit považuje pomocí třídy WIF.  
  
-   WIF je teď povolené ve službě WCF zadáním `useIdentityConfiguration` atributu u `<system.serviceModel>` / `<behaviors>` / `<serviceBehaviors>` / `<serviceCredentials>` element jako následující kód XML:  
  
    ```xml  
    <serviceCredentials useIdentityConfiguration="true">  
        <!--Certificate added by Identity And Access VS Package.  Subject='CN=localhost', Issuer='CN=localhost'. Make sure you have this certificate installed. The Identity and Access tool does not install this certificate.-->  
        <serviceCertificate findValue="CN=localhost" storeLocation="LocalMachine" storeName="My" x509FindType="FindBySubjectDistinguishedName" />  
    </serviceCredentials>  
    ```  
  
     Při použití **identita a přístup pro sadu Visual Studio 2012** (najdete v části **změny prostředí Visual Studio** výše), nástroj přidá `<serviceCredentials>` element s `useIdentityConfiguration` atribut nastaven na konfigurační soubor pro vás. Také přidá odpovídající [ \<system.identityModel >](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel.md) element, který obsahuje konfigurační nastavení WIF a přidá vazbu a další nastavení, které jsou nezbytné pro externí ověřování pro vaši vybranou služby tokenů zabezpečení.  
  
## <a name="see-also"></a>Viz také  
 [Pokyny k migraci aplikace sestavené pomocí WIF 3.5 na WIF 4.5](../../../docs/framework/security/guidelines-for-migrating-an-application-built-using-wif-3-5-to-wif-4-5.md)  
 [Mapování oborů názvů mezi WIF 3.5 a WIF 4.5](../../../docs/framework/security/namespace-mapping-between-wif-3-5-and-wif-4-5.md)  
 [Referenční dokumentace k rozhraní API WIF](../../../docs/framework/security/wif-api-reference.md)  
 [Referenční dokumentace ke konfiguraci WIF](../../../docs/framework/security/wif-configuration-reference.md)
