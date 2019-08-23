---
title: Formátovací modul a selektor operace
ms.date: 03/30/2017
ms.assetid: 1c27e9fe-11f8-4377-8140-828207b98a0e
ms.openlocfilehash: 977a759b2c3f6d803879fc640439cd0b3465ffbf
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965593"
---
# <a name="operation-formatter-and-operation-selector"></a><span data-ttu-id="b3568-102">Formátovací modul a selektor operace</span><span class="sxs-lookup"><span data-stu-id="b3568-102">Operation Formatter and Operation Selector</span></span>
<span data-ttu-id="b3568-103">Tento příklad ukazuje, jak lze použít body rozšiřitelnosti Windows Communication Foundation (WCF) k povolení dat zprávy v jiném formátu, od kterého očekává WCF.</span><span class="sxs-lookup"><span data-stu-id="b3568-103">This sample demonstrates how Windows Communication Foundation (WCF) extensibility points can be used to allow message data in a different format from what WCF expects.</span></span> <span data-ttu-id="b3568-104">Ve výchozím nastavení očekávají formátovací moduly WCF parametry metody, které mají být zahrnuty `soap:body` do elementu.</span><span class="sxs-lookup"><span data-stu-id="b3568-104">By default, WCF formatters expect method parameters to be included under the `soap:body` element.</span></span> <span data-ttu-id="b3568-105">Ukázka ukazuje, jak implementovat vlastní formátovací modul operace, který analyzuje data parametrů z řetězce dotazu HTTP GET a vyvolává metody používající tato data.</span><span class="sxs-lookup"><span data-stu-id="b3568-105">The sample shows how to implement a custom operation formatter that parses parameter data from an HTTP GET query string instead and invokes methods using that data.</span></span>  
  
 <span data-ttu-id="b3568-106">Ukázka je založena na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md), která implementuje `ICalculator` kontrakt služby.</span><span class="sxs-lookup"><span data-stu-id="b3568-106">The sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md), which implements the `ICalculator` service contract.</span></span> <span data-ttu-id="b3568-107">Zobrazuje způsob, jakým se dají zprávy přidat, odečíst, násobit a rozdělit použít k použití HTTP GET pro požadavky klienta na server a HTTP POST se POX zprávami pro odpovědi ze serveru na klienta.</span><span class="sxs-lookup"><span data-stu-id="b3568-107">It shows how Add, Subtract, Multiply, and Divide messages can be changed to use HTTP GET for client-to-server requests and HTTP POST with POX messages for server-to-client responses.</span></span>  
  
 <span data-ttu-id="b3568-108">V takovém případě ukázka poskytuje následující:</span><span class="sxs-lookup"><span data-stu-id="b3568-108">To do so, the sample provides the following:</span></span>  
  
- <span data-ttu-id="b3568-109">`QueryStringFormatter`, který implementuje <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> a <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> pro klienta a server, v uvedeném pořadí a zpracovává data v řetězci dotazu.</span><span class="sxs-lookup"><span data-stu-id="b3568-109">`QueryStringFormatter`, which implements <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> and <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> for the client and server, respectively, and processes the data in the query string.</span></span>  
  
- <span data-ttu-id="b3568-110">`UriOperationSelector`, který implementuje <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> na serveru k provedení odeslání operace na základě názvu operace v žádosti o získání.</span><span class="sxs-lookup"><span data-stu-id="b3568-110">`UriOperationSelector`, which implements <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> on the server to perform operation dispatch based on the operation name in the GET request.</span></span>  
  
- <span data-ttu-id="b3568-111">`EnableHttpGetRequestsBehavior`chování koncového bodu (a odpovídající konfigurace), které do modulu runtime přidává potřebný selektor operací.</span><span class="sxs-lookup"><span data-stu-id="b3568-111">`EnableHttpGetRequestsBehavior` endpoint behavior (and corresponding configuration), which adds the necessary operation selector to the runtime.</span></span>  
  
- <span data-ttu-id="b3568-112">Ukazuje, jak vložit nový formátovací modul operace do modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="b3568-112">Shows how to insert a new operation formatter into the runtime.</span></span>  
  
