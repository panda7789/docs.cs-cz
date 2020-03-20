---
title: Bezpečnostní uzamčení PII
ms.date: 03/30/2017
ms.assetid: c44fb338-9527-4dd0-8607-b8787d15acb4
ms.openlocfilehash: ad4f4a024b04a028b815faedded58713e001cab0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79144263"
---
# <a name="pii-security-lockdown"></a>Bezpečnostní uzamčení PII
Tato ukázka ukazuje, jak řídit několik funkcí souvisejících se zabezpečením služby WCF (Windows Communication Foundation) pomocí:  
  
- Šifrování citlivých informací v konfiguračním souboru služby.  
  
- Uzamykání prvků v konfiguračním souboru tak, aby vnořené podadresáře služby nemohly přepsat nastavení.  
  
- Řízení protokolování osobně identifikovatelných informací (PII) v protokolech trasování a zpráv.  
  
> [!IMPORTANT]
> Ukázky mohou být již nainstalovány v počítači. Před pokračováním zkontrolujte následující (výchozí) adresář.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka je umístěna v následujícím adresáři.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\SecurityLockdown`  
  
## <a name="discussion"></a>Diskuse  
 Každá z těchto funkcí lze použít samostatně nebo společně k řízení aspektů zabezpečení služby. Toto není definitivní průvodce zabezpečení služby WCF.  
  
 Konfigurační soubory rozhraní .NET Framework mohou obsahovat citlivé informace, například připojovací řetězce pro připojení k databázím. Ve sdílených scénářích hostovaných na webu může být žádoucí zašifrovat tyto informace v konfiguračním souboru pro službu tak, aby data obsažená v konfiguračním souboru byla odolná vůči náhodnému zobrazení. Rozhraní .NET Framework 2.0 a novější má možnost šifrovat části konfiguračního souboru pomocí aplikačního programovacího rozhraní Windows Data Protection (DPAPI) nebo zprostředkovatele kryptografických služeb RSA. Nástroj aspnet_regiis.exe používající protokol DPAPI nebo RSA může šifrovat vybrané části konfiguračního souboru.  
  
 Ve scénářích hostovaných na webu je možné mít služby v podadresářích jiných služeb. Výchozí sémantika pro určení konfiguračních hodnot umožňuje konfiguračním souborům v vnořených adresářích přepsat hodnoty konfigurace v nadřazeném adresáři. V určitých situacích to může být nežádoucí z různých důvodů. Konfigurace služby WCF podporuje uzamčení hodnot konfigurace tak, aby vnořená konfigurace generovala výjimky při spuštění vnořené služby pomocí přepsaných konfiguračních hodnot.  
  
 Tato ukázka ukazuje, jak řídit protokolování známých osobně identifikovatelných informací (PII) v protokolech trasování a zpráv, jako je uživatelské jméno a heslo. Ve výchozím nastavení je protokolování známých pii zakázáno, ale v určitých situacích může být protokolování pii důležité při ladění aplikace. Tato ukázka je založena na [začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md). Kromě toho tato ukázka používá trasování a protokolování zpráv. Další informace naleznete v tématu [Trasování a protokolování zpráv](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md) ukázka.  
  
## <a name="encrypting-configuration-file-elements"></a>Šifrování prvků konfiguračního souboru  
 Z bezpečnostních důvodů ve sdíleném webhostingovém prostředí může být žádoucí šifrovat určité konfigurační prvky, například připojovací řetězce databáze, které mohou obsahovat citlivé informace. Konfigurační prvek může být šifrován pomocí nástroje aspnet_regiis.exe, který se nachází ve složce rozhraní .NET Framework Například %WINDIR%\Microsoft.NET\Framework\v4.0.20728.  
  
#### <a name="to-encrypt-the-values-in-the-appsettings-section-in-webconfig-for-the-sample"></a>Šifrování hodnot v části appSettings v souboru Web.config pro ukázku  
  
1. Otevřete příkazový řádek pomocí spuštění >spustit.... Zadejte `cmd` a klepněte na tlačítko **OK**.  
  
2. Přejděte do aktuálního adresáře rozhraní .NET `cd %WINDIR%\Microsoft.NET\Framework\v4.0.20728`Framework vydáním následujícího příkazu: .  
  
3. Šifrujte nastavení konfigurace appSettings ve složce Web.config vydáním následujícího příkazu: `aspnet_regiis -pe "appSettings" -app "/servicemodelsamples" -prov "DataProtectionConfigurationProvider"`.  
  
 Další informace o šifrování částí konfiguračních souborů naleznete v návodu na DPAPI v konfiguraci ASP.NET[(Building Secure ASP.NET Applications: Authentication, Authorization, and Secure Communication)](https://docs.microsoft.com/previous-versions/msp-n-p/ff649248(v=pandp.10))a how-to na RSA v ASP.NET konfiguraci ([Jak: Šifrovat konfigurační sekce v ASP.NET 2.0 pomocí RSA](https://docs.microsoft.com/previous-versions/msp-n-p/ff650304(v=pandp.10))).  
  
## <a name="locking-configuration-file-elements"></a>Zamykání prvků konfiguračního souboru  
 Ve scénářích hostovaných na webu je možné mít služby v podadresářích služeb. V těchto situacích jsou hodnoty konfigurace služby v podadresáři vypočteny tak, že se prozkoumá hodnoty v souboru Machine.config a postupně se sloučí se všemi soubory Web.config v nadřazených adresářích, které se přesunou dolů do adresářového stromu a nakonec sloučí Soubor Web.config v adresáři, který obsahuje službu. Výchozím chováním většiny konfiguračních prvků je povolit konfiguračním souborům v podadresářích přepsat hodnoty nastavené v nadřazených adresářích. V určitých situacích může být žádoucí zabránit tomu, aby konfigurační soubory v podadresářích přecvakovaly hodnoty nastavené v konfiguraci nadřazeného adresáře.  
  
 Rozhraní .NET Framework poskytuje způsob uzamčení prvků konfiguračního souboru tak, aby konfigurace, které přepíší uzamčené konfigurační prvky, vyvolaly výjimky za běhu.  
  
 Konfigurační prvek lze uzamknout zadáním atributu `lockItem` pro uzel v konfiguračním souboru, například pro uzamčení uzlu CalculatorServiceBehavior v konfiguračním souboru tak, aby kalkulačka služby v vnořených konfiguračních souborů nelze změnit chování, lze použít následující konfiguraci.  
  
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
  
 Uzamčení konfiguračních prvků může být konkrétnější. Seznam prvků lze zadat jako hodnotu `lockElements` pro uzamčení sady prvků v rámci kolekce dílčích prvků. Seznam atributů lze zadat jako hodnotu `lockAttributes` pro uzamčení sady atributů v rámci prvku. Celou kolekci prvků nebo atributů lze uzamknout s `lockAllElementsExcept` výjimkou `lockAllAttributesExcept` zadaného seznamu zadáním atributů nebo v uzlu.  
  
## <a name="pii-logging-configuration"></a>Konfigurace protokolování pii  
 Protokolování pii je řízeno dvěma přepínači: nastavením pro celý počítač, které se nachází v souboru Machine.config, které umožňuje správci počítače povolit nebo odepřít protokolování pii a nastavení aplikace, které umožňuje správci aplikace přepínat protokolování pii pro každý v souboru Web.config nebo App.config.  
  
 Nastavení celého počítače je `enableLoggingKnownPii` řízeno `false`nastavením `machineSettings` `true` nebo , v prvku v souboru Machine.config. Následující umožňuje aplikacím například zapnout protokolování pii.  
  
```xml  
<configuration>  
    <system.serviceModel>  
        <machineSettings enableLoggingKnownPii="true" />  
    </system.serviceModel>  
