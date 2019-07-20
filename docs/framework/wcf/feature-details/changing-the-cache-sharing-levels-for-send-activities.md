---
title: Změna úrovní sdílení mezipaměti pro aktivity odesílání
ms.date: 03/30/2017
ms.assetid: 03926a64-753d-460e-ac06-2a4ff8e1bbf5
ms.openlocfilehash: ac4f2e4fe85d6b243999add6bda65f4fb202f79c
ms.sourcegitcommit: 30a83efb57c468da74e9e218de26cf88d3254597
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/20/2019
ms.locfileid: "68363835"
---
# <a name="changing-the-cache-sharing-levels-for-send-activities"></a><span data-ttu-id="671a1-102">Změna úrovní sdílení mezipaměti pro aktivity odesílání</span><span class="sxs-lookup"><span data-stu-id="671a1-102">Changing the Cache Sharing Levels for Send Activities</span></span>
<span data-ttu-id="671a1-103">Rozšíření umožňuje přizpůsobit úroveň sdílení mezipaměti, nastavení mezipaměti objektu pro vytváření kanálu a nastavení mezipaměti kanálu pro pracovní postupy, které odesílají zprávy do koncových bodů služby pomocí <xref:System.ServiceModel.Activities.Send> aktivit zasílání zpráv. <xref:System.ServiceModel.Activities.SendMessageChannelCache></span><span class="sxs-lookup"><span data-stu-id="671a1-103">The <xref:System.ServiceModel.Activities.SendMessageChannelCache> extension enables you to customize the cache sharing levels, the settings of the channel factory cache, and the settings of the channel cache for workflows that send messages to service endpoints using <xref:System.ServiceModel.Activities.Send> messaging activities.</span></span> <span data-ttu-id="671a1-104">Tyto pracovní postupy jsou obvykle pracovní postupy klienta, ale mohou být také služby pracovního postupu, které jsou hostovány v <xref:System.ServiceModel.WorkflowServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="671a1-104">These workflows are typically client workflows but could also be workflow services that are hosted in a <xref:System.ServiceModel.WorkflowServiceHost>.</span></span> <span data-ttu-id="671a1-105">Mezipaměť objektu pro vytváření kanálů obsahuje <xref:System.ServiceModel.ChannelFactory%601> objekty v mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="671a1-105">The channel factory cache contains cached <xref:System.ServiceModel.ChannelFactory%601> objects.</span></span> <span data-ttu-id="671a1-106">Mezipaměť kanálu obsahuje kanály v mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="671a1-106">The channel cache contains cached channels.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="671a1-107">Pracovní postupy mohou <xref:System.ServiceModel.Activities.Send> používat aktivity zasílání zpráv k odeslání buď zpráv, nebo parametrů.</span><span class="sxs-lookup"><span data-stu-id="671a1-107">Workflows can use <xref:System.ServiceModel.Activities.Send> messaging activities to send either messages or parameters.</span></span> <span data-ttu-id="671a1-108">Modul runtime pracovního postupu přidává do mezipaměti továrny kanálů, které vytvářejí kanály typu <xref:System.ServiceModel.Channels.IRequestChannel> při <xref:System.ServiceModel.Activities.ReceiveReply> použití aktivity s <xref:System.ServiceModel.Activities.Send> <xref:System.ServiceModel.Activities.Send> aktivitou a <xref:System.ServiceModel.Channels.IOutputChannel> při pouhém použití aktivity (ne <xref:System.ServiceModel.Activities.ReceiveReply>).</span><span class="sxs-lookup"><span data-stu-id="671a1-108">The workflow runtime adds channel factories to the cache that create channels of type <xref:System.ServiceModel.Channels.IRequestChannel> when you use a <xref:System.ServiceModel.Activities.ReceiveReply> activity with a <xref:System.ServiceModel.Activities.Send> activity, and an <xref:System.ServiceModel.Channels.IOutputChannel> when just using a <xref:System.ServiceModel.Activities.Send> activity (no <xref:System.ServiceModel.Activities.ReceiveReply>).</span></span>  
  
