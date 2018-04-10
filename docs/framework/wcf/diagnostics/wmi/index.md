---
title: Diagnostika prostřednictvím rozhraní WMI (Windows Management Instrumentation)
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fe48738d-e31b-454d-b5ec-24c85c6bf79a
caps.latest.revision: 24
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 0862f747cb969a6aa2e63d86e842097260e95b56
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="using-windows-management-instrumentation-for-diagnostics"></a><span data-ttu-id="b9d9d-102">Diagnostika prostřednictvím rozhraní WMI (Windows Management Instrumentation)</span><span class="sxs-lookup"><span data-stu-id="b9d9d-102">Using Windows Management Instrumentation for Diagnostics</span></span>
[!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]<span data-ttu-id="b9d9d-103">zpřístupní dat kontroly služby za běhu prostřednictvím [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] zprostředkovatele Windows Management Instrumentation (WMI).</span><span class="sxs-lookup"><span data-stu-id="b9d9d-103"> exposes inspection data of a service at runtime through a [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] Windows Management Instrumentation (WMI) provider.</span></span>  
  
## <a name="enabling-wmi"></a><span data-ttu-id="b9d9d-104">Povolení služby WMI</span><span class="sxs-lookup"><span data-stu-id="b9d9d-104">Enabling WMI</span></span>  
 <span data-ttu-id="b9d9d-105">Služba WMI je implementace Web-Based Enterprise Management (WBEM) standardní společnosti Microsoft.</span><span class="sxs-lookup"><span data-stu-id="b9d9d-105">WMI is Microsoft's implementation of the Web-Based Enterprise Management (WBEM) standard.</span></span> [!INCLUDE[crabout](../../../../../includes/crabout-md.md)]<span data-ttu-id="b9d9d-106">Sada SDK rozhraní WMI najdete v části [Windows Management Instrumentation](https://msdn.microsoft.com/library/aa394582.aspx).</span><span class="sxs-lookup"><span data-stu-id="b9d9d-106"> the WMI SDK, see [Windows Management Instrumentation](https://msdn.microsoft.com/library/aa394582.aspx).</span></span> <span data-ttu-id="b9d9d-107">WBEM je oborový standard pro jak aplikace vystavit WMI pro externí nástroje pro správu.</span><span class="sxs-lookup"><span data-stu-id="b9d9d-107">WBEM is an industry standard for how applications expose management instrumentation to external management tools.</span></span>  
  
 <span data-ttu-id="b9d9d-108">Zprostředkovatel rozhraní WMI je součást, která zveřejňuje instrumentace za běhu prostřednictvím rozhraní WBEM kompatibilní.</span><span class="sxs-lookup"><span data-stu-id="b9d9d-108">A WMI provider is a component that exposes instrumentation at runtime through a WBEM-compatible interface.</span></span> <span data-ttu-id="b9d9d-109">Obsahuje sadu objektů rozhraní WMI, které mají dvojice atribut hodnota.</span><span class="sxs-lookup"><span data-stu-id="b9d9d-109">It consists of a set of WMI objects that have attribute/value pairs.</span></span> <span data-ttu-id="b9d9d-110">Dvojice může mít několik jednoduchých typů.</span><span class="sxs-lookup"><span data-stu-id="b9d9d-110">Pairs can be of a number of simple types.</span></span> <span data-ttu-id="b9d9d-111">Nástroje pro správu můžete připojit ke službám prostřednictvím rozhraní za běhu.</span><span class="sxs-lookup"><span data-stu-id="b9d9d-111">Management tools can connect to the services through the interface at runtime.</span></span> [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)]<span data-ttu-id="b9d9d-112">zpřístupní atributy služeb, jako je adresy, vazby, chování a naslouchací procesy.</span><span class="sxs-lookup"><span data-stu-id="b9d9d-112"> exposes attributes of services such as addresses, bindings, behaviors, and listeners.</span></span>  
  
 <span data-ttu-id="b9d9d-113">Předdefinované zprostředkovatele rozhraní WMI je možné aktivovat v konfiguračním souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="b9d9d-113">The built-in WMI provider can be activated in the configuration file of the application.</span></span> <span data-ttu-id="b9d9d-114">To se provádí prostřednictvím `wmiProviderEnabled` atribut [ \<diagnostics >](../../../../../docs/framework/configure-apps/file-schema/wcf/diagnostics.md) v [ \<system.serviceModel >](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) části, jak znázorňuje následující ukázka konfigurace.</span><span class="sxs-lookup"><span data-stu-id="b9d9d-114">This is done through the `wmiProviderEnabled` attribute of the [\<diagnostics>](../../../../../docs/framework/configure-apps/file-schema/wcf/diagnostics.md) in the [\<system.serviceModel>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) section, as shown in the following sample configuration.</span></span>  
  
