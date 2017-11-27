---
title: "Trvanlivý kontext instance"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 97bc2994-5a2c-47c7-927a-c4cd273153df
caps.latest.revision: "12"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 540f6b6fe7795eb958afd84695865fd2e4271175
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="durable-instance-context"></a><span data-ttu-id="10660-102">Trvanlivý kontext instance</span><span class="sxs-lookup"><span data-stu-id="10660-102">Durable Instance Context</span></span>
<span data-ttu-id="10660-103">Tento příklad ukazuje, jak přizpůsobit [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] runtime umožňující kontexty trvanlivý instance.</span><span class="sxs-lookup"><span data-stu-id="10660-103">This sample demonstrates how to customize the [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] runtime to enable durable instance contexts.</span></span> <span data-ttu-id="10660-104">SQL Server 2005 používá jako své úložiště zálohování (SQL Server 2005 Express v tomto případě).</span><span class="sxs-lookup"><span data-stu-id="10660-104">It uses SQL Server 2005 as its backing store (SQL Server 2005 Express in this case).</span></span> <span data-ttu-id="10660-105">Však také poskytuje přístup k vlastní úložiště mechanismy.</span><span class="sxs-lookup"><span data-stu-id="10660-105">However, it also provides a way to access custom storage mechanisms.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="10660-106">V postupu a sestavení pokynech k instalaci této ukázce jsou umístěné na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="10660-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="10660-107">Tato ukázka zahrnuje rozšíření vrstvy kanálu a vrstva modelu služby z [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="10660-107">This sample involves extending both the channel layer and the service model layer of the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span> <span data-ttu-id="10660-108">Proto je potřeba pochopit základní koncepty před přechodem do podrobnosti implementace.</span><span class="sxs-lookup"><span data-stu-id="10660-108">Therefore it is necessary to understand the underlying concepts before going into the implementation details.</span></span>  
  
 <span data-ttu-id="10660-109">Trvanlivý instance kontexty naleznete ve skutečných scénářích velmi často.</span><span class="sxs-lookup"><span data-stu-id="10660-109">Durable instance contexts can be found in the real world scenarios quite often.</span></span> <span data-ttu-id="10660-110">Aplikaci nákupního košíku například má možnost pozastavit shopping polovině vzdálenosti prostřednictvím a pokračovat na další den.</span><span class="sxs-lookup"><span data-stu-id="10660-110">A shopping cart application for example, has the ability to pause shopping halfway through and continue it on another day.</span></span> <span data-ttu-id="10660-111">Takže když jsme navštěvovat nákupní košík následujícího dne, je obnoven naše původní kontextu.</span><span class="sxs-lookup"><span data-stu-id="10660-111">So that when we visit the shopping cart the next day, our original context is restored.</span></span> <span data-ttu-id="10660-112">Je důležité si uvědomit, nákupní košík aplikace (na serveru) při jsme jsou odpojené nespravuje nákupní košík instance.</span><span class="sxs-lookup"><span data-stu-id="10660-112">It is important to note that the shopping cart application (on the server) does not maintain the shopping cart instance while we are disconnected.</span></span> <span data-ttu-id="10660-113">Místo toho potrvají stavu do média odolná úložiště a použije při vytváření nové instance pro obnovené kontext.</span><span class="sxs-lookup"><span data-stu-id="10660-113">Instead, it persists its state into a durable storage media and uses it when constructing a new instance for the restored context.</span></span> <span data-ttu-id="10660-114">Instance služby, která může obsluhovat stejný kontextu není stejný jako předchozí instanci (to znamená, nemá stejnou adresu paměti).</span><span class="sxs-lookup"><span data-stu-id="10660-114">Therefore the service instance that may service for the same context is not the same as the previous instance (that is, it does not have the same memory address).</span></span>  
  
 <span data-ttu-id="10660-115">Trvanlivý kontext instance je možné díky malé protokol, který výměny ID kontextu mezi klientem a službou.</span><span class="sxs-lookup"><span data-stu-id="10660-115">Durable instance context is made possible by a small protocol that exchanges a context ID between the client and service.</span></span> <span data-ttu-id="10660-116">Toto ID kontextu je vytvořen v klientovi a odesílané informace ke službě.</span><span class="sxs-lookup"><span data-stu-id="10660-116">This context ID is created on the client and transmitted to the service.</span></span> <span data-ttu-id="10660-117">Při vytvoření instance služby je běh služby se pokusí načíst trvalého stavu, která odpovídá toto ID kontextu z trvalého úložiště (ve výchozím nastavení je databáze systému SQL Server 2005).</span><span class="sxs-lookup"><span data-stu-id="10660-117">When the service instance is created, the service runtime tries to load the persisted state that corresponds to this context ID from a persistent storage (by default it is a SQL Server 2005 database).</span></span> <span data-ttu-id="10660-118">Pokud je k dispozici žádný stav má novou instanci výchozího stavu.</span><span class="sxs-lookup"><span data-stu-id="10660-118">If no state is available the new instance has its default state.</span></span> <span data-ttu-id="10660-119">Implementace služby používá k označení operace, které změní stav implementace služby tak, aby modul runtime můžete uložit instanci služby po vyvolání je vlastní atribut.</span><span class="sxs-lookup"><span data-stu-id="10660-119">The service implementation uses a custom attribute to mark operations that change the state of the service implementation so that the runtime can save the service instance after invoking them.</span></span>  
  
 <span data-ttu-id="10660-120">Podle předchozích popis může být snadno odlišena dva kroky k dosažení cíle:</span><span class="sxs-lookup"><span data-stu-id="10660-120">By the previous description, two steps can easily be distinguished to achieve the goal:</span></span>  
  
1.  <span data-ttu-id="10660-121">Změnit zprávu, která přejde na sítě pro přenos ID kontextu.</span><span class="sxs-lookup"><span data-stu-id="10660-121">Change the message that goes on the wire to carry the context ID.</span></span>  
  
2.  <span data-ttu-id="10660-122">Změňte chování místní služby k implementaci vlastní logiky zřizování instancí.</span><span class="sxs-lookup"><span data-stu-id="10660-122">Change the service local behavior to implement custom instancing logic.</span></span>  
  
 <span data-ttu-id="10660-123">Vzhledem k tomu, že první z nich v seznamu ovlivňuje zprávy v drátové síti by měla být implementována jako vlastní kanál a být připojených k vrstvy kanálu.</span><span class="sxs-lookup"><span data-stu-id="10660-123">Because the first one in the list affects the messages on the wire it should be implemented as a custom channel and be hooked up to the channel layer.</span></span> <span data-ttu-id="10660-124">Druhá možnost se týká pouze místní chování služby a proto může být implementováno tím, že rozšíří několik bodů rozšiřitelnosti služby.</span><span class="sxs-lookup"><span data-stu-id="10660-124">The latter only affects the service local behavior and therefore can be implemented by extending several service extensibility points.</span></span> <span data-ttu-id="10660-125">V následujících částech několik každý z těchto rozšíření jsou popsané.</span><span class="sxs-lookup"><span data-stu-id="10660-125">In the next few sections, each of these extensions are discussed.</span></span>  
  
