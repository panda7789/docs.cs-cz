---
title: Bezpečnostní uzamčení PII
ms.date: 03/30/2017
ms.assetid: c44fb338-9527-4dd0-8607-b8787d15acb4
ms.openlocfilehash: 63410ecc19e94e57f943e5d7dc13a6098bd91d51
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74714627"
---
# <a name="pii-security-lockdown"></a>Bezpečnostní uzamčení PII
Tato ukázka předvádí, jak řídit několik funkcí služby Windows Communication Foundation (WCF) souvisejících se zabezpečením pomocí:  
  
- Šifrování citlivých informací v konfiguračním souboru služby.  
  
- Uzamykání prvků v konfiguračním souboru, aby vnořené podadresáře služby nemohly přepsat nastavení.  
  
- Řízení protokolování identifikovatelné osobní údaje (PII) v protokolech trasování a zpráv.  
  
> [!IMPORTANT]
> Ukázky již mohou být nainstalovány v počítači. Než budete pokračovat, vyhledejte následující (výchozí) adresář.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Samples. Tato ukázka se nachází v následujícím adresáři.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\SecurityLockdown`  
  
## <a name="discussion"></a>Účely  
 Každá z těchto funkcí se dá použít samostatně nebo společně k řízení aspektů zabezpečení služby. Nejedná se o nekonečný Průvodce zabezpečením služby WCF.  
  
 Konfigurační soubory .NET Framework můžou obsahovat citlivé informace, jako jsou připojovací řetězce pro připojení k databázím. Ve sdílených scénářích hostovaných na webu může být žádoucí zašifrovat tyto informace v konfiguračním souboru pro službu, aby data obsažená v konfiguračním souboru byla odolná vůči příležitostnému zobrazení. .NET Framework 2,0 a novější má schopnost šifrovat části konfiguračního souboru pomocí rozhraní DPAPI (Windows Data Protection Application Programming Interface) nebo zprostředkovatele kryptografických služeb RSA. Aspnet_regiis. exe používající rozhraní DPAPI nebo RSA může šifrovat vybrané části konfiguračního souboru.  
  
 Ve scénářích hostovaných na webu je možné mít služby v podadresářích jiných služeb. Výchozí sémantika pro určení hodnot konfigurace umožňuje, aby konfigurační soubory ve vnořených adresářích přepsaly konfigurační hodnoty v nadřazeném adresáři. V některých situacích může být to nežádoucí z nejrůznějších důvodů. Konfigurace služby WCF podporuje uzamykání hodnot konfigurace, aby vnořená konfigurace generovala výjimky při spuštění vnořené služby pomocí přepsaných hodnot konfigurace.  
  
 Tato ukázka předvádí, jak řídit protokolování známých identifikovatelných osobních údajů (PII) v protokolech trasování a zpráv, jako je uživatelské jméno a heslo. Ve výchozím nastavení je protokolování známého PII zakázáno, ale v některých situacích může být protokolování PII důležité při ladění aplikace. Tato ukázka je založena na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md). Kromě toho tato ukázka používá trasování a protokolování zpráv. Další informace najdete v ukázce [trasování a protokolování zpráv](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md) .  
  
## <a name="encrypting-configuration-file-elements"></a>Šifrování elementů konfiguračního souboru  
 Pro účely zabezpečení ve sdíleném prostředí pro hostování webů může být vhodné zašifrovat určité konfigurační prvky, například databázové připojovací řetězce, které mohou obsahovat citlivé informace. Element konfigurace může být zašifrovaný pomocí nástroje aspnet_regiis. exe, který se nachází ve složce .NET Framework, například%WINDIR%\Microsoft.NET\Framework\v4.0.20728.  
  
#### <a name="to-encrypt-the-values-in-the-appsettings-section-in-webconfig-for-the-sample"></a>Chcete-li zašifrovat hodnoty v oddílu appSettings v souboru Web. config pro ukázku  
  
1. Otevřete příkazový řádek pomocí rutiny Start-> Spustit.... Zadejte `cmd` a klikněte na **OK**.  
  
2. Přejděte do aktuálního adresáře .NET Framework tím, že vydáváte následující příkaz: `cd %WINDIR%\Microsoft.NET\Framework\v4.0.20728`.  
  
3. Zašifrujte konfigurační nastavení appSettings ve složce Web. config vyvoláním následujícího příkazu: `aspnet_regiis -pe "appSettings" -app "/servicemodelsamples" -prov "DataProtectionConfigurationProvider"`.  
  
 Další informace o šifrování oddílů konfiguračních souborů najdete v tématu věnovaném konfiguraci rozhraní DPAPI v ASP.NET ([sestavování zabezpečených aplikací ASP.NET: ověřování, autorizace a zabezpečená komunikace](https://go.microsoft.com/fwlink/?LinkId=95137)) a s postupy v tématu Konfigurace ASP.NET v ([Postupy: šifrování konfiguračních oddílů v ASP.NET 2,0 pomocí RSA](https://go.microsoft.com/fwlink/?LinkId=95138)).  
  
## <a name="locking-configuration-file-elements"></a>Zamykání elementů konfiguračního souboru  
 Ve scénářích hostovaných na webu je možné mít služby v podadresářích služeb. V těchto situacích se hodnoty konfigurace pro službu v podadresáři vypočítávají prozkoumáním hodnot v souboru Machine. config a následným sloučením se soubory Web. config v nadřazených adresářích, které přesunují strom adresářů a nakonec sloučí Soubor Web. config v adresáři, který obsahuje službu. Výchozím chováním pro většinu konfiguračních elementů je umožnit, aby konfigurační soubory v podadresářích přepsaly hodnoty nastavené v nadřazených adresářích. V některých situacích může být žádoucí zabránit konfiguračním souborům v podadresářích z přepsání hodnot nastavených v konfiguraci nadřazeného adresáře.  
  
 .NET Framework poskytuje způsob, jak uzamknout prvky konfiguračního souboru tak, aby konfigurace, které přepíší uzamčené konfigurační prvky, vyvolaly výjimky za běhu.  
  
 Element konfigurace může být uzamčen zadáním atributu `lockItem` pro uzel v konfiguračním souboru, například pro uzamknutí uzlu CalculatorServiceBehavior v konfiguračním souboru, aby služby kalkulačky ve vnořených konfiguračních souborech nemohly měnit chování, lze použít následující konfiguraci.  
  
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
  
 Uzamykání konfiguračních elementů může být konkrétnější. Seznam elementů může být zadán jako hodnota `lockElements` pro uzamknutí sady prvků v kolekci dílčích prvků. Seznam atributů může být zadán jako hodnota `lockAttributes` k uzamknutí sady atributů v rámci elementu. Celá kolekce prvků nebo atributů může být uzamčena s výjimkou zadaného seznamu zadáním atributů `lockAllElementsExcept` nebo `lockAllAttributesExcept` na uzlu.  
  
## <a name="pii-logging-configuration"></a>Konfigurace protokolování PII  
 Přihlášení k PII je řízeno dvěma přepínači: nastavení v rámci počítače, které se nachází v souboru Machine. config, který umožňuje správci počítače povolit nebo odepřít protokolování PII a nastavení aplikace, které umožňuje správci aplikace přepnout protokolování PII pro každý zdroj v souboru Web. config nebo App. config.  
  
 Nastavení na úrovni počítače je řízeno nastavením `enableLoggingKnownPii` na `true` nebo `false`, v `machineSettings` elementu Machine. config. Následující příklad umožňuje aplikacím zapnout protokolování PII.  
  
```xml  
<configuration>  
    <system.serviceModel>  
        <machineSettings enableLoggingKnownPii="true" />  
    </system.serviceModel>  
