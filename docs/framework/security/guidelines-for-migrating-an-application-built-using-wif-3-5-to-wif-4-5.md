---
title: Pokyny k migraci aplikace vyvíjené v WIF 3.5 na verzi WIF 4.5
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7a32fe6e-5f68-4693-9371-19411fa8063c
caps.latest.revision: ''
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload:
- dotnet
ms.openlocfilehash: 87443a83b80440a30e942b30bd98cce09816f25f
ms.sourcegitcommit: c883637b41ee028786edceece4fa872939d2e64c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/26/2018
---
# <a name="guidelines-for-migrating-an-application-built-using-wif-35-to-wif-45"></a>Pokyny k migraci aplikace vyvíjené v WIF 3.5 na verzi WIF 4.5
## <a name="applies-to"></a>Platí pro  
  
-   Microsoft® Windows® Identity Foundation (WIF) 3.5 a 4.5.  
  
## <a name="overview"></a>Přehled  
 Windows Identity Foundation (WIF) byla původně vydána v rozhraní .NET 3.5 SP1 časový rámec. Tuto verzi WIF se označuje jako WIF 3.5. Byl vydán jako samostatný modul runtime a sady SDK, to znamená, že každý počítač, na kterém byl spuštěn aplikace s povolenými WIF museli mít nainstalován modul runtime WIF a vývojáři museli stáhnout a nainstalovat sadu SDK WIF šablony sady Visual Studio a nástrojů, který povolený vývoj aplikací s povolenými WIF. Od verze rozhraní .NET 4.5, WIF plně integrovaná do rozhraní .NET Framework. Samostatný modul runtime již není potřeba a nástrojů WIF lze nainstalovat v sadě Visual Studio 2012 pomocí Správce rozšíření pro Visual Studio. Tato verze WIF se označuje jako WIF 4.5.  
  
 Integrace WIF do .NET žádoucí několik změn v plochy rozhraní WIF API. WIF 4.5 zahrnuje nové obory názvů, některé změny konfigurace – elementy a nových nástrojů pro Visual Studio. Toto téma obsahuje pokyny, které vám pomůže vám pomůže při migraci aplikace vytvořené pomocí WIF 3.5 na verzi WIF 4.5. Může existovat scénáře, ve kterých budete muset spustit starší verze aplikace vytvořené pomocí WIF 3.5 na počítače se systémem Windows 8 nebo Windows Server 2012. Toto téma obsahuje také pokyny o tom, jak povolit WIF 3.5 pro tyto operační systémy.  
  
## <a name="changes-required-for-wif-45"></a>Změny požadované pro WIF 4.5  
 Tato část popisuje změny, které jsou potřeba k migraci aplikace WIF 3.5 na verzi WIF 4.5.  
  
