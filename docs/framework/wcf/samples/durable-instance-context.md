---
title: Trvanlivý kontext instance
ms.date: 03/30/2017
ms.assetid: 97bc2994-5a2c-47c7-927a-c4cd273153df
ms.openlocfilehash: 567ca62d48e80993328548b11f8b59c4fcd355fe
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84600591"
---
# <a name="durable-instance-context"></a><span data-ttu-id="b390d-102">Trvanlivý kontext instance</span><span class="sxs-lookup"><span data-stu-id="b390d-102">Durable Instance Context</span></span>

<span data-ttu-id="b390d-103">Tato ukázka předvádí, jak přizpůsobit modul runtime Windows Communication Foundation (WCF), aby umožňoval trvalé kontexty instancí.</span><span class="sxs-lookup"><span data-stu-id="b390d-103">This sample demonstrates how to customize the Windows Communication Foundation (WCF) runtime to enable durable instance contexts.</span></span> <span data-ttu-id="b390d-104">Jako své záložní úložiště používá SQL Server 2005 (SQL Server 2005 Express v tomto případě).</span><span class="sxs-lookup"><span data-stu-id="b390d-104">It uses SQL Server 2005 as its backing store (SQL Server 2005 Express in this case).</span></span> <span data-ttu-id="b390d-105">Poskytuje ale taky způsob, jak získat přístup k vlastním mechanismům úložiště.</span><span class="sxs-lookup"><span data-stu-id="b390d-105">However, it also provides a way to access custom storage mechanisms.</span></span>

> [!NOTE]
> <span data-ttu-id="b390d-106">Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="b390d-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

<span data-ttu-id="b390d-107">Tato ukázka zahrnuje rozšíření vrstvy kanálu a vrstvy modelu služby WCF.</span><span class="sxs-lookup"><span data-stu-id="b390d-107">This sample involves extending both the channel layer and the service model layer of the WCF.</span></span> <span data-ttu-id="b390d-108">Proto je nutné před použitím podrobností implementace pochopit základní koncepty.</span><span class="sxs-lookup"><span data-stu-id="b390d-108">Therefore it is necessary to understand the underlying concepts before going into the implementation details.</span></span>

<span data-ttu-id="b390d-109">Trvalé kontexty instance můžete najít ve scénářích reálného světa často.</span><span class="sxs-lookup"><span data-stu-id="b390d-109">Durable instance contexts can be found in the real world scenarios quite often.</span></span> <span data-ttu-id="b390d-110">Aplikace nákupního košíku má například možnost pozastavit nákup uprostřed a pokračovat v jiném dni.</span><span class="sxs-lookup"><span data-stu-id="b390d-110">A shopping cart application, for example, has the ability to pause shopping halfway through and continue it on another day.</span></span> <span data-ttu-id="b390d-111">Takže když na příští den navštívíme nákupní košík, náš původní kontext se obnoví.</span><span class="sxs-lookup"><span data-stu-id="b390d-111">So that when we visit the shopping cart the next day, our original context is restored.</span></span> <span data-ttu-id="b390d-112">Je důležité si uvědomit, že aplikace nákupního košíku (na serveru) neudržuje během odpojování instanci nákupního košíku.</span><span class="sxs-lookup"><span data-stu-id="b390d-112">It is important to note that the shopping cart application (on the server) does not maintain the shopping cart instance while we are disconnected.</span></span> <span data-ttu-id="b390d-113">Místo toho uchovává svůj stav na trvalé paměťové médium a používá ho při vytváření nové instance pro obnovený kontext.</span><span class="sxs-lookup"><span data-stu-id="b390d-113">Instead, it persists its state into a durable storage media and uses it when constructing a new instance for the restored context.</span></span> <span data-ttu-id="b390d-114">Proto instance služby, která se může nabývat stejným kontextem, není stejná jako předchozí instance (to znamená, že nemá stejnou adresu paměti).</span><span class="sxs-lookup"><span data-stu-id="b390d-114">Therefore the service instance that may service for the same context is not the same as the previous instance (that is, it does not have the same memory address).</span></span>

<span data-ttu-id="b390d-115">Je možné, že kontext trvalé instance je možný malým protokolem, který vyměňuje ID kontextu mezi klientem a službou.</span><span class="sxs-lookup"><span data-stu-id="b390d-115">Durable instance context is made possible by a small protocol that exchanges a context ID between the client and service.</span></span> <span data-ttu-id="b390d-116">Toto ID kontextu se vytvoří v klientovi a přenáší do služby.</span><span class="sxs-lookup"><span data-stu-id="b390d-116">This context ID is created on the client and transmitted to the service.</span></span> <span data-ttu-id="b390d-117">Když je instance služby vytvořená, pokusí se modul runtime služby načíst trvalý stav, který odpovídá tomuto ID kontextu z trvalého úložiště (ve výchozím nastavení je to databáze SQL Server 2005).</span><span class="sxs-lookup"><span data-stu-id="b390d-117">When the service instance is created, the service runtime tries to load the persisted state that corresponds to this context ID from a persistent storage (by default it is a SQL Server 2005 database).</span></span> <span data-ttu-id="b390d-118">Pokud není k dispozici žádný stav, má nová instance svůj výchozí stav.</span><span class="sxs-lookup"><span data-stu-id="b390d-118">If no state is available, the new instance has its default state.</span></span> <span data-ttu-id="b390d-119">Implementace služby používá vlastní atribut k označení operací, které mění stav implementace služby, aby modul runtime po jejich vyvolání mohl uložit instanci služby.</span><span class="sxs-lookup"><span data-stu-id="b390d-119">The service implementation uses a custom attribute to mark operations that change the state of the service implementation so that the runtime can save the service instance after invoking them.</span></span>

<span data-ttu-id="b390d-120">V předchozím popisu lze snadno odlišit dva kroky, aby bylo možné dosáhnout tohoto cíle:</span><span class="sxs-lookup"><span data-stu-id="b390d-120">By the previous description, two steps can easily be distinguished to achieve the goal:</span></span>

1. <span data-ttu-id="b390d-121">Změňte zprávu, která je na lince, aby převedla ID kontextu.</span><span class="sxs-lookup"><span data-stu-id="b390d-121">Change the message that goes on the wire to carry the context ID.</span></span>

2. <span data-ttu-id="b390d-122">Pokud chcete implementovat vlastní logiku vytváření instancí, změňte místní chování služby.</span><span class="sxs-lookup"><span data-stu-id="b390d-122">Change the service local behavior to implement custom instancing logic.</span></span>

