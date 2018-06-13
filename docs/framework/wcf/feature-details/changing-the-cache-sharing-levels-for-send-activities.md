---
title: Změna úrovní sdílení mezipaměti pro aktivity odesílání
ms.date: 03/30/2017
ms.assetid: 03926a64-753d-460e-ac06-2a4ff8e1bbf5
ms.openlocfilehash: 359a9189cee34eeb814a2303be3d2da725456e39
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33494531"
---
# <a name="changing-the-cache-sharing-levels-for-send-activities"></a><span data-ttu-id="31810-102">Změna úrovní sdílení mezipaměti pro aktivity odesílání</span><span class="sxs-lookup"><span data-stu-id="31810-102">Changing the Cache Sharing Levels for Send Activities</span></span>
<span data-ttu-id="31810-103"><xref:System.ServiceModel.Activities.SendMessageChannelCache> Rozšíření umožňuje přizpůsobit mezipaměti sdílení úrovní, nastavení objektu pro vytváření mezipaměti kanál, a nastavení kanál mezipaměti pro pracovní postupy, které odesílají zprávy do koncových bodů služby pomocí <xref:System.ServiceModel.Activities.Send> aktivity zasílání zpráv.</span><span class="sxs-lookup"><span data-stu-id="31810-103">The <xref:System.ServiceModel.Activities.SendMessageChannelCache> extension enables you to customize the cache sharing levels, the settings of the channel factory cache, and the settings of the channel cache for workflows that send messages to service endpoints using <xref:System.ServiceModel.Activities.Send> messaging activities.</span></span> <span data-ttu-id="31810-104">Tyto pracovní postupy jsou obvykle pracovní postupy klienta, ale mohou být také služby pracovního postupu, které jsou hostovány v <xref:System.ServiceModel.WorkflowServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="31810-104">These workflows are typically client workflows but could also be workflow services that are hosted in a <xref:System.ServiceModel.WorkflowServiceHost>.</span></span> <span data-ttu-id="31810-105">Obsahuje objekt pro vytváření mezipaměti kanál v mezipaměti <xref:System.ServiceModel.ChannelFactory%601> objekty.</span><span class="sxs-lookup"><span data-stu-id="31810-105">The channel factory cache contains cached <xref:System.ServiceModel.ChannelFactory%601> objects.</span></span> <span data-ttu-id="31810-106">Mezipaměť kanál obsahuje uložené v mezipaměti kanály.</span><span class="sxs-lookup"><span data-stu-id="31810-106">The channel cache contains cached channels.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="31810-107">Pracovní postupy můžete použít <xref:System.ServiceModel.Activities.Send> aktivity k odeslání zprávy nebo parametry zasílání zpráv.</span><span class="sxs-lookup"><span data-stu-id="31810-107">Workflows can use <xref:System.ServiceModel.Activities.Send> messaging activities to send either messages or parameters.</span></span> <span data-ttu-id="31810-108">Modulu runtime pracovního postupu přidává objekty factory kanálu do mezipaměti, která vytvořit kanály typu <xref:System.ServiceModel.Channels.IRequestChannel> při použití <xref:System.ServiceModel.Activities.ReceiveReply> aktivitu <xref:System.ServiceModel.Activities.Send> aktivity a <xref:System.ServiceModel.Channels.IOutputChannel> při použití jenom <xref:System.ServiceModel.Activities.Send> aktivity (žádné <xref:System.ServiceModel.Activities.ReceiveReply>).</span><span class="sxs-lookup"><span data-stu-id="31810-108">The workflow runtime adds channel factories to the cache that create channels of type <xref:System.ServiceModel.Channels.IRequestChannel> when you use a <xref:System.ServiceModel.Activities.ReceiveReply> activity with a <xref:System.ServiceModel.Activities.Send> activity, and an <xref:System.ServiceModel.Channels.IOutputChannel> when just using a <xref:System.ServiceModel.Activities.Send> activity (no <xref:System.ServiceModel.Activities.ReceiveReply>).</span></span>  
  
