---
title: Formátovací modul a selektor operace
ms.date: 03/30/2017
ms.assetid: 1c27e9fe-11f8-4377-8140-828207b98a0e
ms.openlocfilehash: 3843feacca0da6118ecc9d0f54a2cb088865caaa
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59100402"
---
# <a name="operation-formatter-and-operation-selector"></a><span data-ttu-id="bf1ce-102">Formátovací modul a selektor operace</span><span class="sxs-lookup"><span data-stu-id="bf1ce-102">Operation Formatter and Operation Selector</span></span>
<span data-ttu-id="bf1ce-103">Tato ukázka předvádí, jak lze umožňující data zprávy v jiném formátu z co WCF očekává, že body rozšiřitelnosti Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="bf1ce-103">This sample demonstrates how Windows Communication Foundation (WCF) extensibility points can be used to allow message data in a different format from what WCF expects.</span></span> <span data-ttu-id="bf1ce-104">Ve výchozím nastavení, formátování WCF očekávat parametry metody mají být zahrnuty v části `soap:body` elementu.</span><span class="sxs-lookup"><span data-stu-id="bf1ce-104">By default, WCF formatters expect method parameters to be included under the `soap:body` element.</span></span> <span data-ttu-id="bf1ce-105">Vzorek ukazuje, jak implementovat vlastní operace formátování, které místo toho analyzuje data parametrů z řetězce dotazu HTTP GET a volá metody pomocí tato data.</span><span class="sxs-lookup"><span data-stu-id="bf1ce-105">The sample shows how to implement a custom operation formatter that parses parameter data from an HTTP GET query string instead and invokes methods using that data.</span></span>  
  
 <span data-ttu-id="bf1ce-106">Vzorek je založen na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md), která implementuje `ICalculator` kontrakt služby.</span><span class="sxs-lookup"><span data-stu-id="bf1ce-106">The sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md), which implements the `ICalculator` service contract.</span></span> <span data-ttu-id="bf1ce-107">To ukazuje, jak přidat, odečte krát a dělení zprávy lze změnit na požadavky klienta na server pomocí HTTP GET a HTTP POST s POX zprávy pro server klient odpovědi.</span><span class="sxs-lookup"><span data-stu-id="bf1ce-107">It shows how Add, Subtract, Multiply, and Divide messages can be changed to use HTTP GET for client-to-server requests and HTTP POST with POX messages for server-to-client responses.</span></span>  
  
 <span data-ttu-id="bf1ce-108">Uděláte to tak, ukázka poskytuje následující:</span><span class="sxs-lookup"><span data-stu-id="bf1ce-108">To do so, the sample provides the following:</span></span>  
  
-   `QueryStringFormatter`<span data-ttu-id="bf1ce-109">, která implementuje <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> a <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> pro klienta a serveru, v uvedeném pořadí a zpracovává data v řetězci dotazu.</span><span class="sxs-lookup"><span data-stu-id="bf1ce-109">, which implements <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> and <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> for the client and server, respectively, and processes the data in the query string.</span></span>  
  
-   `UriOperationSelector`<span data-ttu-id="bf1ce-110">, která implementuje <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> na serveru k provedení operace odeslání podle názvu operace v požadavek GET.</span><span class="sxs-lookup"><span data-stu-id="bf1ce-110">, which implements <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> on the server to perform operation dispatch based on the operation name in the GET request.</span></span>  
  
-   `EnableHttpGetRequestsBehavior` <span data-ttu-id="bf1ce-111">konfigurace koncového bodu chování (a odpovídající), který modulu runtime přidá selektor potřebné operace.</span><span class="sxs-lookup"><span data-stu-id="bf1ce-111">endpoint behavior (and corresponding configuration), which adds the necessary operation selector to the runtime.</span></span>  
  
-   <span data-ttu-id="bf1ce-112">Ukazuje, jak vložit nový formátovací modul operace do modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="bf1ce-112">Shows how to insert a new operation formatter into the runtime.</span></span>  
  
