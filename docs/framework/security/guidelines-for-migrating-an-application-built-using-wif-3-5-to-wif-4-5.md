---
title: Pokyny k migraci aplikace sestavené pomocí WIF 3.5 na WIF 4.5
ms.date: 03/30/2017
ms.assetid: 7a32fe6e-5f68-4693-9371-19411fa8063c
author: BrucePerlerMS
ms.openlocfilehash: d843f2d01072db8b848f4d6f26dba32b4e48f302
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54696184"
---
# <a name="guidelines-for-migrating-an-application-built-using-wif-35-to-wif-45"></a>Pokyny k migraci aplikace sestavené pomocí WIF 3.5 na WIF 4.5
## <a name="applies-to"></a>Platí pro  
  
-   Microsoft Windows® Identity Foundation (WIF) 3.5 a 4.5.  
  
## <a name="overview"></a>Přehled  
 Technologie Windows Identity Foundation (WIF) byl vydaný už v rozhraní .NET 3.5 SP1 časový rámec. Tuto verzi technologie WIF jsou označovány jako technologie WIF 3.5. Byl vydán jako samostatný modul runtime a sadu SDK, znamená, že každý počítač, na kterém byl spuštěn podporou technologie WIF aplikace musel si modul runtime WIF nainstalovaný a vývojáři měli ke stažení a instalace sady SDK technologie WIF k získání šablony sady Visual Studio a nabízí nástroje, které povoleno vývoj aplikací s podporou technologie WIF. Od verze rozhraní .NET 4.5, WIF plně integrovaná do rozhraní .NET Framework. Už nepotřebujete samostatný modul runtime a nástroje pro technologii WIF lze nainstalovat v sadě Visual Studio 2012 pomocí Správce rozšíření sady Visual Studio. Tuto verzi technologie WIF jsou označovány jako technologie WIF 4.5.  
  
 Integrace technologie WIF do technologie .NET nezbytné několik změn v plochy rozhraní API technologie WIF. Technologie WIF 4.5 obsahuje nové obory názvů, některé změny elementů konfigurace a nové nástroje pro Visual Studio. Toto téma obsahuje pokyny, které můžete použít při migraci aplikace sestavené pomocí WIF 3.5 to WIF 4.5. Můžou existovat scénáře, ve kterých je potřeba spouštět starší verze aplikace sestavené pomocí WIF 3.5 na počítačích se systémem Windows 8 nebo Windows Server 2012. Toto téma obsahuje také pokyny k povolení technologie WIF 3.5 pro tyto operační systémy.  
  
## <a name="changes-required-for-wif-45"></a>Změny pro technologie WIF 4.5  
 Tato část popisuje změny, které jsou potřeba k migraci aplikace technologie WIF 3.5 to WIF 4.5.  
  
