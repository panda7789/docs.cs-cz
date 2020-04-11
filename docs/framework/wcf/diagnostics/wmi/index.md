---
title: Diagnostika prostřednictvím rozhraní WMI (Windows Management Instrumentation)
ms.date: 03/30/2017
ms.assetid: fe48738d-e31b-454d-b5ec-24c85c6bf79a
ms.openlocfilehash: b14f9401266bdf7edccd7dca12cb818cdd2cb348
ms.sourcegitcommit: 43cbde34970f5f38f30c43cd63b9c7e2e83717ae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/11/2020
ms.locfileid: "81121551"
---
# <a name="using-windows-management-instrumentation-for-diagnostics"></a><span data-ttu-id="aa3ba-102">Diagnostika prostřednictvím rozhraní WMI (Windows Management Instrumentation)</span><span class="sxs-lookup"><span data-stu-id="aa3ba-102">Using Windows Management Instrumentation for Diagnostics</span></span>
<span data-ttu-id="aa3ba-103">Windows Communication Foundation (WCF) zveřejňuje kontrolní data služby za běhu prostřednictvím wcf windows management instrumentace (WMI) zprostředkovatele.</span><span class="sxs-lookup"><span data-stu-id="aa3ba-103">Windows Communication Foundation (WCF) exposes inspection data of a service at runtime through a WCF Windows Management Instrumentation (WMI) provider.</span></span>  
  
## <a name="enabling-wmi"></a><span data-ttu-id="aa3ba-104">Povolení technologie WMI</span><span class="sxs-lookup"><span data-stu-id="aa3ba-104">Enabling WMI</span></span>  
 <span data-ttu-id="aa3ba-105">Služba WMI je implementací standardu WBEM (Web-Based Enterprise Management) společností Microsoft.</span><span class="sxs-lookup"><span data-stu-id="aa3ba-105">WMI is Microsoft's implementation of the Web-Based Enterprise Management (WBEM) standard.</span></span> <span data-ttu-id="aa3ba-106">Další informace o sdk sady WMI naleznete v [tématu WMI Management Instrumentation](/windows/desktop/WmiSdk/wmi-start-page).</span><span class="sxs-lookup"><span data-stu-id="aa3ba-106">For more information about the WMI SDK, see [Windows Management Instrumentation](/windows/desktop/WmiSdk/wmi-start-page).</span></span> <span data-ttu-id="aa3ba-107">WBEM je oborový standard pro to, jak aplikace zveřejňují nástroje pro správu externím nástrojům pro správu.</span><span class="sxs-lookup"><span data-stu-id="aa3ba-107">WBEM is an industry standard for how applications expose management instrumentation to external management tools.</span></span>  
  
 <span data-ttu-id="aa3ba-108">Zprostředkovatel služby WMI je součást, která zpřístupňuje instrumentaci za běhu prostřednictvím rozhraní kompatibilního s rozhraním wbem.</span><span class="sxs-lookup"><span data-stu-id="aa3ba-108">A WMI provider is a component that exposes instrumentation at runtime through a WBEM-compatible interface.</span></span> <span data-ttu-id="aa3ba-109">Skládá se ze sady objektů služby WMI, které mají dvojice atributů a hodnot.</span><span class="sxs-lookup"><span data-stu-id="aa3ba-109">It consists of a set of WMI objects that have attribute/value pairs.</span></span> <span data-ttu-id="aa3ba-110">Dvojice mohou být několika jednoduchých typů.</span><span class="sxs-lookup"><span data-stu-id="aa3ba-110">Pairs can be of a number of simple types.</span></span> <span data-ttu-id="aa3ba-111">Nástroje pro správu se mohou připojit ke službám prostřednictvím rozhraní za běhu.</span><span class="sxs-lookup"><span data-stu-id="aa3ba-111">Management tools can connect to the services through the interface at runtime.</span></span> <span data-ttu-id="aa3ba-112">WCF zveřejňuje atributy služeb, jako jsou adresy, vazby, chování a naslouchací procesy.</span><span class="sxs-lookup"><span data-stu-id="aa3ba-112">WCF exposes attributes of services such as addresses, bindings, behaviors, and listeners.</span></span>  
  
 <span data-ttu-id="aa3ba-113">Vestavěného zprostředkovatele služby WMI lze aktivovat v konfiguračním souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="aa3ba-113">The built-in WMI provider can be activated in the configuration file of the application.</span></span> <span data-ttu-id="aa3ba-114">To se provádí `wmiProviderEnabled` prostřednictvím atributu [ \<diagnostics>](../../../configure-apps/file-schema/wcf/diagnostics.md) v části [ \<system.serviceModel>,](../../../configure-apps/file-schema/wcf/system-servicemodel.md) jak je znázorněno na následující ukázce konfigurace.</span><span class="sxs-lookup"><span data-stu-id="aa3ba-114">This is done through the `wmiProviderEnabled` attribute of the [\<diagnostics>](../../../configure-apps/file-schema/wcf/diagnostics.md) in the [\<system.serviceModel>](../../../configure-apps/file-schema/wcf/system-servicemodel.md) section, as shown in the following sample configuration.</span></span>  
  