```xml  
<system.serviceModel>  
    …  
    <diagnostics wmiProviderEnabled="true" />  
    …  
</system.serviceModel>  
```  
  
 <span data-ttu-id="b9d9d-115">Tato položka konfigurace vystavuje rozhraní WMI.</span><span class="sxs-lookup"><span data-stu-id="b9d9d-115">This configuration entry exposes a WMI interface.</span></span> <span data-ttu-id="b9d9d-116">Aplikace pro správu teď můžete připojit přes toto rozhraní a přístup WMI aplikace.</span><span class="sxs-lookup"><span data-stu-id="b9d9d-116">Management applications can now connect through this interface and access the management instrumentation of the application.</span></span>  
  
## <a name="accessing-wmi-data"></a><span data-ttu-id="b9d9d-117">Přístup k datům rozhraní WMI</span><span class="sxs-lookup"><span data-stu-id="b9d9d-117">Accessing WMI Data</span></span>  
 <span data-ttu-id="b9d9d-118">Data rozhraní WMI je přístupná v mnoha různými způsoby.</span><span class="sxs-lookup"><span data-stu-id="b9d9d-118">WMI data can be accessed in many different ways.</span></span> <span data-ttu-id="b9d9d-119">Společnost Microsoft poskytuje rozhraní API služby WMI pro skripty, [!INCLUDE[vbprvb](../../../../../includes/vbprvb-md.md)] aplikace, aplikace C++ a [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b9d9d-119">Microsoft provides WMI APIs for scripts, [!INCLUDE[vbprvb](../../../../../includes/vbprvb-md.md)] applications, C++ applications, and the [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)].</span></span> <span data-ttu-id="b9d9d-120">Další informace najdete v tématu [pomocí rozhraní WMI](http://go.microsoft.com/fwlink/?LinkId=95183).</span><span class="sxs-lookup"><span data-stu-id="b9d9d-120">For more information, see [Using WMI](http://go.microsoft.com/fwlink/?LinkId=95183).</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="b9d9d-121">Pokud používáte rozhraní .NET Framework poskytuje metody pro přístup programu ke dat služby WMI, byste měli vědět, že tyto metody může vyvolat výjimky při připojení.</span><span class="sxs-lookup"><span data-stu-id="b9d9d-121">If you use the .NET Framework provided methods to programmatically access WMI data, you should be aware that such methods may throw exceptions when the connection is established.</span></span> <span data-ttu-id="b9d9d-122">Během vytváření služby nebude navázáno připojení <xref:System.Management.ManagementObject> instanci, ale v prvním požadavku zahrnující exchange skutečná data.</span><span class="sxs-lookup"><span data-stu-id="b9d9d-122">The connection is not established during the construction of the <xref:System.Management.ManagementObject> instance, but on the first request involving actual data exchange.</span></span> <span data-ttu-id="b9d9d-123">Proto byste měli používat `try..catch` bloku k zachycení možné výjimky.</span><span class="sxs-lookup"><span data-stu-id="b9d9d-123">Therefore, you should use a `try..catch` block to catch the possible exceptions.</span></span>  
  
 <span data-ttu-id="b9d9d-124">Můžete změnit na trasování a úroveň protokolování zpráv, a také možnosti protokolování zpráv pro `System.ServiceModel` zdroj trasování v rozhraní WMI.</span><span class="sxs-lookup"><span data-stu-id="b9d9d-124">You can change the trace and message logging level, as well as message logging options for the `System.ServiceModel` trace source in WMI.</span></span> <span data-ttu-id="b9d9d-125">To lze provést pomocí přístupu k [AppDomainInfo](../../../../../docs/framework/wcf/diagnostics/wmi/appdomaininfo.md) instanci, která zpřístupňuje tyto logická hodnota vlastnosti: `LogMessagesAtServiceLevel`, `LogMessagesAtTransportLevel`, `LogMalformedMessages`, a `TraceLevel`.</span><span class="sxs-lookup"><span data-stu-id="b9d9d-125">This can be done by accessing the [AppDomainInfo](../../../../../docs/framework/wcf/diagnostics/wmi/appdomaininfo.md) instance, which exposes these Boolean properties: `LogMessagesAtServiceLevel`, `LogMessagesAtTransportLevel`, `LogMalformedMessages`, and `TraceLevel`.</span></span> <span data-ttu-id="b9d9d-126">Proto pokud nakonfigurujete naslouchací proces trasování pro protokolování zpráv, ale nastavit tyto možnosti pro `false` v konfiguraci, můžete později změnit, aby `true` při spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="b9d9d-126">Therefore, if you configure a trace listener for message logging, but set these options to `false` in configuration, you can later change them to `true` when the application is running.</span></span> <span data-ttu-id="b9d9d-127">Efektivně tím povolíte protokolování zpráv za běhu.</span><span class="sxs-lookup"><span data-stu-id="b9d9d-127">This will effectively enable message logging at runtime.</span></span> <span data-ttu-id="b9d9d-128">Podobně pokud povolíte protokolování v konfiguračním souboru zpráv, ji můžete vypnout v době běhu pomocí služby WMI.</span><span class="sxs-lookup"><span data-stu-id="b9d9d-128">Similarly, if you enable message logging in your configuration file, you can disable it at runtime using WMI.</span></span>  
  
 <span data-ttu-id="b9d9d-129">Je třeba si uvědomit, že pokud žádné protokolování zpráv trasování – moduly naslouchání pro protokolování zpráv nebo Ne `System.ServiceModel` trasování – moduly naslouchání pro trasování jsou zadané v konfiguračním souboru, změny jsou přijata žádná platit, i když přijímat změny jsou rozhraní WMI.</span><span class="sxs-lookup"><span data-stu-id="b9d9d-129">You should be aware that if no message logging trace listeners for message logging, or no `System.ServiceModel` trace listeners for tracing are specified in the configuration file, none of your changes are taken into effect, even though the changes are accepted by WMI.</span></span> <span data-ttu-id="b9d9d-130">Další informace o správné nastavení příslušných naslouchací procesy najdete v tématu [konfigurace protokolování zpráv](../../../../../docs/framework/wcf/diagnostics/configuring-message-logging.md) a [Konfigurace trasování](../../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md).</span><span class="sxs-lookup"><span data-stu-id="b9d9d-130">For more information on properly setting up the respective listeners, see [Configuring Message Logging](../../../../../docs/framework/wcf/diagnostics/configuring-message-logging.md) and [Configuring Tracing](../../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md).</span></span> <span data-ttu-id="b9d9d-131">Úroveň trasování ze všech ostatních zdrojů trasování zadáno v konfiguraci je platná, když se aplikace spustí a nelze je změnit.</span><span class="sxs-lookup"><span data-stu-id="b9d9d-131">The trace level of all other trace sources specified by configuration is effective when the application starts, and cannot be changed.</span></span>  
  
 [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)]<span data-ttu-id="b9d9d-132">zpřístupní `GetOperationCounterInstanceName` metoda pro skriptování.</span><span class="sxs-lookup"><span data-stu-id="b9d9d-132"> exposes a `GetOperationCounterInstanceName` method for scripting.</span></span> <span data-ttu-id="b9d9d-133">Tato metoda vrátí název instance čítače výkonu, pokud jste zadali s názvem operaci.</span><span class="sxs-lookup"><span data-stu-id="b9d9d-133">This method returns a performance counter instance name if you provide it with an operation name.</span></span> <span data-ttu-id="b9d9d-134">Neověřuje však váš vstup.</span><span class="sxs-lookup"><span data-stu-id="b9d9d-134">However, it does not validate your input.</span></span> <span data-ttu-id="b9d9d-135">Proto pokud zadáte název nesprávný operace, je vrácen název nesprávné čítače.</span><span class="sxs-lookup"><span data-stu-id="b9d9d-135">Therefore, if you provide an incorrect operation name, an incorrect counter name is returned.</span></span>  
  
 <span data-ttu-id="b9d9d-136">`OutgoingChannel` Vlastnost `Service` instance nepočítá kanály otevřít službou se připojit k jiné službě, pokud [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] klienta do cílové služby není vytvořena v rámci `Service` metoda.</span><span class="sxs-lookup"><span data-stu-id="b9d9d-136">The `OutgoingChannel` property of the `Service` instance does not count channels opened by a service to connect to another service, if the [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] client to the destination service is not created within the `Service` method.</span></span>  
  
 <span data-ttu-id="b9d9d-137">**Upozornění:** podporuje pouze rozhraní WMI <xref:System.TimeSpan> hodnotu až 3 desetinných míst.</span><span class="sxs-lookup"><span data-stu-id="b9d9d-137">**Caution** WMI only supports a <xref:System.TimeSpan> value up to 3 decimal points.</span></span> <span data-ttu-id="b9d9d-138">Například, pokud vaše služba nastaví její vlastnosti, aby <xref:System.TimeSpan.MaxValue>, jeho hodnota se zkrátí po 3 desetinných míst, při zobrazení v rozhraní WMI.</span><span class="sxs-lookup"><span data-stu-id="b9d9d-138">For example, if your service sets one of its properties to <xref:System.TimeSpan.MaxValue>, its value is truncated after 3 decimal points when viewed through WMI.</span></span>  
  