### <a name="assembly-and-namespace-changes"></a>Sestavení a Namespace změny  
 V WIF 3.5 všechny třídy WIF byly obsaženy v `Microsoft.IdentityModel` sestavení (microsoft.identitymicrosoft.identitymodel.dll). Ve verzi WIF 4.5 mít byla třídy WIF rozdělit do následujících sestavení: `mscorlib` (mscorlib.dll), `System.IdentityModel` (System.IdentityModel.dll), `System.IdentityModel.Services` (System.IdentityModel.Services.dll), a `System.ServiceModel` (System.ServiceModel.dll ).  
  
 Třídy WIF 3.5 byly obsaženy v jednom z `Microsoft.IdentityModel` obory názvů, například `Microsoft.IdentityModel`, `Microsoft.IdentityModel.Tokens`, `Microsoft.IdentityModel.Web`a tak dále. Ve verzi WIF 4.5, jsou třídy WIF teď rozloženy [System.IdentityModel](http://go.microsoft.com/fwlink/?LinkId=272004) obory názvů, <xref:System.Security.Claims?displayProperty=nameWithType> obor názvů a <xref:System.ServiceModel.Security?displayProperty=nameWithType> oboru názvů. Kromě tohoto reorganizaci byly vynechány některé třídy WIF 3.5 v WIF 4.5.  
  
 V následující tabulce jsou uvedeny některé důležité oborů názvů WIF 4.5 a druh třídy, která obsahují. Podrobnější informace o tom, jak obory názvů mapování mezi WIF 3.5 a WIF 4.5 a o obory názvů a třídy, které byly vynechány v WIF 4.5 najdete v tématu [Namespace mapování mezi WIF 3.5 a WIF 4.5](../../../docs/framework/security/namespace-mapping-between-wif-3-5-and-wif-4-5.md).  
  
|WIF 4.5 Namespace|Popis|  
|-----------------------|-----------------|  
|<xref:System.IdentityModel?displayProperty=nameWithType>|Obsahuje třídy, které představují transformace souborů cookie, služby tokenů zabezpečení a specializované slovník čtečky XML. Obsahuje třídy z následujících oborů názvů WIF 3.5: `Microsoft.IdentityModel`, `Microsoft.IdentityModel.SecurityTokenService`, a `Microsoft.IdentityModel.Threading`.|  
|<xref:System.Security.Claims?displayProperty=nameWithType>|Obsahuje třídy, které představují deklarace identity, na základě deklarace identity, objekty zabezpečení na základě deklarace identity a artefaktů deklarace podle identity modelu. Obsahuje třídy z `Microsoft.IdentityModel.Claims` oboru názvů.|  
|<xref:System.IdentityModel.Tokens?displayProperty=nameWithType>|Obsahuje třídy, které představují tokeny zabezpečení, obslužné rutiny tokenu zabezpečení a artefaktů tokenu zabezpečení. Obsahuje třídy z následujících oborů názvů WIF 3.5: `Microsoft.IdentityModel.Tokens`, `Microsoft.IdentityModel.Tokens.Saml11`, a `Microsoft.IdentityModel.Tokens.Saml2`.|  
|<xref:System.IdentityModel.Services?displayProperty=nameWithType>|Obsahuje třídy, které se používají ve scénářích pasivní (WS-Federation). Obsahuje třídy z `Microsoft.IdentityModel.Web` oboru názvů.|  
|<xref:System.ServiceModel.Security?displayProperty=nameWithType>|Třídy, které představují WCF kontrakty, kanály, hostitelé služeb a jiných artefaktů, které se používají ve scénářích active (WS-Trust) jsou nyní v tomto oboru názvů. V WIF 3.5, tyto třídy byly v `Microsoft.IdentityModel.Protocols.WSTrust` oboru názvů.|  
  
> [!IMPORTANT]
>  Následující `System.IdentityModel` obory názvů obsahuje třídy, které implementují modelu WCF na základě deklarace identity: <xref:System.IdentityModel.Claims?displayProperty=nameWithType>, <xref:System.IdentityModel.Policy?displayProperty=nameWithType>, a <xref:System.IdentityModel.Selectors?displayProperty=nameWithType>. Model deklarovaných identit technologie WCF je nahrazen technologií WIF. Při sestavování řešení založená na verzi WIF byste neměli používat třídy v tyto tři obory názvů.  
  
### <a name="changes-due-to-net-integration"></a>Změny z důvodu .NET – integrace  
 WIF je nyní integrována do rozhraní .NET Framework. Většina tříd rozhraní .NET identity a zabezpečení jsou odvozeny od <xref:System.Security.Claims.ClaimsIdentity?displayProperty=nameWithType> a <xref:System.Security.Claims.ClaimsPrincipal?displayProperty=nameWithType>. Výsledky k následujícím změnám v WIF 4.5:  
  
-   WIF tříd, které teď představují deklarace identity, identity a objekty existují v <xref:System.Security.Claims?displayProperty=nameWithType> oboru názvů.  
  
    > [!IMPORTANT]
    >  <xref:System.IdentityModel.Claims?displayProperty=nameWithType> Obor názvů obsahuje třídy, které představují artefakty ve model WCF na základě deklarace identity. Mnoho z těchto tříd mít názvy, které jsou stejné jako WIF třídy; například `Claims`. Při sestavování řešení založená na verzi WIF nepoužívejte tyto třídy.  
  
-   Třídy identity a zabezpečení rozhraní .NET jsou odvozeny přímo z <xref:System.Security.Claims.ClaimsIdentity?displayProperty=nameWithType> a <xref:System.Security.Claims.ClaimsPrincipal?displayProperty=nameWithType>, které představují založené na deklaracích identity a objekty zabezpečení. Z tohoto důvodu WIF 3.5 rozhraní `IClaimsIdentity` a `IClaimsPrincipal` již nejsou potřebné a nejsou k dispozici v WIF 4.5.  
  
-   Because.NET identity a objekt třídy, jako <xref:System.Security.Principal.WindowsIdentity?displayProperty=nameWithType> a <xref:System.Security.Principal.WindowsPrincipal?displayProperty=nameWithType> nyní odvozena od <xref:System.Security.Claims.ClaimsIdentity> a <xref:System.Security.Claims.ClaimsPrincipal>, mají deklarace funkce integrované. Pro tento důvod, specifické pro deklarace identity a objekt třídy, jako `WindowsClaimsIdentity` a `WindowsClaimsPrincipal` , které byly součástí WIF 3.5 již nejsou potřebné a nejsou k dispozici v WIF 4.5.  
  
### <a name="other-changes-to-wif-functionality"></a>Další změny WIF funkčnosti  
 Kromě změn obor názvů a změny z důvodu integrace s rozhraním .NET dojde k následující obecné změny funkce WIF v WIF 4.5.  
  
-   `Microsoft.IdentityModel.ExceptionMapper` Třídy, která poskytuje funkce, které vám umožní mapovat výjimky pro konkrétní SOAP chyb povoleno, je odebrán.  
  
-   Výjimka prostor se výrazně snižují.  
  
-   Mnoho tříd, které definované protokol nebo WS-* konkrétní konstanty byly odstraněny; například `Microsoft.IdentityModel.WSAddressing10Constants` třídy, která definované konstanty související s WS-Addressing 1.0.  
  
-   Deklarace identity na službu tokenů systému Windows (c2wts) a jeho přidružené třídy v `Microsoft.IdentityModel.WindowsTokenService` obor názvů se odeberou.  
  
### <a name="wif-configuration-changes"></a>Změny konfigurace WIF  
 Mnoho změn v konfiguračním souboru být způsobena aktualizace oboru názvů v WIF 4.5. Zvažte například následující položku WIF 3.5 v `<httpModules>` přidejte WS-Federation Authentication Manager pro aplikaci:  
  
```xml  
<add name="WSFederationAuthenticationModule" type="Microsoft.IdentityModel.Web.WSFederationAuthenticationModule, Microsoft.IdentityModel, Version=3.5.0.0, Culture=neutral, PublicKeyToken=abcd … 5678" />  
```  
  
 Tato položka se aktualizovalo v WIF 4.5 zahrnuje nové obory názvů a verze sestavení:  
  
```xml  
<add name="WSFederationAuthenticationModule" type="System.IdentityModel.Services.WSFederationAuthenticationModule, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=abcd … 5678"/>  
```  
  
 Následující seznam obsahuje hlavní změny konfiguračního souboru pro verzi WIF 4.5.  
  
-   `<microsoft.identityModel>` Je oddíl [ \<system.identityModel >](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel.md) části.  
  
-   `<service>` Element je teď [ \<identityConfiguration >](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) element.  
  
-   Nová část, [ \<system.identityModel.services >](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel-services.md), byla přidána k určení nastavení, které řídí chování ve scénářích pasivní (WS-Federation).  
  
-   [ \<FederationConfiguration >](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md) elementu a jeho podřízené elementy byly přesunuté z `<service>` element v WIF 3.5 do nového `<system.identityModel.services>` elementu.  
  
-   Několika elementy, které může být zadán v úrovni služby přímo pod `<service>` element v WIF 3.5 byly omezené na specifikované v části [ \<securityTokenHandlerConfiguration >](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md) element. (Může být stále zadané v části [ \<identityConfiguration >](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) element v WIF 4.5 z důvodu zpětné kompatibility.)  
  
 Úplný seznam konfigurační prvky WIF 4.5, najdete v části [schéma konfigurace WIF](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/index.md).  
  
### <a name="visual-studio-tooling-changes"></a>Změny nástrojů Visual Studio  
 Sada SDK WIF 3.5 nabízí nástroje pro samostatný federační FedUtil.exe (FedUtil), který můžete použít pro externí identity management WIF povolené aplikace služby tokenů zabezpečení (STS). Tento nástroj Přidat WIF nastavení do konfiguračního souboru aplikace se zapnout aplikaci získat tokeny zabezpečení z jednoho nebo více STSs a byla prezentované v sadě Visual Studio prostřednictvím **přidat odkaz na službu tokenů zabezpečení** tlačítko. FedUtil se nedodává s WIF 4.5. Místo toho WIF 4.5 podporuje nové rozšíření sady Visual Studio s názvem identita a přístup pro sadu Visual Studio 2012, který můžete použít k úpravě souboru konfigurace aplikace s WIF nastavení požadované k externí správu identit do služby tokenů zabezpečení. Identita a přístup také implementuje služby tokenů zabezpečení nazývá místní služby tokenů zabezpečení, který můžete použít k testování aplikací povolit WIF. Tato funkce v mnoha případech, vyloučí potřebu vytvářet vlastní STSs, které byly často nezbytné v otestovat řešení ve vývoji WIF 3.5. Z tohoto důvodu šablony služby tokenů zabezpečení již nejsou podporovány v sadě Visual Studio 2012; třídy, které podporují vývoj STSs jsou však stále k dispozici v WIF 4.5.  
  
 Identita a přístup můžete nainstalovat z rozšíření a aktualizace Manager v sadě Visual Studio nebo si můžete stáhnout z této stránky na galerie kódů: [identita a přístup pro sadu Visual Studio 2012 na galerie kódů](http://go.microsoft.com/fwlink/?LinkID=245849). Změny nástrojů Visual Studio jsou shrnuty v následujícím seznamu:  
  
-   Přidat odkaz na službu tokenů zabezpečení funkce se odebere. Pokud chcete nahrazení je identita a přístup.  
  
-   Šablony Visual Studio služby tokenů zabezpečení, se odeberou. Můžete použít místní službu tokenů zabezpečení, která je k dispozici prostřednictvím Identity a přístup k testování řešení identity, které jste vývoji WIF. Konfigurace místní služby tokenů zabezpečení můžete upravit tak, aby přizpůsobit deklarace identity, které funguje.  
  
-   Samostatné nástrojem Federation Utility (FedUtil) není k dispozici v WIF 4.5. Můžete identita a přístup k úpravě konfiguračních souborů využívající správu identit do služby tokenů zabezpečení.  
  
 Další informace o identitě a Access Tool najdete v tématu [identita a přístup pro sadu Visual Studio 2012](../../../docs/framework/security/identity-and-access-tool-for-vs.md)  
  
<a name="BKMK_ToolingChanges"></a>   
### <a name="passive-ws-federation-scenarios"></a>Scénáře pasivní (WS-Federation):  
  
-   Třídy, které podporují scénáře pasivní byly přesunuty do <xref:System.IdentityModel.Services?displayProperty=nameWithType> oboru názvů. V WIF 3.5 tyto třídy byly v `Microsoft.IdentityModel.Web` oboru názvů.  
  
-   Třídy v `Microsoft.IdentityModel.Web.Configuration` obor názvů, byly přesunuty do <xref:System.IdentityModel.Services.Configuration?displayProperty=nameWithType>. Tyto třídy představují konkrétní objekty do konfigurace v nástroji pasivní scénáře.  
  
-   `FederatedPasssiveSignInControl` Již není podporována; všechny třídy v `Microsoft.IdentityModel.Web.Controls` obor názvů byly odebrány z WIF 4.5.  
  
-   Modul ověřování WS-Federation (<xref:System.IdentityModel.Services.WSFederationAuthenticationModule>) odhlašování funkce se liší od WIF 3.5. Další podrobnosti o tom, jak odhlašování funguje v WIF 4.5 najdete v tématu <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> třída tématu.  
  
### <a name="active-wcfws-trust-scenarios"></a>Aktivní scénáře (WCF/WS-Trust):  
  
-   `Microsoft.IdentityModel.Protocols.WSTrust` Obor názvů rozdělena především do dva obory názvů v WIF 4.5. Třídy, které představují artefaktů, které jsou specifické pro protokol WS-Trust jsou teď ve <xref:System.IdentityModel.Protocols.WSTrust?displayProperty=nameWithType>. To zahrnuje třídy jako <xref:System.IdentityModel.Protocols.WSTrust.RequestSecurityToken>. Třídy, které představují kontraktů služby, kanály, hostitelé služeb a jiných artefaktů, které jsou součástí použití WS-Trust v aplikacích WCF byly přesunuty do <xref:System.ServiceModel.Security?displayProperty=nameWithType>, například <xref:System.ServiceModel.Security.IWSTrust13AsyncContract> rozhraní.  
  
-   Konfigurace aplikace WCF na technologii WIF používají je výrazně jednodušší. Dříve `Microsoft.IdentityModel.Configuration.ConfigureServiceHostBehaviorExtensionElement` měl být přidán jako rozšíření chování a pak používá tato funkce se k Klínový WIF do chování služby zadáním `<federatedServiceHostConfiguration>` elementu. WIF 4.5 více úzce integrovaná s použitím technologie WCF. Teď povolit WIF na službu WCF zadáním `useIdentityConfiguration` atributu u `<system.serviceModel>` / `<behaviors>` / `<serviceBehaviors>` / `<serviceCredentials>` element jako následující kód XML:  
  
    ```xml  
    <serviceCredentials useIdentityConfiguration="true">  
        <!--Certificate added by Identity And Access VS Package.  Subject='CN=localhost', Issuer='CN=localhost'. Make sure you have this certificate installed. The Identity and Access tool does not install this certificate.-->  
        <serviceCertificate findValue="CN=localhost" storeLocation="LocalMachine" storeName="My" x509FindType="FindBySubjectDistinguishedName" />  
    </serviceCredentials>  
    ```  
  
-   Ve verzi WIF 4.5 služby je třeba zadat certifikát používaný k aktivní službě (WCF) na hostitele služby. V konfiguraci, můžete k tomu prostřednictvím `<system.serviceModel>` / `<behaviors>` / `<serviceBehaviors>` / `<serviceCredentials>` / `<serviceCertificate>` element, jak je znázorněno v předchozím příkladu. V WIF 3.5 může být zadána certifikát služby prostřednictvím `<serviceCertificate>` podřízený element WIF `<service>` elementu. Tato funkce ve verzi WIF 4.5; neexistuje. Zadejte `<serviceCertificate>` prvek v rámci `<serviceCredentials>` element místo.  
  
-   Třídy používané k Klínový WIF 3.5 do WCF již existuje. To zahrnuje následující třídy v `Microsoft.IdentityModel.Tokens` obor názvů: `FederatedSecurityTokenManager`, `FederatedServiceCredentials`, a `IdentityModelServiceAuthorizationManager`, a taky `Microsoft.IdentityModel.Configuration.ConfigureServiceHostBehaviorExtensionElement` třídy.  
  
## <a name="enabling-wif-35-in-windows-8"></a>Povolit WIF 3.5 ve Windows 8  
 Protože WIF 4.5 je součástí rozhraní .NET 4.5, je automaticky povolené v počítačích se systémem Windows 8 a Windows Server 2012 a aplikací, které jsou vytvořené pomocí WIF 4.5 budou spouštěny pod Windows 8 nebo Windows Server 2012 ve výchozím nastavení. Můžete však spustit aplikací, které byly vytvořené pomocí WIF 3.5 na počítači se systémem Windows 8 nebo Windows Server 2012. V takovém případě musíte povolit WIF 3.5 v cílovém počítači. V počítači se systémem Windows 8 můžete to provést pomocí nástroje Deployment Image Servicing and Management (DISM). V počítači se systémem Windows Server 2012, můžete pomocí nástroje DISM nebo můžete použít prostředí Windows PowerShell `Add-WindowsFeature` rutiny. V obou případech můžete vyvolat příslušnými příkazy v příkazovém řádku nebo z v prostředí Windows PowerShell.  
  
 Následující příkazy ukazují, jak pomocí nástroje DISM z příkazového řádku nebo v prostředí Windows PowerShell. Ve výchozím nastavení modul PowerShell nástroje DISM je součástí systému Windows 8 a Windows Server 2012 a není potřeba importovat. Další informace o použití DISM pomocí prostředí Windows PowerShell najdete v tématu [postup pomocí nástroje DISM v prostředí Windows PowerShell](http://go.microsoft.com/fwlink/?LinkId=254419).  
  
 Chcete-li povolit WIF 3.5 pomocí nástroje DISM:  
  
```  
dism /online /enable-feature:windows-identity-foundation  
```  
  
 Postup při zakázání WIF 3.5 pomocí nástroje DISM:  
  
```  
dism /online /disable-feature:windows-identity-foundation  
```  
  
 Kontrola funkce, které jsou povolené nebo zakázané, pomocí nástroje DISM:  
  
```  
dism /online /get-features  
```  
  
 V počítačích se systémem Windows Server 2012, můžete případně povolit WIF 3.5, pomocí prostředí Windows PowerShell `Add-WindowsFeature` rutiny. Uděláte to tak že z příkazového řádku můžete zadat následující příkaz:  
  
```  
powershell "add-windowsfeature windows-identity-foundation"  
```  
  
 Z v prostředí Windows PowerShell, můžete zadat příkaz přímo:  
  
```  
add-windowsfeature windows-identity-foundation  
```  
  
> [!NOTE]
>  Protože mnoho tříd v WIF 3.5 a WIF 4.5 sdílet stejné názvy, pokud používáte WIF 3.5 a WIF 4.5 společně, je nutné buď použijte plně kvalifikovaných názvů třídy nebo obor názvů aliasy použijte k rozlišení mezi třídami v WIF 3.5 a WIF 4.5.  
  
## <a name="see-also"></a>Viz také  
 [Schéma konfigurace WIF](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/index.md)  
 [Mapování oborů názvů mezi WIF 3.5 a WIF 4.5](../../../docs/framework/security/namespace-mapping-between-wif-3-5-and-wif-4-5.md)  
 [Novinky ve Windows Workflow Foundation 4.5](../../../docs/framework/security/whats-new-in-wif.md)  
 [Nástroj Identita a přístup pro Visual Studio 2012](../../../docs/framework/security/identity-and-access-tool-for-vs.md)
