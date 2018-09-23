---
title: Doporučené postupy hostování Internetové informační služby
ms.date: 03/30/2017
ms.assetid: 0834768e-9665-46bf-86eb-d4b09ab91af5
ms.openlocfilehash: 0ca5e20b846a1b10f5a52748ff06a4af958b2f4c
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/23/2018
ms.locfileid: "46703499"
---
# <a name="internet-information-services-hosting-best-practices"></a>Doporučené postupy hostování Internetové informační služby
Toto téma popisuje některé osvědčené postupy pro hostování služby Windows Communication Foundation (WCF).  
  
## <a name="implementing-wcf-services-as-dlls"></a>Implementace služby WCF jako knihovny DLL  
 Implementace WCF umožňuje služby jako knihovnu DLL, která je nasazena k adresáři \bin sady webovou aplikaci že můžete znovu použít službu mimo model webové aplikace, například v testovacím prostředí, která nemusí mít nasazený Internetové informační služby (IIS).  
  
## <a name="service-hosts-in-iis-hosted-applications"></a>Obsluha hostitelů v aplikace hostované v IIS  
 Nepoužívejte imperativní rozhraní API hostování na vlastním serveru k vytvoření nové služby hostitele tohoto naslouchání na síťové přenosy, které jsou nativně podporovány službou IIS hostitelské prostředí (například [!INCLUDE[iis601](../../../../includes/iis601-md.md)] hostovat TCP služby, protože komunikaci TCP nativně nepodporuje [!INCLUDE[iis601](../../../../includes/iis601-md.md)]). Tento přístup nedoporučuje. Obsluha hostitelů vytvořené imperativně nejsou známy v rámci služby IIS hostitelského prostředí. Kritický bod je, že zpracování provádí imperativně vytvořené služby nepočítá službou IIS při určování, zda je hostování fondu aplikací nečinný. Výsledkem je, že aplikace, které mají tyto hostitele imperativně vytvořené služby IIS hostitelské prostředí, které normálně agresivně uvolní hostitelské procesy služby IIS.  
  
## <a name="uris-and-iis-hosted-endpoints"></a>Identifikátory URI a hostované v IIS koncových bodů  
 Koncové body služby hostované v IIS musí být nakonfigurovaný pomocí relativní Uniform Resource Identifier (identifikátory URI), není absolutní adresy. Zaručí se tak, že adresa koncového bodu spadá do sady adresy URI, které patří do hostitelské aplikace a zajišťuje, že se aktivace založená na zprávách stane dle očekávání.  
  
## <a name="state-management-and-process-recycling"></a>Správa stavu a recyklace procesů  
 Hostitelské prostředí služby IIS je optimalizovaná pro služby, které nemají místní stavu v paměti. Služba IIS recykluje hostitelský proces v reakci na různé události externí a interní způsobující žádné nestálá stav uloženy výhradně ve paměti ke ztrátě. Služby hostované ve službě IIS byste uložit jejich stav externího procesu (například v databázi) nebo do mezipaměti v paměti, které mohou být snadno znovu vytvořit Pokud události recyklace aplikace dojde k.  
  
> [!NOTE]
>  Protokoly používají WCF pro zprávu vrstvy spolehlivost a zabezpečení provedete používají nestálá stavu v paměti. WCF spolehlivé relace a relace zabezpečení pravděpodobně dojde k neočekávanému ukončení z důvodu aplikace recykluje. Aplikace hostované službou IIS, kterým je použití těchto protokolů by neměly být buď závislé na něco jiného než klíč relace poskytované WCF ke korelaci stavu aplikační vrstvu (například aplikační vrstvu konstrukce nebo vlastní korelace záhlaví) nebo zakázat Proces služby IIS recykluje hostované aplikace.  
  
## <a name="optimizing-performance-in-middle-tier-scenarios"></a>Optimalizace výkonu ve scénářích střední vrstvy  
 Pro optimální výkon *scénář střední vrstvy*– služba, která vám sdělí, k dalším službám v reakci na příchozí zprávy – po vytvoření instance klienta služby WCF ve vzdálené službě a opakovaně ji používat napříč více příchozí požadavky. Vytvoření instance klienty služby WCF je náročná operace vzhledem k provádění volání na existující instanci klienta služby a střední vrstvy scénáře vytváření zvýšení výkonu různých ukládáním vzdálených klientů napříč požadavky. Klienty služby WCF jsou bezpečná pro vlákno, takže není nutné k synchronizaci přístupu k klienta napříč více vlákny.  
  
 Zvýšení výkonu střední vrstvy scénáře také vytvořit pomocí asynchronního rozhraní API generovaný `svcutil /a` možnost. `/a` Možnost způsobí, že [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) ke generování `BeginXXX/EndXXX` metod pro každou operaci služby, které umožňuje vzdálené volání potenciálně dlouhotrvající na vlákna na pozadí.  
  