### <a name="assembly-and-namespace-changes"></a>Sestavení a změny Namespace  
 Technologie WIF 3.5, všechny třídy technologie WIF byly obsaženy v `Microsoft.IdentityModel` sestavení (microsoft.identitymicrosoft.identitymodel.dll). Do verze WIF 4.5 byla rozdělení třídy technologie WIF na následující sestavení: `mscorlib` (mscorlib.dll) `System.IdentityModel` (System.IdentityModel.dll) `System.IdentityModel.Services` (System.IdentityModel.Services.dll), a `System.ServiceModel` (System.ServiceModel.dll ).  
  
 Třídy technologie WIF 3.5 byly obsaženy v jednom z `Microsoft.IdentityModel` obory názvů, třeba `Microsoft.IdentityModel`, `Microsoft.IdentityModel.Tokens`, `Microsoft.IdentityModel.Web`, a tak dále. V technologii WIF 4.5 třídy technologie WIF jsou nyní rozloženy mezi [System.IdentityModel](https://go.microsoft.com/fwlink/?LinkId=272004) obory názvů, <xref:System.Security.Claims?displayProperty=nameWithType> obor názvů a <xref:System.ServiceModel.Security?displayProperty=nameWithType> oboru názvů. Kromě tohoto reorganizaci byly vynechány některé třídy technologie WIF 3.5 v technologie WIF 4.5.  
  
 V následující tabulce jsou uvedeny některé důležité technologie WIF 4.5 oborů názvů a typ třídy, které obsahují. Podrobnější informace o mapování oborů názvů mezi WIF 3.5 a WIF 4.5 a o obory názvů a třídy, které se odstranily technologie WIF 4.5 naleznete v tématu [Namespace mapování mezi verzemi WIF 3.5 a WIF 4.5](../../../docs/framework/security/namespace-mapping-between-wif-3-5-and-wif-4-5.md).  
  
|Technologie WIF 4.5 Namespace|Popis|  
|-----------------------|-----------------|  
|<xref:System.IdentityModel?displayProperty=nameWithType>|Obsahuje třídy, které představují transformace souborů cookie, služby tokenu zabezpečení a specializované čtenáře slovníku XML. Obsahuje třídy z následujících oborů názvů WIF 3.5: `Microsoft.IdentityModel`, `Microsoft.IdentityModel.SecurityTokenService`, a `Microsoft.IdentityModel.Threading`.|  
|<xref:System.Security.Claims?displayProperty=nameWithType>|Obsahuje třídy, které představují deklarace identity, založené na deklaracích identity, objekty zabezpečení na základě deklarací identity a jiné artefakty model deklarovaných identit. Obsahuje třídy z `Microsoft.IdentityModel.Claims` oboru názvů.|  
|<xref:System.IdentityModel.Tokens?displayProperty=nameWithType>|Obsahuje třídy, které představují tokeny zabezpečení, obslužné rutiny tokenů zabezpečení a další artefakty tokenu zabezpečení. Obsahuje třídy z následujících oborů názvů WIF 3.5: `Microsoft.IdentityModel.Tokens`, `Microsoft.IdentityModel.Tokens.Saml11`, a `Microsoft.IdentityModel.Tokens.Saml2`.|  
|<xref:System.IdentityModel.Services?displayProperty=nameWithType>|Obsahuje třídy, které se používají ve scénářích pasivní (WS-Federation). Obsahuje třídy z `Microsoft.IdentityModel.Web` oboru názvů.|  
|<xref:System.ServiceModel.Security?displayProperty=nameWithType>|Třídy, které představují WCF kontrakty, kanály, obsluha hostitelů a další artefakty, které se používají ve scénářích aktivní (WS-Trust) jsou teď v tomto oboru názvů. Technologie WIF 3.5, tyto třídy byly v `Microsoft.IdentityModel.Protocols.WSTrust` oboru názvů.|  
  
> [!IMPORTANT]
>  Následující `System.IdentityModel` obory názvů obsahují třídy, které implementují model deklarovaných identit WCF: <xref:System.IdentityModel.Claims?displayProperty=nameWithType>, <xref:System.IdentityModel.Policy?displayProperty=nameWithType>, a <xref:System.IdentityModel.Selectors?displayProperty=nameWithType>. Model deklarovaných identit technologie WCF je nahrazen technologií WIF. Při vytváření řešení založených na technologii WIF byste neměli používat třídy v těchto třech oborech názvů.  
  
### <a name="changes-due-to-net-integration"></a>Změny z důvodu .NET – integrace  
 Technologie WIF je nyní integrován do rozhraní .NET Framework. Většina tříd identity a zabezpečení rozhraní .NET jsou nyní odvozeny z <xref:System.Security.Claims.ClaimsIdentity?displayProperty=nameWithType> a <xref:System.Security.Claims.ClaimsPrincipal?displayProperty=nameWithType>. Výsledky v následující změny v technologie WIF 4.5:  
  
-   Třídy technologie WIF, které představují deklarací identity a objekty zabezpečení nyní existuje v <xref:System.Security.Claims?displayProperty=nameWithType> oboru názvů.  
  
    > [!IMPORTANT]
    >  <xref:System.IdentityModel.Claims?displayProperty=nameWithType> Obor názvů obsahuje třídy, které reprezentují artefakty v modelu deklarovaných identit WCF. Mnohé z těchto tříd mají názvy, které jsou stejné jako třídy technologie WIF; například `Claims`. Nepoužívejte tyto třídy při sestavování řešení založená na technologii WIF.  
  
-   Identity a instanční objekt třídy rozhraní .NET jsou nyní odvozeny přímo z <xref:System.Security.Claims.ClaimsIdentity?displayProperty=nameWithType> a <xref:System.Security.Claims.ClaimsPrincipal?displayProperty=nameWithType>, které představují založené na deklaracích identity a objekty zabezpečení. Z tohoto důvodu rozhraní technologie WIF 3.5 `IClaimsIdentity` a `IClaimsPrincipal` už nejsou potřeba a nejsou k dispozici v technologie WIF 4.5.  
  
-   Because.NET identity a instanční objekt třídy jako <xref:System.Security.Principal.WindowsIdentity?displayProperty=nameWithType> a <xref:System.Security.Principal.WindowsPrincipal?displayProperty=nameWithType> jsou nyní odvozeny z <xref:System.Security.Claims.ClaimsIdentity> a <xref:System.Security.Claims.ClaimsPrincipal>, mají integrované funkce deklarací identity. Pro tento důvod, specifické pro deklarace identity a instanční objekt třídy, jako `WindowsClaimsIdentity` a `WindowsClaimsPrincipal` , které byly součástí technologie WIF 3.5 už nejsou potřeba a neexistují v technologie WIF 4.5.  
  
### <a name="other-changes-to-wif-functionality"></a>Další změny funkcí technologie WIF  
 Kromě změn názvů a změny z důvodu integraci s .NET k následujícím změnám obecné funkcí technologie WIF do technologie WIF 4.5.  
  
-   `Microsoft.IdentityModel.ExceptionMapper` Třída, která poskytuje funkce, které umožňuje mapování výjimky na konkrétní chyby SOAP, Odebereme.  
  
-   Výjimka povrchu se výrazně snižují.  
  
-   Mnoho tříd, které definuje protokol nebo WS-* konkrétní konstanty se odebraly; například `Microsoft.IdentityModel.WSAddressing10Constants` třídy, které definuje konstanty související s WS-Addressing 1.0.  
  
-   Deklarace identity do tokenů služby Windows (c2wts) a jeho přidružených tříd v `Microsoft.IdentityModel.WindowsTokenService` obor názvů se odeberou.  
  
### <a name="wif-configuration-changes"></a>Změny konfigurace WIF  
 Mnoho změn v konfiguračním souboru byly způsobeny aktualizace oboru názvů v technologie WIF 4.5. Představte si třeba následující technologie WIF 3.5 položku v `<httpModules>` přidejte Správce ověřování WS-Federation pro aplikace:  
  
```xml  
<add name="WSFederationAuthenticationModule" type="Microsoft.IdentityModel.Web.WSFederationAuthenticationModule, Microsoft.IdentityModel, Version=3.5.0.0, Culture=neutral, PublicKeyToken=abcd … 5678" />  
```  
  
 Tato položka byla aktualizována v nové obory názvů a sestavení verze WIF 4.5:  
  
```xml  
<add name="WSFederationAuthenticationModule" type="System.IdentityModel.Services.WSFederationAuthenticationModule, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=abcd … 5678"/>  
```  
  
 Následující seznam obsahuje hlavní změny do konfiguračního souboru pro technologie WIF 4.5.  
  
-   `<microsoft.identityModel>` Části je teď [ \<system.identityModel >](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel.md) oddílu.  
  
-   `<service>` Prvek je nyní [ \<identityConfiguration >](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) elementu.  
  
-   Nová část, [ \<system.identityModel.services >](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel-services.md), byla přidána k určení nastavení, která řídí chování v pasivním scénáře (WS-Federation).  
  
-   [ \<FederationConfiguration >](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md) elementu a jeho podřízené prvky byly přesunuté z `<service>` element v technologie WIF 3.5 na nový `<system.identityModel.services>` elementu.  
  
-   Několik prvků, které by mohl být specifikován v úrovni služby přímo pod `<service>` element v technologie WIF 3.5 byly omezené na zadané v části [ \<securityTokenHandlerConfiguration >](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md) element. (Je pořád lze zadat v rámci [ \<identityConfiguration >](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) prvek v technologie WIF 4.5 z důvodu zpětné kompatibility.)  
  
 Úplný seznam konfigurační prvky technologie WIF 4.5 naleznete v tématu [schématu konfigurace WIF](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/index.md).  
  
### <a name="visual-studio-tooling-changes"></a>Změny nástrojů sady Visual Studio  
 Technologie WIF 3.5 SDK nabízí samostatný federační nástroj FedUtil.exe (řádku FedUtil), který můžete použít k externí správy identit do aplikací do služby tokenů zabezpečení (STS) s podporou technologie WIF. Tento nástroj přidáno nastavení technologie WIF do konfiguračního souboru aplikace umožňuje aplikaci získat tokeny zabezpečení z jednoho nebo více tokenů zabezpečení a se zobrazí v sadě Visual Studio prostřednictvím **přidat odkaz na službu STS** tlačítko. Řádku FedUtil se nedodává s WIF 4.5. Místo toho technologie WIF 4.5 podporuje nové rozšíření sady Visual Studio s názvem nástroj Identity and Access Tool for Visual Studio 2012, můžete upravit konfigurační soubor vaší aplikace pomocí technologie WIF nastavením požadovaným pro externí správu identit do služby STS. Nástroj Identity and Access Tool implementuje také služby tokenů zabezpečení volá místní službu tokenů zabezpečení, který vám pomůže otestovat aplikaci s podporou technologie WIF. V mnoha případech se vyloučí tuto funkci nutné k vytváření vlastních služeb STS, které byly často nezbytné ve technologie WIF 3.5 pro testování řešení ve vývoji. Z tohoto důvodu šablony služby STS již nejsou podporovány v aplikaci Visual Studio 2012; třídy, které podporují vývoj služby tokenů zabezpečení jsou však stále k dispozici v technologie WIF 4.5.  
  
 Můžete nainstalovat nástroj Identity and Access Tool z rozšíření a aktualizace správce v sadě Visual Studio nebo si můžete stáhnout z následující stránky na galerii kódu: [Identity and Access Tool for Visual Studio 2012 ve Galerii kódu](https://go.microsoft.com/fwlink/?LinkID=245849). Změny nástrojů sady Visual Studio jsou shrnuty v následujícím seznamu:  
  
-   Přidat odkaz na službu STS funkce se odebere. Pokud chcete nahrazení je nástroj Identity and Access Tool.  
  
-   Šablony služby STS Visual Studio se odeberou. Můžete použít místní služba tokenů zabezpečení, která je dostupná prostřednictvím Identity and Access Tool pro testování řešení identit, které vyvíjíte pomocí technologie WIF. Konfigurace místní služby tokenů zabezpečení můžete upravit tak, aby přizpůsobení deklarací identity, které najde.  
  
-   Samostatné nástrojem Federation Utility (řádku FedUtil) není k dispozici v technologie WIF 4.5. Nástroj Identity and Access Tool můžete upravit konfigurační soubory pro externí správu identit do služby STS.  
  
 Další informace o nástroj Identity and Access Tool najdete v tématu [Identity and Access Tool for Visual Studio 2012](../../../docs/framework/security/identity-and-access-tool-for-vs.md)  
  
<a name="BKMK_ToolingChanges"></a>   
### <a name="passive-ws-federation-scenarios"></a>Scénáře pasivní (WS-Federation):  
  
-   Třídy, které podporují scénáře pasivní se přesunuly do <xref:System.IdentityModel.Services?displayProperty=nameWithType> oboru názvů. Technologie WIF 3.5 tyto třídy byly v `Microsoft.IdentityModel.Web` oboru názvů.  
  
-   Třídy v `Microsoft.IdentityModel.Web.Configuration` obor názvů se přesunuly do <xref:System.IdentityModel.Services.Configuration?displayProperty=nameWithType>. Tyto třídy představují konkrétní objekty do konfigurace v pasivním scénáře.  
  
-   `FederatedPasssiveSignInControl` Už není podporovaná; všechny třídy v `Microsoft.IdentityModel.Web.Controls` obor názvů se odstranily z technologie WIF 4.5.  
  
-   Ověřovací modul WS-Federation (<xref:System.IdentityModel.Services.WSFederationAuthenticationModule>) odhlašování funkce se liší od technologie WIF 3.5. Další podrobnosti o tom, jak odhlašování funguje v technologie WIF 4.5 naleznete v tématu <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> třídě.  
  
### <a name="active-wcfws-trust-scenarios"></a>Aktivní (WCF/WS-Trust) scénáře:  
  
-   `Microsoft.IdentityModel.Protocols.WSTrust` Obor názvů byla rozdělena, hlavně na dva obory názvů v technologie WIF 4.5. Třídy, které reprezentují artefakty, které jsou specifické pro protokol WS-Trust jsou teď v <xref:System.IdentityModel.Protocols.WSTrust?displayProperty=nameWithType>. To zahrnuje třídy typu <xref:System.IdentityModel.Protocols.WSTrust.RequestSecurityToken>. Třídy, které představují kontrakty služeb, kanály, obsluha hostitelů a další artefakty, které jsou součástí aplikací WCF pomocí WS-Trust se přesunuly do <xref:System.ServiceModel.Security?displayProperty=nameWithType>, například <xref:System.ServiceModel.Security.IWSTrust13AsyncContract> rozhraní.  
  
-   Konfigurace aplikace WCF pro použití technologie WIF je výrazně zjednodušené. Dříve `Microsoft.IdentityModel.Configuration.ConfigureServiceHostBehaviorExtensionElement` má být přidán jako rozšíření chování a tato funkce se použijí k Klínový technologie WIF do chování služby tak, že zadáte `<federatedServiceHostConfiguration>` elementu. Technologie WIF 4.5 obsahuje těsněji integrované s použitím technologie WCF. Nyní povolení technologie WIF ve službě WCF zadáním `useIdentityConfiguration` atribut na `<system.serviceModel>` / `<behaviors>` / `<serviceBehaviors>` / `<serviceCredentials>` element jako následující kód XML:  
  
    ```xml  
    <serviceCredentials useIdentityConfiguration="true">  
        <!--Certificate added by Identity And Access VS Package.  Subject='CN=localhost', Issuer='CN=localhost'. Make sure you have this certificate installed. The Identity and Access tool does not install this certificate.-->  
        <serviceCertificate findValue="CN=localhost" storeLocation="LocalMachine" storeName="My" x509FindType="FindBySubjectDistinguishedName" />  
    </serviceCredentials>  
    ```  
  
-   V technologii WIF 4.5 služby je nutné zadat certifikát používaný serverem služby aktivní (WCF) na hostitele služby. V konfiguraci, můžete udělat prostřednictvím `<system.serviceModel>` / `<behaviors>` / `<serviceBehaviors>` / `<serviceCredentials>` / `<serviceCertificate>` elementu, jak je znázorněno v předchozím příkladu. Technologie WIF 3.5 by mohl být specifikován certifikát služby prostřednictvím `<serviceCertificate>` podřízený element technologie WIF `<service>` elementu. Tato funkce v technologie WIF 4.5; neexistuje. Zadejte `<serviceCertificate>` element v rámci `<serviceCredentials>` element místo.  
  
-   Třídy používané k Klínový technologie WIF 3.5 do WCF již existuje. To zahrnuje následující třídy v `Microsoft.IdentityModel.Tokens` obor názvů: `FederatedSecurityTokenManager`, `FederatedServiceCredentials`, a `IdentityModelServiceAuthorizationManager`, jakož i `Microsoft.IdentityModel.Configuration.ConfigureServiceHostBehaviorExtensionElement` třídy.  
  
## <a name="enabling-wif-35-in-windows-8"></a>Povolení technologie WIF 3.5 v systému Windows 8  
 Technologie WIF 4.5 je součástí rozhraní .NET 4.5, je automaticky povolen v počítačích se systémem Windows 8 a Windows Server 2012 a v systému Windows 8 nebo Windows Server 2012 bude ve výchozím nastavení spouští aplikace, které jsou vytvořené pomocí technologie WIF 4.5. Potřebujete ale spouštění aplikací, které byly vytvořeny s použitím technologie WIF 3.5 na počítači se systémem Windows 8 nebo Windows Server 2012. V takovém případě je potřeba povolit technologii WIF 3.5 na cílovém počítači. Na počítači se systémem Windows 8 můžete to provést pomocí nástroje Deployment Image Servicing and Management (DISM). Na počítači se systémem Windows Server 2012, můžete pomocí nástroje DISM nebo můžete použít rutinu prostředí Windows PowerShell `Add-WindowsFeature` rutiny. V obou případech může být vyvolána příslušnými příkazy v příkazovém řádku nebo z uvnitř prostředí Windows PowerShell.  
  
 Následující příkazy ukazují, jak pomocí nástroje DISM z příkazového řádku nebo v prostředí Windows PowerShell. Ve výchozím nastavení modul DISM PowerShell je součástí systému Windows 8 a Windows Server 2012 a nemusí být importován. Další informace o použití DISM pomocí Windows Powershellu najdete v tématu [tom, jak pomocí nástroje DISM prostředí Windows PowerShell](https://go.microsoft.com/fwlink/?LinkId=254419).  
  
 Pokud chcete povolit technologii WIF 3.5 a to pomocí nástroje DISM:  
  
```  
dism /online /enable-feature:windows-identity-foundation  
```  
  
 Postup při zakázání technologie WIF 3.5 a to pomocí nástroje DISM:  
  
```  
dism /online /disable-feature:windows-identity-foundation  
```  
  
 Chcete-li zkontrolovat funkcí, které jsou povolené nebo zakázané, pomocí nástroje DISM:  
  
```  
dism /online /get-features  
```  
  
 V počítačích se systémem Windows Server 2012, můžete případně povolit technologii WIF 3.5, pomocí prostředí Windows PowerShell `Add-WindowsFeature` rutiny. Provedete to tak že z příkazového řádku můžete zadat následující příkaz:  
  
```  
powershell "add-windowsfeature windows-identity-foundation"  
```  
  
 Z uvnitř prostředí Windows PowerShell, můžete zadat příkaz přímo:  
  
```  
add-windowsfeature windows-identity-foundation  
```  
  
> [!NOTE]
>  Protože mnoho třídy technologie WIF 3.5 a WIF 4.5 sdílí stejné názvy, při použití technologie WIF 3.5 a WIF 4.5 společně, nezapomeňte použít plně kvalifikované třídě názvy nebo aliasy oboru názvů použijte k rozlišení mezi třídy technologie WIF 3.5 a WIF 4.5.  
  
## <a name="see-also"></a>Viz také:
- [Schéma konfigurace WIF](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/index.md)
- [Mapování oborů názvů mezi WIF 3.5 a WIF 4.5](../../../docs/framework/security/namespace-mapping-between-wif-3-5-and-wif-4-5.md)
- [Novinky ve Windows Workflow Foundation 4.5](../../../docs/framework/security/whats-new-in-wif.md)
- [Nástroj Identita a přístup pro Visual Studio 2012](../../../docs/framework/security/identity-and-access-tool-for-vs.md)