## <a name="durable-instancecontext-channel"></a><span data-ttu-id="10660-126">Trvale InstanceContext kanálu</span><span class="sxs-lookup"><span data-stu-id="10660-126">Durable InstanceContext Channel</span></span>  
 <span data-ttu-id="10660-127">Nejprve si prohlédněte si je rozšíření vrstvy kanálu.</span><span class="sxs-lookup"><span data-stu-id="10660-127">The first thing to look at is a channel layer extension.</span></span> <span data-ttu-id="10660-128">Prvním krokem při psaní vlastní kanál, který se má rozhodnout strukturu komunikační kanál.</span><span class="sxs-lookup"><span data-stu-id="10660-128">The first step in writing a custom channel is to decide the communication structure of the channel.</span></span> <span data-ttu-id="10660-129">Jako nový protokol přenosu je uvedena kanál by měla spolupracovat s téměř jakoukoli kanál v zásobníku kanálu.</span><span class="sxs-lookup"><span data-stu-id="10660-129">As a new wire protocol is being introduced the channel should work with almost any other channel in the channel stack.</span></span> <span data-ttu-id="10660-130">Proto má podporovat všechny vzorky exchange zprávu.</span><span class="sxs-lookup"><span data-stu-id="10660-130">Therefore it should support all the message exchange patterns.</span></span> <span data-ttu-id="10660-131">Základní funkce služby kanál je však stejný bez ohledu na jeho struktura komunikace.</span><span class="sxs-lookup"><span data-stu-id="10660-131">However, the core functionality of the channel is the same regardless of its communication structure.</span></span> <span data-ttu-id="10660-132">Přesněji řečeno z klienta se zapíše ID kontextu zprávy a ze služby by měl čtení toto ID kontextu ze zprávy a předejte ji do vyšší úrovně.</span><span class="sxs-lookup"><span data-stu-id="10660-132">More specifically, from the client it should write the context ID to the messages and from the service it should read this context ID from the messages and pass it to the upper levels.</span></span> <span data-ttu-id="10660-133">Z tohoto důvodu `DurableInstanceContextChannelBase` vytvořit třídu, která funguje jako abstraktní základní třída pro všechny instance trvanlivý kontext kanál implementace.</span><span class="sxs-lookup"><span data-stu-id="10660-133">Because of that, a `DurableInstanceContextChannelBase` class is created that acts as the abstract base class for all durable instance context channel implementations.</span></span> <span data-ttu-id="10660-134">Tato třída obsahuje běžné funkce správy stavu počítač a dva chráněné členy pro použití a přečtěte si informace o kontextu do a z zprávy.</span><span class="sxs-lookup"><span data-stu-id="10660-134">This class contains the common state machine management functions and two protected members to apply and read the context information to and from messages.</span></span>  
  
```  
class DurableInstanceContextChannelBase  
{  
  //…  
  protected void ApplyContext(Message message)  
  {  
    //…              
  }  
  protected string ReadContextId(Message message)  
  {  
    //…              
  }  
}  
```  
  
 <span data-ttu-id="10660-135">Ujistěte se, tyto dvě metody použití `IContextManager` implementace k zápisu a čtení ID kontextu do nebo ze zprávy.</span><span class="sxs-lookup"><span data-stu-id="10660-135">These two methods make use of `IContextManager` implementations to write and read the context ID to or from the message.</span></span> <span data-ttu-id="10660-136">(`IContextManager` je vlastní rozhraní používá k definování kontraktu pro všechny správce kontextu.) Kanál může obsahovat buď ID kontextu, ve vlastní hlavičky SOAP nebo v hlavičce souboru cookie HTTP.</span><span class="sxs-lookup"><span data-stu-id="10660-136">(`IContextManager` is a custom interface used to define the contract for all context managers.) The channel can either include the context ID in a custom SOAP header or in a HTTP cookie header.</span></span> <span data-ttu-id="10660-137">Každá implementace manager kontextu dědí z `ContextManagerBase` třídu, která obsahuje funkci společné pro všechny správce kontextu.</span><span class="sxs-lookup"><span data-stu-id="10660-137">Each context manager implementation inherits from the `ContextManagerBase` class that contains the common functionality for all context managers.</span></span> <span data-ttu-id="10660-138">`GetContextId` Metoda v tato třída se používá k pocházejí ID kontextu z klienta.</span><span class="sxs-lookup"><span data-stu-id="10660-138">The `GetContextId` method in this class is used to originate the context ID from the client.</span></span> <span data-ttu-id="10660-139">Kontext, ve kterém je ID pochází poprvé, když tato metoda uloží ho do textového souboru, jehož název je vytvořený pomocí adresy vzdálený koncový bod (název souboru je neplatný. znaky v typické identifikátory URI jsou nahrazeny @ znaků).</span><span class="sxs-lookup"><span data-stu-id="10660-139">When a context ID is originated for the first time, this method saves it into a text file whose name is constructed by the remote endpoint address (the invalid file name characters in the typical URIs are replaced with @ characters).</span></span>  
  
 <span data-ttu-id="10660-140">Později je požadováno pro stejné vzdálený koncový bod ID kontextu, zkontroluje, zda existuje příslušný soubor.</span><span class="sxs-lookup"><span data-stu-id="10660-140">Later when the context ID is required for the same remote endpoint, it checks whether an appropriate file exists.</span></span> <span data-ttu-id="10660-141">Pokud ano, přečte ID kontextu a vrátí.</span><span class="sxs-lookup"><span data-stu-id="10660-141">If it does, it reads the context ID and returns.</span></span> <span data-ttu-id="10660-142">V opačném případě vrátí ID nově generovaným kontextem a uloží do souboru.</span><span class="sxs-lookup"><span data-stu-id="10660-142">Otherwise it returns a newly generated context ID and saves it to a file.</span></span> <span data-ttu-id="10660-143">U výchozí konfigurace tyto soubory jsou umístěny v adresář s názvem ContextStore, který se nachází v adresáři temp aktuálního uživatele.</span><span class="sxs-lookup"><span data-stu-id="10660-143">With the default configuration, these files are placed in a directory called ContextStore, which resides in the current user’s temp directory.</span></span> <span data-ttu-id="10660-144">Toto umístění je ale možné konfigurovat pomocí prvku vazby.</span><span class="sxs-lookup"><span data-stu-id="10660-144">However this location is configurable using the binding element.</span></span>  
  
 <span data-ttu-id="10660-145">Tento mechanismus používá k přenosu ID kontextu je možné konfigurovat.</span><span class="sxs-lookup"><span data-stu-id="10660-145">The mechanism used to transport the context ID is configurable.</span></span> <span data-ttu-id="10660-146">Ho může buď zapsat hlavička cookie HTTP nebo vlastní hlavičku protokolu SOAP.</span><span class="sxs-lookup"><span data-stu-id="10660-146">It could be either written to the HTTP cookie header or to a custom SOAP header.</span></span> <span data-ttu-id="10660-147">Vlastní hlavička přístup protokolu SOAP umožňuje tento protokol pomocí jiných protokolů než HTTP (například TCP nebo pojmenované kanály).</span><span class="sxs-lookup"><span data-stu-id="10660-147">The custom SOAP header approach makes it possible to use this protocol with non-HTTP protocols (for example, TCP or Named Pipes).</span></span> <span data-ttu-id="10660-148">Existují dvě třídy, konkrétně `MessageHeaderContextManager` a `HttpCookieContextManager`, který implementovat tyto dvě možnosti.</span><span class="sxs-lookup"><span data-stu-id="10660-148">There are two classes, namely `MessageHeaderContextManager` and `HttpCookieContextManager`, which implement these two options.</span></span>  
  
 <span data-ttu-id="10660-149">Oba dva zapisovat ID kontextu zpráva správně.</span><span class="sxs-lookup"><span data-stu-id="10660-149">Both of them write the context ID to the message appropriately.</span></span> <span data-ttu-id="10660-150">Například `MessageHeaderContextManager` třída zapíše ho do hlavičku protokolu SOAP v `WriteContext` metoda.</span><span class="sxs-lookup"><span data-stu-id="10660-150">For example, the `MessageHeaderContextManager` class writes it to a SOAP header in the `WriteContext` method.</span></span>  
  