## <a name="the-cache-sharing-levels"></a><span data-ttu-id="671a1-109">Úrovně sdílení mezipaměti</span><span class="sxs-lookup"><span data-stu-id="671a1-109">The Cache Sharing Levels</span></span>  
 <span data-ttu-id="671a1-110">Ve výchozím nastavení se v pracovním postupu hostovaném <xref:System.ServiceModel.WorkflowServiceHost> v mezipaměti <xref:System.ServiceModel.Activities.Send> používané aktivity zasílání zpráv sdílí mezi <xref:System.ServiceModel.WorkflowServiceHost> všemi instancemi pracovního postupu v (ukládání do mezipaměti na úrovni hostitele).</span><span class="sxs-lookup"><span data-stu-id="671a1-110">By default, in a workflow hosted by a <xref:System.ServiceModel.WorkflowServiceHost> the cache used by <xref:System.ServiceModel.Activities.Send> messaging activities is shared across all workflow instances in the <xref:System.ServiceModel.WorkflowServiceHost> (host-level caching).</span></span> <span data-ttu-id="671a1-111">Pro klienta pracovní postup, který není hostované <xref:System.ServiceModel.WorkflowServiceHost>, mezipaměť je k dispozici pouze pro instanci pracovního postupu (ukládání do mezipaměti na úrovni instance).</span><span class="sxs-lookup"><span data-stu-id="671a1-111">For a client workflow that is not hosted by a <xref:System.ServiceModel.WorkflowServiceHost>, the cache is available only to the workflow instance (instance-level caching).</span></span> <span data-ttu-id="671a1-112">Mezipaměť je k dispozici pouze <xref:System.ServiceModel.Activities.Send> pro aktivity, které nepoužívají koncové body definované v konfiguraci, pokud není povoleno zabezpečené ukládání do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="671a1-112">The cache is only available for <xref:System.ServiceModel.Activities.Send> activities that do not use endpoints defined in configuration unless unsafe caching is enabled.</span></span>  
  
 <span data-ttu-id="671a1-113">Níže jsou k dispozici různé úrovně sdílení mezipaměti pro <xref:System.ServiceModel.Activities.Send> aktivity v pracovním postupu a jejich Doporučené použití:</span><span class="sxs-lookup"><span data-stu-id="671a1-113">The following are the different cache sharing levels available for <xref:System.ServiceModel.Activities.Send> activities in a workflow and their recommended use:</span></span>  
  
- <span data-ttu-id="671a1-114">**Úroveň hostitele**: V úrovni sdílení hostitelů je mezipaměť dostupná jenom pro instance pracovních postupů hostované v hostiteli služby pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="671a1-114">**Host Level**: In the host sharing level, the cache is available only to the workflow instances hosted in the workflow service host.</span></span> <span data-ttu-id="671a1-115">Mezipaměť lze také sdílet mezi hostiteli služby pracovního postupu v mezipaměti na úrovni procesu.</span><span class="sxs-lookup"><span data-stu-id="671a1-115">A cache can also be shared between workflow service hosts in a process-wide cache.</span></span>  
  
- <span data-ttu-id="671a1-116">**Úroveň instance**: V úrovni sdílení instancí je mezipaměť k dispozici pro konkrétní instanci pracovního postupu po celou dobu své životnosti, ale mezipaměť není k dispozici pro jiné instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="671a1-116">**Instance Level**: In the instance sharing level, the cache is available to a particular workflow instance throughout its lifetime but the cache is not available to other workflow instances.</span></span>  
  
- <span data-ttu-id="671a1-117">**Žádná mezipaměť**: Mezipaměť je ve výchozím nastavení vypnuta v případě, že máte pracovní postup, který používá koncové body definované v konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="671a1-117">**No Cache**: The cache is turned off by default if you have a workflow that uses endpoints defined in configuration.</span></span> <span data-ttu-id="671a1-118">V takovém případě se taky doporučuje uchovávat mezipaměť, protože zapnutí této mezipaměti je nezabezpečené.</span><span class="sxs-lookup"><span data-stu-id="671a1-118">It is also recommended to keep the cache turned off in this case because turning it on could be unsecure.</span></span> <span data-ttu-id="671a1-119">Například pokud je pro každé odeslání vyžadována jiná identita (jiné přihlašovací údaje nebo použití zosobnění).</span><span class="sxs-lookup"><span data-stu-id="671a1-119">For example, if a different identity (different credentials or using impersonation) is required for each send.</span></span>  
  
