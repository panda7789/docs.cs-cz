---
title: "Rozšíření hostování pomocí třídy ServiceHostFactory"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bcc5ae1b-21ce-4e0e-a184-17fad74a441e
caps.latest.revision: "12"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 06859e8f12f96f964054817bac553f6534d5960e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="extending-hosting-using-servicehostfactory"></a><span data-ttu-id="3a0ee-102">Rozšíření hostování pomocí třídy ServiceHostFactory</span><span class="sxs-lookup"><span data-stu-id="3a0ee-102">Extending Hosting Using ServiceHostFactory</span></span>
<span data-ttu-id="3a0ee-103">Standardní <xref:System.ServiceModel.ServiceHost> rozhraní API pro hostování služeb v [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] je bod rozšiřitelnosti v [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] architektura.</span><span class="sxs-lookup"><span data-stu-id="3a0ee-103">The standard <xref:System.ServiceModel.ServiceHost> API for hosting services in [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] is an extensibility point in the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] architecture.</span></span> <span data-ttu-id="3a0ee-104">Uživatelé mohou odvozovat vlastní hostitele z <xref:System.ServiceModel.ServiceHost>, obvykle k přepsání <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening> používat <xref:System.ServiceModel.Description.ServiceDescription> výchozí koncové body imperativní přidávat nebo upravovat chování před otevřením službu.</span><span class="sxs-lookup"><span data-stu-id="3a0ee-104">Users can derive their own host classes from <xref:System.ServiceModel.ServiceHost>, usually to override <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening> to use <xref:System.ServiceModel.Description.ServiceDescription> to add default endpoints imperatively or modify behaviors, prior to opening the service.</span></span>  
  
 <span data-ttu-id="3a0ee-105">V prostředí hostování na vlastním serveru nemáte vytvoření vlastní <xref:System.ServiceModel.ServiceHost> protože napsat kód, který vytvoří instanci hostitele a pak zavolají <xref:System.ServiceModel.ICommunicationObject.Open> na něm po vytvoření instance ho.</span><span class="sxs-lookup"><span data-stu-id="3a0ee-105">In the self-host environment, you do not have to create a custom <xref:System.ServiceModel.ServiceHost> because you write the code that instantiates the host and then call <xref:System.ServiceModel.ICommunicationObject.Open> on it after you instantiate it.</span></span> <span data-ttu-id="3a0ee-106">Mezi tyto dva kroky můžete provést libovolně.</span><span class="sxs-lookup"><span data-stu-id="3a0ee-106">Between those two steps you can do whatever you want.</span></span> <span data-ttu-id="3a0ee-107">Například může přidat novou <xref:System.ServiceModel.Description.IServiceBehavior>:</span><span class="sxs-lookup"><span data-stu-id="3a0ee-107">You could, for example, add a new <xref:System.ServiceModel.Description.IServiceBehavior>:</span></span>  
  
```  
public static void Main()  
{  
   ServiceHost host = new ServiceHost( typeof( MyService ) );  
   host.Description.Add( new MyServiceBehavior() );  
   host.Open();  
  
   ...  
}  
```  
  
 <span data-ttu-id="3a0ee-108">Tento přístup není opakovaně použitelné.</span><span class="sxs-lookup"><span data-stu-id="3a0ee-108">This approach is not reusable.</span></span> <span data-ttu-id="3a0ee-109">Kód, který zpracovává popis je zakódovaný do hostitelského programu (v tomto případě funkce Main()), takže je obtížné znovu použít tuto logiku v jiném kontextu.</span><span class="sxs-lookup"><span data-stu-id="3a0ee-109">The code that manipulates the description is coded into the host program (in this case, the Main() function), so it is difficult to reuse that logic in other contexts.</span></span> <span data-ttu-id="3a0ee-110">Existují také další způsoby přidávání <xref:System.ServiceModel.Description.IServiceBehavior> nevyžadují imperativní kódu.</span><span class="sxs-lookup"><span data-stu-id="3a0ee-110">There are also other ways of adding an <xref:System.ServiceModel.Description.IServiceBehavior> that do not require imperative code.</span></span> <span data-ttu-id="3a0ee-111">Odvozujete atribut z <xref:System.ServiceModel.ServiceBehaviorAttribute> a umístí, na implementaci služby typu nebo můžete vytvořit vlastní chování konfigurovat a vytvořit dynamicky pomocí konfigurace.</span><span class="sxs-lookup"><span data-stu-id="3a0ee-111">You can derive an attribute from <xref:System.ServiceModel.ServiceBehaviorAttribute> and put that on your service implementation type or you can make a custom behavior configurable and compose it dynamically using configuration.</span></span>  
  
 <span data-ttu-id="3a0ee-112">Ale mírné varianta příkladu lze také chcete tento problém vyřešit.</span><span class="sxs-lookup"><span data-stu-id="3a0ee-112">However, a slight variation of the example can also be used to solve this problem.</span></span> <span data-ttu-id="3a0ee-113">Jeden z přístupů je přesunout kód, který přidá ServiceBehavior mimo `Main()` a do <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A> metoda vlastní odvozený ze <xref:System.ServiceModel.ServiceHost>:</span><span class="sxs-lookup"><span data-stu-id="3a0ee-113">One approach is to move the code that adds the ServiceBehavior out of `Main()` and into the <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A> method of a custom derivative of <xref:System.ServiceModel.ServiceHost>:</span></span>  
  