-   <span data-ttu-id="bf1ce-113">V této ukázce jsou klient a služba konzolové aplikace (.exe).</span><span class="sxs-lookup"><span data-stu-id="bf1ce-113">In this sample, both the client and the service are console applications (.exe).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bf1ce-114">Postup a sestavení pokynů pro tuto ukázku se nachází na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="bf1ce-114">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
## <a name="key-concepts"></a><span data-ttu-id="bf1ce-115">Klíčové koncepty</span><span class="sxs-lookup"><span data-stu-id="bf1ce-115">Key Concepts</span></span>  
 `QueryStringFormatter` <span data-ttu-id="bf1ce-116">-Operace formátování je součástí WCF, který je zodpovědný za převod zprávu do pole parametru objekty a pole objektů parametr do zprávy.</span><span class="sxs-lookup"><span data-stu-id="bf1ce-116">- The operation formatter is the component in WCF that is responsible for converting a message into an array of parameter objects and an array of parameter objects into a message.</span></span> <span data-ttu-id="bf1ce-117">To se provádí na straně klienta pomocí <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> rozhraní a na serveru se službou <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="bf1ce-117">This is done on the client using the <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> interface and on the server with the <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> interface.</span></span> <span data-ttu-id="bf1ce-118">Tato rozhraní umožňují uživatelům získat zprávy požadavků a odpovědí z `Serialize` a `Deserialize` metody.</span><span class="sxs-lookup"><span data-stu-id="bf1ce-118">These interfaces enable users to get the request and response messages from the `Serialize` and `Deserialize` methods.</span></span>  
  
 <span data-ttu-id="bf1ce-119">V této ukázce `QueryStringFormatter` implementuje oba z těchto rozhraní a je implementována v klientem a serverem.</span><span class="sxs-lookup"><span data-stu-id="bf1ce-119">In this sample, `QueryStringFormatter` implements both of these interfaces and is implemented on the client and server.</span></span>  
  
 <span data-ttu-id="bf1ce-120">Žádost:</span><span class="sxs-lookup"><span data-stu-id="bf1ce-120">Request:</span></span>  
  
-   <span data-ttu-id="bf1ce-121">Ukázka používá <xref:System.ComponentModel.TypeConverter> třída převést parametr data ve zprávě požadavku do a z řetězce.</span><span class="sxs-lookup"><span data-stu-id="bf1ce-121">The sample uses the <xref:System.ComponentModel.TypeConverter> class to convert parameter data in the request message to and from strings.</span></span> <span data-ttu-id="bf1ce-122">Pokud <xref:System.ComponentModel.TypeConverter> není k dispozici pro konkrétní typ, vyvolá formátování ukázka výjimku.</span><span class="sxs-lookup"><span data-stu-id="bf1ce-122">If a <xref:System.ComponentModel.TypeConverter> is not available for a specific type, the sample formatter throws an exception.</span></span>  
  