## <a name="the-cache-sharing-levels"></a><span data-ttu-id="31810-109">Úrovní sdílení mezipaměti</span><span class="sxs-lookup"><span data-stu-id="31810-109">The Cache Sharing Levels</span></span>  
 <span data-ttu-id="31810-110">Ve výchozím nastavení, v pracovním postupu hostované <xref:System.ServiceModel.WorkflowServiceHost> mezipaměti používané <xref:System.ServiceModel.Activities.Send> aktivity zasílání zpráv je sdílen na všechny instance pracovního postupu ve <xref:System.ServiceModel.WorkflowServiceHost> (ukládání do mezipaměti hostitele úrovni).</span><span class="sxs-lookup"><span data-stu-id="31810-110">By default, in a workflow hosted by a <xref:System.ServiceModel.WorkflowServiceHost> the cache used by <xref:System.ServiceModel.Activities.Send> messaging activities is shared across all workflow instances in the <xref:System.ServiceModel.WorkflowServiceHost> (host-level caching).</span></span> <span data-ttu-id="31810-111">Pro klienta pracovní postup, který není hostované <xref:System.ServiceModel.WorkflowServiceHost>, mezipaměť je k dispozici pouze pro instanci pracovního postupu (ukládání do mezipaměti na úrovni instance).</span><span class="sxs-lookup"><span data-stu-id="31810-111">For a client workflow that is not hosted by a <xref:System.ServiceModel.WorkflowServiceHost>, the cache is available only to the workflow instance (instance-level caching).</span></span> <span data-ttu-id="31810-112">Mezipaměť je k dispozici pouze <xref:System.ServiceModel.Activities.Send> aktivity, které nepoužívají koncové body definované v konfiguraci, pokud není unsafe ukládání do mezipaměti povolena.</span><span class="sxs-lookup"><span data-stu-id="31810-112">The cache is only available for <xref:System.ServiceModel.Activities.Send> activities that do not use endpoints defined in configuration unless unsafe caching is enabled.</span></span>  
  
 <span data-ttu-id="31810-113">Toto jsou různé mezipaměti sdílení úrovně, které jsou k dispozici pro <xref:System.ServiceModel.Activities.Send> aktivity v pracovním postupu a jejich doporučená použití:</span><span class="sxs-lookup"><span data-stu-id="31810-113">The following are the different cache sharing levels available for <xref:System.ServiceModel.Activities.Send> activities in a workflow and their recommended use:</span></span>  
  
-   <span data-ttu-id="31810-114">**Hostování úroveň**: na hostiteli, úrovně sdílení, mezipaměť je k dispozici pouze instance pracovních postupů, které jsou hostované na hostiteli služby pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="31810-114">**Host Level**: In the host sharing level, the cache is available only to the workflow instances hosted in the workflow service host.</span></span> <span data-ttu-id="31810-115">Mezipaměti můžete také sdílet mezi hostiteli služby pracovního postupu v mezipaměti úrovni procesu.</span><span class="sxs-lookup"><span data-stu-id="31810-115">A cache can also be shared between workflow service hosts in a process-wide cache.</span></span>  
  
-   <span data-ttu-id="31810-116">**Instance úroveň**: V instanci, úrovně sdílení, mezipaměť je k dispozici pro instanci pracovního postupu konkrétní v průběhu své životnosti, ale mezipaměti není k dispozici pro další instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="31810-116">**Instance Level**: In the instance sharing level, the cache is available to a particular workflow instance throughout its lifetime but the cache is not available to other workflow instances.</span></span>  
  
-   <span data-ttu-id="31810-117">**Žádné mezipaměti**: mezipaměť je ve výchozím nastavení vypnuté Pokud máte pracovní postup, který používá koncové body definované v konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="31810-117">**No Cache**: The cache is turned off by default if you have a workflow that uses endpoints defined in configuration.</span></span> <span data-ttu-id="31810-118">Doporučujeme také pravidelně mezipaměť je vypnuté v takovém případě vzhledem k tomu může být zapnutí nezabezpečená.</span><span class="sxs-lookup"><span data-stu-id="31810-118">It is also recommended to keep the cache turned off in this case because turning it on could be unsecure.</span></span> <span data-ttu-id="31810-119">Například, pokud jiné identity (jiná pověření nebo pomocí zosobnění) je vyžadována pro každý odeslání.</span><span class="sxs-lookup"><span data-stu-id="31810-119">For example, if a different identity (different credentials or using impersonation) is required for each send.</span></span>  
  