```  
public override void WriteContext(Message message)  
{  
  string contextId = this.GetContextId();  
  
  MessageHeader contextHeader =  
    MessageHeader.CreateHeader(DurableInstanceContextUtility.HeaderName,  
      DurableInstanceContextUtility.HeaderNamespace,  
      contextId,   
      true);  
  
  message.Headers.Add(contextHeader);  
}   
```  
  
 <span data-ttu-id="10660-151">Jak `ApplyContext` a `ReadContextId` metody v `DurableInstanceContextChannelBase` vyvolání třídy `IContextManager.ReadContext` a `IContextManager.WriteContext`, v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="10660-151">Both the `ApplyContext` and `ReadContextId` methods in the `DurableInstanceContextChannelBase` class invoke the `IContextManager.ReadContext` and `IContextManager.WriteContext`, respectively.</span></span> <span data-ttu-id="10660-152">Však těmito manažery kontextu nejsou vytvořené přímo `DurableInstanceContextChannelBase` třídy.</span><span class="sxs-lookup"><span data-stu-id="10660-152">However, these context managers are not directly created by the `DurableInstanceContextChannelBase` class.</span></span> <span data-ttu-id="10660-153">Místo toho použije `ContextManagerFactory` třídy provést tuto úlohu.</span><span class="sxs-lookup"><span data-stu-id="10660-153">Instead it uses the `ContextManagerFactory` class to do that job.</span></span>  
  
```  
IContextManager contextManager =  
                ContextManagerFactory.CreateContextManager(contextType,   
                this.contextStoreLocation,   
                this.endpointAddress);  
```  
  
 <span data-ttu-id="10660-154">`ApplyContext` Metoda je volána pomocí odesílání kanály.</span><span class="sxs-lookup"><span data-stu-id="10660-154">The `ApplyContext` method is invoked by the sending channels.</span></span> <span data-ttu-id="10660-155">Se vloží ID kontextu do odesílaných zpráv.</span><span class="sxs-lookup"><span data-stu-id="10660-155">It injects the context ID to the outgoing messages.</span></span> <span data-ttu-id="10660-156">`ReadContextId` Je volána metoda podle přijímající kanály.</span><span class="sxs-lookup"><span data-stu-id="10660-156">The `ReadContextId` method is invoked by the receiving channels.</span></span> <span data-ttu-id="10660-157">Tato metoda zajišťuje, že ID kontextu je k dispozici v příchozí zprávy a přidává ji k `Properties` kolekce `Message` třídy.</span><span class="sxs-lookup"><span data-stu-id="10660-157">This method ensures that the context ID is available in the incoming messages and adds it to the `Properties` collection of the `Message` class.</span></span> <span data-ttu-id="10660-158">Také vyvolá `CommunicationException` v případě selhání čtení ID kontextu a proto způsobí, že kanál přerušena.</span><span class="sxs-lookup"><span data-stu-id="10660-158">It also throws a `CommunicationException` in case of a failure to read the context ID and thus causes the channel to be aborted.</span></span>  
  
```  
message.Properties.Add(DurableInstanceContextUtility.ContextIdProperty, contextId);  
```  
  
 <span data-ttu-id="10660-159">Než budete pokračovat, je důležité si uvědomit, použití `Properties` kolekce v `Message` třídy.</span><span class="sxs-lookup"><span data-stu-id="10660-159">Before proceeding, it is important to understand the usage of the `Properties` collection in the `Message` class.</span></span> <span data-ttu-id="10660-160">Obvykle to `Properties` kolekce se používá při předávání dat z snížit na horní úrovně z vrstvy kanálu.</span><span class="sxs-lookup"><span data-stu-id="10660-160">Typically, this `Properties` collection is used when passing data from lower to the upper levels from the channel layer.</span></span> <span data-ttu-id="10660-161">Tímto způsobem k požadovaným datům lze zadat do vyšší úrovně konzistentním způsobem bez ohledu na podrobnosti protokolu.</span><span class="sxs-lookup"><span data-stu-id="10660-161">This way the desired data can be provided to the upper levels in a consistent manner regardless of the protocol details.</span></span> <span data-ttu-id="10660-162">Jinými slovy vrstvy kanálu můžete odesílat a přijímat ID kontextu buď jako hlavičku protokolu SOAP nebo soubor cookie hlavičku protokolu HTTP.</span><span class="sxs-lookup"><span data-stu-id="10660-162">In other words, the channel layer can send and receive the context ID either as a SOAP header or a HTTP cookie header.</span></span> <span data-ttu-id="10660-163">Není nutné pro vyšší úrovně vědět o tyto podrobnosti, protože vrstvy kanálu zpřístupní tyto informace v, ale `Properties` kolekce.</span><span class="sxs-lookup"><span data-stu-id="10660-163">But it is not necessary for the upper levels to know about these details because the channel layer makes this information available in the `Properties` collection.</span></span>  
  
 <span data-ttu-id="10660-164">Teď se `DurableInstanceContextChannelBase` třídy zavedené všechny deset rozhraní potřebná (IOutputChannel IInputChannel, IOutputSessionChannel, IInputSessionChannel, třídu IRequestChannel, IReplyChannel, IRequestSessionChannel, IReplySessionChannel, Musí být implementované IDuplexChannel, IDuplexSessionChannel).</span><span class="sxs-lookup"><span data-stu-id="10660-164">Now with the `DurableInstanceContextChannelBase` class in place all ten of the necessary interfaces (IOutputChannel, IInputChannel, IOutputSessionChannel, IInputSessionChannel, IRequestChannel, IReplyChannel, IRequestSessionChannel, IReplySessionChannel, IDuplexChannel, IDuplexSessionChannel) must be implemented.</span></span> <span data-ttu-id="10660-165">Se podobají každých vzorce výměny zpráv k dispozici (datagram, simplex, duplexní režim a jejich relacemi varianty).</span><span class="sxs-lookup"><span data-stu-id="10660-165">They resemble every available message exchange pattern (datagram, simplex, duplex and their sessionful variants).</span></span> <span data-ttu-id="10660-166">Každý z těchto implementace dědění základní třída popsaných výše a volání `ApplyContext` a `ReadContexId` správně.</span><span class="sxs-lookup"><span data-stu-id="10660-166">Each of these implementations inherit the base class previously described and calls `ApplyContext` and `ReadContexId` appropriately.</span></span> <span data-ttu-id="10660-167">Například `DurableInstanceContextOutputChannel` - který implementuje rozhraní IOutputChannel - volá `ApplyContext` metoda z každé metody, která odesílá zprávy.</span><span class="sxs-lookup"><span data-stu-id="10660-167">For example, `DurableInstanceContextOutputChannel` - which implements the IOutputChannel interface - calls the `ApplyContext` method from each method that sends the messages.</span></span>  
  