-   <span data-ttu-id="bf1ce-123">V `IClientMessageFormatter.SerializeRequest` metody na straně klienta, formátovací modul vytváří identifikátor URI s příslušnou adresu a přidá název operace jako příponu.</span><span class="sxs-lookup"><span data-stu-id="bf1ce-123">In the `IClientMessageFormatter.SerializeRequest` method on the client, the formatter creates a URI with the appropriate To address and appends the operation name as a suffix.</span></span> <span data-ttu-id="bf1ce-124">Tento název se používá k odeslání do příslušné operace na serveru.</span><span class="sxs-lookup"><span data-stu-id="bf1ce-124">This name is used to dispatch to the appropriate operation on the server.</span></span> <span data-ttu-id="bf1ce-125">Potom přijímá pole objektů parametr a serializuje data parametru řetězce dotazu URI pomocí názvy parametrů a hodnot pomocí převedeny <xref:System.ComponentModel.TypeConverter> třídy.</span><span class="sxs-lookup"><span data-stu-id="bf1ce-125">It then takes the array of parameter objects and serializes the parameter data to the URI query string using parameter names and the values converted by the <xref:System.ComponentModel.TypeConverter> class.</span></span> <span data-ttu-id="bf1ce-126"><xref:System.ServiceModel.Channels.MessageHeaders.To%2A> a <xref:System.ServiceModel.Channels.MessageProperties.Via%2A> vlastnosti jsou pak nastavte na tento identifikátor URI.</span><span class="sxs-lookup"><span data-stu-id="bf1ce-126">The <xref:System.ServiceModel.Channels.MessageHeaders.To%2A> and <xref:System.ServiceModel.Channels.MessageProperties.Via%2A> properties are then set to this URI.</span></span> <xref:System.ServiceModel.Channels.MessageProperties> <span data-ttu-id="bf1ce-127">je přístupný prostřednictvím <xref:System.ServiceModel.Channels.Message.Properties%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="bf1ce-127">is accessed through the <xref:System.ServiceModel.Channels.Message.Properties%2A> property.</span></span>  
  
-   <span data-ttu-id="bf1ce-128">V `IDispatchMessageFormatter.DeserializeRequest` načte formátovací modul metoda na serveru, `Via` identifikátor URI ve vlastnostech příchozí zprávy požadavku.</span><span class="sxs-lookup"><span data-stu-id="bf1ce-128">In the `IDispatchMessageFormatter.DeserializeRequest` method on the server, the formatter retrieves the `Via` URI in the incoming request message properties.</span></span> <span data-ttu-id="bf1ce-129">Analyzuje dvojice název hodnota v řetězci dotazu identifikátoru URI do názvy parametrů a hodnot a využije názvy parametrů a hodnoty k vyplnění pole parametry předané do metody.</span><span class="sxs-lookup"><span data-stu-id="bf1ce-129">It parses the name-value pairs in the URI query string into parameter names and values and uses the parameter names and values to populate the array of parameters passed into the method.</span></span> <span data-ttu-id="bf1ce-130">Všimněte si, že operace odeslání již došlo, tak v této metodě se ignoruje přípona názvu operace.</span><span class="sxs-lookup"><span data-stu-id="bf1ce-130">Note that operation dispatch has already occurred, so the operation name suffix is ignored in this method.</span></span>  
  
 <span data-ttu-id="bf1ce-131">Odpověď:</span><span class="sxs-lookup"><span data-stu-id="bf1ce-131">Response:</span></span>  
  
-   <span data-ttu-id="bf1ce-132">V této ukázce GET protokolu HTTP se používá pouze pro daný požadavek.</span><span class="sxs-lookup"><span data-stu-id="bf1ce-132">In this sample, HTTP GET is used only for the request.</span></span> <span data-ttu-id="bf1ce-133">Formátovací modul delegátů, odeslání odpovědi na původní formátovací modul, který by byl použit ke generování hlášení XML.</span><span class="sxs-lookup"><span data-stu-id="bf1ce-133">The formatter delegates the sending of the response to the original formatter that would have been used to generate an XML message.</span></span> <span data-ttu-id="bf1ce-134">Jedním z cílů tohoto příkladu je zobrazit, jak je možné implementovat Delegující formátování.</span><span class="sxs-lookup"><span data-stu-id="bf1ce-134">One of the goals of this sample is to show how such a delegating formatter can be implemented.</span></span>  
  
