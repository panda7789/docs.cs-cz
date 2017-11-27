---
title: "Bezpečnostní uzamčení PII"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c44fb338-9527-4dd0-8607-b8787d15acb4
caps.latest.revision: "25"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 93849fc315409b769a06cdd216bbc86e83cf6155
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="pii-security-lockdown"></a><span data-ttu-id="05fd1-102">Bezpečnostní uzamčení PII</span><span class="sxs-lookup"><span data-stu-id="05fd1-102">PII Security Lockdown</span></span>
<span data-ttu-id="05fd1-103">Tento příklad ukazuje, jak řídit některé funkce související se zabezpečením služby [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] služby podle:</span><span class="sxs-lookup"><span data-stu-id="05fd1-103">This sample demonstrates how to control several security-related features of a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] service by:</span></span>  
  
-   <span data-ttu-id="05fd1-104">Šifrování citlivých informací v konfiguračním souboru služby.</span><span class="sxs-lookup"><span data-stu-id="05fd1-104">Encrypting sensitive information in a service's configuration file.</span></span>  
  
-   <span data-ttu-id="05fd1-105">Zamykání elementy v konfiguračním souboru tak, aby vnořené podadresářů služby nejde přepsat nastavení.</span><span class="sxs-lookup"><span data-stu-id="05fd1-105">Locking elements in the configuration file so that nested service subdirectories cannot override settings.</span></span>  
  