<span data-ttu-id="b390d-123">Vzhledem k tomu, že první v seznamu má vliv na zprávy, měla by být implementována jako vlastní kanál a zapojena do vrstvy kanálu.</span><span class="sxs-lookup"><span data-stu-id="b390d-123">Because the first one in the list affects the messages on the wire, it should be implemented as a custom channel and be hooked up to the channel layer.</span></span> <span data-ttu-id="b390d-124">Ta má vliv pouze na místní chování služby, a proto může být implementována rozšířením několika bodů rozšiřitelnosti služby.</span><span class="sxs-lookup"><span data-stu-id="b390d-124">The latter only affects the service local behavior and therefore can be implemented by extending several service extensibility points.</span></span> <span data-ttu-id="b390d-125">V následujících částech jsou popsána všechna tato rozšíření.</span><span class="sxs-lookup"><span data-stu-id="b390d-125">In the next few sections, each of these extensions are discussed.</span></span>

## <a name="durable-instancecontext-channel"></a><span data-ttu-id="b390d-126">Trvalý kanál InstanceContext</span><span class="sxs-lookup"><span data-stu-id="b390d-126">Durable InstanceContext Channel</span></span>

<span data-ttu-id="b390d-127">První věc, kterou si můžete prohlédnout, je rozšíření vrstvy kanálu.</span><span class="sxs-lookup"><span data-stu-id="b390d-127">The first thing to look at is a channel layer extension.</span></span> <span data-ttu-id="b390d-128">Prvním krokem při psaní vlastního kanálu je určení komunikační struktury kanálu.</span><span class="sxs-lookup"><span data-stu-id="b390d-128">The first step in writing a custom channel is to decide the communication structure of the channel.</span></span> <span data-ttu-id="b390d-129">Při zavádění nového přenosového protokolu by kanál měl spolupracovat s prakticky jakýmkoli jiným kanálem v zásobníku kanálů.</span><span class="sxs-lookup"><span data-stu-id="b390d-129">As a new wire protocol is being introduced, the channel should work with almost any other channel in the channel stack.</span></span> <span data-ttu-id="b390d-130">Proto by měl podporovat všechny vzory výměny zpráv.</span><span class="sxs-lookup"><span data-stu-id="b390d-130">Therefore it should support all the message exchange patterns.</span></span> <span data-ttu-id="b390d-131">Základní funkce kanálu jsou však stejné bez ohledu na jeho komunikační strukturu.</span><span class="sxs-lookup"><span data-stu-id="b390d-131">However, the core functionality of the channel is the same regardless of its communication structure.</span></span> <span data-ttu-id="b390d-132">Konkrétně z klienta by měl z klienta napsat ID kontextu pro zprávy a ze služby, které by mělo číst toto ID kontextu ze zpráv a předávat je do horních úrovní.</span><span class="sxs-lookup"><span data-stu-id="b390d-132">More specifically, from the client it should write the context ID to the messages and from the service it should read this context ID from the messages and pass it to the upper levels.</span></span> <span data-ttu-id="b390d-133">Z tohoto důvodu `DurableInstanceContextChannelBase` je vytvořena třída, která funguje jako abstraktní základní třída pro všechny implementace kontextu trvalého kanálu instance.</span><span class="sxs-lookup"><span data-stu-id="b390d-133">Because of that, a `DurableInstanceContextChannelBase` class is created that acts as the abstract base class for all durable instance context channel implementations.</span></span> <span data-ttu-id="b390d-134">Tato třída obsahuje funkce správy běžných stavových počítačů a dva chráněné členy pro použití a čtení informací o kontextu do a ze zpráv.</span><span class="sxs-lookup"><span data-stu-id="b390d-134">This class contains the common state machine management functions and two protected members to apply and read the context information to and from messages.</span></span>

```csharp
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

<span data-ttu-id="b390d-135">Tyto dvě metody využívají `IContextManager` implementace pro zápis a čtení ID kontextu do nebo ze zprávy.</span><span class="sxs-lookup"><span data-stu-id="b390d-135">These two methods make use of `IContextManager` implementations to write and read the context ID to or from the message.</span></span> <span data-ttu-id="b390d-136">( `IContextManager` je vlastní rozhraní používané k definování kontraktu pro všechny správce kontextu.) Kanál může buď zahrnout ID kontextu ve vlastní hlavičce SOAP, nebo v hlavičce souboru cookie protokolu HTTP.</span><span class="sxs-lookup"><span data-stu-id="b390d-136">(`IContextManager` is a custom interface used to define the contract for all context managers.) The channel can either include the context ID in a custom SOAP header or in an HTTP cookie header.</span></span> <span data-ttu-id="b390d-137">Každá implementace správce kontextu dědí z `ContextManagerBase` třídy, která obsahuje společné funkce pro všechny správce kontextu.</span><span class="sxs-lookup"><span data-stu-id="b390d-137">Each context manager implementation inherits from the `ContextManagerBase` class that contains the common functionality for all context managers.</span></span> <span data-ttu-id="b390d-138">`GetContextId`Metoda v této třídě slouží k původnímu ID kontextu z klienta.</span><span class="sxs-lookup"><span data-stu-id="b390d-138">The `GetContextId` method in this class is used to originate the context ID from the client.</span></span> <span data-ttu-id="b390d-139">Při prvním pokusu o ID kontextu je tato metoda uložena do textového souboru, jehož název je vytvořen pomocí adresy vzdáleného koncového bodu (neplatné znaky názvu souboru v typických identifikátorech URI jsou nahrazeny znakem @).</span><span class="sxs-lookup"><span data-stu-id="b390d-139">When a context ID is originated for the first time, this method saves it into a text file whose name is constructed by the remote endpoint address (the invalid file name characters in the typical URIs are replaced with @ characters).</span></span>

<span data-ttu-id="b390d-140">Později, když je ID kontextu vyžadováno pro stejný vzdálený koncový bod, kontroluje, zda existuje příslušný soubor.</span><span class="sxs-lookup"><span data-stu-id="b390d-140">Later when the context ID is required for the same remote endpoint, it checks whether an appropriate file exists.</span></span> <span data-ttu-id="b390d-141">V takovém případě přečte ID kontextu a vrátí.</span><span class="sxs-lookup"><span data-stu-id="b390d-141">If it does, it reads the context ID and returns.</span></span> <span data-ttu-id="b390d-142">V opačném případě vrátí nově generované ID kontextu a uloží jej do souboru.</span><span class="sxs-lookup"><span data-stu-id="b390d-142">Otherwise it returns a newly generated context ID and saves it to a file.</span></span> <span data-ttu-id="b390d-143">S výchozí konfigurací jsou tyto soubory umístěny v adresáři s názvem ContextStore, který se nachází v dočasném adresáři aktuálního uživatele.</span><span class="sxs-lookup"><span data-stu-id="b390d-143">With the default configuration, these files are placed in a directory called ContextStore, which resides in the current user's temp directory.</span></span> <span data-ttu-id="b390d-144">Toto umístění však lze konfigurovat pomocí elementu vazby.</span><span class="sxs-lookup"><span data-stu-id="b390d-144">However this location is configurable using the binding element.</span></span>

<span data-ttu-id="b390d-145">Mechanismus použitý k přenosu ID kontextu je možné nakonfigurovat.</span><span class="sxs-lookup"><span data-stu-id="b390d-145">The mechanism used to transport the context ID is configurable.</span></span> <span data-ttu-id="b390d-146">Mohl by být buď zapsaný do hlavičky souboru cookie protokolu HTTP, nebo do vlastní hlavičky SOAP.</span><span class="sxs-lookup"><span data-stu-id="b390d-146">It could be either written to the HTTP cookie header or to a custom SOAP header.</span></span> <span data-ttu-id="b390d-147">Vlastní přístup k hlavičkám SOAP umožňuje používat tento protokol u jiných protokolů než HTTP (například TCP nebo Named Pipes).</span><span class="sxs-lookup"><span data-stu-id="b390d-147">The custom SOAP header approach makes it possible to use this protocol with non-HTTP protocols (for example, TCP or Named Pipes).</span></span> <span data-ttu-id="b390d-148">Existují dvě třídy, konkrétně `MessageHeaderContextManager` a `HttpCookieContextManager` , které implementují tyto dvě možnosti.</span><span class="sxs-lookup"><span data-stu-id="b390d-148">There are two classes, namely `MessageHeaderContextManager` and `HttpCookieContextManager`, which implement these two options.</span></span>

<span data-ttu-id="b390d-149">Oba Oba napíší ID kontextu do zprávy odpovídajícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="b390d-149">Both of them write the context ID to the message appropriately.</span></span> <span data-ttu-id="b390d-150">Například `MessageHeaderContextManager` Třída ji zapíše do HLAVIČKY SOAP v `WriteContext` metodě.</span><span class="sxs-lookup"><span data-stu-id="b390d-150">For example, the `MessageHeaderContextManager` class writes it to a SOAP header in the `WriteContext` method.</span></span>

```csharp
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