### <a name="uripathsuffixoperationselector-class"></a><span data-ttu-id="bf1ce-135">Třída UriPathSuffixOperationSelector</span><span class="sxs-lookup"><span data-stu-id="bf1ce-135">UriPathSuffixOperationSelector Class</span></span>  
 <span data-ttu-id="bf1ce-136"><xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> Rozhraní umožňuje uživatelům implementovat své vlastní logiky, které operace by měla konkrétní zpráva odeslána.</span><span class="sxs-lookup"><span data-stu-id="bf1ce-136">The <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> interface enables users to implement their own logic for which operation a particular message should be dispatched.</span></span>  
  
 <span data-ttu-id="bf1ce-137">V této ukázce `UriPathSuffixOperationSelector` musí implementovat na server vybrat příslušnou operaci, protože název operace je součástí identifikátoru URI HTTP GET, spíše než hlavičku akce ve zprávě.</span><span class="sxs-lookup"><span data-stu-id="bf1ce-137">In this sample, `UriPathSuffixOperationSelector` must be implemented on the server to select the appropriate operation because the operation name is included in the HTTP GET URI rather than an action header in the message.</span></span> <span data-ttu-id="bf1ce-138">Ukázka je nastavit a povolit pouze malá a velká písmena operace názvy.</span><span class="sxs-lookup"><span data-stu-id="bf1ce-138">The sample is set up to allow only case-insensitive operation names.</span></span>  
  
 <span data-ttu-id="bf1ce-139">`SelectOperation` Metoda přijímá příchozí zprávy a vyhledá `Via` identifikátor URI ve vlastnostech zprávy.</span><span class="sxs-lookup"><span data-stu-id="bf1ce-139">The `SelectOperation` method takes the incoming message and looks up the `Via` URI in its message properties.</span></span> <span data-ttu-id="bf1ce-140">Extrahuje příponu názvu operace z identifikátoru URI, vyhledá a získat tak název operace, které zpráva by měla být odesláno do interní tabulku a vrátí název této operace.</span><span class="sxs-lookup"><span data-stu-id="bf1ce-140">It extracts the operation name suffix from the URI, looks up an internal table to get the operation name that the message should be dispatched to, and returns that operation name.</span></span>  
  
### <a name="enablehttpgetrequestsbehavior-class"></a><span data-ttu-id="bf1ce-141">EnableHttpGetRequestsBehavior Class</span><span class="sxs-lookup"><span data-stu-id="bf1ce-141">EnableHttpGetRequestsBehavior Class</span></span>  
 <span data-ttu-id="bf1ce-142">`UriPathSuffixOperationSelector` Komponenty lze nastavit programově nebo prostřednictvím chování koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="bf1ce-142">The `UriPathSuffixOperationSelector` component can be set up programmatically or through an endpoint behavior.</span></span> <span data-ttu-id="bf1ce-143">Ukázka implementuje `EnableHttpGetRequestsBehavior` chování, které je určeno v konfiguračním souboru aplikace služby.</span><span class="sxs-lookup"><span data-stu-id="bf1ce-143">The sample implements the `EnableHttpGetRequestsBehavior` behavior, which is specified in service’s application configuration file.</span></span>  
  
 <span data-ttu-id="bf1ce-144">Na serveru:</span><span class="sxs-lookup"><span data-stu-id="bf1ce-144">On the server:</span></span>  
  
 <span data-ttu-id="bf1ce-145"><xref:System.ServiceModel.Dispatcher.DispatchRuntime.OperationSelector%2A> Nastavena <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> implementace.</span><span class="sxs-lookup"><span data-stu-id="bf1ce-145">The <xref:System.ServiceModel.Dispatcher.DispatchRuntime.OperationSelector%2A> is set to the <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> implementation.</span></span>  
  
 <span data-ttu-id="bf1ce-146">Ve výchozím nastavení používá WCF filtr adresy přesnou shodu.</span><span class="sxs-lookup"><span data-stu-id="bf1ce-146">By default, WCF uses an exact-match address filter.</span></span> <span data-ttu-id="bf1ce-147">Identifikátor URI v příchozí zprávě obsahuje příponou název operace, za nímž následuje řetězec dotazu, který obsahuje data parametrů, takže chování koncového bodu se také změní filtr adres bude předpony, které odpovídají filtru.</span><span class="sxs-lookup"><span data-stu-id="bf1ce-147">The URI on the incoming message contains an operation name suffix followed by a query string that contains parameter data, so the endpoint behavior also changes the address filter to be a prefix match filter.</span></span> <span data-ttu-id="bf1ce-148">Používá WCF<xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter> pro tento účel.</span><span class="sxs-lookup"><span data-stu-id="bf1ce-148">It uses the WCF<xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter> for this purpose.</span></span>  
  
