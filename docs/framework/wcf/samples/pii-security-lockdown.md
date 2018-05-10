---
title: Bezpečnostní uzamčení PII
ms.date: 03/30/2017
ms.assetid: c44fb338-9527-4dd0-8607-b8787d15acb4
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: ec8af8c7df9335774b1f3953f88c2aad438963b6
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="pii-security-lockdown"></a>Bezpečnostní uzamčení PII
Tato ukázka ukazuje, jak řídit několik funkcí souvisejících se zabezpečením služby Windows Communication Foundation (WCF) podle:  
  
-   Šifrování citlivých informací v konfiguračním souboru služby.  
  
-   Zamykání elementy v konfiguračním souboru tak, aby vnořené podadresářů služby nejde přepsat nastavení.  
  
-   Řízení protokolování z identifikovatelné osobní informace (PII) v protokolech trasování a zprávy.  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalován ve vašem počítači. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\SecurityLockdown`  
  
## <a name="discussion"></a>Diskusní  
 Každý z těchto funkcí může být používat samostatně nebo společně k řízení aspektů zabezpečení služby. Nejedná se o základní příručka k zabezpečení služby WCF.  
  
 Rozhraní .NET Framework konfigurační soubory, které mohou obsahovat citlivé údaje, jako je například připojovací řetězce pro připojení k databázím. Ve scénářích sdílené, hostovat webové může být žádoucí k zašifrování těchto informací v konfiguračním souboru pro službu, aby byla data obsažená v konfiguračním souboru odolné vůči běžné zobrazení. .NET framework 2.0 nebo novější má možnost šifrování části konfiguračního souboru pomocí aplikace Windows Data Protection programovací rozhraní (DPAPI), nebo zprostředkovatele šifrování RSA. Aspnet_regiis.exe pomocí rozhraní DPAPI nebo RSA můžete šifrovat vyberte části konfiguračního souboru.  
  
 Ve scénářích hostované webové je možné, že služby v podadresářích adresáře dalších služeb. Výchozí hodnota pro určení hodnoty konfigurace sémantického umožňuje konfigurační soubory v adresáři vnořené přepsat hodnoty konfigurace v nadřazeném adresáři. V některých situacích může být žádoucí z různých důvodů. Podporuje konfigurace služby WCF uzamykání hodnoty konfigurace tak, aby vnořené konfigurace generuje výjimky při spuštění vnořené služby pomocí přepsat hodnoty konfigurace.  
  
 Tento příklad znázorňuje postup řízení protokolování z známé identifikovatelné osobní informace (PII) v protokolech trasování a zprávy, jako je například uživatelské jméno a heslo. Ve výchozím nastavení protokolování známé PII je zakázáno, ale v některých situacích může být důležité při ladění aplikace protokolování PII. Tato ukázka je založena na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md). Kromě toho tato ukázka používá trasování a protokolování zpráv. Další informace najdete v tématu [trasování a protokolování zpráv](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md) ukázka.  
  
## <a name="encrypting-configuration-file-elements"></a>Šifrování souboru konfigurace – elementy  
 Z bezpečnostních důvodů v prostředí sdílené hostování webů může být žádoucí k šifrování určitých konfigurační prvky, jako je například databázové připojovací řetězce, které mohou obsahovat citlivé informace. Element konfigurace může šifrované pomocí nástroje aspnet_regiis.exe nachází ve složce % například WINDIR%\Micrsoft.NET\Framework\v4.0.20728 rozhraní .NET Framework.  
  
#### <a name="to-encrypt-the-values-in-the-appsettings-section-in-webconfig-for-the-sample"></a>K šifrování hodnoty v oddílu appSettings v souboru Web.config pro ukázku  
  
1.  Otevřete příkazový řádek pomocí Start -> spustit... Zadejte `cmd` a klikněte na tlačítko **OK**.  
  
2.  Přejděte k aktuálnímu adresáři rozhraní .NET Framework po vydání následujícího příkazu: `cd %WINDIR%\Microsoft.NET\Framework\v4.0.20728`.  
  
3.  Šifrování appSettings nastavení konfigurace ve složce Web.config po vydání následujícího příkazu: `aspnet_regiis -pe "appSettings" -app "/servicemodelsamples" -prov "DataProtectionConfigurationProvider"`.  
  
 Naleznete další informace o šifrování oddílů konfigurační soubory načtením postupy na rozhraní DPAPI v konfiguraci ASP.NET ([vytváření zabezpečení aplikací ASP.NET: ověřování, autorizace a zabezpečená komunikace](http://go.microsoft.com/fwlink/?LinkId=95137)) a postupy v RSA v konfiguraci ASP.NET ([postupy: šifrování konfigurační oddíly funkce v technologii ASP.NET 2.0 pomocí RSA](http://go.microsoft.com/fwlink/?LinkId=95138)).  
  
## <a name="locking-configuration-file-elements"></a>Zamykání souborů konfigurace – elementy  
 Ve scénářích hostuje Web je možné, že služby v podadresářích adresáře služby. V těchto situacích se určí hodnoty konfigurace pro službu v podadresáři zkoumání hodnoty v souboru Machine.config a postupně sloučení se všechny soubory Web.config nadřazeného adresáře přesunutí dolů ve stromu adresáře a nakonec slučování Soubor Web.config v adresáři, který obsahuje službu. Výchozí chování pro většinu prvků konfigurace je umožnit konfigurační soubory nacházejí v podadresářích adresáře přepsat s hodnotami nastavenými v nadřazeného adresáře. V některých situacích může být žádoucí, abyste zabránili přepsání hodnotami nastavenými v nadřazené konfiguraci adresáře konfigurační soubory nacházejí v podadresářích adresáře.  
  
 Rozhraní .NET Framework poskytuje způsob, jak uzamknout konfigurační soubor prvky tak, aby konfigurace, které potlačí uzamčeném konfigurace – elementy throw výjimky v době běhu.  
  
 Zadáním jde Zamknout prvek konfigurace `lockItem` atribut pro uzel v konfiguračním souboru, například k uzamčení uzlu CalculatorServiceBehavior v konfiguračním souboru tak, aby kalkulačky služeb ve vnořených konfigurační soubory nelze změnit chování, následující konfigurace můžete použít.  
  
```xml  
<configuration>  
   <system.serviceModel>  
      <behaviors>   
          <serviceBehaviors>   
             <behavior name="CalculatorServiceBehavior" lockItem="true">   
               <serviceMetadata httpGetEnabled="True"/>   
               <serviceDebug includeExceptionDetailInFaults="False" />   
             </behavior>   
          </serviceBehaviors>   
       </behaviors>   
    </system.serviceModel>  