## <a name="security"></a><span data-ttu-id="b9d9d-139">Zabezpečení</span><span class="sxs-lookup"><span data-stu-id="b9d9d-139">Security</span></span>  
 <span data-ttu-id="b9d9d-140">Protože [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] zprostředkovatele rozhraní WMI umožňuje zjišťování služeb v prostředí, postupujte opatrně extrémně pro udělení přístupu k němu.</span><span class="sxs-lookup"><span data-stu-id="b9d9d-140">Because the [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] WMI provider allows the discovery of services in an environment, you should exercise extreme caution for granting access to it.</span></span> <span data-ttu-id="b9d9d-141">Pokud jste uvolnit výchozí přístup pouze správce, může povolit méně důvěryhodné strany přístup k citlivým datům ve vašem prostředí.</span><span class="sxs-lookup"><span data-stu-id="b9d9d-141">If you relax the default administrator-only access, you may allow less-trusted parties access to sensitive data in your environment.</span></span> <span data-ttu-id="b9d9d-142">Pokud jste povolte oprávnění pro vzdálený přístup k rozhraní WMI, konkrétně zahlcení útoky může dojít k.</span><span class="sxs-lookup"><span data-stu-id="b9d9d-142">Specifically, if you loosen permissions on remote WMI access, flooding attacks can occur.</span></span> <span data-ttu-id="b9d9d-143">Pokud proces je přetížené nadměrné požadavky rozhraní WMI, může docházet ke snížení jeho výkon.</span><span class="sxs-lookup"><span data-stu-id="b9d9d-143">If a process is flooded by excessive WMI requests, its performance can be degraded.</span></span>  
  
 <span data-ttu-id="b9d9d-144">Kromě toho pokud jste uvolnit přístupová oprávnění pro soubor MOF, méně důvěryhodné strany můžete upravit chování rozhraní WMI a měnit objekty, které jsou načteny ve schématu WMI.</span><span class="sxs-lookup"><span data-stu-id="b9d9d-144">In addition, if you relax access permissions for the MOF file, less-trusted parties can manipulate the behavior of WMI and alter the objects that are loaded in the WMI schema.</span></span> <span data-ttu-id="b9d9d-145">Například pole můžete odebrat tak, že je důležitá data zakryté od správce nebo pole, která naplnit nebo způsobit výjimky jsou přidány do souboru.</span><span class="sxs-lookup"><span data-stu-id="b9d9d-145">For example, fields can be removed such that critical data is concealed from the administrator or that fields that do not populate or cause exceptions are added to the file.</span></span>  
  
 <span data-ttu-id="b9d9d-146">Ve výchozím nastavení [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] zprostředkovatele rozhraní WMI uděluje "provést metodu", "zapisovat zprostředkovatele" a "Povolit účet" oprávnění pro správce a oprávnění "Povolit účet" pro ASP.NET, místní služby a síťové služby.</span><span class="sxs-lookup"><span data-stu-id="b9d9d-146">By default, the [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] WMI provider grants "execute method", "provider write", and "enable account" permission for Administrator, and "enable account" permission for ASP.NET, Local Service and Network Service.</span></span> <span data-ttu-id="b9d9d-147">Konkrétně na jinou hodnotu než[!INCLUDE[wv](../../../../../includes/wv-md.md)] platforem ASP.NET účtu má přístup pro čtení k oboru názvů WMI ServiceModel.</span><span class="sxs-lookup"><span data-stu-id="b9d9d-147">In particular, on non-[!INCLUDE[wv](../../../../../includes/wv-md.md)] platforms, the ASP.NET account has read access to the WMI ServiceModel namespace.</span></span> <span data-ttu-id="b9d9d-148">Pokud nechcete udělení těchto oprávnění určitou skupinu uživatelů, si deaktivovat zprostředkovatele rozhraní WMI (je zakázáno ve výchozím nastavení), nebo zakázat přístup pro určité uživatelské skupiny.</span><span class="sxs-lookup"><span data-stu-id="b9d9d-148">If you do not want to grant these privileges to a particular user group, you should either deactivate the WMI provider (it is disabled by default), or disable access for the specific user group.</span></span>  
  
 <span data-ttu-id="b9d9d-149">Kromě toho při pokusu o povolení rozhraní WMI prostřednictvím konfigurace není povolené rozhraní WMI z důvodu nedostatečných uživatelských oprávnění.</span><span class="sxs-lookup"><span data-stu-id="b9d9d-149">In addition, when you attempt to enable WMI through configuration, WMI may not be enabled due to insufficient user privilege.</span></span> <span data-ttu-id="b9d9d-150">Ale žádná událost se zapíše do protokolu událostí k zaznamenání této chyby.</span><span class="sxs-lookup"><span data-stu-id="b9d9d-150">However, no event is written to the event log to record this failure.</span></span>  
  
 <span data-ttu-id="b9d9d-151">Chcete-li upravit úrovně oprávnění uživatele, použijte následující kroky.</span><span class="sxs-lookup"><span data-stu-id="b9d9d-151">To modify user privilege levels, use the following steps.</span></span>  
  
