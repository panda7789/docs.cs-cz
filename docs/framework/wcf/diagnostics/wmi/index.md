---
title: Diagnostika prostřednictvím rozhraní WMI (Windows Management Instrumentation)
ms.date: 03/30/2017
ms.assetid: fe48738d-e31b-454d-b5ec-24c85c6bf79a
ms.openlocfilehash: 26758c8a4f537f9522d5ab650ae6b3cd8f044db2
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/05/2019
ms.locfileid: "74837438"
---
# <a name="using-windows-management-instrumentation-for-diagnostics"></a><span data-ttu-id="b2fb7-102">Diagnostika prostřednictvím rozhraní WMI (Windows Management Instrumentation)</span><span class="sxs-lookup"><span data-stu-id="b2fb7-102">Using Windows Management Instrumentation for Diagnostics</span></span>
<span data-ttu-id="b2fb7-103">Windows Communication Foundation (WCF) zveřejňuje kontrolní data služby za běhu prostřednictvím poskytovatele WCF rozhraní WMI (Windows Management Instrumentation) (WMI).</span><span class="sxs-lookup"><span data-stu-id="b2fb7-103">Windows Communication Foundation (WCF) exposes inspection data of a service at runtime through a WCF Windows Management Instrumentation (WMI) provider.</span></span>  
  
## <a name="enabling-wmi"></a><span data-ttu-id="b2fb7-104">Povolení služby WMI</span><span class="sxs-lookup"><span data-stu-id="b2fb7-104">Enabling WMI</span></span>  
 <span data-ttu-id="b2fb7-105">WMI je implementace standardu WBEM (Web-Based Enterprise Management) od Microsoftu.</span><span class="sxs-lookup"><span data-stu-id="b2fb7-105">WMI is Microsoft's implementation of the Web-Based Enterprise Management (WBEM) standard.</span></span> <span data-ttu-id="b2fb7-106">Další informace o sadě WMI SDK naleznete v tématu [rozhraní WMI (Windows Management Instrumentation)](/windows/desktop/WmiSdk/wmi-start-page).</span><span class="sxs-lookup"><span data-stu-id="b2fb7-106">For more information about the WMI SDK, see [Windows Management Instrumentation](/windows/desktop/WmiSdk/wmi-start-page).</span></span> <span data-ttu-id="b2fb7-107">WBEM je oborovým standardem, jak aplikace vystavují instrumentaci pro správu externích nástrojů pro správu.</span><span class="sxs-lookup"><span data-stu-id="b2fb7-107">WBEM is an industry standard for how applications expose management instrumentation to external management tools.</span></span>  
  
 <span data-ttu-id="b2fb7-108">Zprostředkovatel rozhraní WMI je komponenta, která zveřejňuje instrumentaci za běhu prostřednictvím rozhraní kompatibilního se standardem WBEM.</span><span class="sxs-lookup"><span data-stu-id="b2fb7-108">A WMI provider is a component that exposes instrumentation at runtime through a WBEM-compatible interface.</span></span> <span data-ttu-id="b2fb7-109">Skládá se ze sady objektů WMI, které mají páry atribut/hodnota.</span><span class="sxs-lookup"><span data-stu-id="b2fb7-109">It consists of a set of WMI objects that have attribute/value pairs.</span></span> <span data-ttu-id="b2fb7-110">Páry můžou být v mnoha jednoduchých typech.</span><span class="sxs-lookup"><span data-stu-id="b2fb7-110">Pairs can be of a number of simple types.</span></span> <span data-ttu-id="b2fb7-111">Nástroje pro správu se můžou ke službám připojit prostřednictvím rozhraní za běhu.</span><span class="sxs-lookup"><span data-stu-id="b2fb7-111">Management tools can connect to the services through the interface at runtime.</span></span> <span data-ttu-id="b2fb7-112">WCF zpřístupňuje atributy služeb, jako jsou adresy, vazby, chování a naslouchací procesy.</span><span class="sxs-lookup"><span data-stu-id="b2fb7-112">WCF exposes attributes of services such as addresses, bindings, behaviors, and listeners.</span></span>  
  
 <span data-ttu-id="b2fb7-113">Integrovaného zprostředkovatele WMI lze aktivovat v konfiguračním souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="b2fb7-113">The built-in WMI provider can be activated in the configuration file of the application.</span></span> <span data-ttu-id="b2fb7-114">To se provádí pomocí atributu `wmiProviderEnabled` [\<diagnostiky >](../../../configure-apps/file-schema/wcf/diagnostics.md) v části [\<system. ServiceModel >](../../../configure-apps/file-schema/wcf/system-servicemodel.md) , jak je znázorněno v následující ukázkové konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="b2fb7-114">This is done through the `wmiProviderEnabled` attribute of the [\<diagnostics>](../../../configure-apps/file-schema/wcf/diagnostics.md) in the [\<system.serviceModel>](../../../configure-apps/file-schema/wcf/system-servicemodel.md) section, as shown in the following sample configuration.</span></span>  
  
