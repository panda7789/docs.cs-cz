---
title: Změna úrovní sdílení mezipaměti pro aktivity odesílání
ms.date: 03/30/2017
ms.assetid: 03926a64-753d-460e-ac06-2a4ff8e1bbf5
ms.openlocfilehash: 101aab98a7d34ad45ad29efbe252cff0814ca290
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185397"
---
# <a name="changing-the-cache-sharing-levels-for-send-activities"></a><span data-ttu-id="ff496-102">Změna úrovní sdílení mezipaměti pro aktivity odesílání</span><span class="sxs-lookup"><span data-stu-id="ff496-102">Changing the Cache Sharing Levels for Send Activities</span></span>
<span data-ttu-id="ff496-103">Rozšíření <xref:System.ServiceModel.Activities.SendMessageChannelCache> umožňuje přizpůsobit úrovně sdílení mezipaměti, nastavení mezipaměti kanálu a nastavení mezipaměti kanálu pro pracovní postupy, <xref:System.ServiceModel.Activities.Send> které odesílají zprávy koncovým bodům služby pomocí aktivit zasílání zpráv.</span><span class="sxs-lookup"><span data-stu-id="ff496-103">The <xref:System.ServiceModel.Activities.SendMessageChannelCache> extension enables you to customize the cache sharing levels, the settings of the channel factory cache, and the settings of the channel cache for workflows that send messages to service endpoints using <xref:System.ServiceModel.Activities.Send> messaging activities.</span></span> <span data-ttu-id="ff496-104">Tyto pracovní postupy jsou obvykle pracovní postupy klienta, ale mohou být také služby pracovního postupu, které jsou hostovány v <xref:System.ServiceModel.WorkflowServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="ff496-104">These workflows are typically client workflows but could also be workflow services that are hosted in a <xref:System.ServiceModel.WorkflowServiceHost>.</span></span> <span data-ttu-id="ff496-105">Mezipaměť kanálu factory <xref:System.ServiceModel.ChannelFactory%601> obsahuje objekty uložené v mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="ff496-105">The channel factory cache contains cached <xref:System.ServiceModel.ChannelFactory%601> objects.</span></span> <span data-ttu-id="ff496-106">Mezipaměť kanálu obsahuje kanály uložené v mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="ff496-106">The channel cache contains cached channels.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ff496-107">Pracovní postupy <xref:System.ServiceModel.Activities.Send> mohou používat aktivity zasílání zpráv k odesílání zpráv nebo parametrů.</span><span class="sxs-lookup"><span data-stu-id="ff496-107">Workflows can use <xref:System.ServiceModel.Activities.Send> messaging activities to send either messages or parameters.</span></span> <span data-ttu-id="ff496-108">Za běhu pracovního postupu přidá továrny kanálu <xref:System.ServiceModel.Channels.IRequestChannel> do mezipaměti, které vytvářejí kanály typu <xref:System.ServiceModel.Activities.Send> při <xref:System.ServiceModel.Activities.ReceiveReply>použití <xref:System.ServiceModel.Activities.ReceiveReply> aktivity s aktivitou <xref:System.ServiceModel.Activities.Send> a <xref:System.ServiceModel.Channels.IOutputChannel> při použití pouze aktivity (ne).</span><span class="sxs-lookup"><span data-stu-id="ff496-108">The workflow runtime adds channel factories to the cache that create channels of type <xref:System.ServiceModel.Channels.IRequestChannel> when you use a <xref:System.ServiceModel.Activities.ReceiveReply> activity with a <xref:System.ServiceModel.Activities.Send> activity, and an <xref:System.ServiceModel.Channels.IOutputChannel> when just using a <xref:System.ServiceModel.Activities.Send> activity (no <xref:System.ServiceModel.Activities.ReceiveReply>).</span></span>  
  