1.  <span data-ttu-id="b9d9d-152">Klikněte na tlačítko Start a pak spusťte a zadejte **compmgmt.msc**.</span><span class="sxs-lookup"><span data-stu-id="b9d9d-152">Click Start and then Run and type **compmgmt.msc**.</span></span>  
  
2.  <span data-ttu-id="b9d9d-153">Klikněte pravým tlačítkem na **služby a aplikace/WMI ovládací prvky** vyberte **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="b9d9d-153">Right-click **Services and Application/WMI Controls** to select **Properties**.</span></span>  
  
3.  <span data-ttu-id="b9d9d-154">Vyberte **zabezpečení** kartě a přejděte do **kořenové nebo ServiceModel** oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="b9d9d-154">Select the **Security** Tab, and navigate to the **Root/ServiceModel** namespace.</span></span> <span data-ttu-id="b9d9d-155">Klikněte **zabezpečení** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="b9d9d-155">Click the **Security** button.</span></span>  
  
4.  <span data-ttu-id="b9d9d-156">Vyberte konkrétní skupinu nebo uživatele, který chcete řízení přístupu a použití **povolit** nebo **Odepřít** políčko konfigurace oprávnění.</span><span class="sxs-lookup"><span data-stu-id="b9d9d-156">Select the specific group or user that you want to control access and use the **Allow** or **Deny** checkbox to configure permissions.</span></span>  
  
