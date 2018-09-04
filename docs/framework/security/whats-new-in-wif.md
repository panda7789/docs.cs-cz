---
title: Co&#39;nového ve Windows Workflow Foundation 4.5
ms.date: 03/30/2017
ms.assetid: 3b381f04-593b-471f-bd33-0362be1aade5
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 2a275c32caefb54b11cc605c1339526465c8319a
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43562421"
---
# <a name="what39s-new-in-windows-identity-foundation-45"></a>Co&#39;nového ve Windows Workflow Foundation 4.5
První verze technologie Windows Identity Foundation (WIF) byla uvedena na trh jako samostatný produkt ke stažení a je známa pod označením WIF 3.5, protože byla uvedena ve stejném období jako technologie .NET 3.5 SP1. Počínaje verzí .NET 4.5 je technologie WIF součástí rozhraní .NET Framework. Tříd WIF přímo k dispozici v rozhraní umožňuje mnohem hlubší integraci deklarovaných identit v .NET, což usnadňuje používání deklarací. Aplikace napsané pro technologie WIF 3.5 bude nutné upravit tak, aby mohli využít nový model; informace najdete v tématu [pokyny k migraci Application Built Using WIF 3.5 to WIF 4.5](../../../docs/framework/security/guidelines-for-migrating-an-application-built-using-wif-3-5-to-wif-4-5.md).  
  
 Následuje přehled některých hlavních změn.  
  
