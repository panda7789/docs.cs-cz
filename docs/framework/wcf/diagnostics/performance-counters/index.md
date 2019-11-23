---
title: Čítače výkonu WCF
ms.date: 03/30/2017
helpviewer_keywords:
- performance counters [WCF]
ms.assetid: f559b2bd-ed83-4988-97a1-e88f06646609
ms.openlocfilehash: 73bb02379308fbfe507137e61ac8d84e6b9760b4
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/16/2019
ms.locfileid: "72395898"
---
# <a name="wcf-performance-counters"></a><span data-ttu-id="7ecbf-102">Čítače výkonu WCF</span><span class="sxs-lookup"><span data-stu-id="7ecbf-102">WCF Performance Counters</span></span>
<span data-ttu-id="7ecbf-103">Windows Communication Foundation (WCF) obsahuje velkou sadu čítačů výkonu, které vám pomůžou posoudit výkon aplikace.</span><span class="sxs-lookup"><span data-stu-id="7ecbf-103">Windows Communication Foundation (WCF) includes a large set of performance counters to help you gauge your application's performance.</span></span>  
  
## <a name="enabling-performance-counters"></a><span data-ttu-id="7ecbf-104">Povolení čítačů výkonu</span><span class="sxs-lookup"><span data-stu-id="7ecbf-104">Enabling Performance Counters</span></span>  
 <span data-ttu-id="7ecbf-105">Můžete povolit čítače výkonu pro službu WCF prostřednictvím konfiguračního souboru App. config služby WCF následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="7ecbf-105">You can enable performance counters for a WCF service through the app.config configuration file of the WCF service as follows:</span></span>  
  
```xml  
<configuration>  
    <system.serviceModel>  
        <diagnostics performanceCounters="All" />  
    </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="7ecbf-106">Atribut `performanceCounters` lze nastavit tak, aby povoloval určitý typ čítačů výkonu.</span><span class="sxs-lookup"><span data-stu-id="7ecbf-106">The `performanceCounters` attribute can be set to enable a specific type of performance counters.</span></span> <span data-ttu-id="7ecbf-107">Platné hodnoty jsou</span><span class="sxs-lookup"><span data-stu-id="7ecbf-107">Valid values are</span></span>  
  
- <span data-ttu-id="7ecbf-108">All: jsou povoleny všechny čítače kategorií (ServiceModelService, ServiceModelEndpoint a ServiceModelOperation).</span><span class="sxs-lookup"><span data-stu-id="7ecbf-108">All: All category counters (ServiceModelService, ServiceModelEndpoint and ServiceModelOperation) are enabled.</span></span>  
  
- <span data-ttu-id="7ecbf-109">ServiceOnly: jsou povoleny pouze čítače kategorií ServiceModelService.</span><span class="sxs-lookup"><span data-stu-id="7ecbf-109">ServiceOnly: Only ServiceModelService category counters are enabled.</span></span> <span data-ttu-id="7ecbf-110">Jedná se o výchozí hodnotu.</span><span class="sxs-lookup"><span data-stu-id="7ecbf-110">This is the default value.</span></span>  
  
- <span data-ttu-id="7ecbf-111">Off: čítače výkonu ServiceModel \* jsou zakázané.</span><span class="sxs-lookup"><span data-stu-id="7ecbf-111">Off: ServiceModel\* performance counters are disabled.</span></span>  
  
 <span data-ttu-id="7ecbf-112">Pokud chcete povolit čítače výkonu pro všechny aplikace WCF, můžete nastavení konfigurace umístit do souboru Machine. config.</span><span class="sxs-lookup"><span data-stu-id="7ecbf-112">If you want to enable performance counters for all WCF applications, you can place the configuration settings in the Machine.config file.</span></span>  <span data-ttu-id="7ecbf-113">Další informace o konfiguraci dostatečné paměti pro čítače výkonu na počítači najdete v části **zvětšení paměti pro čítače výkonu** .</span><span class="sxs-lookup"><span data-stu-id="7ecbf-113">Please see the **Increasing Memory Size for Performance Counters** section below for more information on configuring sufficient memory for performance counters on your machine.</span></span>  
  
 <span data-ttu-id="7ecbf-114">Pokud používáte body rozšiřitelnosti WCF, jako je například vlastní operace invokers, měli byste také vygenerovat vlastní čítače výkonu.</span><span class="sxs-lookup"><span data-stu-id="7ecbf-114">If you use WCF extensibility points such as custom operation invokers, you should also emit your own performance counters.</span></span> <span data-ttu-id="7ecbf-115">Důvodem je, že pokud implementujete bod rozšiřitelnosti, WCF již nesmí generovat standardní data čítače výkonu ve výchozí cestě.</span><span class="sxs-lookup"><span data-stu-id="7ecbf-115">This is because if you implement an extensibility point, WCF may no longer emit the standard performance counter data in the default path.</span></span> <span data-ttu-id="7ecbf-116">Pokud neimplementujete ruční podporu čítače výkonu, nemusí se vám zobrazovat očekávaná data čítače výkonu.</span><span class="sxs-lookup"><span data-stu-id="7ecbf-116">If you do not implement manual performance counter support, you may not see the performance counter data you expect.</span></span>  
  
 <span data-ttu-id="7ecbf-117">Čítače výkonu můžete v kódu povolit také následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="7ecbf-117">You can also enable performance counters in your code as follows,</span></span>  
  
```csharp
using System.Configuration;  
using System.ServiceModel.Configuration;  
using System.ServiceModel.Diagnostics;  
Configuration config = ConfigurationManager.OpenExeConfiguration(  
    ConfigurationUserLevel.None);  