<span data-ttu-id="b390d-151">`ApplyContext` `ReadContextId` Metody a ve `DurableInstanceContextChannelBase` třídě vyvolávají `IContextManager.ReadContext` a v `IContextManager.WriteContext` uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="b390d-151">Both the `ApplyContext` and `ReadContextId` methods in the `DurableInstanceContextChannelBase` class invoke the `IContextManager.ReadContext` and `IContextManager.WriteContext`, respectively.</span></span> <span data-ttu-id="b390d-152">Tyto správce kontextu však nejsou přímo vytvořeny `DurableInstanceContextChannelBase` třídou.</span><span class="sxs-lookup"><span data-stu-id="b390d-152">However, these context managers are not directly created by the `DurableInstanceContextChannelBase` class.</span></span> <span data-ttu-id="b390d-153">Místo toho používá `ContextManagerFactory` třídu k provedení této úlohy.</span><span class="sxs-lookup"><span data-stu-id="b390d-153">Instead it uses the `ContextManagerFactory` class to do that job.</span></span>

```csharp
IContextManager contextManager =
                ContextManagerFactory.CreateContextManager(contextType,
                this.contextStoreLocation,
                this.endpointAddress);
```

<span data-ttu-id="b390d-154">`ApplyContext`Metoda je vyvolána odesílajícími kanály.</span><span class="sxs-lookup"><span data-stu-id="b390d-154">The `ApplyContext` method is invoked by the sending channels.</span></span> <span data-ttu-id="b390d-155">Vloží ID kontextu do odchozích zpráv.</span><span class="sxs-lookup"><span data-stu-id="b390d-155">It injects the context ID to the outgoing messages.</span></span> <span data-ttu-id="b390d-156">`ReadContextId`Metoda je vyvolána přijímacími kanály.</span><span class="sxs-lookup"><span data-stu-id="b390d-156">The `ReadContextId` method is invoked by the receiving channels.</span></span> <span data-ttu-id="b390d-157">Tato metoda zajistí, že ID kontextu je k dispozici v příchozích zprávách a přidá je do `Properties` kolekce `Message` třídy.</span><span class="sxs-lookup"><span data-stu-id="b390d-157">This method ensures that the context ID is available in the incoming messages and adds it to the `Properties` collection of the `Message` class.</span></span> <span data-ttu-id="b390d-158">Vyvolá také v případě, že dojde `CommunicationException` k selhání při čtení ID kontextu, čímž dojde k přerušení kanálu.</span><span class="sxs-lookup"><span data-stu-id="b390d-158">It also throws a `CommunicationException` in case of a failure to read the context ID and thus causes the channel to be aborted.</span></span>

```csharp
message.Properties.Add(DurableInstanceContextUtility.ContextIdProperty, contextId);
```

<span data-ttu-id="b390d-159">Než budete pokračovat, je důležité pochopit použití `Properties` kolekce ve `Message` třídě.</span><span class="sxs-lookup"><span data-stu-id="b390d-159">Before proceeding, it is important to understand the usage of the `Properties` collection in the `Message` class.</span></span> <span data-ttu-id="b390d-160">Tato `Properties` kolekce se obvykle používá při předávání dat z nižší úrovně do horních úrovní z vrstvy kanálu.</span><span class="sxs-lookup"><span data-stu-id="b390d-160">Typically, this `Properties` collection is used when passing data from lower to the upper levels from the channel layer.</span></span> <span data-ttu-id="b390d-161">Tímto způsobem je možné zajistit, aby se požadovaná data poskytovala na nejvyšší úrovni konzistentním způsobem bez ohledu na podrobnosti protokolu.</span><span class="sxs-lookup"><span data-stu-id="b390d-161">This way the desired data can be provided to the upper levels in a consistent manner regardless of the protocol details.</span></span> <span data-ttu-id="b390d-162">Jinými slovy, vrstva kanálu může odeslat a přijmout ID kontextu buď jako hlavičku protokolu SOAP, nebo jako hlavičku souboru cookie protokolu HTTP.</span><span class="sxs-lookup"><span data-stu-id="b390d-162">In other words, the channel layer can send and receive the context ID either as a SOAP header or an HTTP cookie header.</span></span> <span data-ttu-id="b390d-163">Není ale nutné, aby horní úrovně věděli o těchto podrobnostech, protože vrstva kanálu zpřístupňuje tyto informace v `Properties` kolekci.</span><span class="sxs-lookup"><span data-stu-id="b390d-163">But it is not necessary for the upper levels to know about these details because the channel layer makes this information available in the `Properties` collection.</span></span>