-   <span data-ttu-id="05fd1-106">Řízení protokolování z identifikovatelné osobní informace (PII) v protokolech trasování a zprávy.</span><span class="sxs-lookup"><span data-stu-id="05fd1-106">Controlling the logging of Personally Identifiable Information (PII) in trace and message logs.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="05fd1-107">Ukázky může být již nainstalován ve vašem počítači.</span><span class="sxs-lookup"><span data-stu-id="05fd1-107">The samples may already be installed on your computer.</span></span> <span data-ttu-id="05fd1-108">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="05fd1-108">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="05fd1-109">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="05fd1-109">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="05fd1-110">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="05fd1-110">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\SecurityLockdown`  
  
## <a name="discussion"></a><span data-ttu-id="05fd1-111">Diskusní</span><span class="sxs-lookup"><span data-stu-id="05fd1-111">Discussion</span></span>  
 <span data-ttu-id="05fd1-112">Každý z těchto funkcí může být používat samostatně nebo společně k řízení aspektů zabezpečení služby.</span><span class="sxs-lookup"><span data-stu-id="05fd1-112">Each of these features can be used separately or together to control aspects of a service's security.</span></span> <span data-ttu-id="05fd1-113">Nejedná se o základní příručka k zabezpečení [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby.</span><span class="sxs-lookup"><span data-stu-id="05fd1-113">This is not a definitive guide to securing a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service.</span></span>  
  
 <span data-ttu-id="05fd1-114">Rozhraní .NET Framework konfigurační soubory, které mohou obsahovat citlivé údaje, jako je například připojovací řetězce pro připojení k databázím.</span><span class="sxs-lookup"><span data-stu-id="05fd1-114">The .NET Framework configuration files can contain sensitive information such as connection strings to connect to databases.</span></span> <span data-ttu-id="05fd1-115">Ve scénářích sdílené, hostovat webové může být žádoucí k zašifrování těchto informací v konfiguračním souboru pro službu, aby byla data obsažená v konfiguračním souboru odolné vůči běžné zobrazení.</span><span class="sxs-lookup"><span data-stu-id="05fd1-115">In shared, Web-hosted scenarios it may be desirable to encrypt this information in the configuration file for a service so that the data contained within the configuration file is resistant to casual viewing.</span></span> <span data-ttu-id="05fd1-116">.NET framework 2.0 nebo novější má možnost šifrování části konfiguračního souboru pomocí aplikace Windows Data Protection programovací rozhraní (DPAPI), nebo zprostředkovatele šifrování RSA.</span><span class="sxs-lookup"><span data-stu-id="05fd1-116">.NET Framework 2.0 and later has the ability to encrypt portions of the configuration file using the Windows Data Protection application programming interface (DPAPI) or the RSA Cryptographic provider.</span></span> <span data-ttu-id="05fd1-117">Aspnet_regiis.exe pomocí rozhraní DPAPI nebo RSA můžete šifrovat vyberte části konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="05fd1-117">The aspnet_regiis.exe using the DPAPI or RSA can encrypt select portions of a configuration file.</span></span>  
  
 <span data-ttu-id="05fd1-118">Ve scénářích hostované webové je možné, že služby v podadresářích adresáře dalších služeb.</span><span class="sxs-lookup"><span data-stu-id="05fd1-118">In Web-hosted scenarios it is possible to have services in subdirectories of other services.</span></span> <span data-ttu-id="05fd1-119">Výchozí hodnota pro určení hodnoty konfigurace sémantického umožňuje konfigurační soubory v adresáři vnořené přepsat hodnoty konfigurace v nadřazeném adresáři.</span><span class="sxs-lookup"><span data-stu-id="05fd1-119">The default semantic for determining configuration values allows configuration files in the nested directories to override the configuration values in the parent directory.</span></span> <span data-ttu-id="05fd1-120">V některých situacích může být žádoucí z různých důvodů.</span><span class="sxs-lookup"><span data-stu-id="05fd1-120">In certain situations this may be undesirable for a variety of reasons.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="05fd1-121">podporuje konfigurace služby uzamykání hodnoty konfigurace tak, aby vnořené konfigurace generuje výjimky při spuštění vnořené služby pomocí přepsat hodnoty konfigurace.</span><span class="sxs-lookup"><span data-stu-id="05fd1-121"> service configuration supports the locking of configuration values so that nested configuration generates exceptions when a nested service is run using overridden configuration values.</span></span>  
  
 <span data-ttu-id="05fd1-122">Tento příklad znázorňuje postup řízení protokolování z známé identifikovatelné osobní informace (PII) v protokolech trasování a zprávy, jako je například uživatelské jméno a heslo.</span><span class="sxs-lookup"><span data-stu-id="05fd1-122">This sample demonstrates how to control the logging of known Personally Identifiable Information (PII) in trace and message logs, such as username and password.</span></span> <span data-ttu-id="05fd1-123">Ve výchozím nastavení protokolování známé PII je zakázáno, ale v některých situacích může být důležité při ladění aplikace protokolování PII.</span><span class="sxs-lookup"><span data-stu-id="05fd1-123">By default, logging of known PII is disabled however in certain situations logging of PII can be important in debugging an application.</span></span> <span data-ttu-id="05fd1-124">Tato ukázka je založena na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="05fd1-124">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span> <span data-ttu-id="05fd1-125">Kromě toho tato ukázka používá trasování a protokolování zpráv.</span><span class="sxs-lookup"><span data-stu-id="05fd1-125">In addition, this sample uses tracing and message logging.</span></span> <span data-ttu-id="05fd1-126">Další informace najdete v tématu [trasování a protokolování zpráv](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md) ukázka.</span><span class="sxs-lookup"><span data-stu-id="05fd1-126">For more information, see the [Tracing and Message Logging](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md) sample.</span></span>  
  
## <a name="encrypting-configuration-file-elements"></a><span data-ttu-id="05fd1-127">Šifrování souboru konfigurace – elementy</span><span class="sxs-lookup"><span data-stu-id="05fd1-127">Encrypting Configuration File Elements</span></span>  
 <span data-ttu-id="05fd1-128">Z bezpečnostních důvodů v prostředí sdílené hostování webů může být žádoucí k šifrování určitých konfigurační prvky, jako je například databázové připojovací řetězce, které mohou obsahovat citlivé informace.</span><span class="sxs-lookup"><span data-stu-id="05fd1-128">For security purposes in a shared Web-hosting environment, it may be desirable to encrypt certain configuration elements, such as database connection strings that may contain sensitive information.</span></span> <span data-ttu-id="05fd1-129">Element konfigurace může šifrované pomocí nástroje aspnet_regiis.exe nachází ve složce % například WINDIR%\Micrsoft.NET\Framework\v4.0.20728 rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="05fd1-129">A configuration element may be encrypted using the aspnet_regiis.exe tool found in the .NET Framework folder For example, %WINDIR%\Micrsoft.NET\Framework\v4.0.20728.</span></span>  
  
#### <a name="to-encrypt-the-values-in-the-appsettings-section-in-webconfig-for-the-sample"></a><span data-ttu-id="05fd1-130">K šifrování hodnoty v oddílu appSettings v souboru Web.config pro ukázku</span><span class="sxs-lookup"><span data-stu-id="05fd1-130">To encrypt the values in the appSettings section in Web.config for the sample</span></span>  
  
1.  <span data-ttu-id="05fd1-131">Otevřete příkazový řádek pomocí Start -> spustit...</span><span class="sxs-lookup"><span data-stu-id="05fd1-131">Open a command prompt by using Start->Run….</span></span> <span data-ttu-id="05fd1-132">Zadejte `cmd` a klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="05fd1-132">Type in `cmd` and click **OK**.</span></span>  
  
2.  <span data-ttu-id="05fd1-133">Přejděte k aktuálnímu adresáři rozhraní .NET Framework po vydání následujícího příkazu: `cd %WINDIR%\Microsoft.NET\Framework\v4.0.20728`.</span><span class="sxs-lookup"><span data-stu-id="05fd1-133">Navigate to the current .NET Framework directory by issuing the following command: `cd %WINDIR%\Microsoft.NET\Framework\v4.0.20728`.</span></span>  
  
3.  <span data-ttu-id="05fd1-134">Šifrování appSettings nastavení konfigurace ve složce Web.config po vydání následujícího příkazu: `aspnet_regiis -pe "appSettings" -app "/servicemodelsamples" -prov "DataProtectionConfigurationProvider"`.</span><span class="sxs-lookup"><span data-stu-id="05fd1-134">Encrypt the appSettings configuration settings in the Web.config folder by issuing the following command: `aspnet_regiis -pe "appSettings" -app "/servicemodelsamples" -prov "DataProtectionConfigurationProvider"`.</span></span>  
  
 <span data-ttu-id="05fd1-135">Naleznete další informace o šifrování oddílů konfigurační soubory načtením postupy na rozhraní DPAPI v konfiguraci ASP.NET ([vytváření zabezpečení aplikací ASP.NET: ověřování, autorizace a zabezpečená komunikace](http://go.microsoft.com/fwlink/?LinkId=95137)) a postupy v RSA v konfiguraci ASP.NET ([postupy: šifrování konfigurační oddíly funkce v technologii ASP.NET 2.0 pomocí RSA](http://go.microsoft.com/fwlink/?LinkId=95138)).</span><span class="sxs-lookup"><span data-stu-id="05fd1-135">More information about encrypting sections of configuration files can be found by reading a how-to on DPAPI in ASP.NET configuration ([Building Secure ASP.NET Applications: Authentication, Authorization, and Secure Communication](http://go.microsoft.com/fwlink/?LinkId=95137)) and a how-to on RSA in ASP.NET configuration ([How To: Encrypt Configuration Sections in ASP.NET 2.0 Using RSA](http://go.microsoft.com/fwlink/?LinkId=95138)).</span></span>  
  
## <a name="locking-configuration-file-elements"></a><span data-ttu-id="05fd1-136">Zamykání souborů konfigurace – elementy</span><span class="sxs-lookup"><span data-stu-id="05fd1-136">Locking configuration file elements</span></span>  
 <span data-ttu-id="05fd1-137">Ve scénářích hostuje Web je možné, že služby v podadresářích adresáře služby.</span><span class="sxs-lookup"><span data-stu-id="05fd1-137">In Web-hosted scenarios, it is possible to have services in subdirectories of services.</span></span> <span data-ttu-id="05fd1-138">V těchto situacích se určí hodnoty konfigurace pro službu v podadresáři zkoumání hodnoty v souboru Machine.config a postupně sloučení se všechny soubory Web.config nadřazeného adresáře přesunutí dolů ve stromu adresáře a nakonec slučování Soubor Web.config v adresáři, který obsahuje službu.</span><span class="sxs-lookup"><span data-stu-id="05fd1-138">In these situations, configuration values for the service in the subdirectory are calculated by examining values in Machine.config and successively merging with any Web.config files in parent directories moving down the directory tree and finally merging the Web.config file in the directory that contains the service.</span></span> <span data-ttu-id="05fd1-139">Výchozí chování pro většinu prvků konfigurace je umožnit konfigurační soubory nacházejí v podadresářích adresáře přepsat s hodnotami nastavenými v nadřazeného adresáře.</span><span class="sxs-lookup"><span data-stu-id="05fd1-139">The default behavior for most configuration elements is to allow configuration files in subdirectories to override the values set in parent directories.</span></span> <span data-ttu-id="05fd1-140">V některých situacích může být žádoucí, abyste zabránili přepsání hodnotami nastavenými v nadřazené konfiguraci adresáře konfigurační soubory nacházejí v podadresářích adresáře.</span><span class="sxs-lookup"><span data-stu-id="05fd1-140">In certain situations it may be desirable to prevent configuration files in subdirectories from overriding values set in parent directory configuration.</span></span>  
  
 <span data-ttu-id="05fd1-141">Rozhraní .NET Framework poskytuje způsob, jak uzamknout konfigurační soubor prvky tak, aby konfigurace, které potlačí uzamčeném konfigurace – elementy throw výjimky v době běhu.</span><span class="sxs-lookup"><span data-stu-id="05fd1-141">The .NET Framework provides a way to lock configuration file elements so that configurations that override locked configuration elements throw run-time exceptions.</span></span>  
  
 <span data-ttu-id="05fd1-142">Zadáním jde Zamknout prvek konfigurace `lockItem` atribut pro uzel v konfiguračním souboru, například k uzamčení uzlu CalculatorServiceBehavior v konfiguračním souboru tak, aby kalkulačky služeb ve vnořených konfigurační soubory nelze změnit chování, následující konfigurace můžete použít.</span><span class="sxs-lookup"><span data-stu-id="05fd1-142">A configuration element can be locked by specifying the `lockItem` attribute for a node in the configuration file, for example, to lock the CalculatorServiceBehavior node in the configuration file so that calculator services in nested configuration files cannot change the behavior, the following configuration can be used.</span></span>  
  
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
  
 <span data-ttu-id="05fd1-143">Uzamykání konfigurace – elementy může být konkrétnější.</span><span class="sxs-lookup"><span data-stu-id="05fd1-143">Locking of configuration elements can be more specific.</span></span> <span data-ttu-id="05fd1-144">Seznam prvků lze zadat jako hodnotu `lockElements` k uzamčení sadu elementů v kolekci podřízených elementů.</span><span class="sxs-lookup"><span data-stu-id="05fd1-144">A list of elements can be specified as the value to the `lockElements` to lock a set of elements within a collection of sub-elements.</span></span> <span data-ttu-id="05fd1-145">Seznam atributů lze zadat jako hodnotu `lockAttributes` k uzamčení sadu atributů v rámci elementu.</span><span class="sxs-lookup"><span data-stu-id="05fd1-145">A list of attributes can be specified as the value to the `lockAttributes` to lock a set of attributes within an element.</span></span> <span data-ttu-id="05fd1-146">Celou kolekci elementy nebo atributy jde Zamknout s výjimkou zadaného seznamu tak, že zadáte `lockAllElementsExcept` nebo `lockAllAttributesExcept` atributy na uzlu.</span><span class="sxs-lookup"><span data-stu-id="05fd1-146">An entire collection of elements or attributes can be locked except for a specified list by specifying the `lockAllElementsExcept` or `lockAllAttributesExcept` attributes on a node.</span></span>  
  
## <a name="pii-logging-configuration"></a><span data-ttu-id="05fd1-147">Konfigurace protokolování PII</span><span class="sxs-lookup"><span data-stu-id="05fd1-147">PII Logging Configuration</span></span>  
 <span data-ttu-id="05fd1-148">Protokolování PII řídí dva přepínače: v souboru Machine.config, který umožňuje správci počítače můžete povolit nebo zakázat protokolování PII a nastavení aplikace, které umožňuje Správce aplikací k přepnutí protokolování PII pro každou najít nastavení platná pro celý počítač zdroj v souboru Web.config nebo App.config.</span><span class="sxs-lookup"><span data-stu-id="05fd1-148">Logging of PII is controlled by two switches: a computer-wide setting found in Machine.config that allows a computer administrator to permit or deny logging of PII and an application setting that allows an application administrator to toggle logging of PII for each source in a Web.config or App.config file.</span></span>  
  
 <span data-ttu-id="05fd1-149">Nastavení platná pro celý počítač je řízena nastavením `enableLoggingKnownPii` k `true` nebo `false`v `machineSettings` element v souboru Machine.config. Následující například umožňuje aplikacím zapnout protokolování PII.</span><span class="sxs-lookup"><span data-stu-id="05fd1-149">The computer-wide setting is controlled by setting `enableLoggingKnownPii` to `true` or `false`, in the `machineSettings` element in Machine.config. For example, the following allows applications to turn on logging of PII.</span></span>  
  
```xml  
<configuration>  
    <system.serviceModel>  
        <machineSettings enableLoggingKnownPii="true" />  
    </system.serviceModel>  