## <a name="changing-the-cache-sharing-level-for-a-client-workflow"></a><span data-ttu-id="31810-120">Změna úrovně sdílení pro pracovní postup klienta mezipaměti</span><span class="sxs-lookup"><span data-stu-id="31810-120">Changing the Cache Sharing Level for a Client Workflow</span></span>  
 <span data-ttu-id="31810-121">Nastavení mezipaměti sdílení v pracovním postupu klienta, přidá instanci <xref:System.ServiceModel.Activities.SendMessageChannelCache> třída jako rozšíření na požadovanou sadu instancí pracovních postupů.</span><span class="sxs-lookup"><span data-stu-id="31810-121">To set the cache sharing in a client workflow, add an instance of the <xref:System.ServiceModel.Activities.SendMessageChannelCache> class as an extension to the desired set of workflow instances.</span></span> <span data-ttu-id="31810-122">Výsledkem sdílení mezipaměti napříč všechny instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="31810-122">This results in sharing the cache across all the workflow instances.</span></span> <span data-ttu-id="31810-123">Následující příklady kódu ukazují, jak provést tyto kroky.</span><span class="sxs-lookup"><span data-stu-id="31810-123">The following code examples show how to perform these steps.</span></span>  
  
 <span data-ttu-id="31810-124">Nejprve deklarujte instanci typu <xref:System.ServiceModel.Activities.SendMessageChannelCache>.</span><span class="sxs-lookup"><span data-stu-id="31810-124">First, declare an instance of type <xref:System.ServiceModel.Activities.SendMessageChannelCache>.</span></span>  
  
```  
// Create an instance of SendMessageChannelCache with default cache settings.  
static SendMessageChannelCache sharedChannelCacheExtension =  
    new SendMessageChannelCache();  
```  
  
 <span data-ttu-id="31810-125">Dále přidáte rozšíření mezipaměti každá instance workflowu klienta.</span><span class="sxs-lookup"><span data-stu-id="31810-125">Next, add the cache extension to each client workflow instance.</span></span>  
  
```  
WorkflowApplication clientInstance1 = new WorkflowApplication(new clientWorkflow1());  
WorkflowApplication clientInstance2 = new WorkflowApplication(new clientWorkflow2());  
  
// Share the cache extension object   
  
clientInstance1.Extensions.Add(sharedChannelCacheExtension);  
clientInstance2.Extensions.Add(sharedChannelCacheExtension);  
```  
  
## <a name="changing-the-cache-sharing-level-for-a-hosted-workflow-service"></a><span data-ttu-id="31810-126">Změna mezipaměti úrovně sdílení služby hostovaných pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="31810-126">Changing the Cache Sharing Level for a Hosted Workflow Service</span></span>  
 <span data-ttu-id="31810-127">Nastavení mezipaměti sdílení v hostovaných pracovních postupů služby, přidat instanci <xref:System.ServiceModel.Activities.SendMessageChannelCache> třída jako rozšíření pro všechny hostitele služby pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="31810-127">To set the cache sharing in a hosted workflow service, add an instance of the <xref:System.ServiceModel.Activities.SendMessageChannelCache> class as an extension to all the workflow service hosts.</span></span> <span data-ttu-id="31810-128">Výsledkem sdílení mezipaměti mezi všechny hostitele služby pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="31810-128">This results in sharing the cache across all the workflow service hosts.</span></span> <span data-ttu-id="31810-129">Následující příklady kódu ukazují k provedení těchto kroků.</span><span class="sxs-lookup"><span data-stu-id="31810-129">The following code examples show to perform these steps.</span></span>  
  
 <span data-ttu-id="31810-130">Nejprve deklarujte instanci typu <xref:System.ServiceModel.Activities.SendMessageChannelCache> na úrovni třídy.</span><span class="sxs-lookup"><span data-stu-id="31810-130">First, declare an instance  of type <xref:System.ServiceModel.Activities.SendMessageChannelCache> at the class level.</span></span>  
  
```  
// Create static instance of SendMessageChannelCache with default cache settings.  
static SendMessageChannelCache sharedChannelCacheExtension = new  
    SendMessageChannelCache();  
```  
  
 <span data-ttu-id="31810-131">V dalším kroku přidejte rozšíření statická mezipaměť na každém hostiteli služby pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="31810-131">Next, add the static cache extension to each workflow service host.</span></span>  
  
