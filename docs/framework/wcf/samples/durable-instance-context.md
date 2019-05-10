---
title: Trvanlivý kontext instance
ms.date: 03/30/2017
ms.assetid: 97bc2994-5a2c-47c7-927a-c4cd273153df
ms.openlocfilehash: 7c5b102313cc61b623d33056649c56fc236c9e79
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64650102"
---
# <a name="durable-instance-context"></a><span data-ttu-id="f7286-102">Trvanlivý kontext instance</span><span class="sxs-lookup"><span data-stu-id="f7286-102">Durable Instance Context</span></span>
<span data-ttu-id="f7286-103">Tento příklad ukazuje, jak přizpůsobit modul runtime Windows Communication Foundation (WCF) umožňuje trvalý instance kontexty.</span><span class="sxs-lookup"><span data-stu-id="f7286-103">This sample demonstrates how to customize the Windows Communication Foundation (WCF) runtime to enable durable instance contexts.</span></span> <span data-ttu-id="f7286-104">Jako svůj záložní úložiště (SQL Server 2005 Express v tomto případě) používá SQL Server 2005.</span><span class="sxs-lookup"><span data-stu-id="f7286-104">It uses SQL Server 2005 as its backing store (SQL Server 2005 Express in this case).</span></span> <span data-ttu-id="f7286-105">Ale také poskytuje způsob, jak přistupovat k mechanismy vlastního úložiště.</span><span class="sxs-lookup"><span data-stu-id="f7286-105">However, it also provides a way to access custom storage mechanisms.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f7286-106">Postup a sestavení pokynů pro tuto ukázku se nachází na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="f7286-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="f7286-107">Tento příklad zahrnuje rozšíření vrstvy kanálu a vrstva modelu služby WCF.</span><span class="sxs-lookup"><span data-stu-id="f7286-107">This sample involves extending both the channel layer and the service model layer of the WCF.</span></span> <span data-ttu-id="f7286-108">Proto je potřeba pochopit základní koncepty před přechodem k podrobnostem implementace.</span><span class="sxs-lookup"><span data-stu-id="f7286-108">Therefore it is necessary to understand the underlying concepts before going into the implementation details.</span></span>  
  
 <span data-ttu-id="f7286-109">Kontexty trvalý instance najdete ve skutečných scénářích velmi často.</span><span class="sxs-lookup"><span data-stu-id="f7286-109">Durable instance contexts can be found in the real world scenarios quite often.</span></span> <span data-ttu-id="f7286-110">Nákupní košík aplikaci například má schopnost pozastavit nákupní uprostřed prostřednictvím a pokračovat na další den.</span><span class="sxs-lookup"><span data-stu-id="f7286-110">A shopping cart application for example, has the ability to pause shopping halfway through and continue it on another day.</span></span> <span data-ttu-id="f7286-111">Takže pokud používáte nákupního košíku dalšího dne, naše původního kontextu se obnoví.</span><span class="sxs-lookup"><span data-stu-id="f7286-111">So that when we visit the shopping cart the next day, our original context is restored.</span></span> <span data-ttu-id="f7286-112">Je důležité si uvědomit, že aplikaci nákupního košíku (na serveru) nespravuje nákupního košíku instance odpojené jsme se.</span><span class="sxs-lookup"><span data-stu-id="f7286-112">It is important to note that the shopping cart application (on the server) does not maintain the shopping cart instance while we are disconnected.</span></span> <span data-ttu-id="f7286-113">Místo toho uchovává stavu do trvalého úložiště médií a používá se při vytváření nové instance pro obnovený kontext.</span><span class="sxs-lookup"><span data-stu-id="f7286-113">Instead, it persists its state into a durable storage media and uses it when constructing a new instance for the restored context.</span></span> <span data-ttu-id="f7286-114">Proto instance služby, která může obsluhovat pro stejný kontext není stejný jako předchozí instanci (to znamená, nemá stejnou adresu paměti).</span><span class="sxs-lookup"><span data-stu-id="f7286-114">Therefore the service instance that may service for the same context is not the same as the previous instance (that is, it does not have the same memory address).</span></span>  
  
 <span data-ttu-id="f7286-115">Trvanlivý kontext instance je možné díky malé protokol, který vyměňuje ID kontextu mezi klientem a službou.</span><span class="sxs-lookup"><span data-stu-id="f7286-115">Durable instance context is made possible by a small protocol that exchanges a context ID between the client and service.</span></span> <span data-ttu-id="f7286-116">Toto ID kontextu je vytvořen na straně klienta a do služby.</span><span class="sxs-lookup"><span data-stu-id="f7286-116">This context ID is created on the client and transmitted to the service.</span></span> <span data-ttu-id="f7286-117">Při vytvoření instance služby je modul runtime služby se pokouší načíst trvalého stavu, který odpovídá toto ID kontextu z trvalého úložiště (ve výchozím nastavení je databáze systému SQL Server 2005).</span><span class="sxs-lookup"><span data-stu-id="f7286-117">When the service instance is created, the service runtime tries to load the persisted state that corresponds to this context ID from a persistent storage (by default it is a SQL Server 2005 database).</span></span> <span data-ttu-id="f7286-118">Pokud je k dispozici žádný stav má novou instanci výchozího stavu.</span><span class="sxs-lookup"><span data-stu-id="f7286-118">If no state is available the new instance has its default state.</span></span> <span data-ttu-id="f7286-119">Implementace služby používá k označení operace, které změní stav implementace služby tak, aby modul runtime můžete uložit instanci služby po vyvolání je vlastní atribut.</span><span class="sxs-lookup"><span data-stu-id="f7286-119">The service implementation uses a custom attribute to mark operations that change the state of the service implementation so that the runtime can save the service instance after invoking them.</span></span>  
  
 <span data-ttu-id="f7286-120">Podle předchozího popisu lze dva kroky snadno rozlišit k dosažení cíle:</span><span class="sxs-lookup"><span data-stu-id="f7286-120">By the previous description, two steps can easily be distinguished to achieve the goal:</span></span>  
  
1. <span data-ttu-id="f7286-121">Změňte zprávu, která přejde na lince provádět ID kontextu.</span><span class="sxs-lookup"><span data-stu-id="f7286-121">Change the message that goes on the wire to carry the context ID.</span></span>  
  