## <a name="granting-wcf-wmi-registration-permissions-to-additional-users"></a><span data-ttu-id="b9d9d-157">Udělení oprávnění registrace služby WCF WMI dalším uživatelům</span><span class="sxs-lookup"><span data-stu-id="b9d9d-157">Granting WCF WMI Registration Permissions to Additional Users</span></span>  
 <span data-ttu-id="b9d9d-158">WCF zpřístupní data správy k rozhraní WMI.</span><span class="sxs-lookup"><span data-stu-id="b9d9d-158">WCF exposes management data to WMI.</span></span> <span data-ttu-id="b9d9d-159">Dělá to tak hostováním poskytovatele rozhraní WMI v procesu, někdy označuje jako "odpojeného zprostředkovatele".</span><span class="sxs-lookup"><span data-stu-id="b9d9d-159">It does so by hosting an in-process WMI provider, sometimes called a "decoupled provider".</span></span> <span data-ttu-id="b9d9d-160">Pro data správy, které mají být exponovány účet, který registruje tohoto zprostředkovatele musí mít příslušná oprávnění.</span><span class="sxs-lookup"><span data-stu-id="b9d9d-160">For the management data to be exposed, the account that registers this provider must have the appropriate permissions.</span></span> <span data-ttu-id="b9d9d-161">V systému Windows můžete pouze malého privilegovaných účtů zaregistrovat odpojeného zprostředkovatele ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="b9d9d-161">In Windows, only a small set of privileged accounts can register decoupled providers by default.</span></span> <span data-ttu-id="b9d9d-162">Tento problém je, protože uživatelé běžně chcete vystavit data rozhraní WMI ze služby WCF spuštěn pod účtem, který není v sadě výchozí.</span><span class="sxs-lookup"><span data-stu-id="b9d9d-162">This is a problem because users commonly want to expose WMI data from a WCF service running under an account that is not in the default set.</span></span>  
  
 <span data-ttu-id="b9d9d-163">Pokud chcete poskytnout tento přístup, musí správce udělit následující oprávnění k další účet v následujícím pořadí:</span><span class="sxs-lookup"><span data-stu-id="b9d9d-163">To provide this access, an administrator must grant the following permissions to the additional account in the following order:</span></span>  
  
