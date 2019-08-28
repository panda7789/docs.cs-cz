---
title: Postup kanálu a mezipaměť
ms.date: 03/30/2017
ms.assetid: 954f030e-091c-4c0e-a7a2-10f9a6b1f529
ms.openlocfilehash: 98b77071204e2c2f98609e6c5bb1ca84a896dd58
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2019
ms.locfileid: "70040204"
---
# <a name="channel-factory-and-caching"></a><span data-ttu-id="93772-102">Postup kanálu a mezipaměť</span><span class="sxs-lookup"><span data-stu-id="93772-102">Channel Factory and Caching</span></span>

<span data-ttu-id="93772-103">Klientské aplikace WCF používají <xref:System.ServiceModel.ChannelFactory%601> třídu k vytvoření komunikačního kanálu se službou WCF.</span><span class="sxs-lookup"><span data-stu-id="93772-103">WCF client applications use the <xref:System.ServiceModel.ChannelFactory%601> class to create a communication channel with a WCF service.</span></span>  <span data-ttu-id="93772-104">Vytváření <xref:System.ServiceModel.ChannelFactory%601> instancí má za následek určitou režii, protože zahrnuje následující operace:</span><span class="sxs-lookup"><span data-stu-id="93772-104">Creating <xref:System.ServiceModel.ChannelFactory%601> instances incurs some overhead because it involves the following operations:</span></span>

- <span data-ttu-id="93772-105">Sestavování <xref:System.ServiceModel.Description.ContractDescription> stromu</span><span class="sxs-lookup"><span data-stu-id="93772-105">Constructing the <xref:System.ServiceModel.Description.ContractDescription> tree</span></span>

- <span data-ttu-id="93772-106">Reflektování všech požadovaných typů CLR</span><span class="sxs-lookup"><span data-stu-id="93772-106">Reflecting all of the required CLR types</span></span>

- <span data-ttu-id="93772-107">Sestavování zásobníku kanálů</span><span class="sxs-lookup"><span data-stu-id="93772-107">Constructing the channel stack</span></span>

- <span data-ttu-id="93772-108">Odstraňování prostředků</span><span class="sxs-lookup"><span data-stu-id="93772-108">Disposing of resources</span></span>

<span data-ttu-id="93772-109">Pro lepší minimalizaci této režie může WCF při použití proxy serveru WCF ukládat do mezipaměti objekty kanálu.</span><span class="sxs-lookup"><span data-stu-id="93772-109">To help minimize this overhead, WCF can cache channel factories when you are using a WCF client proxy.</span></span>

> [!TIP]
> <span data-ttu-id="93772-110">Při přímém použití <xref:System.ServiceModel.ChannelFactory%601> třídy máte přímou kontrolu nad vytvořením objektu pro vytváření kanálů.</span><span class="sxs-lookup"><span data-stu-id="93772-110">You have direct control over channel factory creation when you use the <xref:System.ServiceModel.ChannelFactory%601> class directly.</span></span>