## <a name="changing-the-cache-sharing-level-for-a-client-workflow"></a><span data-ttu-id="671a1-120">Změna úrovně sdílení mezipaměti pro klientský pracovní postup</span><span class="sxs-lookup"><span data-stu-id="671a1-120">Changing the Cache Sharing Level for a Client Workflow</span></span>  
 <span data-ttu-id="671a1-121">Chcete-li nastavit sdílení mezipaměti v klientském pracovním postupu, přidejte instanci <xref:System.ServiceModel.Activities.SendMessageChannelCache> třídy jako rozšíření do požadované sady instancí pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="671a1-121">To set the cache sharing in a client workflow, add an instance of the <xref:System.ServiceModel.Activities.SendMessageChannelCache> class as an extension to the desired set of workflow instances.</span></span> <span data-ttu-id="671a1-122">Výsledkem je sdílení mezipaměti napříč všemi instancemi pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="671a1-122">This results in sharing the cache across all the workflow instances.</span></span> <span data-ttu-id="671a1-123">Následující příklady kódu ukazují, jak provést tyto kroky.</span><span class="sxs-lookup"><span data-stu-id="671a1-123">The following code examples show how to perform these steps.</span></span>  
  
 <span data-ttu-id="671a1-124">Nejprve deklarujte instanci typu <xref:System.ServiceModel.Activities.SendMessageChannelCache>.</span><span class="sxs-lookup"><span data-stu-id="671a1-124">First, declare an instance of type <xref:System.ServiceModel.Activities.SendMessageChannelCache>.</span></span>  
  
```csharp  
// Create an instance of SendMessageChannelCache with default cache settings.  
static SendMessageChannelCache sharedChannelCacheExtension =  
    new SendMessageChannelCache();  
```  
  
 <span data-ttu-id="671a1-125">Dále přidejte rozšíření mezipaměti do každé instance pracovního postupu klienta.</span><span class="sxs-lookup"><span data-stu-id="671a1-125">Next, add the cache extension to each client workflow instance.</span></span>  
  
```csharp 
WorkflowApplication clientInstance1 = new WorkflowApplication(new clientWorkflow1());  
WorkflowApplication clientInstance2 = new WorkflowApplication(new clientWorkflow2());  
  
// Share the cache extension object   
  
clientInstance1.Extensions.Add(sharedChannelCacheExtension);  
clientInstance2.Extensions.Add(sharedChannelCacheExtension);  
```  
  
## <a name="changing-the-cache-sharing-level-for-a-hosted-workflow-service"></a><span data-ttu-id="671a1-126">Změna úrovně sdílení mezipaměti pro hostovanou službu pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="671a1-126">Changing the Cache Sharing Level for a Hosted Workflow Service</span></span>  
 <span data-ttu-id="671a1-127">Chcete-li nastavit sdílení mezipaměti ve službě hostovaného pracovního postupu, přidejte instanci <xref:System.ServiceModel.Activities.SendMessageChannelCache> třídy jako rozšíření do všech hostitelů služby pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="671a1-127">To set the cache sharing in a hosted workflow service, add an instance of the <xref:System.ServiceModel.Activities.SendMessageChannelCache> class as an extension to all the workflow service hosts.</span></span> <span data-ttu-id="671a1-128">Výsledkem je sdílení mezipaměti ve všech hostitelích služby pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="671a1-128">This results in sharing the cache across all the workflow service hosts.</span></span> <span data-ttu-id="671a1-129">Následující příklady kódu ukazují, jak provést tyto kroky.</span><span class="sxs-lookup"><span data-stu-id="671a1-129">The following code examples show to perform these steps.</span></span>  
  
 <span data-ttu-id="671a1-130">Nejprve deklarujte instanci typu <xref:System.ServiceModel.Activities.SendMessageChannelCache> na úrovni třídy.</span><span class="sxs-lookup"><span data-stu-id="671a1-130">First, declare an instance  of type <xref:System.ServiceModel.Activities.SendMessageChannelCache> at the class level.</span></span>  
  