### <a name="installing-operation-formatters"></a><span data-ttu-id="bf1ce-149">Instalace operace formátování</span><span class="sxs-lookup"><span data-stu-id="bf1ce-149">Installing operation formatters</span></span>  
 <span data-ttu-id="bf1ce-150">Chování operace, které zadejte formátovací moduly jsou jedinečné.</span><span class="sxs-lookup"><span data-stu-id="bf1ce-150">Operation behaviors that specify formatters are unique.</span></span> <span data-ttu-id="bf1ce-151">Jeden takový chování je vždy implementováno ve výchozím nastavení pro každou operaci vytvoření nezbytných formátovací modul.</span><span class="sxs-lookup"><span data-stu-id="bf1ce-151">One such behavior is always implemented by default for every operation to create the necessary operation formatter.</span></span> <span data-ttu-id="bf1ce-152">Ale těchto projevů vypadat podobně jako jakékoli jiné chování operace; nejsou poznáte ho podle jiného atributu.</span><span class="sxs-lookup"><span data-stu-id="bf1ce-152">However, these behaviors look like just another operation behavior; they are not identifiable by any other attribute.</span></span> <span data-ttu-id="bf1ce-153">Náhradní chování instalace, implementace musí vyhledat konkrétní formátovací modul chování, které jsou nainstalované ve WCF typ zavaděč ve výchozím nastavení a buď ji nahradit nebo přidat kompatibilní chování následný výchozí chování.</span><span class="sxs-lookup"><span data-stu-id="bf1ce-153">To install a replacement behavior, the implementation must look for specific formatter behaviors that are installed by the WCF type loader by default and either replace it or add a compatible behavior to run after the default behavior.</span></span>  
  
 <span data-ttu-id="bf1ce-154">Tyto operace formátování chování lze nastavit programově před voláním <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A?displayProperty=nameWithType> nebo zadáním na operaci chování, která se spustí po výchozí hodnotu.</span><span class="sxs-lookup"><span data-stu-id="bf1ce-154">These operation formatters behaviors can be set up programmatically prior to calling <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A?displayProperty=nameWithType> or by specifying an operation behavior that is executed after the default one.</span></span> <span data-ttu-id="bf1ce-155">Však ho nelze snadno nastavit pomocí chování koncového bodu (a tedy konfigurace) protože model chování nepovoluje chování a nahraďte Další chování nebo jinak upravit stromu popis.</span><span class="sxs-lookup"><span data-stu-id="bf1ce-155">However, it cannot easily be set up by an endpoint behavior (and therefore by configuration) because the behavior model does not allow a behavior to replace other behaviors or otherwise modify the description tree.</span></span>  
  
 <span data-ttu-id="bf1ce-156">Na straně klienta:</span><span class="sxs-lookup"><span data-stu-id="bf1ce-156">On the client:</span></span>  
  
 <span data-ttu-id="bf1ce-157"><xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> Implementace musí být implementované tak, aby ho převést požadavky na požadavky HTTP GET a delegovat na původní formátování odpovědi.</span><span class="sxs-lookup"><span data-stu-id="bf1ce-157">The <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> implementation must be implemented so that it can convert the requests into HTTP GET requests and delegate to the original formatter for responses.</span></span> <span data-ttu-id="bf1ce-158">To se provádí pomocí volání `EnableHttpGetRequestsBehavior.ReplaceFormatterBehavior` Pomocná metoda.</span><span class="sxs-lookup"><span data-stu-id="bf1ce-158">This is done by calling the `EnableHttpGetRequestsBehavior.ReplaceFormatterBehavior` helper method.</span></span>  
  
 <span data-ttu-id="bf1ce-159">To je nutné provést před voláním `CreateChannel`.</span><span class="sxs-lookup"><span data-stu-id="bf1ce-159">This must be done before calling `CreateChannel`.</span></span>  
  
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
  
 <span data-ttu-id="bf1ce-160">Na serveru:</span><span class="sxs-lookup"><span data-stu-id="bf1ce-160">On the server:</span></span>  
  