```xml  
<system.serviceModel>  
    …  
    <diagnostics wmiProviderEnabled="true" />  
    …  
</system.serviceModel>  
```  
  
 <span data-ttu-id="b2fb7-115">Tato položka konfigurace zpřístupňuje rozhraní WMI.</span><span class="sxs-lookup"><span data-stu-id="b2fb7-115">This configuration entry exposes a WMI interface.</span></span> <span data-ttu-id="b2fb7-116">Aplikace pro správu se teď můžou přes toto rozhraní připojit a přistupovat k instrumentaci správy aplikace.</span><span class="sxs-lookup"><span data-stu-id="b2fb7-116">Management applications can now connect through this interface and access the management instrumentation of the application.</span></span>  
  
## <a name="accessing-wmi-data"></a><span data-ttu-id="b2fb7-117">Přístup k datům WMI</span><span class="sxs-lookup"><span data-stu-id="b2fb7-117">Accessing WMI Data</span></span>  
 <span data-ttu-id="b2fb7-118">K datům WMI lze přistupovat mnoha různými způsoby.</span><span class="sxs-lookup"><span data-stu-id="b2fb7-118">WMI data can be accessed in many different ways.</span></span> <span data-ttu-id="b2fb7-119">Microsoft poskytuje rozhraní API služby WMI pro skripty, Visual Basic C++ aplikace, aplikace a .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b2fb7-119">Microsoft provides WMI APIs for scripts, Visual Basic applications, C++ applications, and the .NET Framework.</span></span> <span data-ttu-id="b2fb7-120">Další informace najdete v tématu [použití rozhraní WMI](https://go.microsoft.com/fwlink/?LinkId=95183).</span><span class="sxs-lookup"><span data-stu-id="b2fb7-120">For more information, see [Using WMI](https://go.microsoft.com/fwlink/?LinkId=95183).</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="b2fb7-121">Pokud používáte metody poskytnuté .NET Framework pro programový přístup k datům WMI, měli byste si uvědomit, že tyto metody mohou vyvolat výjimky při navázání spojení.</span><span class="sxs-lookup"><span data-stu-id="b2fb7-121">If you use the .NET Framework provided methods to programmatically access WMI data, you should be aware that such methods may throw exceptions when the connection is established.</span></span> <span data-ttu-id="b2fb7-122">Připojení není během vytváření instance <xref:System.Management.ManagementObject> navázáno, ale na první požadavek týkající se samotné výměny dat.</span><span class="sxs-lookup"><span data-stu-id="b2fb7-122">The connection is not established during the construction of the <xref:System.Management.ManagementObject> instance, but on the first request involving actual data exchange.</span></span> <span data-ttu-id="b2fb7-123">Proto byste měli použít `try..catch` blok k zachycení možných výjimek.</span><span class="sxs-lookup"><span data-stu-id="b2fb7-123">Therefore, you should use a `try..catch` block to catch the possible exceptions.</span></span>  
  
 <span data-ttu-id="b2fb7-124">Můžete změnit úroveň trasování a protokolování zpráv a také možnosti protokolování zpráv pro zdroj trasování `System.ServiceModel` v rozhraní WMI.</span><span class="sxs-lookup"><span data-stu-id="b2fb7-124">You can change the trace and message logging level, as well as message logging options for the `System.ServiceModel` trace source in WMI.</span></span> <span data-ttu-id="b2fb7-125">To lze provést přístupem k instanci [AppDomainInfo](appdomaininfo.md) , která zpřístupňuje tyto logické vlastnosti: `LogMessagesAtServiceLevel`, `LogMessagesAtTransportLevel`, `LogMalformedMessages`a `TraceLevel`.</span><span class="sxs-lookup"><span data-stu-id="b2fb7-125">This can be done by accessing the [AppDomainInfo](appdomaininfo.md) instance, which exposes these Boolean properties: `LogMessagesAtServiceLevel`, `LogMessagesAtTransportLevel`, `LogMalformedMessages`, and `TraceLevel`.</span></span> <span data-ttu-id="b2fb7-126">Proto pokud nakonfigurujete naslouchací proces trasování pro protokolování zpráv, ale nastavte tyto možnosti na `false` v konfiguraci, můžete je později změnit na `true`, pokud je aplikace spuštěná.</span><span class="sxs-lookup"><span data-stu-id="b2fb7-126">Therefore, if you configure a trace listener for message logging, but set these options to `false` in configuration, you can later change them to `true` when the application is running.</span></span> <span data-ttu-id="b2fb7-127">Tím se efektivně povolí protokolování zpráv za běhu.</span><span class="sxs-lookup"><span data-stu-id="b2fb7-127">This will effectively enable message logging at runtime.</span></span> <span data-ttu-id="b2fb7-128">Podobně platí, že pokud povolíte protokolování zpráv v konfiguračním souboru, můžete ho za běhu zakázat pomocí rozhraní WMI.</span><span class="sxs-lookup"><span data-stu-id="b2fb7-128">Similarly, if you enable message logging in your configuration file, you can disable it at runtime using WMI.</span></span>  
  
 <span data-ttu-id="b2fb7-129">Měli byste si uvědomit, že pokud pro protokolování zpráv nejsou k dispozici naslouchací procesy trasování zpráv, nebo nejsou žádné naslouchací procesy trasování `System.ServiceModel` pro trasování v konfiguračním souboru, nejsou uplatněny žádné změny, ani když jsou změny přijímány rozhraním WMI.</span><span class="sxs-lookup"><span data-stu-id="b2fb7-129">You should be aware that if no message logging trace listeners for message logging, or no `System.ServiceModel` trace listeners for tracing are specified in the configuration file, none of your changes are taken into effect, even though the changes are accepted by WMI.</span></span> <span data-ttu-id="b2fb7-130">Další informace o správném nastavení příslušného naslouchacího procesu najdete v tématu [Konfigurace protokolování zpráv](../configuring-message-logging.md) a [Konfigurace trasování](../tracing/configuring-tracing.md).</span><span class="sxs-lookup"><span data-stu-id="b2fb7-130">For more information on properly setting up the respective listeners, see [Configuring Message Logging](../configuring-message-logging.md) and [Configuring Tracing](../tracing/configuring-tracing.md).</span></span> <span data-ttu-id="b2fb7-131">Úroveň trasování všech ostatních zdrojů trasování určených konfigurací je platná při spuštění aplikace a nelze ji změnit.</span><span class="sxs-lookup"><span data-stu-id="b2fb7-131">The trace level of all other trace sources specified by configuration is effective when the application starts, and cannot be changed.</span></span>  
  
 <span data-ttu-id="b2fb7-132">WCF zpřístupňuje metodu `GetOperationCounterInstanceName` pro skriptování.</span><span class="sxs-lookup"><span data-stu-id="b2fb7-132">WCF exposes a `GetOperationCounterInstanceName` method for scripting.</span></span> <span data-ttu-id="b2fb7-133">Tato metoda vrací název instance čítače výkonu, pokud jej zadáte s názvem operace.</span><span class="sxs-lookup"><span data-stu-id="b2fb7-133">This method returns a performance counter instance name if you provide it with an operation name.</span></span> <span data-ttu-id="b2fb7-134">Neověřuje ale vaše zadání.</span><span class="sxs-lookup"><span data-stu-id="b2fb7-134">However, it does not validate your input.</span></span> <span data-ttu-id="b2fb7-135">Proto pokud zadáte nesprávný název operace, vrátí se nesprávný název čítače.</span><span class="sxs-lookup"><span data-stu-id="b2fb7-135">Therefore, if you provide an incorrect operation name, an incorrect counter name is returned.</span></span>  
  
 <span data-ttu-id="b2fb7-136">Vlastnost `OutgoingChannel` instance `Service` nepočítá kanály, které služba otevřela, aby se mohla připojit k jiné službě, pokud klient WCF cílové službě není vytvořen v rámci metody `Service`.</span><span class="sxs-lookup"><span data-stu-id="b2fb7-136">The `OutgoingChannel` property of the `Service` instance does not count channels opened by a service to connect to another service, if the WCF client to the destination service is not created within the `Service` method.</span></span>  
  
 <span data-ttu-id="b2fb7-137">**Upozornění** WMI podporuje pouze <xref:System.TimeSpan> hodnotu až 3 desetinná místa.</span><span class="sxs-lookup"><span data-stu-id="b2fb7-137">**Caution** WMI only supports a <xref:System.TimeSpan> value up to 3 decimal points.</span></span> <span data-ttu-id="b2fb7-138">Například pokud vaše služba nastaví jednu z vlastností na <xref:System.TimeSpan.MaxValue>, její hodnota se po zobrazení pomocí rozhraní WMI zkrátí po 3 desítkových bodech.</span><span class="sxs-lookup"><span data-stu-id="b2fb7-138">For example, if your service sets one of its properties to <xref:System.TimeSpan.MaxValue>, its value is truncated after 3 decimal points when viewed through WMI.</span></span>  
  