```xml  
<system.serviceModel>  
    …  
    <diagnostics wmiProviderEnabled="true" />  
    …  
</system.serviceModel>  
```  
  
 <span data-ttu-id="aa3ba-115">Tato položka konfigurace zpřístupňuje rozhraní služby WMI.</span><span class="sxs-lookup"><span data-stu-id="aa3ba-115">This configuration entry exposes a WMI interface.</span></span> <span data-ttu-id="aa3ba-116">Aplikace pro správu se nyní mohou připojit prostřednictvím tohoto rozhraní a získat přístup k nástroji pro správu aplikace.</span><span class="sxs-lookup"><span data-stu-id="aa3ba-116">Management applications can now connect through this interface and access the management instrumentation of the application.</span></span>  
  
## <a name="accessing-wmi-data"></a><span data-ttu-id="aa3ba-117">Přístup k datům wmi</span><span class="sxs-lookup"><span data-stu-id="aa3ba-117">Accessing WMI Data</span></span>  
 <span data-ttu-id="aa3ba-118">K datům wmi lze přistupovat mnoha různými způsoby.</span><span class="sxs-lookup"><span data-stu-id="aa3ba-118">WMI data can be accessed in many different ways.</span></span> <span data-ttu-id="aa3ba-119">Společnost Microsoft poskytuje rozhraní WMI rozhraní API pro skripty, aplikace jazyka Visual Basic, aplikace jazyka C++ a rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="aa3ba-119">Microsoft provides WMI APIs for scripts, Visual Basic applications, C++ applications, and the .NET Framework.</span></span> <span data-ttu-id="aa3ba-120">Další informace naleznete [v tématu Using WMI](/windows/win32/wmisdk/using-wmi).</span><span class="sxs-lookup"><span data-stu-id="aa3ba-120">For more information, see [Using WMI](/windows/win32/wmisdk/using-wmi).</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="aa3ba-121">Pokud používáte metody .NET Framework k programovému přístupu k datům rozhraní WMI, měli byste si být vědomi toho, že tyto metody mohou při navázání připojení vyvolat výjimky.</span><span class="sxs-lookup"><span data-stu-id="aa3ba-121">If you use the .NET Framework provided methods to programmatically access WMI data, you should be aware that such methods may throw exceptions when the connection is established.</span></span> <span data-ttu-id="aa3ba-122">Připojení není navázáno během <xref:System.Management.ManagementObject> výstavby instance, ale na první žádost zahrnující skutečnou výměnu dat.</span><span class="sxs-lookup"><span data-stu-id="aa3ba-122">The connection is not established during the construction of the <xref:System.Management.ManagementObject> instance, but on the first request involving actual data exchange.</span></span> <span data-ttu-id="aa3ba-123">Proto byste měli `try..catch` použít blok zachytit možné výjimky.</span><span class="sxs-lookup"><span data-stu-id="aa3ba-123">Therefore, you should use a `try..catch` block to catch the possible exceptions.</span></span>  
  
 <span data-ttu-id="aa3ba-124">Můžete změnit úroveň trasování a protokolování zpráv, stejně jako možnosti protokolování zpráv pro zdroj `System.ServiceModel` trasování ve službě WMI.</span><span class="sxs-lookup"><span data-stu-id="aa3ba-124">You can change the trace and message logging level, as well as message logging options for the `System.ServiceModel` trace source in WMI.</span></span> <span data-ttu-id="aa3ba-125">To lze provést přístupem k instanci [AppDomainInfo,](appdomaininfo.md) která `LogMessagesAtServiceLevel`zpřístupňuje tyto logické vlastnosti: , `LogMessagesAtTransportLevel`, `LogMalformedMessages`a `TraceLevel`.</span><span class="sxs-lookup"><span data-stu-id="aa3ba-125">This can be done by accessing the [AppDomainInfo](appdomaininfo.md) instance, which exposes these Boolean properties: `LogMessagesAtServiceLevel`, `LogMessagesAtTransportLevel`, `LogMalformedMessages`, and `TraceLevel`.</span></span> <span data-ttu-id="aa3ba-126">Proto pokud nakonfigurujete naslouchací proces trasování pro protokolování zpráv, ale nastavte tyto možnosti v `false` konfiguraci, můžete je později změnit na `true` při spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="aa3ba-126">Therefore, if you configure a trace listener for message logging, but set these options to `false` in configuration, you can later change them to `true` when the application is running.</span></span> <span data-ttu-id="aa3ba-127">To efektivně umožní protokolování zpráv za běhu.</span><span class="sxs-lookup"><span data-stu-id="aa3ba-127">This will effectively enable message logging at runtime.</span></span> <span data-ttu-id="aa3ba-128">Podobně pokud povolíte protokolování zpráv v konfiguračním souboru, můžete jej zakázat za běhu pomocí služby WMI.</span><span class="sxs-lookup"><span data-stu-id="aa3ba-128">Similarly, if you enable message logging in your configuration file, you can disable it at runtime using WMI.</span></span>  
  
 <span data-ttu-id="aa3ba-129">Měli byste si být vědomi toho, že pokud žádné `System.ServiceModel` posluchače trasování protokolování zpráv pro protokolování zpráv nebo žádné posluchače trasování pro trasování jsou zadány v konfiguračním souboru, žádné změny jsou uvedeny v platnosti, i když změny jsou přijaty službou WMI.</span><span class="sxs-lookup"><span data-stu-id="aa3ba-129">You should be aware that if no message logging trace listeners for message logging, or no `System.ServiceModel` trace listeners for tracing are specified in the configuration file, none of your changes are taken into effect, even though the changes are accepted by WMI.</span></span> <span data-ttu-id="aa3ba-130">Další informace o správném nastavení příslušných naslouchacích procesů naleznete v [tématu Konfigurace protokolování zpráv](../configuring-message-logging.md) a [konfigurace trasování](../tracing/configuring-tracing.md)zpráv .</span><span class="sxs-lookup"><span data-stu-id="aa3ba-130">For more information on properly setting up the respective listeners, see [Configuring Message Logging](../configuring-message-logging.md) and [Configuring Tracing](../tracing/configuring-tracing.md).</span></span> <span data-ttu-id="aa3ba-131">Úroveň trasování všech ostatních zdrojů trasování určené konfigurace je účinná při spuštění aplikace a nelze ji změnit.</span><span class="sxs-lookup"><span data-stu-id="aa3ba-131">The trace level of all other trace sources specified by configuration is effective when the application starts, and cannot be changed.</span></span>  
  
 <span data-ttu-id="aa3ba-132">WCF zpřístupňuje metodu `GetOperationCounterInstanceName` pro skriptování.</span><span class="sxs-lookup"><span data-stu-id="aa3ba-132">WCF exposes a `GetOperationCounterInstanceName` method for scripting.</span></span> <span data-ttu-id="aa3ba-133">Tato metoda vrátí název instance čítače výkonu, pokud jí poskytnete název operace.</span><span class="sxs-lookup"><span data-stu-id="aa3ba-133">This method returns a performance counter instance name if you provide it with an operation name.</span></span> <span data-ttu-id="aa3ba-134">Však neověřuje vstup.</span><span class="sxs-lookup"><span data-stu-id="aa3ba-134">However, it does not validate your input.</span></span> <span data-ttu-id="aa3ba-135">Proto pokud zadáte nesprávný název operace, je vrácen nesprávný název čítače.</span><span class="sxs-lookup"><span data-stu-id="aa3ba-135">Therefore, if you provide an incorrect operation name, an incorrect counter name is returned.</span></span>  
  
 <span data-ttu-id="aa3ba-136">Vlastnost `OutgoingChannel` `Service` instance nepočítá kanály otevřené službou pro připojení k jiné službě, pokud klient WCF `Service` k cílové službě není vytvořen v rámci metody.</span><span class="sxs-lookup"><span data-stu-id="aa3ba-136">The `OutgoingChannel` property of the `Service` instance does not count channels opened by a service to connect to another service, if the WCF client to the destination service is not created within the `Service` method.</span></span>  
  
 <span data-ttu-id="aa3ba-137">**Pozor** Službu WMI <xref:System.TimeSpan> podporuje pouze hodnotu až 3 desetinné čárky.</span><span class="sxs-lookup"><span data-stu-id="aa3ba-137">**Caution** WMI only supports a <xref:System.TimeSpan> value up to 3 decimal points.</span></span> <span data-ttu-id="aa3ba-138">Pokud například služba nastaví jednu <xref:System.TimeSpan.MaxValue>ze svých vlastností na , bude její hodnota zkrácena po 3 desetinných bodech při zobrazení prostřednictvím služby WMI.</span><span class="sxs-lookup"><span data-stu-id="aa3ba-138">For example, if your service sets one of its properties to <xref:System.TimeSpan.MaxValue>, its value is truncated after 3 decimal points when viewed through WMI.</span></span>  
  