-   <span data-ttu-id="bf1ce-161"><xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> Musí implementovat rozhraní, tak, aby může číst požadavky HTTP GET a delegovat na původní formátovací modul pro psaní odpovědi.</span><span class="sxs-lookup"><span data-stu-id="bf1ce-161">The <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> interface must be implemented so that it can read HTTP GET requests and delegate to the original formatter for writing responses.</span></span> <span data-ttu-id="bf1ce-162">To se provádí voláním stejné `EnableHttpGetRequestsBehavior.ReplaceFormatterBehavior` pomocnou metodu jako klient (viz předchozí ukázka kódu).</span><span class="sxs-lookup"><span data-stu-id="bf1ce-162">This is done by calling the same `EnableHttpGetRequestsBehavior.ReplaceFormatterBehavior` helper method as the client (see the previous code sample).</span></span>  
  
-   <span data-ttu-id="bf1ce-163">To je nutné provést před <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> je volána.</span><span class="sxs-lookup"><span data-stu-id="bf1ce-163">This must be done before <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> is called.</span></span> <span data-ttu-id="bf1ce-164">V tomto příkladu vám ukážeme, jak formátovací modul ručně změnit před voláním <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>.</span><span class="sxs-lookup"><span data-stu-id="bf1ce-164">In this sample, we show how the formatter is manually modified before calling <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>.</span></span> <span data-ttu-id="bf1ce-165">Jiný způsob, jak dosáhnout stejnou věc je na odvození třídy z <xref:System.ServiceModel.ServiceHost> , která provádí volání na `EnableHttpGetRequestsBehavior.ReplaceFormatterBehavior` před otevřením (podrobnosti najdete na hostování dokumentaci a ukázky pro příklady).</span><span class="sxs-lookup"><span data-stu-id="bf1ce-165">Another way to achieve the same thing is to derive a class from <xref:System.ServiceModel.ServiceHost> that makes the calls to `EnableHttpGetRequestsBehavior.ReplaceFormatterBehavior` before opening (please see hosting documentation and samples for examples).</span></span>  
  
### <a name="user-experience"></a><span data-ttu-id="bf1ce-166">Činnost koncového uživatele</span><span class="sxs-lookup"><span data-stu-id="bf1ce-166">User experience</span></span>  
 <span data-ttu-id="bf1ce-167">Na serveru:</span><span class="sxs-lookup"><span data-stu-id="bf1ce-167">On the server:</span></span>  
  
-   <span data-ttu-id="bf1ce-168">Server `ICalculator` implementace není potřeba změnit.</span><span class="sxs-lookup"><span data-stu-id="bf1ce-168">The server `ICalculator` implementation does not need to change.</span></span>  
  
-   <span data-ttu-id="bf1ce-169">App.config pro službu, musíte použít vlastní POX vazby, který nastaví `messageVersion` atribut `textMessageEncoding` elementu `None`.</span><span class="sxs-lookup"><span data-stu-id="bf1ce-169">The App.config for the service must use a custom POX binding that sets the `messageVersion` attribute of the `textMessageEncoding` element to `None`.</span></span>  
  
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
  
