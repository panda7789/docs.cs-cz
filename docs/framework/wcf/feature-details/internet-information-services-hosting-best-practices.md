---
title: Doporučené postupy hostování Internetové informační služby
ms.date: 03/30/2017
ms.assetid: 0834768e-9665-46bf-86eb-d4b09ab91af5
ms.openlocfilehash: 119f14df9d46883a33272903558d83128501b293
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="internet-information-services-hosting-best-practices"></a>Doporučené postupy hostování Internetové informační služby
Toto téma popisuje některé z osvědčených postupů pro hostování služby Windows Communication Foundation (WCF).  
  
## <a name="implementing-wcf-services-as-dlls"></a>Implementace služby WCF jako knihovny DLL  
 Implementace službou WCF umožňuje služby jako knihovny DLL, která je nasazena do adresáře \bin webové aplikace, že můžete znovu použít službu mimo model webové aplikace, například v testovacím prostředí, která nemusí mít nasazený Internetové informační služby (IIS).  
  
## <a name="service-hosts-in-iis-hosted-applications"></a>Hostitelé služeb v aplikace hostované služby IIS  
 Vytvořit nové hostitele služby tohoto naslouchání na síťové přenosy není nativně podporované službou IIS hostování prostředí nepoužívejte imperativní rozhraní API hostování na vlastním serveru (například [!INCLUDE[iis601](../../../../includes/iis601-md.md)] k hostování TCP služby, protože komunikaci TCP nativně nepodporují [!INCLUDE[iis601](../../../../includes/iis601-md.md)]). Tento přístup se nedoporučuje. Hostitelé služeb z vytvořili imperativní nejsou známá v rámci služby IIS hostitelské prostředí. Kritický bod je, že zpracování provádí imperativní vytvořený služby není pozornost službou IIS při určování, zda je v nečinnosti hostování fondu aplikací. Výsledkem je, že aplikace, které mají takové hostitelé služeb z imperativní vytvořený mají hostování prostředí služby IIS, které intenzivně uvolní procesy hostitele služby IIS.  
  
## <a name="uris-and-iis-hosted-endpoints"></a>Koncové body hostované službou IIS a identifikátory URI  
 Koncové body pro služby hostované službou IIS musí být nakonfigurovaný pomocí relativní identifikátory Uniform Resource (Identifier), není absolutní adresy. To zaručuje, že adresa koncového bodu spadá do sadu adresy URI, které patří k hostování aplikací a zajišťuje, že na základě zpráv aktivace se stane dle očekávání.  
  
## <a name="state-management-and-process-recycling"></a>Stav správy a recyklace procesů  
 Hostitelské prostředí služby IIS je optimalizovaná pro služby, které neudržují lokálního stavu v paměti. Služby IIS recykluje procesu hostitele v reakci na celou řadu událostí externí i interní způsobuje žádný volatile stav uložena výhradně v paměti, aby ztratí. Služby hostované ve službě IIS měli uložit jejich stavu externího procesu (například v databázi) nebo do mezipaměti v paměti, mohou být snadno znovu vytvořit Pokud události recyklace aplikace dojde k.  
  
> [!NOTE]
>  Protokoly WCF používají pro zabezpečení a spolehlivost zpráva vrstvy provedete pomocí volatile stavu v paměti. Spolehlivé relace WCF a zabezpečení relací může neočekávaně ukončit kvůli aplikace recykluje. Aplikace hostované službou IIS, které pomocí těchto protokolů by měl buď závisí na něco jiného než klíč relace zadaný WCF pro korelace stavu aplikační vrstvu (například aplikační vrstvě konstrukce nebo vlastní korelace záhlaví) nebo zakázat Proces služby IIS recyklování pro hostované aplikace.  
  
## <a name="optimizing-performance-in-middle-tier-scenarios"></a>Optimalizace výkonu ve scénářích střední vrstvy  
 Pro optimální výkon v *střední vrstvy scénář*– služba, která volá k jiným službám v reakci na příchozí zprávy – vytvoření klienta služby WCF službě vzdálené instance jednou a opakovaně ji používat napříč více příchozí požadavky. Vytváření instancí klienti služby WCF je relativní vzhledem k provedení služby v existující instanci klienta volat náročná operace a střední vrstvy scénáře vytváření zvýšení výkonu odlišné pomocí ukládání do mezipaměti vzdálených klientů napříč požadavky. Klienti služby WCF jsou bezpečné pro přístup z více vláken, takže není nutné k synchronizaci přístup ke klientovi napříč více vláken.  
  
 Střední vrstvy scénáře také vytvořit zvýšení výkonu pomocí asynchronní rozhraní API generovaných `svcutil /a` možnost. `/a` Možnost příčiny [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) ke generování `BeginXXX/EndXXX` metody pro každou operaci služby, která umožňuje vzdálené volání potenciálně dlouho běžící na vlákna na pozadí.  
  