- <span data-ttu-id="b3568-113">V této ukázce je klient i služba Konzolová aplikace (. exe).</span><span class="sxs-lookup"><span data-stu-id="b3568-113">In this sample, both the client and the service are console applications (.exe).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b3568-114">Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="b3568-114">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
## <a name="key-concepts"></a><span data-ttu-id="b3568-115">Klíčové koncepty</span><span class="sxs-lookup"><span data-stu-id="b3568-115">Key Concepts</span></span>  
 <span data-ttu-id="b3568-116">`QueryStringFormatter`-Formátovací modul operace je součástí služby WCF, která je odpovědná za převod zprávy na pole objektů parametrů a pole objektů parametrů do zprávy.</span><span class="sxs-lookup"><span data-stu-id="b3568-116">`QueryStringFormatter` - The operation formatter is the component in WCF that is responsible for converting a message into an array of parameter objects and an array of parameter objects into a message.</span></span> <span data-ttu-id="b3568-117">To se provádí na klientovi pomocí <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> rozhraní a na serveru <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> s rozhraním.</span><span class="sxs-lookup"><span data-stu-id="b3568-117">This is done on the client using the <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> interface and on the server with the <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> interface.</span></span> <span data-ttu-id="b3568-118">Tato rozhraní umožňují uživatelům získat zprávy žádosti a odpovědi z `Serialize` metod a. `Deserialize`</span><span class="sxs-lookup"><span data-stu-id="b3568-118">These interfaces enable users to get the request and response messages from the `Serialize` and `Deserialize` methods.</span></span>  
  
 <span data-ttu-id="b3568-119">V této ukázce `QueryStringFormatter` implementuje obě tato rozhraní a je implementována na straně klienta a serveru.</span><span class="sxs-lookup"><span data-stu-id="b3568-119">In this sample, `QueryStringFormatter` implements both of these interfaces and is implemented on the client and server.</span></span>  
  
 <span data-ttu-id="b3568-120">Request</span><span class="sxs-lookup"><span data-stu-id="b3568-120">Request:</span></span>  
  
- <span data-ttu-id="b3568-121">Ukázka používá <xref:System.ComponentModel.TypeConverter> třídu pro převod dat parametrů ve zprávě požadavku na a z řetězců.</span><span class="sxs-lookup"><span data-stu-id="b3568-121">The sample uses the <xref:System.ComponentModel.TypeConverter> class to convert parameter data in the request message to and from strings.</span></span> <span data-ttu-id="b3568-122"><xref:System.ComponentModel.TypeConverter> Pokud není pro určitý typ k dispozici, vygeneruje vzorový modul formátování výjimku.</span><span class="sxs-lookup"><span data-stu-id="b3568-122">If a <xref:System.ComponentModel.TypeConverter> is not available for a specific type, the sample formatter throws an exception.</span></span>  
  
- <span data-ttu-id="b3568-123">`IClientMessageFormatter.SerializeRequest` V metodě na klientovi modul formátování vytvoří identifikátor URI s odpovídajícími adresami pro adresu a připojí název operace jako příponu.</span><span class="sxs-lookup"><span data-stu-id="b3568-123">In the `IClientMessageFormatter.SerializeRequest` method on the client, the formatter creates a URI with the appropriate To address and appends the operation name as a suffix.</span></span> <span data-ttu-id="b3568-124">Tento název slouží k odeslání na příslušnou operaci na serveru.</span><span class="sxs-lookup"><span data-stu-id="b3568-124">This name is used to dispatch to the appropriate operation on the server.</span></span> <span data-ttu-id="b3568-125">Pak převezme pole objektů parametrů a serializace data parametrů do řetězce dotazu identifikátoru URI pomocí názvů parametrů a hodnot převedených <xref:System.ComponentModel.TypeConverter> třídou.</span><span class="sxs-lookup"><span data-stu-id="b3568-125">It then takes the array of parameter objects and serializes the parameter data to the URI query string using parameter names and the values converted by the <xref:System.ComponentModel.TypeConverter> class.</span></span> <span data-ttu-id="b3568-126">Vlastnosti <xref:System.ServiceModel.Channels.MessageHeaders.To%2A> a<xref:System.ServiceModel.Channels.MessageProperties.Via%2A> se pak nastaví na tento identifikátor URI.</span><span class="sxs-lookup"><span data-stu-id="b3568-126">The <xref:System.ServiceModel.Channels.MessageHeaders.To%2A> and <xref:System.ServiceModel.Channels.MessageProperties.Via%2A> properties are then set to this URI.</span></span> <span data-ttu-id="b3568-127"><xref:System.ServiceModel.Channels.MessageProperties>je k dispozici <xref:System.ServiceModel.Channels.Message.Properties%2A> prostřednictvím vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="b3568-127"><xref:System.ServiceModel.Channels.MessageProperties> is accessed through the <xref:System.ServiceModel.Channels.Message.Properties%2A> property.</span></span>  
  