## <a name="security"></a><span data-ttu-id="aa3ba-139">Zabezpečení</span><span class="sxs-lookup"><span data-stu-id="aa3ba-139">Security</span></span>  
 <span data-ttu-id="aa3ba-140">Vzhledem k tomu, že zprostředkovatel WMI WCF umožňuje zjišťování služeb v prostředí, měli byste být velmi opatrní při udělování přístupu k němu.</span><span class="sxs-lookup"><span data-stu-id="aa3ba-140">Because the WCF WMI provider allows the discovery of services in an environment, you should exercise extreme caution for granting access to it.</span></span> <span data-ttu-id="aa3ba-141">Pokud uvolníte výchozí přístup pouze pro správce, můžete méně důvěryhodným stranám povolit přístup k citlivým datům ve vašem prostředí.</span><span class="sxs-lookup"><span data-stu-id="aa3ba-141">If you relax the default administrator-only access, you may allow less-trusted parties access to sensitive data in your environment.</span></span> <span data-ttu-id="aa3ba-142">Konkrétně pokud uvolníte oprávnění pro vzdálený přístup služby WMI, může dojít k zaplavujícím útokům.</span><span class="sxs-lookup"><span data-stu-id="aa3ba-142">Specifically, if you loosen permissions on remote WMI access, flooding attacks can occur.</span></span> <span data-ttu-id="aa3ba-143">Pokud je proces zaplaven nadměrnými požadavky služby WMI, může být jeho výkon snížen.</span><span class="sxs-lookup"><span data-stu-id="aa3ba-143">If a process is flooded by excessive WMI requests, its performance can be degraded.</span></span>  
  
 <span data-ttu-id="aa3ba-144">Pokud navíc uvolníte přístupová oprávnění pro soubor MOF, méně důvěryhodné strany mohou manipulovat s chováním systému WMI a měnit objekty načtené do schématu systému WMI.</span><span class="sxs-lookup"><span data-stu-id="aa3ba-144">In addition, if you relax access permissions for the MOF file, less-trusted parties can manipulate the behavior of WMI and alter the objects that are loaded in the WMI schema.</span></span> <span data-ttu-id="aa3ba-145">Pole lze například odebrat tak, aby byla před správcem skryta kritická data nebo aby byla do souboru přidána pole, která nenaplňují nebo nezpůsobují výjimky.</span><span class="sxs-lookup"><span data-stu-id="aa3ba-145">For example, fields can be removed such that critical data is concealed from the administrator or that fields that do not populate or cause exceptions are added to the file.</span></span>  
  
 <span data-ttu-id="aa3ba-146">Ve výchozím nastavení uděluje zprostředkovatel wmi wmi oprávnění "metoda spuštění", "zápis zprostředkovatele" a oprávnění "povolit účet" pro správce a oprávnění "povolit účet" pro ASP.NET, místní služby a síťové služby.</span><span class="sxs-lookup"><span data-stu-id="aa3ba-146">By default, the WCF WMI provider grants "execute method", "provider write", and "enable account" permission for Administrator, and "enable account" permission for ASP.NET, Local Service and Network Service.</span></span> <span data-ttu-id="aa3ba-147">Zejména na platformách, které nejsou platformami systému Windows Vista, má účet ASP.NET přístup pro čtení do oboru názvů WMI ServiceModel.</span><span class="sxs-lookup"><span data-stu-id="aa3ba-147">In particular, on non-Windows Vista platforms, the ASP.NET account has read access to the WMI ServiceModel namespace.</span></span> <span data-ttu-id="aa3ba-148">Pokud nechcete udělit tato oprávnění určité skupině uživatelů, měli byste buď deaktivovat zprostředkovatele služby WMI (ve výchozím nastavení je zakázáno), nebo zakázat přístup pro konkrétní skupinu uživatelů.</span><span class="sxs-lookup"><span data-stu-id="aa3ba-148">If you do not want to grant these privileges to a particular user group, you should either deactivate the WMI provider (it is disabled by default), or disable access for the specific user group.</span></span>  
  
 <span data-ttu-id="aa3ba-149">Pokud se navíc pokusíte povolit službu WMI prostřednictvím konfigurace, služba WMI nemusí být povolena z důvodu nedostatečných uživatelských oprávnění.</span><span class="sxs-lookup"><span data-stu-id="aa3ba-149">In addition, when you attempt to enable WMI through configuration, WMI may not be enabled due to insufficient user privilege.</span></span> <span data-ttu-id="aa3ba-150">Do protokolu událostí však není zapsána žádná událost, která by tuto chybu zaznamenala.</span><span class="sxs-lookup"><span data-stu-id="aa3ba-150">However, no event is written to the event log to record this failure.</span></span>  
  
 <span data-ttu-id="aa3ba-151">Chcete-li upravit úrovně uživatelských oprávnění, použijte následující kroky.</span><span class="sxs-lookup"><span data-stu-id="aa3ba-151">To modify user privilege levels, use the following steps.</span></span>  
  