## <a name="wcf-in-multi-homed-or-multi-named-scenarios"></a>WCF ve scénářích s více adresami nebo více s názvem  
 Nasazením služby WCF v IIS webové farmy služby, kde sadu počítačů sdílí společný externí název (například http://www.contoso.com) , ale jsou jednotlivě používala různé názvy hostitelů (například http://www.contoso.com může směrovat přenosy na dva různé počítače s názvem http://machine1.internal.contoso.com a http://machine2.internal.contoso.com). Tento scénář nasazení plně podporuje WCF, ale vyžaduje zvláštní konfiguraci služby IIS webu hostování služby WCF, které chcete zobrazit správný název hostitele (external) v metadatech služby (Web Services Description Language).  
  
 Chcete-li zajistit, aby se správný název hostitele v metadatech služby WCF generuje, nakonfigurovat výchozí identitu pro web služby IIS, který je hostitelem služby WCF použít explicitní název hostitele. Počítače, které se nacházejí v rámci farmy www.contoso.com by měl použít například vazba webu služby IIS *:80:www.contoso.com pro protokol HTTP a \*: 443:www.contoso.com pro protokol HTTPS.  
  
 Vazby webu služby IIS můžete nakonfigurovat pomocí modulu snap-in služby IIS Microsoft Management Console (MMC).  
  
## <a name="application-pools-running-in-different-user-contexts-overwrite-assemblies-from-other-accounts-in-the-temporary-folder"></a>Fondy aplikací, které jsou spuštěné v kontextu jiného uživatele přepsat sestavení z jiné účty v dočasné složce  
 K zajištění, že fondy aplikací, které jsou spuštěné v kontextu jiného uživatele nelze přepsat sestavení z jiné účty v dočasný [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] soubory, složky, použijte jiný identity a dočasných složek pro různé aplikace. Například, pokud máte dva/Application1 virtuální aplikace a / Application2, můžete vytvořit dvěma fondy aplikací, A a B, pomocí dvou různých identit. Fond aplikací A můžete spustit identity v rámci jednoho uživatele (uživatel1), zatímco fond aplikací B může běžet pod jinou identitu uživatele (uživatel2) a nakonfigurovat/Application1 A použití a /Application2 používat B.  
  
 V souboru Web.config, můžete nakonfigurovat dočasnou složku použitím \< system.web/compilation/@tempFolder>. Pro/Application1 může být "c:\tempForUser1" a pro application2 může být "c:\tempForUser2". Udělte odpovídající oprávnění k zápisu do těchto složek pro dvě identity.  
  
 Potom uživatel2 nelze změnit složku generování kódu pro /application2 (v rámci c:\tempForUser1).  
  
## <a name="enabling-asynchronous-processing"></a>Povolení asynchronního zpracování  
 Ve výchozím nastavení jsou zpracovávány zprávy odeslané do služby WCF hostované v rámci služby IIS 6.0 a starší synchronním způsobem. ASP.NET volá do WCF ve vlastním vlákně (pracovní vlákno ASP.NET) a WCF používá jiné vlákno pro zpracování požadavku. Na pracovní vlákno ASP.NET obsahuje WCF, až do dokončení jeho zpracování. To vede k synchronní zpracování požadavků. Asynchronní zpracování požadavků umožňuje větší škálovatelnost, protože snižuje počet vláken, které jsou potřebné ke zpracování žádosti – WCF nemá nastaveno vlákno ASP.NET při zpracování požadavku. Použití asynchronní chování není doporučeno pro počítače, které běží služby IIS 6.0, protože neexistuje žádný způsob, jak omezit příchozích požadavků, které otevře serveru *Denial Of Service* útoky (DOS). Od verze služby IIS 7.0, bylo zavedeno omezení počtu souběžných požadavků: `[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ASP.NET\2.0.50727.0]"MaxConcurrentRequestsPerCpu`. Pomocí této nové omezení je bezpečné použít asynchronní zpracování.  Ve výchozím nastavení ve službě IIS 7.0 je zaregistrovaný modul a asynchronní obslužné rutiny. Pokud to byl vypnut, můžete ručně povolit asynchronní zpracování požadavků v souboru Web.config vaší aplikace. Nastavení použijete, závisí na vaší `aspNetCompatibilityEnabled` nastavení. Pokud máte `aspNetCompatibilityEnabled` nastavena na `false`, nakonfigurujte `System.ServiceModel.Activation.ServiceHttpModule` jak je znázorněno v následujícím fragmentu kódu konfigurace.  
  
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
  
 Pokud máte `aspNetCompatibilityEnabled` nastavena na `true`, nakonfigurujte `System.ServiceModel.Activation.ServiceHttpHandlerFactory` jak je znázorněno v následujícím fragmentu kódu konfigurace.  
  
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
 [Ukázky služby hostování](http://msdn.microsoft.com/library/f703a3f6-0fba-418a-a92f-7ce75ccfa47e)  
 [Hostování funkcí systému Windows Server App Fabric](http://go.microsoft.com/fwlink/?LinkId=201276)