## <a name="security"></a><span data-ttu-id="b2fb7-139">Zabezpečení –</span><span class="sxs-lookup"><span data-stu-id="b2fb7-139">Security</span></span>  
 <span data-ttu-id="b2fb7-140">Vzhledem k tomu, že zprostředkovatel rozhraní WMI služby WCF umožňuje zjišťování služeb v prostředí, měli byste pro udělení přístupu využít mimořádně opatrní.</span><span class="sxs-lookup"><span data-stu-id="b2fb7-140">Because the WCF WMI provider allows the discovery of services in an environment, you should exercise extreme caution for granting access to it.</span></span> <span data-ttu-id="b2fb7-141">Pokud nebudete mít přístup k citlivým datům ve vašem prostředí jen výchozím správcem, můžete jim udělit méně důvěryhodné strany.</span><span class="sxs-lookup"><span data-stu-id="b2fb7-141">If you relax the default administrator-only access, you may allow less-trusted parties access to sensitive data in your environment.</span></span> <span data-ttu-id="b2fb7-142">Konkrétně, pokud k přístupu ke vzdálenému přístupu přes rozhraní WMI přistupujete, může dojít k útokům při zahlcení.</span><span class="sxs-lookup"><span data-stu-id="b2fb7-142">Specifically, if you loosen permissions on remote WMI access, flooding attacks can occur.</span></span> <span data-ttu-id="b2fb7-143">Pokud je proces zahlcen nadměrnými požadavky rozhraní WMI, může jeho výkon zhoršit.</span><span class="sxs-lookup"><span data-stu-id="b2fb7-143">If a process is flooded by excessive WMI requests, its performance can be degraded.</span></span>  
  
 <span data-ttu-id="b2fb7-144">Kromě toho platí, že pokud pro soubor MOF dojde k nedostatku oprávnění, nedůvěryhodné strany budou moci manipulovat s chováním služby WMI a měnit objekty, které jsou načteny ve schématu WMI.</span><span class="sxs-lookup"><span data-stu-id="b2fb7-144">In addition, if you relax access permissions for the MOF file, less-trusted parties can manipulate the behavior of WMI and alter the objects that are loaded in the WMI schema.</span></span> <span data-ttu-id="b2fb7-145">Například je možné odebrat pole tak, aby důležitá data byla skryta od správce nebo aby se do souboru přidala pole, která neplní nebo nezpůsobí výjimky.</span><span class="sxs-lookup"><span data-stu-id="b2fb7-145">For example, fields can be removed such that critical data is concealed from the administrator or that fields that do not populate or cause exceptions are added to the file.</span></span>  
  
 <span data-ttu-id="b2fb7-146">Ve výchozím nastavení udělí zprostředkovatel WMI WCF oprávnění "spouštět metodu", "Provider Write" a "Enable Account" pro správce a oprávnění "Povolit účet" pro ASP.NET, místní službu a síťovou službu.</span><span class="sxs-lookup"><span data-stu-id="b2fb7-146">By default, the WCF WMI provider grants "execute method", "provider write", and "enable account" permission for Administrator, and "enable account" permission for ASP.NET, Local Service and Network Service.</span></span> <span data-ttu-id="b2fb7-147">Zejména na platformách jiných než Windows Vista má účet ASP.NET oprávnění ke čtení pro obor názvů rozhraní WMI ServiceModel.</span><span class="sxs-lookup"><span data-stu-id="b2fb7-147">In particular, on non-Windows Vista platforms, the ASP.NET account has read access to the WMI ServiceModel namespace.</span></span> <span data-ttu-id="b2fb7-148">Pokud nechcete tato oprávnění udělit konkrétní skupině uživatelů, měli byste buď deaktivovat poskytovatele rozhraní WMI (ve výchozím nastavení je zakázaný), nebo zakázat přístup pro konkrétní skupinu uživatelů.</span><span class="sxs-lookup"><span data-stu-id="b2fb7-148">If you do not want to grant these privileges to a particular user group, you should either deactivate the WMI provider (it is disabled by default), or disable access for the specific user group.</span></span>  
  
 <span data-ttu-id="b2fb7-149">Kromě toho, pokud se pokusíte povolit rozhraní WMI prostřednictvím konfigurace, rozhraní WMI nemusí být povoleno z důvodu nedostatečného oprávnění uživatele.</span><span class="sxs-lookup"><span data-stu-id="b2fb7-149">In addition, when you attempt to enable WMI through configuration, WMI may not be enabled due to insufficient user privilege.</span></span> <span data-ttu-id="b2fb7-150">Nicméně žádná událost není zapsána do protokolu událostí, aby mohla zaznamenat tuto chybu.</span><span class="sxs-lookup"><span data-stu-id="b2fb7-150">However, no event is written to the event log to record this failure.</span></span>  
  
 <span data-ttu-id="b2fb7-151">Chcete-li upravit úrovně oprávnění uživatele, použijte následující postup.</span><span class="sxs-lookup"><span data-stu-id="b2fb7-151">To modify user privilege levels, use the following steps.</span></span>  
  
