---
title: Bezpečnostní uzamčení PII
ms.date: 03/30/2017
ms.assetid: c44fb338-9527-4dd0-8607-b8787d15acb4
ms.openlocfilehash: 64c07825f0756b029781e173eb2098711cdbe60a
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84600474"
---
# <a name="pii-security-lockdown"></a><span data-ttu-id="68422-102">Bezpečnostní uzamčení PII</span><span class="sxs-lookup"><span data-stu-id="68422-102">PII Security Lockdown</span></span>
<span data-ttu-id="68422-103">Tato ukázka předvádí, jak řídit několik funkcí služby Windows Communication Foundation (WCF) souvisejících se zabezpečením pomocí:</span><span class="sxs-lookup"><span data-stu-id="68422-103">This sample demonstrates how to control several security-related features of a Windows Communication Foundation (WCF) service by:</span></span>  
  
- <span data-ttu-id="68422-104">Šifrování citlivých informací v konfiguračním souboru služby.</span><span class="sxs-lookup"><span data-stu-id="68422-104">Encrypting sensitive information in a service's configuration file.</span></span>  
  
- <span data-ttu-id="68422-105">Uzamykání prvků v konfiguračním souboru, aby vnořené podadresáře služby nemohly přepsat nastavení.</span><span class="sxs-lookup"><span data-stu-id="68422-105">Locking elements in the configuration file so that nested service subdirectories cannot override settings.</span></span>  
  