## <a name="the-cache-sharing-levels"></a><span data-ttu-id="ff496-109">Úrovně sdílení mezipaměti</span><span class="sxs-lookup"><span data-stu-id="ff496-109">The Cache Sharing Levels</span></span>  
 <span data-ttu-id="ff496-110">Ve výchozím nastavení je v <xref:System.ServiceModel.WorkflowServiceHost> pracovním postupu <xref:System.ServiceModel.Activities.Send> hostovaném mezipamětí používanou aktivitami zasílání zpráv sdílena ve všech instancích pracovního postupu v oblasti <xref:System.ServiceModel.WorkflowServiceHost> (ukládání do mezipaměti na úrovni hostitele).</span><span class="sxs-lookup"><span data-stu-id="ff496-110">By default, in a workflow hosted by a <xref:System.ServiceModel.WorkflowServiceHost> the cache used by <xref:System.ServiceModel.Activities.Send> messaging activities is shared across all workflow instances in the <xref:System.ServiceModel.WorkflowServiceHost> (host-level caching).</span></span> <span data-ttu-id="ff496-111">Pro klienta pracovní postup, který není hostované <xref:System.ServiceModel.WorkflowServiceHost>, mezipaměť je k dispozici pouze pro instanci pracovního postupu (ukládání do mezipaměti na úrovni instance).</span><span class="sxs-lookup"><span data-stu-id="ff496-111">For a client workflow that is not hosted by a <xref:System.ServiceModel.WorkflowServiceHost>, the cache is available only to the workflow instance (instance-level caching).</span></span> <span data-ttu-id="ff496-112">Mezipaměť je k <xref:System.ServiceModel.Activities.Send> dispozici pouze pro aktivity, které nepoužívají koncové body definované v konfiguraci, pokud není povoleno nebezpečné ukládání do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="ff496-112">The cache is only available for <xref:System.ServiceModel.Activities.Send> activities that do not use endpoints defined in configuration unless unsafe caching is enabled.</span></span>  
  
 <span data-ttu-id="ff496-113">Níže jsou uvedeny různé úrovně <xref:System.ServiceModel.Activities.Send> sdílení mezipaměti, které jsou k dispozici pro aktivity v pracovním postupu, a jejich doporučené použití:</span><span class="sxs-lookup"><span data-stu-id="ff496-113">The following are the different cache sharing levels available for <xref:System.ServiceModel.Activities.Send> activities in a workflow and their recommended use:</span></span>  
  
- <span data-ttu-id="ff496-114">**Úroveň hostitele**: Na úrovni sdílení hostitele je mezipaměť k dispozici pouze pro instance pracovního postupu hostované v hostiteli služby pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="ff496-114">**Host Level**: In the host sharing level, the cache is available only to the workflow instances hosted in the workflow service host.</span></span> <span data-ttu-id="ff496-115">Mezipaměť lze také sdílet mezi hostiteli služby pracovního postupu v mezipaměti pro celý proces.</span><span class="sxs-lookup"><span data-stu-id="ff496-115">A cache can also be shared between workflow service hosts in a process-wide cache.</span></span>  
  
- <span data-ttu-id="ff496-116">**Úroveň instance**: V úrovni sdílení instance je mezipaměť k dispozici pro konkrétní instanci pracovního postupu po celou dobu její životnosti, ale mezipaměť není k dispozici pro jiné instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="ff496-116">**Instance Level**: In the instance sharing level, the cache is available to a particular workflow instance throughout its lifetime but the cache is not available to other workflow instances.</span></span>  
  
- <span data-ttu-id="ff496-117">**Žádná mezipaměť**: Mezipaměť je ve výchozím nastavení vypnutá, pokud máte pracovní postup, který používá koncové body definované v konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="ff496-117">**No Cache**: The cache is turned off by default if you have a workflow that uses endpoints defined in configuration.</span></span> <span data-ttu-id="ff496-118">V tomto případě je také doporučeno ponechat mezipaměť vypnutou, protože její zapnutí může být nezabezpečené.</span><span class="sxs-lookup"><span data-stu-id="ff496-118">It is also recommended to keep the cache turned off in this case because turning it on could be unsecure.</span></span> <span data-ttu-id="ff496-119">Například pokud je pro každé odeslání vyžadována jiná identita (jiná pověření nebo použití zosobnění).</span><span class="sxs-lookup"><span data-stu-id="ff496-119">For example, if a different identity (different credentials or using impersonation) is required for each send.</span></span>  
  