```  
public void Send(Message message, TimeSpan timeout)  
{  
    // Apply the context information before sending the message.  
    this.ApplyContext(message);  
    //…  
}   
```  
  
 <span data-ttu-id="10660-168">Na druhé straně `DurableInstanceContextInputChannel` – které implementuje `IInputChannel` rozhraní - volání `ReadContextId` metoda dané metody, která přijímá zprávy.</span><span class="sxs-lookup"><span data-stu-id="10660-168">On the other hand, `DurableInstanceContextInputChannel` - which implements the `IInputChannel` interface - calls the `ReadContextId` method in each method which receives the messages.</span></span>  
  
```  
public Message Receive(TimeSpan timeout)  
{  
    //…  
      ReadContextId(message);  
      return message;  
}  
```  
  
 <span data-ttu-id="10660-169">Kromě toho tyto implementace kanál delegovat volání metod kanálu uvedenou pod nimi v zásobníku kanálu.</span><span class="sxs-lookup"><span data-stu-id="10660-169">Apart from this, these channel implementations delegate the method invocations to the channel below them in the channel stack.</span></span> <span data-ttu-id="10660-170">Relacemi variant však mít základní logika a ujistěte se, že ID kontextu je odeslán a se čtou jenom pro první zprávu, která způsobí, že relace, který se má vytvořit.</span><span class="sxs-lookup"><span data-stu-id="10660-170">However, sessionful variants have a basic logic to make sure that the context ID is sent and is read only for the first message that causes the session to be created.</span></span>  
  
```  
if (isFirstMessage)  
{  
//…  
    this.ApplyContext(message);  
    isFirstMessage = false;  
}  
```  
  
 <span data-ttu-id="10660-171">Tyto implementace kanál se pak přidají do [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] runtime kanál pomocí `DurableInstanceContextBindingElement` třídy a `DurableInstanceContextBindingElementSection` třídy správně.</span><span class="sxs-lookup"><span data-stu-id="10660-171">These channel implementations are then added to the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] channel runtime by the `DurableInstanceContextBindingElement` class and `DurableInstanceContextBindingElementSection` class appropriately.</span></span> <span data-ttu-id="10660-172">Najdete v článku [HttpCookieSession](../../../../docs/framework/wcf/samples/httpcookiesession.md) kanálu ukázková dokumentace pro další podrobnosti o elementů vazby a vazby element oddíly.</span><span class="sxs-lookup"><span data-stu-id="10660-172">See the [HttpCookieSession](../../../../docs/framework/wcf/samples/httpcookiesession.md) channel sample documentation for more details about binding elements and binding element sections.</span></span>  
  
## <a name="service-model-layer-extensions"></a><span data-ttu-id="10660-173">Rozšíření vrstvy modelu služby</span><span class="sxs-lookup"><span data-stu-id="10660-173">Service Model Layer Extensions</span></span>  
 <span data-ttu-id="10660-174">Teď, když má ID kontextu cesty prostřednictvím vrstvy kanálu, můžete k přizpůsobení instance implementovat chování služby.</span><span class="sxs-lookup"><span data-stu-id="10660-174">Now that the context ID has traveled through the channel layer, the service behavior can be implemented to customize the instantiation.</span></span> <span data-ttu-id="10660-175">V této ukázce Správce úložiště slouží k načtení a uložení stavu z nebo do trvalého úložiště.</span><span class="sxs-lookup"><span data-stu-id="10660-175">In this sample, a storage manager is used to load and save state from or to the persistent store.</span></span> <span data-ttu-id="10660-176">Jak je popsáno dříve, tato ukázka poskytuje správce úložiště, který používá systém SQL Server 2005 jako své úložiště zálohování.</span><span class="sxs-lookup"><span data-stu-id="10660-176">As explained previously, this sample provides a storage manager that uses SQL Server 2005 as its backing store.</span></span> <span data-ttu-id="10660-177">Je však také možné přidat vlastní úložiště mechanismy pro tuto příponu.</span><span class="sxs-lookup"><span data-stu-id="10660-177">However, it is also possible to add custom storage mechanisms to this extension.</span></span> <span data-ttu-id="10660-178">K tomu veřejné rozhraní je deklarovaná, který musí implementovat všechny správce úložiště.</span><span class="sxs-lookup"><span data-stu-id="10660-178">To do that a public interface is declared, which must be implemented by all storage managers.</span></span>  
  
```  
public interface IStorageManager  
{  
    object GetInstance(string contextId, Type type);  
    void SaveInstance(string contextId, object state);  
}  
```  
  
 <span data-ttu-id="10660-179">`SqlServerStorageManager` Třída obsahuje výchozí `IStorageManager` implementace.</span><span class="sxs-lookup"><span data-stu-id="10660-179">The `SqlServerStorageManager` class contains the default `IStorageManager` implementation.</span></span> <span data-ttu-id="10660-180">V jeho `SaveInstance` metoda daný objekt serializován pomocí třídy XmlSerializer a je uložen do databáze SQL serveru.</span><span class="sxs-lookup"><span data-stu-id="10660-180">In its `SaveInstance` method the given object is serialized using the XmlSerializer and is saved to the SQL Server database.</span></span>  
  
```  
XmlSerializer serializer = new XmlSerializer(state.GetType());  
string data;  
  
using (StringWriter writer = new StringWriter(CultureInfo.InvariantCulture))  
{  
    serializer.Serialize(writer, state);  
    data = writer.ToString();  
}  
  
using (SqlConnection connection = new SqlConnection(GetConnectionString()))  
{  
    connection.Open();  
  
    string update = @"UPDATE Instances SET Instance = @instance WHERE ContextId = @contextId";  
  
    using (SqlCommand command = new SqlCommand(update, connection))  
    {  
        command.Parameters.Add("@instance", SqlDbType.VarChar, 2147483647).Value = data;  
        command.Parameters.Add("@contextId", SqlDbType.VarChar, 256).Value = contextId;  
  
        int rows = command.ExecuteNonQuery();  
  
        if (rows == 0)  
        {  
            string insert = @"INSERT INTO Instances(ContextId, Instance) VALUES(@contextId, @instance)";  
            command.CommandText = insert;  
            command.ExecuteNonQuery();  
        }  
    }  
}  
```  
  
 <span data-ttu-id="10660-181">V `GetInstance` metoda serializovaná data je pro čtení pro daný kontext ID a je objekt vytvořený z něj vrácen volajícímu.</span><span class="sxs-lookup"><span data-stu-id="10660-181">In the `GetInstance` method the serialized data is read for a given context ID and the object constructed from it is returned to the caller.</span></span>  
  
