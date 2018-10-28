---
title: Bezpečnostní uzamčení PII
ms.date: 03/30/2017
ms.assetid: c44fb338-9527-4dd0-8607-b8787d15acb4
ms.openlocfilehash: 48b62ed5c27463b863ff585520a4b42fc4c83f88
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2018
ms.locfileid: "50195135"
---
# <a name="pii-security-lockdown"></a><span data-ttu-id="c5dbd-102">Bezpečnostní uzamčení PII</span><span class="sxs-lookup"><span data-stu-id="c5dbd-102">PII Security Lockdown</span></span>
<span data-ttu-id="c5dbd-103">Tento příklad ukazuje, jak řídit několik funkcí souvisejících se zabezpečením pomocí služby Windows Communication Foundation (WCF):</span><span class="sxs-lookup"><span data-stu-id="c5dbd-103">This sample demonstrates how to control several security-related features of a Windows Communication Foundation (WCF) service by:</span></span>  
  
-   <span data-ttu-id="c5dbd-104">Šifrování citlivých informací v konfiguračním souboru služby.</span><span class="sxs-lookup"><span data-stu-id="c5dbd-104">Encrypting sensitive information in a service's configuration file.</span></span>  
  
-   <span data-ttu-id="c5dbd-105">Uzamčení elementů v konfiguračním souboru tak, aby vnořené podadresářů služby nelze přepsat nastavení.</span><span class="sxs-lookup"><span data-stu-id="c5dbd-105">Locking elements in the configuration file so that nested service subdirectories cannot override settings.</span></span>  
  