## <a name="changing-the-cache-sharing-level-for-a-client-workflow"></a><span data-ttu-id="ff496-120">Změna úrovně sdílení mezipaměti pro pracovní postup klienta</span><span class="sxs-lookup"><span data-stu-id="ff496-120">Changing the Cache Sharing Level for a Client Workflow</span></span>  
 <span data-ttu-id="ff496-121">Chcete-li nastavit sdílení mezipaměti v pracovním <xref:System.ServiceModel.Activities.SendMessageChannelCache> postupu klienta, přidejte instanci třídy jako rozšíření požadované sady instancí pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="ff496-121">To set the cache sharing in a client workflow, add an instance of the <xref:System.ServiceModel.Activities.SendMessageChannelCache> class as an extension to the desired set of workflow instances.</span></span> <span data-ttu-id="ff496-122">Výsledkem je sdílení mezipaměti ve všech instancích pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="ff496-122">This results in sharing the cache across all the workflow instances.</span></span> <span data-ttu-id="ff496-123">Následující příklady kódu ukazují, jak provést tyto kroky.</span><span class="sxs-lookup"><span data-stu-id="ff496-123">The following code examples show how to perform these steps.</span></span>  
  
 <span data-ttu-id="ff496-124">Nejprve deklarujte <xref:System.ServiceModel.Activities.SendMessageChannelCache>instanci typu .</span><span class="sxs-lookup"><span data-stu-id="ff496-124">First, declare an instance of type <xref:System.ServiceModel.Activities.SendMessageChannelCache>.</span></span>  
  
```csharp  
// Create an instance of SendMessageChannelCache with default cache settings.  
static SendMessageChannelCache sharedChannelCacheExtension =  
    new SendMessageChannelCache();  
```  
  
 <span data-ttu-id="ff496-125">Dále přidejte rozšíření mezipaměti do každé instance pracovního postupu klienta.</span><span class="sxs-lookup"><span data-stu-id="ff496-125">Next, add the cache extension to each client workflow instance.</span></span>  
  
```csharp
WorkflowApplication clientInstance1 = new WorkflowApplication(new clientWorkflow1());  
WorkflowApplication clientInstance2 = new WorkflowApplication(new clientWorkflow2());  
  
// Share the cache extension object
  
clientInstance1.Extensions.Add(sharedChannelCacheExtension);  
clientInstance2.Extensions.Add(sharedChannelCacheExtension);  
```  
  
## <a name="changing-the-cache-sharing-level-for-a-hosted-workflow-service"></a><span data-ttu-id="ff496-126">Změna úrovně sdílení mezipaměti pro hostovkou služby pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="ff496-126">Changing the Cache Sharing Level for a Hosted Workflow Service</span></span>  
 <span data-ttu-id="ff496-127">Chcete-li nastavit sdílení mezipaměti v hostované službě <xref:System.ServiceModel.Activities.SendMessageChannelCache> pracovního postupu, přidejte instanci třídy jako rozšíření ke všem hostitelům služby pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="ff496-127">To set the cache sharing in a hosted workflow service, add an instance of the <xref:System.ServiceModel.Activities.SendMessageChannelCache> class as an extension to all the workflow service hosts.</span></span> <span data-ttu-id="ff496-128">Výsledkem je sdílení mezipaměti mezi všemi hostiteli služby pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="ff496-128">This results in sharing the cache across all the workflow service hosts.</span></span> <span data-ttu-id="ff496-129">Následující příklady kódu ukazují provést tyto kroky.</span><span class="sxs-lookup"><span data-stu-id="ff496-129">The following code examples show to perform these steps.</span></span>  
  
 <span data-ttu-id="ff496-130">Nejprve deklarujte <xref:System.ServiceModel.Activities.SendMessageChannelCache> instanci typu na úrovni třídy.</span><span class="sxs-lookup"><span data-stu-id="ff496-130">First, declare an instance  of type <xref:System.ServiceModel.Activities.SendMessageChannelCache> at the class level.</span></span>  
  
```csharp  
// Create static instance of SendMessageChannelCache with default cache settings.  
static SendMessageChannelCache sharedChannelCacheExtension = new  
    SendMessageChannelCache();  
```  
  
 <span data-ttu-id="ff496-131">Dále přidejte rozšíření statické mezipaměti ke každému hostiteli služby pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="ff496-131">Next, add the static cache extension to each workflow service host.</span></span>  
  