1. <span data-ttu-id="b2fb7-152">Klikněte na Start, pak na spustit a zadejte **compmgmt. msc**.</span><span class="sxs-lookup"><span data-stu-id="b2fb7-152">Click Start and then Run and type **compmgmt.msc**.</span></span>  
  
2. <span data-ttu-id="b2fb7-153">Klikněte pravým tlačítkem na **služby a ovládací prvky Application/WMI** a vyberte **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="b2fb7-153">Right-click **Services and Application/WMI Controls** to select **Properties**.</span></span>  
  
3. <span data-ttu-id="b2fb7-154">Vyberte kartu **zabezpečení** a přejděte do oboru názvů **root/ServiceModel** .</span><span class="sxs-lookup"><span data-stu-id="b2fb7-154">Select the **Security** Tab, and navigate to the **Root/ServiceModel** namespace.</span></span> <span data-ttu-id="b2fb7-155">Klikněte na tlačítko **zabezpečení** .</span><span class="sxs-lookup"><span data-stu-id="b2fb7-155">Click the **Security** button.</span></span>  
  
4. <span data-ttu-id="b2fb7-156">Vyberte konkrétní skupinu nebo uživatele, kterým chcete řídit přístup, a pro konfiguraci oprávnění použijte zaškrtávací políčko **Povolit** nebo **Odepřít** .</span><span class="sxs-lookup"><span data-stu-id="b2fb7-156">Select the specific group or user that you want to control access and use the **Allow** or **Deny** checkbox to configure permissions.</span></span>  
  
