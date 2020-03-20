---
title: Formátovací modul a selektor operace
ms.date: 03/30/2017
ms.assetid: 1c27e9fe-11f8-4377-8140-828207b98a0e
ms.openlocfilehash: 9d1bc0afa54f89e064eab3f3e45da60c8d10de38
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79144276"
---
# <a name="operation-formatter-and-operation-selector"></a><span data-ttu-id="26962-102">Formátovací modul a selektor operace</span><span class="sxs-lookup"><span data-stu-id="26962-102">Operation Formatter and Operation Selector</span></span>
<span data-ttu-id="26962-103">Tato ukázka ukazuje, jak windows communication foundation (WCF) body rozšiřitelnosti lze povolit data zprávy v jiném formátu, než wcf očekává.</span><span class="sxs-lookup"><span data-stu-id="26962-103">This sample demonstrates how Windows Communication Foundation (WCF) extensibility points can be used to allow message data in a different format from what WCF expects.</span></span> <span data-ttu-id="26962-104">Ve výchozím nastavení WCF formatters očekávat parametry `soap:body` metody, které mají být zahrnuty do prvku.</span><span class="sxs-lookup"><span data-stu-id="26962-104">By default, WCF formatters expect method parameters to be included under the `soap:body` element.</span></span> <span data-ttu-id="26962-105">Ukázka ukazuje, jak implementovat vlastní operace formatter, který analyzuje data parametrů z řetězce dotazu HTTP GET místo a vyvolá metody pomocí dat.</span><span class="sxs-lookup"><span data-stu-id="26962-105">The sample shows how to implement a custom operation formatter that parses parameter data from an HTTP GET query string instead and invokes methods using that data.</span></span>  
  
 <span data-ttu-id="26962-106">Ukázka je založena na [začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md), `ICalculator` který implementuje servisní smlouvy.</span><span class="sxs-lookup"><span data-stu-id="26962-106">The sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md), which implements the `ICalculator` service contract.</span></span> <span data-ttu-id="26962-107">Ukazuje, jak přidat, odečíst, násobit a rozdělit zprávy lze změnit na použití HTTP GET pro požadavky klienta na server a HTTP POST se zprávami POX pro odpovědi mezi servery.</span><span class="sxs-lookup"><span data-stu-id="26962-107">It shows how Add, Subtract, Multiply, and Divide messages can be changed to use HTTP GET for client-to-server requests and HTTP POST with POX messages for server-to-client responses.</span></span>  
  
 <span data-ttu-id="26962-108">Chcete-li tak učinit, ukázka poskytuje následující:</span><span class="sxs-lookup"><span data-stu-id="26962-108">To do so, the sample provides the following:</span></span>  
  
- <span data-ttu-id="26962-109">`QueryStringFormatter`, který <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> implementuje a <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> pro klienta a server, respektive a zpracovává data v řetězci dotazu.</span><span class="sxs-lookup"><span data-stu-id="26962-109">`QueryStringFormatter`, which implements <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> and <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> for the client and server, respectively, and processes the data in the query string.</span></span>  
  
- <span data-ttu-id="26962-110">`UriOperationSelector`, který <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> implementuje na serveru k provedení expedice operace na základě názvu operace v požadavku GET.</span><span class="sxs-lookup"><span data-stu-id="26962-110">`UriOperationSelector`, which implements <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> on the server to perform operation dispatch based on the operation name in the GET request.</span></span>  
  
- <span data-ttu-id="26962-111">`EnableHttpGetRequestsBehavior`koncového bodu (a odpovídající konfigurace), který přidá potřebný volič operací do běhu.</span><span class="sxs-lookup"><span data-stu-id="26962-111">`EnableHttpGetRequestsBehavior` endpoint behavior (and corresponding configuration), which adds the necessary operation selector to the runtime.</span></span>  
  
- <span data-ttu-id="26962-112">Ukazuje, jak vložit novou operaci forpono do modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="26962-112">Shows how to insert a new operation formatter into the runtime.</span></span>  
  