1.  <span data-ttu-id="b9d9d-164">Oprávnění k přístupu k Namespace WMI WCF.</span><span class="sxs-lookup"><span data-stu-id="b9d9d-164">Permission to access to the WCF WMI Namespace.</span></span>  
  
2.  <span data-ttu-id="b9d9d-165">Oprávnění k registraci zprostředkovatele rozhraní WMI odpojené WCF.</span><span class="sxs-lookup"><span data-stu-id="b9d9d-165">Permission to register the WCF Decoupled WMI Provider.</span></span>  
  
#### <a name="to-grant-wmi-namespace-access-permission"></a><span data-ttu-id="b9d9d-166">Udělit oprávnění k oboru názvů rozhraní WMI</span><span class="sxs-lookup"><span data-stu-id="b9d9d-166">To grant WMI namespace access permission</span></span>  
  
1.  <span data-ttu-id="b9d9d-167">Spusťte následující skript prostředí PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b9d9d-167">Run the following PowerShell script.</span></span>  
  
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
  
     <span data-ttu-id="b9d9d-168">Tento skript prostředí PowerShell používá zabezpečení SDDL Descriptor Definition Language () k udělení přístupu skupiny předdefinované uživatelé k oboru názvů WMI "kořenový/servicemodel".</span><span class="sxs-lookup"><span data-stu-id="b9d9d-168">This PowerShell script uses Security Descriptor Definition Language (SDDL) to grant the Built-In Users group access to the "root/servicemodel" WMI namespace.</span></span> <span data-ttu-id="b9d9d-169">Následující seznamy ACL určuje:</span><span class="sxs-lookup"><span data-stu-id="b9d9d-169">It specifies the following ACLs:</span></span>  
  
    -   <span data-ttu-id="b9d9d-170">Předdefinovaný účet Administrator (BA) - už měli přístup.</span><span class="sxs-lookup"><span data-stu-id="b9d9d-170">Built-In Administrator (BA) - Already Had Access.</span></span>  
  
    -   <span data-ttu-id="b9d9d-171">Síťová služba (NS) - už měli přístup.</span><span class="sxs-lookup"><span data-stu-id="b9d9d-171">Network Service (NS) - Already Had Access.</span></span>  
  
    -   <span data-ttu-id="b9d9d-172">Místní systém (LS) - už měli přístup.</span><span class="sxs-lookup"><span data-stu-id="b9d9d-172">Local System (LS) - Already Had Access.</span></span>  
  
    -   <span data-ttu-id="b9d9d-173">Předdefinované uživatelé – skupina k udělení přístupu k.</span><span class="sxs-lookup"><span data-stu-id="b9d9d-173">Built-In Users - The group to grant access to.</span></span>  
  
#### <a name="to-grant-provider-registration-access"></a><span data-ttu-id="b9d9d-174">Zprostředkovatel udělit přístup k registraci</span><span class="sxs-lookup"><span data-stu-id="b9d9d-174">To grant provider registration access</span></span>  
  
1.  <span data-ttu-id="b9d9d-175">Spusťte následující skript prostředí PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b9d9d-175">Run the following PowerShell script.</span></span>  
  
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
  
### <a name="granting-access-to-arbitrary-users-or-groups"></a><span data-ttu-id="b9d9d-176">Udělení přístupu na libovolného uživatele nebo skupiny</span><span class="sxs-lookup"><span data-stu-id="b9d9d-176">Granting Access to Arbitrary Users or Groups</span></span>  
 <span data-ttu-id="b9d9d-177">Příklad v této části uděluje oprávnění registrace zprostředkovatele rozhraní WMI na všech místních uživatelů.</span><span class="sxs-lookup"><span data-stu-id="b9d9d-177">The example in this section grants WMI Provider registration privileges to all local users.</span></span> <span data-ttu-id="b9d9d-178">Pokud chcete udělit přístup na uživatele nebo skupinu, která není součástí, pak je nutné získat tohoto uživatele nebo skupiny identifikátor zabezpečení (SID).</span><span class="sxs-lookup"><span data-stu-id="b9d9d-178">If you want to grant access to a user or group that is not built in, then you must obtain that user or group’s Security Identifier (SID).</span></span> <span data-ttu-id="b9d9d-179">Neexistuje žádný jednoduchý způsob, jak získat identifikátor SID pro libovolný uživatel.</span><span class="sxs-lookup"><span data-stu-id="b9d9d-179">There is no simple way to get the SID for an arbitrary user.</span></span> <span data-ttu-id="b9d9d-180">Přihlaste se jako požadovaného uživatele a potom vydat příkaz prostředí je jednu metodu.</span><span class="sxs-lookup"><span data-stu-id="b9d9d-180">One method is to log on as the desired user and then issue the following shell command.</span></span>  
  
