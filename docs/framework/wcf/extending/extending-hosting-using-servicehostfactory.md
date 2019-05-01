---
title: Rozšíření hostování pomocí třídy ServiceHostFactory
ms.date: 03/30/2017
ms.assetid: bcc5ae1b-21ce-4e0e-a184-17fad74a441e
ms.openlocfilehash: e553fe161ffc5b50850d916cf1cef6b38dd5c1a9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61991312"
---
# <a name="extending-hosting-using-servicehostfactory"></a><span data-ttu-id="6328b-102">Rozšíření hostování pomocí třídy ServiceHostFactory</span><span class="sxs-lookup"><span data-stu-id="6328b-102">Extending Hosting Using ServiceHostFactory</span></span>
<span data-ttu-id="6328b-103">Standardní <xref:System.ServiceModel.ServiceHost> bod rozšiřitelnosti architektury WCF je rozhraní API pro hostování služby Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="6328b-103">The standard <xref:System.ServiceModel.ServiceHost> API for hosting services in Windows Communication Foundation (WCF) is an extensibility point in the WCF architecture.</span></span> <span data-ttu-id="6328b-104">Uživatelé můžou odvozovat vlastní hostitele z <xref:System.ServiceModel.ServiceHost>, obvykle k přepsání <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening> používat <xref:System.ServiceModel.Description.ServiceDescription> výchozí koncové body imperativně přidávat nebo upravovat chování před otevřením služby.</span><span class="sxs-lookup"><span data-stu-id="6328b-104">Users can derive their own host classes from <xref:System.ServiceModel.ServiceHost>, usually to override <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening> to use <xref:System.ServiceModel.Description.ServiceDescription> to add default endpoints imperatively or modify behaviors, prior to opening the service.</span></span>  
  
 <span data-ttu-id="6328b-105">V prostředí hostování na vlastním serveru, není nutné vytvořit vlastní <xref:System.ServiceModel.ServiceHost> vzhledem k tomu, že napíšete kód, který vytvoří instanci hostitele a poté zavolejte <xref:System.ServiceModel.ICommunicationObject.Open> na něm po vytvořit její instanci.</span><span class="sxs-lookup"><span data-stu-id="6328b-105">In the self-host environment, you do not have to create a custom <xref:System.ServiceModel.ServiceHost> because you write the code that instantiates the host and then call <xref:System.ServiceModel.ICommunicationObject.Open> on it after you instantiate it.</span></span> <span data-ttu-id="6328b-106">Mezi tyto dva kroky vám pomůžou cokoliv, co chcete.</span><span class="sxs-lookup"><span data-stu-id="6328b-106">Between those two steps you can do whatever you want.</span></span> <span data-ttu-id="6328b-107">Například můžete přidat nový <xref:System.ServiceModel.Description.IServiceBehavior>:</span><span class="sxs-lookup"><span data-stu-id="6328b-107">You could, for example, add a new <xref:System.ServiceModel.Description.IServiceBehavior>:</span></span>  
  
```  
public static void Main()  
{  
   ServiceHost host = new ServiceHost( typeof( MyService ) );  
   host.Description.Add( new MyServiceBehavior() );  
   host.Open();  
  
   ...  
}  
```  
  
 <span data-ttu-id="6328b-108">Tento přístup není opakovaně použitelné.</span><span class="sxs-lookup"><span data-stu-id="6328b-108">This approach is not reusable.</span></span> <span data-ttu-id="6328b-109">Kód, který provádí úpravy popisu je zakódovaný do hostitelského programu (v tomto případě funkce Main()), takže je obtížné znovu použít tuto logiku v jiném kontextu.</span><span class="sxs-lookup"><span data-stu-id="6328b-109">The code that manipulates the description is coded into the host program (in this case, the Main() function), so it is difficult to reuse that logic in other contexts.</span></span> <span data-ttu-id="6328b-110">Existují také jiné způsoby přidání <xref:System.ServiceModel.Description.IServiceBehavior> , které nevyžadují imperativního kódu.</span><span class="sxs-lookup"><span data-stu-id="6328b-110">There are also other ways of adding an <xref:System.ServiceModel.Description.IServiceBehavior> that do not require imperative code.</span></span> <span data-ttu-id="6328b-111">Lze odvodit z atributu <xref:System.ServiceModel.ServiceBehaviorAttribute> a vložit, že pro vaše implementace služby typu nebo je můžete konfigurovatelné vlastní chování a tvoří ji dynamicky pomocí konfigurace.</span><span class="sxs-lookup"><span data-stu-id="6328b-111">You can derive an attribute from <xref:System.ServiceModel.ServiceBehaviorAttribute> and put that on your service implementation type or you can make a custom behavior configurable and compose it dynamically using configuration.</span></span>  
  
 <span data-ttu-id="6328b-112">Však drobnou změnu v příkladu můžete také použít pro vyřešení tohoto problému.</span><span class="sxs-lookup"><span data-stu-id="6328b-112">However, a slight variation of the example can also be used to solve this problem.</span></span> <span data-ttu-id="6328b-113">Jedním z přístupů je přesunout kód, který přidá ServiceBehavior z celkového počtu `Main()` a do <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A> metoda vlastní odvozený ze <xref:System.ServiceModel.ServiceHost>:</span><span class="sxs-lookup"><span data-stu-id="6328b-113">One approach is to move the code that adds the ServiceBehavior out of `Main()` and into the <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A> method of a custom derivative of <xref:System.ServiceModel.ServiceHost>:</span></span>  
  
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
  
 <span data-ttu-id="6328b-114">Potom ovládacího `Main()` můžete použít:</span><span class="sxs-lookup"><span data-stu-id="6328b-114">Then, inside of `Main()` you can use:</span></span>  
  