1. <span data-ttu-id="aa3ba-152">Klepněte na tlačítko Start a potom na příkaz Spustit a zadejte **příkaz compmgmt.msc**.</span><span class="sxs-lookup"><span data-stu-id="aa3ba-152">Click Start and then Run and type **compmgmt.msc**.</span></span>  
  
2. <span data-ttu-id="aa3ba-153">Klepnutím pravým tlačítkem myši na **položku Služby a ovládací prvky aplikace/služby WMI** vyberte příkaz **Vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="aa3ba-153">Right-click **Services and Application/WMI Controls** to select **Properties**.</span></span>  
  
3. <span data-ttu-id="aa3ba-154">Vyberte kartu **Zabezpečení** a přejděte do oboru názvů **Root/ServiceModel.**</span><span class="sxs-lookup"><span data-stu-id="aa3ba-154">Select the **Security** Tab, and navigate to the **Root/ServiceModel** namespace.</span></span> <span data-ttu-id="aa3ba-155">Klepněte na tlačítko **Zabezpečení.**</span><span class="sxs-lookup"><span data-stu-id="aa3ba-155">Click the **Security** button.</span></span>  
  
4. <span data-ttu-id="aa3ba-156">Vyberte konkrétní skupinu nebo uživatele, u kterého chcete řídit přístup, a pomocí zaškrtávacího políčka **Povolit** nebo **Odepřít** nakonfigurujte oprávnění.</span><span class="sxs-lookup"><span data-stu-id="aa3ba-156">Select the specific group or user that you want to control access and use the **Allow** or **Deny** checkbox to configure permissions.</span></span>  
  