</configuration>  
```  
  
> [!NOTE]
>  <span data-ttu-id="05fd1-150">Souboru Machine.config má výchozí umístění: % WINDIR%\Microsoft.NET\Framework\v2.0.50727\CONFIG.</span><span class="sxs-lookup"><span data-stu-id="05fd1-150">The Machine.config file has a default location: %WINDIR%\Microsoft.NET\Framework\v2.0.50727\CONFIG.</span></span>  
  
 <span data-ttu-id="05fd1-151">Pokud `enableLoggingKnownPii` atribut není k dispozici v souboru Machine.config, není povoleno protokolování PII.</span><span class="sxs-lookup"><span data-stu-id="05fd1-151">If the `enableLoggingKnownPii` attribute is not present in Machine.config, logging of PII is not allowed.</span></span>  
  
 <span data-ttu-id="05fd1-152">Povolení protokolování PII pro aplikace se provádí nastavením `logKnownPii` atribut elementu zdroj `true` nebo `false` v souboru Web.config nebo App.config.</span><span class="sxs-lookup"><span data-stu-id="05fd1-152">Enabling logging of PII for an application is done by setting the `logKnownPii` attribute of the source element to `true` or `false` in the Web.config or App.config file.</span></span> <span data-ttu-id="05fd1-153">Následující příklad umožňuje protokolování PII pro protokolování zpráv a protokolování trasování.</span><span class="sxs-lookup"><span data-stu-id="05fd1-153">For example, the following enables logging of PII for both message logging and trace logging.</span></span>  
  
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
  
 <span data-ttu-id="05fd1-154">Pokud `logKnownPii` atribut nezadá, pak se neprotokolují PII.</span><span class="sxs-lookup"><span data-stu-id="05fd1-154">If the `logKnownPii` attribute is not specified, then PII is not logged.</span></span>  
  
 <span data-ttu-id="05fd1-155">PII se zaznamená pouze, pokud obě `enableLoggingKnownPii` je nastaven na `true`, a `logKnownPii` je nastaven na `true`.</span><span class="sxs-lookup"><span data-stu-id="05fd1-155">PII is only logged if both `enableLoggingKnownPii` is set to `true`, and `logKnownPii` is set to `true`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="05fd1-156">System.Diagnostics ignoruje všechny atributy pro všechny zdroje kromě první uveden v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="05fd1-156">System.Diagnostics ignores all attributes on all sources except the first one listed in the configuration file.</span></span> <span data-ttu-id="05fd1-157">Přidávání `logKnownPii` atribut ke zdroji druhý v konfiguračním souboru nemá žádný vliv.</span><span class="sxs-lookup"><span data-stu-id="05fd1-157">Adding the `logKnownPii` attribute to the second source in the configuration file has no effect.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="05fd1-158">Chcete tuto ukázku spustit zahrnuje ruční úpravy souboru Machine.config. Potřeba dát pozor při úpravách souboru Machine.config tvoří nesprávné hodnoty nebo syntaxe může zabránit spouštění všech aplikací rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="05fd1-158">To run this sample involves manual modification of Machine.config. Care should be taken when modifying Machine.config as incorrect values or syntax may prevent all .NET Framework applications from running.</span></span>  
  
 <span data-ttu-id="05fd1-159">Také je možné zašifrovat soubor konfigurace – elementy pomocí rozhraní DPAPI a RSA.</span><span class="sxs-lookup"><span data-stu-id="05fd1-159">It is also possible to encrypt configuration file elements using DPAPI and RSA.</span></span> <span data-ttu-id="05fd1-160">Další informace najdete v následujících tématech:</span><span class="sxs-lookup"><span data-stu-id="05fd1-160">For more information, see the following links:</span></span>  
  
-   [<span data-ttu-id="05fd1-161">Vytváření aplikací ASP.NET zabezpečení: Ověřování, autorizace a zabezpečenou komunikaci</span><span class="sxs-lookup"><span data-stu-id="05fd1-161">Building Secure ASP.NET Applications: Authentication, Authorization, and Secure Communication</span></span>](http://go.microsoft.com/fwlink/?LinkId=95137)  
  
-   [<span data-ttu-id="05fd1-162">Postupy: Šifrování konfigurační oddíly funkce v technologii ASP.NET 2.0 pomocí RSA</span><span class="sxs-lookup"><span data-stu-id="05fd1-162">How To: Encrypt Configuration Sections in ASP.NET 2.0 Using RSA</span></span>](http://go.microsoft.com/fwlink/?LinkId=95138)  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="05fd1-163">Pokud chcete nastavit, sestavit a spustit ukázku</span><span class="sxs-lookup"><span data-stu-id="05fd1-163">To set up, build and run the sample</span></span>  
  
1.  <span data-ttu-id="05fd1-164">Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="05fd1-164">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="05fd1-165">Upravit Machine.config nastavit `enableLoggingKnownPii` atribut `true`, přidání nadřazených uzlů v případě potřeby.</span><span class="sxs-lookup"><span data-stu-id="05fd1-165">Edit Machine.config to set the `enableLoggingKnownPii` attribute to `true`, adding the parent nodes if necessary.</span></span>  
  
3.  <span data-ttu-id="05fd1-166">Sestavení C# nebo Visual Basic .NET edice řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="05fd1-166">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4.  <span data-ttu-id="05fd1-167">Spustit ukázku v konfiguraci s jednou nebo mezi počítači, postupujte podle pokynů v [spuštění ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="05fd1-167">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
#### <a name="to-clean-up-the-sample"></a><span data-ttu-id="05fd1-168">Vyčistěte vzorku</span><span class="sxs-lookup"><span data-stu-id="05fd1-168">To clean up the sample</span></span>  
  
1.  <span data-ttu-id="05fd1-169">Upravit Machine.config nastavit `enableLoggingKnownPii` atribut `false`.</span><span class="sxs-lookup"><span data-stu-id="05fd1-169">Edit Machine.config to set the `enableLoggingKnownPii` attribute to `false`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05fd1-170">Viz také</span><span class="sxs-lookup"><span data-stu-id="05fd1-170">See Also</span></span>  
 [<span data-ttu-id="05fd1-171">Ukázky monitorování AppFabric</span><span class="sxs-lookup"><span data-stu-id="05fd1-171">AppFabric Monitoring Samples</span></span>](http://go.microsoft.com/fwlink/?LinkId=193959)