```csharp  
// Create static instance of SendMessageChannelCache with default cache settings.  
static SendMessageChannelCache sharedChannelCacheExtension = new  
    SendMessageChannelCache();  
```  
  
 <span data-ttu-id="671a1-131">Dále přidejte rozšíření statické mezipaměti do každého hostitele služby pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="671a1-131">Next, add the static cache extension to each workflow service host.</span></span>  
  
```csharp  
WorkflowServiceHost host1 = new WorkflowServiceHost(new serviceWorkflow1(), new Uri(baseAddress1));  
WorkflowServiceHost host2 = new WorkflowServiceHost(new serviceWorkflow2(), new Uri(baseAddress2));  
  
// Share the static cache to get an AppDomain level cache.  
host1.WorkflowExtensions.Add(sharedChannelCacheExtension);  
host2.WorkflowExtensions.Add(sharedChannelCacheExtension);  
```  
  
 <span data-ttu-id="671a1-132">Chcete-li nastavit sdílení mezipaměti ve službě hostovaného pracovního postupu na úrovni instance, přidejte `Func<SendMessageChannelCache>` delegáta jako rozšíření do hostitele služby pracovního postupu a přiřaďte tohoto delegáta kódu, který vytvoří instanci nové instance <xref:System.ServiceModel.Activities.SendMessageChannelCache> třídy.</span><span class="sxs-lookup"><span data-stu-id="671a1-132">To set the cache sharing in a hosted workflow service to the instance level, add a `Func<SendMessageChannelCache>` delegate as an extension to the workflow service host and assign this delegate to the code that instantiates a new instance of the <xref:System.ServiceModel.Activities.SendMessageChannelCache> class.</span></span> <span data-ttu-id="671a1-133">Výsledkem je odlišná mezipaměť pro každou jednotlivou instanci pracovního postupu, a ne jednu mezipaměť sdílenou všemi instancemi pracovního postupu v hostiteli služby pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="671a1-133">This results in a different cache for each individual workflow instance, instead of a single cache shared by all workflow instances in the workflow service host.</span></span> <span data-ttu-id="671a1-134">Následující příklad kódu ukazuje, jak toho dosáhnout pomocí výrazu lambda pro přímé definování <xref:System.ServiceModel.Activities.SendMessageChannelCache> rozšíření, na které tento delegát odkazuje.</span><span class="sxs-lookup"><span data-stu-id="671a1-134">The following code example shows how to achieve this by using a lambda expression to directly define the <xref:System.ServiceModel.Activities.SendMessageChannelCache> extension that the delegate points to.</span></span>  
  
```csharp 
serviceHost.WorkflowExtensions.Add(() => new SendMessageChannelCache  
{  
    // Use FactorySettings property to add custom factory cache settings.  
    FactorySettings = new ChannelCacheSettings   
    { MaxItemsInCache = 5, },  
    // Use ChannelSettings property to add custom channel cache settings.  
    ChannelSettings = new ChannelCacheSettings   
    { MaxItemsInCache = 10 },  
});  
```  
  