<span data-ttu-id="b390d-164">Teď je potřeba, aby `DurableInstanceContextChannelBase` byla v rámci třídy místo všech deseti z nezbytných rozhraní (IOutputChannel, IInputChannel, IOutputSessionChannel, IInputSessionChannel, třídu IRequestChannel, IReplyChannel, IRequestSessionChannel, IReplySessionChannel, IDuplexChannel, IDuplexSessionChannel) implementovaná.</span><span class="sxs-lookup"><span data-stu-id="b390d-164">Now with the `DurableInstanceContextChannelBase` class in place all ten of the necessary interfaces (IOutputChannel, IInputChannel, IOutputSessionChannel, IInputSessionChannel, IRequestChannel, IReplyChannel, IRequestSessionChannel, IReplySessionChannel, IDuplexChannel, IDuplexSessionChannel) must be implemented.</span></span> <span data-ttu-id="b390d-165">Podobá se každému dostupnému vzorci výměny zpráv (datagram, simplexní, duplexní a jejich variantní relace).</span><span class="sxs-lookup"><span data-stu-id="b390d-165">They resemble every available message exchange pattern (datagram, simplex, duplex, and their sessionful variants).</span></span> <span data-ttu-id="b390d-166">Každá z těchto implementací dědí základní třídu, která byla dříve popsána, a `ApplyContext` `ReadContextId` správné volání.</span><span class="sxs-lookup"><span data-stu-id="b390d-166">Each of these implementations inherits the base class previously described and calls `ApplyContext` and `ReadContextId` appropriately.</span></span> <span data-ttu-id="b390d-167">Například, `DurableInstanceContextOutputChannel` který implementuje rozhraní IOutputChannel – zavolá `ApplyContext` metodu z každé metody, která odesílá zprávy.</span><span class="sxs-lookup"><span data-stu-id="b390d-167">For example, `DurableInstanceContextOutputChannel` - which implements the IOutputChannel interface - calls the `ApplyContext` method from each method that sends the messages.</span></span>

```csharp
public void Send(Message message, TimeSpan timeout)
{
    // Apply the context information before sending the message.
    this.ApplyContext(message);
    //…
}
```

<span data-ttu-id="b390d-168">Na druhé straně `DurableInstanceContextInputChannel` – to implementuje `IInputChannel` rozhraní – volá `ReadContextId` metodu v každé metodě, která přijímá zprávy.</span><span class="sxs-lookup"><span data-stu-id="b390d-168">On the other hand, `DurableInstanceContextInputChannel` - which implements the `IInputChannel` interface - calls the `ReadContextId` method in each method, which receives the messages.</span></span>

```csharp
public Message Receive(TimeSpan timeout)
{
    //…
      ReadContextId(message);
      return message;
}
```

<span data-ttu-id="b390d-169">Kromě toho tato implementace kanálu deleguje volání metody do kanálu pod nimi v zásobníku kanálu.</span><span class="sxs-lookup"><span data-stu-id="b390d-169">Apart from this, these channel implementations delegate the method invocations to the channel below them in the channel stack.</span></span> <span data-ttu-id="b390d-170">Varianty v relaci však mají základní logiku, aby bylo zajištěno, že ID kontextu je odesláno a je určeno pouze pro první zprávu, která způsobí vytvoření relace.</span><span class="sxs-lookup"><span data-stu-id="b390d-170">However, sessionful variants have a basic logic to make sure that the context ID is sent and is read only for the first message that causes the session to be created.</span></span>

```csharp
if (isFirstMessage)
{
//…
    this.ApplyContext(message);
    isFirstMessage = false;
}
```

<span data-ttu-id="b390d-171">Tato implementace kanálu se pak do modulu runtime kanálu WCF přidají `DurableInstanceContextBindingElement` odpovídající třídou a `DurableInstanceContextBindingElementSection` třídou.</span><span class="sxs-lookup"><span data-stu-id="b390d-171">These channel implementations are then added to the WCF channel runtime by the `DurableInstanceContextBindingElement` class and `DurableInstanceContextBindingElementSection` class appropriately.</span></span> <span data-ttu-id="b390d-172">Další podrobnosti o prvcích vazby a oddílech prvků vazby najdete v ukázkové dokumentaci k [HttpCookieSession](httpcookiesession.md) kanálu.</span><span class="sxs-lookup"><span data-stu-id="b390d-172">See the [HttpCookieSession](httpcookiesession.md) channel sample documentation for more details about binding elements and binding element sections.</span></span>

## <a name="service-model-layer-extensions"></a><span data-ttu-id="b390d-173">Rozšíření vrstvy modelu služby</span><span class="sxs-lookup"><span data-stu-id="b390d-173">Service Model Layer Extensions</span></span>

<span data-ttu-id="b390d-174">Teď, když je ID kontextu přenášeno přes vrstvu kanálu, může být implementováno chování služby pro přizpůsobení vytváření instancí.</span><span class="sxs-lookup"><span data-stu-id="b390d-174">Now that the context ID has traveled through the channel layer, the service behavior can be implemented to customize the instantiation.</span></span> <span data-ttu-id="b390d-175">V této ukázce se k načtení a uložení stavu z nebo do trvalého úložiště používá správce úložiště.</span><span class="sxs-lookup"><span data-stu-id="b390d-175">In this sample, a storage manager is used to load and save state from or to the persistent store.</span></span> <span data-ttu-id="b390d-176">Jak bylo vysvětleno dříve, Tato ukázka poskytuje Správce úložiště, který jako své záložní úložiště používá SQL Server 2005.</span><span class="sxs-lookup"><span data-stu-id="b390d-176">As explained previously, this sample provides a storage manager that uses SQL Server 2005 as its backing store.</span></span> <span data-ttu-id="b390d-177">Do tohoto rozšíření je ale také možné přidat vlastní mechanismy úložiště.</span><span class="sxs-lookup"><span data-stu-id="b390d-177">However, it is also possible to add custom storage mechanisms to this extension.</span></span> <span data-ttu-id="b390d-178">K tomu, aby bylo deklarováno veřejné rozhraní, které musí být implementováno všemi Správci úložiště.</span><span class="sxs-lookup"><span data-stu-id="b390d-178">To do that a public interface is declared, which must be implemented by all storage managers.</span></span>

```csharp
public interface IStorageManager
{
    object GetInstance(string contextId, Type type);
    void SaveInstance(string contextId, object state);
}
```

<span data-ttu-id="b390d-179">`SqlServerStorageManager`Třída obsahuje výchozí `IStorageManager` implementaci.</span><span class="sxs-lookup"><span data-stu-id="b390d-179">The `SqlServerStorageManager` class contains the default `IStorageManager` implementation.</span></span> <span data-ttu-id="b390d-180">Ve své `SaveInstance` metodě je daný objekt serializován pomocí objektu XmlSerializer a je uložen do databáze SQL Server.</span><span class="sxs-lookup"><span data-stu-id="b390d-180">In its `SaveInstance` method, the given object is serialized using the XmlSerializer and is saved to the SQL Server database.</span></span>