```csharp  
WorkflowServiceHost host1 = new WorkflowServiceHost(new serviceWorkflow1(), new Uri(baseAddress1));  
WorkflowServiceHost host2 = new WorkflowServiceHost(new serviceWorkflow2(), new Uri(baseAddress2));  
  
// Share the static cache to get an AppDomain level cache.  
host1.WorkflowExtensions.Add(sharedChannelCacheExtension);  
host2.WorkflowExtensions.Add(sharedChannelCacheExtension);  
```  
  
 <span data-ttu-id="ff496-132">Chcete-li nastavit sdílení mezipaměti ve službě hostovaného `Func<SendMessageChannelCache>` pracovního postupu na úroveň instance, přidejte delegáta jako rozšíření k hostiteli služby pracovního postupu a přiřaďte tohoto delegáta ke kódu, který instancije novou instanci <xref:System.ServiceModel.Activities.SendMessageChannelCache> třídy.</span><span class="sxs-lookup"><span data-stu-id="ff496-132">To set the cache sharing in a hosted workflow service to the instance level, add a `Func<SendMessageChannelCache>` delegate as an extension to the workflow service host and assign this delegate to the code that instantiates a new instance of the <xref:System.ServiceModel.Activities.SendMessageChannelCache> class.</span></span> <span data-ttu-id="ff496-133">Výsledkem je jiná mezipaměť pro každou jednotlivé instance pracovního postupu namísto jedné mezipaměti sdílené všemi instancemi pracovního postupu v hostiteli služby pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="ff496-133">This results in a different cache for each individual workflow instance, instead of a single cache shared by all workflow instances in the workflow service host.</span></span> <span data-ttu-id="ff496-134">Následující příklad kódu ukazuje, jak toho dosáhnout pomocí výrazu <xref:System.ServiceModel.Activities.SendMessageChannelCache> lambda k přímému definování rozšíření, na které delegát odkazuje.</span><span class="sxs-lookup"><span data-stu-id="ff496-134">The following code example shows how to achieve this by using a lambda expression to directly define the <xref:System.ServiceModel.Activities.SendMessageChannelCache> extension that the delegate points to.</span></span>  
  
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
  
## <a name="customizing-cache-settings"></a><span data-ttu-id="ff496-135">Přizpůsobení nastavení mezipaměti</span><span class="sxs-lookup"><span data-stu-id="ff496-135">Customizing Cache Settings</span></span>  
 <span data-ttu-id="ff496-136">Nastavení mezipaměti můžete přizpůsobit pro mezipaměť kanálu a mezipaměť kanálu.</span><span class="sxs-lookup"><span data-stu-id="ff496-136">You can customize the cache settings for the channel factory cache and the channel cache.</span></span> <span data-ttu-id="ff496-137">Nastavení mezipaměti jsou <xref:System.ServiceModel.Activities.ChannelCacheSettings> definovány ve třídě.</span><span class="sxs-lookup"><span data-stu-id="ff496-137">The cache settings are defined in the <xref:System.ServiceModel.Activities.ChannelCacheSettings> class.</span></span> <span data-ttu-id="ff496-138">Třída <xref:System.ServiceModel.Activities.SendMessageChannelCache> definuje výchozí nastavení mezipaměti pro vyrovnávací paměť kanálu a mezipaměť kanálu v jeho konstruktoru bez parametrů.</span><span class="sxs-lookup"><span data-stu-id="ff496-138">The <xref:System.ServiceModel.Activities.SendMessageChannelCache> class defines default cache settings for the channel factory cache and the channel cache in its parameterless constructor.</span></span> <span data-ttu-id="ff496-139">V následující tabulce jsou uvedeny výchozí hodnoty těchto nastavení mezipaměti pro každý typ mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="ff496-139">The following table lists the default values of these cache settings for each type of cache.</span></span>  
  