2. <span data-ttu-id="f7286-122">Místní chování služby k implementaci vlastní logiky vytvoření instance změňte.</span><span class="sxs-lookup"><span data-stu-id="f7286-122">Change the service local behavior to implement custom instancing logic.</span></span>  
  
 <span data-ttu-id="f7286-123">Vzhledem k tomu, že první z nich v seznamu ovlivňuje zpráv na lince by měla být implementována jako vlastního kanálu a připojili k vrstvě kanálu.</span><span class="sxs-lookup"><span data-stu-id="f7286-123">Because the first one in the list affects the messages on the wire it should be implemented as a custom channel and be hooked up to the channel layer.</span></span> <span data-ttu-id="f7286-124">Druhá možnost se týká pouze místní chování služby a proto může být implementována rozšíření několik bodů rozšiřitelnosti služby.</span><span class="sxs-lookup"><span data-stu-id="f7286-124">The latter only affects the service local behavior and therefore can be implemented by extending several service extensibility points.</span></span> <span data-ttu-id="f7286-125">V následujících částech jsou popsány každý z těchto rozšíření.</span><span class="sxs-lookup"><span data-stu-id="f7286-125">In the next few sections, each of these extensions are discussed.</span></span>  
  
## <a name="durable-instancecontext-channel"></a><span data-ttu-id="f7286-126">Kanál kontextu InstanceContext durable</span><span class="sxs-lookup"><span data-stu-id="f7286-126">Durable InstanceContext Channel</span></span>  
 <span data-ttu-id="f7286-127">První věc, kterou si prohlédnout je rozšíření vrstvy kanálu.</span><span class="sxs-lookup"><span data-stu-id="f7286-127">The first thing to look at is a channel layer extension.</span></span> <span data-ttu-id="f7286-128">Prvním krokem při psaní vlastního kanálu je rozhodnout strukturu komunikační kanál.</span><span class="sxs-lookup"><span data-stu-id="f7286-128">The first step in writing a custom channel is to decide the communication structure of the channel.</span></span> <span data-ttu-id="f7286-129">Jak je uvedena nová přenosový protokol kanálu by měla fungovat s téměř jakémkoli jiném kanálu v zásobníku kanálu.</span><span class="sxs-lookup"><span data-stu-id="f7286-129">As a new wire protocol is being introduced the channel should work with almost any other channel in the channel stack.</span></span> <span data-ttu-id="f7286-130">Proto má podporovat všechny vzorky zprávy exchange.</span><span class="sxs-lookup"><span data-stu-id="f7286-130">Therefore it should support all the message exchange patterns.</span></span> <span data-ttu-id="f7286-131">Základní funkce kanálu je však stejný bez ohledu na jeho strukturu komunikace.</span><span class="sxs-lookup"><span data-stu-id="f7286-131">However, the core functionality of the channel is the same regardless of its communication structure.</span></span> <span data-ttu-id="f7286-132">Přesněji řečeno z klienta by měl zápis ID kontextu do zprávy a ze služby by toto ID kontextu četlo zprávy a předejte jej do vyšší úrovně.</span><span class="sxs-lookup"><span data-stu-id="f7286-132">More specifically, from the client it should write the context ID to the messages and from the service it should read this context ID from the messages and pass it to the upper levels.</span></span> <span data-ttu-id="f7286-133">Proto `DurableInstanceContextChannelBase` je vytvořená třída, která slouží jako abstraktní základní třída pro všechny implementace kanálu kontextu trvalé instanci.</span><span class="sxs-lookup"><span data-stu-id="f7286-133">Because of that, a `DurableInstanceContextChannelBase` class is created that acts as the abstract base class for all durable instance context channel implementations.</span></span> <span data-ttu-id="f7286-134">Tato třída obsahuje běžným funkcím správy stavu počítače a dvou chráněné členy pro použití a přečtěte si informace o kontextu do a ze zprávy.</span><span class="sxs-lookup"><span data-stu-id="f7286-134">This class contains the common state machine management functions and two protected members to apply and read the context information to and from messages.</span></span>  
  
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
  
 <span data-ttu-id="f7286-135">Tyto dvě metody využívání `IContextManager` implementace pro zápis a čtení ID kontextu do nebo ze zprávy.</span><span class="sxs-lookup"><span data-stu-id="f7286-135">These two methods make use of `IContextManager` implementations to write and read the context ID to or from the message.</span></span> <span data-ttu-id="f7286-136">(`IContextManager` je vlastní rozhraní používá k definování kontraktů pro všechny místní správce.) Kanál může obsahovat buď ID kontextu, v záhlaví SOAP, které vlastní nebo v hlavičce souboru cookie HTTP.</span><span class="sxs-lookup"><span data-stu-id="f7286-136">(`IContextManager` is a custom interface used to define the contract for all context managers.) The channel can either include the context ID in a custom SOAP header or in a HTTP cookie header.</span></span> <span data-ttu-id="f7286-137">Každá implementace správce kontextu dědí z `ContextManagerBase` třídu, která obsahuje běžné funkce pro všechny správce kontextu.</span><span class="sxs-lookup"><span data-stu-id="f7286-137">Each context manager implementation inherits from the `ContextManagerBase` class that contains the common functionality for all context managers.</span></span> <span data-ttu-id="f7286-138">`GetContextId` Metody této třídy se používá k pocházejí z ID kontextové z klienta.</span><span class="sxs-lookup"><span data-stu-id="f7286-138">The `GetContextId` method in this class is used to originate the context ID from the client.</span></span> <span data-ttu-id="f7286-139">Když kontextu, který je ID pochází poprvé, tato metoda uloží ho do textového souboru, jehož název je vytvářený adresu vzdáleného koncového bodu (neplatné znaky názvu souboru v typické identifikátory URI jsou nahrazeny @ znaků).</span><span class="sxs-lookup"><span data-stu-id="f7286-139">When a context ID is originated for the first time, this method saves it into a text file whose name is constructed by the remote endpoint address (the invalid file name characters in the typical URIs are replaced with @ characters).</span></span>  
  
 <span data-ttu-id="f7286-140">Později je vyžadováno pro stejný koncový bod vzdáleného ID kontextu, zkontroluje, zda existuje příslušný soubor.</span><span class="sxs-lookup"><span data-stu-id="f7286-140">Later when the context ID is required for the same remote endpoint, it checks whether an appropriate file exists.</span></span> <span data-ttu-id="f7286-141">Pokud ano, přečte ID kontextu a vrátí.</span><span class="sxs-lookup"><span data-stu-id="f7286-141">If it does, it reads the context ID and returns.</span></span> <span data-ttu-id="f7286-142">V opačném případě vrátí ID nově generovaným kontextem a uloží jej do souboru.</span><span class="sxs-lookup"><span data-stu-id="f7286-142">Otherwise it returns a newly generated context ID and saves it to a file.</span></span> <span data-ttu-id="f7286-143">Ve výchozí konfiguraci tyto soubory jsou umístěny v adresáři s názvem ContextStore, který je umístěný v adresáři temp aktuálního uživatele.</span><span class="sxs-lookup"><span data-stu-id="f7286-143">With the default configuration, these files are placed in a directory called ContextStore, which resides in the current user’s temp directory.</span></span> <span data-ttu-id="f7286-144">Ale toto umístění je možné konfigurovat pomocí elementu vazby.</span><span class="sxs-lookup"><span data-stu-id="f7286-144">However this location is configurable using the binding element.</span></span>  
  
 <span data-ttu-id="f7286-145">Mechanismus, který se používá k přenosu ID kontextu je možné konfigurovat.</span><span class="sxs-lookup"><span data-stu-id="f7286-145">The mechanism used to transport the context ID is configurable.</span></span> <span data-ttu-id="f7286-146">To může být buď napsaná hlavičky souborů cookie protokolu HTTP nebo vlastní hlavičky SOAP.</span><span class="sxs-lookup"><span data-stu-id="f7286-146">It could be either written to the HTTP cookie header or to a custom SOAP header.</span></span> <span data-ttu-id="f7286-147">Vlastní přístup záhlaví SOAP umožňuje tento protokol pomocí jiných protokolů než HTTP (například TCP nebo pojmenované kanály).</span><span class="sxs-lookup"><span data-stu-id="f7286-147">The custom SOAP header approach makes it possible to use this protocol with non-HTTP protocols (for example, TCP or Named Pipes).</span></span> <span data-ttu-id="f7286-148">Existují dvě třídy, a to `MessageHeaderContextManager` a `HttpCookieContextManager`, který implementovat tyto dvě možnosti.</span><span class="sxs-lookup"><span data-stu-id="f7286-148">There are two classes, namely `MessageHeaderContextManager` and `HttpCookieContextManager`, which implement these two options.</span></span>  
  
 <span data-ttu-id="f7286-149">Jejich zapsat kontextu ID zprávy odpovídajícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="f7286-149">Both of them write the context ID to the message appropriately.</span></span> <span data-ttu-id="f7286-150">Například `MessageHeaderContextManager` zapíše do záhlaví SOAP ve třídě `WriteContext` metoda.</span><span class="sxs-lookup"><span data-stu-id="f7286-150">For example, the `MessageHeaderContextManager` class writes it to a SOAP header in the `WriteContext` method.</span></span>  
  
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
  
 <span data-ttu-id="f7286-151">Jak `ApplyContext` a `ReadContextId` metody v `DurableInstanceContextChannelBase` vyvolání třídy `IContextManager.ReadContext` a `IContextManager.WriteContext`v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="f7286-151">Both the `ApplyContext` and `ReadContextId` methods in the `DurableInstanceContextChannelBase` class invoke the `IContextManager.ReadContext` and `IContextManager.WriteContext`, respectively.</span></span> <span data-ttu-id="f7286-152">Ale tyto místní správci nejsou vytvořené přímo `DurableInstanceContextChannelBase` třídy.</span><span class="sxs-lookup"><span data-stu-id="f7286-152">However, these context managers are not directly created by the `DurableInstanceContextChannelBase` class.</span></span> <span data-ttu-id="f7286-153">Místo toho používá `ContextManagerFactory` třídě, aby provedl tuto úlohu.</span><span class="sxs-lookup"><span data-stu-id="f7286-153">Instead it uses the `ContextManagerFactory` class to do that job.</span></span>  
  