-   <span data-ttu-id="c5dbd-106">Řízení přihlašování z identifikovatelné osobní údaje (PII) v protokolech trasování a zprávy.</span><span class="sxs-lookup"><span data-stu-id="c5dbd-106">Controlling the logging of Personally Identifiable Information (PII) in trace and message logs.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="c5dbd-107">Vzorky mohou již být nainstalováno ve vašem počítači.</span><span class="sxs-lookup"><span data-stu-id="c5dbd-107">The samples may already be installed on your computer.</span></span> <span data-ttu-id="c5dbd-108">Před pokračováním zkontrolujte následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="c5dbd-108">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="c5dbd-109">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="c5dbd-109">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="c5dbd-110">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="c5dbd-110">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\SecurityLockdown`  
  
## <a name="discussion"></a><span data-ttu-id="c5dbd-111">Diskuse</span><span class="sxs-lookup"><span data-stu-id="c5dbd-111">Discussion</span></span>  
 <span data-ttu-id="c5dbd-112">Každá z těchto funkcí může být používat samostatně nebo společně k řízení aspektů zabezpečení služby.</span><span class="sxs-lookup"><span data-stu-id="c5dbd-112">Each of these features can be used separately or together to control aspects of a service's security.</span></span> <span data-ttu-id="c5dbd-113">Nejedná se úplnou příručku k zabezpečení ve službě WCF.</span><span class="sxs-lookup"><span data-stu-id="c5dbd-113">This is not a definitive guide to securing a WCF service.</span></span>  
  
 <span data-ttu-id="c5dbd-114">Konfigurační soubory rozhraní .NET Framework mohou obsahovat citlivé údaje, jako je například připojovací řetězce k připojení k databázím.</span><span class="sxs-lookup"><span data-stu-id="c5dbd-114">The .NET Framework configuration files can contain sensitive information such as connection strings to connect to databases.</span></span> <span data-ttu-id="c5dbd-115">Ve sdílené, hostovaný Web scénářích může být žádoucí k zašifrování těchto informací v konfiguračním souboru služby tak, aby data obsažená v konfiguračním souboru byla odolná vůči příležitostné zobrazení.</span><span class="sxs-lookup"><span data-stu-id="c5dbd-115">In shared, Web-hosted scenarios it may be desirable to encrypt this information in the configuration file for a service so that the data contained within the configuration file is resistant to casual viewing.</span></span> <span data-ttu-id="c5dbd-116">Rozhraní .NET framework 2.0 a novější má možnost šifrování části konfiguračního souboru pomocí rozhraní Windows Data Protection application programming rozhraní DPAPI nebo zprostředkovatel RSA kryptografických služeb.</span><span class="sxs-lookup"><span data-stu-id="c5dbd-116">.NET Framework 2.0 and later has the ability to encrypt portions of the configuration file using the Windows Data Protection application programming interface (DPAPI) or the RSA Cryptographic provider.</span></span> <span data-ttu-id="c5dbd-117">Vyberte část konfigurační soubor můžete šifrovat aspnet_regiis.exe pomocí rozhraní DPAPI nebo RSA.</span><span class="sxs-lookup"><span data-stu-id="c5dbd-117">The aspnet_regiis.exe using the DPAPI or RSA can encrypt select portions of a configuration file.</span></span>  
  
 <span data-ttu-id="c5dbd-118">V hostované Web scénářích je možné mít služby v podadresářích dalších služeb.</span><span class="sxs-lookup"><span data-stu-id="c5dbd-118">In Web-hosted scenarios it is possible to have services in subdirectories of other services.</span></span> <span data-ttu-id="c5dbd-119">Výchozí sémantické pro určení hodnoty konfigurace umožňuje konfigurační soubory v adresářích vnořené přepsat hodnoty konfigurace v nadřazeném adresáři.</span><span class="sxs-lookup"><span data-stu-id="c5dbd-119">The default semantic for determining configuration values allows configuration files in the nested directories to override the configuration values in the parent directory.</span></span> <span data-ttu-id="c5dbd-120">V některých situacích může nežádoucí u z různých důvodů.</span><span class="sxs-lookup"><span data-stu-id="c5dbd-120">In certain situations this may be undesirable for a variety of reasons.</span></span> <span data-ttu-id="c5dbd-121">Podporuje konfigurace služby WCF uzamčení konfigurační hodnoty tak, aby vnořené konfigurace generuje výjimky při spuštění pomocí služby vnořené přepsat hodnoty konfigurace.</span><span class="sxs-lookup"><span data-stu-id="c5dbd-121">WCF service configuration supports the locking of configuration values so that nested configuration generates exceptions when a nested service is run using overridden configuration values.</span></span>  
  
 <span data-ttu-id="c5dbd-122">Tento příklad ukazuje, jak řízení protokolování ze známých identifikovatelné osobní údaje (PII) v protokolech trasování a zprávy, jako je například uživatelské jméno a heslo.</span><span class="sxs-lookup"><span data-stu-id="c5dbd-122">This sample demonstrates how to control the logging of known Personally Identifiable Information (PII) in trace and message logs, such as username and password.</span></span> <span data-ttu-id="c5dbd-123">Ve výchozím nastavení je zakázáno přihlášení známého PII, ale v některých situacích může být důležité při ladění aplikace protokolování identifikovatelné osobní údaje.</span><span class="sxs-lookup"><span data-stu-id="c5dbd-123">By default, logging of known PII is disabled however in certain situations logging of PII can be important in debugging an application.</span></span> <span data-ttu-id="c5dbd-124">Tato ukázka je založena na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="c5dbd-124">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span> <span data-ttu-id="c5dbd-125">Kromě toho tato ukázka používá trasování a protokolování zpráv.</span><span class="sxs-lookup"><span data-stu-id="c5dbd-125">In addition, this sample uses tracing and message logging.</span></span> <span data-ttu-id="c5dbd-126">Další informace najdete v tématu [trasování a protokolování zpráv](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md) vzorku.</span><span class="sxs-lookup"><span data-stu-id="c5dbd-126">For more information, see the [Tracing and Message Logging](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md) sample.</span></span>  
  
## <a name="encrypting-configuration-file-elements"></a><span data-ttu-id="c5dbd-127">Šifrování souboru elementy konfigurace</span><span class="sxs-lookup"><span data-stu-id="c5dbd-127">Encrypting Configuration File Elements</span></span>  
 <span data-ttu-id="c5dbd-128">Z bezpečnostních důvodů ve sdíleném prostředí hostování webů může být žádoucí šifrovat určité konfigurační prvky, jako jsou databázové připojovací řetězce, které mohou obsahovat citlivé informace.</span><span class="sxs-lookup"><span data-stu-id="c5dbd-128">For security purposes in a shared Web-hosting environment, it may be desirable to encrypt certain configuration elements, such as database connection strings that may contain sensitive information.</span></span> <span data-ttu-id="c5dbd-129">Prvek konfigurace je možné zašifrovat pomocí aspnet_regiis.exe nástroj nachází ve složce % například WINDIR%\Micrsoft.NET\Framework\v4.0.20728 rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c5dbd-129">A configuration element may be encrypted using the aspnet_regiis.exe tool found in the .NET Framework folder For example, %WINDIR%\Micrsoft.NET\Framework\v4.0.20728.</span></span>  
  
#### <a name="to-encrypt-the-values-in-the-appsettings-section-in-webconfig-for-the-sample"></a><span data-ttu-id="c5dbd-130">K šifrování hodnoty v oddíle appSettings souboru Web.config pro ukázku</span><span class="sxs-lookup"><span data-stu-id="c5dbd-130">To encrypt the values in the appSettings section in Web.config for the sample</span></span>  
  
1.  <span data-ttu-id="c5dbd-131">Otevřete příkazový řádek s použitím Start -> spustit...</span><span class="sxs-lookup"><span data-stu-id="c5dbd-131">Open a command prompt by using Start->Run….</span></span> <span data-ttu-id="c5dbd-132">Zadejte `cmd` a klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="c5dbd-132">Type in `cmd` and click **OK**.</span></span>  
  
2.  <span data-ttu-id="c5dbd-133">Přejděte do aktuálního adresáře rozhraní .NET Framework pomocí následujícího příkazu: `cd %WINDIR%\Microsoft.NET\Framework\v4.0.20728`.</span><span class="sxs-lookup"><span data-stu-id="c5dbd-133">Navigate to the current .NET Framework directory by issuing the following command: `cd %WINDIR%\Microsoft.NET\Framework\v4.0.20728`.</span></span>  
  
3.  <span data-ttu-id="c5dbd-134">Nastavení konfigurace appSettings ve složce Web.config šifrovat pomocí následujícího příkazu: `aspnet_regiis -pe "appSettings" -app "/servicemodelsamples" -prov "DataProtectionConfigurationProvider"`.</span><span class="sxs-lookup"><span data-stu-id="c5dbd-134">Encrypt the appSettings configuration settings in the Web.config folder by issuing the following command: `aspnet_regiis -pe "appSettings" -app "/servicemodelsamples" -prov "DataProtectionConfigurationProvider"`.</span></span>  
  
 <span data-ttu-id="c5dbd-135">Další informace o šifrování oddíly konfiguračních souborů můžete zobrazit tak čtení postupy na rozhraní DPAPI v konfiguraci technologie ASP.NET ([vytváření bezpečných aplikací technologie ASP.NET: ověřování, autorizaci a zabezpečená komunikace](https://go.microsoft.com/fwlink/?LinkId=95137)) a postupy v RSA v konfiguraci technologie ASP.NET ([postupy: šifrování konfigurační oddíly funkce v ASP.NET 2.0 pomocí RSA](https://go.microsoft.com/fwlink/?LinkId=95138)).</span><span class="sxs-lookup"><span data-stu-id="c5dbd-135">More information about encrypting sections of configuration files can be found by reading a how-to on DPAPI in ASP.NET configuration ([Building Secure ASP.NET Applications: Authentication, Authorization, and Secure Communication](https://go.microsoft.com/fwlink/?LinkId=95137)) and a how-to on RSA in ASP.NET configuration ([How To: Encrypt Configuration Sections in ASP.NET 2.0 Using RSA](https://go.microsoft.com/fwlink/?LinkId=95138)).</span></span>  
  
## <a name="locking-configuration-file-elements"></a><span data-ttu-id="c5dbd-136">Zamykání souborů elementy konfigurace</span><span class="sxs-lookup"><span data-stu-id="c5dbd-136">Locking configuration file elements</span></span>  
 <span data-ttu-id="c5dbd-137">V hostované Web scénářích je možné mít služby v podadresářích služeb.</span><span class="sxs-lookup"><span data-stu-id="c5dbd-137">In Web-hosted scenarios, it is possible to have services in subdirectories of services.</span></span> <span data-ttu-id="c5dbd-138">V těchto situacích se počítají hodnoty konfigurace pro službu v podadresáři kontrolou hodnoty v souboru Machine.config a postupně se žádné soubory Web.config v nadřazené adresáře přesunutí dolů ve stromu adresáře a nakonec slučování sloučení Soubor Web.config v adresáře, který obsahuje službu.</span><span class="sxs-lookup"><span data-stu-id="c5dbd-138">In these situations, configuration values for the service in the subdirectory are calculated by examining values in Machine.config and successively merging with any Web.config files in parent directories moving down the directory tree and finally merging the Web.config file in the directory that contains the service.</span></span> <span data-ttu-id="c5dbd-139">Výchozí chování pro většinu prvků konfigurace je umožnit konfiguračních souborů v podadresářích přepisují hodnoty nastavené v nadřazené adresáře.</span><span class="sxs-lookup"><span data-stu-id="c5dbd-139">The default behavior for most configuration elements is to allow configuration files in subdirectories to override the values set in parent directories.</span></span> <span data-ttu-id="c5dbd-140">V některých situacích může být žádoucí konfiguračních souborů v podadresářích zabránit potlačení hodnot nastavených v konfiguraci nadřazené adresáře.</span><span class="sxs-lookup"><span data-stu-id="c5dbd-140">In certain situations it may be desirable to prevent configuration files in subdirectories from overriding values set in parent directory configuration.</span></span>  
  
 <span data-ttu-id="c5dbd-141">Rozhraní .NET Framework poskytuje způsob, jak uzamknout soubor elementů konfigurace tak, aby konfigurace, které přepíší elementy uzamčené konfigurace vyvolat výjimky za běhu.</span><span class="sxs-lookup"><span data-stu-id="c5dbd-141">The .NET Framework provides a way to lock configuration file elements so that configurations that override locked configuration elements throw run-time exceptions.</span></span>  
  
 <span data-ttu-id="c5dbd-142">Prvek konfigurace můžete uzamknout tak, že zadáte `lockItem` atribut pro uzel v konfiguračním souboru, například k uzamčení CalculatorServiceBehavior uzlu v konfiguračním souboru tak, aby Kalkulačka služby ve vnořené konfiguračních souborů nelze změnit chování následující konfigurace můžete použít.</span><span class="sxs-lookup"><span data-stu-id="c5dbd-142">A configuration element can be locked by specifying the `lockItem` attribute for a node in the configuration file, for example, to lock the CalculatorServiceBehavior node in the configuration file so that calculator services in nested configuration files cannot change the behavior, the following configuration can be used.</span></span>  
  
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
  
 <span data-ttu-id="c5dbd-143">Uzamčení elementů konfigurace může být konkrétnější.</span><span class="sxs-lookup"><span data-stu-id="c5dbd-143">Locking of configuration elements can be more specific.</span></span> <span data-ttu-id="c5dbd-144">Seznam prvků se dá nastavit jako hodnota, která má `lockElements` uzamknout sadu elementů v rámci kolekce podřízených elementů.</span><span class="sxs-lookup"><span data-stu-id="c5dbd-144">A list of elements can be specified as the value to the `lockElements` to lock a set of elements within a collection of sub-elements.</span></span> <span data-ttu-id="c5dbd-145">Seznam atributů lze zadat jako hodnota, která má `lockAttributes` uzamknout sadu atributů v rámci elementu.</span><span class="sxs-lookup"><span data-stu-id="c5dbd-145">A list of attributes can be specified as the value to the `lockAttributes` to lock a set of attributes within an element.</span></span> <span data-ttu-id="c5dbd-146">S výjimkou zadaného seznamu jde zamknout celou kolekci elementů nebo atributů tak, že zadáte `lockAllElementsExcept` nebo `lockAllAttributesExcept` atributy uzlu.</span><span class="sxs-lookup"><span data-stu-id="c5dbd-146">An entire collection of elements or attributes can be locked except for a specified list by specifying the `lockAllElementsExcept` or `lockAllAttributesExcept` attributes on a node.</span></span>  
  
## <a name="pii-logging-configuration"></a><span data-ttu-id="c5dbd-147">Konfigurace protokolování identifikovatelné osobní údaje</span><span class="sxs-lookup"><span data-stu-id="c5dbd-147">PII Logging Configuration</span></span>  
 <span data-ttu-id="c5dbd-148">Protokolování identifikovatelné osobní údaje se řídí dva přepínače: nastavení celý počítač se nenašel v souboru Machine.config, který umožňuje správci počítače můžete povolit nebo zakázat protokolování identifikovatelné osobní údaje a nastavení aplikace, která umožňuje správci aplikace přepnout protokolování identifikovatelné osobní údaje pro každou zdroj v souboru Web.config nebo App.config.</span><span class="sxs-lookup"><span data-stu-id="c5dbd-148">Logging of PII is controlled by two switches: a computer-wide setting found in Machine.config that allows a computer administrator to permit or deny logging of PII and an application setting that allows an application administrator to toggle logging of PII for each source in a Web.config or App.config file.</span></span>  
  
 <span data-ttu-id="c5dbd-149">Nastavení pro celý počítač je řízena nastavením `enableLoggingKnownPii` k `true` nebo `false`v `machineSettings` element v souboru Machine.config. Následující příklad umožňuje aplikacím zapnout protokolování identifikovatelné osobní údaje.</span><span class="sxs-lookup"><span data-stu-id="c5dbd-149">The computer-wide setting is controlled by setting `enableLoggingKnownPii` to `true` or `false`, in the `machineSettings` element in Machine.config. For example, the following allows applications to turn on logging of PII.</span></span>  
  
```xml  
<configuration>  
    <system.serviceModel>  
        <machineSettings enableLoggingKnownPii="true" />  
    </system.serviceModel>  