## <a name="granting-wcf-wmi-registration-permissions-to-additional-users"></a><span data-ttu-id="aa3ba-157">Udělení oprávnění k registraci wmi wmi dalším uživatelům</span><span class="sxs-lookup"><span data-stu-id="aa3ba-157">Granting WCF WMI Registration Permissions to Additional Users</span></span>  
 <span data-ttu-id="aa3ba-158">WCF zpřístupňuje data správy do wmi.</span><span class="sxs-lookup"><span data-stu-id="aa3ba-158">WCF exposes management data to WMI.</span></span> <span data-ttu-id="aa3ba-159">Činí tak hostováním v procesu zprostředkovatele služby WMI, někdy nazývaného "oddělený zprostředkovatel".</span><span class="sxs-lookup"><span data-stu-id="aa3ba-159">It does so by hosting an in-process WMI provider, sometimes called a "decoupled provider".</span></span> <span data-ttu-id="aa3ba-160">Aby byla data správy vystavena, musí mít účet, který registruje tohoto zprostředkovatele, příslušná oprávnění.</span><span class="sxs-lookup"><span data-stu-id="aa3ba-160">For the management data to be exposed, the account that registers this provider must have the appropriate permissions.</span></span> <span data-ttu-id="aa3ba-161">V systému Windows může ve výchozím nastavení zaregistrovat oddělené zprostředkovatele pouze malá sada privilegovaných účtů.</span><span class="sxs-lookup"><span data-stu-id="aa3ba-161">In Windows, only a small set of privileged accounts can register decoupled providers by default.</span></span> <span data-ttu-id="aa3ba-162">Jedná se o problém, protože uživatelé obvykle chtějí vystavit data služby WMI ze služby WCF spuštěné pod účtem, který není ve výchozí sadě.</span><span class="sxs-lookup"><span data-stu-id="aa3ba-162">This is a problem because users commonly want to expose WMI data from a WCF service running under an account that is not in the default set.</span></span>  
  
 <span data-ttu-id="aa3ba-163">Chcete-li tento přístup poskytnout, musí správce udělit další účet následující oprávnění v následujícím pořadí:</span><span class="sxs-lookup"><span data-stu-id="aa3ba-163">To provide this access, an administrator must grant the following permissions to the additional account in the following order:</span></span>  
  
