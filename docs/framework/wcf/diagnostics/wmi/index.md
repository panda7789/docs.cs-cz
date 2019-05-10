---
title: Diagnostika prostřednictvím rozhraní WMI (Windows Management Instrumentation)
ms.date: 03/30/2017
ms.assetid: fe48738d-e31b-454d-b5ec-24c85c6bf79a
ms.openlocfilehash: 47aece36368be12a2a63283367e95dcaa64ef484
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64662471"
---
# <a name="using-windows-management-instrumentation-for-diagnostics"></a><span data-ttu-id="88ee9-102">Diagnostika prostřednictvím rozhraní WMI (Windows Management Instrumentation)</span><span class="sxs-lookup"><span data-stu-id="88ee9-102">Using Windows Management Instrumentation for Diagnostics</span></span>
<span data-ttu-id="88ee9-103">Windows Communication Foundation (WCF) poskytuje dat kontroly služby za běhu pomocí zprostředkovatele WCF Windows Management Instrumentation (WMI).</span><span class="sxs-lookup"><span data-stu-id="88ee9-103">Windows Communication Foundation (WCF) exposes inspection data of a service at runtime through a WCF Windows Management Instrumentation (WMI) provider.</span></span>  
  
## <a name="enabling-wmi"></a><span data-ttu-id="88ee9-104">Povolení rozhraní WMI</span><span class="sxs-lookup"><span data-stu-id="88ee9-104">Enabling WMI</span></span>  
 <span data-ttu-id="88ee9-105">Rozhraní WMI se výlučně implementace Microsoftu Web-Based Enterprise Management (WBEM) standard.</span><span class="sxs-lookup"><span data-stu-id="88ee9-105">WMI is Microsoft's implementation of the Web-Based Enterprise Management (WBEM) standard.</span></span> <span data-ttu-id="88ee9-106">Další informace o sadě SDK rozhraní WMI najdete v tématu [Windows Management Instrumentation](/windows/desktop/WmiSdk/wmi-start-page).</span><span class="sxs-lookup"><span data-stu-id="88ee9-106">For more information about the WMI SDK, see [Windows Management Instrumentation](/windows/desktop/WmiSdk/wmi-start-page).</span></span> <span data-ttu-id="88ee9-107">WBEM je oborový standard pro aplikace jak vystavit WMI pro externí nástroje pro správu.</span><span class="sxs-lookup"><span data-stu-id="88ee9-107">WBEM is an industry standard for how applications expose management instrumentation to external management tools.</span></span>  
  
 <span data-ttu-id="88ee9-108">Zprostředkovatel rozhraní WMI je komponenta, která zveřejňuje instrumentace za běhu pomocí rozhraní WBEM kompatibilní.</span><span class="sxs-lookup"><span data-stu-id="88ee9-108">A WMI provider is a component that exposes instrumentation at runtime through a WBEM-compatible interface.</span></span> <span data-ttu-id="88ee9-109">Zahrnuje sadu objektů WMI, které mají páry atribut hodnota.</span><span class="sxs-lookup"><span data-stu-id="88ee9-109">It consists of a set of WMI objects that have attribute/value pairs.</span></span> <span data-ttu-id="88ee9-110">Páry může být několik jednoduchých typů.</span><span class="sxs-lookup"><span data-stu-id="88ee9-110">Pairs can be of a number of simple types.</span></span> <span data-ttu-id="88ee9-111">Nástroje pro správu můžou připojit ke službám prostřednictvím rozhraní za běhu.</span><span class="sxs-lookup"><span data-stu-id="88ee9-111">Management tools can connect to the services through the interface at runtime.</span></span> <span data-ttu-id="88ee9-112">WCF zpřístupňuje atributy služeb, jako jsou adresy, vazby, chování a naslouchací procesy.</span><span class="sxs-lookup"><span data-stu-id="88ee9-112">WCF exposes attributes of services such as addresses, bindings, behaviors, and listeners.</span></span>  
  
 <span data-ttu-id="88ee9-113">Předdefinovaný poskytovatel rozhraní WMI je aktivovat v konfiguračním souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="88ee9-113">The built-in WMI provider can be activated in the configuration file of the application.</span></span> <span data-ttu-id="88ee9-114">To se provádí prostřednictvím `wmiProviderEnabled` atribut [ \<diagnostiky >](../../../../../docs/framework/configure-apps/file-schema/wcf/diagnostics.md) v [ \<system.serviceModel >](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) části, jak je znázorněno v následující ukázce konfigurace.</span><span class="sxs-lookup"><span data-stu-id="88ee9-114">This is done through the `wmiProviderEnabled` attribute of the [\<diagnostics>](../../../../../docs/framework/configure-apps/file-schema/wcf/diagnostics.md) in the [\<system.serviceModel>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) section, as shown in the following sample configuration.</span></span>  
  
