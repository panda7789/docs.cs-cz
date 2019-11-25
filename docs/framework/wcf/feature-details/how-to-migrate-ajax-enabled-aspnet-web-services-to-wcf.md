---
title: 'Postupy: Migrace webových služeb ASP.NET s podporou AJAXu na službu WCF'
ms.date: 03/30/2017
ms.assetid: 1428df4d-b18f-4e6d-bd4d-79ab3dd5147c
ms.openlocfilehash: 60e3088b9075464176c328af1f52676a69c4990f
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/12/2019
ms.locfileid: "73976134"
---
# <a name="how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf"></a><span data-ttu-id="6edc1-102">Postupy: Migrace webových služeb ASP.NET s podporou AJAXu na službu WCF</span><span class="sxs-lookup"><span data-stu-id="6edc1-102">How to: Migrate AJAX-Enabled ASP.NET Web Services to WCF</span></span>
<span data-ttu-id="6edc1-103">V tomto tématu jsou popsány postupy pro migraci základní služby ASP.NET AJAX do ekvivalentní služby Windows Communication Foundation WCF (AJAX Enabled).</span><span class="sxs-lookup"><span data-stu-id="6edc1-103">This topic outlines procedures to migrate a basic ASP.NET AJAX service to an equivalent AJAX-enabled Windows Communication Foundation (WCF) service.</span></span> <span data-ttu-id="6edc1-104">Ukazuje, jak vytvořit funkčně ekvivalentní verzi WCF služby ASP.NET AJAX.</span><span class="sxs-lookup"><span data-stu-id="6edc1-104">It shows how to create a functionally equivalent WCF version of an ASP.NET AJAX service.</span></span> <span data-ttu-id="6edc1-105">Tyto dvě služby se pak dají použít souběžně nebo službu WCF můžete použít k nahrazení služby ASP.NET AJAX.</span><span class="sxs-lookup"><span data-stu-id="6edc1-105">The two services can then be used side by side, or the WCF service can be used to replace the ASP.NET AJAX service.</span></span>

 <span data-ttu-id="6edc1-106">Migrace stávající služby ASP.NET AJAX do služby WCF AJAX přináší následující výhody:</span><span class="sxs-lookup"><span data-stu-id="6edc1-106">Migrating an existing ASP.NET AJAX service to a WCF AJAX service gives you the following benefits:</span></span>

- <span data-ttu-id="6edc1-107">Službu AJAX můžete vystavit jako službu SOAP s minimální dodatečnou konfigurací.</span><span class="sxs-lookup"><span data-stu-id="6edc1-107">You can expose your AJAX service as a SOAP service with minimal extra configuration.</span></span>

- <span data-ttu-id="6edc1-108">Můžete využít výhod funkcí WCF, jako je trasování a tak dále.</span><span class="sxs-lookup"><span data-stu-id="6edc1-108">You can benefit from WCF features such as tracing, and so on.</span></span>

 <span data-ttu-id="6edc1-109">V následujících postupech se předpokládá, že používáte Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="6edc1-109">The following procedures assume that you are using Visual Studio 2012.</span></span>

 <span data-ttu-id="6edc1-110">Kód, který je výsledkem postupů popsaných v tomto tématu, je uveden v příkladu, který následuje po postupech.</span><span class="sxs-lookup"><span data-stu-id="6edc1-110">The code that results from the procedures outlined in this topic is provided in the example following the procedures.</span></span>

 <span data-ttu-id="6edc1-111">Další informace o vystavení služby WCF prostřednictvím koncového bodu s povoleným AJAX naleznete v tématu [How to: use Configuration to Add the ASP.NET AJAX Endpoint](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md) .</span><span class="sxs-lookup"><span data-stu-id="6edc1-111">For more information about exposing a WCF service through an AJAX-enabled endpoint, see the [How to: Use Configuration to Add an ASP.NET AJAX Endpoint](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md) topic.</span></span>

### <a name="to-create-and-test-the-aspnet-web-service-application"></a><span data-ttu-id="6edc1-112">Vytvoření a otestování aplikace webové služby ASP.NET</span><span class="sxs-lookup"><span data-stu-id="6edc1-112">To create and test the ASP.NET Web service application</span></span>

