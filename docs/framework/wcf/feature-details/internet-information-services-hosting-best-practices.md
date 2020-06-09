---
title: Doporučené postupy hostování Internetové informační služby
ms.date: 03/30/2017
ms.assetid: 0834768e-9665-46bf-86eb-d4b09ab91af5
ms.openlocfilehash: e62fed4f6a711ecc317b8f758d4948a477d136e1
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84595268"
---
# <a name="internet-information-services-hosting-best-practices"></a>Doporučené postupy hostování Internetové informační služby
Toto téma popisuje některé osvědčené postupy pro hostování služby Windows Communication Foundation (WCF).  
  
## <a name="implementing-wcf-services-as-dlls"></a>Implementace služeb WCF jako knihoven DLL  
 Implementace služby WCF jako knihovny DLL, která je nasazena v adresáři \Bin webové aplikace, umožňuje znovu použít službu mimo model webové aplikace, například v testovacím prostředí, které nemusí mít nasazenou službu Internetová informační služba (IIS).  
  
## <a name="service-hosts-in-iis-hosted-applications"></a>Hostitelé služeb v aplikacích hostovaných službou IIS  
 Nepoužívejte imperativní rozhraní API pro samoobslužné hostování k vytváření nových hostitelů služby, které naslouchají síťovým přenosům, které nejsou nativně podporované hostitelským prostředím služby IIS (například IIS 6,0 pro hostování služeb TCP, protože komunikace TCP není nativně podporovaná ve službě IIS 6,0). Tento přístup se nedoporučuje. Hostitelé služeb, které jsou vytvořeny imperativně, nejsou v hostitelském prostředí služby IIS známy. Kritickým bodem je, že zpracování prováděné imperativně vytvořenými službami není pro službu IIS účtováno, když určuje, zda je fond hostitelských aplikací nečinný. Výsledkem je, že aplikace, které mají tyto imperativně vytvořené hostitele služeb, mají hostitelské prostředí služby IIS, které neagresivním způsobem uvolňuje hostitelské procesy služby IIS.  
  
## <a name="uris-and-iis-hosted-endpoints"></a>Identifikátory URI a koncové body hostované službou IIS  
 Koncové body služby hostované službou IIS by měly být nakonfigurované pomocí relativních identifikátorů URI (Uniform Resource Identifier), nikoli absolutních adres. To zaručuje, že adresa koncového bodu spadá do sady adres URI, které patří do hostující aplikace, a zajišťuje tak, že aktivace na základě zpráv proběhne podle očekávání.  
  
## <a name="state-management-and-process-recycling"></a>Recyklace správy stavů a procesů  
 Prostředí hostování služby IIS je optimalizované pro služby, které neudržují místní stav v paměti. Služba IIS recykluje hostitelský proces v reakci na celou řadu externích a interních událostí, což způsobí ztrátu jakéhokoli nestálého stavu uloženého exkluzivně v paměti. Služby hostované ve službě IIS by měly ukládat svůj stav externě do procesu (například v databázi) nebo v mezipaměti v paměti, kterou lze snadno znovu vytvořit, pokud dojde k události recyklace aplikace.  
  
> [!NOTE]
> Protokoly WCF používají pro spolehlivost a zabezpečení vrstvy zpráv a využívají stálý stav v paměti. Spolehlivé relace WCF a relace zabezpečení můžou neočekávaně skončit kvůli recyklaci aplikací. Aplikace hostované ve službě IIS, které využívají tyto protokoly, by měly buď záviset na něčem, než je klíč relace poskytnutý službou WCF pro korelaci stavu aplikační vrstvy (například konstrukce aplikační vrstvy nebo vlastní hlavičky korelace), nebo vypnout recyklaci procesů IIS pro hostovanou aplikaci.  
  