- <span data-ttu-id="b3568-128">V metodě na serveru načte formátovací modul `Via` identifikátor URI ve vlastnostech zprávy příchozího požadavku. `IDispatchMessageFormatter.DeserializeRequest`</span><span class="sxs-lookup"><span data-stu-id="b3568-128">In the `IDispatchMessageFormatter.DeserializeRequest` method on the server, the formatter retrieves the `Via` URI in the incoming request message properties.</span></span> <span data-ttu-id="b3568-129">Analyzuje páry název-hodnota v řetězci dotazu URI na názvy parametrů a hodnoty a používá názvy parametrů a hodnoty k naplnění pole parametrů předaných metodě.</span><span class="sxs-lookup"><span data-stu-id="b3568-129">It parses the name-value pairs in the URI query string into parameter names and values and uses the parameter names and values to populate the array of parameters passed into the method.</span></span> <span data-ttu-id="b3568-130">Všimněte si, že operace odeslání operace již proběhla, takže se v této metodě ignoruje přípona názvu operace.</span><span class="sxs-lookup"><span data-stu-id="b3568-130">Note that operation dispatch has already occurred, so the operation name suffix is ignored in this method.</span></span>  
  
 <span data-ttu-id="b3568-131">Základě</span><span class="sxs-lookup"><span data-stu-id="b3568-131">Response:</span></span>  
  
- <span data-ttu-id="b3568-132">V této ukázce se HTTP GET používá jenom pro požadavek.</span><span class="sxs-lookup"><span data-stu-id="b3568-132">In this sample, HTTP GET is used only for the request.</span></span> <span data-ttu-id="b3568-133">Formátovací modul deleguje odeslání odpovědi do původního formátovacího modulu, který by byl použit k vygenerování zprávy XML.</span><span class="sxs-lookup"><span data-stu-id="b3568-133">The formatter delegates the sending of the response to the original formatter that would have been used to generate an XML message.</span></span> <span data-ttu-id="b3568-134">Jedním z cílů této ukázky je Ukázat, jak se dá implementovat takový formátovací modul.</span><span class="sxs-lookup"><span data-stu-id="b3568-134">One of the goals of this sample is to show how such a delegating formatter can be implemented.</span></span>  
  
### <a name="uripathsuffixoperationselector-class"></a><span data-ttu-id="b3568-135">UriPathSuffixOperationSelector – třída</span><span class="sxs-lookup"><span data-stu-id="b3568-135">UriPathSuffixOperationSelector Class</span></span>  
 <span data-ttu-id="b3568-136"><xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> Rozhraní umožňuje uživatelům implementovat vlastní logiku, pro kterou operace by měla být odeslána konkrétní zpráva.</span><span class="sxs-lookup"><span data-stu-id="b3568-136">The <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> interface enables users to implement their own logic for which operation a particular message should be dispatched.</span></span>  
  
 <span data-ttu-id="b3568-137">V této ukázce `UriPathSuffixOperationSelector` musí být na serveru implementována aplikace, aby bylo možné vybrat příslušnou operaci, protože název operace je obsažen v identifikátoru URI požadavku HTTP, nikoli jako záhlaví akce ve zprávě.</span><span class="sxs-lookup"><span data-stu-id="b3568-137">In this sample, `UriPathSuffixOperationSelector` must be implemented on the server to select the appropriate operation because the operation name is included in the HTTP GET URI rather than an action header in the message.</span></span> <span data-ttu-id="b3568-138">Ukázka je nastavena tak, aby povolovala pouze názvy operací nerozlišující malá a velká písmena.</span><span class="sxs-lookup"><span data-stu-id="b3568-138">The sample is set up to allow only case-insensitive operation names.</span></span>  
  
 <span data-ttu-id="b3568-139">Metoda přijme příchozí zprávu a vyhledá `Via` identifikátor URI ve vlastnostech zprávy. `SelectOperation`</span><span class="sxs-lookup"><span data-stu-id="b3568-139">The `SelectOperation` method takes the incoming message and looks up the `Via` URI in its message properties.</span></span> <span data-ttu-id="b3568-140">Extrahuje příponu názvu operace z identifikátoru URI, vyhledá interní tabulku, aby získala název operace, na kterou by měla být zpráva odeslána, a vrátí tento název operace.</span><span class="sxs-lookup"><span data-stu-id="b3568-140">It extracts the operation name suffix from the URI, looks up an internal table to get the operation name that the message should be dispatched to, and returns that operation name.</span></span>  
  