```  
IContextManager contextManager =  
                ContextManagerFactory.CreateContextManager(contextType,   
                this.contextStoreLocation,   
                this.endpointAddress);  
```  
  
 <span data-ttu-id="f7286-154">`ApplyContext` Vyvolá metodu odesílajícího kanály.</span><span class="sxs-lookup"><span data-stu-id="f7286-154">The `ApplyContext` method is invoked by the sending channels.</span></span> <span data-ttu-id="f7286-155">Ho vkládá ID kontextu pro odchozí zprávy.</span><span class="sxs-lookup"><span data-stu-id="f7286-155">It injects the context ID to the outgoing messages.</span></span> <span data-ttu-id="f7286-156">`ReadContextId` Vyvolá metoda přijímající kanály.</span><span class="sxs-lookup"><span data-stu-id="f7286-156">The `ReadContextId` method is invoked by the receiving channels.</span></span> <span data-ttu-id="f7286-157">Tato metoda zajišťuje, že ID kontextu je k dispozici v příchozích zprávách a přidá jej do `Properties` kolekce `Message` třídy.</span><span class="sxs-lookup"><span data-stu-id="f7286-157">This method ensures that the context ID is available in the incoming messages and adds it to the `Properties` collection of the `Message` class.</span></span> <span data-ttu-id="f7286-158">Také vyvolá výjimku `CommunicationException` v případě selhání přečíst ID kontextu a proto způsobí, že kanál ho.</span><span class="sxs-lookup"><span data-stu-id="f7286-158">It also throws a `CommunicationException` in case of a failure to read the context ID and thus causes the channel to be aborted.</span></span>  
  