## <a name="customizing-cache-settings"></a><span data-ttu-id="671a1-135">Přizpůsobení nastavení mezipaměti</span><span class="sxs-lookup"><span data-stu-id="671a1-135">Customizing Cache Settings</span></span>  
 <span data-ttu-id="671a1-136">Můžete přizpůsobit nastavení mezipaměti pro mezipaměť objektu pro vytváření kanálu a mezipaměť kanálu.</span><span class="sxs-lookup"><span data-stu-id="671a1-136">You can customize the cache settings for the channel factory cache and the channel cache.</span></span> <span data-ttu-id="671a1-137">Nastavení mezipaměti je definováno ve <xref:System.ServiceModel.Activities.ChannelCacheSettings> třídě.</span><span class="sxs-lookup"><span data-stu-id="671a1-137">The cache settings are defined in the <xref:System.ServiceModel.Activities.ChannelCacheSettings> class.</span></span> <span data-ttu-id="671a1-138"><xref:System.ServiceModel.Activities.SendMessageChannelCache> Třída definuje výchozí nastavení mezipaměti pro mezipaměť objektu pro vytváření kanálu a mezipaměť kanálu v jeho konstruktoru bez parametrů.</span><span class="sxs-lookup"><span data-stu-id="671a1-138">The <xref:System.ServiceModel.Activities.SendMessageChannelCache> class defines default cache settings for the channel factory cache and the channel cache in its parameterless constructor.</span></span> <span data-ttu-id="671a1-139">Následující tabulka uvádí výchozí hodnoty těchto nastavení mezipaměti pro každý typ mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="671a1-139">The following table lists the default values of these cache settings for each type of cache.</span></span>  
  
|<span data-ttu-id="671a1-140">Nastavení</span><span class="sxs-lookup"><span data-stu-id="671a1-140">Settings</span></span>|<span data-ttu-id="671a1-141">LeaseTimeout (min)</span><span class="sxs-lookup"><span data-stu-id="671a1-141">LeaseTimeout (min)</span></span>|<span data-ttu-id="671a1-142">IdleTimeout (min)</span><span class="sxs-lookup"><span data-stu-id="671a1-142">IdleTimeout (min)</span></span>|<span data-ttu-id="671a1-143">MaxItemsInCache</span><span class="sxs-lookup"><span data-stu-id="671a1-143">MaxItemsInCache</span></span>|  
|-|-|-|-|  
|<span data-ttu-id="671a1-144">Výchozí mezipaměť pro tovární nastavení</span><span class="sxs-lookup"><span data-stu-id="671a1-144">Factory Cache Default</span></span>|<span data-ttu-id="671a1-145">TimeSpan. MaxValue</span><span class="sxs-lookup"><span data-stu-id="671a1-145">TimeSpan.MaxValue</span></span>|<span data-ttu-id="671a1-146">2</span><span class="sxs-lookup"><span data-stu-id="671a1-146">2</span></span>|<span data-ttu-id="671a1-147">16</span><span class="sxs-lookup"><span data-stu-id="671a1-147">16</span></span>|  
|<span data-ttu-id="671a1-148">Výchozí nastavení mezipaměti kanálu</span><span class="sxs-lookup"><span data-stu-id="671a1-148">Channel Cache Default</span></span>|<span data-ttu-id="671a1-149">5</span><span class="sxs-lookup"><span data-stu-id="671a1-149">5</span></span>|<span data-ttu-id="671a1-150">2</span><span class="sxs-lookup"><span data-stu-id="671a1-150">2</span></span>|<span data-ttu-id="671a1-151">16</span><span class="sxs-lookup"><span data-stu-id="671a1-151">16</span></span>|  
  
 <span data-ttu-id="671a1-152">Chcete-li přizpůsobit mezipaměť továrny a nastavení mezipaměti kanálu, vytvořte <xref:System.ServiceModel.Activities.SendMessageChannelCache> instanci třídy pomocí parametrizovaného konstruktoru <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> a předejte novou instanci <xref:System.ServiceModel.Activities.ChannelCacheSettings> s vlastními hodnotami do každého z těchto a `channelSettings` `factorySettings` ukazatelů.</span><span class="sxs-lookup"><span data-stu-id="671a1-152">To customize the factory cache and channel cache settings, instantiate the <xref:System.ServiceModel.Activities.SendMessageChannelCache> class using the parameterized constructor <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> and pass a new instance of the <xref:System.ServiceModel.Activities.ChannelCacheSettings> with custom values to each of the `factorySettings` and `channelSettings` parameters.</span></span> <span data-ttu-id="671a1-153">Dále přidejte novou instanci této třídy jako rozšíření hostitele služby pracovního postupu nebo instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="671a1-153">Next, add the new instance of this class as an extension to a workflow service host or a workflow instance.</span></span> <span data-ttu-id="671a1-154">Následující příklad kódu ukazuje, jak provést tyto kroky pro instanci pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="671a1-154">The following code example shows how to perform these steps for a workflow instance.</span></span>  
  