- <span data-ttu-id="26962-113">V této ukázce jsou klient a služba konzolové aplikace (.exe).</span><span class="sxs-lookup"><span data-stu-id="26962-113">In this sample, both the client and the service are console applications (.exe).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="26962-114">Postup instalace a pokyny k sestavení pro tuto ukázku jsou umístěny na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="26962-114">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
## <a name="key-concepts"></a><span data-ttu-id="26962-115">Klíčové koncepty</span><span class="sxs-lookup"><span data-stu-id="26962-115">Key Concepts</span></span>  
 <span data-ttu-id="26962-116">`QueryStringFormatter`- Operace formátovací modul je součást wcf, který je zodpovědný za převod zprávy do pole parametr objekty a pole parametr objekty do zprávy.</span><span class="sxs-lookup"><span data-stu-id="26962-116">`QueryStringFormatter` - The operation formatter is the component in WCF that is responsible for converting a message into an array of parameter objects and an array of parameter objects into a message.</span></span> <span data-ttu-id="26962-117">To se provádí na <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> straně klienta pomocí <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> rozhraní a na serveru s rozhraním.</span><span class="sxs-lookup"><span data-stu-id="26962-117">This is done on the client using the <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> interface and on the server with the <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> interface.</span></span> <span data-ttu-id="26962-118">Tato rozhraní umožňují uživatelům získat zprávy požadavku `Serialize` a `Deserialize` odpovědi z metody a.</span><span class="sxs-lookup"><span data-stu-id="26962-118">These interfaces enable users to get the request and response messages from the `Serialize` and `Deserialize` methods.</span></span>  
  
 <span data-ttu-id="26962-119">V této `QueryStringFormatter` ukázce implementuje obě tato rozhraní a je implementována na straně klienta a serveru.</span><span class="sxs-lookup"><span data-stu-id="26962-119">In this sample, `QueryStringFormatter` implements both of these interfaces and is implemented on the client and server.</span></span>  
  
 <span data-ttu-id="26962-120">Požadavek:</span><span class="sxs-lookup"><span data-stu-id="26962-120">Request:</span></span>  
  
- <span data-ttu-id="26962-121">Ukázka používá <xref:System.ComponentModel.TypeConverter> třídu k převodu dat parametrů ve zprávě požadavku na řetězce a z řetězce.</span><span class="sxs-lookup"><span data-stu-id="26962-121">The sample uses the <xref:System.ComponentModel.TypeConverter> class to convert parameter data in the request message to and from strings.</span></span> <span data-ttu-id="26962-122">Pokud <xref:System.ComponentModel.TypeConverter> a není k dispozici pro konkrétní typ, ukázkový formavý modul vyvolá výjimku.</span><span class="sxs-lookup"><span data-stu-id="26962-122">If a <xref:System.ComponentModel.TypeConverter> is not available for a specific type, the sample formatter throws an exception.</span></span>  
  
- <span data-ttu-id="26962-123">V `IClientMessageFormatter.SerializeRequest` metodě na straně klienta vytvoří modul pro formátování ano s příslušnou adresou To a připojí název operace jako příponu.</span><span class="sxs-lookup"><span data-stu-id="26962-123">In the `IClientMessageFormatter.SerializeRequest` method on the client, the formatter creates a URI with the appropriate To address and appends the operation name as a suffix.</span></span> <span data-ttu-id="26962-124">Tento název se používá k odeslání do příslušné operace na serveru.</span><span class="sxs-lookup"><span data-stu-id="26962-124">This name is used to dispatch to the appropriate operation on the server.</span></span> <span data-ttu-id="26962-125">Potom převezme pole objektů parametrů a serializuje data parametrů do řetězce dotazu URI pomocí názvů <xref:System.ComponentModel.TypeConverter> parametrů a hodnot převedených třídou.</span><span class="sxs-lookup"><span data-stu-id="26962-125">It then takes the array of parameter objects and serializes the parameter data to the URI query string using parameter names and the values converted by the <xref:System.ComponentModel.TypeConverter> class.</span></span> <span data-ttu-id="26962-126"><xref:System.ServiceModel.Channels.MessageHeaders.To%2A> Vlastnosti <xref:System.ServiceModel.Channels.MessageProperties.Via%2A> a jsou pak nastaveny na tento identifikátor URI.</span><span class="sxs-lookup"><span data-stu-id="26962-126">The <xref:System.ServiceModel.Channels.MessageHeaders.To%2A> and <xref:System.ServiceModel.Channels.MessageProperties.Via%2A> properties are then set to this URI.</span></span> <span data-ttu-id="26962-127"><xref:System.ServiceModel.Channels.MessageProperties>je přístupný prostřednictvím ubytovacího <xref:System.ServiceModel.Channels.Message.Properties%2A> zařízení.</span><span class="sxs-lookup"><span data-stu-id="26962-127"><xref:System.ServiceModel.Channels.MessageProperties> is accessed through the <xref:System.ServiceModel.Channels.Message.Properties%2A> property.</span></span>  
  
