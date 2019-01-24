---
title: Čítače výkonu WCF
ms.date: 03/30/2017
helpviewer_keywords:
  - 'performance counters [WCF]'
ms.assetid: f559b2bd-ed83-4988-97a1-e88f06646609
---
# <a name="wcf-performance-counters"></a><span data-ttu-id="980c5-102">Čítače výkonu WCF</span><span class="sxs-lookup"><span data-stu-id="980c5-102">WCF Performance Counters</span></span>
<span data-ttu-id="980c5-103">Windows Communication Foundation (WCF) obsahuje velké sady čítače výkonu umožňují měřit výkon vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="980c5-103">Windows Communication Foundation (WCF) includes a large set of performance counters to help you gauge your application's performance.</span></span>  
  
## <a name="enabling-performance-counters"></a><span data-ttu-id="980c5-104">Povolení čítače výkonu</span><span class="sxs-lookup"><span data-stu-id="980c5-104">Enabling Performance Counters</span></span>  
 <span data-ttu-id="980c5-105">Čítače výkonu služby WCF pomocí konfiguračního souboru app.config služby WCF můžete povolit následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="980c5-105">You can enable performance counters for a WCF service through the app.config configuration file of the WCF service as follows:</span></span>  
  
```xml  
<configuration>  
    <system.serviceModel>  
        <diagnostics performanceCounters="All" />  
    </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="980c5-106">`performanceCounters` Atribut můžete nastavit pro povolení konkrétní typ čítače výkonu.</span><span class="sxs-lookup"><span data-stu-id="980c5-106">The `performanceCounters` attribute can be set to enable a specific type of performance counters.</span></span> <span data-ttu-id="980c5-107">Platné hodnoty jsou</span><span class="sxs-lookup"><span data-stu-id="980c5-107">Valid values are</span></span>  
  
-   <span data-ttu-id="980c5-108">Všechny: Jsou povoleny všechny kategorie čítače (ServiceModelService, ServiceModelEndpoint a ServiceModelOperation).</span><span class="sxs-lookup"><span data-stu-id="980c5-108">All: All category counters (ServiceModelService, ServiceModelEndpoint and ServiceModelOperation) are enabled.</span></span>  
  
-   <span data-ttu-id="980c5-109">ServiceOnly: Jsou povoleny pouze ServiceModelService kategorie čítače.</span><span class="sxs-lookup"><span data-stu-id="980c5-109">ServiceOnly: Only ServiceModelService category counters are enabled.</span></span> <span data-ttu-id="980c5-110">Jedná se o výchozí hodnotu.</span><span class="sxs-lookup"><span data-stu-id="980c5-110">This is the default value.</span></span>  
  
-   <span data-ttu-id="980c5-111">Vypnuto: Čítače výkonu ServiceModel \* jsou zakázány.</span><span class="sxs-lookup"><span data-stu-id="980c5-111">Off: ServiceModel\* performance counters are disabled.</span></span>  
  
 <span data-ttu-id="980c5-112">Pokud chcete povolit čítače výkonu pro všechny aplikace, WCF, můžete umístit nastavení konfigurace v souboru Machine.config.</span><span class="sxs-lookup"><span data-stu-id="980c5-112">If you want to enable performance counters for all WCF applications, you can place the configuration settings in the Machine.config file.</span></span>  <span data-ttu-id="980c5-113">Podrobnosti najdete **zvýšit velikost paměti pro čítače výkonu** níže v části Další informace o konfiguraci na svém počítači dostatek paměti pro čítače výkonu.</span><span class="sxs-lookup"><span data-stu-id="980c5-113">Please see the **Increasing Memory Size for Performance Counters** section below for more information on configuring sufficient memory for performance counters on your machine.</span></span>  
  
 <span data-ttu-id="980c5-114">Pokud používáte bodů rozšiřitelnosti WCF, jako je vlastní operace invokers, by měly taky vydávat vlastní čítače výkonu.</span><span class="sxs-lookup"><span data-stu-id="980c5-114">If you use WCF extensibility points such as custom operation invokers, you should also emit your own performance counters.</span></span> <span data-ttu-id="980c5-115">Je to proto, že pokud se rozhodnete implementovat bod rozšiřitelnosti, WCF může už negeneruje data čítače výkonu ve výchozí cestě.</span><span class="sxs-lookup"><span data-stu-id="980c5-115">This is because if you implement an extensibility point, WCF may no longer emit the standard performance counter data in the default path.</span></span> <span data-ttu-id="980c5-116">Pokud implementujete není podpora čítače výkonu ruční, nemusíte vidět data čítače výkonu, které očekáváte.</span><span class="sxs-lookup"><span data-stu-id="980c5-116">If you do not implement manual performance counter support, you may not see the performance counter data you expect.</span></span>  
  
 <span data-ttu-id="980c5-117">Můžete také povolit čítače výkonu ve vašem kódu následujícím způsobem</span><span class="sxs-lookup"><span data-stu-id="980c5-117">You can also enable performance counters in your code as follows,</span></span>  
  
```  
using System.Configuration;  
using System.ServiceModel.Configuration;  
using System.ServiceModel.Diagnostics;  
Configuration config = ConfigurationManager.OpenExeConfiguration(  
    ConfigurationUserLevel.None);  