- <span data-ttu-id="68422-106">Řízení protokolování identifikovatelné osobní údaje (PII) v protokolech trasování a zpráv.</span><span class="sxs-lookup"><span data-stu-id="68422-106">Controlling the logging of Personally Identifiable Information (PII) in trace and message logs.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="68422-107">Ukázky již mohou být nainstalovány v počítači.</span><span class="sxs-lookup"><span data-stu-id="68422-107">The samples may already be installed on your computer.</span></span> <span data-ttu-id="68422-108">Než budete pokračovat, vyhledejte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="68422-108">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="68422-109">Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek.</span><span class="sxs-lookup"><span data-stu-id="68422-109">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="68422-110">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="68422-110">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\SecurityLockdown`  
  
## <a name="discussion"></a><span data-ttu-id="68422-111">Účely</span><span class="sxs-lookup"><span data-stu-id="68422-111">Discussion</span></span>  
 <span data-ttu-id="68422-112">Každá z těchto funkcí se dá použít samostatně nebo společně k řízení aspektů zabezpečení služby.</span><span class="sxs-lookup"><span data-stu-id="68422-112">Each of these features can be used separately or together to control aspects of a service's security.</span></span> <span data-ttu-id="68422-113">Nejedná se o nekonečný Průvodce zabezpečením služby WCF.</span><span class="sxs-lookup"><span data-stu-id="68422-113">This is not a definitive guide to securing a WCF service.</span></span>  
  
 <span data-ttu-id="68422-114">Konfigurační soubory .NET Framework můžou obsahovat citlivé informace, jako jsou připojovací řetězce pro připojení k databázím.</span><span class="sxs-lookup"><span data-stu-id="68422-114">The .NET Framework configuration files can contain sensitive information such as connection strings to connect to databases.</span></span> <span data-ttu-id="68422-115">Ve sdílených scénářích hostovaných na webu může být žádoucí zašifrovat tyto informace v konfiguračním souboru pro službu, aby data obsažená v konfiguračním souboru byla odolná vůči příležitostnému zobrazení.</span><span class="sxs-lookup"><span data-stu-id="68422-115">In shared, Web-hosted scenarios it may be desirable to encrypt this information in the configuration file for a service so that the data contained within the configuration file is resistant to casual viewing.</span></span> <span data-ttu-id="68422-116">.NET Framework 2,0 a novější má schopnost šifrovat části konfiguračního souboru pomocí rozhraní DPAPI (Windows Data Protection Application Programming Interface) nebo zprostředkovatele kryptografických služeb RSA.</span><span class="sxs-lookup"><span data-stu-id="68422-116">.NET Framework 2.0 and later has the ability to encrypt portions of the configuration file using the Windows Data Protection application programming interface (DPAPI) or the RSA Cryptographic provider.</span></span> <span data-ttu-id="68422-117">Aspnet_regiis. exe používající rozhraní DPAPI nebo RSA může šifrovat vybrané části konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="68422-117">The aspnet_regiis.exe using the DPAPI or RSA can encrypt select portions of a configuration file.</span></span>  
  
 <span data-ttu-id="68422-118">Ve scénářích hostovaných na webu je možné mít služby v podadresářích jiných služeb.</span><span class="sxs-lookup"><span data-stu-id="68422-118">In Web-hosted scenarios it is possible to have services in subdirectories of other services.</span></span> <span data-ttu-id="68422-119">Výchozí sémantika pro určení hodnot konfigurace umožňuje, aby konfigurační soubory ve vnořených adresářích přepsaly konfigurační hodnoty v nadřazeném adresáři.</span><span class="sxs-lookup"><span data-stu-id="68422-119">The default semantic for determining configuration values allows configuration files in the nested directories to override the configuration values in the parent directory.</span></span> <span data-ttu-id="68422-120">V některých situacích může být to nežádoucí z nejrůznějších důvodů.</span><span class="sxs-lookup"><span data-stu-id="68422-120">In certain situations this may be undesirable for a variety of reasons.</span></span> <span data-ttu-id="68422-121">Konfigurace služby WCF podporuje uzamykání hodnot konfigurace, aby vnořená konfigurace generovala výjimky při spuštění vnořené služby pomocí přepsaných hodnot konfigurace.</span><span class="sxs-lookup"><span data-stu-id="68422-121">WCF service configuration supports the locking of configuration values so that nested configuration generates exceptions when a nested service is run using overridden configuration values.</span></span>  
  
 <span data-ttu-id="68422-122">Tato ukázka předvádí, jak řídit protokolování známých identifikovatelných osobních údajů (PII) v protokolech trasování a zpráv, jako je uživatelské jméno a heslo.</span><span class="sxs-lookup"><span data-stu-id="68422-122">This sample demonstrates how to control the logging of known Personally Identifiable Information (PII) in trace and message logs, such as username and password.</span></span> <span data-ttu-id="68422-123">Ve výchozím nastavení je protokolování známého PII zakázáno, ale v některých situacích může být protokolování PII důležité při ladění aplikace.</span><span class="sxs-lookup"><span data-stu-id="68422-123">By default, logging of known PII is disabled however in certain situations logging of PII can be important in debugging an application.</span></span> <span data-ttu-id="68422-124">Tato ukázka je založena na [Začínáme](getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="68422-124">This sample is based on the [Getting Started](getting-started-sample.md).</span></span> <span data-ttu-id="68422-125">Kromě toho tato ukázka používá trasování a protokolování zpráv.</span><span class="sxs-lookup"><span data-stu-id="68422-125">In addition, this sample uses tracing and message logging.</span></span> <span data-ttu-id="68422-126">Další informace najdete v ukázce [trasování a protokolování zpráv](tracing-and-message-logging.md) .</span><span class="sxs-lookup"><span data-stu-id="68422-126">For more information, see the [Tracing and Message Logging](tracing-and-message-logging.md) sample.</span></span>  
  
## <a name="encrypting-configuration-file-elements"></a><span data-ttu-id="68422-127">Šifrování elementů konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="68422-127">Encrypting Configuration File Elements</span></span>  
 <span data-ttu-id="68422-128">Pro účely zabezpečení ve sdíleném prostředí pro hostování webů může být vhodné zašifrovat určité konfigurační prvky, například databázové připojovací řetězce, které mohou obsahovat citlivé informace.</span><span class="sxs-lookup"><span data-stu-id="68422-128">For security purposes in a shared Web-hosting environment, it may be desirable to encrypt certain configuration elements, such as database connection strings that may contain sensitive information.</span></span> <span data-ttu-id="68422-129">Element konfigurace může být zašifrovaný pomocí nástroje aspnet_regiis. exe, který se nachází ve složce .NET Framework, například%WINDIR%\Microsoft.NET\Framework\v4.0.20728..</span><span class="sxs-lookup"><span data-stu-id="68422-129">A configuration element may be encrypted using the aspnet_regiis.exe tool found in the .NET Framework folder For example, %WINDIR%\Microsoft.NET\Framework\v4.0.20728.</span></span>  
  
#### <a name="to-encrypt-the-values-in-the-appsettings-section-in-webconfig-for-the-sample"></a><span data-ttu-id="68422-130">Chcete-li zašifrovat hodnoty v oddílu appSettings v souboru Web. config pro ukázku</span><span class="sxs-lookup"><span data-stu-id="68422-130">To encrypt the values in the appSettings section in Web.config for the sample</span></span>  
  
1. <span data-ttu-id="68422-131">Otevřete příkazový řádek pomocí rutiny Start->spustit....</span><span class="sxs-lookup"><span data-stu-id="68422-131">Open a command prompt by using Start->Run….</span></span> <span data-ttu-id="68422-132">Zadejte `cmd` a klikněte na **OK**.</span><span class="sxs-lookup"><span data-stu-id="68422-132">Type in `cmd` and click **OK**.</span></span>  
  
2. <span data-ttu-id="68422-133">Přejděte do aktuálního adresáře .NET Framework tím, že vydáváte následující příkaz: `cd %WINDIR%\Microsoft.NET\Framework\v4.0.20728` .</span><span class="sxs-lookup"><span data-stu-id="68422-133">Navigate to the current .NET Framework directory by issuing the following command: `cd %WINDIR%\Microsoft.NET\Framework\v4.0.20728`.</span></span>  
  
3. <span data-ttu-id="68422-134">Zašifrujte konfigurační nastavení appSettings ve složce Web. config vyvoláním následujícího příkazu: `aspnet_regiis -pe "appSettings" -app "/servicemodelsamples" -prov "DataProtectionConfigurationProvider"` .</span><span class="sxs-lookup"><span data-stu-id="68422-134">Encrypt the appSettings configuration settings in the Web.config folder by issuing the following command: `aspnet_regiis -pe "appSettings" -app "/servicemodelsamples" -prov "DataProtectionConfigurationProvider"`.</span></span>  
  
 <span data-ttu-id="68422-135">Další informace o šifrování oddílů konfiguračních souborů najdete v tématu věnovaném konfiguraci rozhraní DPAPI v ASP.NET ([sestavování zabezpečených aplikací ASP.NET: ověřování, autorizace a zabezpečená komunikace](https://docs.microsoft.com/previous-versions/msp-n-p/ff649248(v=pandp.10))) a s postupy v tématu Konfigurace ASP.NET v ([Postupy: šifrování konfiguračních oddílů v ASP.NET 2,0 pomocí RSA](https://docs.microsoft.com/previous-versions/msp-n-p/ff650304(v=pandp.10))).</span><span class="sxs-lookup"><span data-stu-id="68422-135">More information about encrypting sections of configuration files can be found by reading a how-to on DPAPI in ASP.NET configuration ([Building Secure ASP.NET Applications: Authentication, Authorization, and Secure Communication](https://docs.microsoft.com/previous-versions/msp-n-p/ff649248(v=pandp.10))) and a how-to on RSA in ASP.NET configuration ([How To: Encrypt Configuration Sections in ASP.NET 2.0 Using RSA](https://docs.microsoft.com/previous-versions/msp-n-p/ff650304(v=pandp.10))).</span></span>  
  
## <a name="locking-configuration-file-elements"></a><span data-ttu-id="68422-136">Zamykání elementů konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="68422-136">Locking configuration file elements</span></span>  
 <span data-ttu-id="68422-137">Ve scénářích hostovaných na webu je možné mít služby v podadresářích služeb.</span><span class="sxs-lookup"><span data-stu-id="68422-137">In Web-hosted scenarios, it is possible to have services in subdirectories of services.</span></span> <span data-ttu-id="68422-138">V těchto situacích se hodnoty konfigurace pro službu v podadresáři vypočítávají prozkoumáním hodnot v souboru Machine. config a následným sloučením se soubory Web. config v nadřazených adresářích, které přesunují strom adresářů a nakonec sloučí soubor Web. config v adresáři, který obsahuje službu.</span><span class="sxs-lookup"><span data-stu-id="68422-138">In these situations, configuration values for the service in the subdirectory are calculated by examining values in Machine.config and successively merging with any Web.config files in parent directories moving down the directory tree and finally merging the Web.config file in the directory that contains the service.</span></span> <span data-ttu-id="68422-139">Výchozím chováním pro většinu konfiguračních elementů je umožnit, aby konfigurační soubory v podadresářích přepsaly hodnoty nastavené v nadřazených adresářích.</span><span class="sxs-lookup"><span data-stu-id="68422-139">The default behavior for most configuration elements is to allow configuration files in subdirectories to override the values set in parent directories.</span></span> <span data-ttu-id="68422-140">V některých situacích může být žádoucí zabránit konfiguračním souborům v podadresářích z přepsání hodnot nastavených v konfiguraci nadřazeného adresáře.</span><span class="sxs-lookup"><span data-stu-id="68422-140">In certain situations it may be desirable to prevent configuration files in subdirectories from overriding values set in parent directory configuration.</span></span>  
  
 <span data-ttu-id="68422-141">.NET Framework poskytuje způsob, jak uzamknout prvky konfiguračního souboru tak, aby konfigurace, které přepíší uzamčené konfigurační prvky, vyvolaly výjimky za běhu.</span><span class="sxs-lookup"><span data-stu-id="68422-141">The .NET Framework provides a way to lock configuration file elements so that configurations that override locked configuration elements throw run-time exceptions.</span></span>  
  
 <span data-ttu-id="68422-142">Element konfigurace může být uzamčen zadáním `lockItem` atributu pro uzel v konfiguračním souboru, například pro uzamknutí uzlu CalculatorServiceBehavior v konfiguračním souboru, aby služby kalkulačky ve vnořených konfiguračních souborech nemohly změnit chování, lze použít následující konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="68422-142">A configuration element can be locked by specifying the `lockItem` attribute for a node in the configuration file, for example, to lock the CalculatorServiceBehavior node in the configuration file so that calculator services in nested configuration files cannot change the behavior, the following configuration can be used.</span></span>  
  
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
  
 <span data-ttu-id="68422-143">Uzamykání konfiguračních elementů může být konkrétnější.</span><span class="sxs-lookup"><span data-stu-id="68422-143">Locking of configuration elements can be more specific.</span></span> <span data-ttu-id="68422-144">Seznam elementů lze zadat jako hodnotu pro `lockElements` uzamknutí sady prvků v kolekci dílčích prvků.</span><span class="sxs-lookup"><span data-stu-id="68422-144">A list of elements can be specified as the value to the `lockElements` to lock a set of elements within a collection of sub-elements.</span></span> <span data-ttu-id="68422-145">Seznam atributů lze zadat jako hodnotu pro `lockAttributes` uzamknutí sady atributů v rámci elementu.</span><span class="sxs-lookup"><span data-stu-id="68422-145">A list of attributes can be specified as the value to the `lockAttributes` to lock a set of attributes within an element.</span></span> <span data-ttu-id="68422-146">Celá kolekce prvků nebo atributů může být uzamčena s výjimkou zadaného seznamu zadáním `lockAllElementsExcept` `lockAllAttributesExcept` atributů nebo v uzlu.</span><span class="sxs-lookup"><span data-stu-id="68422-146">An entire collection of elements or attributes can be locked except for a specified list by specifying the `lockAllElementsExcept` or `lockAllAttributesExcept` attributes on a node.</span></span>  
  
## <a name="pii-logging-configuration"></a><span data-ttu-id="68422-147">Konfigurace protokolování PII</span><span class="sxs-lookup"><span data-stu-id="68422-147">PII Logging Configuration</span></span>  
 <span data-ttu-id="68422-148">Přihlášení k PII je ovládáno dvěma přepínači: nastavení pro celé počítače v souboru Machine. config, které umožňuje správcům počítače povolit nebo odepřít protokolování PII a nastavení aplikace, které umožňuje správci aplikace přepnout protokolování PII pro každý zdroj v souboru Web. config nebo App. config.</span><span class="sxs-lookup"><span data-stu-id="68422-148">Logging of PII is controlled by two switches: a computer-wide setting found in Machine.config that allows a computer administrator to permit or deny logging of PII and an application setting that allows an application administrator to toggle logging of PII for each source in a Web.config or App.config file.</span></span>  
  
 <span data-ttu-id="68422-149">Nastavení na úrovni počítače je řízeno nastavením `enableLoggingKnownPii` na `true` nebo `false` , v `machineSettings` elementu v souboru Machine. config. Následující příklad umožňuje aplikacím zapnout protokolování PII.</span><span class="sxs-lookup"><span data-stu-id="68422-149">The computer-wide setting is controlled by setting `enableLoggingKnownPii` to `true` or `false`, in the `machineSettings` element in Machine.config. For example, the following allows applications to turn on logging of PII.</span></span>  
  
```xml  
<configuration>  
    <system.serviceModel>  
        <machineSettings enableLoggingKnownPii="true" />  
    </system.serviceModel>  