- <span data-ttu-id="26962-128">V `IDispatchMessageFormatter.DeserializeRequest` metodě na serveru formátovací modul `Via` načte identifikátor URI ve vlastnostech zprávy příchozího požadavku.</span><span class="sxs-lookup"><span data-stu-id="26962-128">In the `IDispatchMessageFormatter.DeserializeRequest` method on the server, the formatter retrieves the `Via` URI in the incoming request message properties.</span></span> <span data-ttu-id="26962-129">Analyzuje dvojice název-hodnota v řetězci dotazu URI na názvy a hodnoty parametrů a používá názvy parametrů a hodnoty k naplnění pole parametrů předaných do metody.</span><span class="sxs-lookup"><span data-stu-id="26962-129">It parses the name-value pairs in the URI query string into parameter names and values and uses the parameter names and values to populate the array of parameters passed into the method.</span></span> <span data-ttu-id="26962-130">Všimněte si, že operace odeslání již došlo, takže název operace přípona je ignorována v této metodě.</span><span class="sxs-lookup"><span data-stu-id="26962-130">Note that operation dispatch has already occurred, so the operation name suffix is ignored in this method.</span></span>  
  
 <span data-ttu-id="26962-131">Odpověď:</span><span class="sxs-lookup"><span data-stu-id="26962-131">Response:</span></span>  
  
- <span data-ttu-id="26962-132">V této ukázce HTTP GET se používá pouze pro požadavek.</span><span class="sxs-lookup"><span data-stu-id="26962-132">In this sample, HTTP GET is used only for the request.</span></span> <span data-ttu-id="26962-133">Formátovací modul deleguje odesílání odpovědi na původní formátovací modul, který by byl použit ke generování zprávy XML.</span><span class="sxs-lookup"><span data-stu-id="26962-133">The formatter delegates the sending of the response to the original formatter that would have been used to generate an XML message.</span></span> <span data-ttu-id="26962-134">Jedním z cílů této ukázky je ukázat, jak může být implementována taková delegující forponáta.</span><span class="sxs-lookup"><span data-stu-id="26962-134">One of the goals of this sample is to show how such a delegating formatter can be implemented.</span></span>  
  