```  
message.Properties.Add(DurableInstanceContextUtility.ContextIdProperty, contextId);  
```  
  
 <span data-ttu-id="f7286-159">Než budete pokračovat, je důležité porozumět využití `Properties` kolekce `Message` třídy.</span><span class="sxs-lookup"><span data-stu-id="f7286-159">Before proceeding, it is important to understand the usage of the `Properties` collection in the `Message` class.</span></span> <span data-ttu-id="f7286-160">Obvykle to `Properties` kolekce se používá při předání dat z snížit na vyšší úrovně z vrstvy kanálu.</span><span class="sxs-lookup"><span data-stu-id="f7286-160">Typically, this `Properties` collection is used when passing data from lower to the upper levels from the channel layer.</span></span> <span data-ttu-id="f7286-161">Tímto způsobem požadovaná data je možné poskytnout vyšší úrovně konzistentním způsobem bez ohledu na podrobnosti protokolu.</span><span class="sxs-lookup"><span data-stu-id="f7286-161">This way the desired data can be provided to the upper levels in a consistent manner regardless of the protocol details.</span></span> <span data-ttu-id="f7286-162">Jinými slovy vrstvy kanálu můžete odesílat a přijímat ID kontextu jako záhlaví SOAP nebo Hlavička cookie HTTP.</span><span class="sxs-lookup"><span data-stu-id="f7286-162">In other words, the channel layer can send and receive the context ID either as a SOAP header or a HTTP cookie header.</span></span> <span data-ttu-id="f7286-163">Ale to není nezbytné pro vyšší úrovně vědět o tyto podrobnosti, protože vrstvy kanálu zpřístupňuje tyto informace v `Properties` kolekce.</span><span class="sxs-lookup"><span data-stu-id="f7286-163">But it is not necessary for the upper levels to know about these details because the channel layer makes this information available in the `Properties` collection.</span></span>  
  
 <span data-ttu-id="f7286-164">Teď se `DurableInstanceContextChannelBase` třídy v místě všech deset rozhraní nezbytné (IOutputChannel IInputChannel, IOutputSessionChannel, IInputSessionChannel, třídu IRequestChannel, IReplyChannel, IRequestSessionChannel, IReplySessionChannel, Musí být implementované IDuplexChannel, IDuplexSessionChannel).</span><span class="sxs-lookup"><span data-stu-id="f7286-164">Now with the `DurableInstanceContextChannelBase` class in place all ten of the necessary interfaces (IOutputChannel, IInputChannel, IOutputSessionChannel, IInputSessionChannel, IRequestChannel, IReplyChannel, IRequestSessionChannel, IReplySessionChannel, IDuplexChannel, IDuplexSessionChannel) must be implemented.</span></span> <span data-ttu-id="f7286-165">Se podobají každý vzoru výměny zpráv k dispozici (datagramu, simplexně, duplexní režim a jejich s relacemi varianty).</span><span class="sxs-lookup"><span data-stu-id="f7286-165">They resemble every available message exchange pattern (datagram, simplex, duplex and their sessionful variants).</span></span> <span data-ttu-id="f7286-166">Každá z těchto implementací základní třídy výše popsaný a volání Zdědit `ApplyContext` a `ReadContexId` odpovídajícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="f7286-166">Each of these implementations inherit the base class previously described and calls `ApplyContext` and `ReadContexId` appropriately.</span></span> <span data-ttu-id="f7286-167">Například `DurableInstanceContextOutputChannel` – který implementuje rozhraní IOutputChannel – zavolá `ApplyContext` metoda z každé metody, která odesílá zprávy.</span><span class="sxs-lookup"><span data-stu-id="f7286-167">For example, `DurableInstanceContextOutputChannel` - which implements the IOutputChannel interface - calls the `ApplyContext` method from each method that sends the messages.</span></span>  
  
```  
public void Send(Message message, TimeSpan timeout)  
{  
    // Apply the context information before sending the message.  
    this.ApplyContext(message);  
    //…  
}   
```  
  
 <span data-ttu-id="f7286-168">Na druhé straně `DurableInstanceContextInputChannel` – která implementuje `IInputChannel` rozhraní - volání `ReadContextId` metoda v každé metodě, která přijímá zprávy.</span><span class="sxs-lookup"><span data-stu-id="f7286-168">On the other hand, `DurableInstanceContextInputChannel` - which implements the `IInputChannel` interface - calls the `ReadContextId` method in each method which receives the messages.</span></span>  
  
```  
public Message Receive(TimeSpan timeout)  
{  
    //…  
      ReadContextId(message);  
      return message;  
}  
```  
  
 <span data-ttu-id="f7286-169">Kromě toho tyto implementace kanálu delegáta volání metod na kanál pod nimi v zásobníku kanálu.</span><span class="sxs-lookup"><span data-stu-id="f7286-169">Apart from this, these channel implementations delegate the method invocations to the channel below them in the channel stack.</span></span> <span data-ttu-id="f7286-170">S relacemi varianty však mít základní logiku, abyste měli jistotu, že ID kontextu se odesílají a je pro čtení jenom pro první zprávu, která způsobí, že relace, který se má vytvořit.</span><span class="sxs-lookup"><span data-stu-id="f7286-170">However, sessionful variants have a basic logic to make sure that the context ID is sent and is read only for the first message that causes the session to be created.</span></span>  
  
```  
if (isFirstMessage)  
{  
//…  
    this.ApplyContext(message);  
    isFirstMessage = false;  
}  
```  
  
 <span data-ttu-id="f7286-171">Tyto implementace kanálu se pak přidá do modulu runtime kanál WCF `DurableInstanceContextBindingElement` třídy a `DurableInstanceContextBindingElementSection` třídy odpovídajícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="f7286-171">These channel implementations are then added to the WCF channel runtime by the `DurableInstanceContextBindingElement` class and `DurableInstanceContextBindingElementSection` class appropriately.</span></span> <span data-ttu-id="f7286-172">Zobrazit [HttpCookieSession](../../../../docs/framework/wcf/samples/httpcookiesession.md) ukázková dokumentace pro další podrobnosti o elementů vazby a oddíly elementů vazby kanálu.</span><span class="sxs-lookup"><span data-stu-id="f7286-172">See the [HttpCookieSession](../../../../docs/framework/wcf/samples/httpcookiesession.md) channel sample documentation for more details about binding elements and binding element sections.</span></span>  
  
## <a name="service-model-layer-extensions"></a><span data-ttu-id="f7286-173">Rozšíření modelu vrstvy služeb</span><span class="sxs-lookup"><span data-stu-id="f7286-173">Service Model Layer Extensions</span></span>  
 <span data-ttu-id="f7286-174">Teď, když má ID kontextu přenést přes kanál vrstvu, je možné implementovat chování služby k přizpůsobení instance.</span><span class="sxs-lookup"><span data-stu-id="f7286-174">Now that the context ID has traveled through the channel layer, the service behavior can be implemented to customize the instantiation.</span></span> <span data-ttu-id="f7286-175">V této ukázce Správce úložiště slouží k načtení a uložení stavu z nebo do trvalého úložiště.</span><span class="sxs-lookup"><span data-stu-id="f7286-175">In this sample, a storage manager is used to load and save state from or to the persistent store.</span></span> <span data-ttu-id="f7286-176">Jak jsme vysvětlili dříve, tato ukázka poskytuje správce úložiště, který používá SQL Server 2005 jako svůj záložní úložiště.</span><span class="sxs-lookup"><span data-stu-id="f7286-176">As explained previously, this sample provides a storage manager that uses SQL Server 2005 as its backing store.</span></span> <span data-ttu-id="f7286-177">Je však také možné přidat vlastní úložiště mechanismy pro toto rozšíření.</span><span class="sxs-lookup"><span data-stu-id="f7286-177">However, it is also possible to add custom storage mechanisms to this extension.</span></span> <span data-ttu-id="f7286-178">K tomu veřejného rozhraní je teď deklarována, který musí implementovat všechny správce úložiště.</span><span class="sxs-lookup"><span data-stu-id="f7286-178">To do that a public interface is declared, which must be implemented by all storage managers.</span></span>  
  