## <a name="granting-wcf-wmi-registration-permissions-to-additional-users"></a><span data-ttu-id="b2fb7-157">Udělení oprávnění k registraci rozhraní WMI WCF dalším uživatelům</span><span class="sxs-lookup"><span data-stu-id="b2fb7-157">Granting WCF WMI Registration Permissions to Additional Users</span></span>  
 <span data-ttu-id="b2fb7-158">WCF zpřístupňuje data správy rozhraní WMI.</span><span class="sxs-lookup"><span data-stu-id="b2fb7-158">WCF exposes management data to WMI.</span></span> <span data-ttu-id="b2fb7-159">Je tak hostitelem zprostředkovatele rozhraní WMI v procesu, někdy označovaného jako "oddělený poskytovatel".</span><span class="sxs-lookup"><span data-stu-id="b2fb7-159">It does so by hosting an in-process WMI provider, sometimes called a "decoupled provider".</span></span> <span data-ttu-id="b2fb7-160">Aby bylo možné zveřejnit data správy, musí mít účet, který registruje tohoto poskytovatele, příslušná oprávnění.</span><span class="sxs-lookup"><span data-stu-id="b2fb7-160">For the management data to be exposed, the account that registers this provider must have the appropriate permissions.</span></span> <span data-ttu-id="b2fb7-161">V systému Windows je ve výchozím nastavení možné zaregistrovat oddělené zprostředkovatele jenom v malých sestavách privilegovaných účtů.</span><span class="sxs-lookup"><span data-stu-id="b2fb7-161">In Windows, only a small set of privileged accounts can register decoupled providers by default.</span></span> <span data-ttu-id="b2fb7-162">Tato chyba je způsobena tím, že uživatelé obvykle chtějí vystavit data služby WMI ze služby WCF spuštěné v rámci účtu, který není ve výchozí sadě.</span><span class="sxs-lookup"><span data-stu-id="b2fb7-162">This is a problem because users commonly want to expose WMI data from a WCF service running under an account that is not in the default set.</span></span>  
  
 <span data-ttu-id="b2fb7-163">K poskytnutí tohoto přístupu musí správce udělit dodatečnému účtu následující oprávnění v následujícím pořadí:</span><span class="sxs-lookup"><span data-stu-id="b2fb7-163">To provide this access, an administrator must grant the following permissions to the additional account in the following order:</span></span>  
  
