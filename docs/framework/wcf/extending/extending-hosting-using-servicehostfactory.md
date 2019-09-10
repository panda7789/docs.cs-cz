---
title: Rozšíření hostování pomocí třídy ServiceHostFactory
ms.date: 03/30/2017
ms.assetid: bcc5ae1b-21ce-4e0e-a184-17fad74a441e
ms.openlocfilehash: de6a590b94285872dd77006eda7f86d5d629be9d
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2019
ms.locfileid: "70849900"
---
# <a name="extending-hosting-using-servicehostfactory"></a><span data-ttu-id="a5d20-102">Rozšíření hostování pomocí třídy ServiceHostFactory</span><span class="sxs-lookup"><span data-stu-id="a5d20-102">Extending Hosting Using ServiceHostFactory</span></span>
<span data-ttu-id="a5d20-103">Standardní <xref:System.ServiceModel.ServiceHost> rozhraní API pro hostování služeb v Windows Communication Foundation (WCF) je bod rozšíření v architektuře WCF.</span><span class="sxs-lookup"><span data-stu-id="a5d20-103">The standard <xref:System.ServiceModel.ServiceHost> API for hosting services in Windows Communication Foundation (WCF) is an extensibility point in the WCF architecture.</span></span> <span data-ttu-id="a5d20-104">Uživatelé mohou odvodit své vlastní třídy hostitelů <xref:System.ServiceModel.ServiceHost>z, obvykle přepsat <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening> pro použití <xref:System.ServiceModel.Description.ServiceDescription> pro přidání výchozích koncových bodů imperativně nebo změnit chování před otevřením služby.</span><span class="sxs-lookup"><span data-stu-id="a5d20-104">Users can derive their own host classes from <xref:System.ServiceModel.ServiceHost>, usually to override <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening> to use <xref:System.ServiceModel.Description.ServiceDescription> to add default endpoints imperatively or modify behaviors, prior to opening the service.</span></span>  
  
 <span data-ttu-id="a5d20-105">V prostředí pro vlastní hostování nemusíte vytvářet vlastní <xref:System.ServiceModel.ServiceHost> , protože píšete kód, který vytváří instance hostitele, a pak ho zavolat <xref:System.ServiceModel.ICommunicationObject.Open> po jeho vytvoření.</span><span class="sxs-lookup"><span data-stu-id="a5d20-105">In the self-host environment, you do not have to create a custom <xref:System.ServiceModel.ServiceHost> because you write the code that instantiates the host and then call <xref:System.ServiceModel.ICommunicationObject.Open> on it after you instantiate it.</span></span> <span data-ttu-id="a5d20-106">Mezi těmito dvěma kroky můžete provádět cokoli, co potřebujete.</span><span class="sxs-lookup"><span data-stu-id="a5d20-106">Between those two steps you can do whatever you want.</span></span> <span data-ttu-id="a5d20-107">Můžete například přidat nové <xref:System.ServiceModel.Description.IServiceBehavior>:</span><span class="sxs-lookup"><span data-stu-id="a5d20-107">You could, for example, add a new <xref:System.ServiceModel.Description.IServiceBehavior>:</span></span>  
  
```csharp
public static void Main()  
{  
   ServiceHost host = new ServiceHost( typeof( MyService ) );  
   host.Description.Add( new MyServiceBehavior() );  
   host.Open();  
  
   ...  
}  
```  
  
 <span data-ttu-id="a5d20-108">Tento přístup nejde opakovaně použít.</span><span class="sxs-lookup"><span data-stu-id="a5d20-108">This approach is not reusable.</span></span> <span data-ttu-id="a5d20-109">Kód, který pracuje s popisem, je kódován do hostitelského programu (v tomto případě funkce main ()), takže je obtížné znovu použít tuto logiku v jiných kontextech.</span><span class="sxs-lookup"><span data-stu-id="a5d20-109">The code that manipulates the description is coded into the host program (in this case, the Main() function), so it is difficult to reuse that logic in other contexts.</span></span> <span data-ttu-id="a5d20-110">Existují také další způsoby přidávání <xref:System.ServiceModel.Description.IServiceBehavior> , které nevyžadují imperativní kód.</span><span class="sxs-lookup"><span data-stu-id="a5d20-110">There are also other ways of adding an <xref:System.ServiceModel.Description.IServiceBehavior> that do not require imperative code.</span></span> <span data-ttu-id="a5d20-111">Můžete odvodit atribut z <xref:System.ServiceModel.ServiceBehaviorAttribute> a umístit ho do typu implementace služby, nebo můžete vytvořit vlastní chování a vytvořit ho dynamicky pomocí konfigurace.</span><span class="sxs-lookup"><span data-stu-id="a5d20-111">You can derive an attribute from <xref:System.ServiceModel.ServiceBehaviorAttribute> and put that on your service implementation type or you can make a custom behavior configurable and compose it dynamically using configuration.</span></span>  
  
 <span data-ttu-id="a5d20-112">K vyřešení tohoto problému ale můžete použít i mírnou variaci tohoto příkladu.</span><span class="sxs-lookup"><span data-stu-id="a5d20-112">However, a slight variation of the example can also be used to solve this problem.</span></span> <span data-ttu-id="a5d20-113">Jedním z přístupů je přesunutí kódu, který přidá ServiceBehavior z `Main()` a <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A> do metody vlastního odvozeného <xref:System.ServiceModel.ServiceHost>:</span><span class="sxs-lookup"><span data-stu-id="a5d20-113">One approach is to move the code that adds the ServiceBehavior out of `Main()` and into the <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A> method of a custom derivative of <xref:System.ServiceModel.ServiceHost>:</span></span>  
  
