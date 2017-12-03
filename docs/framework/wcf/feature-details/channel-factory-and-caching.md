---
title: "Postup kanálu a mezipaměť"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 954f030e-091c-4c0e-a7a2-10f9a6b1f529
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 1b06d290760afa9a52274c30899e25f00bc18af2
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="channel-factory-and-caching"></a><span data-ttu-id="6f836-102">Postup kanálu a mezipaměť</span><span class="sxs-lookup"><span data-stu-id="6f836-102">Channel Factory and Caching</span></span>
<span data-ttu-id="6f836-103">Pomocí klientských aplikací WCF <xref:System.ServiceModel.ChannelFactory%601> třída k vytvoření kanálu komunikace se službou WCF.</span><span class="sxs-lookup"><span data-stu-id="6f836-103">WCF client applications use the <xref:System.ServiceModel.ChannelFactory%601> class to create a communication channel with a WCF service.</span></span>  <span data-ttu-id="6f836-104">Vytváření <xref:System.ServiceModel.ChannelFactory%601> instance způsobuje zvýšení zatížení, protože se týká následující operace:</span><span class="sxs-lookup"><span data-stu-id="6f836-104">Creating <xref:System.ServiceModel.ChannelFactory%601> instances incurs some overhead because it involves the following operations:</span></span>  
  
-   <span data-ttu-id="6f836-105">Vytváření <xref:System.ServiceModel.Description.ContractDescription> stromu</span><span class="sxs-lookup"><span data-stu-id="6f836-105">Constructing the <xref:System.ServiceModel.Description.ContractDescription> tree</span></span>  
  
-   <span data-ttu-id="6f836-106">Odrážející všechny požadované typy CLR</span><span class="sxs-lookup"><span data-stu-id="6f836-106">Reflecting all of the required CLR types</span></span>  
  
-   <span data-ttu-id="6f836-107">Vytváření kanálu zásobníku</span><span class="sxs-lookup"><span data-stu-id="6f836-107">Constructing the channel stack</span></span>  
  
-   <span data-ttu-id="6f836-108">Uvolnění prostředků</span><span class="sxs-lookup"><span data-stu-id="6f836-108">Disposing of resources</span></span>  
  
 <span data-ttu-id="6f836-109">Abyste minimalizovali Tato dodatečná režie, můžete WCF mezipaměti objektů Factory kanál, když používáte proxy server klienta WCF.</span><span class="sxs-lookup"><span data-stu-id="6f836-109">To help minimize this overhead, WCF can cache channel factories when you are using a WCF client proxy.</span></span>  
  
> [!TIP]
>  <span data-ttu-id="6f836-110">Máte přímou kontrolu nad vytvoření objektu pro vytváření kanálu při použití <xref:System.ServiceModel.ChannelFactory%601> přímo třídu.</span><span class="sxs-lookup"><span data-stu-id="6f836-110">You have direct control over channel factory creation when you use the <xref:System.ServiceModel.ChannelFactory%601> class directly.</span></span>  
  
 <span data-ttu-id="6f836-111">Proxy klienta WCF vygeneroval s [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) jsou odvozeny od <xref:System.ServiceModel.ClientBase%601>.</span><span class="sxs-lookup"><span data-stu-id="6f836-111">WCF client proxies generated with [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) are derived from <xref:System.ServiceModel.ClientBase%601>.</span></span> <span data-ttu-id="6f836-112"><xref:System.ServiceModel.ClientBase%601>Definuje statického <xref:System.ServiceModel.ClientBase%601.CacheSetting%2A> vlastnost, která definuje chování ukládání do mezipaměti objekt pro vytváření kanálu.</span><span class="sxs-lookup"><span data-stu-id="6f836-112"><xref:System.ServiceModel.ClientBase%601> defines a static <xref:System.ServiceModel.ClientBase%601.CacheSetting%2A> property that defines channel factory caching behavior.</span></span> <span data-ttu-id="6f836-113">Nastavení mezipaměti jsou vytvářeny pro konkrétní typ.</span><span class="sxs-lookup"><span data-stu-id="6f836-113">Cache settings are made for a specific type.</span></span> <span data-ttu-id="6f836-114">Například nastavení `ClientBase<ITest>.CacheSettings` na jednu z hodnot fronty definovaných níže ovlivní pouze ty proxy nebo třídu ClientBase typu `ITest`.</span><span class="sxs-lookup"><span data-stu-id="6f836-114">For example, setting  `ClientBase<ITest>.CacheSettings` to one of the values defined below will affect only those proxy/ClientBase of type `ITest`.</span></span> <span data-ttu-id="6f836-115">Nastavení mezipaměti pro konkrétní <xref:System.ServiceModel.ClientBase%601> se nedá změnit, jakmile se vytvoří první instance proxy nebo třídu ClientBase.</span><span class="sxs-lookup"><span data-stu-id="6f836-115">The cache setting for a particular <xref:System.ServiceModel.ClientBase%601> is immutable as soon as the first proxy/ClientBase instance is created.</span></span>  
  