-   <span data-ttu-id="bf1ce-170">Souboru App.config pro službu musíte zadat také vlastní `EnableHttpGetRequestsBehavior` přidáním do oddílu rozšíření chování a jeho použití.</span><span class="sxs-lookup"><span data-stu-id="bf1ce-170">The App.config for the service also must specify the custom `EnableHttpGetRequestsBehavior` by adding it to the behavior extensions section and using it.</span></span>  
  
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
  
-   <span data-ttu-id="bf1ce-171">Přidání operace formátování před voláním <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>.</span><span class="sxs-lookup"><span data-stu-id="bf1ce-171">Add operation formatters before calling <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>.</span></span>  
  
 <span data-ttu-id="bf1ce-172">Na straně klienta:</span><span class="sxs-lookup"><span data-stu-id="bf1ce-172">On the client:</span></span>  
  
-   <span data-ttu-id="bf1ce-173">Implementace klienta není potřeba změnit.</span><span class="sxs-lookup"><span data-stu-id="bf1ce-173">The client implementation does not need to change.</span></span>  
  
-   <span data-ttu-id="bf1ce-174">App.config pro klienta, musíte použít vlastní POX vazby, který nastaví `messageVersion` atribut `textMessageEncoding` elementu `None`.</span><span class="sxs-lookup"><span data-stu-id="bf1ce-174">The App.config for the client must use a custom POX binding that sets the `messageVersion` attribute of the `textMessageEncoding` element to `None`.</span></span> <span data-ttu-id="bf1ce-175">Jedním z rozdílů ze služby je, že klient musí povolit ruční adresování tak, aby odesílaných na adresu je možné upravit.</span><span class="sxs-lookup"><span data-stu-id="bf1ce-175">One difference from the service is that the client must enable manual addressing so that the outgoing To address can be modified.</span></span>  
  
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
  
-   <span data-ttu-id="bf1ce-176">Souboru App.config pro klienta, musíte zadat stejné vlastní `EnableHttpGetRequestsBehavior` jako server.</span><span class="sxs-lookup"><span data-stu-id="bf1ce-176">The App.config for the client must specify the same custom `EnableHttpGetRequestsBehavior` as the server.</span></span>  
  
-   <span data-ttu-id="bf1ce-177">Přidání operace formátování před voláním <xref:System.ServiceModel.ChannelFactory%601.CreateChannel>.</span><span class="sxs-lookup"><span data-stu-id="bf1ce-177">Add operation formatters before calling <xref:System.ServiceModel.ChannelFactory%601.CreateChannel>.</span></span>  
  
 <span data-ttu-id="bf1ce-178">Při spuštění ukázky operace žádosti a odpovědi se zobrazí v okně konzoly klienta.</span><span class="sxs-lookup"><span data-stu-id="bf1ce-178">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="bf1ce-179">Všechny čtyři operace (přidat, odečítání, násobení a rozdělit) musí být úspěšný.</span><span class="sxs-lookup"><span data-stu-id="bf1ce-179">All four operations (Add, Subtract, Multiply, and Divide) must succeed.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="bf1ce-180">Vzorky mohou již být nainstalováno na svém počítači.</span><span class="sxs-lookup"><span data-stu-id="bf1ce-180">The samples may already be installed on your machine.</span></span> <span data-ttu-id="bf1ce-181">Před pokračováním zkontrolujte následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="bf1ce-181">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="bf1ce-182">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="bf1ce-182">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="bf1ce-183">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="bf1ce-183">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Formatters\QuieryStringFormatter`  
  
##### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="bf1ce-184">Chcete-li nastavit, sestavte a spusťte ukázku</span><span class="sxs-lookup"><span data-stu-id="bf1ce-184">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="bf1ce-185">Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="bf1ce-185">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="bf1ce-186">Abyste mohli sestavit řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="bf1ce-186">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="bf1ce-187">Spusťte ukázku v konfiguraci s jedním nebo více počítačů, postupujte podle pokynů v [spouštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="bf1ce-187">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