```csharp
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

<span data-ttu-id="b390d-181">V `GetInstance` metodě jsou serializovaná data čtena pro dané ID kontextu a objekt sestavený z něj je vrácen volajícímu.</span><span class="sxs-lookup"><span data-stu-id="b390d-181">In the `GetInstance` method, the serialized data is read for a given context ID and the object constructed from it is returned to the caller.</span></span>

```csharp
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

<span data-ttu-id="b390d-182">Uživatelé těchto správců úložiště by nemuseli vytvářet instance přímo.</span><span class="sxs-lookup"><span data-stu-id="b390d-182">Users of these storage managers are not supposed to instantiate them directly.</span></span> <span data-ttu-id="b390d-183">Používají `StorageManagerFactory` třídu, která je abstraktní z podrobností o vytváření Správce úložiště.</span><span class="sxs-lookup"><span data-stu-id="b390d-183">They use the `StorageManagerFactory` class, which abstracts from the storage manager creation details.</span></span> <span data-ttu-id="b390d-184">Tato třída má jednoho statického člena, `GetStorageManager` který vytvoří instanci daného typu Správce úložiště.</span><span class="sxs-lookup"><span data-stu-id="b390d-184">This class has one static member, `GetStorageManager`, which creates an instance of a given storage manager type.</span></span> <span data-ttu-id="b390d-185">Pokud je parametrem typu `null` , tato metoda vytvoří instanci výchozí `SqlServerStorageManager` třídy a vrátí ji.</span><span class="sxs-lookup"><span data-stu-id="b390d-185">If the type parameter is `null`, this method creates an instance of the default `SqlServerStorageManager` class and returns it.</span></span> <span data-ttu-id="b390d-186">Ověří také daný typ, aby zajistil, že implementuje `IStorageManager` rozhraní.</span><span class="sxs-lookup"><span data-stu-id="b390d-186">It also validates the given type to make sure that it implements the `IStorageManager` interface.</span></span>

```csharp
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

<span data-ttu-id="b390d-187">Je implementována potřebná infrastruktura pro čtení a zápis instancí z trvalého úložiště.</span><span class="sxs-lookup"><span data-stu-id="b390d-187">The necessary infrastructure to read and write instances from the persistent storage is implemented.</span></span> <span data-ttu-id="b390d-188">Teď je potřeba udělat kroky ke změně chování služby.</span><span class="sxs-lookup"><span data-stu-id="b390d-188">Now the necessary steps to change the service behavior have to be taken.</span></span>

<span data-ttu-id="b390d-189">Jako první krok tohoto procesu musíme Uložit ID kontextu, které bylo předáno přes vrstvu kanálu, do aktuálního rozhraní InstanceContext.</span><span class="sxs-lookup"><span data-stu-id="b390d-189">As the first step of this process we have to save the context ID, which came through the channel layer to the current InstanceContext.</span></span> <span data-ttu-id="b390d-190">InstanceContext je komponenta modulu runtime, která funguje jako propojení mezi dispečerem WCF a instancí služby.</span><span class="sxs-lookup"><span data-stu-id="b390d-190">InstanceContext is a runtime component that acts as the link between the WCF dispatcher and the service instance.</span></span> <span data-ttu-id="b390d-191">Dá se použít k poskytnutí dalšího stavu a chování instance služby.</span><span class="sxs-lookup"><span data-stu-id="b390d-191">It can be used to provide additional state and behavior to the service instance.</span></span> <span data-ttu-id="b390d-192">To je nezbytné proto, že při komunikaci v relaci je ID kontextu odesláno pouze s první zprávou.</span><span class="sxs-lookup"><span data-stu-id="b390d-192">This is essential because in sessionful communication the context ID is sent only with the first message.</span></span>

<span data-ttu-id="b390d-193">Služba WCF umožňuje rozšířit svou komponentu běhového prostředí InstanceContext přidáním nového stavu a chování pomocí jeho modelu rozšiřitelného objektu.</span><span class="sxs-lookup"><span data-stu-id="b390d-193">WCF allows extending its InstanceContext runtime component by adding a new state and behavior using its extensible object pattern.</span></span> <span data-ttu-id="b390d-194">Model rozšiřitelného objektu se používá ve službě WCF pro rozšiřující existující běhové třídy s novými funkcemi nebo pro přidání nových funkcí stavu do objektu.</span><span class="sxs-lookup"><span data-stu-id="b390d-194">The extensible object pattern is used in WCF to either extend existing runtime classes with new functionality or to add new state features to an object.</span></span> <span data-ttu-id="b390d-195">Existují tři rozhraní ve vzoru rozšiřitelného objektu – IExtensibleObject \<T> , IExtension \<T> a IExtensionCollection \<T> :</span><span class="sxs-lookup"><span data-stu-id="b390d-195">There are three interfaces in the extensible object pattern - IExtensibleObject\<T>, IExtension\<T>, and IExtensionCollection\<T>:</span></span>

- <span data-ttu-id="b390d-196">Rozhraní IExtensibleObject \<T> je implementováno pomocí objektů, které umožňují rozšíření, která přizpůsobují jejich fungování.</span><span class="sxs-lookup"><span data-stu-id="b390d-196">The IExtensibleObject\<T> interface is implemented by objects that allow extensions that customize their functionality.</span></span>

- <span data-ttu-id="b390d-197">Rozhraní IExtension \<T> je implementováno objekty, které jsou rozšíření třídy typu T.</span><span class="sxs-lookup"><span data-stu-id="b390d-197">The IExtension\<T> interface is implemented by objects that are extensions of classes of type T.</span></span>

- <span data-ttu-id="b390d-198">Rozhraní IExtensionCollection \<T> je kolekce IExtensions, která umožňuje načíst IExtensions podle jejich typu.</span><span class="sxs-lookup"><span data-stu-id="b390d-198">The IExtensionCollection\<T> interface is a collection of IExtensions that allows for retrieving IExtensions by their type.</span></span>

<span data-ttu-id="b390d-199">Proto by měla být vytvořena třída InstanceContextExtension, která implementuje rozhraní IExtension a definuje požadovaný stav pro uložení ID kontextu.</span><span class="sxs-lookup"><span data-stu-id="b390d-199">Therefore an InstanceContextExtension class should be created that implements the IExtension interface and defines the required state to save the context ID.</span></span> <span data-ttu-id="b390d-200">Tato třída také poskytuje stav pro uchování používaného Správce úložiště.</span><span class="sxs-lookup"><span data-stu-id="b390d-200">This class also provides the state to hold the storage manager being used.</span></span> <span data-ttu-id="b390d-201">Jakmile je nový stav uložený, neměl by být možné ho upravovat.</span><span class="sxs-lookup"><span data-stu-id="b390d-201">Once the new state is saved, it should not be possible to modify it.</span></span> <span data-ttu-id="b390d-202">Proto je stav poskytován a uložen do instance v době, kdy je vytvořen, a je přístupný pouze pomocí vlastností jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="b390d-202">Therefore the state is provided and saved to the instance at the time it is being constructed and then only accessible using read-only properties.</span></span>

```csharp
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