```  
object data;  
using (SqlConnection connection = new SqlConnection(GetConnectionString()))  
{  
    connection.Open();  
  
    string select = "SELECT Instance FROM Instances WHERE ContextId = @contextId";  
    using (SqlCommand command = new SqlCommand(select, connection))  
    {  
        command.Parameters.Add("@contextId", SqlDbType.VarChar, 256).Value = contextId;  
        data = command.ExecuteScalar();  
    }  
}  
  
if (data != null)  
{  
    XmlSerializer serializer = new XmlSerializer(type);  
    using (StringReader reader = new StringReader((string)data))  
    {  
        object instance = serializer.Deserialize(reader);  
        return instance;  
    }  
}  
```  
  
 <span data-ttu-id="10660-182">Uživatelé těchto úložiště správci nemají co dělat vytvořit přímo instanci.</span><span class="sxs-lookup"><span data-stu-id="10660-182">Users of these storage managers are not supposed to instantiate them directly.</span></span> <span data-ttu-id="10660-183">Používají `StorageManagerFactory` třída, která abstrahuje z podrobnosti vytváření Správce úložiště.</span><span class="sxs-lookup"><span data-stu-id="10660-183">They use the `StorageManagerFactory` class, which abstracts from the storage manager creation details.</span></span> <span data-ttu-id="10660-184">Tato třída obsahuje jeden statický člen `GetStorageManager`, která vytvoří instanci typu manager dané úložiště.</span><span class="sxs-lookup"><span data-stu-id="10660-184">This class has one static member, `GetStorageManager`, which creates an instance of a given storage manager type.</span></span> <span data-ttu-id="10660-185">Pokud je parametr typu `null`, tato metoda vytvoří instanci výchozí `SqlServerStorageManager` třídy a vrátí ji.</span><span class="sxs-lookup"><span data-stu-id="10660-185">If the type parameter is `null`, this method creates an instance of the default `SqlServerStorageManager` class and returns it.</span></span> <span data-ttu-id="10660-186">Zároveň ověří, abyste měli jistotu, že implementuje daného typu `IStorageManager` rozhraní.</span><span class="sxs-lookup"><span data-stu-id="10660-186">It also validates the given type to make sure that it implements the `IStorageManager` interface.</span></span>  
  
```  
public static IStorageManager GetStorageManager(Type storageManagerType)  
{  
IStorageManager storageManager = null;  
  
if (storageManagerType == null)  
{  
    return new SqlServerStorageManager();  
}  
else  
{  
    object obj = Activator.CreateInstance(storageManagerType);  
  
    // Throw if the specified storage manager type does not  
    // implement IStorageManager.  
    if (obj is IStorageManager)  
    {  
        storageManager = (IStorageManager)obj;  
    }  
    else  
    {  
        throw new InvalidOperationException(  
                  ResourceHelper.GetString("ExInvalidStorageManager"));  
    }  
  
    return storageManager;  
}                  
}   
```  
  
 <span data-ttu-id="10660-187">Potřebnou infrastrukturu pro čtení a zápisu instancí z trvalého úložiště je implementováno.</span><span class="sxs-lookup"><span data-stu-id="10660-187">The necessary infrastructure to read and write instances from the persistent storage is implemented.</span></span> <span data-ttu-id="10660-188">Nyní musí vzít potřebné kroky, chcete-li změnit chování služby.</span><span class="sxs-lookup"><span data-stu-id="10660-188">Now the necessary steps to change the service behavior have to be taken.</span></span>  
  
 <span data-ttu-id="10660-189">Jako první krok tohoto procesu se musí uložit ID kontextu, které pochází z vrstvy kanálu pro aktuální objekt InstanceContext.</span><span class="sxs-lookup"><span data-stu-id="10660-189">As the first step of this process we have to save the context ID, which came through the channel layer to the current InstanceContext.</span></span> <span data-ttu-id="10660-190">Parametr InstanceContext je součástí modulu runtime, která slouží jako propojení mezi [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] dispečera a instance služby.</span><span class="sxs-lookup"><span data-stu-id="10660-190">InstanceContext is a runtime component that acts as the link between the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] dispatcher and the service instance.</span></span> <span data-ttu-id="10660-191">Slouží k poskytování dalších stavu a chování v instanci služby.</span><span class="sxs-lookup"><span data-stu-id="10660-191">It can be used to provide additional state and behavior to the service instance.</span></span> <span data-ttu-id="10660-192">To je důležité, protože komunikaci mezi relacemi ID kontextu jsou odeslány pouze s první zprávu.</span><span class="sxs-lookup"><span data-stu-id="10660-192">This is essential because in sessionful communication the context ID is sent only with the first message.</span></span>  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="10660-193">umožňuje rozšíření jeho komponenty runtime InstanceContext přidáním nového stavu a chování pomocí jeho vzor extensible objektu.</span><span class="sxs-lookup"><span data-stu-id="10660-193"> allows extending its InstanceContext runtime component by adding a new state and behavior using its extensible object pattern.</span></span> <span data-ttu-id="10660-194">Vzor extensible objektu se používá v [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] buď rozšířit existující třídy runtime s novými funkcemi, nebo při přidání nových funkcí stavu do objektu.</span><span class="sxs-lookup"><span data-stu-id="10660-194">The extensible object pattern is used in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] to either extend existing runtime classes with new functionality or to add new state features to an object.</span></span> <span data-ttu-id="10660-195">Existují tři rozhraní ve vzoru extensible objekt - IExtensibleObject\<T >, IExtension\<T > a IExtensionCollection\<T >:</span><span class="sxs-lookup"><span data-stu-id="10660-195">There are three interfaces in the extensible object pattern - IExtensibleObject\<T>, IExtension\<T>, and IExtensionCollection\<T>:</span></span>  
  
-   <span data-ttu-id="10660-196">IExtensibleObject\<T > rozhraní je implementováno modulem objekty, které umožňují rozšíření, které přizpůsobit jejich funkce.</span><span class="sxs-lookup"><span data-stu-id="10660-196">The IExtensibleObject\<T> interface is implemented by objects that allow extensions that customize their functionality.</span></span>  
  
-   <span data-ttu-id="10660-197">IExtension\<T > rozhraní je implementováno modulem objekty, které jsou rozšíření třídy typu T.</span><span class="sxs-lookup"><span data-stu-id="10660-197">The IExtension\<T> interface is implemented by objects that are extensions of classes of type T.</span></span>  
  
-   <span data-ttu-id="10660-198">IExtensionCollection\<T > rozhraní je kolekce IExtensions, která umožňuje načítání IExtensions dle jejich typu.</span><span class="sxs-lookup"><span data-stu-id="10660-198">The IExtensionCollection\<T> interface is a collection of IExtensions that allows for retrieving IExtensions by their type.</span></span>  
  
 <span data-ttu-id="10660-199">Proto třídu InstanceContextExtension by měl být vytvořen, který implementuje rozhraní IExtension a definuje stav vyžaduje pro uložení ID kontextu.</span><span class="sxs-lookup"><span data-stu-id="10660-199">Therefore an InstanceContextExtension class should be created that implements the IExtension interface and defines the required state to save the context ID.</span></span> <span data-ttu-id="10660-200">Tato třída rovněž poskytuje stav pro uložení úložiště správce používá.</span><span class="sxs-lookup"><span data-stu-id="10660-200">This class also provides the state to hold the storage manager being used.</span></span> <span data-ttu-id="10660-201">Po uložení nového stavu, neměl by být možné ji upravit.</span><span class="sxs-lookup"><span data-stu-id="10660-201">Once the new state is saved, it should not be possible to modify it.</span></span> <span data-ttu-id="10660-202">Stav jsou proto zadat a uložit do instance v době, kdy se vytvořený a potom dostupné jenom pomocí vlastnosti jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="10660-202">Therefore the state is provided and saved to the instance at the time it is being constructed and then only accessible using read-only properties.</span></span>  
  