ServiceModelSectionGroup sg = ServiceModelSectionGroup.GetSectionGroup(config);  
sg.Diagnostic.PerformanceCounters = PerformanceCounterScope.All;  
config.Save();  
```  
  
## <a name="viewing-performance-data"></a><span data-ttu-id="7ecbf-118">Zobrazení údajů o výkonu</span><span class="sxs-lookup"><span data-stu-id="7ecbf-118">Viewing Performance Data</span></span>  
 <span data-ttu-id="7ecbf-119">Chcete-li zobrazit data zachycená čítači výkonu, můžete použít nástroj sledování výkonu (Perfmon. exe), který je součástí systému Windows.</span><span class="sxs-lookup"><span data-stu-id="7ecbf-119">To view data captured by the performance counters, you can use the Performance Monitor (Perfmon.exe) that comes with Windows.</span></span> <span data-ttu-id="7ecbf-120">Tento nástroj můžete spustit tak, že přejdete na **Start**a kliknete na **Spustit** a do dialogového okna zadejte `perfmon.exe`.</span><span class="sxs-lookup"><span data-stu-id="7ecbf-120">You can launch this tool by going to **Start**, and click **Run** and type `perfmon.exe` in the dialog box.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7ecbf-121">Instance čítače výkonu mohou být vydány před tím, než byly poslední zprávy zpracovány dispečerem koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="7ecbf-121">Performance counter instances may be released before the last messages have been processed by the endpoint dispatcher.</span></span> <span data-ttu-id="7ecbf-122">To může vést k tomu, že se data o výkonu nezaznamenávají pro několik zpráv.</span><span class="sxs-lookup"><span data-stu-id="7ecbf-122">This can result in performance data not being captured for a few messages.</span></span>  
  
## <a name="increasing-memory-size-for-performance-counters"></a><span data-ttu-id="7ecbf-123">Zvýšení velikosti paměti pro čítače výkonu</span><span class="sxs-lookup"><span data-stu-id="7ecbf-123">Increasing Memory Size for Performance Counters</span></span>  
 <span data-ttu-id="7ecbf-124">WCF používá pro kategorie čítače výkonu samostatnou sdílenou paměť.</span><span class="sxs-lookup"><span data-stu-id="7ecbf-124">WCF uses separate shared memory for its performance counter categories.</span></span>  
  
 <span data-ttu-id="7ecbf-125">Ve výchozím nastavení je samostatná sdílená paměť nastavená na čtvrtinu velikosti globální paměti čítače výkonu.</span><span class="sxs-lookup"><span data-stu-id="7ecbf-125">By default, separate shared memory is set to a quarter the size of global performance counter memory.</span></span> <span data-ttu-id="7ecbf-126">Výchozí globální paměť čítače výkonu je 524 288 bajtů.</span><span class="sxs-lookup"><span data-stu-id="7ecbf-126">The default global performance counter memory is 524,288 bytes.</span></span> <span data-ttu-id="7ecbf-127">Proto tři kategorie čítače výkonu WCF mají výchozí velikost přibližně 128 KB každého.</span><span class="sxs-lookup"><span data-stu-id="7ecbf-127">Therefore, the three WCF performance counter categories have a default size of approximately 128KB each.</span></span> <span data-ttu-id="7ecbf-128">V závislosti na charakteristikách modulu runtime aplikací WCF na počítači může být vyčerpána paměť čítače výkonu.</span><span class="sxs-lookup"><span data-stu-id="7ecbf-128">Depending upon the runtime characteristics of the WCF applications on a machine, performance counter memory may be exhausted.</span></span> <span data-ttu-id="7ecbf-129">Pokud k tomu dojde, WCF zapíše chybu do protokolu událostí aplikace.</span><span class="sxs-lookup"><span data-stu-id="7ecbf-129">When this happens, WCF writes an error to the application event log.</span></span> <span data-ttu-id="7ecbf-130">Obsah chyby uvádí, že čítač výkonu nebyl načten, a položka obsahuje výjimku "System. InvalidOperationException: zobrazení souboru vlastních čítačů není dostatek paměti."</span><span class="sxs-lookup"><span data-stu-id="7ecbf-130">The content of the error states that a performance counter was not loaded, and the entry contains the exception "System.InvalidOperationException: Custom counters file view is out of memory."</span></span> <span data-ttu-id="7ecbf-131">Pokud je trasování povoleno na úrovni chyby, tato chyba se také sleduje.</span><span class="sxs-lookup"><span data-stu-id="7ecbf-131">If tracing is enabled at the error level, this failure is also traced.</span></span> <span data-ttu-id="7ecbf-132">Pokud je paměť čítače výkonu vyčerpána, může pokračovat v spouštění aplikací WCF s povolenými čítači výkonu, což může způsobit snížení výkonu.</span><span class="sxs-lookup"><span data-stu-id="7ecbf-132">If performance counter memory is exhausted, continuing to run your WCF applications with performance counters enabled could result in performance degradation.</span></span> <span data-ttu-id="7ecbf-133">Pokud jste správcem počítače, měli byste ho nakonfigurovat, aby bylo možné přidělit dostatek paměti pro podporu maximálního počtu čítačů výkonu, které mohou existovat kdykoli.</span><span class="sxs-lookup"><span data-stu-id="7ecbf-133">If you are an administrator of the machine, you should configure it to allocate enough memory to support the maximum number of performance counters that can exist at any time.</span></span>  
  
 <span data-ttu-id="7ecbf-134">Můžete změnit množství paměti čítače výkonu pro kategorie WCF v registru.</span><span class="sxs-lookup"><span data-stu-id="7ecbf-134">You can change the amount of performance counter memory for WCF categories in the registry.</span></span> <span data-ttu-id="7ecbf-135">K tomu je potřeba přidat novou hodnotu DWORD s názvem `FileMappingSize` do tří následujících umístění a nastavit ji na požadovanou hodnotu v bajtech.</span><span class="sxs-lookup"><span data-stu-id="7ecbf-135">To do so, you need to add a new DWORD value named `FileMappingSize` to the three following locations, and set it to the desired value in bytes.</span></span> <span data-ttu-id="7ecbf-136">Restartujte počítač, aby byly tyto změny uplatněny.</span><span class="sxs-lookup"><span data-stu-id="7ecbf-136">Reboot your machine so that these changes are taken into effect.</span></span>  
  
- <span data-ttu-id="7ecbf-137">HKLM\System\CurrentControlSet\Services\ServiceModelEndpoint 4.0.0.0\Performance</span><span class="sxs-lookup"><span data-stu-id="7ecbf-137">HKLM\System\CurrentControlSet\Services\ServiceModelEndpoint 4.0.0.0\Performance</span></span>  
  
- <span data-ttu-id="7ecbf-138">HKLM\System\CurrentControlSet\Services\ServiceModelOperation 4.0.0.0\Performance</span><span class="sxs-lookup"><span data-stu-id="7ecbf-138">HKLM\System\CurrentControlSet\Services\ServiceModelOperation 4.0.0.0\Performance</span></span>  
  
- <span data-ttu-id="7ecbf-139">HKLM\System\CurrentControlSet\Services\ServiceModelService 4.0.0.0\Performance</span><span class="sxs-lookup"><span data-stu-id="7ecbf-139">HKLM\System\CurrentControlSet\Services\ServiceModelService 4.0.0.0\Performance</span></span>  
  
 <span data-ttu-id="7ecbf-140">V případě, že je v případě, že je uvolněno uvolňování paměti, vyřadí velký počet objektů (například ServiceHost), čítač výkonu `PrivateBytes` zaregistruje neobvykle vysoké číslo.</span><span class="sxs-lookup"><span data-stu-id="7ecbf-140">When a large number of objects (for example, ServiceHost) are disposed of but waiting to be garbage-collected, the `PrivateBytes` performance counter will register an unusually high number.</span></span> <span data-ttu-id="7ecbf-141">Chcete-li tento problém vyřešit, můžete buď přidat vlastní čítače specifické pro danou aplikaci, nebo pomocí atributu `performanceCounters` povolit pouze čítače na úrovni služby.</span><span class="sxs-lookup"><span data-stu-id="7ecbf-141">To resolve this problem, you can either add your own application-specific counters, or use the `performanceCounters` attribute to enable only service-level counters.</span></span>  
  
## <a name="types-of-performance-counters"></a><span data-ttu-id="7ecbf-142">Typy čítačů výkonu</span><span class="sxs-lookup"><span data-stu-id="7ecbf-142">Types of Performance Counters</span></span>  
 <span data-ttu-id="7ecbf-143">Čítače výkonu jsou vymezeny na tři různé úrovně: služba, koncový bod a operace.</span><span class="sxs-lookup"><span data-stu-id="7ecbf-143">Performance counters are scoped to three different levels: Service, Endpoint and Operation.</span></span>  
  
 <span data-ttu-id="7ecbf-144">Pomocí rozhraní WMI můžete načíst název instance čítače výkonu.</span><span class="sxs-lookup"><span data-stu-id="7ecbf-144">You can use WMI to retrieve the name of a performance counter instance.</span></span> <span data-ttu-id="7ecbf-145">Například</span><span class="sxs-lookup"><span data-stu-id="7ecbf-145">For example,</span></span>  
  
- <span data-ttu-id="7ecbf-146">Název instance čítače služby se dá získat prostřednictvím vlastnosti CounterInstanceName instance [služby](../wmi/service.md) WMI.</span><span class="sxs-lookup"><span data-stu-id="7ecbf-146">Service counter instance name can be obtained through WMI [Service](../wmi/service.md) instance's "CounterInstanceName" property.</span></span>  
  
- <span data-ttu-id="7ecbf-147">Název instance čítače koncového bodu se dá získat pomocí vlastnosti CounterInstanceName instance [koncového bodu](../wmi/endpoint.md) služby WMI.</span><span class="sxs-lookup"><span data-stu-id="7ecbf-147">Endpoint counter instance name can be obtained through WMI [Endpoint](../wmi/endpoint.md) instance's "CounterInstanceName" property.</span></span>  
  
- <span data-ttu-id="7ecbf-148">Název instance čítače operace se dá získat pomocí metody GetOperationCounterInstanceName instance [koncového bodu](../wmi/endpoint.md) služby WMI.</span><span class="sxs-lookup"><span data-stu-id="7ecbf-148">Operation counter instance name can be obtained through WMI [Endpoint](../wmi/endpoint.md) instance's "GetOperationCounterInstanceName" method.</span></span>  
  
 <span data-ttu-id="7ecbf-149">Další informace o rozhraní WMI najdete v tématu [použití rozhraní WMI (Windows Management Instrumentation) pro diagnostiku](../wmi/index.md).</span><span class="sxs-lookup"><span data-stu-id="7ecbf-149">For more information on WMI, see [Using Windows Management Instrumentation for Diagnostics](../wmi/index.md).</span></span>  
  
### <a name="service-performance-counters"></a><span data-ttu-id="7ecbf-150">Čítače výkonu služby</span><span class="sxs-lookup"><span data-stu-id="7ecbf-150">Service performance counters</span></span>  
 <span data-ttu-id="7ecbf-151">Čítače výkonu služby měří chování služby jako celku a dají se použít k diagnostice výkonu celé služby.</span><span class="sxs-lookup"><span data-stu-id="7ecbf-151">Service performance counters measure the service behavior as a whole and can be used to diagnose the performance of the whole service.</span></span> <span data-ttu-id="7ecbf-152">Lze je najít v `ServiceModelService 4.0.0.0` objekt výkonu při zobrazení pomocí nástroje sledování výkonu.</span><span class="sxs-lookup"><span data-stu-id="7ecbf-152">They can be found under the `ServiceModelService 4.0.0.0` performance object when viewing with Performance Monitor.</span></span> <span data-ttu-id="7ecbf-153">Instance jsou pojmenovány pomocí následujícího vzoru:</span><span class="sxs-lookup"><span data-stu-id="7ecbf-153">The instances are named using the following pattern:</span></span>  
  
`ServiceName@ServiceBaseAddress`
  
 <span data-ttu-id="7ecbf-154">Čítač v oboru služby je agregován z čítače v kolekci koncových bodů.</span><span class="sxs-lookup"><span data-stu-id="7ecbf-154">A counter in a service scope is aggregated from counter in a collection of endpoints.</span></span>  
  
 <span data-ttu-id="7ecbf-155">Čítače výkonu pro vytvoření instance služby se zvýší při vytvoření nové třídy InstanceContext.</span><span class="sxs-lookup"><span data-stu-id="7ecbf-155">Performance counters for service instance creation are incremented when a new InstanceContext is created.</span></span> <span data-ttu-id="7ecbf-156">Všimněte si, že se vytvoří nová třída InstanceContext, i když obdržíte neaktivační zprávu (s existující službou) nebo když se připojíte k instanci z jedné relace, ukončíte relaci a pak se znovu připojíte z jiné relace.</span><span class="sxs-lookup"><span data-stu-id="7ecbf-156">Note that a new InstanceContext is created even when you receive a non-activating message (with an existing service), or when you connect to an instance from one session, end the session, and then reconnect from another session.</span></span>  
  
### <a name="endpoint-performance-counters"></a><span data-ttu-id="7ecbf-157">Čítače výkonu koncového bodu</span><span class="sxs-lookup"><span data-stu-id="7ecbf-157">Endpoint performance counters</span></span>  
 <span data-ttu-id="7ecbf-158">Čítače výkonu koncového bodu umožňují podívat se na data, která odrážejí, jak koncový bod přijímá zprávy.</span><span class="sxs-lookup"><span data-stu-id="7ecbf-158">Endpoint performance counters enable you to look at data reflecting how an endpoint is accepting messages.</span></span> <span data-ttu-id="7ecbf-159">Lze je najít v `ServiceModelEndpoint 4.0.0.0` objekt výkonu při zobrazení pomocí nástroje sledování výkonu.</span><span class="sxs-lookup"><span data-stu-id="7ecbf-159">They can be found under the `ServiceModelEndpoint 4.0.0.0` performance object when viewing using the Performance Monitor.</span></span> <span data-ttu-id="7ecbf-160">Instance jsou pojmenovány pomocí následujícího vzoru:</span><span class="sxs-lookup"><span data-stu-id="7ecbf-160">The instances are named using the following pattern:</span></span>  
  
`(ServiceName).(ContractName)@(endpoint listener address)`
  
 <span data-ttu-id="7ecbf-161">Data jsou podobná tomu, co se shromažďují pro jednotlivé operace, ale agreguje se jenom v rámci koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="7ecbf-161">The data is similar to what is collected for individual operations, but is only aggregated across the endpoint.</span></span>  
  
 <span data-ttu-id="7ecbf-162">Čítač v rozsahu koncového bodu je agregovaný z čítačů v kolekci operací.</span><span class="sxs-lookup"><span data-stu-id="7ecbf-162">A counter in an endpoint scope is aggregated from counters in a collection of operations.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7ecbf-163">Pokud dva koncové body mají stejné názvy kontraktů a adres, jsou namapovány na stejnou instanci čítače.</span><span class="sxs-lookup"><span data-stu-id="7ecbf-163">If two endpoints have identical contract names and addresses, they are mapped to the same counter instance.</span></span>  
  
### <a name="operation-performance-counters"></a><span data-ttu-id="7ecbf-164">Čítače výkonu operací</span><span class="sxs-lookup"><span data-stu-id="7ecbf-164">Operation performance counters</span></span>  
 <span data-ttu-id="7ecbf-165">Čítače výkonu operace se při zobrazení s monitorováním výkonu nacházejí v objektu `ServiceModelOperation 4.0.0.0`ho výkonu.</span><span class="sxs-lookup"><span data-stu-id="7ecbf-165">Operation performance counters are found under the `ServiceModelOperation 4.0.0.0` performance object when viewing with the Performance Monitor.</span></span> <span data-ttu-id="7ecbf-166">Každá operace má jednotlivou instanci.</span><span class="sxs-lookup"><span data-stu-id="7ecbf-166">Each operation has an individual instance.</span></span> <span data-ttu-id="7ecbf-167">To znamená, že pokud má daný kontrakt 10 operací, je k této smlouvě přidruženo 10 instancí čítače operací.</span><span class="sxs-lookup"><span data-stu-id="7ecbf-167">That is, if a given contract has 10 operations, 10 operation counter instances are associated with that contract.</span></span> <span data-ttu-id="7ecbf-168">Instance objektů jsou pojmenovány pomocí následujícího vzoru:</span><span class="sxs-lookup"><span data-stu-id="7ecbf-168">The object instances are named using the following pattern:</span></span>  
  
`(ServiceName).(ContractName).(OperationName)@(first endpoint listener address)`
  
 <span data-ttu-id="7ecbf-169">Tento čítač vám umožní změřit způsob, jakým se volání používá, a to, jak dobře probíhá operace.</span><span class="sxs-lookup"><span data-stu-id="7ecbf-169">This counter enables you to measure how the call is being used and how well the operation is performing.</span></span>  
  
 <span data-ttu-id="7ecbf-170">Když jsou čítače viditelné ve více oborech, data shromážděná z většího rozsahu jsou agregována s daty z nižších rozsahů.</span><span class="sxs-lookup"><span data-stu-id="7ecbf-170">When counters are visible at multiple scopes, data gathered from a higher scope are aggregated with data from lower scopes.</span></span> <span data-ttu-id="7ecbf-171">Například `Calls` na koncovém bodu představuje součet všech volání operace v rámci koncového bodu; `Calls` ve službě představuje součet všech volání všech koncových bodů v rámci služby.</span><span class="sxs-lookup"><span data-stu-id="7ecbf-171">For example, `Calls` at an endpoint represents the sum of all operation calls within the endpoint; `Calls` at a service represents the sum of all calls to all endpoints within the service.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7ecbf-172">Pokud ve smlouvě máte duplicitní názvy operací, získáte pro obě operace jenom jednu instanci čítače.</span><span class="sxs-lookup"><span data-stu-id="7ecbf-172">If you have duplicate operation names on a contract, you only get one counter instances for both operations.</span></span>  
  
## <a name="programming-the-wcf-performance-counters"></a><span data-ttu-id="7ecbf-173">Programování čítačů výkonu WCF</span><span class="sxs-lookup"><span data-stu-id="7ecbf-173">Programming the WCF Performance Counters</span></span>  

<span data-ttu-id="7ecbf-174">V instalační složce sady SDK je nainstalováno několik souborů, aby bylo možné získat přístup k čítačům výkonu WCF programově.</span><span class="sxs-lookup"><span data-stu-id="7ecbf-174">Several files are installed in the SDK install folder so that you can access the WCF performance counters programmatically.</span></span> <span data-ttu-id="7ecbf-175">Tyto soubory jsou uvedené níže:</span><span class="sxs-lookup"><span data-stu-id="7ecbf-175">These files are listed as follows:</span></span>
  
- <span data-ttu-id="7ecbf-176">*\_ServiceModelEndpointPerfCounters. vrg*</span><span class="sxs-lookup"><span data-stu-id="7ecbf-176">*\_ServiceModelEndpointPerfCounters.vrg*</span></span>
- <span data-ttu-id="7ecbf-177">*\_ServiceModelOperationPerfCounters. vrg*</span><span class="sxs-lookup"><span data-stu-id="7ecbf-177">*\_ServiceModelOperationPerfCounters.vrg*</span></span>
- <span data-ttu-id="7ecbf-178">*\_ServiceModelServicePerfCounters. vrg*</span><span class="sxs-lookup"><span data-stu-id="7ecbf-178">*\_ServiceModelServicePerfCounters.vrg*</span></span>  
- <span data-ttu-id="7ecbf-179">*\_SMSvcHostPerfCounters. vrg*</span><span class="sxs-lookup"><span data-stu-id="7ecbf-179">*\_SMSvcHostPerfCounters.vrg*</span></span>
- <span data-ttu-id="7ecbf-180">*\_TransactionBridgePerfCounters. vrg*</span><span class="sxs-lookup"><span data-stu-id="7ecbf-180">*\_TransactionBridgePerfCounters.vrg*</span></span>
  
<span data-ttu-id="7ecbf-181">Další informace o tom, jak programově přistupovat k čítačům, najdete v tématu [Architektura programování čítače výkonu](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/5f9bkxzf(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="7ecbf-181">For more information on how to access the counters programmatically, see [Performance Counter Programming Architecture](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/5f9bkxzf(v=vs.90)).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="7ecbf-182">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7ecbf-182">See also</span></span>

- [<span data-ttu-id="7ecbf-183">Správa a diagnostika</span><span class="sxs-lookup"><span data-stu-id="7ecbf-183">Administration and Diagnostics</span></span>](../index.md)