|<span data-ttu-id="ff496-140">Nastavení</span><span class="sxs-lookup"><span data-stu-id="ff496-140">Settings</span></span>|<span data-ttu-id="ff496-141">LeaseTimeout (min)</span><span class="sxs-lookup"><span data-stu-id="ff496-141">LeaseTimeout (min)</span></span>|<span data-ttu-id="ff496-142">IdleTimeout (min)</span><span class="sxs-lookup"><span data-stu-id="ff496-142">IdleTimeout (min)</span></span>|<span data-ttu-id="ff496-143">MaxItemsv mezipaměti</span><span class="sxs-lookup"><span data-stu-id="ff496-143">MaxItemsInCache</span></span>|  
|-|-|-|-|  
|<span data-ttu-id="ff496-144">Výchozí vyrovnávací paměť z výroby</span><span class="sxs-lookup"><span data-stu-id="ff496-144">Factory Cache Default</span></span>|<span data-ttu-id="ff496-145">Timespan.maxvalue</span><span class="sxs-lookup"><span data-stu-id="ff496-145">TimeSpan.MaxValue</span></span>|<span data-ttu-id="ff496-146">2</span><span class="sxs-lookup"><span data-stu-id="ff496-146">2</span></span>|<span data-ttu-id="ff496-147">16</span><span class="sxs-lookup"><span data-stu-id="ff496-147">16</span></span>|  
|<span data-ttu-id="ff496-148">Výchozí mezipaměť kanálu</span><span class="sxs-lookup"><span data-stu-id="ff496-148">Channel Cache Default</span></span>|<span data-ttu-id="ff496-149">5</span><span class="sxs-lookup"><span data-stu-id="ff496-149">5</span></span>|<span data-ttu-id="ff496-150">2</span><span class="sxs-lookup"><span data-stu-id="ff496-150">2</span></span>|<span data-ttu-id="ff496-151">16</span><span class="sxs-lookup"><span data-stu-id="ff496-151">16</span></span>|  
  
 <span data-ttu-id="ff496-152">Chcete-li přizpůsobit nastavení mezipaměti výroby a <xref:System.ServiceModel.Activities.SendMessageChannelCache> mezipaměti kanálu, vytvořte instanci třídy pomocí parametrizovaného <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> konstruktoru a předejte novou instanci <xref:System.ServiceModel.Activities.ChannelCacheSettings> s vlastními hodnotami každému z parametrů `factorySettings` a. `channelSettings`</span><span class="sxs-lookup"><span data-stu-id="ff496-152">To customize the factory cache and channel cache settings, instantiate the <xref:System.ServiceModel.Activities.SendMessageChannelCache> class using the parameterized constructor <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> and pass a new instance of the <xref:System.ServiceModel.Activities.ChannelCacheSettings> with custom values to each of the `factorySettings` and `channelSettings` parameters.</span></span> <span data-ttu-id="ff496-153">Dále přidejte novou instanci této třídy jako rozšíření k hostiteli služby pracovního postupu nebo instanci pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="ff496-153">Next, add the new instance of this class as an extension to a workflow service host or a workflow instance.</span></span> <span data-ttu-id="ff496-154">Následující příklad kódu ukazuje, jak provést tyto kroky pro instanci pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="ff496-154">The following code example shows how to perform these steps for a workflow instance.</span></span>  
  
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
  
 <span data-ttu-id="ff496-155">Chcete-li povolit ukládání do mezipaměti, pokud má služba <xref:System.ServiceModel.Activities.SendMessageChannelCache> pracovního postupu koncové <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> body `allowUnsafeCaching` definované v `true`konfiguraci, vytvořte instanci třídy pomocí parametrizovaného konstruktoru s parametrem nastaveným na .</span><span class="sxs-lookup"><span data-stu-id="ff496-155">To enable caching when your workflow service has endpoints defined in configuration, instantiate the <xref:System.ServiceModel.Activities.SendMessageChannelCache> class using the parameterized constructor <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> with the `allowUnsafeCaching` parameter set to `true`.</span></span> <span data-ttu-id="ff496-156">Dále přidejte novou instanci této třídy jako rozšíření k hostiteli služby pracovního postupu nebo instanci pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="ff496-156">Next, add the new instance of this class as an extension to a workflow service host or a workflow instance.</span></span> <span data-ttu-id="ff496-157">Následující příklad kódu ukazuje, jak povolit ukládání do mezipaměti pro instanci pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="ff496-157">The following code example shows how to enable caching for a workflow instance.</span></span>  
  
