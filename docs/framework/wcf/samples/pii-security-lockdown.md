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
# <a name="pii-security-lockdown"></a><span data-ttu-id="c71f1-102">Bezpečnostní uzamčení PII</span><span class="sxs-lookup"><span data-stu-id="c71f1-102">PII Security Lockdown</span></span>
<span data-ttu-id="c71f1-103">Tato ukázka ukazuje, jak řídit několik funkcí souvisejících se zabezpečením služby WCF (Windows Communication Foundation) pomocí:</span><span class="sxs-lookup"><span data-stu-id="c71f1-103">This sample demonstrates how to control several security-related features of a Windows Communication Foundation (WCF) service by:</span></span>  
  
- <span data-ttu-id="c71f1-104">Šifrování citlivých informací v konfiguračním souboru služby.</span><span class="sxs-lookup"><span data-stu-id="c71f1-104">Encrypting sensitive information in a service's configuration file.</span></span>  
  
- <span data-ttu-id="c71f1-105">Uzamykání prvků v konfiguračním souboru tak, aby vnořené podadresáře služby nemohly přepsat nastavení.</span><span class="sxs-lookup"><span data-stu-id="c71f1-105">Locking elements in the configuration file so that nested service subdirectories cannot override settings.</span></span>  
  
- <span data-ttu-id="c71f1-106">Řízení protokolování osobně identifikovatelných informací (PII) v protokolech trasování a zpráv.</span><span class="sxs-lookup"><span data-stu-id="c71f1-106">Controlling the logging of Personally Identifiable Information (PII) in trace and message logs.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="c71f1-107">Ukázky mohou být již nainstalovány v počítači.</span><span class="sxs-lookup"><span data-stu-id="c71f1-107">The samples may already be installed on your computer.</span></span> <span data-ttu-id="c71f1-108">Před pokračováním zkontrolujte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="c71f1-108">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="c71f1-109">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="c71f1-109">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="c71f1-110">Tato ukázka je umístěna v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="c71f1-110">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\SecurityLockdown`  
  
## <a name="discussion"></a><span data-ttu-id="c71f1-111">Diskuse</span><span class="sxs-lookup"><span data-stu-id="c71f1-111">Discussion</span></span>  
 <span data-ttu-id="c71f1-112">Každá z těchto funkcí lze použít samostatně nebo společně k řízení aspektů zabezpečení služby.</span><span class="sxs-lookup"><span data-stu-id="c71f1-112">Each of these features can be used separately or together to control aspects of a service's security.</span></span> <span data-ttu-id="c71f1-113">Toto není definitivní průvodce zabezpečení služby WCF.</span><span class="sxs-lookup"><span data-stu-id="c71f1-113">This is not a definitive guide to securing a WCF service.</span></span>  
  
 <span data-ttu-id="c71f1-114">Konfigurační soubory rozhraní .NET Framework mohou obsahovat citlivé informace, například připojovací řetězce pro připojení k databázím.</span><span class="sxs-lookup"><span data-stu-id="c71f1-114">The .NET Framework configuration files can contain sensitive information such as connection strings to connect to databases.</span></span> <span data-ttu-id="c71f1-115">Ve sdílených scénářích hostovaných na webu může být žádoucí zašifrovat tyto informace v konfiguračním souboru pro službu tak, aby data obsažená v konfiguračním souboru byla odolná vůči náhodnému zobrazení.</span><span class="sxs-lookup"><span data-stu-id="c71f1-115">In shared, Web-hosted scenarios it may be desirable to encrypt this information in the configuration file for a service so that the data contained within the configuration file is resistant to casual viewing.</span></span> <span data-ttu-id="c71f1-116">Rozhraní .NET Framework 2.0 a novější má možnost šifrovat části konfiguračního souboru pomocí aplikačního programovacího rozhraní Windows Data Protection (DPAPI) nebo zprostředkovatele kryptografických služeb RSA.</span><span class="sxs-lookup"><span data-stu-id="c71f1-116">.NET Framework 2.0 and later has the ability to encrypt portions of the configuration file using the Windows Data Protection application programming interface (DPAPI) or the RSA Cryptographic provider.</span></span> <span data-ttu-id="c71f1-117">Nástroj aspnet_regiis.exe používající protokol DPAPI nebo RSA může šifrovat vybrané části konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="c71f1-117">The aspnet_regiis.exe using the DPAPI or RSA can encrypt select portions of a configuration file.</span></span>  
  
 <span data-ttu-id="c71f1-118">Ve scénářích hostovaných na webu je možné mít služby v podadresářích jiných služeb.</span><span class="sxs-lookup"><span data-stu-id="c71f1-118">In Web-hosted scenarios it is possible to have services in subdirectories of other services.</span></span> <span data-ttu-id="c71f1-119">Výchozí sémantika pro určení konfiguračních hodnot umožňuje konfiguračním souborům v vnořených adresářích přepsat hodnoty konfigurace v nadřazeném adresáři.</span><span class="sxs-lookup"><span data-stu-id="c71f1-119">The default semantic for determining configuration values allows configuration files in the nested directories to override the configuration values in the parent directory.</span></span> <span data-ttu-id="c71f1-120">V určitých situacích to může být nežádoucí z různých důvodů.</span><span class="sxs-lookup"><span data-stu-id="c71f1-120">In certain situations this may be undesirable for a variety of reasons.</span></span> <span data-ttu-id="c71f1-121">Konfigurace služby WCF podporuje uzamčení hodnot konfigurace tak, aby vnořená konfigurace generovala výjimky při spuštění vnořené služby pomocí přepsaných konfiguračních hodnot.</span><span class="sxs-lookup"><span data-stu-id="c71f1-121">WCF service configuration supports the locking of configuration values so that nested configuration generates exceptions when a nested service is run using overridden configuration values.</span></span>  
  
 <span data-ttu-id="c71f1-122">Tato ukázka ukazuje, jak řídit protokolování známých osobně identifikovatelných informací (PII) v protokolech trasování a zpráv, jako je uživatelské jméno a heslo.</span><span class="sxs-lookup"><span data-stu-id="c71f1-122">This sample demonstrates how to control the logging of known Personally Identifiable Information (PII) in trace and message logs, such as username and password.</span></span> <span data-ttu-id="c71f1-123">Ve výchozím nastavení je protokolování známých pii zakázáno, ale v určitých situacích může být protokolování pii důležité při ladění aplikace.</span><span class="sxs-lookup"><span data-stu-id="c71f1-123">By default, logging of known PII is disabled however in certain situations logging of PII can be important in debugging an application.</span></span> <span data-ttu-id="c71f1-124">Tato ukázka je založena na [začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="c71f1-124">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span> <span data-ttu-id="c71f1-125">Kromě toho tato ukázka používá trasování a protokolování zpráv.</span><span class="sxs-lookup"><span data-stu-id="c71f1-125">In addition, this sample uses tracing and message logging.</span></span> <span data-ttu-id="c71f1-126">Další informace naleznete v tématu [Trasování a protokolování zpráv](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md) ukázka.</span><span class="sxs-lookup"><span data-stu-id="c71f1-126">For more information, see the [Tracing and Message Logging](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md) sample.</span></span>  
  
## <a name="encrypting-configuration-file-elements"></a><span data-ttu-id="c71f1-127">Šifrování prvků konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="c71f1-127">Encrypting Configuration File Elements</span></span>  
 <span data-ttu-id="c71f1-128">Z bezpečnostních důvodů ve sdíleném webhostingovém prostředí může být žádoucí šifrovat určité konfigurační prvky, například připojovací řetězce databáze, které mohou obsahovat citlivé informace.</span><span class="sxs-lookup"><span data-stu-id="c71f1-128">For security purposes in a shared Web-hosting environment, it may be desirable to encrypt certain configuration elements, such as database connection strings that may contain sensitive information.</span></span> <span data-ttu-id="c71f1-129">Konfigurační prvek může být šifrován pomocí nástroje aspnet_regiis.exe, který se nachází ve složce rozhraní .NET Framework Například %WINDIR%\Microsoft.NET\Framework\v4.0.20728.</span><span class="sxs-lookup"><span data-stu-id="c71f1-129">A configuration element may be encrypted using the aspnet_regiis.exe tool found in the .NET Framework folder For example, %WINDIR%\Microsoft.NET\Framework\v4.0.20728.</span></span>  
  
#### <a name="to-encrypt-the-values-in-the-appsettings-section-in-webconfig-for-the-sample"></a><span data-ttu-id="c71f1-130">Šifrování hodnot v části appSettings v souboru Web.config pro ukázku</span><span class="sxs-lookup"><span data-stu-id="c71f1-130">To encrypt the values in the appSettings section in Web.config for the sample</span></span>  
  
1. <span data-ttu-id="c71f1-131">Otevřete příkazový řádek pomocí spuštění >spustit....</span><span class="sxs-lookup"><span data-stu-id="c71f1-131">Open a command prompt by using Start->Run….</span></span> <span data-ttu-id="c71f1-132">Zadejte `cmd` a klepněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="c71f1-132">Type in `cmd` and click **OK**.</span></span>  
  
2. <span data-ttu-id="c71f1-133">Přejděte do aktuálního adresáře rozhraní .NET `cd %WINDIR%\Microsoft.NET\Framework\v4.0.20728`Framework vydáním následujícího příkazu: .</span><span class="sxs-lookup"><span data-stu-id="c71f1-133">Navigate to the current .NET Framework directory by issuing the following command: `cd %WINDIR%\Microsoft.NET\Framework\v4.0.20728`.</span></span>  
  
3. <span data-ttu-id="c71f1-134">Šifrujte nastavení konfigurace appSettings ve složce Web.config vydáním následujícího příkazu: `aspnet_regiis -pe "appSettings" -app "/servicemodelsamples" -prov "DataProtectionConfigurationProvider"`.</span><span class="sxs-lookup"><span data-stu-id="c71f1-134">Encrypt the appSettings configuration settings in the Web.config folder by issuing the following command: `aspnet_regiis -pe "appSettings" -app "/servicemodelsamples" -prov "DataProtectionConfigurationProvider"`.</span></span>  
  
 <span data-ttu-id="c71f1-135">Další informace o šifrování částí konfiguračních souborů naleznete v návodu na DPAPI v konfiguraci ASP.NET[(Building Secure ASP.NET Applications: Authentication, Authorization, and Secure Communication)](https://docs.microsoft.com/previous-versions/msp-n-p/ff649248(v=pandp.10))a how-to na RSA v ASP.NET konfiguraci ([Jak: Šifrovat konfigurační sekce v ASP.NET 2.0 pomocí RSA](https://docs.microsoft.com/previous-versions/msp-n-p/ff650304(v=pandp.10))).</span><span class="sxs-lookup"><span data-stu-id="c71f1-135">More information about encrypting sections of configuration files can be found by reading a how-to on DPAPI in ASP.NET configuration ([Building Secure ASP.NET Applications: Authentication, Authorization, and Secure Communication](https://docs.microsoft.com/previous-versions/msp-n-p/ff649248(v=pandp.10))) and a how-to on RSA in ASP.NET configuration ([How To: Encrypt Configuration Sections in ASP.NET 2.0 Using RSA](https://docs.microsoft.com/previous-versions/msp-n-p/ff650304(v=pandp.10))).</span></span>  
  
## <a name="locking-configuration-file-elements"></a><span data-ttu-id="c71f1-136">Zamykání prvků konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="c71f1-136">Locking configuration file elements</span></span>  
 <span data-ttu-id="c71f1-137">Ve scénářích hostovaných na webu je možné mít služby v podadresářích služeb.</span><span class="sxs-lookup"><span data-stu-id="c71f1-137">In Web-hosted scenarios, it is possible to have services in subdirectories of services.</span></span> <span data-ttu-id="c71f1-138">V těchto situacích jsou hodnoty konfigurace služby v podadresáři vypočteny tak, že se prozkoumá hodnoty v souboru Machine.config a postupně se sloučí se všemi soubory Web.config v nadřazených adresářích, které se přesunou dolů do adresářového stromu a nakonec sloučí Soubor Web.config v adresáři, který obsahuje službu.</span><span class="sxs-lookup"><span data-stu-id="c71f1-138">In these situations, configuration values for the service in the subdirectory are calculated by examining values in Machine.config and successively merging with any Web.config files in parent directories moving down the directory tree and finally merging the Web.config file in the directory that contains the service.</span></span> <span data-ttu-id="c71f1-139">Výchozím chováním většiny konfiguračních prvků je povolit konfiguračním souborům v podadresářích přepsat hodnoty nastavené v nadřazených adresářích.</span><span class="sxs-lookup"><span data-stu-id="c71f1-139">The default behavior for most configuration elements is to allow configuration files in subdirectories to override the values set in parent directories.</span></span> <span data-ttu-id="c71f1-140">V určitých situacích může být žádoucí zabránit tomu, aby konfigurační soubory v podadresářích přecvakovaly hodnoty nastavené v konfiguraci nadřazeného adresáře.</span><span class="sxs-lookup"><span data-stu-id="c71f1-140">In certain situations it may be desirable to prevent configuration files in subdirectories from overriding values set in parent directory configuration.</span></span>  
  
 <span data-ttu-id="c71f1-141">Rozhraní .NET Framework poskytuje způsob uzamčení prvků konfiguračního souboru tak, aby konfigurace, které přepíší uzamčené konfigurační prvky, vyvolaly výjimky za běhu.</span><span class="sxs-lookup"><span data-stu-id="c71f1-141">The .NET Framework provides a way to lock configuration file elements so that configurations that override locked configuration elements throw run-time exceptions.</span></span>  
  
 <span data-ttu-id="c71f1-142">Konfigurační prvek lze uzamknout zadáním atributu `lockItem` pro uzel v konfiguračním souboru, například pro uzamčení uzlu CalculatorServiceBehavior v konfiguračním souboru tak, aby kalkulačka služby v vnořených konfiguračních souborů nelze změnit chování, lze použít následující konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="c71f1-142">A configuration element can be locked by specifying the `lockItem` attribute for a node in the configuration file, for example, to lock the CalculatorServiceBehavior node in the configuration file so that calculator services in nested configuration files cannot change the behavior, the following configuration can be used.</span></span>  
  
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
  
 <span data-ttu-id="c71f1-143">Uzamčení konfiguračních prvků může být konkrétnější.</span><span class="sxs-lookup"><span data-stu-id="c71f1-143">Locking of configuration elements can be more specific.</span></span> <span data-ttu-id="c71f1-144">Seznam prvků lze zadat jako hodnotu `lockElements` pro uzamčení sady prvků v rámci kolekce dílčích prvků.</span><span class="sxs-lookup"><span data-stu-id="c71f1-144">A list of elements can be specified as the value to the `lockElements` to lock a set of elements within a collection of sub-elements.</span></span> <span data-ttu-id="c71f1-145">Seznam atributů lze zadat jako hodnotu `lockAttributes` pro uzamčení sady atributů v rámci prvku.</span><span class="sxs-lookup"><span data-stu-id="c71f1-145">A list of attributes can be specified as the value to the `lockAttributes` to lock a set of attributes within an element.</span></span> <span data-ttu-id="c71f1-146">Celou kolekci prvků nebo atributů lze uzamknout s `lockAllElementsExcept` výjimkou `lockAllAttributesExcept` zadaného seznamu zadáním atributů nebo v uzlu.</span><span class="sxs-lookup"><span data-stu-id="c71f1-146">An entire collection of elements or attributes can be locked except for a specified list by specifying the `lockAllElementsExcept` or `lockAllAttributesExcept` attributes on a node.</span></span>  
  
## <a name="pii-logging-configuration"></a><span data-ttu-id="c71f1-147">Konfigurace protokolování pii</span><span class="sxs-lookup"><span data-stu-id="c71f1-147">PII Logging Configuration</span></span>  
 <span data-ttu-id="c71f1-148">Protokolování pii je řízeno dvěma přepínači: nastavením pro celý počítač, které se nachází v souboru Machine.config, které umožňuje správci počítače povolit nebo odepřít protokolování pii a nastavení aplikace, které umožňuje správci aplikace přepínat protokolování pii pro každý v souboru Web.config nebo App.config.</span><span class="sxs-lookup"><span data-stu-id="c71f1-148">Logging of PII is controlled by two switches: a computer-wide setting found in Machine.config that allows a computer administrator to permit or deny logging of PII and an application setting that allows an application administrator to toggle logging of PII for each source in a Web.config or App.config file.</span></span>  
  
 <span data-ttu-id="c71f1-149">Nastavení celého počítače je `enableLoggingKnownPii` řízeno `false`nastavením `machineSettings` `true` nebo , v prvku v souboru Machine.config. Následující umožňuje aplikacím například zapnout protokolování pii.</span><span class="sxs-lookup"><span data-stu-id="c71f1-149">The computer-wide setting is controlled by setting `enableLoggingKnownPii` to `true` or `false`, in the `machineSettings` element in Machine.config. For example, the following allows applications to turn on logging of PII.</span></span>  
  
```xml  
<configuration>  
    <system.serviceModel>  
        <machineSettings enableLoggingKnownPii="true" />  
    </system.serviceModel>  