1. <span data-ttu-id="b2fb7-164">Oprávnění pro přístup k oboru názvů WMI služby WCF.</span><span class="sxs-lookup"><span data-stu-id="b2fb7-164">Permission to access to the WCF WMI Namespace.</span></span>  
  
2. <span data-ttu-id="b2fb7-165">Oprávnění k registraci zprostředkovatele rozhraní WMI pro oddělené služby WCF.</span><span class="sxs-lookup"><span data-stu-id="b2fb7-165">Permission to register the WCF Decoupled WMI Provider.</span></span>  
  
#### <a name="to-grant-wmi-namespace-access-permission"></a><span data-ttu-id="b2fb7-166">Udělení přístupových oprávnění k oboru názvů rozhraní WMI</span><span class="sxs-lookup"><span data-stu-id="b2fb7-166">To grant WMI namespace access permission</span></span>  
  
1. <span data-ttu-id="b2fb7-167">Spusťte následující skript prostředí PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b2fb7-167">Run the following PowerShell script.</span></span>  
  
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
  
     <span data-ttu-id="b2fb7-168">Tento skript PowerShellu používá jazyk SDDL (Security Descriptor Definition Language) k udělení přístupu předdefinovaných uživatelů do oboru názvů "root/ServiceModel" rozhraní WMI.</span><span class="sxs-lookup"><span data-stu-id="b2fb7-168">This PowerShell script uses Security Descriptor Definition Language (SDDL) to grant the Built-In Users group access to the "root/servicemodel" WMI namespace.</span></span> <span data-ttu-id="b2fb7-169">Určuje následující seznamy ACL:</span><span class="sxs-lookup"><span data-stu-id="b2fb7-169">It specifies the following ACLs:</span></span>  
  
    - <span data-ttu-id="b2fb7-170">Předdefinovaný správce (BA) – již měl přístup.</span><span class="sxs-lookup"><span data-stu-id="b2fb7-170">Built-In Administrator (BA) - Already Had Access.</span></span>  
  
    - <span data-ttu-id="b2fb7-171">Síťová služba (NS) – již měl přístup.</span><span class="sxs-lookup"><span data-stu-id="b2fb7-171">Network Service (NS) - Already Had Access.</span></span>  
  
    - <span data-ttu-id="b2fb7-172">Místní systém (LS) – již měl přístup.</span><span class="sxs-lookup"><span data-stu-id="b2fb7-172">Local System (LS) - Already Had Access.</span></span>  
  
    - <span data-ttu-id="b2fb7-173">Předdefinované uživatele – skupina, pro kterou má být udělen přístup.</span><span class="sxs-lookup"><span data-stu-id="b2fb7-173">Built-In Users - The group to grant access to.</span></span>  
  
#### <a name="to-grant-provider-registration-access"></a><span data-ttu-id="b2fb7-174">Udělení přístupu k registraci poskytovatele</span><span class="sxs-lookup"><span data-stu-id="b2fb7-174">To grant provider registration access</span></span>  
  
1. <span data-ttu-id="b2fb7-175">Spusťte následující skript prostředí PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b2fb7-175">Run the following PowerShell script.</span></span>  
  
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
  
### <a name="granting-access-to-arbitrary-users-or-groups"></a><span data-ttu-id="b2fb7-176">Udělení přístupu libovolným uživatelům nebo skupinám</span><span class="sxs-lookup"><span data-stu-id="b2fb7-176">Granting Access to Arbitrary Users or Groups</span></span>  
 <span data-ttu-id="b2fb7-177">Příklad v této části uděluje oprávnění k registraci zprostředkovatele rozhraní WMI všem místním uživatelům.</span><span class="sxs-lookup"><span data-stu-id="b2fb7-177">The example in this section grants WMI Provider registration privileges to all local users.</span></span> <span data-ttu-id="b2fb7-178">Pokud chcete udělit přístup uživateli nebo skupině, která není integrovaná v, musíte získat identifikátor zabezpečení (SID) daného uživatele nebo skupiny.</span><span class="sxs-lookup"><span data-stu-id="b2fb7-178">If you want to grant access to a user or group that is not built in, then you must obtain that user or group’s Security Identifier (SID).</span></span> <span data-ttu-id="b2fb7-179">Neexistuje žádný jednoduchý způsob, jak získat SID pro libovolného uživatele.</span><span class="sxs-lookup"><span data-stu-id="b2fb7-179">There is no simple way to get the SID for an arbitrary user.</span></span> <span data-ttu-id="b2fb7-180">Jedna z metod se přihlaste jako požadovaný uživatel a pak vydejte následující příkaz prostředí.</span><span class="sxs-lookup"><span data-stu-id="b2fb7-180">One method is to log on as the desired user and then issue the following shell command.</span></span>  
  