</configuration>  
```  
  
 Uzamykání konfigurace – elementy může být konkrétnější. Seznam prvků lze zadat jako hodnotu `lockElements` k uzamčení sadu elementů v kolekci podřízených elementů. Seznam atributů lze zadat jako hodnotu `lockAttributes` k uzamčení sadu atributů v rámci elementu. Celou kolekci elementy nebo atributy jde Zamknout s výjimkou zadaného seznamu tak, že zadáte `lockAllElementsExcept` nebo `lockAllAttributesExcept` atributy na uzlu.  
  
## <a name="pii-logging-configuration"></a>Konfigurace protokolování PII  
 Protokolování PII řídí dva přepínače: v souboru Machine.config, který umožňuje správci počítače můžete povolit nebo zakázat protokolování PII a nastavení aplikace, které umožňuje Správce aplikací k přepnutí protokolování PII pro každou najít nastavení platná pro celý počítač zdroj v souboru Web.config nebo App.config.  
  
 Nastavení platná pro celý počítač je řízena nastavením `enableLoggingKnownPii` k `true` nebo `false`v `machineSettings` element v souboru Machine.config. Následující například umožňuje aplikacím zapnout protokolování PII.  
  
```xml  
<configuration>  
    <system.serviceModel>  
        <machineSettings enableLoggingKnownPii="true" />  
    </system.serviceModel>  
</configuration>  
```  
  
> [!NOTE]
>  Souboru Machine.config má výchozí umístění: % WINDIR%\Microsoft.NET\Framework\v2.0.50727\CONFIG.  
  
 Pokud `enableLoggingKnownPii` atribut není k dispozici v souboru Machine.config, není povoleno protokolování PII.  
  
 Povolení protokolování PII pro aplikace se provádí nastavením `logKnownPii` atribut elementu zdroj `true` nebo `false` v souboru Web.config nebo App.config. Následující příklad umožňuje protokolování PII pro protokolování zpráv a protokolování trasování.  
  
```xml  
<configuration>  
    <system.diagnostics>  
        <sources>  
            <source name="System.ServiceModel.MessageLogging" logKnownPii="true">  
                <listeners>   
                ...   
                </listeners>  
            </source>  
            <source name="System.ServiceModel" switchValue="Verbose, ActivityTracing">  
            <listeners>  
        ...   
            </listeners>  
            </source>  
        </sources>  
    </system.diagnostics>  
</configuration>  
```  
  
 Pokud `logKnownPii` atribut nezadá, pak se neprotokolují PII.  
  
 PII se zaznamená pouze, pokud obě `enableLoggingKnownPii` je nastaven na `true`, a `logKnownPii` je nastaven na `true`.  
  
> [!NOTE]
>  System.Diagnostics ignoruje všechny atributy pro všechny zdroje kromě první uveden v konfiguračním souboru. Přidávání `logKnownPii` atribut ke zdroji druhý v konfiguračním souboru nemá žádný vliv.  
  
> [!IMPORTANT]
>  Chcete tuto ukázku spustit zahrnuje ruční úpravy souboru Machine.config. Potřeba dát pozor při úpravách souboru Machine.config tvoří nesprávné hodnoty nebo syntaxe může zabránit spouštění všech aplikací rozhraní .NET Framework.  
  
 Také je možné zašifrovat soubor konfigurace – elementy pomocí rozhraní DPAPI a RSA. Další informace najdete v následujících tématech:  
  
-   [Vytváření aplikací ASP.NET zabezpečení: Ověřování, autorizace a zabezpečenou komunikaci](http://go.microsoft.com/fwlink/?LinkId=95137)  
  
-   [Postupy: Šifrování konfigurační oddíly funkce v technologii ASP.NET 2.0 pomocí RSA](http://go.microsoft.com/fwlink/?LinkId=95138)  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Pokud chcete nastavit, sestavit a spustit ukázku  
  
1.  Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Upravit Machine.config nastavit `enableLoggingKnownPii` atribut `true`, přidání nadřazených uzlů v případě potřeby.  
  
3.  Sestavení C# nebo Visual Basic .NET edice řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
4.  Spustit ukázku v konfiguraci s jednou nebo mezi počítači, postupujte podle pokynů v [spuštění ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
#### <a name="to-clean-up-the-sample"></a>Vyčistěte vzorku  
  
1.  Upravit Machine.config nastavit `enableLoggingKnownPii` atribut `false`.  
  
## <a name="see-also"></a>Viz také  
 [Ukázky monitorování AppFabric](http://go.microsoft.com/fwlink/?LinkId=193959)