<span data-ttu-id="b390d-203">Třída InstanceContextInitializer implementuje rozhraní IInstanceContextInitializer a přidá rozšíření kontextu instance do kolekce rozšíření konstruované konstrukce InstanceContext.</span><span class="sxs-lookup"><span data-stu-id="b390d-203">The InstanceContextInitializer class implements the IInstanceContextInitializer interface and adds the instance context extension to the Extensions collection of the InstanceContext being constructed.</span></span>

```csharp
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

<span data-ttu-id="b390d-204">Jak je popsáno výše, ID kontextu je načteno z `Properties` kolekce `Message` třídy a předáno do konstruktoru třídy rozšíření.</span><span class="sxs-lookup"><span data-stu-id="b390d-204">As described earlier the context ID is read from the `Properties` collection of the `Message` class and passed to the constructor of the extension class.</span></span> <span data-ttu-id="b390d-205">Ukazuje, jak lze informace mezi vrstvami konzistentně vyměňovat.</span><span class="sxs-lookup"><span data-stu-id="b390d-205">This demonstrates how information can be exchanged between the layers in a consistent manner.</span></span>

<span data-ttu-id="b390d-206">Dalším důležitým krokem je přepsání procesu vytváření instancí služby.</span><span class="sxs-lookup"><span data-stu-id="b390d-206">The next important step is overriding the service instance creation process.</span></span> <span data-ttu-id="b390d-207">WCF umožňuje implementovat vlastní chování vytváření instancí a zapojit je do modulu runtime pomocí rozhraní IInstanceProvider.</span><span class="sxs-lookup"><span data-stu-id="b390d-207">WCF allows implementing custom instantiation behaviors and hooking them up to the runtime using the IInstanceProvider interface.</span></span> <span data-ttu-id="b390d-208">Nová `InstanceProvider` Třída je implementována k provedení této úlohy.</span><span class="sxs-lookup"><span data-stu-id="b390d-208">The new `InstanceProvider` class is implemented to do that job.</span></span> <span data-ttu-id="b390d-209">Typ služby očekávaný od zprostředkovatele instance je přijatý v konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="b390d-209">The service type expected from the instance provider is accepted in the constructor.</span></span> <span data-ttu-id="b390d-210">Později se použije k vytvoření nových instancí.</span><span class="sxs-lookup"><span data-stu-id="b390d-210">Later this is used to create new instances.</span></span> <span data-ttu-id="b390d-211">V `GetInstance` implementaci se vytvoří instance Správce úložiště, kde se hledá trvalá instance.</span><span class="sxs-lookup"><span data-stu-id="b390d-211">In the `GetInstance` implementation, an instance of a storage manager is created looking for a persisted instance.</span></span> <span data-ttu-id="b390d-212">Pokud se vrátí `null` , pak se vytvoří instance nové instance typu služby a vrátí se volajícímu.</span><span class="sxs-lookup"><span data-stu-id="b390d-212">If it returns `null`, then a new instance of the service type is instantiated and returned to the caller.</span></span>

```csharp
public object GetInstance(InstanceContext instanceContext, Message message)
{
    object instance = null;

    DurableInstanceContextExtension extension =
    instanceContext.Extensions.Find<DurableInstanceContextExtension>();

    string contextId = extension.ContextId;
    IStorageManager storageManager = extension.StorageManager;

    instance = storageManager.GetInstance(contextId, serviceType);

    instance ??= Activator.CreateInstance(serviceType);
    return instance;
}
```

<span data-ttu-id="b390d-213">Dalším důležitým krokem je instalace `InstanceContextExtension` tříd, a `InstanceContextInitializer` `InstanceProvider` do modulu runtime modelu služby.</span><span class="sxs-lookup"><span data-stu-id="b390d-213">The next important step is to install the `InstanceContextExtension`, `InstanceContextInitializer`, and `InstanceProvider` classes into the service model runtime.</span></span> <span data-ttu-id="b390d-214">Vlastní atribut lze použít k označení tříd implementace služby pro instalaci chování.</span><span class="sxs-lookup"><span data-stu-id="b390d-214">A custom attribute could be used to mark the service implementation classes to install the behavior.</span></span> <span data-ttu-id="b390d-215">`DurableInstanceContextAttribute`Obsahuje implementaci pro tento atribut a implementuje `IServiceBehavior` rozhraní pro rozšiřování celého modulu runtime služby.</span><span class="sxs-lookup"><span data-stu-id="b390d-215">The `DurableInstanceContextAttribute` contains the implementation for this attribute and it implements the `IServiceBehavior` interface to extend the entire service runtime.</span></span>

<span data-ttu-id="b390d-216">Tato třída má vlastnost, která přijímá typ Správce úložiště, který se má použít.</span><span class="sxs-lookup"><span data-stu-id="b390d-216">This class has a property that accepts the type of the storage manager to be used.</span></span> <span data-ttu-id="b390d-217">Tímto způsobem implementace umožňuje uživatelům zadat vlastní `IStorageManager` implementaci jako parametr tohoto atributu.</span><span class="sxs-lookup"><span data-stu-id="b390d-217">In this way, the implementation enables the users to specify their own `IStorageManager` implementation as parameter of this attribute.</span></span>

<span data-ttu-id="b390d-218">V `ApplyDispatchBehavior` implementaci `InstanceContextMode` `ServiceBehavior` je ověřován aktuální atribut.</span><span class="sxs-lookup"><span data-stu-id="b390d-218">In the `ApplyDispatchBehavior` implementation, the `InstanceContextMode` of the current `ServiceBehavior` attribute is being verified.</span></span> <span data-ttu-id="b390d-219">Pokud je tato vlastnost nastavená na singleton, není možné povolit trvalé vytváření instancí a `InvalidOperationException` k oznamování hostitele je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="b390d-219">If this property is set to Singleton, enabling durable instancing is not possible and an `InvalidOperationException` is thrown to notify the host.</span></span>

```csharp
ServiceBehaviorAttribute serviceBehavior =
    serviceDescription.Behaviors.Find<ServiceBehaviorAttribute>();