```  
public interface IStorageManager  
{  
    object GetInstance(string contextId, Type type);  
    void SaveInstance(string contextId, object state);  
}  
```  
  
 <span data-ttu-id="f7286-179">`SqlServerStorageManager` Třída obsahuje výchozí `IStorageManager` implementace.</span><span class="sxs-lookup"><span data-stu-id="f7286-179">The `SqlServerStorageManager` class contains the default `IStorageManager` implementation.</span></span> <span data-ttu-id="f7286-180">V jeho `SaveInstance` metoda daný objekt serializován pomocí třídy XmlSerializer a je uložen do databáze SQL serveru.</span><span class="sxs-lookup"><span data-stu-id="f7286-180">In its `SaveInstance` method the given object is serialized using the XmlSerializer and is saved to the SQL Server database.</span></span>  
  
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
  
 <span data-ttu-id="f7286-181">V `GetInstance` metoda serializovaných dat je pro čtení pro daný kontext ID a přiřazený objekt vytvořený z něj je vrátit zpět volajícímu.</span><span class="sxs-lookup"><span data-stu-id="f7286-181">In the `GetInstance` method the serialized data is read for a given context ID and the object constructed from it is returned to the caller.</span></span>  
  
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
  
 <span data-ttu-id="f7286-182">Uživatelé těchto úložiště správce neměl konkretizovat přímo.</span><span class="sxs-lookup"><span data-stu-id="f7286-182">Users of these storage managers are not supposed to instantiate them directly.</span></span> <span data-ttu-id="f7286-183">Používají `StorageManagerFactory` třídy, který abstrahuje od podrobnosti o vytvoření Správce úložiště.</span><span class="sxs-lookup"><span data-stu-id="f7286-183">They use the `StorageManagerFactory` class, which abstracts from the storage manager creation details.</span></span> <span data-ttu-id="f7286-184">Tato třída obsahuje jeden statický člen `GetStorageManager`, která vytvoří instanci typu správce daného úložiště.</span><span class="sxs-lookup"><span data-stu-id="f7286-184">This class has one static member, `GetStorageManager`, which creates an instance of a given storage manager type.</span></span> <span data-ttu-id="f7286-185">Pokud je parametr typu `null`, tato metoda vytvoří instanci výchozí `SqlServerStorageManager` třídy a vrátí jej.</span><span class="sxs-lookup"><span data-stu-id="f7286-185">If the type parameter is `null`, this method creates an instance of the default `SqlServerStorageManager` class and returns it.</span></span> <span data-ttu-id="f7286-186">Také ověří daného typu, abyste měli jistotu, že implementuje `IStorageManager` rozhraní.</span><span class="sxs-lookup"><span data-stu-id="f7286-186">It also validates the given type to make sure that it implements the `IStorageManager` interface.</span></span>  
  
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
  
 <span data-ttu-id="f7286-187">Je implementován potřebnou infrastrukturu pro čtení a zápis instance z trvalého úložiště.</span><span class="sxs-lookup"><span data-stu-id="f7286-187">The necessary infrastructure to read and write instances from the persistent storage is implemented.</span></span> <span data-ttu-id="f7286-188">Teď mají nezbytné kroky, chcete-li změnit chování služby mají být provedeny.</span><span class="sxs-lookup"><span data-stu-id="f7286-188">Now the necessary steps to change the service behavior have to be taken.</span></span>  
  
 <span data-ttu-id="f7286-189">Prvním krokem tohoto procesu máme uložte kontextu ID, které pochází z vrstvy kanálu na aktuálním kontextu InstanceContext.</span><span class="sxs-lookup"><span data-stu-id="f7286-189">As the first step of this process we have to save the context ID, which came through the channel layer to the current InstanceContext.</span></span> <span data-ttu-id="f7286-190">Třída InstanceContext je součástí modulu runtime, který slouží jako propojení mezi dispečer WCF a instance služby.</span><span class="sxs-lookup"><span data-stu-id="f7286-190">InstanceContext is a runtime component that acts as the link between the WCF dispatcher and the service instance.</span></span> <span data-ttu-id="f7286-191">Je možné poskytnout další stav a chování v instanci služby.</span><span class="sxs-lookup"><span data-stu-id="f7286-191">It can be used to provide additional state and behavior to the service instance.</span></span> <span data-ttu-id="f7286-192">To je nezbytné, protože při komunikaci s relacemi je odesláno ID kontext pouze s první zprávou.</span><span class="sxs-lookup"><span data-stu-id="f7286-192">This is essential because in sessionful communication the context ID is sent only with the first message.</span></span>  
  
 <span data-ttu-id="f7286-193">WCF umožňuje rozšíření komponenty modulu runtime InstanceContext tak, že přidáte nový stav a chování pomocí způsobu rozšiřitelném objektu.</span><span class="sxs-lookup"><span data-stu-id="f7286-193">WCF allows extending its InstanceContext runtime component by adding a new state and behavior using its extensible object pattern.</span></span> <span data-ttu-id="f7286-194">Vzor rozšiřitelném objektu se používá ve službě WCF buď rozšířit existující třídy modulu runtime s novými funkcemi nebo přidávání nových funkcí stavu k objektu.</span><span class="sxs-lookup"><span data-stu-id="f7286-194">The extensible object pattern is used in WCF to either extend existing runtime classes with new functionality or to add new state features to an object.</span></span> <span data-ttu-id="f7286-195">Existují tři rozhraní ve vzoru extensible object - IExtensibleObject\<T >, IExtension\<T > a IExtensionCollection\<T >:</span><span class="sxs-lookup"><span data-stu-id="f7286-195">There are three interfaces in the extensible object pattern - IExtensibleObject\<T>, IExtension\<T>, and IExtensionCollection\<T>:</span></span>  
  
- <span data-ttu-id="f7286-196">IExtensibleObject\<T > rozhraní implementují objekty, které umožňují rozšíření, která přizpůsobit jejich funkce.</span><span class="sxs-lookup"><span data-stu-id="f7286-196">The IExtensibleObject\<T> interface is implemented by objects that allow extensions that customize their functionality.</span></span>  
  
- <span data-ttu-id="f7286-197">IExtension\<T > rozhraní implementují objekty, které jsou rozšíření třídy typu T.</span><span class="sxs-lookup"><span data-stu-id="f7286-197">The IExtension\<T> interface is implemented by objects that are extensions of classes of type T.</span></span>  
  