1. <span data-ttu-id="6edc1-113">Otevřete Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="6edc1-113">Open Visual Studio 2012.</span></span>

2. <span data-ttu-id="6edc1-114">V nabídce **soubor** vyberte možnost **Nový**, **projekt**, pak **Web**a pak vyberte možnost **aplikace webové služby ASP.NET**.</span><span class="sxs-lookup"><span data-stu-id="6edc1-114">From the **File** menu, select **New**, then **Project**, then **Web**, and then select **ASP.NET Web Service Application**.</span></span>

3. <span data-ttu-id="6edc1-115">Pojmenujte projekt `ASPHello` a klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="6edc1-115">Name the project `ASPHello` and click **OK**.</span></span>

4. <span data-ttu-id="6edc1-116">Odkomentujte řádek v souboru Service1.asmx.cs, který obsahuje `System.Web.Script.Services.ScriptService]` pro povolení AJAX pro tuto službu.</span><span class="sxs-lookup"><span data-stu-id="6edc1-116">Uncomment the line in the Service1.asmx.cs file that contains `System.Web.Script.Services.ScriptService]` to enable AJAX for this service.</span></span>

5. <span data-ttu-id="6edc1-117">V nabídce **sestavení** vyberte **Sestavit řešení**.</span><span class="sxs-lookup"><span data-stu-id="6edc1-117">From the **Build** menu, select **Build Solution**.</span></span>

6. <span data-ttu-id="6edc1-118">V nabídce **ladění** vyberte **Spustit bez ladění**.</span><span class="sxs-lookup"><span data-stu-id="6edc1-118">From the **Debug** menu, select **Start Without Debugging**.</span></span>

7. <span data-ttu-id="6edc1-119">Na vygenerované webové stránce vyberte operaci `HelloWorld`.</span><span class="sxs-lookup"><span data-stu-id="6edc1-119">On the Web page generated, select the `HelloWorld` operation.</span></span>

8. <span data-ttu-id="6edc1-120">Klikněte na tlačítko **vyvolat** na stránce `HelloWorld` test.</span><span class="sxs-lookup"><span data-stu-id="6edc1-120">Click the **Invoke** button on the `HelloWorld` test page.</span></span> <span data-ttu-id="6edc1-121">Měla by se zobrazit následující odpověď XML.</span><span class="sxs-lookup"><span data-stu-id="6edc1-121">You should receive the following XML response.</span></span>

    ```xml
    <?xml version="1.0" encoding="utf-8" ?>
    <string xmlns="http://tempuri.org/">Hello World</string>
    ```

9. <span data-ttu-id="6edc1-122">Tato odpověď potvrzuje, že teď máte funkční službu ASP.NET AJAX, a zejména to, že služba nyní nastavila koncový bod na Service1. asmx/HelloWorld, který reaguje na požadavky HTTP POST a vrací XML.</span><span class="sxs-lookup"><span data-stu-id="6edc1-122">This response confirms that you now have a functioning ASP.NET AJAX service and, in particular, that the service has now exposed an endpoint at Service1.asmx/HelloWorld that responds to HTTP POST requests and returns XML.</span></span>

     <span data-ttu-id="6edc1-123">Nyní jste připraveni tuto službu převést na používání služby WCF AJAX.</span><span class="sxs-lookup"><span data-stu-id="6edc1-123">Now you are ready to convert this service to use a WCF AJAX service.</span></span>

### <a name="to-create-an-equivalent-wcf-ajax-service-application"></a><span data-ttu-id="6edc1-124">Vytvoření ekvivalentní aplikace služby WCF AJAX</span><span class="sxs-lookup"><span data-stu-id="6edc1-124">To create an equivalent WCF AJAX service application</span></span>

1. <span data-ttu-id="6edc1-125">Klikněte pravým tlačítkem na projekt **ASPHello** a vyberte **Přidat**, **Nová položka**a potom **službu WCF s podporou jazyka AJAX**.</span><span class="sxs-lookup"><span data-stu-id="6edc1-125">Right-click the **ASPHello** project and select **Add**, then **New Item**, and then **AJAX-enabled WCF Service**.</span></span>