```  
// Constructor  
public DurableInstanceContextExtension(string contextId,   
            IStorageManager storageManager)  
{  
    this.contextId = contextId;  
    this.storageManager = storageManager;              
}  
  
// Read only properties  
public string ContextId  
{  
    get { return this.contextId; }  
}  
  
public IStorageManager StorageManager  
{  
    get { return this.storageManager; }              
}   
```  
  
 <span data-ttu-id="10660-203">Třída InstanceContextInitializer implementuje rozhraní IInstanceContextInitializer a přidá do kolekce rozšíření InstanceContext vytvářen rozšíření místní instance.</span><span class="sxs-lookup"><span data-stu-id="10660-203">The InstanceContextInitializer class implements the IInstanceContextInitializer interface and adds the instance context extension to the Extensions collection of the InstanceContext being constructed.</span></span>  
  
```  
public void Initialize(InstanceContext instanceContext, Message message)  
{  
    string contextId =   
  (string)message.Properties[DurableInstanceContextUtility.ContextIdProperty];  
  
    DurableInstanceContextExtension extension =  
                new DurableInstanceContextExtension(contextId,   
                     storageManager);  
    instanceContext.Extensions.Add(extension);  
}  
```  
  
 <span data-ttu-id="10660-204">Jak bylo popsáno dříve ID kontextu je pro čtení z `Properties` kolekce `Message` třídy a předaný konstruktoru třídy extension.</span><span class="sxs-lookup"><span data-stu-id="10660-204">As described earlier the context ID is read from the `Properties` collection of the `Message` class and passed to the constructor of the extension class.</span></span> <span data-ttu-id="10660-205">Tento příklad ukazuje, jak nelze vyměňovat informace mezi vrstvami konzistentním způsobem.</span><span class="sxs-lookup"><span data-stu-id="10660-205">This demonstrates how information can be exchanged between the layers in a consistent manner.</span></span>  
  
 <span data-ttu-id="10660-206">Další důležitý krok přepisují proces vytvoření instance služby.</span><span class="sxs-lookup"><span data-stu-id="10660-206">The next important step is overriding the service instance creation process.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="10660-207">Umožňuje implementace chování vlastní vytváření instancí a jejich zapojování až modulu runtime použijte rozhraní IInstanceProvider.</span><span class="sxs-lookup"><span data-stu-id="10660-207"> allows implementing custom instantiation behaviors and hooking them up to the runtime using the IInstanceProvider interface.</span></span> <span data-ttu-id="10660-208">Nové `InstanceProvider` implementaci třídy chcete tuto úlohu.</span><span class="sxs-lookup"><span data-stu-id="10660-208">The new `InstanceProvider` class is implemented to do that job.</span></span> <span data-ttu-id="10660-209">V konstruktoru byla přijata od instance zprostředkovatele je očekáván typ služby.</span><span class="sxs-lookup"><span data-stu-id="10660-209">In the constructor the service type expected from the instance provider is accepted.</span></span> <span data-ttu-id="10660-210">To se později používá k vytvoření nové instance.</span><span class="sxs-lookup"><span data-stu-id="10660-210">Later this is used to create new instances.</span></span> <span data-ttu-id="10660-211">V `GetInstance` implementace instance Správce úložiště je vytvořena hledá trvalou instance.</span><span class="sxs-lookup"><span data-stu-id="10660-211">In the `GetInstance` implementation an instance of a storage manager is created looking for a persisted instance.</span></span> <span data-ttu-id="10660-212">Vrátí-li `null` pak novou instanci typu služby vytvořena a vrácena volajícímu.</span><span class="sxs-lookup"><span data-stu-id="10660-212">If it returns `null` then a new instance of the service type is instantiated and returned to the caller.</span></span>  
  
```  
public object GetInstance(InstanceContext instanceContext, Message message)  
{  
    object instance = null;  
  
    DurableInstanceContextExtension extension =  
    instanceContext.Extensions.Find<DurableInstanceContextExtension>();  
  
    string contextId = extension.ContextId;  
    IStorageManager storageManager = extension.StorageManager;              
  
    instance = storageManager.GetInstance(contextId, serviceType);          
  
    if (instance == null)  
    {  
        instance = Activator.CreateInstance(serviceType);  
    }  
  
    return instance;  
}  
```  
  
 <span data-ttu-id="10660-213">Dalším důležitým krokem je instalace `InstanceContextExtension`, `InstanceContextInitializer` a `InstanceProvider` tříd do modulu runtime modelu služby.</span><span class="sxs-lookup"><span data-stu-id="10660-213">The next important step is to install the `InstanceContextExtension`, `InstanceContextInitializer` and `InstanceProvider` classes into the service model runtime.</span></span> <span data-ttu-id="10660-214">Vlastní atribut může označit implementace třídy služeb pro instalaci chování.</span><span class="sxs-lookup"><span data-stu-id="10660-214">A custom attribute could be used to mark the service implementation classes to install the behavior.</span></span> <span data-ttu-id="10660-215">`DurableInstanceContextAttribute` Obsahuje implementaci pro tento atribut a implementuje `IServiceBehavior` rozhraní rozšíření modulu runtime celé služby.</span><span class="sxs-lookup"><span data-stu-id="10660-215">The `DurableInstanceContextAttribute` contains the implementation for this attribute and it implements the `IServiceBehavior` interface to extend the entire service runtime.</span></span>  
  
 <span data-ttu-id="10660-216">Tato třída obsahuje vlastnosti, která přijímá typ Správce úložiště, který se má použít.</span><span class="sxs-lookup"><span data-stu-id="10660-216">This class has a property that accepts the type of the storage manager to be used.</span></span> <span data-ttu-id="10660-217">Tímto způsobem implementace umožňuje uživatelům zadat vlastní `IStorageManager` implementace jako parametr tohoto atributu.</span><span class="sxs-lookup"><span data-stu-id="10660-217">In this way the implementation enables the users to specify their own `IStorageManager` implementation as parameter of this attribute.</span></span>  
  
 <span data-ttu-id="10660-218">V `ApplyDispatchBehavior` implementace `InstanceContextMode` aktuálního `ServiceBehavior` atribut ověření.</span><span class="sxs-lookup"><span data-stu-id="10660-218">In the `ApplyDispatchBehavior` implementation the `InstanceContextMode` of the current `ServiceBehavior` attribute is being verified.</span></span> <span data-ttu-id="10660-219">Pokud je nastavena na Singleton, povolení trvanlivý vytváření instancí není možné a `InvalidOperationException` je vyvolána oznámit hostitele.</span><span class="sxs-lookup"><span data-stu-id="10660-219">If this property is set to Singleton, enabling durable instancing is not possible and an `InvalidOperationException` is thrown to notify the host.</span></span>  
  