- <span data-ttu-id="f7286-198">IExtensionCollection\<T > rozhraní je kolekce IExtensions, který umožňuje načítání IExtensions podle jejich typu.</span><span class="sxs-lookup"><span data-stu-id="f7286-198">The IExtensionCollection\<T> interface is a collection of IExtensions that allows for retrieving IExtensions by their type.</span></span>  
  
 <span data-ttu-id="f7286-199">Proto třídu InstanceContextExtension by měl být vytvořen, který implementuje rozhraní IExtension a definuje požadovaný stav uložení ID kontextu.</span><span class="sxs-lookup"><span data-stu-id="f7286-199">Therefore an InstanceContextExtension class should be created that implements the IExtension interface and defines the required state to save the context ID.</span></span> <span data-ttu-id="f7286-200">Tato třída rovněž poskytuje stavu k uložení úložiště správce používá.</span><span class="sxs-lookup"><span data-stu-id="f7286-200">This class also provides the state to hold the storage manager being used.</span></span> <span data-ttu-id="f7286-201">Po uložení nového stavu by neměla být možné jej upravit.</span><span class="sxs-lookup"><span data-stu-id="f7286-201">Once the new state is saved, it should not be possible to modify it.</span></span> <span data-ttu-id="f7286-202">Stav je proto k dispozici a uloží do instance v době, kdy je právě vytvořený a pak dostupná jenom pomocí vlastnosti jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="f7286-202">Therefore the state is provided and saved to the instance at the time it is being constructed and then only accessible using read-only properties.</span></span>  
  
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
  
 <span data-ttu-id="f7286-203">InstanceContextInitializer třída implementuje rozhraní IInstanceContextInitializer a přidá do kolekce rozšíření kontextu InstanceContext vytváří rozšíření místní instance.</span><span class="sxs-lookup"><span data-stu-id="f7286-203">The InstanceContextInitializer class implements the IInstanceContextInitializer interface and adds the instance context extension to the Extensions collection of the InstanceContext being constructed.</span></span>  
  
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
  
 <span data-ttu-id="f7286-204">Jak bylo popsáno dříve ID kontextu je číst z `Properties` kolekce `Message` třídy a předat konstruktoru třídy rozšíření.</span><span class="sxs-lookup"><span data-stu-id="f7286-204">As described earlier the context ID is read from the `Properties` collection of the `Message` class and passed to the constructor of the extension class.</span></span> <span data-ttu-id="f7286-205">Tento příklad ukazuje, jak nelze vyměňovat informace mezi vrstvami konzistentním způsobem.</span><span class="sxs-lookup"><span data-stu-id="f7286-205">This demonstrates how information can be exchanged between the layers in a consistent manner.</span></span>  
  
 <span data-ttu-id="f7286-206">Dalším důležitým krokem přepisuje proces vytvoření instance služby.</span><span class="sxs-lookup"><span data-stu-id="f7286-206">The next important step is overriding the service instance creation process.</span></span> <span data-ttu-id="f7286-207">WCF umožňuje implementovat vlastní instance chování a zapojení do modulu runtime pomocí IInstanceProvider rozhraní.</span><span class="sxs-lookup"><span data-stu-id="f7286-207">WCF allows implementing custom instantiation behaviors and hooking them up to the runtime using the IInstanceProvider interface.</span></span> <span data-ttu-id="f7286-208">Nové `InstanceProvider` třídy je implementováno s cílem provést tuto úlohu.</span><span class="sxs-lookup"><span data-stu-id="f7286-208">The new `InstanceProvider` class is implemented to do that job.</span></span> <span data-ttu-id="f7286-209">V konstruktoru je přijat typ služby očekává od instance zprostředkovatele.</span><span class="sxs-lookup"><span data-stu-id="f7286-209">In the constructor the service type expected from the instance provider is accepted.</span></span> <span data-ttu-id="f7286-210">Později to slouží k vytvoření nové instance.</span><span class="sxs-lookup"><span data-stu-id="f7286-210">Later this is used to create new instances.</span></span> <span data-ttu-id="f7286-211">V `GetInstance` implementace Správce úložiště je vytvořena instance hledáte trvalé instanci.</span><span class="sxs-lookup"><span data-stu-id="f7286-211">In the `GetInstance` implementation an instance of a storage manager is created looking for a persisted instance.</span></span> <span data-ttu-id="f7286-212">Vrátí-li `null` novou instanci daného typu služby je vytvořena instance a vrátit zpět volajícímu.</span><span class="sxs-lookup"><span data-stu-id="f7286-212">If it returns `null` then a new instance of the service type is instantiated and returned to the caller.</span></span>  
  
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
  
 <span data-ttu-id="f7286-213">Dalším důležitým krokem je instalace `InstanceContextExtension`, `InstanceContextInitializer` a `InstanceProvider` třídy do modulu runtime service model.</span><span class="sxs-lookup"><span data-stu-id="f7286-213">The next important step is to install the `InstanceContextExtension`, `InstanceContextInitializer` and `InstanceProvider` classes into the service model runtime.</span></span> <span data-ttu-id="f7286-214">Vlastní atribut může použít k označení třídy implementace služby k instalaci chování.</span><span class="sxs-lookup"><span data-stu-id="f7286-214">A custom attribute could be used to mark the service implementation classes to install the behavior.</span></span> <span data-ttu-id="f7286-215">`DurableInstanceContextAttribute` Obsahuje implementaci pro tento atribut a implementuje `IServiceBehavior` rozhraní pro rozšíření modulu runtime celé služby.</span><span class="sxs-lookup"><span data-stu-id="f7286-215">The `DurableInstanceContextAttribute` contains the implementation for this attribute and it implements the `IServiceBehavior` interface to extend the entire service runtime.</span></span>  
  
 <span data-ttu-id="f7286-216">Tato třída obsahuje vlastnosti, která přijímá typ Správce úložiště, který se má použít.</span><span class="sxs-lookup"><span data-stu-id="f7286-216">This class has a property that accepts the type of the storage manager to be used.</span></span> <span data-ttu-id="f7286-217">Tímto způsobem implementace umožňuje uživatelům zadat vlastní `IStorageManager` implementace jako parametr tohoto atributu.</span><span class="sxs-lookup"><span data-stu-id="f7286-217">In this way the implementation enables the users to specify their own `IStorageManager` implementation as parameter of this attribute.</span></span>  
  
 <span data-ttu-id="f7286-218">V `ApplyDispatchBehavior` implementace `InstanceContextMode` aktuálního `ServiceBehavior` atribut se ověřuje.</span><span class="sxs-lookup"><span data-stu-id="f7286-218">In the `ApplyDispatchBehavior` implementation the `InstanceContextMode` of the current `ServiceBehavior` attribute is being verified.</span></span> <span data-ttu-id="f7286-219">Pokud tato vlastnost nastavená na jednotlivý prvek, povolení trvalý vytváření instancí není možné a `InvalidOperationException` je vyvolána výjimka, aby upozornil hostitele.</span><span class="sxs-lookup"><span data-stu-id="f7286-219">If this property is set to Singleton, enabling durable instancing is not possible and an `InvalidOperationException` is thrown to notify the host.</span></span>  
  
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
  
 <span data-ttu-id="f7286-220">Po této instance Správce úložiště, inicializátor instance kontextu a poskytovatele instance jsou vytvořeny a nainstalován v `DispatchRuntime` vytvořena pro každý koncový bod.</span><span class="sxs-lookup"><span data-stu-id="f7286-220">After this the instances of the storage manager, instance context initializer, and the instance provider are created and installed in the `DispatchRuntime` created for every endpoint.</span></span>  
  
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
  
 <span data-ttu-id="f7286-221">Stručně řečeno, pokud tuto ukázku vytvořil kanál, který povolené vlastní přenosový protokol pro kontext vlastní ID exchange a přepíše výchozí chování pro načtení instance z trvalého úložiště vytváření instancí.</span><span class="sxs-lookup"><span data-stu-id="f7286-221">In summary so far, this sample has produced a channel that enabled the custom wire protocol for custom context ID exchange and it also overwrites the default instancing behavior to load the instances from the persistent storage.</span></span>  
  
 <span data-ttu-id="f7286-222">Co je ponecháno je způsob, jak ušetřit instance služby do trvalého úložiště.</span><span class="sxs-lookup"><span data-stu-id="f7286-222">What is left is a way to save the service instance to the persistent storage.</span></span> <span data-ttu-id="f7286-223">Jak je popsáno výše, již existuje požadovanou funkci pro uložení stavu v `IStorageManager` implementace.</span><span class="sxs-lookup"><span data-stu-id="f7286-223">As discussed previously, there is already the required functionality to save the state in an `IStorageManager` implementation.</span></span> <span data-ttu-id="f7286-224">Nyní musíte integrujeme to s modulem runtime WCF.</span><span class="sxs-lookup"><span data-stu-id="f7286-224">We now must integrate this with the WCF runtime.</span></span> <span data-ttu-id="f7286-225">Je vyžadován jiný atribut, který se vztahuje na metody ve třídě implementaci služby.</span><span class="sxs-lookup"><span data-stu-id="f7286-225">Another attribute is required that is applicable to the methods in the service implementation class.</span></span> <span data-ttu-id="f7286-226">Tento atribut se má použít pro metody, které ke změně stavu instance služby.</span><span class="sxs-lookup"><span data-stu-id="f7286-226">This attribute is supposed to be applied to the methods that change the state of the service instance.</span></span>  
  
 <span data-ttu-id="f7286-227">`SaveStateAttribute` Třída implementuje tuto funkci.</span><span class="sxs-lookup"><span data-stu-id="f7286-227">The `SaveStateAttribute` class implements this functionality.</span></span> <span data-ttu-id="f7286-228">Implementuje navíc `IOperationBehavior` třídy změnit modul runtime WCF pro každou operaci.</span><span class="sxs-lookup"><span data-stu-id="f7286-228">It also implements `IOperationBehavior` class to modify the WCF runtime for each operation.</span></span> <span data-ttu-id="f7286-229">Když metoda je označena pomocí tohoto atributu, vyvolá modul runtime WCF `ApplyBehavior` metody odpovídající `DispatchOperation` se vytváří.</span><span class="sxs-lookup"><span data-stu-id="f7286-229">When a method is marked with this attribute, the WCF runtime invokes the `ApplyBehavior` method while the appropriate `DispatchOperation` is being constructed.</span></span> <span data-ttu-id="f7286-230">V této implementaci metody je jediný řádek kódu:</span><span class="sxs-lookup"><span data-stu-id="f7286-230">In this method implementation there is single line of code:</span></span>  
  