1. <span data-ttu-id="aa3ba-164">Oprávnění k přístupu k oboru názvů WCF WMI.</span><span class="sxs-lookup"><span data-stu-id="aa3ba-164">Permission to access to the WCF WMI Namespace.</span></span>  
  
2. <span data-ttu-id="aa3ba-165">Oprávnění k registraci zprostředkovatele wcf odděleného zprostředkovatele služby WMI.</span><span class="sxs-lookup"><span data-stu-id="aa3ba-165">Permission to register the WCF Decoupled WMI Provider.</span></span>  
  
#### <a name="to-grant-wmi-namespace-access-permission"></a><span data-ttu-id="aa3ba-166">Udělení oprávnění k přístupu k oboru názvů wmi</span><span class="sxs-lookup"><span data-stu-id="aa3ba-166">To grant WMI namespace access permission</span></span>  
  
1. <span data-ttu-id="aa3ba-167">Spusťte následující skript prostředí PowerShell.</span><span class="sxs-lookup"><span data-stu-id="aa3ba-167">Run the following PowerShell script.</span></span>  
  
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
  
     <span data-ttu-id="aa3ba-168">Tento skript prostředí PowerShell používá jazyk definice popisovače zabezpečení (SDDL) k udělení přístupu skupiny Předdefinovaných uživatelů k oboru názvů WMI "root/servicemodel".</span><span class="sxs-lookup"><span data-stu-id="aa3ba-168">This PowerShell script uses Security Descriptor Definition Language (SDDL) to grant the Built-In Users group access to the "root/servicemodel" WMI namespace.</span></span> <span data-ttu-id="aa3ba-169">Určuje následující seznamy ACL:</span><span class="sxs-lookup"><span data-stu-id="aa3ba-169">It specifies the following ACLs:</span></span>  
  
    - <span data-ttu-id="aa3ba-170">Vestavěný správce (BA) - již měl přístup.</span><span class="sxs-lookup"><span data-stu-id="aa3ba-170">Built-In Administrator (BA) - Already Had Access.</span></span>  
  
    - <span data-ttu-id="aa3ba-171">Síťová služba (NS) - již měla přístup.</span><span class="sxs-lookup"><span data-stu-id="aa3ba-171">Network Service (NS) - Already Had Access.</span></span>  
  
    - <span data-ttu-id="aa3ba-172">Místní systém (LS) - již měl přístup.</span><span class="sxs-lookup"><span data-stu-id="aa3ba-172">Local System (LS) - Already Had Access.</span></span>  
  
    - <span data-ttu-id="aa3ba-173">Předdefinované uživatelé – skupina, ke které má být přístup.</span><span class="sxs-lookup"><span data-stu-id="aa3ba-173">Built-In Users - The group to grant access to.</span></span>  
  
#### <a name="to-grant-provider-registration-access"></a><span data-ttu-id="aa3ba-174">Udělení přístupu k registraci zprostředkovatele</span><span class="sxs-lookup"><span data-stu-id="aa3ba-174">To grant provider registration access</span></span>  
  
1. <span data-ttu-id="aa3ba-175">Spusťte následující skript prostředí PowerShell.</span><span class="sxs-lookup"><span data-stu-id="aa3ba-175">Run the following PowerShell script.</span></span>  
  
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
  
