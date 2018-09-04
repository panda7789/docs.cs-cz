---
title: Bezpečnostní uzamčení PII
ms.date: 03/30/2017
ms.assetid: c44fb338-9527-4dd0-8607-b8787d15acb4
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: ca85a620638509e183703f7e80c01ea20fadbc81
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43555193"
---
# <a name="pii-security-lockdown"></a>Bezpečnostní uzamčení PII
Tento příklad ukazuje, jak řídit několik funkcí souvisejících se zabezpečením pomocí služby Windows Communication Foundation (WCF):  
  
-   Šifrování citlivých informací v konfiguračním souboru služby.  
  
-   Uzamčení elementů v konfiguračním souboru tak, aby vnořené podadresářů služby nelze přepsat nastavení.  
  
-   Řízení přihlašování z identifikovatelné osobní údaje (PII) v protokolech trasování a zprávy.  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno ve vašem počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\SecurityLockdown`  
  
## <a name="discussion"></a>Diskuse  
 Každá z těchto funkcí může být používat samostatně nebo společně k řízení aspektů zabezpečení služby. Nejedná se úplnou příručku k zabezpečení ve službě WCF.  
  
 Konfigurační soubory rozhraní .NET Framework mohou obsahovat citlivé údaje, jako je například připojovací řetězce k připojení k databázím. Ve sdílené, hostovaný Web scénářích může být žádoucí k zašifrování těchto informací v konfiguračním souboru služby tak, aby data obsažená v konfiguračním souboru byla odolná vůči příležitostné zobrazení. Rozhraní .NET framework 2.0 a novější má možnost šifrování části konfiguračního souboru pomocí rozhraní Windows Data Protection application programming rozhraní DPAPI nebo zprostředkovatel RSA kryptografických služeb. Vyberte část konfigurační soubor můžete šifrovat aspnet_regiis.exe pomocí rozhraní DPAPI nebo RSA.  
  
 V hostované Web scénářích je možné mít služby v podadresářích dalších služeb. Výchozí sémantické pro určení hodnoty konfigurace umožňuje konfigurační soubory v adresářích vnořené přepsat hodnoty konfigurace v nadřazeném adresáři. V některých situacích může nežádoucí u z různých důvodů. Podporuje konfigurace služby WCF uzamčení konfigurační hodnoty tak, aby vnořené konfigurace generuje výjimky při spuštění pomocí služby vnořené přepsat hodnoty konfigurace.  
  
 Tento příklad ukazuje, jak řízení protokolování ze známých identifikovatelné osobní údaje (PII) v protokolech trasování a zprávy, jako je například uživatelské jméno a heslo. Ve výchozím nastavení je zakázáno přihlášení známého PII, ale v některých situacích může být důležité při ladění aplikace protokolování identifikovatelné osobní údaje. Tato ukázka je založena na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md). Kromě toho tato ukázka používá trasování a protokolování zpráv. Další informace najdete v tématu [trasování a protokolování zpráv](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md) vzorku.  
  
## <a name="encrypting-configuration-file-elements"></a>Šifrování souboru elementy konfigurace  
 Z bezpečnostních důvodů ve sdíleném prostředí hostování webů může být žádoucí šifrovat určité konfigurační prvky, jako jsou databázové připojovací řetězce, které mohou obsahovat citlivé informace. Prvek konfigurace je možné zašifrovat pomocí aspnet_regiis.exe nástroj nachází ve složce % například WINDIR%\Micrsoft.NET\Framework\v4.0.20728 rozhraní .NET Framework.  
  
#### <a name="to-encrypt-the-values-in-the-appsettings-section-in-webconfig-for-the-sample"></a>K šifrování hodnoty v oddíle appSettings souboru Web.config pro ukázku  
  
1.  Otevřete příkazový řádek s použitím Start -> spustit... Zadejte `cmd` a klikněte na tlačítko **OK**.  
  
2.  Přejděte do aktuálního adresáře rozhraní .NET Framework pomocí následujícího příkazu: `cd %WINDIR%\Microsoft.NET\Framework\v4.0.20728`.  
  
3.  Nastavení konfigurace appSettings ve složce Web.config šifrovat pomocí následujícího příkazu: `aspnet_regiis -pe "appSettings" -app "/servicemodelsamples" -prov "DataProtectionConfigurationProvider"`.  
  
 Další informace o šifrování oddíly konfiguračních souborů můžete zobrazit tak čtení postupy na rozhraní DPAPI v konfiguraci technologie ASP.NET ([vytváření bezpečných aplikací technologie ASP.NET: ověřování, autorizaci a zabezpečená komunikace](https://go.microsoft.com/fwlink/?LinkId=95137)) a postupy v RSA v konfiguraci technologie ASP.NET ([postupy: šifrování konfigurační oddíly funkce v ASP.NET 2.0 pomocí RSA](https://go.microsoft.com/fwlink/?LinkId=95138)).  
  
## <a name="locking-configuration-file-elements"></a>Zamykání souborů elementy konfigurace  
 V hostované Web scénářích je možné mít služby v podadresářích služeb. V těchto situacích se počítají hodnoty konfigurace pro službu v podadresáři kontrolou hodnoty v souboru Machine.config a postupně se žádné soubory Web.config v nadřazené adresáře přesunutí dolů ve stromu adresáře a nakonec slučování sloučení Soubor Web.config v adresáře, který obsahuje službu. Výchozí chování pro většinu prvků konfigurace je umožnit konfiguračních souborů v podadresářích přepisují hodnoty nastavené v nadřazené adresáře. V některých situacích může být žádoucí konfiguračních souborů v podadresářích zabránit potlačení hodnot nastavených v konfiguraci nadřazené adresáře.  
  
 Rozhraní .NET Framework poskytuje způsob, jak uzamknout soubor elementů konfigurace tak, aby konfigurace, které přepíší elementy uzamčené konfigurace vyvolat výjimky za běhu.  
  
 Prvek konfigurace můžete uzamknout tak, že zadáte `lockItem` atribut pro uzel v konfiguračním souboru, například k uzamčení CalculatorServiceBehavior uzlu v konfiguračním souboru tak, aby Kalkulačka služby ve vnořené konfiguračních souborů nelze změnit chování následující konfigurace můžete použít.  
  
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
  
 Uzamčení elementů konfigurace může být konkrétnější. Seznam prvků se dá nastavit jako hodnota, která má `lockElements` uzamknout sadu elementů v rámci kolekce podřízených elementů. Seznam atributů lze zadat jako hodnota, která má `lockAttributes` uzamknout sadu atributů v rámci elementu. S výjimkou zadaného seznamu jde zamknout celou kolekci elementů nebo atributů tak, že zadáte `lockAllElementsExcept` nebo `lockAllAttributesExcept` atributy uzlu.  
  
## <a name="pii-logging-configuration"></a>Konfigurace protokolování identifikovatelné osobní údaje  
 Protokolování identifikovatelné osobní údaje se řídí dva přepínače: nastavení celý počítač se nenašel v souboru Machine.config, který umožňuje správci počítače můžete povolit nebo zakázat protokolování identifikovatelné osobní údaje a nastavení aplikace, která umožňuje správci aplikace přepnout protokolování identifikovatelné osobní údaje pro každou zdroj v souboru Web.config nebo App.config.  
  
 Nastavení pro celý počítač je řízena nastavením `enableLoggingKnownPii` k `true` nebo `false`v `machineSettings` element v souboru Machine.config. Následující příklad umožňuje aplikacím zapnout protokolování identifikovatelné osobní údaje.  
  
```xml  
<configuration>  
    <system.serviceModel>  
        <machineSettings enableLoggingKnownPii="true" />  
    </system.serviceModel>  