```  
public class DerivedHost : ServiceHost  
{  
   public DerivedHost( Type t, params Uri baseAddresses ) :  
      base( t, baseAddresses ) {}  
  
   public override void OnOpening()  
   {  
  this.Description.Add( new MyServiceBehavior() );  
   }  
}  
```  
  
 <span data-ttu-id="3a0ee-114">Potom uvnitř z `Main()` můžete použít:</span><span class="sxs-lookup"><span data-stu-id="3a0ee-114">Then, inside of `Main()` you can use:</span></span>  
  
```  
public static void Main()  
{  
   ServiceHost host = new DerivedHost( typeof( MyService ) );  
   host.Open();  
  
   ...  
}  
```  
  
 <span data-ttu-id="3a0ee-115">Nyní máte zapouzdřené vlastní logiky do čistého abstrakce, která lze snadno opětovně použít napříč mnoha spustitelné soubory jiného hostitele.</span><span class="sxs-lookup"><span data-stu-id="3a0ee-115">Now you have encapsulated the custom logic into a clean abstraction that can be easily reused across many different host executables.</span></span>  
  
 <span data-ttu-id="3a0ee-116">Není-li si hned zjevné, jak používat tento vlastní <xref:System.ServiceModel.ServiceHost> z v rámci Internetové informační služby (IIS) nebo služby Aktivace procesů systému Windows (WAS).</span><span class="sxs-lookup"><span data-stu-id="3a0ee-116">It is not immediately obvious how to use this custom <xref:System.ServiceModel.ServiceHost> from inside of Internet Information Services (IIS) or Windows Process Activation Service (WAS).</span></span> <span data-ttu-id="3a0ee-117">Těchto prostředích se liší od hostování na vlastním prostředí, protože jeden vytvoření instance hostitelského prostředí <xref:System.ServiceModel.ServiceHost> jménem aplikace.</span><span class="sxs-lookup"><span data-stu-id="3a0ee-117">Those environments are different than the self-host environment, because the hosting environment is the one instantiating the <xref:System.ServiceModel.ServiceHost> on behalf of the application.</span></span> <span data-ttu-id="3a0ee-118">Hostování infrastruktury služby IIS a WAS neví nic o vaše vlastní <xref:System.ServiceModel.ServiceHost> odvozených.</span><span class="sxs-lookup"><span data-stu-id="3a0ee-118">The IIS and WAS hosting infrastructure does not know anything about your custom <xref:System.ServiceModel.ServiceHost> derivative.</span></span>  
  
 <span data-ttu-id="3a0ee-119"><xref:System.ServiceModel.Activation.ServiceHostFactory> Byl navržen k vyřešení tohoto problému přístup k vaší vlastní <xref:System.ServiceModel.ServiceHost> z v rámci služby IIS nebo WAS.</span><span class="sxs-lookup"><span data-stu-id="3a0ee-119">The <xref:System.ServiceModel.Activation.ServiceHostFactory> was designed to solve this problem of accessing your custom <xref:System.ServiceModel.ServiceHost> from within IIS or WAS.</span></span> <span data-ttu-id="3a0ee-120">Protože vlastní hostitelů, který je odvozený od <xref:System.ServiceModel.ServiceHost> dynamicky nastavena a potenciálně různých typů hostitelské prostředí nikdy vytvoří z něj přímo.</span><span class="sxs-lookup"><span data-stu-id="3a0ee-120">Because a custom host that is derived from <xref:System.ServiceModel.ServiceHost> is dynamically configured and potentially of various types, the hosting environment never instantiates it directly.</span></span> <span data-ttu-id="3a0ee-121">Místo toho [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] používá vzor objektu pro vytváření zajistit úroveň dereference mezi hostitelské prostředí a konkrétní typ služby.</span><span class="sxs-lookup"><span data-stu-id="3a0ee-121">Instead, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uses a factory pattern to provide a layer of indirection between the hosting environment and the concrete type of the service.</span></span> <span data-ttu-id="3a0ee-122">Pokud k tomu nedostane jinak, používá výchozí implementaci třídy <xref:System.ServiceModel.Activation.ServiceHostFactory> která vrací instanci třídy <xref:System.ServiceModel.ServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="3a0ee-122">Unless you tell it otherwise, it uses a default implementation of <xref:System.ServiceModel.Activation.ServiceHostFactory> that returns an instance of <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="3a0ee-123">Ale můžete taky zadat vlastní objekt factory, který vrátí odvozené hostiteli tak, že zadáte název vaší implementace objektu factory v typu CLR @ServiceHost – direktiva.</span><span class="sxs-lookup"><span data-stu-id="3a0ee-123">But you can also provide your own factory that returns your derived host by specifying the CLR type name of your factory implementation in the @ServiceHost directive.</span></span>  
  
 <span data-ttu-id="3a0ee-124">Účelem je, že pro základní případy implementace vlastní objekt pro vytváření musí být splněny následující cvičení.</span><span class="sxs-lookup"><span data-stu-id="3a0ee-124">The intent is that for basic cases, implementing your own factory should be a straight forward exercise.</span></span> <span data-ttu-id="3a0ee-125">Zde je vlastní například <xref:System.ServiceModel.Activation.ServiceHostFactory> , který vrací odvozeným <xref:System.ServiceModel.ServiceHost>:</span><span class="sxs-lookup"><span data-stu-id="3a0ee-125">For example, here is a custom <xref:System.ServiceModel.Activation.ServiceHostFactory> that returns a derived <xref:System.ServiceModel.ServiceHost>:</span></span>  
  