### <a name="uripathsuffixoperationselector-class"></a><span data-ttu-id="26962-135">Třída UriPathSuffixOperationSelector</span><span class="sxs-lookup"><span data-stu-id="26962-135">UriPathSuffixOperationSelector Class</span></span>  
 <span data-ttu-id="26962-136">Rozhraní <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> umožňuje uživatelům implementovat vlastní logiku, pro kterou by měla být odeslána určitá zpráva.</span><span class="sxs-lookup"><span data-stu-id="26962-136">The <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> interface enables users to implement their own logic for which operation a particular message should be dispatched.</span></span>  
  
 <span data-ttu-id="26962-137">V této `UriPathSuffixOperationSelector` ukázce musí být implementována na serveru vybrat příslušnou operaci, protože název operace je součástí HTTP GET URI spíše než záhlaví akce ve zprávě.</span><span class="sxs-lookup"><span data-stu-id="26962-137">In this sample, `UriPathSuffixOperationSelector` must be implemented on the server to select the appropriate operation because the operation name is included in the HTTP GET URI rather than an action header in the message.</span></span> <span data-ttu-id="26962-138">Ukázka je nastavena tak, aby umožňovala pouze názvy operací bez rozlišování velkých a malých písmen.</span><span class="sxs-lookup"><span data-stu-id="26962-138">The sample is set up to allow only case-insensitive operation names.</span></span>  
  
 <span data-ttu-id="26962-139">Metoda `SelectOperation` převezme příchozí zprávu a vyhledá `Via` identifikátor URI ve svých vlastnostech zprávy.</span><span class="sxs-lookup"><span data-stu-id="26962-139">The `SelectOperation` method takes the incoming message and looks up the `Via` URI in its message properties.</span></span> <span data-ttu-id="26962-140">Extrahuje příponu názvu operace z identifikátoru URI, vyhledá interní tabulku, aby získal název operace, do které by měla být zpráva odeslána, a vrátí tento název operace.</span><span class="sxs-lookup"><span data-stu-id="26962-140">It extracts the operation name suffix from the URI, looks up an internal table to get the operation name that the message should be dispatched to, and returns that operation name.</span></span>  
  
### <a name="enablehttpgetrequestsbehavior-class"></a><span data-ttu-id="26962-141">Povolit třídu HttpGetRequestsBehavior</span><span class="sxs-lookup"><span data-stu-id="26962-141">EnableHttpGetRequestsBehavior Class</span></span>  
 <span data-ttu-id="26962-142">Součást `UriPathSuffixOperationSelector` lze nastavit programově nebo pomocí chování koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="26962-142">The `UriPathSuffixOperationSelector` component can be set up programmatically or through an endpoint behavior.</span></span> <span data-ttu-id="26962-143">Ukázka implementuje `EnableHttpGetRequestsBehavior` chování, které je určeno v konfiguračním souboru aplikace služby.</span><span class="sxs-lookup"><span data-stu-id="26962-143">The sample implements the `EnableHttpGetRequestsBehavior` behavior, which is specified in service’s application configuration file.</span></span>  
  
 <span data-ttu-id="26962-144">Na serveru:</span><span class="sxs-lookup"><span data-stu-id="26962-144">On the server:</span></span>  
  
 <span data-ttu-id="26962-145">Je <xref:System.ServiceModel.Dispatcher.DispatchRuntime.OperationSelector%2A> nastavena <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> na implementaci.</span><span class="sxs-lookup"><span data-stu-id="26962-145">The <xref:System.ServiceModel.Dispatcher.DispatchRuntime.OperationSelector%2A> is set to the <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> implementation.</span></span>  
  
 <span data-ttu-id="26962-146">Ve výchozím nastavení wcf používá filtr adresy přesné shody.</span><span class="sxs-lookup"><span data-stu-id="26962-146">By default, WCF uses an exact-match address filter.</span></span> <span data-ttu-id="26962-147">Identifikátor URI na příchozí zprávě obsahuje příponu názvu operace následovanou řetězcem dotazu, který obsahuje data parametrů, takže chování koncového bodu také změní filtr adresy na filtr shody předpony.</span><span class="sxs-lookup"><span data-stu-id="26962-147">The URI on the incoming message contains an operation name suffix followed by a query string that contains parameter data, so the endpoint behavior also changes the address filter to be a prefix match filter.</span></span> <span data-ttu-id="26962-148">Používá WCF<xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter> pro tento účel.</span><span class="sxs-lookup"><span data-stu-id="26962-148">It uses the WCF<xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter> for this purpose.</span></span>  
  
