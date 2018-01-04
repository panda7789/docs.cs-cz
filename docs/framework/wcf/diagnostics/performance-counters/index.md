---
title: "Čítače výkonu WCF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: performance counters [WCF]
ms.assetid: f559b2bd-ed83-4988-97a1-e88f06646609
caps.latest.revision: "37"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: be4ffac8444f6365dacb2b20db6abbb6792c2239
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="wcf-performance-counters"></a><span data-ttu-id="5a325-102">Čítače výkonu WCF</span><span class="sxs-lookup"><span data-stu-id="5a325-102">WCF Performance Counters</span></span>
[!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]<span data-ttu-id="5a325-103">obsahuje velké sady čítačů výkonu můžete měřit výkon vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="5a325-103"> includes a large set of performance counters to help you gauge your application's performance.</span></span>  
  
## <a name="enabling-performance-counters"></a><span data-ttu-id="5a325-104">Povolení čítače výkonu</span><span class="sxs-lookup"><span data-stu-id="5a325-104">Enabling Performance Counters</span></span>  
 <span data-ttu-id="5a325-105">Můžete povolit čítače výkonu pro [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] přes z konfiguračního souboru app.config [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] služby následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="5a325-105">You can enable performance counters for a [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] service through the app.config configuration file of the [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] service as follows:</span></span>  
  