```csharp  
ChannelCacheSettings factorySettings = new ChannelCacheSettings{  
                        MaxItemsInCache = 5,   
                        IdleTimeout = TimeSpan.FromMinutes(5),   
                        LeaseTimeout = TimeSpan.FromMinutes(20)};  
  
ChannelCacheSettings channelSettings = new ChannelCacheSettings{  
                        MaxItemsInCache = 5,   
                        IdleTimeout = TimeSpan.FromMinutes(2),  
                        LeaseTimeout = TimeSpan.FromMinutes(10) };  
  
SendMessageChannelCache customChannelCacheExtension =   
    new SendMessageChannelCache(factorySettings, channelSettings);  
  
clientInstance.Extensions.Add(customChannelCacheExtension);  
```  
  
 <span data-ttu-id="671a1-155">Pokud chcete povolit ukládání do mezipaměti, když má vaše služba pracovního postupu v konfiguraci definované <xref:System.ServiceModel.Activities.SendMessageChannelCache> koncové body, vytvořte instanci třídy <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> pomocí parametrizovaného konstruktoru s `true` `allowUnsafeCaching` parametrem nastaveným na.</span><span class="sxs-lookup"><span data-stu-id="671a1-155">To enable caching when your workflow service has endpoints defined in configuration, instantiate the <xref:System.ServiceModel.Activities.SendMessageChannelCache> class using the parameterized constructor <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> with the `allowUnsafeCaching` parameter set to `true`.</span></span> <span data-ttu-id="671a1-156">Dále přidejte novou instanci této třídy jako rozšíření hostitele služby pracovního postupu nebo instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="671a1-156">Next, add the new instance of this class as an extension to a workflow service host or a workflow instance.</span></span> <span data-ttu-id="671a1-157">Následující příklad kódu ukazuje, jak povolit ukládání do mezipaměti pro instanci pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="671a1-157">The following code example shows how to enable caching for a workflow instance.</span></span>  
  
```csharp  
SendMessageChannelCache customChannelCacheExtension =   
    new SendMessageChannelCache{ AllowUnsafeCaching = true };  
  
clientInstance.Extensions.Add(customChannelCacheExtension);  
```  
  
 <span data-ttu-id="671a1-158">Pokud chcete mezipaměť úplně zakázat pro továrny kanálů a kanály, zakažte mezipaměť objektu pro vytváření kanálů.</span><span class="sxs-lookup"><span data-stu-id="671a1-158">To disable the cache completely for the channel factories and the channels, disable the channel factory cache.</span></span> <span data-ttu-id="671a1-159">Tím se také vypne mezipaměť kanálu, protože kanály vlastní odpovídající továrny kanálů.</span><span class="sxs-lookup"><span data-stu-id="671a1-159">Doing so also turns off the channel cache as the channels are owned by their corresponding channel factories.</span></span> <span data-ttu-id="671a1-160">Chcete- `factorySettings` li zakázat mezipaměť objektu <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> pro vytváření kanálu, předejte parametr do konstruktoru inicializovanému <xref:System.ServiceModel.Activities.ChannelCacheSettings.MaxItemsInCache%2A> do <xref:System.ServiceModel.Activities.ChannelCacheSettings> instance s hodnotou 0.</span><span class="sxs-lookup"><span data-stu-id="671a1-160">To disable the channel factory cache, pass the `factorySettings` parameter to the <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> constructor initialized to a <xref:System.ServiceModel.Activities.ChannelCacheSettings> instance with a <xref:System.ServiceModel.Activities.ChannelCacheSettings.MaxItemsInCache%2A> value of 0.</span></span> <span data-ttu-id="671a1-161">Následující příklad kódu ukazuje toto.</span><span class="sxs-lookup"><span data-stu-id="671a1-161">The following code example shows this.</span></span>  
  