### <a name="granting-access-to-arbitrary-users-or-groups"></a><span data-ttu-id="aa3ba-176">Udělení přístupu libovolným uživatelům nebo skupinám</span><span class="sxs-lookup"><span data-stu-id="aa3ba-176">Granting Access to Arbitrary Users or Groups</span></span>  
 <span data-ttu-id="aa3ba-177">Příklad v této části uděluje oprávnění k registraci zprostředkovatele služby WMI všem místním uživatelům.</span><span class="sxs-lookup"><span data-stu-id="aa3ba-177">The example in this section grants WMI Provider registration privileges to all local users.</span></span> <span data-ttu-id="aa3ba-178">Pokud chcete udělit přístup k uživateli nebo skupině, která není integrovaná, musíte získat identifikátor zabezpečení tohoto uživatele nebo skupiny (SID).</span><span class="sxs-lookup"><span data-stu-id="aa3ba-178">If you want to grant access to a user or group that is not built in, then you must obtain that user or group's Security Identifier (SID).</span></span> <span data-ttu-id="aa3ba-179">Neexistuje žádný jednoduchý způsob, jak získat SID pro libovolného uživatele.</span><span class="sxs-lookup"><span data-stu-id="aa3ba-179">There is no simple way to get the SID for an arbitrary user.</span></span> <span data-ttu-id="aa3ba-180">Jednou z metod je přihlásit se jako požadovaný uživatel a potom vydat následující příkaz prostředí.</span><span class="sxs-lookup"><span data-stu-id="aa3ba-180">One method is to log on as the desired user and then issue the following shell command.</span></span>  
  