## <a name="optimizing-performance-in-middle-tier-scenarios"></a>Optimalizace výkonu ve scénářích střední vrstvy  
 Pro zajištění optimálního výkonu ve *scénáři střední vrstvy*– služba, která volá jiné služby v reakci na příchozí zprávy – vytvoří instanci klienta služby WCF pro vzdálenou službu jednou a znovu ji použije v rámci několika příchozích požadavků. Instance klientů služby WCF je náročná operace, která souvisí s tím, že se bude volat služba na stávající instanci klienta, a scénáře střední vrstvy vytvářejí jedinečné nárůsty výkonu ukládáním vzdálených klientů do mezipaměti mezi požadavky. Klienti služby WCF jsou bezpečné pro přístup z více vláken, takže není nutné synchronizovat přístup k klientovi napříč více vlákny.  
  
 Scénáře střední vrstvy také poskytují nárůst výkonu pomocí asynchronních rozhraní API generovaných `svcutil /a` možností. `/a`Možnost způsobí, že nástroj pro dodávání [metadat (Svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) vygeneruje `BeginXXX/EndXXX` metody pro každou operaci služby, což umožňuje spouštět potenciálně dlouhodobá volání vzdálených služeb na vláknech na pozadí.  
  
## <a name="wcf-in-multi-homed-or-multi-named-scenarios"></a>WCF ve scénářích s více adresami nebo s více názvy  
 Služby WCF můžete nasadit v rámci webové farmy služby IIS, kde sada počítačů sdílí společný externí název (například `http://www.contoso.com` ), ale jsou jednotlivě adresovány různými názvy hostitelů (například `http://www.contoso.com` může směrovat provoz do dvou různých počítačů s názvem `http://machine1.internal.contoso.com` a `http://machine2.internal.contoso.com` ). V tomto scénáři nasazení je služba WCF plně podporovaná, ale vyžaduje speciální konfiguraci webu služby IIS hostující služby WCF, aby se zobrazil správný (externí) název hostitele v metadatech služby (Web Services Description Language).  
  
 Aby se zajistilo, že se v metadatech služby vygeneruje správný název hostitele, nakonfigurujte výchozí identitu pro web IIS, který je hostitelem služeb WCF, aby používal explicitní název hostitele. Například počítače, které se nacházejí v rámci farmy, `www.contoso.com` by měly používat vazbu webu IIS *: 80: www. contoso. com pro http a \* : 443: www. contoso. com pro protokol HTTPS.  
  
 Vazby webu služby IIS můžete konfigurovat pomocí modulu snap-in konzoly Microsoft Management Console (MMC) služby IIS.  
  
## <a name="application-pools-running-in-different-user-contexts-overwrite-assemblies-from-other-accounts-in-the-temporary-folder"></a>Fondy aplikací běžící v různých kontextech uživatele přepíší sestavení z jiných účtů v dočasné složce.  
 Chcete-li zajistit, aby fondy aplikací běžící v různých kontextech uživatelů nemohly přepsat sestavení z jiných účtů ve složce dočasných souborů ASP.NET, použijte pro různé aplikace různé identity a dočasné složky. Například pokud máte dvě virtuální aplikace/Application1 nebo Application2, můžete vytvořit dva fondy aplikací, a a B, se dvěma různými identitami. Fond aplikací A může běžet pod identitou jednoho uživatele (uživatel1), zatímco fond aplikací B může běžet pod identitou jiné uživatele (uživatel2), a nakonfigurovat/Application1 na použití a/Application2 pro použití B.  
  
 V souboru Web. config můžete dočasnou složku nakonfigurovat pomocí \<system.web/compilation/@tempFolder> . Pro/Application1 může být "c:\tempForUser1" a pro application2 může to být "c:\tempForUser2". Pro tyto dvě identity udělte odpovídající oprávnění k zápisu do těchto složek.  
  
 Uživatel2 nemůže měnit složku pro generování kódu pro/application2 (v c:\tempForUser1).  
  
## <a name="enabling-asynchronous-processing"></a>Povolení asynchronního zpracování  
 Ve výchozím nastavení jsou zprávy odesílané službě WCF hostované v rámci služby IIS 6,0 a starší zpracovávány synchronním způsobem. ASP.NET volá do WCF ve vlastním vlákně (pracovní vlákno ASP.NET) a WCF používá jiné vlákno ke zpracování žádosti. WCF drží do pracovního vlákna ASP.NET, dokud nedokončí jeho zpracování. To vede k synchronnímu zpracování požadavků. Asynchronní zpracování požadavků umožňuje větší škálovatelnost, protože snižuje počet vláken potřebných ke zpracování požadavku – technologie WCF není při zpracování žádosti ve vlákně ASP.NET. Pro počítače, na kterých běží služba IIS 6,0, se nedoporučuje používat asynchronní chování, protože neexistuje žádný způsob, jak omezit příchozí požadavky, které otevřou Server na útoky DoS ( *Denial of Service* ). Počínaje službou IIS 7,0 byla zavedena souběžná omezení požadavků: `[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ASP.NET\2.0.50727.0]"MaxConcurrentRequestsPerCpu` . Díky tomuto novému omezení je bezpečné použít asynchronní zpracování.  Ve výchozím nastavení je ve službě IIS 7,0 registrována asynchronní obslužná rutina a modul. Pokud je tato možnost vypnuta, můžete ručně povolit asynchronní zpracování požadavků v souboru Web. config vaší aplikace. Nastavení, která použijete, závisí na `aspNetCompatibilityEnabled` nastavení. Pokud jste `aspNetCompatibilityEnabled` nastavili na `false` , nakonfigurujte, `System.ServiceModel.Activation.ServiceHttpModule` jak je znázorněno v následujícím fragmentu konfigurace.  
  
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
  
 Pokud jste `aspNetCompatibilityEnabled` nastavili na `true` , nakonfigurujte, `System.ServiceModel.Activation.ServiceHttpHandlerFactory` jak je znázorněno v následujícím fragmentu konfigurace.  
  
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
- [Funkce hostování technologie Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677189(v=azure.10))