### <a name="enablehttpgetrequestsbehavior-class"></a><span data-ttu-id="b3568-141">EnableHttpGetRequestsBehavior – třída</span><span class="sxs-lookup"><span data-stu-id="b3568-141">EnableHttpGetRequestsBehavior Class</span></span>  
 <span data-ttu-id="b3568-142">`UriPathSuffixOperationSelector` Komponentu lze nastavit programově nebo prostřednictvím chování koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="b3568-142">The `UriPathSuffixOperationSelector` component can be set up programmatically or through an endpoint behavior.</span></span> <span data-ttu-id="b3568-143">Ukázka implementuje `EnableHttpGetRequestsBehavior` chování, které je zadáno v konfiguračním souboru aplikace služby.</span><span class="sxs-lookup"><span data-stu-id="b3568-143">The sample implements the `EnableHttpGetRequestsBehavior` behavior, which is specified in service’s application configuration file.</span></span>  
  
 <span data-ttu-id="b3568-144">Na serveru:</span><span class="sxs-lookup"><span data-stu-id="b3568-144">On the server:</span></span>  
  
 <span data-ttu-id="b3568-145"><xref:System.ServiceModel.Dispatcher.DispatchRuntime.OperationSelector%2A> Je nastaven<xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> na implementaci.</span><span class="sxs-lookup"><span data-stu-id="b3568-145">The <xref:System.ServiceModel.Dispatcher.DispatchRuntime.OperationSelector%2A> is set to the <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> implementation.</span></span>  
  
 <span data-ttu-id="b3568-146">Ve výchozím nastavení používá WCF Filtr adres přesně podle potřeby.</span><span class="sxs-lookup"><span data-stu-id="b3568-146">By default, WCF uses an exact-match address filter.</span></span> <span data-ttu-id="b3568-147">Identifikátor URI příchozí zprávy obsahuje příponu názvu operace následovaný řetězcem dotazu, který obsahuje data parametrů, takže chování koncového bodu také změní Filtr adres tak, aby byl filtrem shody předpon.</span><span class="sxs-lookup"><span data-stu-id="b3568-147">The URI on the incoming message contains an operation name suffix followed by a query string that contains parameter data, so the endpoint behavior also changes the address filter to be a prefix match filter.</span></span> <span data-ttu-id="b3568-148">Pro tento účel používá<xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter> WCF.</span><span class="sxs-lookup"><span data-stu-id="b3568-148">It uses the WCF<xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter> for this purpose.</span></span>  
  