<span data-ttu-id="93772-111">Proxy klientské proxy služby WCF generované pomocí [nástroje ServiceModel Metadata Tool (Svcutil. exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) jsou odvozeny z <xref:System.ServiceModel.ClientBase%601>.</span><span class="sxs-lookup"><span data-stu-id="93772-111">WCF client proxies generated with [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) are derived from <xref:System.ServiceModel.ClientBase%601>.</span></span> <span data-ttu-id="93772-112"><xref:System.ServiceModel.ClientBase%601>definuje statickou <xref:System.ServiceModel.ClientBase%601.CacheSetting%2A> vlastnost, která definuje chování při ukládání do mezipaměti při vytváření kanálu.</span><span class="sxs-lookup"><span data-stu-id="93772-112"><xref:System.ServiceModel.ClientBase%601> defines a static <xref:System.ServiceModel.ClientBase%601.CacheSetting%2A> property that defines channel factory caching behavior.</span></span> <span data-ttu-id="93772-113">Nastavení mezipaměti je provedeno pro konkrétní typ.</span><span class="sxs-lookup"><span data-stu-id="93772-113">Cache settings are made for a specific type.</span></span> <span data-ttu-id="93772-114">Například nastavení `ClientBase<ITest>.CacheSettings` na jednu z hodnot definovaných níže bude mít vliv pouze na typ proxy/ClientBase typu `ITest`.</span><span class="sxs-lookup"><span data-stu-id="93772-114">For example, setting  `ClientBase<ITest>.CacheSettings` to one of the values defined below will affect only those proxy/ClientBase of type `ITest`.</span></span> <span data-ttu-id="93772-115">Nastavení mezipaměti pro určitý <xref:System.ServiceModel.ClientBase%601> objekt je po vytvoření první instance proxy/ClientBase neměnné.</span><span class="sxs-lookup"><span data-stu-id="93772-115">The cache setting for a particular <xref:System.ServiceModel.ClientBase%601> is immutable as soon as the first proxy/ClientBase instance is created.</span></span>

## <a name="specifying-caching-behavior"></a><span data-ttu-id="93772-116">Určení chování při ukládání do mezipaměti</span><span class="sxs-lookup"><span data-stu-id="93772-116">Specifying Caching Behavior</span></span>

<span data-ttu-id="93772-117">Chování ukládání do mezipaměti je určeno nastavením <xref:System.ServiceModel.ClientBase%601.CacheSetting> vlastnosti na jednu z následujících hodnot.</span><span class="sxs-lookup"><span data-stu-id="93772-117">Caching behavior is specified by setting the <xref:System.ServiceModel.ClientBase%601.CacheSetting> property to one of the following values.</span></span>

|<span data-ttu-id="93772-118">Hodnota nastavení mezipaměti</span><span class="sxs-lookup"><span data-stu-id="93772-118">Cache Setting Value</span></span>|<span data-ttu-id="93772-119">Popis</span><span class="sxs-lookup"><span data-stu-id="93772-119">Description</span></span>|
|-------------------------|-----------------|
|<xref:System.ServiceModel.CacheSetting.AlwaysOn>|<span data-ttu-id="93772-120">Všechny instance <xref:System.ServiceModel.ClientBase%601> v rámci aplikační domény se můžou účastnit ukládání do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="93772-120">All instances of <xref:System.ServiceModel.ClientBase%601> within the app-domain can participate in caching.</span></span> <span data-ttu-id="93772-121">Vývojář zjistil, že neexistují žádné nepříznivé důsledky zabezpečení pro ukládání do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="93772-121">The developer has determined that there are no adverse security implications to caching.</span></span> <span data-ttu-id="93772-122">Ukládání do mezipaměti nebude vypnuto ani v případě, že jsou k dispozici vlastnosti <xref:System.ServiceModel.ClientBase%601> "citlivá na zabezpečení".</span><span class="sxs-lookup"><span data-stu-id="93772-122">Caching will not be turned off even if "security-sensitive" properties on <xref:System.ServiceModel.ClientBase%601> are accessed.</span></span> <span data-ttu-id="93772-123">Vlastnosti <xref:System.ServiceModel.ClientBase%601> " <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> jsoucitlivé<xref:System.ServiceModel.ClientBase%601.ChannelFactory%2A>na zabezpečení" jsou a.<xref:System.ServiceModel.ClientBase%601.Endpoint%2A></span><span class="sxs-lookup"><span data-stu-id="93772-123">The "security-sensitive" properties of <xref:System.ServiceModel.ClientBase%601> are <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A>, <xref:System.ServiceModel.ClientBase%601.Endpoint%2A> and <xref:System.ServiceModel.ClientBase%601.ChannelFactory%2A>.</span></span>|
|<xref:System.ServiceModel.CacheSetting.Default>|<span data-ttu-id="93772-124">Ukládání do mezipaměti <xref:System.ServiceModel.ClientBase%601> v rámci aplikační domény se účastní pouze instance vytvořené z koncových bodů definovaných v konfiguračních souborech.</span><span class="sxs-lookup"><span data-stu-id="93772-124">Only instances of <xref:System.ServiceModel.ClientBase%601> created from endpoints defined in configuration files participate in caching within the app-domain.</span></span> <span data-ttu-id="93772-125">Jakékoli instance <xref:System.ServiceModel.ClientBase%601> vytvořené programově v rámci této aplikace – doména se nebudou podílet na ukládání do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="93772-125">Any instances of <xref:System.ServiceModel.ClientBase%601> created programmatically within that app-domain will not participate in caching.</span></span> <span data-ttu-id="93772-126">Mezipaměť se taky zakáže pro instanci, <xref:System.ServiceModel.ClientBase%601> která má přístup ke všem vlastnostem "citlivým na zabezpečení".</span><span class="sxs-lookup"><span data-stu-id="93772-126">Also, caching will be disabled for an instance of <xref:System.ServiceModel.ClientBase%601> once any of its "security-sensitive" properties is accessed.</span></span>|
|<xref:System.ServiceModel.CacheSetting.AlwaysOff>|<span data-ttu-id="93772-127">Pro všechny instance <xref:System.ServiceModel.ClientBase%601> určitého typu v rámci příslušné domény aplikace je ukládání do mezipaměti vypnuté.</span><span class="sxs-lookup"><span data-stu-id="93772-127">Caching is turned off for all instances of <xref:System.ServiceModel.ClientBase%601> of a particular type within the app-domain in question.</span></span>|

<span data-ttu-id="93772-128">Následující fragmenty kódu ilustrují, jak použít <xref:System.ServiceModel.ClientBase%601.CacheSetting%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="93772-128">The following code snippets illustrate how to use the <xref:System.ServiceModel.ClientBase%601.CacheSetting%2A> property.</span></span>

```csharp
class Program
{
   static void Main(string[] args)
   {
      ClientBase<ITest>.CacheSettings = CacheSettings.AlwaysOn;
      foreach (string msg in messages)
      {
         using (TestClient proxy = new TestClient (new BasicHttpBinding(), new EndpointAddress(address)))
         {
            // ...
            proxy.Test(msg);
            // ...
         }
      }
   }
}
// Generated by SvcUtil.exe
public partial class TestClient : System.ServiceModel.ClientBase, ITest { }
```

<span data-ttu-id="93772-129">Ve výše uvedeném kódu všechny instance nástroje budou `TestClient` používat stejný objekt pro vytváření kanálů.</span><span class="sxs-lookup"><span data-stu-id="93772-129">In the above code, all instances of `TestClient` will use the same channel factory.</span></span>

```csharp
class Program
{
   static void Main(string[] args)
   {
      ClientBase.CacheSettings = CacheSettings.Default;
      int i = 1;
      foreach (string msg in messages)
      {
         using (TestClient proxy = new TestClient ("MyEndpoint", new EndpointAddress(address)))
         {
            if (i == 4)
            {
               ServiceEndpoint endpoint = proxy.Endpoint;
               ... // use endpoint in some way
            }
            proxy.Test(msg);
         }
         i++;
   }
}

// Generated by SvcUtil.exe
public partial class TestClient : System.ServiceModel.ClientBase, ITest {}
```

<span data-ttu-id="93772-130">V příkladu výše všechny instance nástroje by používaly stejný objekt pro `TestClient` vytváření kanálů kromě instance #4.</span><span class="sxs-lookup"><span data-stu-id="93772-130">In the example above, all instances of `TestClient` would use the same channel factory except instance #4.</span></span> <span data-ttu-id="93772-131">Instance #4 by používala objekt pro vytváření kanálů, který je vytvořen speciálně pro jeho použití.</span><span class="sxs-lookup"><span data-stu-id="93772-131">Instance #4 would use a channel factory that is created specifically for its use.</span></span> <span data-ttu-id="93772-132">Toto nastavení bude fungovat pro scénáře, ve kterých konkrétní koncový bod potřebuje různá nastavení zabezpečení z ostatních koncových bodů stejného typu objektu pro vytváření kanálů ( `ITest`v tomto případě).</span><span class="sxs-lookup"><span data-stu-id="93772-132">This setting would work for scenarios where a particular endpoint needs different security settings from the other endpoints of the same channel factory type (in this case `ITest`).</span></span>

```csharp
class Program
{
   static void Main(string[] args)
   {
      ClientBase.CacheSettings = CacheSettings.AlwaysOff;
      foreach (string msg in messages)
      {
         using (TestClient proxy = new TestClient ("MyEndpoint", new EndpointAddress(address)))
         {
            proxy.Test(msg);
         }
      }
   }
}

// Generated by SvcUtil.exe
public partial class TestClient : System.ServiceModel.ClientBase, ITest {}
```

<span data-ttu-id="93772-133">V příkladu výše všechny instance `TestClient` nástroje by používaly různé továrny kanálů.</span><span class="sxs-lookup"><span data-stu-id="93772-133">In the example above, all instances of `TestClient` would use different channel factories.</span></span> <span data-ttu-id="93772-134">To je užitečné v případě, že každý koncový bod má jiné požadavky na zabezpečení a nemá žádný smysl ukládat do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="93772-134">This is useful when each endpoint has different security requirements and it makes no sense to cache.</span></span>

## <a name="see-also"></a><span data-ttu-id="93772-135">Viz také:</span><span class="sxs-lookup"><span data-stu-id="93772-135">See also</span></span>

- <xref:System.ServiceModel.ClientBase%601>
- [<span data-ttu-id="93772-136">Sestavování klientů</span><span class="sxs-lookup"><span data-stu-id="93772-136">Building Clients</span></span>](../../../../docs/framework/wcf/building-clients.md)
- [<span data-ttu-id="93772-137">Klienti</span><span class="sxs-lookup"><span data-stu-id="93772-137">Clients</span></span>](../../../../docs/framework/wcf/feature-details/clients.md)
- [<span data-ttu-id="93772-138">Přístup ke službám pomocí klienta WCF</span><span class="sxs-lookup"><span data-stu-id="93772-138">Accessing Services Using a WCF Client</span></span>](../../../../docs/framework/wcf/accessing-services-using-a-wcf-client.md)
- [<span data-ttu-id="93772-139">Postupy: Použití třídy ChannelFactory</span><span class="sxs-lookup"><span data-stu-id="93772-139">How to: Use the ChannelFactory</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-the-channelfactory.md)