```  
ServiceBehaviorAttribute serviceBehavior =  
    serviceDescription.Behaviors.Find<ServiceBehaviorAttribute>();  
  
if (serviceBehavior != null &&  
     serviceBehavior.InstanceContextMode == InstanceContextMode.Single)  
{  
    throw new InvalidOperationException(  
       ResourceHelper.GetString("ExSingeltonInstancingNotSupported"));  
}  
```  
  
 <span data-ttu-id="10660-220">Po této instance Správce úložiště, instance kontextu inicializátoru a poskytovateli instance se vytváří a nainstalované v `DispatchRuntime` vytvořit pro každý koncový bod.</span><span class="sxs-lookup"><span data-stu-id="10660-220">After this the instances of the storage manager, instance context initializer, and the instance provider are created and installed in the `DispatchRuntime` created for every endpoint.</span></span>  
  
```  
IStorageManager storageManager =   
    StorageManagerFactory.GetStorageManager(storageManagerType);  
  
InstanceContextInitializer contextInitializer =  
    new InstanceContextInitializer(storageManager);  
  
InstanceProvider instanceProvider =  
    new InstanceProvider(description.ServiceType);  
  
foreach (ChannelDispatcherBase cdb in serviceHostBase.ChannelDispatchers)  
{  
    ChannelDispatcher cd = cdb as ChannelDispatcher;  
  
    if (cd != null)  
    {  
        foreach (EndpointDispatcher ed in cd.Endpoints)  
        {  
            ed.DispatchRuntime.InstanceContextInitializers.Add(contextInitializer);  
            ed.DispatchRuntime.InstanceProvider = instanceProvider;  
        }  
    }  
}  
```  
  
 <span data-ttu-id="10660-221">V souhrnu, pokud tato ukázka má vytvořeného kanálu, který je povolený protokol vlastní přenosu pro kontext vlastní ID exchange a taky přepíše výchozí chování instance načíst z trvalého úložiště vytváření instancí.</span><span class="sxs-lookup"><span data-stu-id="10660-221">In summary so far, this sample has produced a channel that enabled the custom wire protocol for custom context ID exchange and it also overwrites the default instancing behavior to load the instances from the persistent storage.</span></span>  
  
 <span data-ttu-id="10660-222">Co je ponechán je způsob, jak uložit instanci služby do trvalého úložiště.</span><span class="sxs-lookup"><span data-stu-id="10660-222">What is left is a way to save the service instance to the persistent storage.</span></span> <span data-ttu-id="10660-223">Jak je popsáno dříve, již existuje požadované funkce pro uložení stavu v `IStorageManager` implementace.</span><span class="sxs-lookup"><span data-stu-id="10660-223">As discussed previously, there is already the required functionality to save the state in an `IStorageManager` implementation.</span></span> <span data-ttu-id="10660-224">Jsme teď musíte integrovat o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="10660-224">We now must integrate this with the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] runtime.</span></span> <span data-ttu-id="10660-225">Jiný atribut je požadován, se vztahuje na metody ve třídě implementace služby.</span><span class="sxs-lookup"><span data-stu-id="10660-225">Another attribute is required that is applicable to the methods in the service implementation class.</span></span> <span data-ttu-id="10660-226">Tento atribut by měl použít pro metody, které změní stav instance služby.</span><span class="sxs-lookup"><span data-stu-id="10660-226">This attribute is supposed to be applied to the methods that change the state of the service instance.</span></span>  
  
 <span data-ttu-id="10660-227">`SaveStateAttribute` Třída implementuje tuto funkci.</span><span class="sxs-lookup"><span data-stu-id="10660-227">The `SaveStateAttribute` class implements this functionality.</span></span> <span data-ttu-id="10660-228">Také implementuje `IOperationBehavior` třída změnit [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] modul runtime pro každou operaci.</span><span class="sxs-lookup"><span data-stu-id="10660-228">It also implements `IOperationBehavior` class to modify the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] runtime for each operation.</span></span> <span data-ttu-id="10660-229">Když metoda je označena k tomuto atributu [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] vyvolá runtime `ApplyBehavior` metoda při odpovídající `DispatchOperation` je vytvářen.</span><span class="sxs-lookup"><span data-stu-id="10660-229">When a method is marked with this attribute, the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] runtime invokes the `ApplyBehavior` method while the appropriate `DispatchOperation` is being constructed.</span></span> <span data-ttu-id="10660-230">V této implementaci metoda je jediný řádek kódu:</span><span class="sxs-lookup"><span data-stu-id="10660-230">In this method implementation there is single line of code:</span></span>  
  
```  
dispatch.Invoker = new OperationInvoker(dispatch.Invoker);  
```  
  
 <span data-ttu-id="10660-231">Tento pokyn vytvoří instanci `OperationInvoker` zadejte a přiřadí ji k `Invoker` vlastnost `DispatchOperation` vytvářen.</span><span class="sxs-lookup"><span data-stu-id="10660-231">This instruction creates an instance of `OperationInvoker` type and assigns it to the `Invoker` property of the `DispatchOperation` being constructed.</span></span> <span data-ttu-id="10660-232">`OperationInvoker` Třída je obálka pro původce volání operace výchozí pro vytvořit `DispatchOperation`.</span><span class="sxs-lookup"><span data-stu-id="10660-232">The `OperationInvoker` class is a wrapper for the default operation invoker created for the `DispatchOperation`.</span></span> <span data-ttu-id="10660-233">Tato třída implementuje `IOperationInvoker` rozhraní.</span><span class="sxs-lookup"><span data-stu-id="10660-233">This class implements the `IOperationInvoker` interface.</span></span> <span data-ttu-id="10660-234">V `Invoke` implementace metod volání metody skutečné je delegovaný jako původce vnitřní operace.</span><span class="sxs-lookup"><span data-stu-id="10660-234">In the `Invoke` method implementation the actual method invocation is delegated to the inner operation invoker.</span></span> <span data-ttu-id="10660-235">Nicméně před vrácením výsledky Správce úložiště v `InstanceContext` se používá pro uložení instance služby.</span><span class="sxs-lookup"><span data-stu-id="10660-235">However, before returning the results the storage manager in the `InstanceContext` is used to save the service instance.</span></span>  
  
```  
object result = innerOperationInvoker.Invoke(instance,  
    inputs, out outputs);  
  
// Save the instance using the storage manager saved in the   
// current InstanceContext.  
InstanceContextExtension extension =  
    OperationContext.Current.InstanceContext.Extensions.Find<InstanceContextExtension>();  
  
extension.StorageManager.SaveInstance(extension.ContextId, instance);  
return result;  
```  
  
## <a name="using-the-extension"></a><span data-ttu-id="10660-236">Pomocí rozšíření</span><span class="sxs-lookup"><span data-stu-id="10660-236">Using the Extension</span></span>  
 <span data-ttu-id="10660-237">Kanál vrstvy a služby model vrstvy rozšíření hotovi i nyní je možné použít při [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplikace.</span><span class="sxs-lookup"><span data-stu-id="10660-237">Both the channel layer and service model layer extensions are done and they can now be used in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] applications.</span></span> <span data-ttu-id="10660-238">Služby mít do zásobníku kanál použití vlastní vazby, přidejte kanál a potom označit implementace třídy služeb s odpovídajícími atributy.</span><span class="sxs-lookup"><span data-stu-id="10660-238">Services have to add the channel into the channel stack using a custom binding and then mark the service implementation classes with the appropriate attributes.</span></span>  
  