### <a name="installing-operation-formatters"></a><span data-ttu-id="26962-149">Instalace provozních formatters</span><span class="sxs-lookup"><span data-stu-id="26962-149">Installing operation formatters</span></span>  
 <span data-ttu-id="26962-150">Chování operace, které určují formatters jsou jedinečné.</span><span class="sxs-lookup"><span data-stu-id="26962-150">Operation behaviors that specify formatters are unique.</span></span> <span data-ttu-id="26962-151">Jedno takové chování je vždy implementováno ve výchozím nastavení pro každou operaci k vytvoření potřebné operace formatter.</span><span class="sxs-lookup"><span data-stu-id="26962-151">One such behavior is always implemented by default for every operation to create the necessary operation formatter.</span></span> <span data-ttu-id="26962-152">Toto chování však vypadat jako jen další operace chování; nejsou identifikovatelné žádným jiným atributem.</span><span class="sxs-lookup"><span data-stu-id="26962-152">However, these behaviors look like just another operation behavior; they are not identifiable by any other attribute.</span></span> <span data-ttu-id="26962-153">Chcete-li nainstalovat náhradní chování, implementace musí hledat konkrétní formatter chování, které jsou nainstalovány zavaděč typu WCF ve výchozím nastavení a buď jej nahradit nebo přidat kompatibilní chování spustit po výchozí chování.</span><span class="sxs-lookup"><span data-stu-id="26962-153">To install a replacement behavior, the implementation must look for specific formatter behaviors that are installed by the WCF type loader by default and either replace it or add a compatible behavior to run after the default behavior.</span></span>  
  
 <span data-ttu-id="26962-154">Tyto operace formatters chování lze nastavit programově <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A?displayProperty=nameWithType> před voláním nebo zadáním chování operace, která je provedena po výchozí.</span><span class="sxs-lookup"><span data-stu-id="26962-154">These operation formatters behaviors can be set up programmatically prior to calling <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A?displayProperty=nameWithType> or by specifying an operation behavior that is executed after the default one.</span></span> <span data-ttu-id="26962-155">Nelze jej však snadno nastavit podle chování koncového bodu (a tedy podle konfigurace), protože model chování neumožňuje chování nahradit jiné chování nebo jinak upravit strom popisu.</span><span class="sxs-lookup"><span data-stu-id="26962-155">However, it cannot easily be set up by an endpoint behavior (and therefore by configuration) because the behavior model does not allow a behavior to replace other behaviors or otherwise modify the description tree.</span></span>  
  
 <span data-ttu-id="26962-156">Na straně klienta:</span><span class="sxs-lookup"><span data-stu-id="26962-156">On the client:</span></span>  
  
 <span data-ttu-id="26962-157">Implementace <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> musí být implementována tak, aby bylo možné převést požadavky na požadavky HTTP GET a delegovat na původní modul pro formátování pro odpovědi.</span><span class="sxs-lookup"><span data-stu-id="26962-157">The <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> implementation must be implemented so that it can convert the requests into HTTP GET requests and delegate to the original formatter for responses.</span></span> <span data-ttu-id="26962-158">To se provádí `EnableHttpGetRequestsBehavior.ReplaceFormatterBehavior` voláním pomocné metody.</span><span class="sxs-lookup"><span data-stu-id="26962-158">This is done by calling the `EnableHttpGetRequestsBehavior.ReplaceFormatterBehavior` helper method.</span></span>  
  
 <span data-ttu-id="26962-159">To musí být `CreateChannel`provedeno před voláním .</span><span class="sxs-lookup"><span data-stu-id="26962-159">This must be done before calling `CreateChannel`.</span></span>  
  
```csharp  
void ReplaceFormatterBehavior(OperationDescription operationDescription, EndpointAddress address)  
{  
    // Remove the DataContract behavior if it is present.  
    IOperationBehavior formatterBehavior = operationDescription.Behaviors.Remove<DataContractSerializerOperationBehavior>();  
    if (formatterBehavior == null)  
    {  
        // Remove the XmlSerializer behavior if it is present.  
        formatterBehavior = operationDescription.Behaviors.Remove<XmlSerializerOperationBehavior>();  
        ...  
    }  
  
    // Remember what the innerFormatterBehavior was.  
    DelegatingFormatterBehavior delegatingFormatterBehavior = new DelegatingFormatterBehavior(address);  
    delegatingFormatterBehavior.InnerFormatterBehavior = formatterBehavior;  
   operationDescription.Behaviors.Add(delegatingFormatterBehavior);  
}  
```  
  
 <span data-ttu-id="26962-160">Na serveru:</span><span class="sxs-lookup"><span data-stu-id="26962-160">On the server:</span></span>  
  