2. <span data-ttu-id="6edc1-126">Pojmenujte `WCFHello` služby a klikněte na **Přidat**.</span><span class="sxs-lookup"><span data-stu-id="6edc1-126">Name the service `WCFHello` and click **Add**.</span></span>

3. <span data-ttu-id="6edc1-127">Otevřete soubor WCFHello.svc.cs.</span><span class="sxs-lookup"><span data-stu-id="6edc1-127">Open the WCFHello.svc.cs file.</span></span>

4. <span data-ttu-id="6edc1-128">Z Service1.asmx.cs zkopírujte následující implementaci operace `HelloWorld`.</span><span class="sxs-lookup"><span data-stu-id="6edc1-128">From Service1.asmx.cs, copy the following implementation of the `HelloWorld` operation.</span></span>

    ```csharp
    public string HelloWorld()
    {
        return "Hello World";
    }
    ```

5. <span data-ttu-id="6edc1-129">Vložte do souboru WCFHello.svc.cs na místo následujícího kódu, kde se nachází zkopírovaná implementace operace `HelloWorld`.</span><span class="sxs-lookup"><span data-stu-id="6edc1-129">Paste to copied implementation of the `HelloWorld` operation into the WCFHello.svc.cs file in place of the following code.</span></span>

    ```csharp
    public void DoWork()
    {
          // Add your operation implementation here
          return;
    }
    ```

6. <span data-ttu-id="6edc1-130">Zadejte atribut `Namespace` pro <xref:System.ServiceModel.ServiceContractAttribute> jako `WCFHello`.</span><span class="sxs-lookup"><span data-stu-id="6edc1-130">Specify the `Namespace` attribute for <xref:System.ServiceModel.ServiceContractAttribute> as `WCFHello`.</span></span>

    ```csharp
    [ServiceContract(Namespace="WCFHello")]
    [AspNetCompatibilityRequirements(RequirementsMode=AspNetCompatibilityRequirementsMode.Required)]
    public class WCFHello
    { … }
    ```

7. <span data-ttu-id="6edc1-131">Přidejte <xref:System.ServiceModel.Web.WebInvokeAttribute> do operace `HelloWorld` a nastavte vlastnost <xref:System.ServiceModel.Web.WebInvokeAttribute.ResponseFormat%2A> na hodnotu vrátit <xref:System.ServiceModel.Web.WebMessageFormat.Xml>.</span><span class="sxs-lookup"><span data-stu-id="6edc1-131">Add the <xref:System.ServiceModel.Web.WebInvokeAttribute> to the `HelloWorld` operation and set the <xref:System.ServiceModel.Web.WebInvokeAttribute.ResponseFormat%2A> property to return <xref:System.ServiceModel.Web.WebMessageFormat.Xml>.</span></span> <span data-ttu-id="6edc1-132">Všimněte si, že pokud není nastavena, výchozí návratový typ je <xref:System.ServiceModel.Web.WebMessageFormat.Json>.</span><span class="sxs-lookup"><span data-stu-id="6edc1-132">Note that, if not set, the default return type is <xref:System.ServiceModel.Web.WebMessageFormat.Json>.</span></span>

    ```csharp
    [OperationContract]
    [WebInvoke(ResponseFormat=WebMessageFormat.Xml)]
    public string HelloWorld()
    {
        return "Hello World";
    }
    ```

8. <span data-ttu-id="6edc1-133">V nabídce **sestavení** vyberte **Sestavit řešení**.</span><span class="sxs-lookup"><span data-stu-id="6edc1-133">From the **Build** menu, select **Build Solution**.</span></span>

9. <span data-ttu-id="6edc1-134">Otevřete soubor WCFHello. svc a v nabídce **ladění** vyberte **Spustit bez ladění**.</span><span class="sxs-lookup"><span data-stu-id="6edc1-134">Open the WCFHello.svc file and from the **Debug** menu, select **Start Without Debugging**.</span></span>