```  
dispatch.Invoker = new OperationInvoker(dispatch.Invoker);  
```  
  
 <span data-ttu-id="f7286-231">Tento pokyn vytvoří instanci `OperationInvoker` zadejte a přiřadí ji k `Invoker` vlastnost `DispatchOperation` vytváří.</span><span class="sxs-lookup"><span data-stu-id="f7286-231">This instruction creates an instance of `OperationInvoker` type and assigns it to the `Invoker` property of the `DispatchOperation` being constructed.</span></span> <span data-ttu-id="f7286-232">`OperationInvoker` Třídy tvoří obálku pro původce volání operace výchozí vytvořené pro `DispatchOperation`.</span><span class="sxs-lookup"><span data-stu-id="f7286-232">The `OperationInvoker` class is a wrapper for the default operation invoker created for the `DispatchOperation`.</span></span> <span data-ttu-id="f7286-233">Tato třída implementuje `IOperationInvoker` rozhraní.</span><span class="sxs-lookup"><span data-stu-id="f7286-233">This class implements the `IOperationInvoker` interface.</span></span> <span data-ttu-id="f7286-234">V `Invoke` implementace metody volání skutečné metody se deleguje na původce volání vnitřní operace.</span><span class="sxs-lookup"><span data-stu-id="f7286-234">In the `Invoke` method implementation the actual method invocation is delegated to the inner operation invoker.</span></span> <span data-ttu-id="f7286-235">Však teprve potom se informuje správce úložiště v výsledky `InstanceContext` se používá pro uložení instance služby.</span><span class="sxs-lookup"><span data-stu-id="f7286-235">However, before returning the results the storage manager in the `InstanceContext` is used to save the service instance.</span></span>  
  
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
  
## <a name="using-the-extension"></a><span data-ttu-id="f7286-236">Pomocí rozšíření</span><span class="sxs-lookup"><span data-stu-id="f7286-236">Using the Extension</span></span>  
 <span data-ttu-id="f7286-237">Dokončení vrstvy kanálu a rozšíření modelu vrstvy služeb i se teď dá v aplikacích WCF.</span><span class="sxs-lookup"><span data-stu-id="f7286-237">Both the channel layer and service model layer extensions are done and they can now be used in WCF applications.</span></span> <span data-ttu-id="f7286-238">Služby se mají přidat do kanálu zásobníku použití vlastní vazby kanálu a pak označit třídy implementace služby s příslušnými atributy.</span><span class="sxs-lookup"><span data-stu-id="f7286-238">Services have to add the channel into the channel stack using a custom binding and then mark the service implementation classes with the appropriate attributes.</span></span>  
  
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
  
 <span data-ttu-id="f7286-239">Klientské aplikace, musíte přidat DurableInstanceContextChannel do zásobníku kanál použití vlastní vazby.</span><span class="sxs-lookup"><span data-stu-id="f7286-239">Client applications must add the DurableInstanceContextChannel into the channel stack using a custom binding.</span></span> <span data-ttu-id="f7286-240">Ke konfiguraci kanálu deklarativně v konfiguračním souboru, v části elementu vazby musí být přidán do kolekce rozšíření elementu vazby.</span><span class="sxs-lookup"><span data-stu-id="f7286-240">To configure the channel declaratively in the configuration file, the binding element section has to be added to the binding element extensions collection.</span></span>  
  