```csharp
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
  
 <span data-ttu-id="a5d20-114">Pak můžete v `Main()` nástroji použít:</span><span class="sxs-lookup"><span data-stu-id="a5d20-114">Then, inside of `Main()` you can use:</span></span>  
  
```csharp
public static void Main()  
{  
   ServiceHost host = new DerivedHost( typeof( MyService ) );  
   host.Open();  
  
   ...  
}  
```  
  
 <span data-ttu-id="a5d20-115">Nyní jste zapouzdři vlastní logiky do čisté abstrakce, kterou je možné snadno znovu použít v mnoha různých spustitelných souborech hostitele.</span><span class="sxs-lookup"><span data-stu-id="a5d20-115">Now you have encapsulated the custom logic into a clean abstraction that can be easily reused across many different host executables.</span></span>  
  
 <span data-ttu-id="a5d20-116">Ihned není zřejmé, jak používat tuto vlastní <xref:System.ServiceModel.ServiceHost> verzi v rámci služby Internetová informační služba (IIS) nebo aktivační služby procesů systému Windows (WAS).</span><span class="sxs-lookup"><span data-stu-id="a5d20-116">It is not immediately obvious how to use this custom <xref:System.ServiceModel.ServiceHost> from inside of Internet Information Services (IIS) or Windows Process Activation Service (WAS).</span></span> <span data-ttu-id="a5d20-117">Tato prostředí se liší od prostředí pro samostatné hostování, protože hostující prostředí je jedním z instancí <xref:System.ServiceModel.ServiceHost> aplikace.</span><span class="sxs-lookup"><span data-stu-id="a5d20-117">Those environments are different than the self-host environment, because the hosting environment is the one instantiating the <xref:System.ServiceModel.ServiceHost> on behalf of the application.</span></span> <span data-ttu-id="a5d20-118">Infrastruktura služby IIS a byla hostingová infrastruktura neznala žádné informace <xref:System.ServiceModel.ServiceHost> o vašem vlastním derivátu.</span><span class="sxs-lookup"><span data-stu-id="a5d20-118">The IIS and WAS hosting infrastructure does not know anything about your custom <xref:System.ServiceModel.ServiceHost> derivative.</span></span>  
  
 <span data-ttu-id="a5d20-119">Byl navržen pro řešení tohoto problému s přístupem k vlastnímu <xref:System.ServiceModel.ServiceHost> z IIS nebo was. <xref:System.ServiceModel.Activation.ServiceHostFactory></span><span class="sxs-lookup"><span data-stu-id="a5d20-119">The <xref:System.ServiceModel.Activation.ServiceHostFactory> was designed to solve this problem of accessing your custom <xref:System.ServiceModel.ServiceHost> from within IIS or WAS.</span></span> <span data-ttu-id="a5d20-120">Vzhledem k tomu, že vlastní hostitel, <xref:System.ServiceModel.ServiceHost> který je odvozen z aplikace, je dynamicky nakonfigurován a potenciálně různých typů, hostující prostředí jej nikdy nevytváří instance přímo.</span><span class="sxs-lookup"><span data-stu-id="a5d20-120">Because a custom host that is derived from <xref:System.ServiceModel.ServiceHost> is dynamically configured and potentially of various types, the hosting environment never instantiates it directly.</span></span> <span data-ttu-id="a5d20-121">Místo toho WCF používá model továrny k zajištění vrstvy dereference mezi hostujícím prostředím a konkrétním typem služby.</span><span class="sxs-lookup"><span data-stu-id="a5d20-121">Instead, WCF uses a factory pattern to provide a layer of indirection between the hosting environment and the concrete type of the service.</span></span> <span data-ttu-id="a5d20-122">Pokud to neuděláte jinak, používá výchozí implementaci <xref:System.ServiceModel.Activation.ServiceHostFactory> , která vrací <xref:System.ServiceModel.ServiceHost>instanci.</span><span class="sxs-lookup"><span data-stu-id="a5d20-122">Unless you tell it otherwise, it uses a default implementation of <xref:System.ServiceModel.Activation.ServiceHostFactory> that returns an instance of <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="a5d20-123">Můžete ale také zadat vlastní továrnu, která vrátí vašeho odvozeného hostitele zadáním názvu typu CLR implementace výroby v @ServiceHost direktivě.</span><span class="sxs-lookup"><span data-stu-id="a5d20-123">But you can also provide your own factory that returns your derived host by specifying the CLR type name of your factory implementation in the @ServiceHost directive.</span></span>  
  
 <span data-ttu-id="a5d20-124">Záměrem je, že implementace vlastního továrny by měla být přímým výkonem.</span><span class="sxs-lookup"><span data-stu-id="a5d20-124">The intent is that for basic cases, implementing your own factory should be a straight forward exercise.</span></span> <span data-ttu-id="a5d20-125">Například zde je vlastní <xref:System.ServiceModel.Activation.ServiceHostFactory> , který vrací odvozenou: <xref:System.ServiceModel.ServiceHost></span><span class="sxs-lookup"><span data-stu-id="a5d20-125">For example, here is a custom <xref:System.ServiceModel.Activation.ServiceHostFactory> that returns a derived <xref:System.ServiceModel.ServiceHost>:</span></span>  
  
```csharp
public class DerivedFactory : ServiceHostFactory  
{  
   public override ServiceHost CreateServiceHost( Type t, Uri[] baseAddresses )  
   {  
      return new DerivedHost( t, baseAddresses )  
   }  
}  
```  
  
 <span data-ttu-id="a5d20-126">Chcete-li použít tuto továrnu namísto výchozího objektu pro vytváření, zadejte název typu @ServiceHost v direktivě následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="a5d20-126">To use this factory instead of the default factory, provide the type name in the @ServiceHost directive as follows:</span></span>  
  
`<% @ServiceHost Factory="DerivedFactory" Service="MyService" %>`  
  
 <span data-ttu-id="a5d20-127">I když nebudete mít k <xref:System.ServiceModel.ServiceHost> dispozici žádný technický limit k tomu, abyste se mohli vrátit z <xref:System.ServiceModel.Activation.ServiceHostFactory.CreateServiceHost%2A>, doporučujeme, abyste zajistili, že vaše tovární implementace bude co nejjednodušší.</span><span class="sxs-lookup"><span data-stu-id="a5d20-127">While there is no technical limit on doing what you want to the <xref:System.ServiceModel.ServiceHost> you return from <xref:System.ServiceModel.Activation.ServiceHostFactory.CreateServiceHost%2A>, we suggest that you keep your factory implementations as simple as possible.</span></span> <span data-ttu-id="a5d20-128">Pokud máte spoustu vlastní logiky, je lepší tuto logiku umístit do svého hostitele místo do továrny, aby ji bylo možné znovu použít.</span><span class="sxs-lookup"><span data-stu-id="a5d20-128">If you have lots of custom logic, it is better to put that logic inside of your host instead of inside the factory so that it can be reusable.</span></span>  
  
 <span data-ttu-id="a5d20-129">Rozhraní API pro hostování obsahuje jednu vrstvu, která by zde měla být zmíněná.</span><span class="sxs-lookup"><span data-stu-id="a5d20-129">There is one more layer to the hosting API that should be mentioned here.</span></span> <span data-ttu-id="a5d20-130">WCF má <xref:System.ServiceModel.ServiceHostBase> také a <xref:System.ServiceModel.Activation.ServiceHostFactoryBase>, ze kterého <xref:System.ServiceModel.ServiceHost> a <xref:System.ServiceModel.Activation.ServiceHostFactory> v tomto případě jsou odvozeny.</span><span class="sxs-lookup"><span data-stu-id="a5d20-130">WCF also has <xref:System.ServiceModel.ServiceHostBase> and <xref:System.ServiceModel.Activation.ServiceHostFactoryBase>, from which <xref:System.ServiceModel.ServiceHost> and <xref:System.ServiceModel.Activation.ServiceHostFactory> respectively derive.</span></span> <span data-ttu-id="a5d20-131">Ty existují pro pokročilejší scénáře, kdy je nutné odpínat velké části systému metadat vlastními přizpůsobenými vytvářeními.</span><span class="sxs-lookup"><span data-stu-id="a5d20-131">Those exist for more advanced scenarios where you must swap out large parts of the metadata system with your own customized creations.</span></span>