```  
Whoami /user  
```  
  
 <span data-ttu-id="b9d9d-181">To poskytuje SID aktuálního uživatele, ale tuto metodu nelze použít k získání SID na každý libovolný uživatel.</span><span class="sxs-lookup"><span data-stu-id="b9d9d-181">This provides the SID of the current user, but this method cannot be used to get the SID on any arbitrary user.</span></span> <span data-ttu-id="b9d9d-182">Další možností, jak získat identifikátor SID je použití [getsid.exe](http://go.microsoft.com/fwlink/?LinkId=186467) nástroje z [Windows 2000 Resource Kit Tools pro úlohy správy](http://go.microsoft.com/fwlink/?LinkId=178660).</span><span class="sxs-lookup"><span data-stu-id="b9d9d-182">Another method to get the SID is to use the [getsid.exe](http://go.microsoft.com/fwlink/?LinkId=186467) tool from the [Windows 2000 Resource Kit Tools for administrative tasks](http://go.microsoft.com/fwlink/?LinkId=178660).</span></span> <span data-ttu-id="b9d9d-183">Tento nástroj porovná SID dva uživatele (místní nebo doménový) a jako straně vliv vytiskne dva identifikátory SID na příkazový řádek.</span><span class="sxs-lookup"><span data-stu-id="b9d9d-183">This tool compares the SID of two users (local or domain), and as a side effect prints the two SIDs to the command line.</span></span> [!INCLUDE[crdefault](../../../../../includes/crdefault-md.md)]<span data-ttu-id="b9d9d-184">[Dobře známé identifikátory SID](http://go.microsoft.com/fwlink/?LinkId=186468).</span><span class="sxs-lookup"><span data-stu-id="b9d9d-184"> [Well Known SIDs](http://go.microsoft.com/fwlink/?LinkId=186468).</span></span>  
  
## <a name="accessing-remote-wmi-object-instances"></a><span data-ttu-id="b9d9d-185">Přístup k rozhraní WMI Vzdálená instance objektů</span><span class="sxs-lookup"><span data-stu-id="b9d9d-185">Accessing Remote WMI Object Instances</span></span>  
 <span data-ttu-id="b9d9d-186">Pokud budete potřebovat pro přístup k [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] instance rozhraní WMI na vzdáleném počítači, je nutné povolit paket o ochraně osobních údajů nástroje, které používáte pro přístup.</span><span class="sxs-lookup"><span data-stu-id="b9d9d-186">If you need to access [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] WMI instances on a remote machine, you must enable packet privacy on the tools that you use for access.</span></span> <span data-ttu-id="b9d9d-187">Následující část popisuje, jak tyto dosáhnout pomocí WMI CIM Studio, testování služby WMI, jakož i rozhraní .NET SDK 2.0.</span><span class="sxs-lookup"><span data-stu-id="b9d9d-187">The following section describes how to achieve these using the WMI CIM Studio, Windows Management Instrumentation Tester, as well as .NET SDK 2.0.</span></span>  
  
### <a name="wmi-cim-studio"></a><span data-ttu-id="b9d9d-188">Rozhraní WMI CIM Studio</span><span class="sxs-lookup"><span data-stu-id="b9d9d-188">WMI CIM Studio</span></span>  
 <span data-ttu-id="b9d9d-189">Pokud jste nainstalovali [nástroje pro správu služby WMI](http://go.microsoft.com/fwlink/?LinkId=95185), můžete použít nástroje CIM Studio WMI k instancím přístup k rozhraní WMI.</span><span class="sxs-lookup"><span data-stu-id="b9d9d-189">If you have installed [WMI Administrative Tools](http://go.microsoft.com/fwlink/?LinkId=95185), you can use the WMI CIM Studio to access WMI instances.</span></span> <span data-ttu-id="b9d9d-190">Nástroje jsou v následující složce</span><span class="sxs-lookup"><span data-stu-id="b9d9d-190">The tools are in the following folder</span></span>  
  
 <span data-ttu-id="b9d9d-191">**%WINDIR%\Program Files\WMI nástroje\\**</span><span class="sxs-lookup"><span data-stu-id="b9d9d-191">**%windir%\Program Files\WMI Tools\\**</span></span>  
  
1.  <span data-ttu-id="b9d9d-192">V **připojit k oboru názvů:** zadejte **root\ServiceModel** a klikněte na tlačítko **OK.**</span><span class="sxs-lookup"><span data-stu-id="b9d9d-192">In the **Connect to namespace:** window, type **root\ServiceModel** and click **OK.**</span></span>  
  
2.  <span data-ttu-id="b9d9d-193">V **WMI CIM Studio přihlášení** okně klikněte na tlačítko **možnosti >>** tlačítko rozbalte okno.</span><span class="sxs-lookup"><span data-stu-id="b9d9d-193">In the **WMI CIM Studio Login** window, click the **Options >>** button to expand the window.</span></span> <span data-ttu-id="b9d9d-194">Vyberte **paket o ochraně osobních údajů** pro **úroveň ověřování**a klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="b9d9d-194">Select **Packet privacy** for **Authentication level**, and click **OK**.</span></span>  
  
### <a name="windows-management-instrumentation-tester"></a><span data-ttu-id="b9d9d-195">Testování služby WMI</span><span class="sxs-lookup"><span data-stu-id="b9d9d-195">Windows Management Instrumentation Tester</span></span>  
 <span data-ttu-id="b9d9d-196">Tento nástroj je nainstalována v systému Windows.</span><span class="sxs-lookup"><span data-stu-id="b9d9d-196">This tool is installed by Windows.</span></span> <span data-ttu-id="b9d9d-197">Ji spustit, spusťte příkaz konzole zadáním **cmd.exe** v **spuštění a spuštění** dialogové okno a klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="b9d9d-197">To run it, launch a command console by typing **cmd.exe** in the **Start/Run** dialog box and click **OK**.</span></span> <span data-ttu-id="b9d9d-198">Poté zadejte **wbemtest.exe** v příkazovém okně.</span><span class="sxs-lookup"><span data-stu-id="b9d9d-198">Then, type **wbemtest.exe** in the command window.</span></span> <span data-ttu-id="b9d9d-199">Pak je spustit nástroj testování služby WMI.</span><span class="sxs-lookup"><span data-stu-id="b9d9d-199">The Windows Management Instrumentation Tester tool is then launched.</span></span>  
  
1.  <span data-ttu-id="b9d9d-200">Klikněte **Connect** tlačítko v pravém horním rohu okna.</span><span class="sxs-lookup"><span data-stu-id="b9d9d-200">Click the **Connect** button on the top right corner of the window.</span></span>  
  
2.  <span data-ttu-id="b9d9d-201">V novém okně zadejte **root\ServiceModel** pro **Namespace** pole a vyberte možnost **paket o ochraně osobních údajů** pro **úroveň ověřování**.</span><span class="sxs-lookup"><span data-stu-id="b9d9d-201">In the new window, enter **root\ServiceModel** for the **Namespace** field, and select **Packet privacy** for **Authentication level**.</span></span> <span data-ttu-id="b9d9d-202">Klikněte na tlačítko **připojit**.</span><span class="sxs-lookup"><span data-stu-id="b9d9d-202">Click **Connect**.</span></span>  
  
### <a name="using-managed-code"></a><span data-ttu-id="b9d9d-203">Pomocí spravovaného kódu</span><span class="sxs-lookup"><span data-stu-id="b9d9d-203">Using Managed Code</span></span>  
 <span data-ttu-id="b9d9d-204">Máte můžete také přístup k vzdálené instance rozhraní WMI prostřednictvím kódu programu pomocí třídy poskytované <xref:System.Management> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="b9d9d-204">You can also access remote WMI instances programmatically by using classes provided by the <xref:System.Management> namespace.</span></span> <span data-ttu-id="b9d9d-205">Následující příklad kódu ukazuje, jak to udělat.</span><span class="sxs-lookup"><span data-stu-id="b9d9d-205">The following code sample demonstrates how to do this.</span></span>  
  
```  
String wcfNamespace = String.Format(@"\\{0}\Root\ServiceModel",      
   this.serviceMachineName);  
  
ConnectionOptions connection = new ConnectionOptions();  
connection.Authentication = AuthenticationLevel.PacketPrivacy;  
ManagementScope scope = new ManagementScope(this.wcfNamespace, connection);  
```