</configuration>  
```  
  
> [!NOTE]
> Soubor Machine.config má výchozí umístění: %WINDIR%\Microsoft.NET\Framework\v2.0.50727\CONFIG.  
  
 Pokud `enableLoggingKnownPii` atribut není k dispozici v Machine.config, protokolování PII není povoleno.  
  
 Povolení protokolování pii pro aplikaci `logKnownPii` se provádí nastavením `true` `false` atributu zdrojového prvku do souboru Web.config nebo App.config nebo V souboru Web.config nebo App.config. Následující umožňuje například protokolování pii pro protokolování zpráv a protokolování trasování.  
  
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
  
 Pokud `logKnownPii` atribut není zadán, není protokolován pii.  
  
 PiI je protokolována `enableLoggingKnownPii` pouze `true`v `logKnownPii` případě, `true`že je obě nastavena na .  
  
> [!NOTE]
> System.Diagnostics ignoruje všechny atributy na všech zdrojích kromě první ho uvedeného v konfiguračním souboru. Přidání `logKnownPii` atributu do druhého zdroje v konfiguračním souboru nemá žádný vliv.  
  
> [!IMPORTANT]
> Chcete-li spustit tuto ukázku zahrnuje ruční úpravy Machine.config. Při úpravě souboru Machine.config je třeba dbát na to, aby byly spuštěny nesprávné hodnoty nebo syntaxe.  
  
 Je také možné šifrovat prvky konfiguračního souboru pomocí DPAPI a RSA. Další informace najdete na následujících odkazech:  
  
- [Vytváření zabezpečených aplikací ASP.NET: ověřování, autorizace a zabezpečená komunikace](https://docs.microsoft.com/previous-versions/msp-n-p/ff649248(v=pandp.10))  
  
- [Postup: Šifrování konfiguračních oddílů v ASP.NET 2.0 pomocí rsa](https://docs.microsoft.com/previous-versions/msp-n-p/ff650304(v=pandp.10))  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Chcete-li nastavit, sestavení a spuštění ukázky  
  
1. Ujistěte se, že jste provedli [jednorázový postup instalace pro ukázky windows communication foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Upravit soubor Machine.config `enableLoggingKnownPii` a `true`nastavit atribut na , v případě potřeby přidat nadřazené uzly.  
  
3. Chcete-li vytvořit c# nebo Visual Basic .NET vydání řešení, postupujte podle pokynů v [sestavení windows communication foundation ukázky](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
4. Chcete-li spustit ukázku v konfiguraci jednoho nebo mezi počítači, postupujte podle pokynů v [části Spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
#### <a name="to-clean-up-the-sample"></a>Vyčištění vzorku  
  
1. Chcete-li nastavit `enableLoggingKnownPii` atribut na `false`soubor , upravit soubor Machine.config.  
  
## <a name="see-also"></a>Viz také

- [Vzorky monitorování appfabricu](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))