if (serviceBehavior != null &&
     serviceBehavior.InstanceContextMode == InstanceContextMode.Single)
{
    throw new InvalidOperationException(
       ResourceHelper.GetString("ExSingletonInstancingNotSupported"));
}
```

<span data-ttu-id="b390d-220">Po této instanci se vytvoří a nainstalují instance Správce úložiště, inicializátor kontextu instance a zprostředkovatele instancí v rámci `DispatchRuntime` vytvoření pro každý koncový bod.</span><span class="sxs-lookup"><span data-stu-id="b390d-220">After this the instances of the storage manager, instance context initializer, and the instance provider are created and installed in the `DispatchRuntime` created for every endpoint.</span></span>

```csharp
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

<span data-ttu-id="b390d-221">V dosavadním přehledu vytvořila Tato ukázka kanál, který povolil vlastní přenosový protokol pro výměnu vlastního ID kontextu a také přepisuje výchozí chování vytváření instancí, aby načetl instance z trvalého úložiště.</span><span class="sxs-lookup"><span data-stu-id="b390d-221">In summary so far, this sample has produced a channel that enabled the custom wire protocol for custom context ID exchange and it also overwrites the default instancing behavior to load the instances from the persistent storage.</span></span>

<span data-ttu-id="b390d-222">Levou z možností je uložit instanci služby do trvalého úložiště.</span><span class="sxs-lookup"><span data-stu-id="b390d-222">What is left is a way to save the service instance to the persistent storage.</span></span> <span data-ttu-id="b390d-223">Jak bylo popsáno dříve, již existuje požadovaná funkce pro uložení stavu v `IStorageManager` implementaci.</span><span class="sxs-lookup"><span data-stu-id="b390d-223">As discussed previously, there is already the required functionality to save the state in an `IStorageManager` implementation.</span></span> <span data-ttu-id="b390d-224">Teď je potřeba ji integrovat s modulem runtime WCF.</span><span class="sxs-lookup"><span data-stu-id="b390d-224">We now must integrate this with the WCF runtime.</span></span> <span data-ttu-id="b390d-225">Je vyžadován jiný atribut, který platí pro metody ve třídě implementace služby.</span><span class="sxs-lookup"><span data-stu-id="b390d-225">Another attribute is required that is applicable to the methods in the service implementation class.</span></span> <span data-ttu-id="b390d-226">Tento atribut by měl být použit pro metody, které mění stav instance služby.</span><span class="sxs-lookup"><span data-stu-id="b390d-226">This attribute is supposed to be applied to the methods that change the state of the service instance.</span></span>

<span data-ttu-id="b390d-227">`SaveStateAttribute`Třída implementuje tuto funkci.</span><span class="sxs-lookup"><span data-stu-id="b390d-227">The `SaveStateAttribute` class implements this functionality.</span></span> <span data-ttu-id="b390d-228">Implementuje také `IOperationBehavior` třídu pro úpravu modulu runtime WCF pro každou operaci.</span><span class="sxs-lookup"><span data-stu-id="b390d-228">It also implements `IOperationBehavior` class to modify the WCF runtime for each operation.</span></span> <span data-ttu-id="b390d-229">Když je metoda označena pomocí tohoto atributu, modul runtime WCF vyvolá metodu, `ApplyBehavior` zatímco `DispatchOperation` je vytvořena vhodná.</span><span class="sxs-lookup"><span data-stu-id="b390d-229">When a method is marked with this attribute, the WCF runtime invokes the `ApplyBehavior` method while the appropriate `DispatchOperation` is being constructed.</span></span> <span data-ttu-id="b390d-230">V této implementaci metody je jeden řádek kódu:</span><span class="sxs-lookup"><span data-stu-id="b390d-230">There is a single line of code in this method implementation:</span></span>

```csharp
dispatch.Invoker = new OperationInvoker(dispatch.Invoker);
```

<span data-ttu-id="b390d-231">Tato instrukce vytvoří instanci `OperationInvoker` typu a přiřadí ji k `Invoker` vlastnosti objektu, který je `DispatchOperation` konstruován.</span><span class="sxs-lookup"><span data-stu-id="b390d-231">This instruction creates an instance of `OperationInvoker` type and assigns it to the `Invoker` property of the `DispatchOperation` being constructed.</span></span> <span data-ttu-id="b390d-232">`OperationInvoker`Třída je obálkou pro výchozí operaci původce vytvořenou pro `DispatchOperation` .</span><span class="sxs-lookup"><span data-stu-id="b390d-232">The `OperationInvoker` class is a wrapper for the default operation invoker created for the `DispatchOperation`.</span></span> <span data-ttu-id="b390d-233">Tato třída implementuje `IOperationInvoker` rozhraní.</span><span class="sxs-lookup"><span data-stu-id="b390d-233">This class implements the `IOperationInvoker` interface.</span></span> <span data-ttu-id="b390d-234">V `Invoke` implementaci metody je vlastní volání metody delegováno na původce vnitřní operace.</span><span class="sxs-lookup"><span data-stu-id="b390d-234">In the `Invoke` method implementation, the actual method invocation is delegated to the inner operation invoker.</span></span> <span data-ttu-id="b390d-235">Před vrácením výsledků však správce úložiště v nástroji slouží `InstanceContext` k uložení instance služby.</span><span class="sxs-lookup"><span data-stu-id="b390d-235">However, before returning the results the storage manager in the `InstanceContext` is used to save the service instance.</span></span>

```csharp
object result = innerOperationInvoker.Invoke(instance,
    inputs, out outputs);

// Save the instance using the storage manager saved in the
// current InstanceContext.
InstanceContextExtension extension =
    OperationContext.Current.InstanceContext.Extensions.Find<InstanceContextExtension>();

extension.StorageManager.SaveInstance(extension.ContextId, instance);
return result;
```

## <a name="using-the-extension"></a><span data-ttu-id="b390d-236">Použití rozšíření</span><span class="sxs-lookup"><span data-stu-id="b390d-236">Using the Extension</span></span>

<span data-ttu-id="b390d-237">Vrstva kanálu i rozšíření vrstvy modelu služby jsou hotové a dají se teď použít v aplikacích WCF.</span><span class="sxs-lookup"><span data-stu-id="b390d-237">Both the channel layer and service model layer extensions are done and they can now be used in WCF applications.</span></span> <span data-ttu-id="b390d-238">Služby musí kanál přidat do zásobníku kanálů pomocí vlastní vazby a pak označit třídy implementace služby příslušnými atributy.</span><span class="sxs-lookup"><span data-stu-id="b390d-238">Services must add the channel into the channel stack using a custom binding and then mark the service implementation classes with the appropriate attributes.</span></span>