```  
[DurableInstanceContext]  
[ServiceBehavior(InstanceContextMode=InstanceContextMode.PerSession)]  
public class ShoppingCart : IShoppingCart  
{  
//…  
     [SaveState]  
     public int AddItem(string item)  
     {  
         //…  
     }  
//…  
 }  
```  
  
 <span data-ttu-id="10660-239">Klientské aplikace, musíte přidat DurableInstanceContextChannel do zásobníku kanál použití vlastní vazby.</span><span class="sxs-lookup"><span data-stu-id="10660-239">Client applications must add the DurableInstanceContextChannel into the channel stack using a custom binding.</span></span> <span data-ttu-id="10660-240">Ke konfiguraci kanálu deklarativně v konfiguračním souboru, musí být přidán do kolekce element rozšíření vazby sekce prvku vazby.</span><span class="sxs-lookup"><span data-stu-id="10660-240">To configure the channel declaratively in the configuration file, the binding element section has to be added to the binding element extensions collection.</span></span>  
  
```xml  
<system.serviceModel>  
 <extensions>  
   <bindingElementExtensions>  
     <add name="durableInstanceContext"  
type="Microsoft.ServiceModel.Samples.DurableInstanceContextBindingElementSection, DurableInstanceContextExtension, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null"/>  
   </bindingElementExtensions>  
 </extensions>  
```  
  
 <span data-ttu-id="10660-241">Nyní prvku vazby použít s vlastní vazby stejně jako další prvky standardní vazby:</span><span class="sxs-lookup"><span data-stu-id="10660-241">Now the binding element can be used with a custom binding just like other standard binding elements:</span></span>  
  
```xml  
<bindings>  
 <customBinding>  
   <binding name="TextOverHttp">  
     <durableInstanceContext contextType="HttpCookie"/>             
     <reliableSession />  
     <textMessageEncoding />  
     <httpTransport />  
   </binding>  
 </customBinding>  
</bindings>  
```  
  
## <a name="conclusion"></a><span data-ttu-id="10660-242">Závěr</span><span class="sxs-lookup"><span data-stu-id="10660-242">Conclusion</span></span>  
 <span data-ttu-id="10660-243">Tato ukázka vám ukázal, jak vytvořit vlastní protokol kanál a postup přizpůsobení chování služby povolit.</span><span class="sxs-lookup"><span data-stu-id="10660-243">This sample showed how to create a custom protocol channel and how to customize the service behavior to enable it.</span></span>  
  
 <span data-ttu-id="10660-244">Rozšíření lze dále zvýšit tím, že uživatelé, zadejte `IStorageManager` implementace pomocí konfigurační oddíl.</span><span class="sxs-lookup"><span data-stu-id="10660-244">The extension can be further improved by letting users specify the `IStorageManager` implementation using a configuration section.</span></span> <span data-ttu-id="10660-245">Díky tomu je možné upravit záložní úložiště bez nutnosti rekompilace kódu služby.</span><span class="sxs-lookup"><span data-stu-id="10660-245">This makes it possible to modify the backing store without recompiling the service code.</span></span>  
  
 <span data-ttu-id="10660-246">Kromě toho mohou zkuste implementace třídy (například `StateBag`), který zapouzdří stav instance.</span><span class="sxs-lookup"><span data-stu-id="10660-246">Furthermore you could try to implement a class (for example, `StateBag`), which encapsulates the state of the instance.</span></span> <span data-ttu-id="10660-247">Třídy je zodpovědná za uložením stavu, vždy, když se změní.</span><span class="sxs-lookup"><span data-stu-id="10660-247">That class is responsible for persisting the state whenever it changes.</span></span> <span data-ttu-id="10660-248">Tímto způsobem můžete vyhnout použitím `SaveState` atribut a provádět zachování pracovní přesněji (například může stav zachována, když je ve skutečnosti změnil stav místo uložení každý čas při metodu s `SaveState` atribut voláno).</span><span class="sxs-lookup"><span data-stu-id="10660-248">This way you can avoid using the `SaveState` attribute and perform the persisting work more accurately (for example, you could persist the state when the state is actually changed rather than saving it each time when a method with the `SaveState` attribute is called).</span></span>  
  
 <span data-ttu-id="10660-249">Při spuštění ukázky, zobrazí se následující výstup.</span><span class="sxs-lookup"><span data-stu-id="10660-249">When you run the sample, the following output is displayed.</span></span> <span data-ttu-id="10660-250">Klient přidá dvě položky do jeho nákupní košík a pak získá seznam položek v jeho nákupní košík ze služby.</span><span class="sxs-lookup"><span data-stu-id="10660-250">The client adds two items to its shopping cart and then gets the list of items in its shopping cart from the service.</span></span> <span data-ttu-id="10660-251">Stisknutím klávesy ENTER v každé okna konzoly vypnout klienta a služby.</span><span class="sxs-lookup"><span data-stu-id="10660-251">Press ENTER in each console window to shut down the service and client.</span></span>  
  
```  
Enter the name of the product: apples  
Enter the name of the product: bananas  
  
Shopping cart currently contains the following items.  
apples  
bananas  
Press ENTER to shut down client  
```  
  
> [!NOTE]
>  <span data-ttu-id="10660-252">Znovu sestavit službu přepíše soubor databáze.</span><span class="sxs-lookup"><span data-stu-id="10660-252">Rebuilding the service overwrites the database file.</span></span> <span data-ttu-id="10660-253">Chcete-li sledovat stav zachována napříč více spustí vzorku, nezapomeňte znovu sestavit ukázku mezi spustí.</span><span class="sxs-lookup"><span data-stu-id="10660-253">To observe state preserved across multiple runs of the sample, be sure not to rebuild the sample between runs.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="10660-254">Pokud chcete nastavit, sestavit a spustit ukázku</span><span class="sxs-lookup"><span data-stu-id="10660-254">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="10660-255">Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="10660-255">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="10660-256">Sestavte řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="10660-256">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="10660-257">Spustit ukázku v konfiguraci s jednou nebo mezi počítači, postupujte podle pokynů v [spuštění ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="10660-257">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="10660-258">SQL Server 2005 nebo SQL Express 2005. Chcete tuto ukázku spustit, musíte používat.</span><span class="sxs-lookup"><span data-stu-id="10660-258">You must be running SQL Server 2005 or SQL Express 2005 to run this sample.</span></span> <span data-ttu-id="10660-259">Pokud používáte systém SQL Server 2005, musíte změnit konfiguraci služby připojovací řetězec.</span><span class="sxs-lookup"><span data-stu-id="10660-259">If you are running SQL Server 2005, you must modify the configuration of the service's connection string.</span></span> <span data-ttu-id="10660-260">Při spuštění počítače napříč, SQL Server je potřeba jenom na počítači serveru.</span><span class="sxs-lookup"><span data-stu-id="10660-260">When running cross-machine, SQL Server is only required on the server machine.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="10660-261">Ukázky může být již nainstalována na váš počítač.</span><span class="sxs-lookup"><span data-stu-id="10660-261">The samples may already be installed on your machine.</span></span> <span data-ttu-id="10660-262">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="10660-262">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="10660-263">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="10660-263">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="10660-264">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="10660-264">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Instancing\Durable`  
  
## <a name="see-also"></a><span data-ttu-id="10660-265">Viz také</span><span class="sxs-lookup"><span data-stu-id="10660-265">See Also</span></span>
