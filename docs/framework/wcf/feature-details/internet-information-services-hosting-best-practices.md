---
title: Doporučené postupy hostování Internetové informační služby
ms.date: 03/30/2017
ms.assetid: 0834768e-9665-46bf-86eb-d4b09ab91af5
ms.openlocfilehash: 3be9d4c81f891ad898099ba9041a09b16388b7e4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184720"
---
# <a name="internet-information-services-hosting-best-practices"></a>Doporučené postupy hostování Internetové informační služby
Toto téma popisuje některé osvědčené postupy pro hostování služeb WCF (Windows Communication Foundation).  
  
## <a name="implementing-wcf-services-as-dlls"></a>Implementace služeb WCF jako knihoven DLL  
 Implementace služby WCF jako dll, která je nasazena do adresáře \bin webové aplikace, umožňuje znovu použít službu mimo model webové aplikace, například v testovacím prostředí, ve které nemusí být nasazena Internetová informační služba (IIS).  
  
## <a name="service-hosts-in-iis-hosted-applications"></a>Hostitelé služeb v aplikacích hostovaných službou IIS  
 Nepoužívejte imperativní samoobslužná síťová api k vytvoření nových hostitelů služeb, kteří naslouchají síťovým přenosům, která nejsou nativně podporována hostitelským prostředím služby IIS (například služba IIS 6.0 pro hostování služeb TCP, protože komunikace protokolu TCP není nativně podporována ve službě IIS 6.0). Tento přístup se nedoporučuje. Hostitelé služeb vytvoření imperativně nejsou v hostitelském prostředí služby IIS známi. Kritickým bodem je, že zpracování provedené imperativně vytvořenými službami není službou IIS zohledněno, když určuje, zda je fond hostitelských aplikací nečinný. Výsledkem je, že aplikace, které mají tak imperativně vytvořené hostitele služeb, mají hostitelské prostředí služby IIS, které agresivně likviduje hostitelské procesy služby IIS.  
  
## <a name="uris-and-iis-hosted-endpoints"></a>Identifikátory URI a koncové body hostované ve správě iis  
 Koncové body pro službu hostovanou službou IIS by měly být konfigurovány pomocí relativních identifikátorů jednotných prostředků (URI), nikoli s absolutními adresami. To zaručuje, že adresa koncového bodu spadá do sady adres URI, které patří do hostitelské aplikace, a zajišťuje, že aktivace založená na zprávě proběhne podle očekávání.  
  
## <a name="state-management-and-process-recycling"></a>Řízení státu a recyklace procesů  
 Hostitelské prostředí služby IIS je optimalizováno pro služby, které neudržují místní stav v paměti. Služba IIS recykluje hostitelský proces v reakci na různé externí a interní události, což způsobuje ztrátu stavu nestálého stavu uloženého výhradně v paměti. Služby hostované ve službě IIS by měly ukládat svůj stav mimo proces (například v databázi) nebo do mezipaměti v paměti, kterou lze snadno znovu vytvořit, pokud dojde k události recyklace aplikace.  
  
> [!NOTE]
> Protokoly WCF používá pro spolehlivost vrstvy zpráv a zabezpečení využít nestálého stavu v paměti. WCF spolehlivé relace a relace zabezpečení může ukončit neočekávaně z důvodu recyklace aplikací. Aplikace hostované službou IIS, které využívají tyto protokoly, by měly záviset na něčem jiném než na klíči relace poskytnutém wcf pro korelaci stavu aplikační vrstvy (například konstrukce aplikační vrstvy nebo vlastní korelační hlavičky) nebo zakázat Recyklace procesů služby IIS pro hostovanou aplikaci.  
  
## <a name="optimizing-performance-in-middle-tier-scenarios"></a>Optimalizace výkonu ve scénářích střední vrstvy  
 Pro optimální výkon ve *scénáři střední vrstvy*– službě, která volá na jiné služby v reakci na příchozí zprávy – instanci klienta služby WCF ke vzdálené službě jednou a znovu použít přes více příchozích požadavků. Vytváření inscenování klientů služeb WCF je nákladná operace vzhledem k volání služby na již existující instanci klienta a scénáře střední vrstvy vytvářejí odlišné zvýšení výkonu ukládáním vzdálených klientů do mezipaměti napříč požadavky. Klienti služeb WCF jsou bezpeční pro přístup z více vláken, takže není nutné synchronizovat přístup ke klientovi ve více vláknech.  
  
 Scénáře střední vrstvy také vytvářet zvýšení výkonu pomocí asynchronní `svcutil /a` api generované možnost. Tato `/a` možnost způsobí [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) generovat `BeginXXX/EndXXX` metody pro každou operaci služby, která umožňuje potenciálně dlouhotrvající volání vzdálených služeb, které mají být provedeny na podprocesech na pozadí.  
  