```  
public static void Main()  
{  
   ServiceHost host = new DerivedHost( typeof( MyService ) );  
   host.Open();  
  
   ...  
}  
```  
  
 <span data-ttu-id="6328b-115">Nyní máte zapouzdřené vlastní logiku do čistého abstrakce, která lze snadno opětovně použít napříč mnoha spustitelné soubory jiného hostitele.</span><span class="sxs-lookup"><span data-stu-id="6328b-115">Now you have encapsulated the custom logic into a clean abstraction that can be easily reused across many different host executables.</span></span>  
  
 <span data-ttu-id="6328b-116">Není-li si hned zjevné, jak používat tento vlastní <xref:System.ServiceModel.ServiceHost> z v rámci Internetové informační služby (IIS) nebo Windows Process Activation Service (WAS).</span><span class="sxs-lookup"><span data-stu-id="6328b-116">It is not immediately obvious how to use this custom <xref:System.ServiceModel.ServiceHost> from inside of Internet Information Services (IIS) or Windows Process Activation Service (WAS).</span></span> <span data-ttu-id="6328b-117">Těchto prostředích se liší od prostředí hostování na vlastním serveru, protože hostitelské prostředí je jeden vytvoření instance <xref:System.ServiceModel.ServiceHost> jménem aplikace.</span><span class="sxs-lookup"><span data-stu-id="6328b-117">Those environments are different than the self-host environment, because the hosting environment is the one instantiating the <xref:System.ServiceModel.ServiceHost> on behalf of the application.</span></span> <span data-ttu-id="6328b-118">Infrastruktury hostování IIS a WAS neví nic o vaší vlastní <xref:System.ServiceModel.ServiceHost> odvozených děl na základě.</span><span class="sxs-lookup"><span data-stu-id="6328b-118">The IIS and WAS hosting infrastructure does not know anything about your custom <xref:System.ServiceModel.ServiceHost> derivative.</span></span>  
  
 <span data-ttu-id="6328b-119"><xref:System.ServiceModel.Activation.ServiceHostFactory> Je navržená pro vyřešení tohoto problému, přístup k vaší vlastní <xref:System.ServiceModel.ServiceHost> z v rámci služby IIS nebo WAS.</span><span class="sxs-lookup"><span data-stu-id="6328b-119">The <xref:System.ServiceModel.Activation.ServiceHostFactory> was designed to solve this problem of accessing your custom <xref:System.ServiceModel.ServiceHost> from within IIS or WAS.</span></span> <span data-ttu-id="6328b-120">Protože vlastního hostitele, který je odvozen z <xref:System.ServiceModel.ServiceHost> dynamicky nakonfigurovaný a potenciálně různých typů, hostitelské prostředí nikdy vytvoří z něj přímo.</span><span class="sxs-lookup"><span data-stu-id="6328b-120">Because a custom host that is derived from <xref:System.ServiceModel.ServiceHost> is dynamically configured and potentially of various types, the hosting environment never instantiates it directly.</span></span> <span data-ttu-id="6328b-121">Místo toho WCF používá vzor factory zajistit určitou úroveň dereference mezi hostitelské prostředí a konkrétní typ služby.</span><span class="sxs-lookup"><span data-stu-id="6328b-121">Instead, WCF uses a factory pattern to provide a layer of indirection between the hosting environment and the concrete type of the service.</span></span> <span data-ttu-id="6328b-122">Pokud dáte ho jinak, používá výchozí implementaci třídy <xref:System.ServiceModel.Activation.ServiceHostFactory> , která vrací instanci <xref:System.ServiceModel.ServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="6328b-122">Unless you tell it otherwise, it uses a default implementation of <xref:System.ServiceModel.Activation.ServiceHostFactory> that returns an instance of <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="6328b-123">Ale můžete taky zadat vlastní objekt pro vytváření, který vrací odvozené hostitele tak, že zadáte název typu CLR továrny implementace v @ServiceHost směrnice.</span><span class="sxs-lookup"><span data-stu-id="6328b-123">But you can also provide your own factory that returns your derived host by specifying the CLR type name of your factory implementation in the @ServiceHost directive.</span></span>  
  
 <span data-ttu-id="6328b-124">Cílem je, že pro základní případy implementace vlastní objekt pro vytváření by měl přímo dopředné cvičení.</span><span class="sxs-lookup"><span data-stu-id="6328b-124">The intent is that for basic cases, implementing your own factory should be a straight forward exercise.</span></span> <span data-ttu-id="6328b-125">Například tady je vlastní <xref:System.ServiceModel.Activation.ServiceHostFactory> , která vrací odvozený <xref:System.ServiceModel.ServiceHost>:</span><span class="sxs-lookup"><span data-stu-id="6328b-125">For example, here is a custom <xref:System.ServiceModel.Activation.ServiceHostFactory> that returns a derived <xref:System.ServiceModel.ServiceHost>:</span></span>  
  