10. <span data-ttu-id="6edc1-135">Služba nyní zpřístupňuje koncový bod na `WCFHello.svc/HelloWorld`, který reaguje na požadavky HTTP POST.</span><span class="sxs-lookup"><span data-stu-id="6edc1-135">The service now exposes an endpoint at `WCFHello.svc/HelloWorld`, which responds to HTTP POST requests.</span></span> <span data-ttu-id="6edc1-136">Požadavky HTTP POST nelze testovat z prohlížeče, ale koncový bod vrátí XML následující kód XML.</span><span class="sxs-lookup"><span data-stu-id="6edc1-136">HTTP POST requests cannot be tested from the browser, but the endpoint returns XML following XML.</span></span>

    ```xml
    <string xmlns="http://schemas.microsoft.com/2003/10/Serialization/">Hello World</string>
    ```

11. <span data-ttu-id="6edc1-137">`WCFHello.svc/HelloWorld` a koncové body `Service1.aspx/HelloWorld` jsou nyní funkčně ekvivalentní.</span><span class="sxs-lookup"><span data-stu-id="6edc1-137">The `WCFHello.svc/HelloWorld` and the `Service1.aspx/HelloWorld` endpoints are now functionally equivalent.</span></span>

## <a name="example"></a><span data-ttu-id="6edc1-138">Příklad</span><span class="sxs-lookup"><span data-stu-id="6edc1-138">Example</span></span>
 <span data-ttu-id="6edc1-139">Kód, který je výsledkem postupů popsaných v tomto tématu, je uveden v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="6edc1-139">The code that results from the procedures outlined in this topic is provided in the following example.</span></span>

```csharp
//This is the ASP.NET code in the Service1.asmx.cs file.

using System;
using System.Collections;
using System.ComponentModel;
using System.Data;
using System.Linq;
using System.Web;
using System.Web.Services;
using System.Web.Services.Protocols;
using System.Xml.Linq;
using System.Web.Script.Services;

namespace ASPHello
{
    /// <summary>
    /// Summary description for Service1.
    /// </summary>
    [WebService(Namespace = "http://tempuri.org/")]
    [WebServiceBinding(ConformsTo = WsiProfiles.BasicProfile1_1)]
    [ToolboxItem(false)]
    // To allow this Web Service to be called from script, using ASP.NET AJAX, uncomment the following line.
    [System.Web.Script.Services.ScriptService]
    public class Service1 : System.Web.Services.WebService
    {

        [WebMethod]
        public string HelloWorld()
        {
            return "Hello World";
        }
    }
}

//This is the WCF code in the WCFHello.svc.cs file.
using System;
using System.Linq;
using System.Runtime.Serialization;
using System.ServiceModel;
using System.ServiceModel.Activation;
using System.ServiceModel.Web;

namespace ASPHello
{
    [ServiceContract(Namespace = "WCFHello")]
    [AspNetCompatibilityRequirements(RequirementsMode = AspNetCompatibilityRequirementsMode.Allowed)]
    public class WCFHello
    {
        // Add [WebInvoke] attribute to use HTTP GET.
        [OperationContract]
        [WebInvoke(ResponseFormat=WebMessageFormat.Xml)]
        public string HelloWorld()
        {
            return "Hello World";
        }

        // Add more operations here and mark them with [OperationContract].
    }
}
```

 <span data-ttu-id="6edc1-140">Typ <xref:System.Xml.XmlDocument> není podporován <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>, protože <xref:System.Xml.Serialization.XmlSerializer>jej serializovat.</span><span class="sxs-lookup"><span data-stu-id="6edc1-140">The <xref:System.Xml.XmlDocument> type is not supported by the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> because it is not serializable by the <xref:System.Xml.Serialization.XmlSerializer>.</span></span> <span data-ttu-id="6edc1-141">Můžete použít buď typ <xref:System.Xml.Linq.XDocument>, nebo místo toho <xref:System.Xml.XmlDocument.DocumentElement%2A> serializovat.</span><span class="sxs-lookup"><span data-stu-id="6edc1-141">You can use either an <xref:System.Xml.Linq.XDocument> type, or serialize the <xref:System.Xml.XmlDocument.DocumentElement%2A> instead.</span></span>

 <span data-ttu-id="6edc1-142">Pokud jsou webové služby ASMX upgradovány a migrovány souběžně se službami WCF, vyhněte se mapování dvou typů na stejný název na klientovi.</span><span class="sxs-lookup"><span data-stu-id="6edc1-142">If ASMX Web services are being upgraded and migrated side-by-side to WCF services, avoid mapping two types to the same name on the client.</span></span> <span data-ttu-id="6edc1-143">To způsobí výjimku v serializátorech, pokud je stejný typ použit v <xref:System.Web.Services.WebMethodAttribute> a <xref:System.ServiceModel.ServiceContractAttribute>:</span><span class="sxs-lookup"><span data-stu-id="6edc1-143">This causes an exception in serializers if the same type is used in a <xref:System.Web.Services.WebMethodAttribute> and a <xref:System.ServiceModel.ServiceContractAttribute>:</span></span>