</configuration>  
```  
  
> [!NOTE]
> Soubor Machine. config má výchozí umístění:%WINDIR%\Microsoft.NET\Framework\v2.0.50727\CONFIG.  
  
 Pokud se v souboru Machine. config nenachází atribut `enableLoggingKnownPii`, není protokolování PII povoleno.  
  
 Povolení protokolování PII pro aplikaci je provedeno nastavením atributu `logKnownPii` zdrojového elementu na `true` nebo `false` v souboru Web. config nebo App. config. Následující příklad umožňuje protokolování PII pro protokolování zpráv a protokolování trasování.  
  
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
  
 Pokud není zadán atribut `logKnownPii`, pak PII není protokolován.  
  
 PII je protokolováno pouze v případě, že je obě `enableLoggingKnownPii` nastavena na hodnotu `true`a `logKnownPii` je nastavena na `true`.  
  
> [!NOTE]
> System. Diagnostics ignoruje všechny atributy všech zdrojů s výjimkou prvního, který je uveden v konfiguračním souboru. Přidání atributu `logKnownPii` k druhému zdroji v konfiguračním souboru nemá žádný vliv.  
  
> [!IMPORTANT]
> Spuštění této ukázky zahrnuje ruční úpravu souboru Machine. config. Při úpravách Machine. config jako nesprávné hodnoty nebo syntaxe může zabránit spuštění všech aplikací .NET Framework.  
  
 Je také možné zašifrovat prvky konfiguračního souboru pomocí DPAPI a RSA. Další informace najdete na následujících odkazech:  
  
- [Sestavování zabezpečených aplikací ASP.NET: ověřování, autorizace a zabezpečená komunikace](https://go.microsoft.com/fwlink/?LinkId=95137)  
  
- [Postupy: šifrování konfiguračních oddílů v ASP.NET 2,0 pomocí RSA](https://go.microsoft.com/fwlink/?LinkId=95138)  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky  
  
1. Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Úpravou souboru Machine. config nastavte atribut `enableLoggingKnownPii` na `true`a v případě potřeby přidejte nadřazené uzly.  
  
3. Pokud chcete vytvořit C# edici nebo Visual Basic .NET, postupujte podle pokynů v tématu [sestavování ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
4. Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
#### <a name="to-clean-up-the-sample"></a>Vyčištění ukázky  
  
1. Úpravou souboru Machine. config nastavte atribut `enableLoggingKnownPii` na hodnotu `false`.  
  
## <a name="see-also"></a>Viz také:

- [Ukázky monitorování technologie AppFabric](https://go.microsoft.com/fwlink/?LinkId=193959)