```  
WorkflowServiceHost host1 = new WorkflowServiceHost(new serviceWorkflow1(), new Uri(baseAddress1));  
WorkflowServiceHost host2 = new WorkflowServiceHost(new serviceWorkflow2(), new Uri(baseAddress2));  
  
// Share the static cache to get an AppDomain level cache.  
host1.WorkflowExtensions.Add(sharedChannelCacheExtension);  
host2.WorkflowExtensions.Add(sharedChannelCacheExtension);  
```  
  
 <span data-ttu-id="31810-132">Chcete-li nastavit mezipaměti sdílení v hostovaných pracovních postupů služby na úrovni instance, přidejte `Func<SendMessageChannelCache>` delegovat jako rozšíření hostitele služby pracovního postupu a přiřaďte tento delegát kód, který vytvoří novou instanci třídy <xref:System.ServiceModel.Activities.SendMessageChannelCache> – třída.</span><span class="sxs-lookup"><span data-stu-id="31810-132">To set the cache sharing in a hosted workflow service to the instance level, add a `Func<SendMessageChannelCache>` delegate as an extension to the workflow service host and assign this delegate to the code that instantiates a new instance of the <xref:System.ServiceModel.Activities.SendMessageChannelCache> class.</span></span> <span data-ttu-id="31810-133">Výsledkem různé mezipaměti pro každou instanci jednotlivých pracovního postupu, místo do jedné mezipaměti sdílí všechny instance pracovního postupu na hostiteli služby pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="31810-133">This results in a different cache for each individual workflow instance, instead of a single cache shared by all workflow instances in the workflow service host.</span></span> <span data-ttu-id="31810-134">Následující příklad kódu ukazuje, jak dosáhnout pomocí výrazu lambda přímo zadat <xref:System.ServiceModel.Activities.SendMessageChannelCache> rozšíření, která delegát odkazuje na.</span><span class="sxs-lookup"><span data-stu-id="31810-134">The following code example shows how to achieve this by using a lambda expression to directly define the <xref:System.ServiceModel.Activities.SendMessageChannelCache> extension that the delegate points to.</span></span>  
  