```csharp  
SendMessageChannelCache customChannelCacheExtension =
    new SendMessageChannelCache{ AllowUnsafeCaching = true };  
  
clientInstance.Extensions.Add(customChannelCacheExtension);  
```  
  
 <span data-ttu-id="ff496-158">Chcete-li mezipaměť zcela zakázat pro továrny kanálu a kanály, zakažte mezipaměť kanálu.</span><span class="sxs-lookup"><span data-stu-id="ff496-158">To disable the cache completely for the channel factories and the channels, disable the channel factory cache.</span></span> <span data-ttu-id="ff496-159">Tím také vypnete mezipaměť kanálu, protože kanály jsou vlastněny jejich odpovídajícími továrnami kanálu.</span><span class="sxs-lookup"><span data-stu-id="ff496-159">Doing so also turns off the channel cache as the channels are owned by their corresponding channel factories.</span></span> <span data-ttu-id="ff496-160">Chcete-li zakázat mezipaměť `factorySettings` kanálu <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> výroby, předajte parametr konstruktoru inicializovanému <xref:System.ServiceModel.Activities.ChannelCacheSettings> instanci s hodnotou <xref:System.ServiceModel.Activities.ChannelCacheSettings.MaxItemsInCache%2A> 0.</span><span class="sxs-lookup"><span data-stu-id="ff496-160">To disable the channel factory cache, pass the `factorySettings` parameter to the <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> constructor initialized to a <xref:System.ServiceModel.Activities.ChannelCacheSettings> instance with a <xref:System.ServiceModel.Activities.ChannelCacheSettings.MaxItemsInCache%2A> value of 0.</span></span> <span data-ttu-id="ff496-161">Následující příklad kódu ukazuje toto.</span><span class="sxs-lookup"><span data-stu-id="ff496-161">The following code example shows this.</span></span>  
  
```csharp  
// Disable the factory cache. This results in the channel cache to be turned off as well.  
ChannelCacheSettings factorySettings = new ChannelCacheSettings  
    { MaxItemsInCache = 0 };  
  
ChannelCacheSettings channelSettings = new ChannelCacheSettings();  
  
SendMessageChannelCache customChannelCacheExtension =
    new SendMessageChannelCache(factorySettings, channelSettings);
  
clientInstance.Extensions.Add(customChannelCacheExtension);  
```  
  
 <span data-ttu-id="ff496-162">Můžete použít pouze vyrovnávací paměť kanálu z výroby a `channelSettings` zakázat <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> mezipaměť kanálu předáním parametru konstruktoru inicializovanému <xref:System.ServiceModel.Activities.ChannelCacheSettings> instanci s hodnotou <xref:System.ServiceModel.Activities.ChannelCacheSettings.MaxItemsInCache%2A> 0.</span><span class="sxs-lookup"><span data-stu-id="ff496-162">You can choose to use only the channel factory cache and disable the channel cache by passing the `channelSettings` parameter to the <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> constructor initialized to a <xref:System.ServiceModel.Activities.ChannelCacheSettings> instance with a <xref:System.ServiceModel.Activities.ChannelCacheSettings.MaxItemsInCache%2A> value of 0.</span></span> <span data-ttu-id="ff496-163">Následující příklad kódu ukazuje toto.</span><span class="sxs-lookup"><span data-stu-id="ff496-163">The following code example shows this.</span></span>  
  
```csharp  
ChannelCacheSettings factorySettings = new ChannelCacheSettings();  
// Disable only the channel cache.  
ChannelCacheSettings channelSettings = new ChannelCacheSettings  
    { MaxItemsInCache = 0};  
  
SendMessageChannelCache customChannelCacheExtension =
    new SendMessageChannelCache(factorySettings, channelSettings);
  
clientInstance.Extensions.Add(customChannelCacheExtension);  
```  
  
 <span data-ttu-id="ff496-164">V služby hostované pracovního postupu můžete určit nastavení objekt pro vytváření mezipaměti a kanál mezipaměti v konfiguračním souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="ff496-164">In a hosted workflow service, you can specify the factory cache and channel cache settings in the application configuration file.</span></span> <span data-ttu-id="ff496-165">Chcete-li to provést, přidejte chování služby, který obsahuje nastavení mezipaměti pro objekt pro vytváření a kanál mezipaměti a ke službě Toto chování služby.</span><span class="sxs-lookup"><span data-stu-id="ff496-165">To do so, add a service behavior that contains the cache settings for the factory and channel cache and add this service behavior to your service.</span></span> <span data-ttu-id="ff496-166">Následující příklad ukazuje obsah konfiguračního `MyChannelCacheBehavior` souboru, který obsahuje chování služby s vlastním nastavením mezipaměti výroby a mezipaměti kanálů.</span><span class="sxs-lookup"><span data-stu-id="ff496-166">The following example shows the contents of a configuration file that contains the `MyChannelCacheBehavior` service behavior with the custom factory cache and channel cache settings.</span></span> <span data-ttu-id="ff496-167">Toto chování služby je `behaviorConfiguration` přidán do služby prostřednictvím atributu.</span><span class="sxs-lookup"><span data-stu-id="ff496-167">This service behavior is added to the service through the `behaviorConfiguration` attribute.</span></span>  
  
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