## <a name="wcf-in-multi-homed-or-multi-named-scenarios"></a>U scénářů s více adresami nebo více pojmenované WCF  
 Nasadíte služby WCF v IIS webové farmy služby, kde sadu počítačů sdílet společný externí název (například http://www.contoso.com) ale jednotlivě řešený různé názvy hostitelů (například http://www.contoso.com může směrovat provoz do dvou různých počítačích s názvem http://machine1.internal.contoso.com a http://machine2.internal.contoso.com). Tento scénář nasazení plně podporuje WCF, ale vyžaduje speciální konfigurace web služby IIS, který hostuje služby WCF k zobrazení správné (externí) název hostitele v metadatech služby (Web Services Description Language).  
  
 Ujistěte se, že se zobrazí správný název hostitele v metadatech služby WCF generuje, nakonfigurujte výchozí identitu pro web služby IIS, který je hostitelem služeb WCF pro použití explicitní název hostitele. Počítačů umístěných ve farmě www.contoso.com byste například použít vazbu webu služby IIS z *:80:www.contoso.com pro protokol HTTP a \*: 443:www.contoso.com pro protokol HTTPS.  
  
 Vazby webu služby IIS můžete nakonfigurovat pomocí modulu snap-in Microsoft Management Console (MMC) služby IIS.  
  
## <a name="application-pools-running-in-different-user-contexts-overwrite-assemblies-from-other-accounts-in-the-temporary-folder"></a>Fondy aplikací, které jsou spuštěné v kontextech jiný uživatel přepsat sestavení z ostatních účtů v dočasné složce  
 K zajištění, že fondy aplikací, které jsou spuštěné v kontextu jiného uživatele nelze přepsat sestavení z ostatních účtů v dočasné [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] soubory, složky, použijte jiné identity a dočasných složek pro různé aplikace. Například, pokud máte dva/Application1 virtuální aplikace a / Application2, můžete vytvořit dvěma fondy aplikací A a B, s dvě různé identity. Fond aplikací A můžete spustit identitu v rámci jednoho uživatele (user1) zatímco můžete spustit fond aplikací B pod jinou identitou uživatele (uživatel2) a konfigurace/Application1 nepoužije a /Application2 používat služby serveru B.  
  
 V souboru Web.config, můžete nakonfigurovat dočasnou složku použitím \< system.web/compilation/@tempFolder>. Pro/Application1 může být "c:\tempForUser1" a pro application2 může být "c:\tempForUser2". Udělte odpovídající oprávnění k zápisu do těchto složek pro dvě identity.  
  
 Potom uživatel2 nelze změnit složku generování kódu pro /application2 (v rámci c:\tempForUser1).  
  
## <a name="enabling-asynchronous-processing"></a>Povolení asynchronní zpracování  
 Ve výchozím nastavení jsou zpracována zprávy odeslané do služby WCF hostované v rámci služby IIS 6.0 a starší synchronním způsobem. ASP.NET zavolá WCF ve vlastním vlákně (pracovní vlákno technologie ASP.NET) a WCF používá jiné vlákno zpracovat požadavek. WCF obsahuje do vlákna pracovního procesu ASP.NET, dokud se nedokončí její zpracování. To vede k synchronní zpracování požadavků. Asynchronní zpracování požadavků umožňuje větší škálovatelnost, protože snižuje počet vláken potřebný ke zpracování žádosti – WCF neobsahuje vlákno ASP.NET během zpracování požadavku. Pro počítače, které běží služby IIS 6.0, protože neexistuje žádný způsob, jak omezit příchozí žádosti, které otevřete serveru se nedoporučuje použití asynchronní chování *DOS* útoky (DOS). Od verze služby IIS 7.0, bylo zavedeno omezení souběžný požadavek: `[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ASP.NET\2.0.50727.0]"MaxConcurrentRequestsPerCpu`. Pomocí této nové omezení je bezpečné používat asynchronní zpracování.  Ve výchozím nastavení ve službě IIS 7.0 jsou registrované asynchronní obslužné rutiny a modul. Pokud to bylo vypnuto, můžete ručně povolit asynchronní zpracování požadavků v souboru Web.config vaší aplikace. Nastavení použijete, závisí na vaší `aspNetCompatibilityEnabled` nastavení. Pokud máte `aspNetCompatibilityEnabled` nastavena na `false`, nakonfigurujte `System.ServiceModel.Activation.ServiceHttpModule` jak je znázorněno v následujícím fragmentu kódu konfigurace.  
  
```xml  
<system.serviceModel>  
    <serviceHostingEnvironment aspNetCompatibilityEnabled="false" />      
  </system.serviceModel>  
  <system.webServer>  
    <modules>  
      <remove name="ServiceModel"/>  
      <add name="ServiceModel"   
           preCondition="integratedMode,runtimeVersionv2.0"   
           type="System.ServiceModel.Activation.ServiceHttpModule, System.ServiceModel,Version=3.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"/>  
    </modules>  
    </system.webServer>  
```  
  
 Pokud máte `aspNetCompatibilityEnabled` nastavena na `true`, nakonfigurujte `System.ServiceModel.Activation.ServiceHttpHandlerFactory` jak je znázorněno v následujícím fragmentu kódu config.  
  
```xml  
<system.serviceModel>  
    <serviceHostingEnvironment aspNetCompatibilityEnabled="true" />      
  </system.serviceModel>  
  <system.webServer>  
    <handlers>  
          <clear/>  
          <add name="TestAsyncHttpHandler"   
               path="*.svc"   
               verb="*"   
               type="System.ServiceModel.Activation.ServiceHttpHandlerFactory, System.ServiceModel, Version=3.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"           
               />  
    </handlers>      
  </system.webServer>  
```  
  
## <a name="see-also"></a>Viz také  
 [Služba, která hostuje ukázky](https://msdn.microsoft.com/library/f703a3f6-0fba-418a-a92f-7ce75ccfa47e)  
 [Hostování funkcí systému Windows Server App Fabric](https://go.microsoft.com/fwlink/?LinkId=201276)