</configuration>  
```  
  
> [!NOTE]
> <span data-ttu-id="c71f1-150">Soubor Machine.config má výchozí umístění: %WINDIR%\Microsoft.NET\Framework\v2.0.50727\CONFIG.</span><span class="sxs-lookup"><span data-stu-id="c71f1-150">The Machine.config file has a default location: %WINDIR%\Microsoft.NET\Framework\v2.0.50727\CONFIG.</span></span>  
  
 <span data-ttu-id="c71f1-151">Pokud `enableLoggingKnownPii` atribut není k dispozici v Machine.config, protokolování PII není povoleno.</span><span class="sxs-lookup"><span data-stu-id="c71f1-151">If the `enableLoggingKnownPii` attribute is not present in Machine.config, logging of PII is not allowed.</span></span>  
  
 <span data-ttu-id="c71f1-152">Povolení protokolování pii pro aplikaci `logKnownPii` se provádí nastavením `true` `false` atributu zdrojového prvku do souboru Web.config nebo App.config nebo V souboru Web.config nebo App.config.</span><span class="sxs-lookup"><span data-stu-id="c71f1-152">Enabling logging of PII for an application is done by setting the `logKnownPii` attribute of the source element to `true` or `false` in the Web.config or App.config file.</span></span> <span data-ttu-id="c71f1-153">Následující umožňuje například protokolování pii pro protokolování zpráv a protokolování trasování.</span><span class="sxs-lookup"><span data-stu-id="c71f1-153">For example, the following enables logging of PII for both message logging and trace logging.</span></span>  
  
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
  
 <span data-ttu-id="c71f1-154">Pokud `logKnownPii` atribut není zadán, není protokolován pii.</span><span class="sxs-lookup"><span data-stu-id="c71f1-154">If the `logKnownPii` attribute is not specified, then PII is not logged.</span></span>  
  
 <span data-ttu-id="c71f1-155">PiI je protokolována `enableLoggingKnownPii` pouze `true`v `logKnownPii` případě, `true`že je obě nastavena na .</span><span class="sxs-lookup"><span data-stu-id="c71f1-155">PII is only logged if both `enableLoggingKnownPii` is set to `true`, and `logKnownPii` is set to `true`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c71f1-156">System.Diagnostics ignoruje všechny atributy na všech zdrojích kromě první ho uvedeného v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="c71f1-156">System.Diagnostics ignores all attributes on all sources except the first one listed in the configuration file.</span></span> <span data-ttu-id="c71f1-157">Přidání `logKnownPii` atributu do druhého zdroje v konfiguračním souboru nemá žádný vliv.</span><span class="sxs-lookup"><span data-stu-id="c71f1-157">Adding the `logKnownPii` attribute to the second source in the configuration file has no effect.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="c71f1-158">Chcete-li spustit tuto ukázku zahrnuje ruční úpravy Machine.config. Při úpravě souboru Machine.config je třeba dbát na to, aby byly spuštěny nesprávné hodnoty nebo syntaxe.</span><span class="sxs-lookup"><span data-stu-id="c71f1-158">To run this sample involves manual modification of Machine.config. Care should be taken when modifying Machine.config as incorrect values or syntax may prevent all .NET Framework applications from running.</span></span>  
  
 <span data-ttu-id="c71f1-159">Je také možné šifrovat prvky konfiguračního souboru pomocí DPAPI a RSA.</span><span class="sxs-lookup"><span data-stu-id="c71f1-159">It is also possible to encrypt configuration file elements using DPAPI and RSA.</span></span> <span data-ttu-id="c71f1-160">Další informace najdete na následujících odkazech:</span><span class="sxs-lookup"><span data-stu-id="c71f1-160">For more information, see the following links:</span></span>  
  
- <span data-ttu-id="c71f1-161">[Vytváření zabezpečených aplikací ASP.NET: ověřování, autorizace a zabezpečená komunikace](https://docs.microsoft.com/previous-versions/msp-n-p/ff649248(v=pandp.10))</span><span class="sxs-lookup"><span data-stu-id="c71f1-161">[Building Secure ASP.NET Applications: Authentication, Authorization, and Secure Communication](https://docs.microsoft.com/previous-versions/msp-n-p/ff649248(v=pandp.10))</span></span>  
  
- <span data-ttu-id="c71f1-162">[Postup: Šifrování konfiguračních oddílů v ASP.NET 2.0 pomocí rsa](https://docs.microsoft.com/previous-versions/msp-n-p/ff650304(v=pandp.10))</span><span class="sxs-lookup"><span data-stu-id="c71f1-162">[How To: Encrypt Configuration Sections in ASP.NET 2.0 Using RSA](https://docs.microsoft.com/previous-versions/msp-n-p/ff650304(v=pandp.10))</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="c71f1-163">Chcete-li nastavit, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="c71f1-163">To set up, build and run the sample</span></span>  
  
1. <span data-ttu-id="c71f1-164">Ujistěte se, že jste provedli [jednorázový postup instalace pro ukázky windows communication foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c71f1-164">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="c71f1-165">Upravit soubor Machine.config `enableLoggingKnownPii` a `true`nastavit atribut na , v případě potřeby přidat nadřazené uzly.</span><span class="sxs-lookup"><span data-stu-id="c71f1-165">Edit Machine.config to set the `enableLoggingKnownPii` attribute to `true`, adding the parent nodes if necessary.</span></span>  
  
3. <span data-ttu-id="c71f1-166">Chcete-li vytvořit c# nebo Visual Basic .NET vydání řešení, postupujte podle pokynů v [sestavení windows communication foundation ukázky](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c71f1-166">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4. <span data-ttu-id="c71f1-167">Chcete-li spustit ukázku v konfiguraci jednoho nebo mezi počítači, postupujte podle pokynů v [části Spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c71f1-167">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
#### <a name="to-clean-up-the-sample"></a><span data-ttu-id="c71f1-168">Vyčištění vzorku</span><span class="sxs-lookup"><span data-stu-id="c71f1-168">To clean up the sample</span></span>  
  
1. <span data-ttu-id="c71f1-169">Chcete-li nastavit `enableLoggingKnownPii` atribut na `false`soubor , upravit soubor Machine.config.</span><span class="sxs-lookup"><span data-stu-id="c71f1-169">Edit Machine.config to set the `enableLoggingKnownPii` attribute to `false`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c71f1-170">Viz také</span><span class="sxs-lookup"><span data-stu-id="c71f1-170">See also</span></span>

- <span data-ttu-id="c71f1-171">[Vzorky monitorování appfabricu](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="c71f1-171">[AppFabric Monitoring Samples](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))</span></span>