```  
public class DerivedFactory : ServiceHostFactory  
{  
   public override ServiceHost CreateServiceHost( Type t, Uri[] baseAddresses )  
   {  
      return new DerivedHost( t, baseAddresses )  
   }  
}  
```  
  
 <span data-ttu-id="6328b-126">Pokud chcete použít tento objekt pro vytváření místo výchozí objekt pro vytváření, zadejte název typu v @ServiceHost směrnice následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="6328b-126">To use this factory instead of the default factory, provide the type name in the @ServiceHost directive as follows:</span></span>  
  
```  
<% @ServiceHost Factory="DerivedFactory" Service="MyService" %>  
```  
  
 <span data-ttu-id="6328b-127">Na to, co byste chtěli se neplatí žádné technická omezení <xref:System.ServiceModel.ServiceHost> vrátit z <xref:System.ServiceModel.Activation.ServiceHostFactory.CreateServiceHost%2A>, doporučujeme, abyste vaše implementace factory co nejjednodušší.</span><span class="sxs-lookup"><span data-stu-id="6328b-127">While there is no technical limit on doing what you want to the <xref:System.ServiceModel.ServiceHost> you return from <xref:System.ServiceModel.Activation.ServiceHostFactory.CreateServiceHost%2A>, we suggest that you keep your factory implementations as simple as possible.</span></span> <span data-ttu-id="6328b-128">Pokud máte velké množství vlastní logiku, je lepší umístěte tuto logiku uvnitř hostitele místo objekt pro vytváření tak, aby ji bylo možné opakovaně použitelné.</span><span class="sxs-lookup"><span data-stu-id="6328b-128">If you have lots of custom logic, it is better to put that logic inside of you host instead of inside the factory so that it can be reusable.</span></span>  
  
 <span data-ttu-id="6328b-129">Existuje jeden další vrstvy do hostujícího rozhraní API, která by měla být uvedeny zde.</span><span class="sxs-lookup"><span data-stu-id="6328b-129">There is one more layer to the hosting API that should be mentioned here.</span></span> <span data-ttu-id="6328b-130">WCF má také <xref:System.ServiceModel.ServiceHostBase> a <xref:System.ServiceModel.Activation.ServiceHostFactoryBase>, ze kterého <xref:System.ServiceModel.ServiceHost> a <xref:System.ServiceModel.Activation.ServiceHostFactory> odvodit v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="6328b-130">WCF also has <xref:System.ServiceModel.ServiceHostBase> and <xref:System.ServiceModel.Activation.ServiceHostFactoryBase>, from which <xref:System.ServiceModel.ServiceHost> and <xref:System.ServiceModel.Activation.ServiceHostFactory> respectively derive.</span></span> <span data-ttu-id="6328b-131">Neexistují pro pokročilejší scénáře, ve kterém musí vyměnit velké části metadat systému s vlastní přizpůsobené vytváření.</span><span class="sxs-lookup"><span data-stu-id="6328b-131">Those exist for more advanced scenarios where you must swap out large parts of the metadata system with your own customized creations.</span></span>