## <a name="specifying-caching-behavior"></a><span data-ttu-id="6f836-116">Určení chování ukládání do mezipaměti</span><span class="sxs-lookup"><span data-stu-id="6f836-116">Specifying Caching Behavior</span></span>  
 <span data-ttu-id="6f836-117">Chování ukládání do mezipaměti je určený nastavením <xref:System.ServiceModel.ClientBase%601.CacheSetting> vlastnost na jednu z následujících hodnot.</span><span class="sxs-lookup"><span data-stu-id="6f836-117">Caching behavior is specified by setting the <xref:System.ServiceModel.ClientBase%601.CacheSetting> property to one of the following values.</span></span>  
  
|<span data-ttu-id="6f836-118">Nastavení hodnoty do mezipaměti</span><span class="sxs-lookup"><span data-stu-id="6f836-118">Cache Setting Value</span></span>|<span data-ttu-id="6f836-119">Popis</span><span class="sxs-lookup"><span data-stu-id="6f836-119">Description</span></span>|  
|-------------------------|-----------------|  
|<xref:System.ServiceModel.CacheSetting.AlwaysOn>|<span data-ttu-id="6f836-120">Všechny instance <xref:System.ServiceModel.ClientBase%601> v rámci domény aplikace mohou být součástí ukládání do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="6f836-120">All instances of <xref:System.ServiceModel.ClientBase%601> within the app-domain can participate in caching.</span></span> <span data-ttu-id="6f836-121">Vývojář bylo zjištěno, že neexistují žádné negativní zabezpečení dopady na ukládání do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="6f836-121">The developer has determined that there are no adverse security implications to caching.</span></span> <span data-ttu-id="6f836-122">Ukládání do mezipaměti nebude to i v případě "citlivé na zabezpečení" vlastnosti na vypnout <xref:System.ServiceModel.ClientBase%601> ke kterým se přistupuje.</span><span class="sxs-lookup"><span data-stu-id="6f836-122">Caching will not be turned off even if "security-sensitive" properties on <xref:System.ServiceModel.ClientBase%601> are accessed.</span></span> <span data-ttu-id="6f836-123">Vlastnosti "citlivé na zabezpečení" <xref:System.ServiceModel.ClientBase%601> jsou <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A>, <xref:System.ServiceModel.ClientBase%601.Endpoint%2A> a <xref:System.ServiceModel.ClientBase%601.ChannelFactory%2A>.</span><span class="sxs-lookup"><span data-stu-id="6f836-123">The "security-sensitive" properties of <xref:System.ServiceModel.ClientBase%601> are <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A>, <xref:System.ServiceModel.ClientBase%601.Endpoint%2A> and <xref:System.ServiceModel.ClientBase%601.ChannelFactory%2A>.</span></span>|  
|<xref:System.ServiceModel.CacheSetting.Default>|<span data-ttu-id="6f836-124">Pouze instance <xref:System.ServiceModel.ClientBase%601> vytvořené z koncové body definované v konfiguraci soubory účastnit ukládání do mezipaměti v rámci domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="6f836-124">Only instances of <xref:System.ServiceModel.ClientBase%601> created from endpoints defined in configuration files participate in caching within the app-domain.</span></span> <span data-ttu-id="6f836-125">Všechny instance <xref:System.ServiceModel.ClientBase%601> vytvořit prostřednictvím kódu programu v této doméně aplikace se neúčastní ukládání do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="6f836-125">Any instances of <xref:System.ServiceModel.ClientBase%601> created programmatically within that app-domain will not participate in caching.</span></span> <span data-ttu-id="6f836-126">Navíc ukládání do mezipaměti bude zakázán pro instanci <xref:System.ServiceModel.ClientBase%601> po některou z jejích vlastností "citlivé na zabezpečení" přistupuje.</span><span class="sxs-lookup"><span data-stu-id="6f836-126">Also, caching will be disabled for an instance of <xref:System.ServiceModel.ClientBase%601> once any of its "security-sensitive" properties is accessed.</span></span>|  
|<xref:System.ServiceModel.CacheSetting.AlwaysOff>|<span data-ttu-id="6f836-127">Ukládání do mezipaměti je vypnuté pro všechny instance <xref:System.ServiceModel.ClientBase%601> určitého typu v rámci dotyčném domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="6f836-127">Caching is turned off for all instances of <xref:System.ServiceModel.ClientBase%601> of a particular type within the app-domain in question.</span></span>|  
  
 <span data-ttu-id="6f836-128">Následující fragmenty kódu ukazují, jak používat <xref:System.ServiceModel.ClientBase%601.CacheSetting%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="6f836-128">The following code snippets illustrate how to use the <xref:System.ServiceModel.ClientBase%601.CacheSetting%2A> property.</span></span>  
  