</configuration>  
```  
  
> [!NOTE]
> <span data-ttu-id="68422-150">Soubor Machine. config má výchozí umístění:%WINDIR%\Microsoft.NET\Framework\v2.0.50727\CONFIG.</span><span class="sxs-lookup"><span data-stu-id="68422-150">The Machine.config file has a default location: %WINDIR%\Microsoft.NET\Framework\v2.0.50727\CONFIG.</span></span>  
  
 <span data-ttu-id="68422-151">Pokud `enableLoggingKnownPii` atribut není přítomen v souboru Machine. config, není povoleno protokolování PII.</span><span class="sxs-lookup"><span data-stu-id="68422-151">If the `enableLoggingKnownPii` attribute is not present in Machine.config, logging of PII is not allowed.</span></span>  
  
 <span data-ttu-id="68422-152">Povolení protokolování PII pro aplikaci je provedeno nastavením `logKnownPii` atributu zdrojového prvku na `true` nebo `false` v souboru Web. config nebo App. config.</span><span class="sxs-lookup"><span data-stu-id="68422-152">Enabling logging of PII for an application is done by setting the `logKnownPii` attribute of the source element to `true` or `false` in the Web.config or App.config file.</span></span> <span data-ttu-id="68422-153">Následující příklad umožňuje protokolování PII pro protokolování zpráv a protokolování trasování.</span><span class="sxs-lookup"><span data-stu-id="68422-153">For example, the following enables logging of PII for both message logging and trace logging.</span></span>  
  
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
  
 <span data-ttu-id="68422-154">Pokud `logKnownPii` atribut není zadán, pak PII není protokolován.</span><span class="sxs-lookup"><span data-stu-id="68422-154">If the `logKnownPii` attribute is not specified, then PII is not logged.</span></span>  
  
 <span data-ttu-id="68422-155">PII je protokolováno pouze `enableLoggingKnownPii` v případě, že je nastavena na hodnotu `true` a `logKnownPii` je nastavena na `true` .</span><span class="sxs-lookup"><span data-stu-id="68422-155">PII is only logged if both `enableLoggingKnownPii` is set to `true`, and `logKnownPii` is set to `true`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="68422-156">System. Diagnostics ignoruje všechny atributy všech zdrojů s výjimkou prvního, který je uveden v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="68422-156">System.Diagnostics ignores all attributes on all sources except the first one listed in the configuration file.</span></span> <span data-ttu-id="68422-157">Přidání `logKnownPii` atributu k druhému zdroji v konfiguračním souboru nemá žádný vliv.</span><span class="sxs-lookup"><span data-stu-id="68422-157">Adding the `logKnownPii` attribute to the second source in the configuration file has no effect.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="68422-158">Spuštění této ukázky zahrnuje ruční úpravu souboru Machine. config. Při úpravách Machine. config jako nesprávné hodnoty nebo syntaxe může zabránit spuštění všech aplikací .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="68422-158">To run this sample involves manual modification of Machine.config. Care should be taken when modifying Machine.config as incorrect values or syntax may prevent all .NET Framework applications from running.</span></span>  
  
 <span data-ttu-id="68422-159">Je také možné zašifrovat prvky konfiguračního souboru pomocí DPAPI a RSA.</span><span class="sxs-lookup"><span data-stu-id="68422-159">It is also possible to encrypt configuration file elements using DPAPI and RSA.</span></span> <span data-ttu-id="68422-160">Další informace najdete na následujících odkazech:</span><span class="sxs-lookup"><span data-stu-id="68422-160">For more information, see the following links:</span></span>  
  
- <span data-ttu-id="68422-161">[Sestavování zabezpečených aplikací ASP.NET: ověřování, autorizace a zabezpečená komunikace](https://docs.microsoft.com/previous-versions/msp-n-p/ff649248(v=pandp.10))</span><span class="sxs-lookup"><span data-stu-id="68422-161">[Building Secure ASP.NET Applications: Authentication, Authorization, and Secure Communication](https://docs.microsoft.com/previous-versions/msp-n-p/ff649248(v=pandp.10))</span></span>  
  
- <span data-ttu-id="68422-162">[Postupy: šifrování konfiguračních oddílů v ASP.NET 2,0 pomocí RSA](https://docs.microsoft.com/previous-versions/msp-n-p/ff650304(v=pandp.10))</span><span class="sxs-lookup"><span data-stu-id="68422-162">[How To: Encrypt Configuration Sections in ASP.NET 2.0 Using RSA](https://docs.microsoft.com/previous-versions/msp-n-p/ff650304(v=pandp.10))</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="68422-163">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="68422-163">To set up, build and run the sample</span></span>  
  
1. <span data-ttu-id="68422-164">Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="68422-164">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="68422-165">Úpravou Machine. config nastavte `enableLoggingKnownPii` atribut na `true` , pokud je to nutné, přidejte nadřazené uzly.</span><span class="sxs-lookup"><span data-stu-id="68422-165">Edit Machine.config to set the `enableLoggingKnownPii` attribute to `true`, adding the parent nodes if necessary.</span></span>  
  
3. <span data-ttu-id="68422-166">Chcete-li sestavit edici C# nebo Visual Basic .NET, postupujte podle pokynů v tématu [sestavování ukázek Windows Communication Foundation](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="68422-166">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
4. <span data-ttu-id="68422-167">Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="68422-167">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
#### <a name="to-clean-up-the-sample"></a><span data-ttu-id="68422-168">Vyčištění ukázky</span><span class="sxs-lookup"><span data-stu-id="68422-168">To clean up the sample</span></span>  
  
1. <span data-ttu-id="68422-169">Úpravou souboru Machine. config nastavte `enableLoggingKnownPii` atribut na hodnotu `false` .</span><span class="sxs-lookup"><span data-stu-id="68422-169">Edit Machine.config to set the `enableLoggingKnownPii` attribute to `false`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68422-170">Viz také</span><span class="sxs-lookup"><span data-stu-id="68422-170">See also</span></span>

- <span data-ttu-id="68422-171">[Ukázky monitorování technologie AppFabric](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="68422-171">[AppFabric Monitoring Samples](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))</span></span>