```console
Whoami /user  
```  
  
 <span data-ttu-id="b2fb7-181">Tato metoda poskytuje identifikátor SID aktuálního uživatele, ale tuto metodu nelze použít k získání čísla SID pro libovolného uživatele.</span><span class="sxs-lookup"><span data-stu-id="b2fb7-181">This provides the SID of the current user, but this method cannot be used to get the SID on any arbitrary user.</span></span> <span data-ttu-id="b2fb7-182">Další metodou získání identifikátoru SID je použití nástroje [getsid. exe](https://go.microsoft.com/fwlink/?LinkId=186467) z [nástrojů sady Windows 2000 Resource Kit pro úlohy správy](https://go.microsoft.com/fwlink/?LinkId=178660).</span><span class="sxs-lookup"><span data-stu-id="b2fb7-182">Another method to get the SID is to use the [getsid.exe](https://go.microsoft.com/fwlink/?LinkId=186467) tool from the [Windows 2000 Resource Kit Tools for administrative tasks](https://go.microsoft.com/fwlink/?LinkId=178660).</span></span> <span data-ttu-id="b2fb7-183">Tento nástroj porovná identifikátor SID dvou uživatelů (místní nebo doména) a jako vedlejší efekt budou tyto dva identifikátory SID vytištěny na příkazovém řádku.</span><span class="sxs-lookup"><span data-stu-id="b2fb7-183">This tool compares the SID of two users (local or domain), and as a side effect prints the two SIDs to the command line.</span></span> <span data-ttu-id="b2fb7-184">Další informace najdete v tématu [dobře známé identifikátory SID](https://go.microsoft.com/fwlink/?LinkId=186468).</span><span class="sxs-lookup"><span data-stu-id="b2fb7-184">For more information, see [Well Known SIDs](https://go.microsoft.com/fwlink/?LinkId=186468).</span></span>  
  
## <a name="accessing-remote-wmi-object-instances"></a><span data-ttu-id="b2fb7-185">Přístup k instancím vzdálených objektů služby WMI</span><span class="sxs-lookup"><span data-stu-id="b2fb7-185">Accessing Remote WMI Object Instances</span></span>  
 <span data-ttu-id="b2fb7-186">Pokud potřebujete přístup k instancím WCF WMI na vzdáleném počítači, musíte povolit ochranu osobních údajů paketů u nástrojů, které používáte pro přístup.</span><span class="sxs-lookup"><span data-stu-id="b2fb7-186">If you need to access WCF WMI instances on a remote machine, you must enable packet privacy on the tools that you use for access.</span></span> <span data-ttu-id="b2fb7-187">Následující část popisuje, jak dosáhnout těchto možností pomocí rozhraní WMI CIM Studio, rozhraní WMI (Windows Management Instrumentation) testeru a sady .NET SDK 2,0.</span><span class="sxs-lookup"><span data-stu-id="b2fb7-187">The following section describes how to achieve these using the WMI CIM Studio, Windows Management Instrumentation Tester, as well as .NET SDK 2.0.</span></span>  
  
### <a name="wmi-cim-studio"></a><span data-ttu-id="b2fb7-188">WMI CIM Studio</span><span class="sxs-lookup"><span data-stu-id="b2fb7-188">WMI CIM Studio</span></span>  
 <span data-ttu-id="b2fb7-189">Pokud jste nainstalovali [Nástroje pro správu služby WMI](https://go.microsoft.com/fwlink/?LinkId=95185), můžete k přístupu k INSTANCÍM rozhraní WMI použít rozhraní WMI CIM.</span><span class="sxs-lookup"><span data-stu-id="b2fb7-189">If you have installed [WMI Administrative Tools](https://go.microsoft.com/fwlink/?LinkId=95185), you can use the WMI CIM Studio to access WMI instances.</span></span> <span data-ttu-id="b2fb7-190">Nástroje jsou v následující složce</span><span class="sxs-lookup"><span data-stu-id="b2fb7-190">The tools are in the following folder</span></span>  
  
 <span data-ttu-id="b2fb7-191">**%windir%\Program Files\WMI Tools\\**</span><span class="sxs-lookup"><span data-stu-id="b2fb7-191">**%windir%\Program Files\WMI Tools\\**</span></span>  
  
1. <span data-ttu-id="b2fb7-192">V okně **připojit k oboru názvů:** zadejte **root\ServiceModel** a klikněte na **OK.**</span><span class="sxs-lookup"><span data-stu-id="b2fb7-192">In the **Connect to namespace:** window, type **root\ServiceModel** and click **OK.**</span></span>  
  
2. <span data-ttu-id="b2fb7-193">V okně **přihlášení WMI CIM Studio** kliknutím na tlačítko **Možnosti > >** okno rozbalte.</span><span class="sxs-lookup"><span data-stu-id="b2fb7-193">In the **WMI CIM Studio Login** window, click the **Options >>** button to expand the window.</span></span> <span data-ttu-id="b2fb7-194">Vyberte možnost **Ochrana osobních údajů paketů** pro **úroveň ověřování**a klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="b2fb7-194">Select **Packet privacy** for **Authentication level**, and click **OK**.</span></span>  
  
### <a name="windows-management-instrumentation-tester"></a><span data-ttu-id="b2fb7-195">rozhraní WMI (Windows Management Instrumentation) Tester</span><span class="sxs-lookup"><span data-stu-id="b2fb7-195">Windows Management Instrumentation Tester</span></span>  
 <span data-ttu-id="b2fb7-196">Tento nástroj je nainstalován systémem Windows.</span><span class="sxs-lookup"><span data-stu-id="b2fb7-196">This tool is installed by Windows.</span></span> <span data-ttu-id="b2fb7-197">Pokud ho chcete spustit, spusťte konzolu příkazů tak, že v dialogovém okně **Spustit/spustit** zadáte **cmd. exe** a kliknete na **OK**.</span><span class="sxs-lookup"><span data-stu-id="b2fb7-197">To run it, launch a command console by typing **cmd.exe** in the **Start/Run** dialog box and click **OK**.</span></span> <span data-ttu-id="b2fb7-198">Pak do příkazového okna zadejte **WBEMTest. exe** .</span><span class="sxs-lookup"><span data-stu-id="b2fb7-198">Then, type **wbemtest.exe** in the command window.</span></span> <span data-ttu-id="b2fb7-199">Pak se spustí nástroj rozhraní WMI (Windows Management Instrumentation) Tester.</span><span class="sxs-lookup"><span data-stu-id="b2fb7-199">The Windows Management Instrumentation Tester tool is then launched.</span></span>  
  
1. <span data-ttu-id="b2fb7-200">Klikněte na tlačítko **připojit** v pravém horním rohu okna.</span><span class="sxs-lookup"><span data-stu-id="b2fb7-200">Click the **Connect** button on the top right corner of the window.</span></span>  
  
2. <span data-ttu-id="b2fb7-201">V novém okně zadejte **root\ServiceModel** do pole **obor názvů** a vyberte **ochrana paketů** pro **úroveň ověřování**.</span><span class="sxs-lookup"><span data-stu-id="b2fb7-201">In the new window, enter **root\ServiceModel** for the **Namespace** field, and select **Packet privacy** for **Authentication level**.</span></span> <span data-ttu-id="b2fb7-202">Klikněte na **Připojit**.</span><span class="sxs-lookup"><span data-stu-id="b2fb7-202">Click **Connect**.</span></span>  
  
### <a name="using-managed-code"></a><span data-ttu-id="b2fb7-203">Použití spravovaného kódu</span><span class="sxs-lookup"><span data-stu-id="b2fb7-203">Using Managed Code</span></span>  
 <span data-ttu-id="b2fb7-204">Vzdálené instance služby WMI můžete získat také programově pomocí tříd poskytovaných oborem názvů <xref:System.Management>.</span><span class="sxs-lookup"><span data-stu-id="b2fb7-204">You can also access remote WMI instances programmatically by using classes provided by the <xref:System.Management> namespace.</span></span> <span data-ttu-id="b2fb7-205">Následující příklad kódu ukazuje, jak to provést.</span><span class="sxs-lookup"><span data-stu-id="b2fb7-205">The following code sample demonstrates how to do this.</span></span>  
  
```csharp
String wcfNamespace = $@"\\{this.serviceMachineName}\Root\ServiceModel");
  
ConnectionOptions connection = new ConnectionOptions();  
connection.Authentication = AuthenticationLevel.PacketPrivacy;  
ManagementScope scope = new ManagementScope(this.wcfNamespace, connection);  
```