```  
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
  
## <a name="customizing-cache-settings"></a><span data-ttu-id="31810-135">Přizpůsobení nastavení mezipaměti</span><span class="sxs-lookup"><span data-stu-id="31810-135">Customizing Cache Settings</span></span>  
 <span data-ttu-id="31810-136">Můžete přizpůsobit nastavení do mezipaměti pro mezipaměť objekt pro vytváření kanálu a mezipaměť kanál.</span><span class="sxs-lookup"><span data-stu-id="31810-136">You can customize the cache settings for the channel factory cache and the channel cache.</span></span> <span data-ttu-id="31810-137">Nastavení ukládání do mezipaměti jsou definovány v <xref:System.ServiceModel.Activities.ChannelCacheSettings> třídy.</span><span class="sxs-lookup"><span data-stu-id="31810-137">The cache settings are defined in the <xref:System.ServiceModel.Activities.ChannelCacheSettings> class.</span></span> <span data-ttu-id="31810-138"><xref:System.ServiceModel.Activities.SendMessageChannelCache> Třída definuje výchozí nastavení mezipaměti pro mezipaměť objekt pro vytváření kanálu a mezipaměť kanál v jeho výchozí konstruktor.</span><span class="sxs-lookup"><span data-stu-id="31810-138">The <xref:System.ServiceModel.Activities.SendMessageChannelCache> class defines default cache settings for the channel factory cache and the channel cache in its default constructor.</span></span> <span data-ttu-id="31810-139">Následující tabulka uvádí výchozí hodnoty těchto nastavení mezipaměti pro každý typ mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="31810-139">The following table lists the default values of these cache settings for each type of cache.</span></span>  
  
|<span data-ttu-id="31810-140">Nastavení</span><span class="sxs-lookup"><span data-stu-id="31810-140">Settings</span></span>|<span data-ttu-id="31810-141">LeaseTimeout (min.)</span><span class="sxs-lookup"><span data-stu-id="31810-141">LeaseTimeout (min)</span></span>|<span data-ttu-id="31810-142">IdleTimeout (min.)</span><span class="sxs-lookup"><span data-stu-id="31810-142">IdleTimeout (min)</span></span>|<span data-ttu-id="31810-143">MaxItemsInCache</span><span class="sxs-lookup"><span data-stu-id="31810-143">MaxItemsInCache</span></span>|  
|-|-|-|-|  
|<span data-ttu-id="31810-144">Výchozí objekt pro vytváření mezipaměti</span><span class="sxs-lookup"><span data-stu-id="31810-144">Factory Cache Default</span></span>|<span data-ttu-id="31810-145">TimeSpan.MaxValue, což</span><span class="sxs-lookup"><span data-stu-id="31810-145">TimeSpan.MaxValue</span></span>|<span data-ttu-id="31810-146">2</span><span class="sxs-lookup"><span data-stu-id="31810-146">2</span></span>|<span data-ttu-id="31810-147">16</span><span class="sxs-lookup"><span data-stu-id="31810-147">16</span></span>|  
|<span data-ttu-id="31810-148">Výchozí mezipaměti kanálu</span><span class="sxs-lookup"><span data-stu-id="31810-148">Channel Cache Default</span></span>|<span data-ttu-id="31810-149">5</span><span class="sxs-lookup"><span data-stu-id="31810-149">5</span></span>|<span data-ttu-id="31810-150">2</span><span class="sxs-lookup"><span data-stu-id="31810-150">2</span></span>|<span data-ttu-id="31810-151">16</span><span class="sxs-lookup"><span data-stu-id="31810-151">16</span></span>|  
  
 <span data-ttu-id="31810-152">Pokud chcete přizpůsobit tovární nastavení mezipaměti mezipaměti a kanál, vytváření instancí <xref:System.ServiceModel.Activities.SendMessageChannelCache> pomocí parametrizované konstruktor <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> a předejte novou instanci třídy <xref:System.ServiceModel.Activities.ChannelCacheSettings> s vlastní hodnoty a každý z `factorySettings` a `channelSettings` Parametry.</span><span class="sxs-lookup"><span data-stu-id="31810-152">To customize the factory cache and channel cache settings, instantiate the <xref:System.ServiceModel.Activities.SendMessageChannelCache> class using the parameterized constructor <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> and pass a new instance of the <xref:System.ServiceModel.Activities.ChannelCacheSettings> with custom values to each of the `factorySettings` and `channelSettings` parameters.</span></span> <span data-ttu-id="31810-153">Dál přidejte nové instance této třídy jako rozšíření hostitele služby pracovního postupu nebo instanci pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="31810-153">Next, add the new instance of this class as an extension to a workflow service host or a workflow instance.</span></span> <span data-ttu-id="31810-154">Následující příklad kódu ukazuje, jak provést tyto kroky pro instanci pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="31810-154">The following code example shows how to perform these steps for a workflow instance.</span></span>  
  
```  
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
  
 <span data-ttu-id="31810-155">Pokud chcete povolit ukládání do mezipaměti, když má koncové body definované v konfiguraci služby pracovního postupu, vytváření instancí <xref:System.ServiceModel.Activities.SendMessageChannelCache> pomocí parametrizované konstruktor <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> s `allowUnsafeCaching` parametr nastaven na `true`.</span><span class="sxs-lookup"><span data-stu-id="31810-155">To enable caching when your workflow service has endpoints defined in configuration, instantiate the <xref:System.ServiceModel.Activities.SendMessageChannelCache> class using the parameterized constructor <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> with the `allowUnsafeCaching` parameter set to `true`.</span></span> <span data-ttu-id="31810-156">Dál přidejte nové instance této třídy jako rozšíření hostitele služby pracovního postupu nebo instanci pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="31810-156">Next, add the new instance of this class as an extension to a workflow service host or a workflow instance.</span></span> <span data-ttu-id="31810-157">Následující příklad kódu ukazuje, jak povolit ukládání do mezipaměti pro instanci pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="31810-157">The following code example shows how to enable caching for a workflow instance.</span></span>  
  