```xml  
<configuration>  
    <system.serviceModel>  
        <diagnostics performanceCounters="All" />  
    </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="5a325-106">`performanceCounters` Atributu můžete nastavit pro povolení určitý typ čítače výkonu.</span><span class="sxs-lookup"><span data-stu-id="5a325-106">The `performanceCounters` attribute can be set to enable a specific type of performance counters.</span></span> <span data-ttu-id="5a325-107">Platné hodnoty jsou</span><span class="sxs-lookup"><span data-stu-id="5a325-107">Valid values are</span></span>  
  
-   <span data-ttu-id="5a325-108">All: Všechny kategorie čítače (ServiceModelService, ServiceModelEndpoint a ServiceModelOperation) jsou povoleny.</span><span class="sxs-lookup"><span data-stu-id="5a325-108">All: All category counters (ServiceModelService, ServiceModelEndpoint and ServiceModelOperation) are enabled.</span></span>  
  
-   <span data-ttu-id="5a325-109">ServiceOnly: Jsou povoleny pouze ServiceModelService kategorie čítače.</span><span class="sxs-lookup"><span data-stu-id="5a325-109">ServiceOnly: Only ServiceModelService category counters are enabled.</span></span> <span data-ttu-id="5a325-110">Jedná se o výchozí hodnotu.</span><span class="sxs-lookup"><span data-stu-id="5a325-110">This is the default value.</span></span>  
  
-   <span data-ttu-id="5a325-111">Vypnuto: Čítače výkonu ServiceModel * jsou zakázány.</span><span class="sxs-lookup"><span data-stu-id="5a325-111">Off: ServiceModel* performance counters are disabled.</span></span>  
  
 <span data-ttu-id="5a325-112">Pokud chcete povolit čítače výkonu pro všechny [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] aplikace, nastavení konfigurace můžete umístit v souboru Machine.config.</span><span class="sxs-lookup"><span data-stu-id="5a325-112">If you want to enable performance counters for all [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] applications, you can place the configuration settings in the Machine.config file.</span></span>  <span data-ttu-id="5a325-113">Najdete v tématu **zvýšit velikost paměti pro čítače výkonu** části níže pro další informace o konfiguraci dostatek paměti pro čítače výkonu v počítači.</span><span class="sxs-lookup"><span data-stu-id="5a325-113">Please see the **Increasing Memory Size for Performance Counters** section below for more information on configuring sufficient memory for performance counters on your machine.</span></span>  
  
 <span data-ttu-id="5a325-114">Pokud používáte [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] body rozšiřitelnosti například vlastní operaci invokers jste měli také emitování čítače výkonu.</span><span class="sxs-lookup"><span data-stu-id="5a325-114">If you use [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] extensibility points such as custom operation invokers, you should also emit your own performance counters.</span></span> <span data-ttu-id="5a325-115">Je to proto, pokud byste implementovat bod rozšiřitelnosti, [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] může už negeneruje data čítače výkonu standardní ve výchozí cestě.</span><span class="sxs-lookup"><span data-stu-id="5a325-115">This is because if you implement an extensibility point, [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] may no longer emit the standard performance counter data in the default path.</span></span> <span data-ttu-id="5a325-116">Pokud jste neimplementuje podporu čítače výkonu ruční, nemusíte vidět data čítače výkonu, které očekáváte.</span><span class="sxs-lookup"><span data-stu-id="5a325-116">If you do not implement manual performance counter support, you may not see the performance counter data you expect.</span></span>  
  
 <span data-ttu-id="5a325-117">Můžete také povolit čítače výkonu ve vašem kódu následujícím způsobem</span><span class="sxs-lookup"><span data-stu-id="5a325-117">You can also enable performance counters in your code as follows,</span></span>  
  
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
  
## <a name="viewing-performance-data"></a><span data-ttu-id="5a325-118">Zobrazení dat výkonu</span><span class="sxs-lookup"><span data-stu-id="5a325-118">Viewing Performance Data</span></span>  
 <span data-ttu-id="5a325-119">Chcete-li zobrazit data zaznamenaná podle čítače výkonu, můžete použít sledování výkonu (Perfmon.exe), která se dodává s Windows.</span><span class="sxs-lookup"><span data-stu-id="5a325-119">To view data captured by the performance counters, you can use the Performance Monitor (Perfmon.exe) that comes with Windows.</span></span> <span data-ttu-id="5a325-120">Tento nástroj můžete spustit přechodem na **spustit**a klikněte na tlačítko **spustit** a typ `perfmon.exe` v dialogovém okně.</span><span class="sxs-lookup"><span data-stu-id="5a325-120">You can launch this tool by going to **Start**, and click **Run** and type `perfmon.exe` in the dialog box.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5a325-121">Instance čítače výkonu se může uvolnit před poslední zprávy byly zpracovány dispečera koncový bod.</span><span class="sxs-lookup"><span data-stu-id="5a325-121">Performance counter instances may be released before the last messages have been processed by the endpoint dispatcher.</span></span> <span data-ttu-id="5a325-122">Výsledkem může být data výkonu není zaznamenaná pro několik zprávy.</span><span class="sxs-lookup"><span data-stu-id="5a325-122">This can result in performance data not being captured for a few messages.</span></span>  
  
## <a name="increasing-memory-size-for-performance-counters"></a><span data-ttu-id="5a325-123">Zvýšit velikost paměti pro čítače výkonu</span><span class="sxs-lookup"><span data-stu-id="5a325-123">Increasing Memory Size for Performance Counters</span></span>  
 [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)]<span data-ttu-id="5a325-124">používá samostatné sdílené paměti pro jeho kategorie čítače výkonu.</span><span class="sxs-lookup"><span data-stu-id="5a325-124"> uses separate shared memory for its performance counter categories.</span></span>  
  
 <span data-ttu-id="5a325-125">Ve výchozím nastavení je samostatnou sdílené paměti hodnotu čtvrtletí velikost globálního výkonu čítače paměti.</span><span class="sxs-lookup"><span data-stu-id="5a325-125">By default, separate shared memory is set to a quarter the size of global performance counter memory.</span></span> <span data-ttu-id="5a325-126">Výchozí globální výkonu čítač paměť je 524,288 bajtů.</span><span class="sxs-lookup"><span data-stu-id="5a325-126">The default global performance counter memory is 524,288 bytes.</span></span> <span data-ttu-id="5a325-127">Proto tří [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] kategorie čítače výkonu mají výchozí velikost přibližně 128 KB.</span><span class="sxs-lookup"><span data-stu-id="5a325-127">Therefore, the three [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] performance counter categories have a default size of approximately 128KB each.</span></span> <span data-ttu-id="5a325-128">V závislosti na vlastnosti runtime [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] může dojít k vyčerpání aplikace na počítači, paměti čítače výkonu.</span><span class="sxs-lookup"><span data-stu-id="5a325-128">Depending upon the runtime characteristics of the [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] applications on a machine, performance counter memory may be exhausted.</span></span> <span data-ttu-id="5a325-129">V takovém případě [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] zapíše chybu do protokolu událostí aplikace.</span><span class="sxs-lookup"><span data-stu-id="5a325-129">When this happens, [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] writes an error to the application event log.</span></span> <span data-ttu-id="5a325-130">Obsah chyba stavy nebyla načtena čítače výkonu, a položka obsahuje výjimku "System.InvalidOperationException: vlastní čítače souboru zobrazení je nedostatek paměti."</span><span class="sxs-lookup"><span data-stu-id="5a325-130">The content of the error states that a performance counter was not loaded, and the entry contains the exception "System.InvalidOperationException: Custom counters file view is out of memory."</span></span> <span data-ttu-id="5a325-131">Pokud je trasování povoleno na úrovni chyba, toto selhání je také trasovat.</span><span class="sxs-lookup"><span data-stu-id="5a325-131">If tracing is enabled at the error level, this failure is also traced.</span></span> <span data-ttu-id="5a325-132">Pokud dojde k vyčerpání paměti čítače výkonu, pokračování v používání vaší [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] aplikací pomocí čítače výkonu, které jsou povolené může způsobit snížení výkonu.</span><span class="sxs-lookup"><span data-stu-id="5a325-132">If performance counter memory is exhausted, continuing to run your [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] applications with performance counters enabled could result in performance degradation.</span></span> <span data-ttu-id="5a325-133">Pokud jste správce počítače, byste ho měli nakonfigurovat přidělit dostatek paměti pro podporu maximální počet čítače výkonu, které může existovat kdykoli.</span><span class="sxs-lookup"><span data-stu-id="5a325-133">If you are an administrator of the machine, you should configure it to allocate enough memory to support the maximum number of performance counters that can exist at any time.</span></span>  
  
 <span data-ttu-id="5a325-134">Můžete změnit velikost paměti čítače výkonu pro [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] kategorií v registru.</span><span class="sxs-lookup"><span data-stu-id="5a325-134">You can change the amount of performance counter memory for [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] categories in the registry.</span></span> <span data-ttu-id="5a325-135">To pokud chcete udělat, je nutné přidat novou hodnotu DWORD s názvem `FileMappingSize` do tří následujících umístění a nastavte ji na požadovanou hodnotu v bajtech.</span><span class="sxs-lookup"><span data-stu-id="5a325-135">To do so, you need to add a new DWORD value named `FileMappingSize` to the three following locations, and set it to the desired value in bytes.</span></span> <span data-ttu-id="5a325-136">Restartujte svůj počítač tak, aby se projevily změny.</span><span class="sxs-lookup"><span data-stu-id="5a325-136">Reboot your machine so that these changes are taken into effect.</span></span>  
  
-   <span data-ttu-id="5a325-137">HKLM\System\CurrentControlSet\Services\ServiceModelEndpoint 4.0.0.0\Performance</span><span class="sxs-lookup"><span data-stu-id="5a325-137">HKLM\System\CurrentControlSet\Services\ServiceModelEndpoint 4.0.0.0\Performance</span></span>  
  
-   <span data-ttu-id="5a325-138">HKLM\System\CurrentControlSet\Services\ServiceModelOperation 4.0.0.0\Performance</span><span class="sxs-lookup"><span data-stu-id="5a325-138">HKLM\System\CurrentControlSet\Services\ServiceModelOperation 4.0.0.0\Performance</span></span>  
  
-   <span data-ttu-id="5a325-139">HKLM\System\CurrentControlSet\Services\ServiceModelService 4.0.0.0\Performance</span><span class="sxs-lookup"><span data-stu-id="5a325-139">HKLM\System\CurrentControlSet\Services\ServiceModelService 4.0.0.0\Performance</span></span>  
  
 <span data-ttu-id="5a325-140">Když jsou odstraněny velký počet objektů (například ServiceHost), ale čeká na uklizeny, `PrivateBytes` čítače výkonu se registrují neobvykle vysoké číslo.</span><span class="sxs-lookup"><span data-stu-id="5a325-140">When a large number of objects (for example, ServiceHost) are disposed of but waiting to be garbage-collected, the `PrivateBytes` performance counter will register an unusually high number.</span></span> <span data-ttu-id="5a325-141">Chcete-li vyřešit tento problém, můžete buď přidejte vlastní čítače specifické pro aplikace nebo použijte `performanceCounters` atribut pro povolení čítače pouze úrovně služby.</span><span class="sxs-lookup"><span data-stu-id="5a325-141">To resolve this problem, you can either add your own application-specific counters, or use the `performanceCounters` attribute to enable only service-level counters.</span></span>  
  
## <a name="types-of-performance-counters"></a><span data-ttu-id="5a325-142">Typy čítačů výkonu</span><span class="sxs-lookup"><span data-stu-id="5a325-142">Types of Performance Counters</span></span>  
 <span data-ttu-id="5a325-143">Čítače výkonu jsou omezená na tři různé úrovně: služby, koncový bod a operace.</span><span class="sxs-lookup"><span data-stu-id="5a325-143">Performance counters are scoped to three different levels: Service, Endpoint and Operation.</span></span>  
  
 <span data-ttu-id="5a325-144">Můžete načíst název instance čítače výkonu služby WMI.</span><span class="sxs-lookup"><span data-stu-id="5a325-144">You can use WMI to retrieve the name of a performance counter instance.</span></span> <span data-ttu-id="5a325-145">Například</span><span class="sxs-lookup"><span data-stu-id="5a325-145">For example,</span></span>  
  
-   <span data-ttu-id="5a325-146">Název instance čítače služby můžete získat prostřednictvím služby WMI [služby](../../../../../docs/framework/wcf/diagnostics/wmi/service.md) "CounterInstanceName" vlastnost instance.</span><span class="sxs-lookup"><span data-stu-id="5a325-146">Service counter instance name can be obtained through WMI [Service](../../../../../docs/framework/wcf/diagnostics/wmi/service.md) instance's "CounterInstanceName" property.</span></span>  
  
-   <span data-ttu-id="5a325-147">Název instance čítače koncového bodu můžete získat prostřednictvím služby WMI [koncový bod](../../../../../docs/framework/wcf/diagnostics/wmi/endpoint.md) "CounterInstanceName" vlastnost instance.</span><span class="sxs-lookup"><span data-stu-id="5a325-147">Endpoint counter instance name can be obtained through WMI [Endpoint](../../../../../docs/framework/wcf/diagnostics/wmi/endpoint.md) instance's "CounterInstanceName" property.</span></span>  
  
-   <span data-ttu-id="5a325-148">Název instance čítače operace můžete získat prostřednictvím služby WMI [koncový bod](../../../../../docs/framework/wcf/diagnostics/wmi/endpoint.md) metodu instance "GetOperationCounterInstanceName".</span><span class="sxs-lookup"><span data-stu-id="5a325-148">Operation counter instance name can be obtained through WMI [Endpoint](../../../../../docs/framework/wcf/diagnostics/wmi/endpoint.md) instance's "GetOperationCounterInstanceName" method.</span></span>  
  
 <span data-ttu-id="5a325-149">Další informace o rozhraní WMI najdete v tématu [pomocí rozhraní Windows Management Instrumentation pro diagnostiku](../../../../../docs/framework/wcf/diagnostics/wmi/index.md).</span><span class="sxs-lookup"><span data-stu-id="5a325-149">For more information on WMI, see [Using Windows Management Instrumentation for Diagnostics](../../../../../docs/framework/wcf/diagnostics/wmi/index.md).</span></span>  
  
### <a name="service-performance-counters"></a><span data-ttu-id="5a325-150">Čítače výkonu služby</span><span class="sxs-lookup"><span data-stu-id="5a325-150">Service performance counters</span></span>  
 <span data-ttu-id="5a325-151">Čítače výkonu služby měřit chování služby jako celek a umožňuje diagnostikovat provádění celou služeb.</span><span class="sxs-lookup"><span data-stu-id="5a325-151">Service performance counters measure the service behavior as a whole and can be used to diagnose the performance of the whole service.</span></span> <span data-ttu-id="5a325-152">Najdete v části `ServiceModelService 4.0.0.0` objekt výkonu při zobrazení pomocí sledování výkonu.</span><span class="sxs-lookup"><span data-stu-id="5a325-152">They can be found under the `ServiceModelService 4.0.0.0` performance object when viewing with Performance Monitor.</span></span> <span data-ttu-id="5a325-153">Instance jsou pojmenované pomocí následujícího vzorce:</span><span class="sxs-lookup"><span data-stu-id="5a325-153">The instances are named using the following pattern:</span></span>  
  
```  
ServiceName@ServiceBaseAddress  
```  
  
 <span data-ttu-id="5a325-154">Čítače v oboru služby se shromažďují z čítače v kolekci koncových bodů.</span><span class="sxs-lookup"><span data-stu-id="5a325-154">A counter in a service scope is aggregated from counter in a collection of endpoints.</span></span>  
  
 <span data-ttu-id="5a325-155">Čítače výkonu pro vytvoření instance služby se zvýší, když se vytvoří nový objekt InstanceContext.</span><span class="sxs-lookup"><span data-stu-id="5a325-155">Performance counters for service instance creation are incremented when a new InstanceContext is created.</span></span> <span data-ttu-id="5a325-156">Všimněte si, že i když obdržíte zprávu bez aktivace (s existující službu), nebo při připojení k instanci z jedné relace, ukončením relace a poté znovu připojit z jiné relace je vytvořen nový objekt InstanceContext.</span><span class="sxs-lookup"><span data-stu-id="5a325-156">Note that a new InstanceContext is created even when you receive a non-activating message (with an existing service), or when you connect to an instance from one session, end the session, and then reconnect from another session.</span></span>  
  
### <a name="endpoint-performance-counters"></a><span data-ttu-id="5a325-157">Čítače výkonu koncového bodu</span><span class="sxs-lookup"><span data-stu-id="5a325-157">Endpoint performance counters</span></span>  
 <span data-ttu-id="5a325-158">Čítače výkonu koncového bodu umožňují podívejte se na data, která znázorňuje, jak koncový bod přijímá zprávy.</span><span class="sxs-lookup"><span data-stu-id="5a325-158">Endpoint performance counters enable you to look at data reflecting how an endpoint is accepting messages.</span></span> <span data-ttu-id="5a325-159">Najdete v části `ServiceModelEndpoint 4.0.0.0` objekt výkonu při zobrazení pomocí sledování výkonu.</span><span class="sxs-lookup"><span data-stu-id="5a325-159">They can be found under the `ServiceModelEndpoint 4.0.0.0` performance object when viewing using the Performance Monitor.</span></span> <span data-ttu-id="5a325-160">Instance jsou pojmenované pomocí následujícího vzorce:</span><span class="sxs-lookup"><span data-stu-id="5a325-160">The instances are named using the following pattern:</span></span>  
  
```  
(ServiceName).(ContractName)@(endpoint listener address)  
```  
  
 <span data-ttu-id="5a325-161">Data je podobná co se shromažďují pro jednotlivé operace, ale je pouze agregován přes koncový bod.</span><span class="sxs-lookup"><span data-stu-id="5a325-161">The data is similar to what is collected for individual operations, but is only aggregated across the endpoint.</span></span>  
  
 <span data-ttu-id="5a325-162">Čítače v oboru koncový bod se shromažďují z čítačů v kolekci operací.</span><span class="sxs-lookup"><span data-stu-id="5a325-162">A counter in an endpoint scope is aggregated from counters in a collection of operations.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5a325-163">Pokud dva koncové body mají stejné kontrakt názvy a adresy, jsou namapované na stejnou instanci čítače.</span><span class="sxs-lookup"><span data-stu-id="5a325-163">If two endpoints have identical contract names and addresses, they are mapped to the same counter instance.</span></span>  
  
### <a name="operation-performance-counters"></a><span data-ttu-id="5a325-164">Čítače provozního výkonu</span><span class="sxs-lookup"><span data-stu-id="5a325-164">Operation performance counters</span></span>  
 <span data-ttu-id="5a325-165">Čítače provozního výkonu se nacházejí v části `ServiceModelOperation 4.0.0.0` objekt výkonu při zobrazení pomocí sledování výkonu.</span><span class="sxs-lookup"><span data-stu-id="5a325-165">Operation performance counters are found under the `ServiceModelOperation 4.0.0.0` performance object when viewing with the Performance Monitor.</span></span> <span data-ttu-id="5a325-166">Každá operace má jednotlivé instance.</span><span class="sxs-lookup"><span data-stu-id="5a325-166">Each operation has an individual instance.</span></span> <span data-ttu-id="5a325-167">To znamená Pokud danou zakázku má 10 operace, 10 instancí čítače operace jsou přidruženy k této smlouvy.</span><span class="sxs-lookup"><span data-stu-id="5a325-167">That is, if a given contract has 10 operations, 10 operation counter instances are associated with that contract.</span></span> <span data-ttu-id="5a325-168">Instance objektů jsou pojmenované pomocí následujícího vzorce:</span><span class="sxs-lookup"><span data-stu-id="5a325-168">The object instances are named using the following pattern:</span></span>  
  
```  
(ServiceName).(ContractName).(OperationName)@(first endpoint listener address)  
```  
  
 <span data-ttu-id="5a325-169">Tento čítač umožňuje měření využití volání a jak dobře fungují operaci.</span><span class="sxs-lookup"><span data-stu-id="5a325-169">This counter enables you to measure how the call is being used and how well the operation is performing.</span></span>  
  
 <span data-ttu-id="5a325-170">Pokud čítače jsou viditelné na víc oborů, jsou data shromážděná z vyššího oboru agregován s daty z nižší oborů.</span><span class="sxs-lookup"><span data-stu-id="5a325-170">When counters are visible at multiple scopes, data gathered from a higher scope are aggregated with data from lower scopes.</span></span> <span data-ttu-id="5a325-171">Například `Calls` na koncový bod představuje součet hodnot všechna volání operace v rámci koncový bod; `Calls` na službu představuje součet hodnot všechna volání všechny koncové body v rámci služby.</span><span class="sxs-lookup"><span data-stu-id="5a325-171">For example, `Calls` at an endpoint represents the sum of all operation calls within the endpoint; `Calls` at a service represents the sum of all calls to all endpoints within the service.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5a325-172">Pokud máte operaci duplicitní názvy na kontraktu, zobrazí pouze jedna instance čítače pro obě operace.</span><span class="sxs-lookup"><span data-stu-id="5a325-172">If you have duplicate operation names on a contract, you only get one counter instances for both operations.</span></span>  
  
## <a name="programming-the-wcf-performance-counters"></a><span data-ttu-id="5a325-173">Programování čítače výkonu WCF</span><span class="sxs-lookup"><span data-stu-id="5a325-173">Programming the WCF Performance Counters</span></span>  
 <span data-ttu-id="5a325-174">Několik souborů jsou nainstalovány ve složce instalace sady SDK, takže může získat přístup [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] čítače výkonu prostřednictvím kódu programu.</span><span class="sxs-lookup"><span data-stu-id="5a325-174">Several files are installed in the SDK install folder so that you can access the [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] performance counters programmatically.</span></span> <span data-ttu-id="5a325-175">Tyto soubory jsou uvedené následujícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="5a325-175">These files are listed as follows.</span></span>  
  
-   <span data-ttu-id="5a325-176">_ServiceModelEndpointPerfCounters.vrg</span><span class="sxs-lookup"><span data-stu-id="5a325-176">_ServiceModelEndpointPerfCounters.vrg</span></span>  
  
-   <span data-ttu-id="5a325-177">_ServiceModelOperationPerfCounters.vrg</span><span class="sxs-lookup"><span data-stu-id="5a325-177">_ServiceModelOperationPerfCounters.vrg</span></span>  
  
-   <span data-ttu-id="5a325-178">_ServiceModelServicePerfCounters.vrg</span><span class="sxs-lookup"><span data-stu-id="5a325-178">_ServiceModelServicePerfCounters.vrg</span></span>  
  
-   <span data-ttu-id="5a325-179">_SMSvcHostPerfCounters.vrg</span><span class="sxs-lookup"><span data-stu-id="5a325-179">_SMSvcHostPerfCounters.vrg</span></span>  
  
-   <span data-ttu-id="5a325-180">_TransactionBridgePerfCounters.vrg</span><span class="sxs-lookup"><span data-stu-id="5a325-180">_TransactionBridgePerfCounters.vrg</span></span>  
  
 <span data-ttu-id="5a325-181">Další informace o tom, jak počítadla přístup prostřednictvím kódu programu najdete v tématu [architektura programování čítače výkonu](http://go.microsoft.com/fwlink/?LinkId=95179).</span><span class="sxs-lookup"><span data-stu-id="5a325-181">For more information on how to access the counters programmatically, see [Performance Counter Programming Architecture](http://go.microsoft.com/fwlink/?LinkId=95179).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a325-182">Viz také</span><span class="sxs-lookup"><span data-stu-id="5a325-182">See Also</span></span>  
 [<span data-ttu-id="5a325-183">Správa a diagnostika</span><span class="sxs-lookup"><span data-stu-id="5a325-183">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