```csharp  
// Disable the factory cache. This results in the channel cache to be turned off as well.  
ChannelCacheSettings factorySettings = new ChannelCacheSettings  
    { MaxItemsInCache = 0 };  
  
ChannelCacheSettings channelSettings = new ChannelCacheSettings();  
  
SendMessageChannelCache customChannelCacheExtension =   
    new SendMessageChannelCache(factorySettings, channelSettings);   
  
clientInstance.Extensions.Add(customChannelCacheExtension);  
```  
  
 <span data-ttu-id="671a1-162">Můžete zvolit, že se má použít pouze mezipaměť objektu pro vytváření kanálu, a zakázat mezipaměť kanálu `channelSettings` předáním parametru <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> do konstruktoru inicializovaného <xref:System.ServiceModel.Activities.ChannelCacheSettings> <xref:System.ServiceModel.Activities.ChannelCacheSettings.MaxItemsInCache%2A> do instance s hodnotou 0.</span><span class="sxs-lookup"><span data-stu-id="671a1-162">You can choose to use only the channel factory cache and disable the channel cache by passing the `channelSettings` parameter to the <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> constructor initialized to a <xref:System.ServiceModel.Activities.ChannelCacheSettings> instance with a <xref:System.ServiceModel.Activities.ChannelCacheSettings.MaxItemsInCache%2A> value of 0.</span></span> <span data-ttu-id="671a1-163">Následující příklad kódu ukazuje toto.</span><span class="sxs-lookup"><span data-stu-id="671a1-163">The following code example shows this.</span></span>  
  
```csharp  
ChannelCacheSettings factorySettings = new ChannelCacheSettings();  
// Disable only the channel cache.  
ChannelCacheSettings channelSettings = new ChannelCacheSettings  
    { MaxItemsInCache = 0};  
  
SendMessageChannelCache customChannelCacheExtension =   
    new SendMessageChannelCache(factorySettings, channelSettings);   
  
clientInstance.Extensions.Add(customChannelCacheExtension);  
```  
  
 <span data-ttu-id="671a1-164">V služby hostované pracovního postupu můžete určit nastavení objekt pro vytváření mezipaměti a kanál mezipaměti v konfiguračním souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="671a1-164">In a hosted workflow service, you can specify the factory cache and channel cache settings in the application configuration file.</span></span> <span data-ttu-id="671a1-165">Chcete-li to provést, přidejte chování služby, který obsahuje nastavení mezipaměti pro objekt pro vytváření a kanál mezipaměti a ke službě Toto chování služby.</span><span class="sxs-lookup"><span data-stu-id="671a1-165">To do so, add a service behavior that contains the cache settings for the factory and channel cache and add this service behavior to your service.</span></span> <span data-ttu-id="671a1-166">Následující příklad ukazuje obsah konfiguračního souboru, který obsahuje `MyChannelCacheBehavior` chování služby s nastavením mezipaměti pro vlastní tovární nastavení a mezipamětí kanálu.</span><span class="sxs-lookup"><span data-stu-id="671a1-166">The following example shows the contents of a configuration file that contains the `MyChannelCacheBehavior` service behavior with the custom factory cache and channel cache settings.</span></span> <span data-ttu-id="671a1-167">Toto chování služby se do služby přidá prostřednictvím `behaviorConfiguration` atributu.</span><span class="sxs-lookup"><span data-stu-id="671a1-167">This service behavior is added to the service through the `behaviorConfiguration` attribute.</span></span>  
  
```xml  
<configuration>    
  <system.serviceModel>  
    <!-- List of other config sections here -->   
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="MyChannelCacheBehavior">  
          <sendMessageChannelCache allowUnsafeCaching ="false" >  
            <!-- Control only the host level settings -->   
            <factorySettings maxItemsInCache = "8" idleTimeout = "00:05:00" leaseTimeout="10:00:00" />  
            <channelSettings maxItemsInCache = "32" idleTimeout = "00:05:00" leaseTimeout="00:06:00" />  
          </sendMessageChannelCache>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    <services>  
      <service name="MyService" behaviorConfiguration="MyChannelCacheBehavior" />  
    </services>  
  </system.serviceModel>  
</configuration>  
```