```xml  
<system.serviceModel>  
    …  
    <diagnostics wmiProviderEnabled="true" />  
    …  
</system.serviceModel>  
```  
  
 <span data-ttu-id="88ee9-115">Tato položka konfigurace vystavuje rozhraní WMI.</span><span class="sxs-lookup"><span data-stu-id="88ee9-115">This configuration entry exposes a WMI interface.</span></span> <span data-ttu-id="88ee9-116">Správa aplikací teď můžete připojit přes toto rozhraní a přístup WMI aplikace.</span><span class="sxs-lookup"><span data-stu-id="88ee9-116">Management applications can now connect through this interface and access the management instrumentation of the application.</span></span>  
  
## <a name="accessing-wmi-data"></a><span data-ttu-id="88ee9-117">Přístup k datům služby WMI</span><span class="sxs-lookup"><span data-stu-id="88ee9-117">Accessing WMI Data</span></span>  
 <span data-ttu-id="88ee9-118">Data rozhraní WMI je možný v mnoha různými způsoby.</span><span class="sxs-lookup"><span data-stu-id="88ee9-118">WMI data can be accessed in many different ways.</span></span> <span data-ttu-id="88ee9-119">Společnost Microsoft poskytuje rozhraní API služby WMI pro skripty, Visual Basic aplikací, aplikací v jazyce C++ a [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="88ee9-119">Microsoft provides WMI APIs for scripts, Visual Basic applications, C++ applications, and the [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)].</span></span> <span data-ttu-id="88ee9-120">Další informace najdete v tématu [pomocí rozhraní WMI](https://go.microsoft.com/fwlink/?LinkId=95183).</span><span class="sxs-lookup"><span data-stu-id="88ee9-120">For more information, see [Using WMI](https://go.microsoft.com/fwlink/?LinkId=95183).</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="88ee9-121">Pokud používáte rozhraní .NET Framework poskytuje metody k programovému přístupu ke službě data rozhraní WMI, byste měli vědět, že tyto metody může vyvolat výjimky, když se připojení.</span><span class="sxs-lookup"><span data-stu-id="88ee9-121">If you use the .NET Framework provided methods to programmatically access WMI data, you should be aware that such methods may throw exceptions when the connection is established.</span></span> <span data-ttu-id="88ee9-122">Během procesu vytváření nebude navázáno připojení <xref:System.Management.ManagementObject> instance, ale na první žádost o zahrnující skutečná data systému exchange.</span><span class="sxs-lookup"><span data-stu-id="88ee9-122">The connection is not established during the construction of the <xref:System.Management.ManagementObject> instance, but on the first request involving actual data exchange.</span></span> <span data-ttu-id="88ee9-123">Proto byste měli použít `try..catch` blok catch výjimky.</span><span class="sxs-lookup"><span data-stu-id="88ee9-123">Therefore, you should use a `try..catch` block to catch the possible exceptions.</span></span>  
  
 <span data-ttu-id="88ee9-124">Můžete změnit trasování a úroveň protokolování zprávy, stejně jako možnosti protokolování zpráv `System.ServiceModel` zdroj trasování v rozhraní WMI.</span><span class="sxs-lookup"><span data-stu-id="88ee9-124">You can change the trace and message logging level, as well as message logging options for the `System.ServiceModel` trace source in WMI.</span></span> <span data-ttu-id="88ee9-125">To můžete udělat přechodem k [AppDomainInfo](../../../../../docs/framework/wcf/diagnostics/wmi/appdomaininfo.md) instanci, která poskytuje tyto logické vlastnosti: `LogMessagesAtServiceLevel`, `LogMessagesAtTransportLevel`, `LogMalformedMessages`, a `TraceLevel`.</span><span class="sxs-lookup"><span data-stu-id="88ee9-125">This can be done by accessing the [AppDomainInfo](../../../../../docs/framework/wcf/diagnostics/wmi/appdomaininfo.md) instance, which exposes these Boolean properties: `LogMessagesAtServiceLevel`, `LogMessagesAtTransportLevel`, `LogMalformedMessages`, and `TraceLevel`.</span></span> <span data-ttu-id="88ee9-126">Proto pokud nakonfigurovat naslouchací proces trasování pro protokolování zpráv, ale nastavit tyto možnosti na `false` v konfiguraci, můžete později změnit jejich `true` při spouštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="88ee9-126">Therefore, if you configure a trace listener for message logging, but set these options to `false` in configuration, you can later change them to `true` when the application is running.</span></span> <span data-ttu-id="88ee9-127">To vám umožní efektivní protokolování zpráv za běhu.</span><span class="sxs-lookup"><span data-stu-id="88ee9-127">This will effectively enable message logging at runtime.</span></span> <span data-ttu-id="88ee9-128">Podobně pokud povolíte protokolování. v konfiguračním souboru, můžete ho zakázat za běhu pomocí rozhraní WMI.</span><span class="sxs-lookup"><span data-stu-id="88ee9-128">Similarly, if you enable message logging in your configuration file, you can disable it at runtime using WMI.</span></span>  
  
 <span data-ttu-id="88ee9-129">Je třeba si uvědomit, že pokud žádné protokolování zpráv trasování naslouchacích procesů pro protokolování zpráv nebo Ne `System.ServiceModel` naslouchacích procesů trasování pro trasování jsou uvedeny v konfiguračním souboru, žádná z vašich změn provedených platit, i když jsou změny přijaty rozhraní WMI.</span><span class="sxs-lookup"><span data-stu-id="88ee9-129">You should be aware that if no message logging trace listeners for message logging, or no `System.ServiceModel` trace listeners for tracing are specified in the configuration file, none of your changes are taken into effect, even though the changes are accepted by WMI.</span></span> <span data-ttu-id="88ee9-130">Další informace o správné nastavení příslušných naslouchacích procesů, naleznete v tématu [konfigurace protokolování zpráv](../../../../../docs/framework/wcf/diagnostics/configuring-message-logging.md) a [Konfigurace trasování](../../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md).</span><span class="sxs-lookup"><span data-stu-id="88ee9-130">For more information on properly setting up the respective listeners, see [Configuring Message Logging](../../../../../docs/framework/wcf/diagnostics/configuring-message-logging.md) and [Configuring Tracing](../../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md).</span></span> <span data-ttu-id="88ee9-131">Úroveň trasování pro všechny ostatní zdroje trace zadáno v konfiguraci je účinné, když se aplikace spustí a nedá se změnit.</span><span class="sxs-lookup"><span data-stu-id="88ee9-131">The trace level of all other trace sources specified by configuration is effective when the application starts, and cannot be changed.</span></span>  
  
 <span data-ttu-id="88ee9-132">Zpřístupňuje WCF `GetOperationCounterInstanceName` metodu pro skriptování.</span><span class="sxs-lookup"><span data-stu-id="88ee9-132">WCF exposes a `GetOperationCounterInstanceName` method for scripting.</span></span> <span data-ttu-id="88ee9-133">Tato metoda vrátí název instance čítače výkonu, pokud zadáte s názvem operace.</span><span class="sxs-lookup"><span data-stu-id="88ee9-133">This method returns a performance counter instance name if you provide it with an operation name.</span></span> <span data-ttu-id="88ee9-134">Neověřuje však váš vstup.</span><span class="sxs-lookup"><span data-stu-id="88ee9-134">However, it does not validate your input.</span></span> <span data-ttu-id="88ee9-135">Proto pokud zadáte název nesprávná operace, je vrácen název nesprávné čítače.</span><span class="sxs-lookup"><span data-stu-id="88ee9-135">Therefore, if you provide an incorrect operation name, an incorrect counter name is returned.</span></span>  
  
 <span data-ttu-id="88ee9-136">`OutgoingChannel` Vlastnost `Service` instance nepočítá otevírány služby pro připojení k jiné službě, v případě klienta WFG pro cílové služby není v rámci kanálů `Service` metoda.</span><span class="sxs-lookup"><span data-stu-id="88ee9-136">The `OutgoingChannel` property of the `Service` instance does not count channels opened by a service to connect to another service, if the WCF client to the destination service is not created within the `Service` method.</span></span>  
  
 <span data-ttu-id="88ee9-137">**Upozornění:** WMI podporuje pouze <xref:System.TimeSpan> hodnotu až 3 desetinné čárky.</span><span class="sxs-lookup"><span data-stu-id="88ee9-137">**Caution** WMI only supports a <xref:System.TimeSpan> value up to 3 decimal points.</span></span> <span data-ttu-id="88ee9-138">Například, pokud vaše služba nastavuje jednu z vlastností <xref:System.TimeSpan.MaxValue>, její hodnota je zkrácen po 3 desetinné čárky při prohlížení prostřednictvím rozhraní WMI.</span><span class="sxs-lookup"><span data-stu-id="88ee9-138">For example, if your service sets one of its properties to <xref:System.TimeSpan.MaxValue>, its value is truncated after 3 decimal points when viewed through WMI.</span></span>  
  
## <a name="security"></a><span data-ttu-id="88ee9-139">Zabezpečení</span><span class="sxs-lookup"><span data-stu-id="88ee9-139">Security</span></span>  
 <span data-ttu-id="88ee9-140">Protože zprostředkovatel rozhraní WMI WCF umožňuje zjišťování služeb v prostředí, by měly využít extrémně opatrní pro udělení přístupu k němu.</span><span class="sxs-lookup"><span data-stu-id="88ee9-140">Because the WCF WMI provider allows the discovery of services in an environment, you should exercise extreme caution for granting access to it.</span></span> <span data-ttu-id="88ee9-141">Pokud jste zmírnit výchozí přístup jen pro správce, může povolit méně důvěryhodnému strany přístup k citlivým datům ve vašem prostředí.</span><span class="sxs-lookup"><span data-stu-id="88ee9-141">If you relax the default administrator-only access, you may allow less-trusted parties access to sensitive data in your environment.</span></span> <span data-ttu-id="88ee9-142">Pokud jste povolte oprávnění pro vzdálený přístup pomocí rozhraní WMI, konkrétně zahlcení útoky může dojít k.</span><span class="sxs-lookup"><span data-stu-id="88ee9-142">Specifically, if you loosen permissions on remote WMI access, flooding attacks can occur.</span></span> <span data-ttu-id="88ee9-143">Pokud proces je budete zaplaveni nadměrné požadavky rozhraní WMI, může snížit výkon.</span><span class="sxs-lookup"><span data-stu-id="88ee9-143">If a process is flooded by excessive WMI requests, its performance can be degraded.</span></span>  
  
 <span data-ttu-id="88ee9-144">Kromě toho pokud můžete uvolnit oprávnění k přístupu k souboru MOF, méně důvěryhodnému strany lze manipulovat s chování služby WMI a měnit objekty, které jsou načteny ve schématu WMI.</span><span class="sxs-lookup"><span data-stu-id="88ee9-144">In addition, if you relax access permissions for the MOF file, less-trusted parties can manipulate the behavior of WMI and alter the objects that are loaded in the WMI schema.</span></span> <span data-ttu-id="88ee9-145">Například pole lze odebrat tak, aby je důležitá data skryty od správce nebo pole, která naplnit nebo způsobit výjimky jsou přidány do souboru.</span><span class="sxs-lookup"><span data-stu-id="88ee9-145">For example, fields can be removed such that critical data is concealed from the administrator or that fields that do not populate or cause exceptions are added to the file.</span></span>  
  
 <span data-ttu-id="88ee9-146">Ve výchozím nastavení, zprostředkovatel rozhraní WMI WCF uděluje "metodu execute", "zapisovat zprostředkovatele" a "Povolit účet" oprávnění pro správce a oprávnění "Povolit účet" pro technologii ASP.NET, Local Service a Network Service.</span><span class="sxs-lookup"><span data-stu-id="88ee9-146">By default, the WCF WMI provider grants "execute method", "provider write", and "enable account" permission for Administrator, and "enable account" permission for ASP.NET, Local Service and Network Service.</span></span> <span data-ttu-id="88ee9-147">Konkrétně se na jinou hodnotu než[!INCLUDE[wv](../../../../../includes/wv-md.md)] platformy, účtu technologie ASP.NET má přístup pro čtení k oboru názvů WMI ServiceModel.</span><span class="sxs-lookup"><span data-stu-id="88ee9-147">In particular, on non-[!INCLUDE[wv](../../../../../includes/wv-md.md)] platforms, the ASP.NET account has read access to the WMI ServiceModel namespace.</span></span> <span data-ttu-id="88ee9-148">Pokud nechcete udělení těchto oprávnění určitou skupinu uživatelů, si deaktivace zprostředkovatele rozhraní WMI (je zakázané ve výchozím nastavení), nebo zakázat přístup pro konkrétního uživatele skupiny.</span><span class="sxs-lookup"><span data-stu-id="88ee9-148">If you do not want to grant these privileges to a particular user group, you should either deactivate the WMI provider (it is disabled by default), or disable access for the specific user group.</span></span>  
  
 <span data-ttu-id="88ee9-149">Navíc je při pokusu o povolení rozhraní WMI prostřednictvím konfigurace nemusí být povoleny služby WMI z důvodu nedostatečných uživatelských oprávnění.</span><span class="sxs-lookup"><span data-stu-id="88ee9-149">In addition, when you attempt to enable WMI through configuration, WMI may not be enabled due to insufficient user privilege.</span></span> <span data-ttu-id="88ee9-150">Žádné události je však zapsané do protokolu událostí pro záznam této chyby.</span><span class="sxs-lookup"><span data-stu-id="88ee9-150">However, no event is written to the event log to record this failure.</span></span>  
  
 <span data-ttu-id="88ee9-151">Chcete-li změnit úrovně oprávnění uživatele, postupujte následovně.</span><span class="sxs-lookup"><span data-stu-id="88ee9-151">To modify user privilege levels, use the following steps.</span></span>  
  
1. <span data-ttu-id="88ee9-152">Klikněte na tlačítko Start a pak spusťte a zadejte **compmgmt.msc**.</span><span class="sxs-lookup"><span data-stu-id="88ee9-152">Click Start and then Run and type **compmgmt.msc**.</span></span>  
  
2. <span data-ttu-id="88ee9-153">Klikněte pravým tlačítkem na **služeb a ovládací prvky aplikace/služby WMI** vyberte **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="88ee9-153">Right-click **Services and Application/WMI Controls** to select **Properties**.</span></span>  
  
3. <span data-ttu-id="88ee9-154">Vyberte **zabezpečení** kartu a přejděte **kořenový/ServiceModel** oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="88ee9-154">Select the **Security** Tab, and navigate to the **Root/ServiceModel** namespace.</span></span> <span data-ttu-id="88ee9-155">Klikněte na tlačítko **zabezpečení** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="88ee9-155">Click the **Security** button.</span></span>  
  
4. <span data-ttu-id="88ee9-156">Vyberte konkrétní skupinu nebo uživatele, kterou chcete řízení přístupu a použití **povolit** nebo **Odepřít** zaškrtávací políčko ke konfiguraci oprávnění.</span><span class="sxs-lookup"><span data-stu-id="88ee9-156">Select the specific group or user that you want to control access and use the **Allow** or **Deny** checkbox to configure permissions.</span></span>  
  
## <a name="granting-wcf-wmi-registration-permissions-to-additional-users"></a><span data-ttu-id="88ee9-157">Udělení oprávnění registrace služby WMI WCF dalším uživatelům</span><span class="sxs-lookup"><span data-stu-id="88ee9-157">Granting WCF WMI Registration Permissions to Additional Users</span></span>  
 <span data-ttu-id="88ee9-158">WCF zpřístupňuje data správy ke službě WMI.</span><span class="sxs-lookup"><span data-stu-id="88ee9-158">WCF exposes management data to WMI.</span></span> <span data-ttu-id="88ee9-159">Dělá to tak, že hostitelem poskytovatele služby WMI v procesu, někdy označuje jako "oddělený zprostředkovatel".</span><span class="sxs-lookup"><span data-stu-id="88ee9-159">It does so by hosting an in-process WMI provider, sometimes called a "decoupled provider".</span></span> <span data-ttu-id="88ee9-160">Pro správu data zpřístupní účet, který registruje tohoto zprostředkovatele musí mít příslušná oprávnění.</span><span class="sxs-lookup"><span data-stu-id="88ee9-160">For the management data to be exposed, the account that registers this provider must have the appropriate permissions.</span></span> <span data-ttu-id="88ee9-161">Ve Windows lze zaregistrovat pouze malou sadu privilegované účty oddělení zprostředkovatelé ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="88ee9-161">In Windows, only a small set of privileged accounts can register decoupled providers by default.</span></span> <span data-ttu-id="88ee9-162">To je problém, protože uživatelé běžně chcete je zveřejnit dat služby WMI ze služby WCF spuštěný pod účtem, který není v výchozí nastavení.</span><span class="sxs-lookup"><span data-stu-id="88ee9-162">This is a problem because users commonly want to expose WMI data from a WCF service running under an account that is not in the default set.</span></span>  
  
 <span data-ttu-id="88ee9-163">Pokud chcete poskytnout tento přístup, musí správce, udělte oprávnění na další účet v následujícím pořadí:</span><span class="sxs-lookup"><span data-stu-id="88ee9-163">To provide this access, an administrator must grant the following permissions to the additional account in the following order:</span></span>  
  
1. <span data-ttu-id="88ee9-164">Oprávnění pro přístup k rozhraní WMI Namespace WCF.</span><span class="sxs-lookup"><span data-stu-id="88ee9-164">Permission to access to the WCF WMI Namespace.</span></span>  
  
2. <span data-ttu-id="88ee9-165">Oprávnění k registraci zprostředkovatele rozhraní WMI odděleném WCF.</span><span class="sxs-lookup"><span data-stu-id="88ee9-165">Permission to register the WCF Decoupled WMI Provider.</span></span>  
  
#### <a name="to-grant-wmi-namespace-access-permission"></a><span data-ttu-id="88ee9-166">Udělení oprávnění k oboru názvů rozhraní WMI</span><span class="sxs-lookup"><span data-stu-id="88ee9-166">To grant WMI namespace access permission</span></span>  
  
1. <span data-ttu-id="88ee9-167">Spusťte následující skript prostředí PowerShell.</span><span class="sxs-lookup"><span data-stu-id="88ee9-167">Run the following PowerShell script.</span></span>  
  
    ```powershell  
    write-host ""  
    write-host "Granting Access to root/servicemodel WMI namespace to built in users group"  
    write-host ""  
  
    # Create the binary representation of the permissions to grant in SDDL  
    $newPermissions = "O:BAG:BAD:P(A;CI;CCDCLCSWRPWPRCWD;;;BA)(A;CI;CC;;;NS)(A;CI;CC;;;LS)(A;CI;CC;;;BU)"  
    $converter = new-object system.management.ManagementClass Win32_SecurityDescriptorHelper  
    $binarySD = $converter.SDDLToBinarySD($newPermissions)  
    $convertedPermissions = ,$binarySD.BinarySD  
  
    # Get the object used to set the permissions  
    $security = gwmi -namespace root/servicemodel -class __SystemSecurity  
  
    # Get and output the current settings  
    $binarySD = @($null)  
    $result = $security.PsBase.InvokeMethod("GetSD",$binarySD)  
  
    $outsddl = $converter.BinarySDToSDDL($binarySD[0])  
    write-host "Previous ACL: "$outsddl.SDDL  
  
    # Change the Access Control List (ACL) using SDDL  
    $result = $security.PsBase.InvokeMethod("SetSD",$convertedPermissions)   
  
    # Get and output the current settings  
    $binarySD = @($null)  
    $result = $security.PsBase.InvokeMethod("GetSD",$binarySD)  
  
    $outsddl = $converter.BinarySDToSDDL($binarySD[0])  
    write-host "New ACL:      "$outsddl.SDDL  
    write-host ""  
    ```  
  
     <span data-ttu-id="88ee9-168">Tento skript Powershellu používá zabezpečení SDDL Descriptor Definition Language () k udělení přístupu integrované uživatelé skupiny k oboru názvů WMI "kořenový/servicemodel".</span><span class="sxs-lookup"><span data-stu-id="88ee9-168">This PowerShell script uses Security Descriptor Definition Language (SDDL) to grant the Built-In Users group access to the "root/servicemodel" WMI namespace.</span></span> <span data-ttu-id="88ee9-169">Určuje následující seznamy ACL:</span><span class="sxs-lookup"><span data-stu-id="88ee9-169">It specifies the following ACLs:</span></span>  
  
    - <span data-ttu-id="88ee9-170">Předdefinovaný účet Administrator (BA) - už měli přístup.</span><span class="sxs-lookup"><span data-stu-id="88ee9-170">Built-In Administrator (BA) - Already Had Access.</span></span>  
  
    - <span data-ttu-id="88ee9-171">Síťová služba (NS) - už měli přístup.</span><span class="sxs-lookup"><span data-stu-id="88ee9-171">Network Service (NS) - Already Had Access.</span></span>  
  
    - <span data-ttu-id="88ee9-172">Místní systém (LS) - už měli přístup.</span><span class="sxs-lookup"><span data-stu-id="88ee9-172">Local System (LS) - Already Had Access.</span></span>  
  
    - <span data-ttu-id="88ee9-173">Integrované uživatelé – skupinu, kterou chcete udělit přístup k.</span><span class="sxs-lookup"><span data-stu-id="88ee9-173">Built-In Users - The group to grant access to.</span></span>  
  
#### <a name="to-grant-provider-registration-access"></a><span data-ttu-id="88ee9-174">Poskytovatel udělit přístup k registraci</span><span class="sxs-lookup"><span data-stu-id="88ee9-174">To grant provider registration access</span></span>  
  
1. <span data-ttu-id="88ee9-175">Spusťte následující skript prostředí PowerShell.</span><span class="sxs-lookup"><span data-stu-id="88ee9-175">Run the following PowerShell script.</span></span>  
  
    ```powershell  
    write-host ""  
    write-host "Granting WCF provider registration access to built in users group"  
    write-host ""  
    # Set security on ServiceModel provider  
    $provider = get-WmiObject -namespace "root\servicemodel" __Win32Provider  
  
    write-host "Previous ACL: "$provider.SecurityDescriptor  
    $result = $provider.SecurityDescriptor = "O:BUG:BUD:(A;;0x1;;;BA)(A;;0x1;;;NS)(A;;0x1;;;LS)(A;;0x1;;;BU)"  
  
    # Commit the changes and display it to the console  
    $result = $provider.Put()  
    write-host "New ACL:      "$provider.SecurityDescriptor  
    write-host ""  
    ```  
  
### <a name="granting-access-to-arbitrary-users-or-groups"></a><span data-ttu-id="88ee9-176">Udělení přístupu k libovolného uživatele nebo skupiny</span><span class="sxs-lookup"><span data-stu-id="88ee9-176">Granting Access to Arbitrary Users or Groups</span></span>  
 <span data-ttu-id="88ee9-177">Příklad v této části uděluje oprávnění registrace zprostředkovatele rozhraní WMI pro všechny místní uživatele.</span><span class="sxs-lookup"><span data-stu-id="88ee9-177">The example in this section grants WMI Provider registration privileges to all local users.</span></span> <span data-ttu-id="88ee9-178">Pokud chcete udělit přístup pro uživatele nebo skupiny, které není vestavěný, pak musíte získat tohoto uživatele nebo skupiny identifikátor zabezpečení (SID).</span><span class="sxs-lookup"><span data-stu-id="88ee9-178">If you want to grant access to a user or group that is not built in, then you must obtain that user or group’s Security Identifier (SID).</span></span> <span data-ttu-id="88ee9-179">Neexistuje žádné jednoduchý způsob, jak získat identifikátor SID pro libovolného uživatele.</span><span class="sxs-lookup"><span data-stu-id="88ee9-179">There is no simple way to get the SID for an arbitrary user.</span></span> <span data-ttu-id="88ee9-180">Jedním ze způsobů je přihlášení jako požadovaného uživatele a potom vydejte následující příkaz prostředí.</span><span class="sxs-lookup"><span data-stu-id="88ee9-180">One method is to log on as the desired user and then issue the following shell command.</span></span>  
  
```  
Whoami /user  
```  
  
 <span data-ttu-id="88ee9-181">To poskytuje SID aktuálního uživatele, ale tuto metodu nelze použít k načtení SID pro jakékoli libovolného uživatele.</span><span class="sxs-lookup"><span data-stu-id="88ee9-181">This provides the SID of the current user, but this method cannot be used to get the SID on any arbitrary user.</span></span> <span data-ttu-id="88ee9-182">Získat identifikátor SID jinou metodou je použít [getsid.exe](https://go.microsoft.com/fwlink/?LinkId=186467) nástroj z [Windows 2000 Resource Kit Tools pro úlohy správy](https://go.microsoft.com/fwlink/?LinkId=178660).</span><span class="sxs-lookup"><span data-stu-id="88ee9-182">Another method to get the SID is to use the [getsid.exe](https://go.microsoft.com/fwlink/?LinkId=186467) tool from the [Windows 2000 Resource Kit Tools for administrative tasks](https://go.microsoft.com/fwlink/?LinkId=178660).</span></span> <span data-ttu-id="88ee9-183">Tento nástroj porovná SID dva uživatele (místní nebo doménový) a jako souběžného efekt vytiskne dvě čísla SID do příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="88ee9-183">This tool compares the SID of two users (local or domain), and as a side effect prints the two SIDs to the command line.</span></span> <span data-ttu-id="88ee9-184">Další informace najdete v tématu [dobře známé identifikátory SID](https://go.microsoft.com/fwlink/?LinkId=186468).</span><span class="sxs-lookup"><span data-stu-id="88ee9-184">For more information, see [Well Known SIDs](https://go.microsoft.com/fwlink/?LinkId=186468).</span></span>  
  
## <a name="accessing-remote-wmi-object-instances"></a><span data-ttu-id="88ee9-185">Přistupující objekt instance vzdáleného rozhraní WMI</span><span class="sxs-lookup"><span data-stu-id="88ee9-185">Accessing Remote WMI Object Instances</span></span>  
 <span data-ttu-id="88ee9-186">Pokud potřebujete pro přístup k instancím WCF služby WMI na vzdáleném počítači, je nutné povolit paket o ochraně osobních údajů v nabídce Nástroje, které používáte pro přístup.</span><span class="sxs-lookup"><span data-stu-id="88ee9-186">If you need to access WCF WMI instances on a remote machine, you must enable packet privacy on the tools that you use for access.</span></span> <span data-ttu-id="88ee9-187">Následující část popisuje, jak tyto dosáhnout pomocí nástroje CIM Studio WMI, nástroj testování služby WMI Windows, stejně jako .NET SDK 2.0.</span><span class="sxs-lookup"><span data-stu-id="88ee9-187">The following section describes how to achieve these using the WMI CIM Studio, Windows Management Instrumentation Tester, as well as .NET SDK 2.0.</span></span>  
  
### <a name="wmi-cim-studio"></a><span data-ttu-id="88ee9-188">WMI CIM Studio</span><span class="sxs-lookup"><span data-stu-id="88ee9-188">WMI CIM Studio</span></span>  
 <span data-ttu-id="88ee9-189">Pokud jste nainstalovali [nástroje pro správu služby WMI](https://go.microsoft.com/fwlink/?LinkId=95185), můžete použít nástroje CIM Studio WMI do instancí služby WMI přístup.</span><span class="sxs-lookup"><span data-stu-id="88ee9-189">If you have installed [WMI Administrative Tools](https://go.microsoft.com/fwlink/?LinkId=95185), you can use the WMI CIM Studio to access WMI instances.</span></span> <span data-ttu-id="88ee9-190">Nástroje jsou v následující složce</span><span class="sxs-lookup"><span data-stu-id="88ee9-190">The tools are in the following folder</span></span>  
  
 <span data-ttu-id="88ee9-191">**%windir%\Program Files\WMI Tools\\**</span><span class="sxs-lookup"><span data-stu-id="88ee9-191">**%windir%\Program Files\WMI Tools\\**</span></span>  
  
1. <span data-ttu-id="88ee9-192">V **připojit k oboru názvů:** okno, zadejte **root\ServiceModel** a klikněte na tlačítko **OK.**</span><span class="sxs-lookup"><span data-stu-id="88ee9-192">In the **Connect to namespace:** window, type **root\ServiceModel** and click **OK.**</span></span>  
  
2. <span data-ttu-id="88ee9-193">V **WMI CIM Studio přihlášení** okna, klikněte na tlačítko **možnosti >>** tlačítko pro rozbalení v okně.</span><span class="sxs-lookup"><span data-stu-id="88ee9-193">In the **WMI CIM Studio Login** window, click the **Options >>** button to expand the window.</span></span> <span data-ttu-id="88ee9-194">Vyberte **paket o ochraně osobních údajů** pro **úroveň ověřování**a klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="88ee9-194">Select **Packet privacy** for **Authentication level**, and click **OK**.</span></span>  
  
### <a name="windows-management-instrumentation-tester"></a><span data-ttu-id="88ee9-195">Testování služby Windows Management Instrumentation</span><span class="sxs-lookup"><span data-stu-id="88ee9-195">Windows Management Instrumentation Tester</span></span>  
 <span data-ttu-id="88ee9-196">Tento nástroj je nainstalován ve Windows.</span><span class="sxs-lookup"><span data-stu-id="88ee9-196">This tool is installed by Windows.</span></span> <span data-ttu-id="88ee9-197">K jeho spuštění spuštění nástroje command console tak, že zadáte **cmd.exe** v **spuštění nebo spuštění** dialogové okno a klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="88ee9-197">To run it, launch a command console by typing **cmd.exe** in the **Start/Run** dialog box and click **OK**.</span></span> <span data-ttu-id="88ee9-198">Potom zadejte **wbemtest.exe** v příkazovém okně.</span><span class="sxs-lookup"><span data-stu-id="88ee9-198">Then, type **wbemtest.exe** in the command window.</span></span> <span data-ttu-id="88ee9-199">Pak je spustit nástroj testování služby Windows Management Instrumentation.</span><span class="sxs-lookup"><span data-stu-id="88ee9-199">The Windows Management Instrumentation Tester tool is then launched.</span></span>  
  
1. <span data-ttu-id="88ee9-200">Klikněte na tlačítko **připojit** tlačítko v pravém horním rohu okna.</span><span class="sxs-lookup"><span data-stu-id="88ee9-200">Click the **Connect** button on the top right corner of the window.</span></span>  
  
2. <span data-ttu-id="88ee9-201">V novém okně zadejte **root\ServiceModel** pro **Namespace** pole a vyberte **paket o ochraně osobních údajů** pro **úroveň ověřování**.</span><span class="sxs-lookup"><span data-stu-id="88ee9-201">In the new window, enter **root\ServiceModel** for the **Namespace** field, and select **Packet privacy** for **Authentication level**.</span></span> <span data-ttu-id="88ee9-202">Klikněte na **Připojit**.</span><span class="sxs-lookup"><span data-stu-id="88ee9-202">Click **Connect**.</span></span>  
  
### <a name="using-managed-code"></a><span data-ttu-id="88ee9-203">Pomocí spravovaného kódu</span><span class="sxs-lookup"><span data-stu-id="88ee9-203">Using Managed Code</span></span>  
 <span data-ttu-id="88ee9-204">Dostanete také vzdálené instance rozhraní WMI prostřednictvím kódu programu pomocí tříd poskytovaných oborem <xref:System.Management> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="88ee9-204">You can also access remote WMI instances programmatically by using classes provided by the <xref:System.Management> namespace.</span></span> <span data-ttu-id="88ee9-205">Následující příklad kódu ukazuje, jak to provést.</span><span class="sxs-lookup"><span data-stu-id="88ee9-205">The following code sample demonstrates how to do this.</span></span>  
  
```csharp
String wcfNamespace = $@"\\{this.serviceMachineName}\Root\ServiceModel");
  
ConnectionOptions connection = new ConnectionOptions();  
connection.Authentication = AuthenticationLevel.PacketPrivacy;  
ManagementScope scope = new ManagementScope(this.wcfNamespace, connection);  
```