### <a name="installing-operation-formatters"></a><span data-ttu-id="b3568-149">Instalace formátovacích modulů operací</span><span class="sxs-lookup"><span data-stu-id="b3568-149">Installing operation formatters</span></span>  
 <span data-ttu-id="b3568-150">Chování operací, které určují formátovací modul, je jedinečné.</span><span class="sxs-lookup"><span data-stu-id="b3568-150">Operation behaviors that specify formatters are unique.</span></span> <span data-ttu-id="b3568-151">Toto chování je vždy implementováno ve výchozím nastavení pro každou operaci pro vytvoření formátovacího modulu nezbytné operace.</span><span class="sxs-lookup"><span data-stu-id="b3568-151">One such behavior is always implemented by default for every operation to create the necessary operation formatter.</span></span> <span data-ttu-id="b3568-152">Toto chování ale vypadá stejně jako jiné chování operace; nelze je identifikovat žádným jiným atributem.</span><span class="sxs-lookup"><span data-stu-id="b3568-152">However, these behaviors look like just another operation behavior; they are not identifiable by any other attribute.</span></span> <span data-ttu-id="b3568-153">Chcete-li nainstalovat náhradní chování, implementace musí vyhledat specifické chování formátovacího modulu, které jsou ve výchozím nastavení nainstalovány nástrojem WCF Type Loader, a buď ho nahradit, nebo přidat kompatibilní chování, které se spustí po výchozím chování.</span><span class="sxs-lookup"><span data-stu-id="b3568-153">To install a replacement behavior, the implementation must look for specific formatter behaviors that are installed by the WCF type loader by default and either replace it or add a compatible behavior to run after the default behavior.</span></span>  
  
 <span data-ttu-id="b3568-154">Chování těchto formátovacích funkcí operací se dá nastavit programově před voláním <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A?displayProperty=nameWithType> nebo zadáním chování operace, která se spustí po výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="b3568-154">These operation formatters behaviors can be set up programmatically prior to calling <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A?displayProperty=nameWithType> or by specifying an operation behavior that is executed after the default one.</span></span> <span data-ttu-id="b3568-155">Nelze jej však snadno nastavit pomocí chování koncového bodu (a proto podle konfigurace), protože model chování neumožňuje chování nahradit jiná chování nebo jinak upravovat strom popisů.</span><span class="sxs-lookup"><span data-stu-id="b3568-155">However, it cannot easily be set up by an endpoint behavior (and therefore by configuration) because the behavior model does not allow a behavior to replace other behaviors or otherwise modify the description tree.</span></span>  
  
 <span data-ttu-id="b3568-156">Na klientovi:</span><span class="sxs-lookup"><span data-stu-id="b3568-156">On the client:</span></span>  
  
 <span data-ttu-id="b3568-157"><xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> Implementace musí být implementována tak, aby mohla převést požadavky na požadavky HTTP GET a delegovat na původní formátovací modul pro odpovědi.</span><span class="sxs-lookup"><span data-stu-id="b3568-157">The <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> implementation must be implemented so that it can convert the requests into HTTP GET requests and delegate to the original formatter for responses.</span></span> <span data-ttu-id="b3568-158">To se provádí voláním `EnableHttpGetRequestsBehavior.ReplaceFormatterBehavior` pomocné metody.</span><span class="sxs-lookup"><span data-stu-id="b3568-158">This is done by calling the `EnableHttpGetRequestsBehavior.ReplaceFormatterBehavior` helper method.</span></span>  
  
 <span data-ttu-id="b3568-159">To je nutné provést před voláním `CreateChannel`.</span><span class="sxs-lookup"><span data-stu-id="b3568-159">This must be done before calling `CreateChannel`.</span></span>  
  