```  
SendMessageChannelCache customChannelCacheExtension =   
    new SendMessageChannelCache{ AllowUnsafeCaching = true };  
  
clientInstance.Extensions.Add(customChannelCacheExtension);  
```  
  
 <span data-ttu-id="31810-158">Zakázat mezipaměti úplně objektů Factory kanálů a kanály, zakažte objekt pro vytváření mezipaměti kanálu.</span><span class="sxs-lookup"><span data-stu-id="31810-158">To disable the cache completely for the channel factories and the channels, disable the channel factory cache.</span></span> <span data-ttu-id="31810-159">Díky tomu taky vypne mezipaměti kanálu jako kanály jsou vlastněny objekty Factory jejich odpovídající kanál.</span><span class="sxs-lookup"><span data-stu-id="31810-159">Doing so also turns off the channel cache as the channels are owned by their corresponding channel factories.</span></span> <span data-ttu-id="31810-160">Zakázat objekt pro vytváření mezipaměti kanál, předat `factorySettings` parametru <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> konstruktor inicializována tak, aby <xref:System.ServiceModel.Activities.ChannelCacheSettings> instanci s <xref:System.ServiceModel.Activities.ChannelCacheSettings.MaxItemsInCache%2A> hodnotu 0.</span><span class="sxs-lookup"><span data-stu-id="31810-160">To disable the channel factory cache, pass the `factorySettings` parameter to the <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> constructor initialized to a <xref:System.ServiceModel.Activities.ChannelCacheSettings> instance with a <xref:System.ServiceModel.Activities.ChannelCacheSettings.MaxItemsInCache%2A> value of 0.</span></span> <span data-ttu-id="31810-161">Následující příklad kódu ukazuje to.</span><span class="sxs-lookup"><span data-stu-id="31810-161">The following code example shows this.</span></span>  
  
```  
// Disable the factory cache. This results in the channel cache to be turned off as well.  
ChannelCacheSettings factorySettings = new ChannelCacheSettings  
    { MaxItemsInCache = 0 };  
  
ChannelCacheSettings channelSettings = new ChannelCacheSettings();  
  
SendMessageChannelCache customChannelCacheExtension =   
    new SendMessageChannelCache(factorySettings, channelSettings);   
  
clientInstance.Extensions.Add(customChannelCacheExtension);  
```  
  
 <span data-ttu-id="31810-162">Můžete použít pouze objekt pro vytváření mezipaměti kanál a zakázání mezipaměti kanál předáním `channelSettings` parametru <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> konstruktor inicializována tak, aby <xref:System.ServiceModel.Activities.ChannelCacheSettings> instanci s <xref:System.ServiceModel.Activities.ChannelCacheSettings.MaxItemsInCache%2A> hodnotu 0.</span><span class="sxs-lookup"><span data-stu-id="31810-162">You can choose to use only the channel factory cache and disable the channel cache by passing the `channelSettings` parameter to the <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> constructor initialized to a <xref:System.ServiceModel.Activities.ChannelCacheSettings> instance with a <xref:System.ServiceModel.Activities.ChannelCacheSettings.MaxItemsInCache%2A> value of 0.</span></span> <span data-ttu-id="31810-163">Následující příklad kódu ukazuje to.</span><span class="sxs-lookup"><span data-stu-id="31810-163">The following code example shows this.</span></span>  
  
```  
ChannelCacheSettings factorySettings = new ChannelCacheSettings();  
// Disable only the channel cache.  
ChannelCacheSettings channelSettings = new ChannelCacheSettings  
    { MaxItemsInCache = 0};  
  
SendMessageChannelCache customChannelCacheExtension =   
    new SendMessageChannelCache(factorySettings, channelSettings);   
  
clientInstance.Extensions.Add(customChannelCacheExtension);  
```  
  
 <span data-ttu-id="31810-164">V služby hostované pracovního postupu můžete určit nastavení objekt pro vytváření mezipaměti a kanál mezipaměti v konfiguračním souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="31810-164">In a hosted workflow service, you can specify the factory cache and channel cache settings in the application configuration file.</span></span> <span data-ttu-id="31810-165">Chcete-li to provést, přidejte chování služby, který obsahuje nastavení mezipaměti pro objekt pro vytváření a kanál mezipaměti a ke službě Toto chování služby.</span><span class="sxs-lookup"><span data-stu-id="31810-165">To do so, add a service behavior that contains the cache settings for the factory and channel cache and add this service behavior to your service.</span></span> <span data-ttu-id="31810-166">Následující příklad ukazuje konfigurační soubor, který obsahuje obsah `MyChannelCacheBehavior` chování služby s vlastní objekt pro vytváření mezipaměti a kanál nastavení ukládání do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="31810-166">The following example shows the contents of a configuration file that contains the `MyChannelCacheBehavior` service behavior with the custom factory cache and channel cache settings.</span></span> <span data-ttu-id="31810-167">Toto chování služby se přidá do služby pomocí `behaviorConfiguarion` atribut.</span><span class="sxs-lookup"><span data-stu-id="31810-167">This service behavior is added to the service through the `behaviorConfiguarion` attribute.</span></span>  
  
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