```  
public class DerivedFactory : ServiceHostFactory  
{  
   public override ServiceHost CreateServiceHost( Type t, Uri[] baseAddresses )  
   {  
      return new DerivedHost( t, baseAddresses )  
   }  
}  
```  
  
 <span data-ttu-id="3a0ee-126">Místo výchozí objekt pro vytváření použít tento objekt pro vytváření, zadejte název typu ve @ServiceHost – direktiva následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="3a0ee-126">To use this factory instead of the default factory, provide the type name in the @ServiceHost directive as follows:</span></span>  
  
```  
<% @ServiceHost Factory="DerivedFactory" Service="MyService" %>  
```  
  
 <span data-ttu-id="3a0ee-127">Když neexistuje žádné technické omezení na to, co chcete <xref:System.ServiceModel.ServiceHost> vrátíte z <xref:System.ServiceModel.Activation.ServiceHostFactory.CreateServiceHost%2A>, doporučujeme, abyste vaší implementace objektu pro vytváření co nejjednodušší.</span><span class="sxs-lookup"><span data-stu-id="3a0ee-127">While there is no technical limit on doing what you want to the <xref:System.ServiceModel.ServiceHost> you return from <xref:System.ServiceModel.Activation.ServiceHostFactory.CreateServiceHost%2A>, we suggest that you keep your factory implementations as simple as possible.</span></span> <span data-ttu-id="3a0ee-128">Pokud máte velké množství vlastní logiky, je lepší uvést tuto logiku uvnitř hostitele místo uvnitř objektu pro vytváření, tak, aby bylo možné znovu použitelné.</span><span class="sxs-lookup"><span data-stu-id="3a0ee-128">If you have lots of custom logic, it is better to put that logic inside of you host instead of inside the factory so that it can be reusable.</span></span>  
  
 <span data-ttu-id="3a0ee-129">Neexistuje jeden další vrstvě pro hostování rozhraní API, které by se měla uvádět v tomto poli.</span><span class="sxs-lookup"><span data-stu-id="3a0ee-129">There is one more layer to the hosting API that should be mentioned here.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="3a0ee-130">má také <xref:System.ServiceModel.ServiceHostBase> a <xref:System.ServiceModel.Activation.ServiceHostFactoryBase>, ze kterého <xref:System.ServiceModel.ServiceHost> a <xref:System.ServiceModel.Activation.ServiceHostFactory> odvozena v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="3a0ee-130"> also has <xref:System.ServiceModel.ServiceHostBase> and <xref:System.ServiceModel.Activation.ServiceHostFactoryBase>, from which <xref:System.ServiceModel.ServiceHost> and <xref:System.ServiceModel.Activation.ServiceHostFactory> respectively derive.</span></span> <span data-ttu-id="3a0ee-131">Pro pokročilejší scénáře, kde musí vyměnit velké části systém metadat s vlastními přizpůsobené páskách těch, které neexistují.</span><span class="sxs-lookup"><span data-stu-id="3a0ee-131">Those exist for more advanced scenarios where you must swap out large parts of the metadata system with your own customized creations.</span></span>