```  
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
  
 <span data-ttu-id="6f836-129">Ve výše uvedeném kódu, všechny instance `TestClient` bude používat stejné kanálu.</span><span class="sxs-lookup"><span data-stu-id="6f836-129">In the above code, all instances of `TestClient` will use the same channel factory.</span></span>  
  
```  
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
  
 <span data-ttu-id="6f836-130">V příkladu výše, všechny instance `TestClient` byste použili stejné kanálu s výjimkou instanci #4.</span><span class="sxs-lookup"><span data-stu-id="6f836-130">In the example above, all instances of `TestClient` would use the same channel factory except instance #4.</span></span> <span data-ttu-id="6f836-131">Instance #4 využije kanálu, který je vytvořena speciálně pro jeho použití.</span><span class="sxs-lookup"><span data-stu-id="6f836-131">Instance #4 would use a channel factory that is created specifically for its use.</span></span> <span data-ttu-id="6f836-132">Toto nastavení by fungovat pro scénáře, kde konkrétní koncový bod potřebuje jiné bezpečnostní nastavení z dalších koncových bodů stejný typ objektu pro vytváření kanálu (v tomto případě `ITest`).</span><span class="sxs-lookup"><span data-stu-id="6f836-132">This setting would work for scenarios where a particular endpoint needs different security settings from the other endpoints of the same channel factory type (in this case `ITest`).</span></span>  
  
```  
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
  
 <span data-ttu-id="6f836-133">V příkladu výše, všechny instance `TestClient` byste použili jiný kanál objekty pro vytváření.</span><span class="sxs-lookup"><span data-stu-id="6f836-133">In the example above, all instances of `TestClient` would use different channel factories.</span></span> <span data-ttu-id="6f836-134">To je užitečné, když každý koncový bod má jiné požadavky na zabezpečení a nemá smysl do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="6f836-134">This is useful when each endpoint has different security requirements and it makes no sense to cache.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f836-135">Viz také</span><span class="sxs-lookup"><span data-stu-id="6f836-135">See Also</span></span>  
 <xref:System.ServiceModel.ClientBase%601>  
 [<span data-ttu-id="6f836-136">Sestavování klientů</span><span class="sxs-lookup"><span data-stu-id="6f836-136">Building Clients</span></span>](../../../../docs/framework/wcf/building-clients.md)  
 [<span data-ttu-id="6f836-137">Klienti</span><span class="sxs-lookup"><span data-stu-id="6f836-137">Clients</span></span>](../../../../docs/framework/wcf/feature-details/clients.md)  
 [<span data-ttu-id="6f836-138">Přístup ke službám pomocí klienta WCF</span><span class="sxs-lookup"><span data-stu-id="6f836-138">Accessing Services Using a WCF Client</span></span>](../../../../docs/framework/wcf/accessing-services-using-a-wcf-client.md)  
 [<span data-ttu-id="6f836-139">Postupy: použití třídy ChannelFactory</span><span class="sxs-lookup"><span data-stu-id="6f836-139">How to: Use the ChannelFactory</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-the-channelfactory.md)