ServiceModelSectionGroup sg = ServiceModelSectionGroup.GetSectionGroup(config);  
sg.Diagnostic.PerformanceCounters = PerformanceCounterScope.All;  
config.Save();  
```  
  
## <a name="viewing-performance-data"></a><span data-ttu-id="980c5-118">Zobrazení dat výkonu</span><span class="sxs-lookup"><span data-stu-id="980c5-118">Viewing Performance Data</span></span>  
 <span data-ttu-id="980c5-119">Chcete-li zobrazit data zachycená pomocí čítačů výkonu, můžete použít sledování výkonu (Perfmon.exe), který je součástí Windows.</span><span class="sxs-lookup"><span data-stu-id="980c5-119">To view data captured by the performance counters, you can use the Performance Monitor (Perfmon.exe) that comes with Windows.</span></span> <span data-ttu-id="980c5-120">Tento nástroj můžete spustit tak, že přejdete do **Start**a klikněte na tlačítko **spustit** a typ `perfmon.exe` v dialogovém okně.</span><span class="sxs-lookup"><span data-stu-id="980c5-120">You can launch this tool by going to **Start**, and click **Run** and type `perfmon.exe` in the dialog box.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="980c5-121">Instance čítače výkonu může uvolnit před poslední zprávy byly zpracovány Dispečer koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="980c5-121">Performance counter instances may be released before the last messages have been processed by the endpoint dispatcher.</span></span> <span data-ttu-id="980c5-122">Výsledkem může být údaje o výkonu není zachycena pro několik zpráv.</span><span class="sxs-lookup"><span data-stu-id="980c5-122">This can result in performance data not being captured for a few messages.</span></span>  
  
## <a name="increasing-memory-size-for-performance-counters"></a><span data-ttu-id="980c5-123">Zvětšení velikosti paměti pro čítače výkonu</span><span class="sxs-lookup"><span data-stu-id="980c5-123">Increasing Memory Size for Performance Counters</span></span>  
 <span data-ttu-id="980c5-124">WCF používá samostatné sdílené paměti pro své kategorie čítače výkonu.</span><span class="sxs-lookup"><span data-stu-id="980c5-124">WCF uses separate shared memory for its performance counter categories.</span></span>  
  
 <span data-ttu-id="980c5-125">Ve výchozím nastavení je samostatnou sdílenou paměť nastavit čtvrtletí velikost globálního výkonu čítače paměti.</span><span class="sxs-lookup"><span data-stu-id="980c5-125">By default, separate shared memory is set to a quarter the size of global performance counter memory.</span></span> <span data-ttu-id="980c5-126">Výchozí globálního výkonu čítače paměti je 524,288 bajtů.</span><span class="sxs-lookup"><span data-stu-id="980c5-126">The default global performance counter memory is 524,288 bytes.</span></span> <span data-ttu-id="980c5-127">Proto se tři kategorie čítače výkonu WCF mají výchozí velikost přibližně 128 kB.</span><span class="sxs-lookup"><span data-stu-id="980c5-127">Therefore, the three WCF performance counter categories have a default size of approximately 128KB each.</span></span> <span data-ttu-id="980c5-128">V závislosti na vlastnosti modul runtime WCF aplikací na počítači, může být vyčerpání paměti čítače výkonu.</span><span class="sxs-lookup"><span data-stu-id="980c5-128">Depending upon the runtime characteristics of the WCF applications on a machine, performance counter memory may be exhausted.</span></span> <span data-ttu-id="980c5-129">Pokud k tomu dojde, WCF zapíše chybu do protokolu událostí aplikace.</span><span class="sxs-lookup"><span data-stu-id="980c5-129">When this happens, WCF writes an error to the application event log.</span></span> <span data-ttu-id="980c5-130">Obsah chyba uvádí, že čítač výkonu nebyl načten a položka obsahuje výjimku "System.InvalidOperationException: Zobrazení souboru vlastních čítačů není dostatek paměti."</span><span class="sxs-lookup"><span data-stu-id="980c5-130">The content of the error states that a performance counter was not loaded, and the entry contains the exception "System.InvalidOperationException: Custom counters file view is out of memory."</span></span> <span data-ttu-id="980c5-131">Pokud je povoleno trasování na úrovni chyby, je také sledovat toto selhání.</span><span class="sxs-lookup"><span data-stu-id="980c5-131">If tracing is enabled at the error level, this failure is also traced.</span></span> <span data-ttu-id="980c5-132">Pokud dojde k vyčerpání paměti čítače výkonu, pokračování a spouštění aplikací WCF pomocí čítačů výkonu povolena by mohlo způsobit snížení výkonu.</span><span class="sxs-lookup"><span data-stu-id="980c5-132">If performance counter memory is exhausted, continuing to run your WCF applications with performance counters enabled could result in performance degradation.</span></span> <span data-ttu-id="980c5-133">Pokud jste správcem počítače, měli byste nakonfigurovat ji přidělit dostatek paměti pro podporu maximální počet čítačů výkonu, které mohou existovat v každém okamžiku.</span><span class="sxs-lookup"><span data-stu-id="980c5-133">If you are an administrator of the machine, you should configure it to allocate enough memory to support the maximum number of performance counters that can exist at any time.</span></span>  
  
 <span data-ttu-id="980c5-134">Můžete změnit velikost paměti čítače výkonu WCF kategorií v registru.</span><span class="sxs-lookup"><span data-stu-id="980c5-134">You can change the amount of performance counter memory for WCF categories in the registry.</span></span> <span data-ttu-id="980c5-135">Uděláte to tak, budete muset přidat novou hodnotu DWORD s názvem `FileMappingSize` do tří následujících umístění a nastavte ji na požadovanou hodnotu v bajtech.</span><span class="sxs-lookup"><span data-stu-id="980c5-135">To do so, you need to add a new DWORD value named `FileMappingSize` to the three following locations, and set it to the desired value in bytes.</span></span> <span data-ttu-id="980c5-136">Po restartování počítače, aby tyto změny jsou přijata platit.</span><span class="sxs-lookup"><span data-stu-id="980c5-136">Reboot your machine so that these changes are taken into effect.</span></span>  
  
-   <span data-ttu-id="980c5-137">HKLM\System\CurrentControlSet\Services\ServiceModelEndpoint 4.0.0.0\Performance</span><span class="sxs-lookup"><span data-stu-id="980c5-137">HKLM\System\CurrentControlSet\Services\ServiceModelEndpoint 4.0.0.0\Performance</span></span>  
  
-   <span data-ttu-id="980c5-138">HKLM\System\CurrentControlSet\Services\ServiceModelOperation 4.0.0.0\Performance</span><span class="sxs-lookup"><span data-stu-id="980c5-138">HKLM\System\CurrentControlSet\Services\ServiceModelOperation 4.0.0.0\Performance</span></span>  
  
-   <span data-ttu-id="980c5-139">HKLM\System\CurrentControlSet\Services\ServiceModelService 4.0.0.0\Performance</span><span class="sxs-lookup"><span data-stu-id="980c5-139">HKLM\System\CurrentControlSet\Services\ServiceModelService 4.0.0.0\Performance</span></span>  
  
 <span data-ttu-id="980c5-140">Když jsou odstraněny velký počet objektů (například hostitel služby) ale čeká na prováděno uvolnění paměti `PrivateBytes` čítače výkonu se registrují neobvykle velký počet.</span><span class="sxs-lookup"><span data-stu-id="980c5-140">When a large number of objects (for example, ServiceHost) are disposed of but waiting to be garbage-collected, the `PrivateBytes` performance counter will register an unusually high number.</span></span> <span data-ttu-id="980c5-141">Chcete-li vyřešit tento problém, můžete buď přidat čítače specifické pro aplikaci nebo použijte `performanceCounters` atribut pro povolení pouze SLA čítače.</span><span class="sxs-lookup"><span data-stu-id="980c5-141">To resolve this problem, you can either add your own application-specific counters, or use the `performanceCounters` attribute to enable only service-level counters.</span></span>  
  
## <a name="types-of-performance-counters"></a><span data-ttu-id="980c5-142">Typy čítačů výkonu</span><span class="sxs-lookup"><span data-stu-id="980c5-142">Types of Performance Counters</span></span>  
 <span data-ttu-id="980c5-143">Čítače výkonu jsou nastavit rozsah na třech různých úrovních: Služba, koncový bod a operace.</span><span class="sxs-lookup"><span data-stu-id="980c5-143">Performance counters are scoped to three different levels: Service, Endpoint and Operation.</span></span>  
  
 <span data-ttu-id="980c5-144">Chcete-li načíst název instance čítače výkonu můžete použít rozhraní WMI.</span><span class="sxs-lookup"><span data-stu-id="980c5-144">You can use WMI to retrieve the name of a performance counter instance.</span></span> <span data-ttu-id="980c5-145">Například</span><span class="sxs-lookup"><span data-stu-id="980c5-145">For example,</span></span>  
  
-   <span data-ttu-id="980c5-146">Název instance čítače služby můžete získat prostřednictvím rozhraní WMI [služby](../../../../../docs/framework/wcf/diagnostics/wmi/service.md) vlastnost "CounterInstanceName" instance.</span><span class="sxs-lookup"><span data-stu-id="980c5-146">Service counter instance name can be obtained through WMI [Service](../../../../../docs/framework/wcf/diagnostics/wmi/service.md) instance's "CounterInstanceName" property.</span></span>  
  
-   <span data-ttu-id="980c5-147">Název instance čítače koncového bodu můžete získat prostřednictvím rozhraní WMI [koncový bod](../../../../../docs/framework/wcf/diagnostics/wmi/endpoint.md) vlastnost "CounterInstanceName" instance.</span><span class="sxs-lookup"><span data-stu-id="980c5-147">Endpoint counter instance name can be obtained through WMI [Endpoint](../../../../../docs/framework/wcf/diagnostics/wmi/endpoint.md) instance's "CounterInstanceName" property.</span></span>  
  
-   <span data-ttu-id="980c5-148">Název instance čítače operace můžete získat prostřednictvím rozhraní WMI [koncový bod](../../../../../docs/framework/wcf/diagnostics/wmi/endpoint.md) "GetOperationCounterInstanceName" metodu instance.</span><span class="sxs-lookup"><span data-stu-id="980c5-148">Operation counter instance name can be obtained through WMI [Endpoint](../../../../../docs/framework/wcf/diagnostics/wmi/endpoint.md) instance's "GetOperationCounterInstanceName" method.</span></span>  
  
 <span data-ttu-id="980c5-149">Další informace o rozhraní WMI najdete v tématu [pomocí Windows Management Instrumentation k diagnostice](../../../../../docs/framework/wcf/diagnostics/wmi/index.md).</span><span class="sxs-lookup"><span data-stu-id="980c5-149">For more information on WMI, see [Using Windows Management Instrumentation for Diagnostics](../../../../../docs/framework/wcf/diagnostics/wmi/index.md).</span></span>  
  
### <a name="service-performance-counters"></a><span data-ttu-id="980c5-150">Čítače výkonu služby</span><span class="sxs-lookup"><span data-stu-id="980c5-150">Service performance counters</span></span>  
 <span data-ttu-id="980c5-151">Čítače výkonu služby měření chování služby jako celek a slouží k diagnostice výkonu celou službu.</span><span class="sxs-lookup"><span data-stu-id="980c5-151">Service performance counters measure the service behavior as a whole and can be used to diagnose the performance of the whole service.</span></span> <span data-ttu-id="980c5-152">Najdete v části `ServiceModelService 4.0.0.0` objekt výkonu při zobrazení pomocí sledování výkonu.</span><span class="sxs-lookup"><span data-stu-id="980c5-152">They can be found under the `ServiceModelService 4.0.0.0` performance object when viewing with Performance Monitor.</span></span> <span data-ttu-id="980c5-153">Tyto instance jsou pojmenovány pomocí následujícího vzorce:</span><span class="sxs-lookup"><span data-stu-id="980c5-153">The instances are named using the following pattern:</span></span>  
  
```  
ServiceName@ServiceBaseAddress  
```  
  
 <span data-ttu-id="980c5-154">Čítače v oboru služby se shromažďuje od čítače v kolekce koncových bodů.</span><span class="sxs-lookup"><span data-stu-id="980c5-154">A counter in a service scope is aggregated from counter in a collection of endpoints.</span></span>  
  
 <span data-ttu-id="980c5-155">Čítače výkonu pro vytvoření instance služby se zvýší, když se vytvoří nová třída InstanceContext.</span><span class="sxs-lookup"><span data-stu-id="980c5-155">Performance counters for service instance creation are incremented when a new InstanceContext is created.</span></span> <span data-ttu-id="980c5-156">Všimněte si, že se vytvoří nová třída InstanceContext, i když obdržíte zprávu bez aktivace (s existující služby), nebo když připojit k instanci služby z jedné relace, ukončit relaci a potom se znova připojit z jiné relace.</span><span class="sxs-lookup"><span data-stu-id="980c5-156">Note that a new InstanceContext is created even when you receive a non-activating message (with an existing service), or when you connect to an instance from one session, end the session, and then reconnect from another session.</span></span>  
  
### <a name="endpoint-performance-counters"></a><span data-ttu-id="980c5-157">Čítače výkonu koncového bodu</span><span class="sxs-lookup"><span data-stu-id="980c5-157">Endpoint performance counters</span></span>  
 <span data-ttu-id="980c5-158">Čítače výkonu koncového bodu umožňují podívat se na data, která odráží, jak koncový bod přijímá zprávy.</span><span class="sxs-lookup"><span data-stu-id="980c5-158">Endpoint performance counters enable you to look at data reflecting how an endpoint is accepting messages.</span></span> <span data-ttu-id="980c5-159">Najdete v části `ServiceModelEndpoint 4.0.0.0` objekt výkonu při prohlížení použití nástroje Sledování výkonu.</span><span class="sxs-lookup"><span data-stu-id="980c5-159">They can be found under the `ServiceModelEndpoint 4.0.0.0` performance object when viewing using the Performance Monitor.</span></span> <span data-ttu-id="980c5-160">Tyto instance jsou pojmenovány pomocí následujícího vzorce:</span><span class="sxs-lookup"><span data-stu-id="980c5-160">The instances are named using the following pattern:</span></span>  
  
```  
(ServiceName).(ContractName)@(endpoint listener address)  
```  
  
 <span data-ttu-id="980c5-161">Data jsou podobné, co se shromažďují pro jednotlivé operace, ale pouze se agreguje přes koncový bod.</span><span class="sxs-lookup"><span data-stu-id="980c5-161">The data is similar to what is collected for individual operations, but is only aggregated across the endpoint.</span></span>  
  
 <span data-ttu-id="980c5-162">Čítače v oboru koncový bod se shromažďuje od čítače v kolekci operací.</span><span class="sxs-lookup"><span data-stu-id="980c5-162">A counter in an endpoint scope is aggregated from counters in a collection of operations.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="980c5-163">Pokud dva koncové body mají stejné kontraktu jména a adresy, jsou mapovány na stejnou instanci čítače.</span><span class="sxs-lookup"><span data-stu-id="980c5-163">If two endpoints have identical contract names and addresses, they are mapped to the same counter instance.</span></span>  
  
### <a name="operation-performance-counters"></a><span data-ttu-id="980c5-164">Čítače provozního výkonu</span><span class="sxs-lookup"><span data-stu-id="980c5-164">Operation performance counters</span></span>  
 <span data-ttu-id="980c5-165">Čítače provozního výkonu se nacházejí v rámci `ServiceModelOperation 4.0.0.0` objekt výkonu při zobrazení pomocí nástroje Sledování výkonu.</span><span class="sxs-lookup"><span data-stu-id="980c5-165">Operation performance counters are found under the `ServiceModelOperation 4.0.0.0` performance object when viewing with the Performance Monitor.</span></span> <span data-ttu-id="980c5-166">Každá operace má jednotlivé instance.</span><span class="sxs-lookup"><span data-stu-id="980c5-166">Each operation has an individual instance.</span></span> <span data-ttu-id="980c5-167">To znamená že pokud má daný kontrakt 10 operací, jsou 10 instancí čítače operace spojené s touto smlouvou.</span><span class="sxs-lookup"><span data-stu-id="980c5-167">That is, if a given contract has 10 operations, 10 operation counter instances are associated with that contract.</span></span> <span data-ttu-id="980c5-168">Instance objektů jsou pojmenovány pomocí následujícího vzorce:</span><span class="sxs-lookup"><span data-stu-id="980c5-168">The object instances are named using the following pattern:</span></span>  
  
```  
(ServiceName).(ContractName).(OperationName)@(first endpoint listener address)  
```  
  
 <span data-ttu-id="980c5-169">Tento čítač umožňuje měřit využití volání a jak dobře fungují operace.</span><span class="sxs-lookup"><span data-stu-id="980c5-169">This counter enables you to measure how the call is being used and how well the operation is performing.</span></span>  
  
 <span data-ttu-id="980c5-170">Když čítače jsou viditelné v několika oborech, dat shromážděných z vyššího oboru se agregují s daty z nižší obory.</span><span class="sxs-lookup"><span data-stu-id="980c5-170">When counters are visible at multiple scopes, data gathered from a higher scope are aggregated with data from lower scopes.</span></span> <span data-ttu-id="980c5-171">Například `Calls` na koncový bod představuje součet všech volání operace v rámci koncový bod; `Calls` na službu představuje součet všech volání pro všechny koncové body v rámci služby.</span><span class="sxs-lookup"><span data-stu-id="980c5-171">For example, `Calls` at an endpoint represents the sum of all operation calls within the endpoint; `Calls` at a service represents the sum of all calls to all endpoints within the service.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="980c5-172">Pokud máte na kontrakt operace duplicitní názvy, získáte jenom jedna instance čítačů pro obě operace.</span><span class="sxs-lookup"><span data-stu-id="980c5-172">If you have duplicate operation names on a contract, you only get one counter instances for both operations.</span></span>  
  
## <a name="programming-the-wcf-performance-counters"></a><span data-ttu-id="980c5-173">Programování čítače výkonu WCF</span><span class="sxs-lookup"><span data-stu-id="980c5-173">Programming the WCF Performance Counters</span></span>  
 <span data-ttu-id="980c5-174">Několik souborů se instalují do složky instalace sady SDK tak, aby čítače výkonu WCF můžete přistupovat prostřednictvím kódu programu.</span><span class="sxs-lookup"><span data-stu-id="980c5-174">Several files are installed in the SDK install folder so that you can access the WCF performance counters programmatically.</span></span> <span data-ttu-id="980c5-175">Tyto soubory jsou uvedeny následovně.</span><span class="sxs-lookup"><span data-stu-id="980c5-175">These files are listed as follows.</span></span>  
  
-   <span data-ttu-id="980c5-176">_ServiceModelEndpointPerfCounters.vrg</span><span class="sxs-lookup"><span data-stu-id="980c5-176">_ServiceModelEndpointPerfCounters.vrg</span></span>  
  
-   <span data-ttu-id="980c5-177">_ServiceModelOperationPerfCounters.vrg</span><span class="sxs-lookup"><span data-stu-id="980c5-177">_ServiceModelOperationPerfCounters.vrg</span></span>  
  
-   <span data-ttu-id="980c5-178">_ServiceModelServicePerfCounters.vrg</span><span class="sxs-lookup"><span data-stu-id="980c5-178">_ServiceModelServicePerfCounters.vrg</span></span>  
  
-   <span data-ttu-id="980c5-179">_SMSvcHostPerfCounters.vrg</span><span class="sxs-lookup"><span data-stu-id="980c5-179">_SMSvcHostPerfCounters.vrg</span></span>  
  
-   <span data-ttu-id="980c5-180">_TransactionBridgePerfCounters.vrg</span><span class="sxs-lookup"><span data-stu-id="980c5-180">_TransactionBridgePerfCounters.vrg</span></span>  
  
 <span data-ttu-id="980c5-181">Další informace o tom, jak programově přístup k čítačům najdete v tématu [programovací architektura čítače výkonu](https://go.microsoft.com/fwlink/?LinkId=95179).</span><span class="sxs-lookup"><span data-stu-id="980c5-181">For more information on how to access the counters programmatically, see [Performance Counter Programming Architecture](https://go.microsoft.com/fwlink/?LinkId=95179).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="980c5-182">Viz také:</span><span class="sxs-lookup"><span data-stu-id="980c5-182">See also</span></span>
- [<span data-ttu-id="980c5-183">Správa a diagnostika</span><span class="sxs-lookup"><span data-stu-id="980c5-183">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