- <span data-ttu-id="26962-161">Rozhraní <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> musí být implementováno tak, aby bylo možné číst požadavky HTTP GET a delegovat na původní návrhový modul pro zápis odpovědí.</span><span class="sxs-lookup"><span data-stu-id="26962-161">The <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> interface must be implemented so that it can read HTTP GET requests and delegate to the original formatter for writing responses.</span></span> <span data-ttu-id="26962-162">To se provádí voláním stejné `EnableHttpGetRequestsBehavior.ReplaceFormatterBehavior` pomocné metody jako klient (viz předchozí ukázka kódu).</span><span class="sxs-lookup"><span data-stu-id="26962-162">This is done by calling the same `EnableHttpGetRequestsBehavior.ReplaceFormatterBehavior` helper method as the client (see the previous code sample).</span></span>  
  
- <span data-ttu-id="26962-163">To musí být <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> provedeno dříve, než se nazývá.</span><span class="sxs-lookup"><span data-stu-id="26962-163">This must be done before <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> is called.</span></span> <span data-ttu-id="26962-164">V této ukázce ukážeme, jak je <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>modul vzorníku ručně upraven před voláním .</span><span class="sxs-lookup"><span data-stu-id="26962-164">In this sample, we show how the formatter is manually modified before calling <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>.</span></span> <span data-ttu-id="26962-165">Dalším způsobem, jak dosáhnout stejné věci, <xref:System.ServiceModel.ServiceHost> je odvodit třídu, ze které je volání `EnableHttpGetRequestsBehavior.ReplaceFormatterBehavior` před otevřením (viz hosting dokumentace a ukázky pro příklady).</span><span class="sxs-lookup"><span data-stu-id="26962-165">Another way to achieve the same thing is to derive a class from <xref:System.ServiceModel.ServiceHost> that makes the calls to `EnableHttpGetRequestsBehavior.ReplaceFormatterBehavior` before opening (please see hosting documentation and samples for examples).</span></span>  
  
### <a name="user-experience"></a><span data-ttu-id="26962-166">Uživatelské prostředí</span><span class="sxs-lookup"><span data-stu-id="26962-166">User experience</span></span>  
 <span data-ttu-id="26962-167">Na serveru:</span><span class="sxs-lookup"><span data-stu-id="26962-167">On the server:</span></span>  
  
- <span data-ttu-id="26962-168">Implementace `ICalculator` serveru není nutné měnit.</span><span class="sxs-lookup"><span data-stu-id="26962-168">The server `ICalculator` implementation does not need to change.</span></span>  
  
- <span data-ttu-id="26962-169">Nástroj App.config pro službu musí používat vlastní `messageVersion` vazbu `textMessageEncoding` POX, která nastaví atribut prvku na `None`.</span><span class="sxs-lookup"><span data-stu-id="26962-169">The App.config for the service must use a custom POX binding that sets the `messageVersion` attribute of the `textMessageEncoding` element to `None`.</span></span>  
  
    ```xml  
    <bindings>  
      <customBinding>  
        <binding name="poxBinding">  
          <textMessageEncoding messageVersion="None" />  
          <httpTransport />  
        </binding>  
      </customBinding>  
    </bindings>  
    ```  
  
- <span data-ttu-id="26962-170">App.config pro službu také musí `EnableHttpGetRequestsBehavior` zadat vlastní přidáním do oddílu rozšíření chování a jeho použití.</span><span class="sxs-lookup"><span data-stu-id="26962-170">The App.config for the service also must specify the custom `EnableHttpGetRequestsBehavior` by adding it to the behavior extensions section and using it.</span></span>  
  
    ```xml  
    <behaviors>  
      <endpointBehaviors>  
        <behavior name="enableHttpGetRequestsBehavior">  
          <enableHttpGetRequests />  
        </behavior>  
      </endpointBehaviors>  
    </behaviors>  
  
    <extensions>  
      <behaviorExtensions>  
        <!-- Enabling HTTP GET requests: Behavior Extension -->  
        <add
          name="enableHttpGetRequests"           type="Microsoft.ServiceModel.Samples.EnableHttpGetRequestsBehaviorElement, QueryStringFormatter, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null" />  
      </behaviorExtensions>  
    </extensions>  
    ```  
  