## <a name="wif-is-now-part-of-the-net-framework"></a>Technologie WIF je nyní součástí rozhraní .NET Framework  
 Třídy WIF jsou nyní rozloženy mezi několik sestavení, hlavní se `mscorlib`, `System.IdentityModel`, `System.IdentityModel.Services`, a `System.ServiceModel`. Podobně jsou třídy WIF rozloženy mezi několik oborů názvů: <xref:System.Security.Claims?displayProperty=nameWithType>, několik [System.IdentityModel](https://go.microsoft.com/fwlink/?LinkId=272004) obory názvů, a <xref:System.ServiceModel.Security?displayProperty=nameWithType>. <xref:System.Security.Claims?displayProperty=nameWithType> Obor názvů obsahuje nové <xref:System.Security.Claims.ClaimsPrincipal> a <xref:System.Security.Claims.ClaimsIdentity> třídy (viz níže). Všechny objekty zabezpečení v rozhraní .NET jsou nyní odvozeny z <xref:System.Security.Claims.ClaimsPrincipal>. Podrobné informace o oborech názvů WIF a typech tříd, které obsahují, naleznete v tématu [Reference k rozhraní API technologie WIF](../../../docs/framework/security/wif-api-reference.md). Informace o mapování oborů názvů mezi WIF 3.5 a WIF 4.5 naleznete v tématu [Namespace mapování mezi verzemi WIF 3.5 a WIF 4.5](../../../docs/framework/security/namespace-mapping-between-wif-3-5-and-wif-4-5.md).  
  
## <a name="new-claims-model-and-principal-object"></a>Nový model a objekt zabezpečení založený na deklaracích  
 Deklarace jsou v samotném jádru rozhraní .NET Framework 4.5. Všechny základní třídy deklarací (<xref:System.Security.Claims.Claim>, <xref:System.Security.Claims.ClaimsIdentity>, <xref:System.Security.Claims.ClaimsPrincipal>, <xref:System.Security.Claims.ClaimTypes>, a <xref:System.Security.Claims.ClaimValueTypes>) přímo v `mscorlib` v <xref:System.Security.Claims?displayProperty=nameWithType> oboru názvů. To už nejsou potřebné k použití rozhraní za účelem zařadit deklarací do systému identit .NET: <xref:System.Security.Principal.WindowsPrincipal>, <xref:System.Security.Principal.GenericPrincipal>, a <xref:System.Web.Security.RolePrincipal> nyní dědí z <xref:System.Security.Claims.ClaimsPrincipal>; a <xref:System.Security.Principal.WindowsIdentity>, <xref:System.Security.Principal.GenericIdentity>, a <xref:System.Web.Security.FormsIdentity> nyní dědí. z <xref:System.Security.Claims.ClaimsIdentity>. Stručně řečeno, všechny třídy objektů zabezpečení nyní budou poskytovat deklarace. Třídy integrace technologie WIF 3.5 a rozhraní (`WindowsClaimsIdentity`, `WindowsClaimsPrincipal`, `IClaimsPrincipal`, `IClaimsIdentity`) byly proto odebrány. Kromě toho <xref:System.Security.Claims.ClaimsIdentity> kolekce tříd nyní zveřejňuje metody, které usnadňují dotazování na identitu deklarací.  
  
## <a name="changes-to-the-wif-45-visual-studio-experience"></a>Změny v používání technologie WIF 4.5 v prostředí sady Visual Studio  
  
-   **Přidat odkaz STS....** Funkce Visual Studio (nástroj příkazového řádku FedUtil) již existuje Místo toho můžete použít nové rozšíření sady Visual Studio **Identity and Access Tool for Visual Studio 2012**. To umožňuje federaci s existující službou tokenů zabezpečení (STS). Svá řešení můžete také testovat s použitím místní služby tokenů zabezpečení LocalSTS. Po instalaci rozšíření klikněte pravým tlačítkem na projekt a hledejte **identit a přístupu** v místní nabídce.  
  
-   Šablony technologie ASP.NET a služby STS již nejsou k dispozici, protože deklarace je možné používat přímo v existujících šablonách projektů pro technologii ASP.NET, weby a technologii WCF.  
  
-   Ovládací prvky `Microsoft.IdentityModel.Web.Controls` obor názvů (`SignInControl`, `FederatedPassiveSignInControl`, a `FederatedPassiveSignInStatus`) nejsou přeneseny do verze WIF 4.5.  
  
## <a name="changes-to-the-wif-45-api"></a>Změny v rozhraní API technologie WIF 4.5  
  
-   Obecně jsou deklarace identity související třídy v <xref:System.Security.Claims?displayProperty=nameWithType> obor názvů. Související třídy – WCF – servisní smlouvy, kanály, objekty pro vytváření kanálů a obsluha hostitelů, které se používají pro scénáře, WS-Trust – se v <xref:System.ServiceModel.Security?displayProperty=nameWithType>; a všechny ostatní třídy technologie WIF jsou rozděleny mezi různými [System.IdentityModel](https://go.microsoft.com/fwlink/?LinkId=272004) obory názvů – patří mezi ně, například třídy, které představují WS-* a artefaktů SAML, obslužné rutiny tokenů a související třídy a třídy používané ve scénářích WS-Federation. Další informace najdete v tématu [Namespace mapování mezi verzemi WIF 3.5 a WIF 4.5](../../../docs/framework/security/namespace-mapping-between-wif-3-5-and-wif-4-5.md) a [Reference k rozhraní API technologie WIF](../../../docs/framework/security/wif-api-reference.md).  
  
-   Bylo povoleno používání klíče počítače v souborech cookie relací při používání webových farem. Další informace najdete v tématu [technologie WIF a webové farmy](../../../docs/framework/security/wif-and-web-farms.md).  
  
-   Lze nyní deklarativně nakonfigurovat technologie WIF pod [ \<system.identityModel >](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel.md) a [ \<system.identityModel.services >](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel-services.md) elementy. Další informace o konfiguraci technologie WIF Nalezete v tématu [WIF Configuration Reference](../../../docs/framework/security/wif-configuration-reference.md).  
  
## <a name="other-notable-net-changes-or-features-that-are-caused-by-the-integration-of-wif-into-net"></a>Další významné změny technologie .NET nebo funkce způsobené začleněním technologie WIF do technologie .NET  
  
-   Možnost autorizace na základě deklarované identity (CBAC) je nyní součástí rozhraní .NET Framework. Můžete nakonfigurovat <xref:System.Security.Claims.ClaimsAuthorizationManager> objektu a pak použít <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> a <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> třídy provádět imperativní a deklarativní kontroly přístupu v kódu. Autorizace CBAC poskytuje větší flexibilitu a přesnost než tradiční kontroly přístupu na základě rolí (RBAC). Umožňuje také větší oddělení zásad autorizace od obchodní logiky, protože obchodní logika může kontrolovat přístup na konkrétní deklarace identity nebo sadu deklarací identity a zásady autorizace pro tyto deklarace identit lze nakonfigurovat deklarativně v rámci [ \<claimsAuthorizationManager >](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/claimsauthorizationmanager.md) elementu.  
  
## <a name="wcf-changes-as-a-result-of-wif-integration"></a>Změny v technologii WCF v důsledku integrace technologie WIF:  
  
-   Model deklarovaných identit technologie WCF je nahrazen technologií WIF. To znamená, že třídy v <xref:System.IdentityModel.Claims?displayProperty=nameWithType>, <xref:System.IdentityModel.Policy?displayProperty=nameWithType>, a <xref:System.IdentityModel.Selectors?displayProperty=nameWithType> obory názvů by se měly zahodit používat třídy technologie WIF.  
  
-   Technologie WIF je nyní povolena ve službě WCF zadáním `useIdentityConfiguration` atribut na `<system.serviceModel>` / `<behaviors>` / `<serviceBehaviors>` / `<serviceCredentials>` element jako následující kód XML:  
  
    ```xml  
    <serviceCredentials useIdentityConfiguration="true">  
        <!--Certificate added by Identity And Access VS Package.  Subject='CN=localhost', Issuer='CN=localhost'. Make sure you have this certificate installed. The Identity and Access tool does not install this certificate.-->  
        <serviceCertificate findValue="CN=localhost" storeLocation="LocalMachine" storeName="My" x509FindType="FindBySubjectDistinguishedName" />  
    </serviceCredentials>  
    ```  
  
     Při použití **Identity and Access Tool for Visual Studio 2012** (naleznete v tématu **změny v prostředí sady Visual Studio** výše), přidá tento nástroj `<serviceCredentials>` element s `useIdentityConfiguration` atribut nastaven na konfigurační soubor pro vás. Přidá také odpovídající [ \<system.identityModel >](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel.md) element, který obsahuje konfigurační nastavení technologie WIF a přidá vazbu a další nastavení nezbytná pro externí ověřování vámi zvolené služby tokenů zabezpečení.  
  
## <a name="see-also"></a>Viz také  
 [Pokyny k migraci aplikace sestavené pomocí WIF 3.5 na WIF 4.5](../../../docs/framework/security/guidelines-for-migrating-an-application-built-using-wif-3-5-to-wif-4-5.md)  
 [Mapování oborů názvů mezi WIF 3.5 a WIF 4.5](../../../docs/framework/security/namespace-mapping-between-wif-3-5-and-wif-4-5.md)  
 [Referenční dokumentace k rozhraní API WIF](../../../docs/framework/security/wif-api-reference.md)  
 [Referenční dokumentace ke konfiguraci WIF](../../../docs/framework/security/wif-configuration-reference.md)