## <a name="wcf-in-multi-homed-or-multi-named-scenarios"></a>WCF ve scénářích s více domovy nebo s více názvemi  
 Služby WCF můžete nasadit uvnitř webové farmy služby IIS, kde sada `http://www.contoso.com`počítačů sdílí společný externí název (například) `http://www.contoso.com` ale jsou jednotlivě `http://machine1.internal.contoso.com` adresovány různými názvy hostitelů (například může směrovat provoz na dva různé počítače s názvem a `http://machine2.internal.contoso.com`). Tento scénář nasazení je plně podporován wcf, ale vyžaduje zvláštní konfiguraci webu služby IIS hostování wcf služby pro zobrazení správné (externí) název hostitele v metadatech služby (Web Services Description Language).  
  
 Chcete-li zajistit, aby se v metadatech služby, která wcf generuje, objevil správný název hostitele, nakonfigurujte výchozí identitu webu služby IIS, který je hostitelem služeb WCF, aby používal explicitní název hostitele. Například počítače, které jsou `www.contoso.com` umístěny uvnitř farmy, by měly používat vazbu webu služby IIS *:80:www.contoso.com pro protokol Y HTTP a \*:443:www.contoso.com pro protokol HTTPS.  
  
 Vazby webu služby IIS můžete konfigurovat pomocí modulu snap-in Konzoly MMC služby IIS.  
  
## <a name="application-pools-running-in-different-user-contexts-overwrite-assemblies-from-other-accounts-in-the-temporary-folder"></a>Fondy aplikací spuštěné v různých kontextech uživatelů přepisují sestavení z jiných účtů v dočasné složce  
 Chcete-li zajistit, aby fondy aplikací spuštěné v různých uživatelských kontextech nemohly přepsat sestavení z jiných účtů ve složce dočasných souborů ASP.NET, použijte pro různé aplikace různé identity a dočasné složky. Například pokud máte dvě virtuální aplikace /Application1 a / Application2, můžete vytvořit dva fondy aplikací, A a B, se dvěma různými identitami. Fond aplikací A lze spustit pod jednou identitou uživatele (uživatel1), zatímco fond aplikací B lze spustit pod jinou identitou uživatele (user2) a nakonfigurovat /Application1 pro použití A a /Application2 pro použití B.  
  
 V souboru Web.config můžete nakonfigurovat dočasnou složku pomocí \< system.web/compilation/@tempFolder>. Pro /Application1 může být "c:\tempForUser1" a pro application2 může být "c:\tempForUser2". Udělte těmto složkám odpovídající oprávnění k zápisu pro tyto dvě identity.  
  
 Potom user2 nelze změnit složku generování kódu pro /application2 (pod c:\tempForUser1).  
  
## <a name="enabling-asynchronous-processing"></a>Povolení asynchronního zpracování  
 Ve výchozím nastavení jsou zprávy odeslané službě WCF hostované v systému IIS 6.0 a starších zpráv zpracovány synchronně. ASP.NET volání do WCF ve vlastním vlákně (ASP.NET pracovní vlákno) a WCF používá jiné vlákno ke zpracování požadavku. WCF se drží na pracovní podproces ASP.NET, dokud nedokončí jeho zpracování. To vede k synchronní zpracování požadavků. Zpracování požadavků asynchronně umožňuje větší škálovatelnost, protože snižuje počet podprocesů potřebných ke zpracování požadavku –WCF nedrží ASP.NET vlákno při zpracování požadavku. Použití asynchronního chování se nedoporučuje pro počítače se službou IIS 6.0, protože neexistuje žádný způsob, jak omezit příchozí požadavky, které otevírají server útokům *dosunutí do paměti (DoS).* Počínaje službou IIS 7.0 byla zavedena souběžná akcelerátor požadavku: `[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ASP.NET\2.0.50727.0]"MaxConcurrentRequestsPerCpu`. S tímto novým omezením je bezpečné používat asynchronní zpracování.  Ve výchozím nastavení ve složce IIS 7.0 jsou registrovány asynchronní obslužná rutina a modul. Pokud byla tato možnost vypnuta, můžete ručně povolit asynchronní zpracování požadavků v souboru Web.config aplikace. Nastavení, která používáte, závisí na vašem `aspNetCompatibilityEnabled` nastavení. Pokud jste `aspNetCompatibilityEnabled` nastavili aplikaci `false`, nakonfigurujte tak, `System.ServiceModel.Activation.ServiceHttpModule` jak je znázorněno v následujícím fragmentu konfigurace.  
  
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
  
 Pokud jste `aspNetCompatibilityEnabled` nastavili aplikaci `true`, nakonfigurujte tak, `System.ServiceModel.Activation.ServiceHttpHandlerFactory` jak je znázorněno na následujícím fragmentu konfigurace.  
  
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

- [Ukázky hostování služeb](../samples/hosting.md)
- [Funkce hostování prostředků pro aplikace systému Windows Server](https://docs.microsoft.com/previous-versions/appfabric/ee677189(v=azure.10))