</configuration>  
```  
  
> [!NOTE]
>  <span data-ttu-id="c5dbd-150">Soubor Machine.config obsahuje výchozí umístění: % WINDIR%\Microsoft.NET\Framework\v2.0.50727\CONFIG.</span><span class="sxs-lookup"><span data-stu-id="c5dbd-150">The Machine.config file has a default location: %WINDIR%\Microsoft.NET\Framework\v2.0.50727\CONFIG.</span></span>  
  
 <span data-ttu-id="c5dbd-151">Pokud `enableLoggingKnownPii` atribut není k dispozici v souboru Machine.config, není povoleno protokolování identifikovatelné osobní údaje.</span><span class="sxs-lookup"><span data-stu-id="c5dbd-151">If the `enableLoggingKnownPii` attribute is not present in Machine.config, logging of PII is not allowed.</span></span>  
  
 <span data-ttu-id="c5dbd-152">Povolení protokolování identifikovatelné osobní údaje pro aplikaci se provádí tak, že nastavíte `logKnownPii` atribut zdrojového elementu na `true` nebo `false` v souboru Web.config nebo App.config.</span><span class="sxs-lookup"><span data-stu-id="c5dbd-152">Enabling logging of PII for an application is done by setting the `logKnownPii` attribute of the source element to `true` or `false` in the Web.config or App.config file.</span></span> <span data-ttu-id="c5dbd-153">Následující příklad umožňuje protokolování identifikovatelné osobní údaje pro protokolování trasování a protokolování zpráv.</span><span class="sxs-lookup"><span data-stu-id="c5dbd-153">For example, the following enables logging of PII for both message logging and trace logging.</span></span>  
  
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
  
 <span data-ttu-id="c5dbd-154">Pokud `logKnownPii` není zadán atribut, pak identifikovatelné osobní údaje se neprotokolují.</span><span class="sxs-lookup"><span data-stu-id="c5dbd-154">If the `logKnownPii` attribute is not specified, then PII is not logged.</span></span>  
  
 <span data-ttu-id="c5dbd-155">Identifikovatelné osobní údaje se jenom protokoluje, pokud mají oba `enableLoggingKnownPii` je nastavena na `true`, a `logKnownPii` je nastavena na `true`.</span><span class="sxs-lookup"><span data-stu-id="c5dbd-155">PII is only logged if both `enableLoggingKnownPii` is set to `true`, and `logKnownPii` is set to `true`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c5dbd-156">System.Diagnostics ignoruje všechny atributy pro všechny zdroje s výjimkou první z nich uvedená v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="c5dbd-156">System.Diagnostics ignores all attributes on all sources except the first one listed in the configuration file.</span></span> <span data-ttu-id="c5dbd-157">Přidávání `logKnownPii` atribut do druhého zdroje v konfiguračním souboru nemá žádný vliv.</span><span class="sxs-lookup"><span data-stu-id="c5dbd-157">Adding the `logKnownPii` attribute to the second source in the configuration file has no effect.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="c5dbd-158">Chcete-li spustit tento příklad zahrnuje ruční úpravy souboru Machine.config. Při úpravě souboru Machine.config jako nesprávné hodnoty nebo syntaxe může zabránit spouštění všech aplikací rozhraní .NET Framework by měl být věnovat pozornost.</span><span class="sxs-lookup"><span data-stu-id="c5dbd-158">To run this sample involves manual modification of Machine.config. Care should be taken when modifying Machine.config as incorrect values or syntax may prevent all .NET Framework applications from running.</span></span>  
  
 <span data-ttu-id="c5dbd-159">Je také možné šifrovat konfigurační prvky souboru pomocí DPAPI a RSA.</span><span class="sxs-lookup"><span data-stu-id="c5dbd-159">It is also possible to encrypt configuration file elements using DPAPI and RSA.</span></span> <span data-ttu-id="c5dbd-160">Další informace najdete v následujících tématech:</span><span class="sxs-lookup"><span data-stu-id="c5dbd-160">For more information, see the following links:</span></span>  
  
-   [<span data-ttu-id="c5dbd-161">Vytváření aplikací ASP.NET zabezpečené: Ověřování, autorizaci a zabezpečenou komunikaci</span><span class="sxs-lookup"><span data-stu-id="c5dbd-161">Building Secure ASP.NET Applications: Authentication, Authorization, and Secure Communication</span></span>](https://go.microsoft.com/fwlink/?LinkId=95137)  
  
-   [<span data-ttu-id="c5dbd-162">Postupy: Šifrování konfigurační oddíly funkce v technologii ASP.NET 2.0 pomocí technologie RSA</span><span class="sxs-lookup"><span data-stu-id="c5dbd-162">How To: Encrypt Configuration Sections in ASP.NET 2.0 Using RSA</span></span>](https://go.microsoft.com/fwlink/?LinkId=95138)  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="c5dbd-163">Chcete-li nastavit, sestavte a spusťte ukázku</span><span class="sxs-lookup"><span data-stu-id="c5dbd-163">To set up, build and run the sample</span></span>  
  
1.  <span data-ttu-id="c5dbd-164">Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c5dbd-164">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="c5dbd-165">Upravit soubor Machine.config nastavit `enableLoggingKnownPii` atribut `true`, v případě potřeby přidává uzly nadřazených objektů.</span><span class="sxs-lookup"><span data-stu-id="c5dbd-165">Edit Machine.config to set the `enableLoggingKnownPii` attribute to `true`, adding the parent nodes if necessary.</span></span>  
  
3.  <span data-ttu-id="c5dbd-166">K sestavení edice řešení C# nebo Visual Basic .NET, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c5dbd-166">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4.  <span data-ttu-id="c5dbd-167">Spusťte ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v [spouštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c5dbd-167">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
#### <a name="to-clean-up-the-sample"></a><span data-ttu-id="c5dbd-168">Vyčistit vzorku</span><span class="sxs-lookup"><span data-stu-id="c5dbd-168">To clean up the sample</span></span>  
  
1.  <span data-ttu-id="c5dbd-169">Upravit soubor Machine.config nastavit `enableLoggingKnownPii` atribut `false`.</span><span class="sxs-lookup"><span data-stu-id="c5dbd-169">Edit Machine.config to set the `enableLoggingKnownPii` attribute to `false`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5dbd-170">Viz také</span><span class="sxs-lookup"><span data-stu-id="c5dbd-170">See Also</span></span>  
 [<span data-ttu-id="c5dbd-171">Ukázky AppFabric monitorování</span><span class="sxs-lookup"><span data-stu-id="c5dbd-171">AppFabric Monitoring Samples</span></span>](https://go.microsoft.com/fwlink/?LinkId=193959)