- <span data-ttu-id="26962-171">Přidat operace formatters <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>před voláním .</span><span class="sxs-lookup"><span data-stu-id="26962-171">Add operation formatters before calling <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>.</span></span>  
  
 <span data-ttu-id="26962-172">Na straně klienta:</span><span class="sxs-lookup"><span data-stu-id="26962-172">On the client:</span></span>  
  
- <span data-ttu-id="26962-173">Implementace klienta není nutné změnit.</span><span class="sxs-lookup"><span data-stu-id="26962-173">The client implementation does not need to change.</span></span>  
  
- <span data-ttu-id="26962-174">Nástroj App.config pro klienta musí používat vlastní `messageVersion` vazbu `textMessageEncoding` POX, která nastaví atribut prvku na `None`.</span><span class="sxs-lookup"><span data-stu-id="26962-174">The App.config for the client must use a custom POX binding that sets the `messageVersion` attribute of the `textMessageEncoding` element to `None`.</span></span> <span data-ttu-id="26962-175">Jeden rozdíl od služby je, že klient musí povolit ruční adresování tak, aby odchozí adresa může být změněna.</span><span class="sxs-lookup"><span data-stu-id="26962-175">One difference from the service is that the client must enable manual addressing so that the outgoing To address can be modified.</span></span>  
  
    ```xml  
    <bindings>  
      <customBinding>  
        <binding name="poxBinding">  
          <textMessageEncoding messageVersion="None" />  
          <httpTransport manualAddressing="True" />  
        </binding>  
      </customBinding>  
    </bindings>  
    ```  
  
- <span data-ttu-id="26962-176">Nástroj App.config pro klienta musí `EnableHttpGetRequestsBehavior` zadat stejný vlastní jako server.</span><span class="sxs-lookup"><span data-stu-id="26962-176">The App.config for the client must specify the same custom `EnableHttpGetRequestsBehavior` as the server.</span></span>  
  
- <span data-ttu-id="26962-177">Přidat operace formatters <xref:System.ServiceModel.ChannelFactory%601.CreateChannel>před voláním .</span><span class="sxs-lookup"><span data-stu-id="26962-177">Add operation formatters before calling <xref:System.ServiceModel.ChannelFactory%601.CreateChannel>.</span></span>  
  
 <span data-ttu-id="26962-178">Při spuštění ukázky jsou v okně klientské konzole zobrazeny požadavky na operaci a odpovědi.</span><span class="sxs-lookup"><span data-stu-id="26962-178">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="26962-179">Všechny čtyři operace (Přidat, Odečíst, Násobit a Rozdělit) musí být úspěšné.</span><span class="sxs-lookup"><span data-stu-id="26962-179">All four operations (Add, Subtract, Multiply, and Divide) must succeed.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="26962-180">Ukázky mohou být již nainstalovány v počítači.</span><span class="sxs-lookup"><span data-stu-id="26962-180">The samples may already be installed on your machine.</span></span> <span data-ttu-id="26962-181">Před pokračováním zkontrolujte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="26962-181">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="26962-182">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="26962-182">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="26962-183">Tato ukázka je umístěna v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="26962-183">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Formatters\QueryStringFormatter`  
  
##### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="26962-184">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="26962-184">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="26962-185">Ujistěte se, že jste provedli [jednorázový postup instalace pro ukázky windows communication foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="26962-185">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="26962-186">Chcete-li vytvořit řešení, postupujte podle pokynů v [sestavení windows communication foundation ukázky](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="26962-186">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="26962-187">Chcete-li spustit ukázku v konfiguraci jednoho nebo více počítačů, postupujte podle pokynů v [části Spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="26962-187">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