</configuration>  
```  
  
> [!NOTE]
>  Soubor Machine.config obsahuje výchozí umístění: % WINDIR%\Microsoft.NET\Framework\v2.0.50727\CONFIG.  
  
 Pokud `enableLoggingKnownPii` atribut není k dispozici v souboru Machine.config, není povoleno protokolování identifikovatelné osobní údaje.  
  
 Povolení protokolování identifikovatelné osobní údaje pro aplikaci se provádí tak, že nastavíte `logKnownPii` atribut zdrojového elementu na `true` nebo `false` v souboru Web.config nebo App.config. Následující příklad umožňuje protokolování identifikovatelné osobní údaje pro protokolování trasování a protokolování zpráv.  
  
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
  
 Pokud `logKnownPii` není zadán atribut, pak identifikovatelné osobní údaje se neprotokolují.  
  
 Identifikovatelné osobní údaje se jenom protokoluje, pokud mají oba `enableLoggingKnownPii` je nastavena na `true`, a `logKnownPii` je nastavena na `true`.  
  
> [!NOTE]
>  System.Diagnostics ignoruje všechny atributy pro všechny zdroje s výjimkou první z nich uvedená v konfiguračním souboru. Přidávání `logKnownPii` atribut do druhého zdroje v konfiguračním souboru nemá žádný vliv.  
  
> [!IMPORTANT]
>  Chcete-li spustit tento příklad zahrnuje ruční úpravy souboru Machine.config. Při úpravě souboru Machine.config jako nesprávné hodnoty nebo syntaxe může zabránit spouštění všech aplikací rozhraní .NET Framework by měl být věnovat pozornost.  
  
 Je také možné šifrovat konfigurační prvky souboru pomocí DPAPI a RSA. Další informace najdete v následujících tématech:  
  
-   [Vytváření aplikací ASP.NET zabezpečené: Ověřování, autorizaci a zabezpečenou komunikaci](https://go.microsoft.com/fwlink/?LinkId=95137)  
  
-   [Postupy: Šifrování konfigurační oddíly funkce v technologii ASP.NET 2.0 pomocí technologie RSA](https://go.microsoft.com/fwlink/?LinkId=95138)  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Chcete-li nastavit, sestavte a spusťte ukázku  
  
1.  Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Upravit soubor Machine.config nastavit `enableLoggingKnownPii` atribut `true`, v případě potřeby přidává uzly nadřazených objektů.  
  
3.  K sestavení edice řešení C# nebo Visual Basic .NET, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
4.  Spusťte ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v [spouštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
#### <a name="to-clean-up-the-sample"></a>Vyčistit vzorku  
  
1.  Upravit soubor Machine.config nastavit `enableLoggingKnownPii` atribut `false`.  
  
## <a name="see-also"></a>Viz také  
 [Ukázky AppFabric monitorování](https://go.microsoft.com/fwlink/?LinkId=193959)