- <span data-ttu-id="6edc1-144">Pokud je nejprve přidána služba WCF, vyvolá metoda na webové službě ASMX výjimku v <xref:System.Web.UI.ObjectConverter.ConvertValue%28System.Object%2CSystem.Type%2CSystem.String%29>, protože definice stylu WCF objednávky ve službě proxy má přednost.</span><span class="sxs-lookup"><span data-stu-id="6edc1-144">If WCF service is added first, invoking the method on ASMX Web Service causes exception in <xref:System.Web.UI.ObjectConverter.ConvertValue%28System.Object%2CSystem.Type%2CSystem.String%29> because the WCF style definition of the order in the proxy takes precedence.</span></span>

- <span data-ttu-id="6edc1-145">Pokud je nejprve přidána webová služba ASMX, volání metody ve službě WCF způsobí výjimku v <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> protože definice stylu webové služby objednávky v serveru proxy má přednost.</span><span class="sxs-lookup"><span data-stu-id="6edc1-145">If ASMX Web Service is added first, invoking method on WCF service causes exception in <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> because the Web Service style definition of the order in the proxy takes precedence.</span></span>

 <span data-ttu-id="6edc1-146">Existují významné rozdíly v chování mezi <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> a <xref:System.Web.Script.Serialization.JavaScriptSerializer>ASP.NET AJAX.</span><span class="sxs-lookup"><span data-stu-id="6edc1-146">There are significant differences in behavior between the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> and the ASP.NET AJAX <xref:System.Web.Script.Serialization.JavaScriptSerializer>.</span></span> <span data-ttu-id="6edc1-147"><xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> například představuje slovník jako pole párů klíč/hodnota, zatímco <xref:System.Web.Script.Serialization.JavaScriptSerializer> ASP.NET AJAX představuje slovník jako skutečné objekty JSON.</span><span class="sxs-lookup"><span data-stu-id="6edc1-147">For example, the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> represents a dictionary as an array of key/value pairs, whereas the ASP.NET AJAX <xref:System.Web.Script.Serialization.JavaScriptSerializer> represents a dictionary as actual JSON objects.</span></span> <span data-ttu-id="6edc1-148">Následuje slovník představovaný v ASP.NET AJAX.</span><span class="sxs-lookup"><span data-stu-id="6edc1-148">So the following is the dictionary represented in ASP.NET AJAX.</span></span>

```csharp
Dictionary<string, int> d = new Dictionary<string, int>();
d.Add("one", 1);
d.Add("two", 2);
```

 <span data-ttu-id="6edc1-149">Tento slovník je reprezentován v objektech JSON, jak je znázorněno v následujícím seznamu:</span><span class="sxs-lookup"><span data-stu-id="6edc1-149">This dictionary is represented in JSON objects as shown in the following list:</span></span>

- <span data-ttu-id="6edc1-150">[{"Key": "One"; "value": 1}; {"Key": "Two"; "value": 2}] <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer></span><span class="sxs-lookup"><span data-stu-id="6edc1-150">[{"Key":"one","Value":1},{"Key":"two","Value":2}] by the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer></span></span>