```  
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
  
 <span data-ttu-id="b3568-160">Na serveru:</span><span class="sxs-lookup"><span data-stu-id="b3568-160">On the server:</span></span>  
  
- <span data-ttu-id="b3568-161"><xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> Rozhraní musí být implementováno, aby mohl číst požadavky HTTP GET a delegovat na původní formátovací modul pro psaní odpovědí.</span><span class="sxs-lookup"><span data-stu-id="b3568-161">The <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> interface must be implemented so that it can read HTTP GET requests and delegate to the original formatter for writing responses.</span></span> <span data-ttu-id="b3568-162">To se provádí voláním stejné `EnableHttpGetRequestsBehavior.ReplaceFormatterBehavior` pomocné metody jako klient (viz předchozí ukázka kódu).</span><span class="sxs-lookup"><span data-stu-id="b3568-162">This is done by calling the same `EnableHttpGetRequestsBehavior.ReplaceFormatterBehavior` helper method as the client (see the previous code sample).</span></span>  
  
- <span data-ttu-id="b3568-163">To je nutné provést před <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> voláním metody.</span><span class="sxs-lookup"><span data-stu-id="b3568-163">This must be done before <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> is called.</span></span> <span data-ttu-id="b3568-164">V této ukázce ukážeme, jak je formátovací modul před voláním <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>ručně změněn.</span><span class="sxs-lookup"><span data-stu-id="b3568-164">In this sample, we show how the formatter is manually modified before calling <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>.</span></span> <span data-ttu-id="b3568-165">Dalším způsobem, jak dosáhnout stejného účelu, je odvodit třídu z <xref:System.ServiceModel.ServiceHost> , která provádí `EnableHttpGetRequestsBehavior.ReplaceFormatterBehavior` volání před otevřením (příklady najdete v dokumentaci k hostování a ukázky).</span><span class="sxs-lookup"><span data-stu-id="b3568-165">Another way to achieve the same thing is to derive a class from <xref:System.ServiceModel.ServiceHost> that makes the calls to `EnableHttpGetRequestsBehavior.ReplaceFormatterBehavior` before opening (please see hosting documentation and samples for examples).</span></span>  
  
### <a name="user-experience"></a><span data-ttu-id="b3568-166">Činnost koncového uživatele</span><span class="sxs-lookup"><span data-stu-id="b3568-166">User experience</span></span>  
 <span data-ttu-id="b3568-167">Na serveru:</span><span class="sxs-lookup"><span data-stu-id="b3568-167">On the server:</span></span>  
  
- <span data-ttu-id="b3568-168">Implementace serveru `ICalculator` se nemusí měnit.</span><span class="sxs-lookup"><span data-stu-id="b3568-168">The server `ICalculator` implementation does not need to change.</span></span>  
  
- <span data-ttu-id="b3568-169">Soubor App. config pro službu musí používat vlastní vazbu POX, která nastaví `messageVersion` atribut `textMessageEncoding` elementu na `None`.</span><span class="sxs-lookup"><span data-stu-id="b3568-169">The App.config for the service must use a custom POX binding that sets the `messageVersion` attribute of the `textMessageEncoding` element to `None`.</span></span>  
  
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
  
- <span data-ttu-id="b3568-170">Soubor App. config pro službu musí také určovat vlastní `EnableHttpGetRequestsBehavior` tím, že ho přidá do části rozšíření chování a použije ho.</span><span class="sxs-lookup"><span data-stu-id="b3568-170">The App.config for the service also must specify the custom `EnableHttpGetRequestsBehavior` by adding it to the behavior extensions section and using it.</span></span>  
  
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
  
- <span data-ttu-id="b3568-171">Přidejte formátovací modul operací před voláním <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>.</span><span class="sxs-lookup"><span data-stu-id="b3568-171">Add operation formatters before calling <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>.</span></span>  
  
 <span data-ttu-id="b3568-172">Na klientovi:</span><span class="sxs-lookup"><span data-stu-id="b3568-172">On the client:</span></span>  
  
- <span data-ttu-id="b3568-173">Implementace klienta se nemusí měnit.</span><span class="sxs-lookup"><span data-stu-id="b3568-173">The client implementation does not need to change.</span></span>  
  
- <span data-ttu-id="b3568-174">Soubor App. config pro klienta musí používat vlastní vazbu POX, která nastaví `messageVersion` atribut `textMessageEncoding` elementu na `None`.</span><span class="sxs-lookup"><span data-stu-id="b3568-174">The App.config for the client must use a custom POX binding that sets the `messageVersion` attribute of the `textMessageEncoding` element to `None`.</span></span> <span data-ttu-id="b3568-175">Jedním z rozdílů od služby je, že klient musí povolit ruční adresování, aby bylo možné upravit adresu odchozí na.</span><span class="sxs-lookup"><span data-stu-id="b3568-175">One difference from the service is that the client must enable manual addressing so that the outgoing To address can be modified.</span></span>  
  
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
  
- <span data-ttu-id="b3568-176">Soubor App. config pro klienta musí určovat stejný vlastní `EnableHttpGetRequestsBehavior` jako server.</span><span class="sxs-lookup"><span data-stu-id="b3568-176">The App.config for the client must specify the same custom `EnableHttpGetRequestsBehavior` as the server.</span></span>  
  
- <span data-ttu-id="b3568-177">Přidejte formátovací modul operací před voláním <xref:System.ServiceModel.ChannelFactory%601.CreateChannel>.</span><span class="sxs-lookup"><span data-stu-id="b3568-177">Add operation formatters before calling <xref:System.ServiceModel.ChannelFactory%601.CreateChannel>.</span></span>  
  
 <span data-ttu-id="b3568-178">Při spuštění ukázky se v okně konzoly klienta zobrazí požadavky na operace a odpovědi.</span><span class="sxs-lookup"><span data-stu-id="b3568-178">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="b3568-179">Všechny čtyři operace (sčítání, odčítání, násobení a dělení) musí být úspěšné.</span><span class="sxs-lookup"><span data-stu-id="b3568-179">All four operations (Add, Subtract, Multiply, and Divide) must succeed.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="b3568-180">Ukázky už můžou být na vašem počítači nainstalované.</span><span class="sxs-lookup"><span data-stu-id="b3568-180">The samples may already be installed on your machine.</span></span> <span data-ttu-id="b3568-181">Než budete pokračovat, vyhledejte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="b3568-181">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="b3568-182">Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek.</span><span class="sxs-lookup"><span data-stu-id="b3568-182">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="b3568-183">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="b3568-183">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Formatters\QueryStringFormatter`  
  
##### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="b3568-184">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="b3568-184">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="b3568-185">Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="b3568-185">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="b3568-186">Při sestavování řešení postupujte podle pokynů v tématu sestavování [ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="b3568-186">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="b3568-187">Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="b3568-187">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