```xml  
<system.serviceModel>  
 <extensions>  
   <bindingElementExtensions>  
     <add name="durableInstanceContext"  
type="Microsoft.ServiceModel.Samples.DurableInstanceContextBindingElementSection, DurableInstanceContextExtension, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null"/>  
   </bindingElementExtensions>  
 </extensions>  
```  
  
 <span data-ttu-id="f7286-241">Prvek vazby můžete jej použít s vlastní vazby, stejně jako ostatní standardní vazbu prvky:</span><span class="sxs-lookup"><span data-stu-id="f7286-241">Now the binding element can be used with a custom binding just like other standard binding elements:</span></span>  
  
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
  
## <a name="conclusion"></a><span data-ttu-id="f7286-242">Závěr</span><span class="sxs-lookup"><span data-stu-id="f7286-242">Conclusion</span></span>  
 <span data-ttu-id="f7286-243">Tuto ukázku jsme si ukázali, jak vytvořit vlastní protokol kanál a přizpůsobit chování služby, aby je.</span><span class="sxs-lookup"><span data-stu-id="f7286-243">This sample showed how to create a custom protocol channel and how to customize the service behavior to enable it.</span></span>  
  
 <span data-ttu-id="f7286-244">Rozšíření lze dále zvýšit tím, že uživatelům určit, `IStorageManager` implementace pomocí konfiguračního oddílu.</span><span class="sxs-lookup"><span data-stu-id="f7286-244">The extension can be further improved by letting users specify the `IStorageManager` implementation using a configuration section.</span></span> <span data-ttu-id="f7286-245">Díky tomu je možné změnit bez opětovné kompilace kódu služby záložního úložiště.</span><span class="sxs-lookup"><span data-stu-id="f7286-245">This makes it possible to modify the backing store without recompiling the service code.</span></span>  
  
 <span data-ttu-id="f7286-246">Kromě toho by se mohl pokusit implementace třídy (například `StateBag`), který zapouzdří stav instance.</span><span class="sxs-lookup"><span data-stu-id="f7286-246">Furthermore you could try to implement a class (for example, `StateBag`), which encapsulates the state of the instance.</span></span> <span data-ttu-id="f7286-247">Třídy je zodpovědné za trvalost stavu pokaždé, když se změní.</span><span class="sxs-lookup"><span data-stu-id="f7286-247">That class is responsible for persisting the state whenever it changes.</span></span> <span data-ttu-id="f7286-248">Díky tomu můžete předejít použití `SaveState` atribut a přesněji provedení zachování práce (například může zachování stavu, když ve skutečnosti je změněn stav místo uložení pokaždé, když při metodu s `SaveState` atribut volá se).</span><span class="sxs-lookup"><span data-stu-id="f7286-248">This way you can avoid using the `SaveState` attribute and perform the persisting work more accurately (for example, you could persist the state when the state is actually changed rather than saving it each time when a method with the `SaveState` attribute is called).</span></span>  
  
 <span data-ttu-id="f7286-249">Když spustíte ukázku, zobrazí se následující výstup.</span><span class="sxs-lookup"><span data-stu-id="f7286-249">When you run the sample, the following output is displayed.</span></span> <span data-ttu-id="f7286-250">Klient přidá dvě položky do jeho nákupního košíku a potom získá seznam položek v jeho nákupního košíku ze služby.</span><span class="sxs-lookup"><span data-stu-id="f7286-250">The client adds two items to its shopping cart and then gets the list of items in its shopping cart from the service.</span></span> <span data-ttu-id="f7286-251">Stisknutím klávesy ENTER v každé okno konzoly pro vypnutí klienta a služby.</span><span class="sxs-lookup"><span data-stu-id="f7286-251">Press ENTER in each console window to shut down the service and client.</span></span>  
  
```  
Enter the name of the product: apples  
Enter the name of the product: bananas  
  
Shopping cart currently contains the following items.  
apples  
bananas  
Press ENTER to shut down client  
```  
  
> [!NOTE]
>  <span data-ttu-id="f7286-252">Znovu sestavit službu přepíše soubor databáze.</span><span class="sxs-lookup"><span data-stu-id="f7286-252">Rebuilding the service overwrites the database file.</span></span> <span data-ttu-id="f7286-253">Sledovat stavů zachovaný během různých spuštění ukázky, se ujistěte, že znovu sestavte ukázku mezi spuštění.</span><span class="sxs-lookup"><span data-stu-id="f7286-253">To observe state preserved across multiple runs of the sample, be sure not to rebuild the sample between runs.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="f7286-254">Chcete-li nastavit, sestavte a spusťte ukázku</span><span class="sxs-lookup"><span data-stu-id="f7286-254">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="f7286-255">Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="f7286-255">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="f7286-256">Abyste mohli sestavit řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="f7286-256">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="f7286-257">Spusťte ukázku v konfiguraci s jedním nebo více počítačů, postupujte podle pokynů v [spouštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="f7286-257">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f7286-258">SQL Server 2005 nebo SQL Express 2005. tuto ukázku spustit, musí běžet.</span><span class="sxs-lookup"><span data-stu-id="f7286-258">You must be running SQL Server 2005 or SQL Express 2005 to run this sample.</span></span> <span data-ttu-id="f7286-259">Pokud používáte systém SQL Server 2005, je třeba upravit konfigurace služby připojovací řetězec.</span><span class="sxs-lookup"><span data-stu-id="f7286-259">If you are running SQL Server 2005, you must modify the configuration of the service's connection string.</span></span> <span data-ttu-id="f7286-260">Při spuštění mezi počítači systému SQL Server je potřeba jenom na počítači serveru.</span><span class="sxs-lookup"><span data-stu-id="f7286-260">When running cross-machine, SQL Server is only required on the server machine.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="f7286-261">Vzorky mohou již být nainstalováno na svém počítači.</span><span class="sxs-lookup"><span data-stu-id="f7286-261">The samples may already be installed on your machine.</span></span> <span data-ttu-id="f7286-262">Před pokračováním zkontrolujte následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="f7286-262">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="f7286-263">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="f7286-263">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="f7286-264">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="f7286-264">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Instancing\Durable`  