- <span data-ttu-id="6edc1-151">{"One": 1, "Two": 2} <xref:System.Web.Script.Serialization.JavaScriptSerializer> AJAX ASP.NET</span><span class="sxs-lookup"><span data-stu-id="6edc1-151">{"one":1,"two":2} by the ASP.NET AJAX <xref:System.Web.Script.Serialization.JavaScriptSerializer></span></span>

 <span data-ttu-id="6edc1-152"><xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> je výkonnější v tom smyslu, že může zpracovávat slovníky, kde typ klíče není řetězec, zatímco <xref:System.Web.Script.Serialization.JavaScriptSerializer> nemůže.</span><span class="sxs-lookup"><span data-stu-id="6edc1-152">The <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> is more powerful in the sense that it can handle dictionaries where the key type is not string, while the <xref:System.Web.Script.Serialization.JavaScriptSerializer> cannot.</span></span> <span data-ttu-id="6edc1-153">Ale druhá je srozumitelná pro JSON.</span><span class="sxs-lookup"><span data-stu-id="6edc1-153">But the latter is more JSON-friendly.</span></span>

 <span data-ttu-id="6edc1-154">Významné rozdíly mezi těmito serializátory jsou shrnuty v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="6edc1-154">The significant differences between these serializers are summarized in the following table.</span></span>