```csharp
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

<span data-ttu-id="b390d-239">Klientské aplikace musí přidat DurableInstanceContextChannel do zásobníku kanálů pomocí vlastní vazby.</span><span class="sxs-lookup"><span data-stu-id="b390d-239">Client applications must add the DurableInstanceContextChannel into the channel stack using a custom binding.</span></span> <span data-ttu-id="b390d-240">Chcete-li konfigurovat kanál deklarativně v konfiguračním souboru, musí být oddíl elementu vazby přidán do kolekce rozšíření prvků vazby.</span><span class="sxs-lookup"><span data-stu-id="b390d-240">To configure the channel declaratively in the configuration file, the binding element section has to be added to the binding element extensions collection.</span></span>

```xml
<system.serviceModel>
 <extensions>
   <bindingElementExtensions>
     <add name="durableInstanceContext"
type="Microsoft.ServiceModel.Samples.DurableInstanceContextBindingElementSection, DurableInstanceContextExtension, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null"/>
   </bindingElementExtensions>
 </extensions>
</system.serviceModel>
```

<span data-ttu-id="b390d-241">Prvek vazby lze nyní použít s vlastní vazbou stejným způsobem jako jiné standardní prvky vazby:</span><span class="sxs-lookup"><span data-stu-id="b390d-241">Now the binding element can be used with a custom binding just like other standard binding elements:</span></span>

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

## <a name="conclusion"></a><span data-ttu-id="b390d-242">Závěr</span><span class="sxs-lookup"><span data-stu-id="b390d-242">Conclusion</span></span>

<span data-ttu-id="b390d-243">Tato ukázka ukázala, jak vytvořit vlastní kanál protokolu a jak přizpůsobit chování služby, abyste ho povolili.</span><span class="sxs-lookup"><span data-stu-id="b390d-243">This sample showed how to create a custom protocol channel and how to customize the service behavior to enable it.</span></span>

<span data-ttu-id="b390d-244">Rozšíření lze dále zlepšit tím, že uživatelům umožníte zadat `IStorageManager` implementaci pomocí konfiguračního oddílu.</span><span class="sxs-lookup"><span data-stu-id="b390d-244">The extension can be further improved by letting users specify the `IStorageManager` implementation using a configuration section.</span></span> <span data-ttu-id="b390d-245">Díky tomu je možné změnit záložní úložiště, aniž by bylo nutné znovu kompilovat kód služby.</span><span class="sxs-lookup"><span data-stu-id="b390d-245">This makes it possible to modify the backing store without recompiling the service code.</span></span>

<span data-ttu-id="b390d-246">Kromě toho můžete zkusit implementovat třídu (například `StateBag` ), která zapouzdřuje stav instance.</span><span class="sxs-lookup"><span data-stu-id="b390d-246">Furthermore you could try to implement a class (for example, `StateBag`), which encapsulates the state of the instance.</span></span> <span data-ttu-id="b390d-247">Tato třída zodpovídá za zachování stavu vždy, když se změní.</span><span class="sxs-lookup"><span data-stu-id="b390d-247">That class is responsible for persisting the state whenever it changes.</span></span> <span data-ttu-id="b390d-248">Tímto způsobem se můžete vyhnout použití `SaveState` atributu a přesnější provedení trvalé práce (například můžete zachovat stav při změně stavu, nikoli při každém jeho ukládání při každém volání metody s `SaveState` atributem).</span><span class="sxs-lookup"><span data-stu-id="b390d-248">This way you can avoid using the `SaveState` attribute and perform the persisting work more accurately (for example, you could persist the state when the state is actually changed rather than saving it each time when a method with the `SaveState` attribute is called).</span></span>

<span data-ttu-id="b390d-249">Při spuštění ukázky se zobrazí následující výstup.</span><span class="sxs-lookup"><span data-stu-id="b390d-249">When you run the sample, the following output is displayed.</span></span> <span data-ttu-id="b390d-250">Klient přidá do nákupního košíku dvě položky a pak ze služby získá seznam položek v rámci svého nákupního košíku.</span><span class="sxs-lookup"><span data-stu-id="b390d-250">The client adds two items to its shopping cart and then gets the list of items in its shopping cart from the service.</span></span> <span data-ttu-id="b390d-251">V každém okně konzoly stiskněte klávesu ENTER a ukončete službu a klienta.</span><span class="sxs-lookup"><span data-stu-id="b390d-251">Press ENTER in each console window to shut down the service and client.</span></span>

```console
Enter the name of the product: apples
Enter the name of the product: bananas

Shopping cart currently contains the following items.
apples
bananas
Press ENTER to shut down client
```

> [!NOTE]
> <span data-ttu-id="b390d-252">Opakované sestavení služby přepíše soubor databáze.</span><span class="sxs-lookup"><span data-stu-id="b390d-252">Rebuilding the service overwrites the database file.</span></span> <span data-ttu-id="b390d-253">Chcete-li sledovat stav zachované napříč několika spuštěními vzorku, nezapomeňte, že není nutné znovu sestavovat ukázku mezi spuštěními.</span><span class="sxs-lookup"><span data-stu-id="b390d-253">To observe state preserved across multiple runs of the sample, be sure not to rebuild the sample between runs.</span></span>

#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="b390d-254">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="b390d-254">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="b390d-255">Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="b390d-255">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="b390d-256">Při sestavování řešení postupujte podle pokynů v tématu [sestavování ukázek Windows Communication Foundation](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="b390d-256">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

3. <span data-ttu-id="b390d-257">Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="b390d-257">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>

> [!NOTE]
> <span data-ttu-id="b390d-258">Pro spuštění této ukázky musíte mít spuštěný SQL Server 2005 nebo SQL Express 2005.</span><span class="sxs-lookup"><span data-stu-id="b390d-258">You must be running SQL Server 2005 or SQL Express 2005 to run this sample.</span></span> <span data-ttu-id="b390d-259">Pokud používáte SQL Server 2005, musíte upravit konfiguraci připojovacího řetězce služby.</span><span class="sxs-lookup"><span data-stu-id="b390d-259">If you are running SQL Server 2005, you must modify the configuration of the service's connection string.</span></span> <span data-ttu-id="b390d-260">Při spuštění křížového počítače se SQL Server vyžaduje jenom na serverovém počítači.</span><span class="sxs-lookup"><span data-stu-id="b390d-260">When running cross-machine, SQL Server is only required on the server machine.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b390d-261">Ukázky už můžou být na vašem počítači nainstalované.</span><span class="sxs-lookup"><span data-stu-id="b390d-261">The samples may already be installed on your machine.</span></span> <span data-ttu-id="b390d-262">Než budete pokračovat, vyhledejte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="b390d-262">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="b390d-263">Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek.</span><span class="sxs-lookup"><span data-stu-id="b390d-263">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="b390d-264">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="b390d-264">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Instancing\Durable`