```console
Whoami /user  
```  
  
 <span data-ttu-id="aa3ba-181">To poskytuje SID aktuálního uživatele, ale tuto metodu nelze použít k získání SID na libovolný uživatel.</span><span class="sxs-lookup"><span data-stu-id="aa3ba-181">This provides the SID of the current user, but this method cannot be used to get the SID on any arbitrary user.</span></span> <span data-ttu-id="aa3ba-182">Další metodou získání sid je použití nástroje [getsid.exe](/windows/win32/wmisdk/using-wmi) z nástrojů sady Windows 2000 Resource Kit pro úkoly správy.</span><span class="sxs-lookup"><span data-stu-id="aa3ba-182">Another method to get the SID is to use the [getsid.exe](/windows/win32/wmisdk/using-wmi) tool from the Windows 2000 Resource Kit Tools for administrative tasks.</span></span> <span data-ttu-id="aa3ba-183">Tento nástroj porovnává SID dvou uživatelů (místní nebo domény) a jako vedlejší efekt vytiskne dva SID s příkazovým řádkem.</span><span class="sxs-lookup"><span data-stu-id="aa3ba-183">This tool compares the SID of two users (local or domain), and as a side effect prints the two SIDs to the command line.</span></span> <span data-ttu-id="aa3ba-184">Další informace naleznete v [tématu Známé SID](https://support.microsoft.com/help/243330/well-known-security-identifiers-in-windows-operating-systems).</span><span class="sxs-lookup"><span data-stu-id="aa3ba-184">For more information, see [Well Known SIDs](https://support.microsoft.com/help/243330/well-known-security-identifiers-in-windows-operating-systems).</span></span>  
  
## <a name="accessing-remote-wmi-object-instances"></a><span data-ttu-id="aa3ba-185">Přístup ke vzdáleným instancím objektů služby WMI</span><span class="sxs-lookup"><span data-stu-id="aa3ba-185">Accessing Remote WMI Object Instances</span></span>  
 <span data-ttu-id="aa3ba-186">Pokud potřebujete přístup k instancíw WMI WCF ve vzdáleném počítači, musíte povolit ochranu osobních údajů paketů v nástrojích, které používáte pro přístup.</span><span class="sxs-lookup"><span data-stu-id="aa3ba-186">If you need to access WCF WMI instances on a remote machine, you must enable packet privacy on the tools that you use for access.</span></span> <span data-ttu-id="aa3ba-187">Následující část popisuje, jak jich dosáhnout pomocí wmi CIM Studio, Windows Management Instrumentation Tester a .NET SDK 2.0.</span><span class="sxs-lookup"><span data-stu-id="aa3ba-187">The following section describes how to achieve these using the WMI CIM Studio, Windows Management Instrumentation Tester, as well as .NET SDK 2.0.</span></span>  
  
### <a name="wmi-cim-studio"></a><span data-ttu-id="aa3ba-188">WMI CIM Studio</span><span class="sxs-lookup"><span data-stu-id="aa3ba-188">WMI CIM Studio</span></span>

<span data-ttu-id="aa3ba-189">Pokud jste nainstalovali nástroje pro správu služby WMI, můžete k instancím služby WMI použít aplikaci WMI CIM Studio.</span><span class="sxs-lookup"><span data-stu-id="aa3ba-189">If you've installed WMI Administrative Tools, you can use the WMI CIM Studio to access WMI instances.</span></span> <span data-ttu-id="aa3ba-190">Nástroje jsou v následující složce:</span><span class="sxs-lookup"><span data-stu-id="aa3ba-190">The tools are in the following folder:</span></span>
  
<span data-ttu-id="aa3ba-191">*%windir%\Program Files\Nástroje WMI\\*</span><span class="sxs-lookup"><span data-stu-id="aa3ba-191">*%windir%\Program Files\WMI Tools\\*</span></span>
  
1. <span data-ttu-id="aa3ba-192">V okně **Připojit k oboru názvů:** zadejte **root\ServiceModel** a klepněte na **tlačítko OK.**</span><span class="sxs-lookup"><span data-stu-id="aa3ba-192">In the **Connect to namespace:** window, type **root\ServiceModel** and click **OK.**</span></span>  
  
2. <span data-ttu-id="aa3ba-193">V okně **Přihlášení aplikace WMI CIM Studio** rozbalte okno klepnutím na tlačítko **Možnosti >>.**</span><span class="sxs-lookup"><span data-stu-id="aa3ba-193">In the **WMI CIM Studio Login** window, click the **Options >>** button to expand the window.</span></span> <span data-ttu-id="aa3ba-194">Vyberte **úroveň ochrany osobních údajů paketů** pro **ověřování**a klepněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="aa3ba-194">Select **Packet privacy** for **Authentication level**, and click **OK**.</span></span>  
  
### <a name="windows-management-instrumentation-tester"></a><span data-ttu-id="aa3ba-195">Tester pro správu systému Windows</span><span class="sxs-lookup"><span data-stu-id="aa3ba-195">Windows Management Instrumentation Tester</span></span>  
 <span data-ttu-id="aa3ba-196">Tento nástroj je nainstalován systémem Windows.</span><span class="sxs-lookup"><span data-stu-id="aa3ba-196">This tool is installed by Windows.</span></span> <span data-ttu-id="aa3ba-197">Chcete-li ji spustit, spusťte konzolu příkazů zadáním příkazu **cmd.exe** v dialogovém okně **Start/Spustit** a klepněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="aa3ba-197">To run it, launch a command console by typing **cmd.exe** in the **Start/Run** dialog box and click **OK**.</span></span> <span data-ttu-id="aa3ba-198">Potom zadejte **wbemtest.exe** v příkazovém okně.</span><span class="sxs-lookup"><span data-stu-id="aa3ba-198">Then, type **wbemtest.exe** in the command window.</span></span> <span data-ttu-id="aa3ba-199">Poté je spuštěn nástroj Windows Management Instrumentation Tester.</span><span class="sxs-lookup"><span data-stu-id="aa3ba-199">The Windows Management Instrumentation Tester tool is then launched.</span></span>  
  
1. <span data-ttu-id="aa3ba-200">Klikněte na tlačítko **Připojit** v pravém horním rohu okna.</span><span class="sxs-lookup"><span data-stu-id="aa3ba-200">Click the **Connect** button on the top right corner of the window.</span></span>  
  
2. <span data-ttu-id="aa3ba-201">V novém okně zadejte **root\ServiceModel** pro pole **Obor názvů** a vyberte úroveň **ochrany osobních údajů paketů** pro **ověřování**.</span><span class="sxs-lookup"><span data-stu-id="aa3ba-201">In the new window, enter **root\ServiceModel** for the **Namespace** field, and select **Packet privacy** for **Authentication level**.</span></span> <span data-ttu-id="aa3ba-202">Klikněte na **Připojit**.</span><span class="sxs-lookup"><span data-stu-id="aa3ba-202">Click **Connect**.</span></span>  
  
### <a name="using-managed-code"></a><span data-ttu-id="aa3ba-203">Použití spravovaného kódu</span><span class="sxs-lookup"><span data-stu-id="aa3ba-203">Using Managed Code</span></span>  
 <span data-ttu-id="aa3ba-204">Ke vzdáleným instancím služby WMI můžete také <xref:System.Management> přistupovat programově pomocí tříd poskytovaných oborem názvů.</span><span class="sxs-lookup"><span data-stu-id="aa3ba-204">You can also access remote WMI instances programmatically by using classes provided by the <xref:System.Management> namespace.</span></span> <span data-ttu-id="aa3ba-205">Následující ukázka kódu ukazuje, jak to provést.</span><span class="sxs-lookup"><span data-stu-id="aa3ba-205">The following code sample demonstrates how to do this.</span></span>  
  
```csharp
String wcfNamespace = $@"\\{this.serviceMachineName}\Root\ServiceModel");
  
ConnectionOptions connection = new ConnectionOptions();  
connection.Authentication = AuthenticationLevel.PacketPrivacy;  
ManagementScope scope = new ManagementScope(this.wcfNamespace, connection);  
```