|<span data-ttu-id="6edc1-155">Kategorie rozdílů</span><span class="sxs-lookup"><span data-stu-id="6edc1-155">Category of Differences</span></span>|<span data-ttu-id="6edc1-156">DataContractJsonSerializer</span><span class="sxs-lookup"><span data-stu-id="6edc1-156">DataContractJsonSerializer</span></span>|<span data-ttu-id="6edc1-157">ASP.NET AJAX – JavaScriptSerializer</span><span class="sxs-lookup"><span data-stu-id="6edc1-157">ASP.NET AJAX JavaScriptSerializer</span></span>|
|-----------------------------|--------------------------------|---------------------------------------|
|<span data-ttu-id="6edc1-158">Deserializace prázdné vyrovnávací paměti (New Byte [0]) do <xref:System.Object> (nebo <xref:System.Uri>nebo některé jiné třídy).</span><span class="sxs-lookup"><span data-stu-id="6edc1-158">Deserializing the empty buffer (new byte[0]) into <xref:System.Object> (or <xref:System.Uri>, or some other classes).</span></span>|<span data-ttu-id="6edc1-159">SerializationException</span><span class="sxs-lookup"><span data-stu-id="6edc1-159">SerializationException</span></span>|<span data-ttu-id="6edc1-160">null</span><span class="sxs-lookup"><span data-stu-id="6edc1-160">null</span></span>|
|<span data-ttu-id="6edc1-161">Serializace <xref:System.DBNull.Value></span><span class="sxs-lookup"><span data-stu-id="6edc1-161">Serialization of <xref:System.DBNull.Value></span></span>|<span data-ttu-id="6edc1-162">{} (nebo {"__type": "#System"})</span><span class="sxs-lookup"><span data-stu-id="6edc1-162">{} (or {"__type":"#System"})</span></span>|<span data-ttu-id="6edc1-163">Null</span><span class="sxs-lookup"><span data-stu-id="6edc1-163">Null</span></span>|
|<span data-ttu-id="6edc1-164">Serializace privátních členů typů [serializovatelných].</span><span class="sxs-lookup"><span data-stu-id="6edc1-164">Serialization of the private members of [Serializable] types.</span></span>|<span data-ttu-id="6edc1-165">serializovat</span><span class="sxs-lookup"><span data-stu-id="6edc1-165">serialized</span></span>|<span data-ttu-id="6edc1-166">Neserializované</span><span class="sxs-lookup"><span data-stu-id="6edc1-166">not serialized</span></span>|
|<span data-ttu-id="6edc1-167">Serializace veřejných vlastností <xref:System.Runtime.Serialization.ISerializable>ch typů.</span><span class="sxs-lookup"><span data-stu-id="6edc1-167">Serialization of the public properties of <xref:System.Runtime.Serialization.ISerializable> types.</span></span>|<span data-ttu-id="6edc1-168">Neserializované</span><span class="sxs-lookup"><span data-stu-id="6edc1-168">not serialized</span></span>|<span data-ttu-id="6edc1-169">serializovat</span><span class="sxs-lookup"><span data-stu-id="6edc1-169">serialized</span></span>|
|<span data-ttu-id="6edc1-170">Rozšíření JSON</span><span class="sxs-lookup"><span data-stu-id="6edc1-170">"Extensions" of JSON</span></span>|<span data-ttu-id="6edc1-171">Dodržuje specifikaci JSON, která vyžaduje uvozovky na názvy členů objektu ({"a": "Hello"}).</span><span class="sxs-lookup"><span data-stu-id="6edc1-171">Adheres to the JSON specification, which requires quotes on object member names ({"a":"hello"}).</span></span>|<span data-ttu-id="6edc1-172">Podporuje názvy členů objektů bez uvozovek ({a: "Hello"}).</span><span class="sxs-lookup"><span data-stu-id="6edc1-172">Supports the names of object members without quotes ({a:"hello"}).</span></span>|
|<span data-ttu-id="6edc1-173"><xref:System.DateTime> koordinovaný světový čas (UTC)</span><span class="sxs-lookup"><span data-stu-id="6edc1-173"><xref:System.DateTime> Coordinated Universal Time (UTC)</span></span>|<span data-ttu-id="6edc1-174">Nepodporuje formát "\\/Date (123456789U)\\/" nebo "\\/Date\\(\d + (U&#124;(\\+\\-[\d{4}]))?\\)\\\\/) ".</span><span class="sxs-lookup"><span data-stu-id="6edc1-174">Does not support format "\\/Date(123456789U)\\/" or "\\/Date\\(\d+(U&#124;(\\+\\-[\d{4}]))?\\)\\\\/)".</span></span>|<span data-ttu-id="6edc1-175">Podporuje formát\\/Date (123456789U)\\/a\\/Date\\(\d + (U&#124;(\\+\\-[\d{4}]))?\\)\\\\/) "jako hodnoty DateTime.</span><span class="sxs-lookup"><span data-stu-id="6edc1-175">Supports format "\\/Date(123456789U)\\/" and "\\/Date\\(\d+(U&#124;(\\+\\-[\d{4}]))?\\)\\\\/)" as DateTime values.</span></span>|
|<span data-ttu-id="6edc1-176">Reprezentace slovníků</span><span class="sxs-lookup"><span data-stu-id="6edc1-176">Representation of dictionaries</span></span>|<span data-ttu-id="6edc1-177">Pole nenašla\<K, V >, zpracovává typy klíčů, které nejsou řetězci.</span><span class="sxs-lookup"><span data-stu-id="6edc1-177">An array of KeyValuePair\<K,V>, handles key types that are not strings.</span></span>|<span data-ttu-id="6edc1-178">Jako skutečné objekty JSON – ale zpracovává jenom typy klíčů, které jsou řetězce.</span><span class="sxs-lookup"><span data-stu-id="6edc1-178">As actual JSON objects - but only handles key types that are strings.</span></span>|
|<span data-ttu-id="6edc1-179">Řídicí znaky</span><span class="sxs-lookup"><span data-stu-id="6edc1-179">Escaped characters</span></span>|<span data-ttu-id="6edc1-180">Vždy s řídicím lomítkem (/); nikdy nepovoluje řídicí znaky neplatných znaků JSON, například "\n".</span><span class="sxs-lookup"><span data-stu-id="6edc1-180">Always with an escape forward slash (/); never allows un-escaped invalid JSON characters, such as "\n".</span></span>|<span data-ttu-id="6edc1-181">S řídicím lomítkem (/) pro hodnoty data a času.</span><span class="sxs-lookup"><span data-stu-id="6edc1-181">With an escape forward slash (/) for DateTime values.</span></span>|

## <a name="see-also"></a><span data-ttu-id="6edc1-182">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6edc1-182">See also</span></span>

- [<span data-ttu-id="6edc1-183">Postupy: Použití konfigurace k přidání koncového bodu ASP.NET AJAX</span><span class="sxs-lookup"><span data-stu-id="6edc1-183">How to: Use Configuration to Add an ASP.NET AJAX Endpoint</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md)
