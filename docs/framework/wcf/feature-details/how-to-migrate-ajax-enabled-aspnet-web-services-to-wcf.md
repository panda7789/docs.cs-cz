---
title: 'Postupy: Migrace webových služeb ASP.NET s povolenou službou AJAX na WCF'
ms.date: 03/30/2017
ms.assetid: 1428df4d-b18f-4e6d-bd4d-79ab3dd5147c
ms.openlocfilehash: 3c7052a67e756ae0c3fa1692c3ed746419384de4
ms.sourcegitcommit: 3630c2515809e6f4b7dbb697a3354efec105a5cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2019
ms.locfileid: "58410937"
---
# <a name="how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf"></a><span data-ttu-id="eb212-102">Postupy: Migrace webových služeb ASP.NET s povolenou službou AJAX na WCF</span><span class="sxs-lookup"><span data-stu-id="eb212-102">How to: Migrate AJAX-Enabled ASP.NET Web Services to WCF</span></span>
<span data-ttu-id="eb212-103">Toto téma popisuje postupy migrace základní služby technologie ASP.NET AJAX do ekvivalentní služby s povoleným AJAX Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="eb212-103">This topic outlines procedures to migrate a basic ASP.NET AJAX service to an equivalent AJAX-enabled Windows Communication Foundation (WCF) service.</span></span> <span data-ttu-id="eb212-104">Ukazuje, jak vytvořit funkčně ekvivalentní verzi WCF služby technologie ASP.NET AJAX.</span><span class="sxs-lookup"><span data-stu-id="eb212-104">It shows how to create a functionally equivalent WCF version of an ASP.NET AJAX service.</span></span> <span data-ttu-id="eb212-105">Tyto dvě služby je pak možné použít vedle sebe nebo službu WCF je možné nahradit služby technologie ASP.NET AJAX.</span><span class="sxs-lookup"><span data-stu-id="eb212-105">The two services can then be used side by side, or the WCF service can be used to replace the ASP.NET AJAX service.</span></span>

 <span data-ttu-id="eb212-106">Migrace stávající technologie ASP.NET AJAX komunikace mezi službami WCF AJAX poskytuje následující výhody:</span><span class="sxs-lookup"><span data-stu-id="eb212-106">Migrating an existing ASP.NET AJAX service to a WCF AJAX service gives you the following benefits:</span></span>

-   <span data-ttu-id="eb212-107">Vaše služba AJAX mohou vystavit jako službu SOAP s minimálními další konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="eb212-107">You can expose your AJAX service as a SOAP service with minimal extra configuration.</span></span>

-   <span data-ttu-id="eb212-108">Můžete využívat funkce WCF, jako je sledování a tak dále.</span><span class="sxs-lookup"><span data-stu-id="eb212-108">You can benefit from WCF features such as tracing, and so on.</span></span>

 <span data-ttu-id="eb212-109">V následujících postupech se předpokládá, že používáte sadu Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="eb212-109">The following procedures assume that you are using Visual Studio 2012.</span></span>

 <span data-ttu-id="eb212-110">Kód, které vyplývají z postupů uvedených v tomto tématu najdete v příkladu následující postupy.</span><span class="sxs-lookup"><span data-stu-id="eb212-110">The code that results from the procedures outlined in this topic is provided in the example following the procedures.</span></span>

 <span data-ttu-id="eb212-111">Další informace o vystavení služby WCF přes koncový bod s povoleným AJAX, najdete v článku [jak: Použití konfigurace k přidání koncového bodu ASP.NET AJAX](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md) tématu.</span><span class="sxs-lookup"><span data-stu-id="eb212-111">For more information about exposing a WCF service through an AJAX-enabled endpoint, see the [How to: Use Configuration to Add an ASP.NET AJAX Endpoint](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md) topic.</span></span>

### <a name="to-create-and-test-the-aspnet-web-service-application"></a><span data-ttu-id="eb212-112">Vytvořit a otestovat aplikaci technologie ASP.NET webové služby</span><span class="sxs-lookup"><span data-stu-id="eb212-112">To create and test the ASP.NET Web service application</span></span>

1.  <span data-ttu-id="eb212-113">Open Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="eb212-113">Open Visual Studio 2012.</span></span>

2.  <span data-ttu-id="eb212-114">Z **souboru** nabídce vyberte možnost **nový**, pak **projektu**, pak **webové**a pak vyberte **aplikaci webové služby ASP.NET** .</span><span class="sxs-lookup"><span data-stu-id="eb212-114">From the **File** menu, select **New**, then **Project**, then **Web**, and then select **ASP.NET Web Service Application**.</span></span>

3.  <span data-ttu-id="eb212-115">Pojmenujte projekt `ASPHello` a klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="eb212-115">Name the project `ASPHello` and click **OK**.</span></span>

4.  <span data-ttu-id="eb212-116">Zrušením komentáře u řádku v souboru Service1.asmx.cs, který obsahuje `System.Web.Script.Services.ScriptService]` umožňující AJAX pro tuto službu.</span><span class="sxs-lookup"><span data-stu-id="eb212-116">Uncomment the line in the Service1.asmx.cs file that contains `System.Web.Script.Services.ScriptService]` to enable AJAX for this service.</span></span>

5.  <span data-ttu-id="eb212-117">Z **sestavení** nabídce vyberte možnost **sestavit řešení**.</span><span class="sxs-lookup"><span data-stu-id="eb212-117">From the **Build** menu, select **Build Solution**.</span></span>

6.  <span data-ttu-id="eb212-118">Z **ladění** nabídce vyberte možnost **spustit bez ladění**.</span><span class="sxs-lookup"><span data-stu-id="eb212-118">From the **Debug** menu, select **Start Without Debugging**.</span></span>

7.  <span data-ttu-id="eb212-119">Na webové stránce vygenerovat, vyberte `HelloWorld` operace.</span><span class="sxs-lookup"><span data-stu-id="eb212-119">On the Web page generated, select the `HelloWorld` operation.</span></span>

8.  <span data-ttu-id="eb212-120">Klikněte na tlačítko **Invoke** tlačítko `HelloWorld` zkušební stránku.</span><span class="sxs-lookup"><span data-stu-id="eb212-120">Click the **Invoke** button on the `HelloWorld` test page.</span></span> <span data-ttu-id="eb212-121">Měli byste obdržet odpověď na následující XML.</span><span class="sxs-lookup"><span data-stu-id="eb212-121">You should receive the following XML response.</span></span>

    ```xml
    <?xml version="1.0" encoding="utf-8" ?>
    <string xmlns="http://tempuri.org/">Hello World</string>
    ```

9. <span data-ttu-id="eb212-122">Tato odpověď potvrzuje, že teď máte funkční služba ASP.NET AJAX, konkrétně se, že služba má nyní zpřístupněn koncový bod na Service1.asmx/HelloWorld, který reaguje na HTTP POST požadavků a vrátí XML.</span><span class="sxs-lookup"><span data-stu-id="eb212-122">This response confirms that you now have a functioning ASP.NET AJAX service and, in particular, that the service has now exposed an endpoint at Service1.asmx/HelloWorld that responds to HTTP POST requests and returns XML.</span></span>

     <span data-ttu-id="eb212-123">Nyní jste připraveni k převedení této služby k používání služby WCF AJAX.</span><span class="sxs-lookup"><span data-stu-id="eb212-123">Now you are ready to convert this service to use a WCF AJAX service.</span></span>

### <a name="to-create-an-equivalent-wcf-ajax-service-application"></a><span data-ttu-id="eb212-124">Chcete-li vytvořit rovnocenné aplikace služby WCF AJAX</span><span class="sxs-lookup"><span data-stu-id="eb212-124">To create an equivalent WCF AJAX service application</span></span>

1.  <span data-ttu-id="eb212-125">Klikněte pravým tlačítkem myši **ASPHello** projektu a vyberte **přidat**, pak **nová položka**a potom **s povoleným AJAX služba WCF**.</span><span class="sxs-lookup"><span data-stu-id="eb212-125">Right-click the **ASPHello** project and select **Add**, then **New Item**, and then **AJAX-enabled WCF Service**.</span></span>

2.  <span data-ttu-id="eb212-126">Pojmenujte službu `WCFHello` a klikněte na tlačítko **přidat**.</span><span class="sxs-lookup"><span data-stu-id="eb212-126">Name the service `WCFHello` and click **Add**.</span></span>

3.  <span data-ttu-id="eb212-127">Otevřete soubor WCFHello.svc.cs.</span><span class="sxs-lookup"><span data-stu-id="eb212-127">Open the WCFHello.svc.cs file.</span></span>

4.  <span data-ttu-id="eb212-128">Z Service1.asmx.cs, zkopírujte následující provádění `HelloWorld` operace.</span><span class="sxs-lookup"><span data-stu-id="eb212-128">From Service1.asmx.cs, copy the following implementation of the `HelloWorld` operation.</span></span>

    ```
    public string HelloWorld()
    {
         return "Hello World";
    }
    ```

5.  <span data-ttu-id="eb212-129">Vložte zkopírovaný provádění `HelloWorld` operace do souboru WCFHello.svc.cs místo následující kód.</span><span class="sxs-lookup"><span data-stu-id="eb212-129">Paste to copied implementation of the `HelloWorld` operation into the WCFHello.svc.cs file in place of the following code.</span></span>

    ```
    public void DoWork()
    {
          // Add your operation implementation here
          return;
    }
    ```

6.  <span data-ttu-id="eb212-130">Zadejte `Namespace` atributu <xref:System.ServiceModel.ServiceContractAttribute> jako `WCFHello`.</span><span class="sxs-lookup"><span data-stu-id="eb212-130">Specify the `Namespace` attribute for <xref:System.ServiceModel.ServiceContractAttribute> as `WCFHello`.</span></span>

    ```
    [ServiceContract(Namespace="WCFHello")]
    [AspNetCompatibilityRequirements(RequirementsMode=AspNetCompatibilityRequirementsMode.Required)]
    public class WCFHello
    { … }
    ```

7.  <span data-ttu-id="eb212-131">Přidat <xref:System.ServiceModel.Web.WebInvokeAttribute> k `HelloWorld` operace a sady <xref:System.ServiceModel.Web.WebInvokeAttribute.ResponseFormat%2A> vlastnost vrátit <xref:System.ServiceModel.Web.WebMessageFormat.Xml>.</span><span class="sxs-lookup"><span data-stu-id="eb212-131">Add the <xref:System.ServiceModel.Web.WebInvokeAttribute> to the `HelloWorld` operation and set the <xref:System.ServiceModel.Web.WebInvokeAttribute.ResponseFormat%2A> property to return <xref:System.ServiceModel.Web.WebMessageFormat.Xml>.</span></span> <span data-ttu-id="eb212-132">Všimněte si, že, pokud není nastavena, výchozí hodnota je návratový typ <xref:System.ServiceModel.Web.WebMessageFormat.Json>.</span><span class="sxs-lookup"><span data-stu-id="eb212-132">Note that, if not set, the default return type is <xref:System.ServiceModel.Web.WebMessageFormat.Json>.</span></span>

    ```
    [OperationContract]
    [WebInvoke(ResponseFormat=WebMessageFormat.Xml)]
    public string HelloWorld()
    {
        return "Hello World";
    }
    ```

8.  <span data-ttu-id="eb212-133">Z **sestavení** nabídce vyberte možnost **sestavit řešení**.</span><span class="sxs-lookup"><span data-stu-id="eb212-133">From the **Build** menu, select **Build Solution**.</span></span>

9. <span data-ttu-id="eb212-134">Otevřete soubor WCFHello.svc z a **ladění** nabídce vyberte možnost **spustit bez ladění**.</span><span class="sxs-lookup"><span data-stu-id="eb212-134">Open the WCFHello.svc file and from the **Debug** menu, select **Start Without Debugging**.</span></span>

10. <span data-ttu-id="eb212-135">Služba teď zpřístupňuje koncový bod na `WCFHello.svc/HelloWorld`, který reaguje na požadavky HTTP POST.</span><span class="sxs-lookup"><span data-stu-id="eb212-135">The service now exposes an endpoint at `WCFHello.svc/HelloWorld`, which responds to HTTP POST requests.</span></span> <span data-ttu-id="eb212-136">Požadavky HTTP POST nelze provést test z prohlížeče, ale koncový bod vrátí následující XML XML.</span><span class="sxs-lookup"><span data-stu-id="eb212-136">HTTP POST requests cannot be tested from the browser, but the endpoint returns XML following XML.</span></span>

    ```xml
    <string xmlns="http://schemas.microsoft.com/2003/10/Serialization/">Hello World</string>
    ```

11. <span data-ttu-id="eb212-137">`WCFHello.svc/HelloWorld` a `Service1.aspx/HelloWorld` koncové body jsou funkčně ekvivalentní.</span><span class="sxs-lookup"><span data-stu-id="eb212-137">The `WCFHello.svc/HelloWorld` and the `Service1.aspx/HelloWorld` endpoints are now functionally equivalent.</span></span>

## <a name="example"></a><span data-ttu-id="eb212-138">Příklad</span><span class="sxs-lookup"><span data-stu-id="eb212-138">Example</span></span>
 <span data-ttu-id="eb212-139">Kód, který je výsledkem postupů uvedených v tomto tématu najdete v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="eb212-139">The code that results from the procedures outlined in this topic is provided in the following example.</span></span>

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

 <span data-ttu-id="eb212-140"><xref:System.Xml.XmlDocument> Typ není podporován <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> protože to není serializovatelný podle <xref:System.Xml.Serialization.XmlSerializer>.</span><span class="sxs-lookup"><span data-stu-id="eb212-140">The <xref:System.Xml.XmlDocument> type is not supported by the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> because it is not serializable by the <xref:System.Xml.Serialization.XmlSerializer>.</span></span> <span data-ttu-id="eb212-141">Můžete použít buď <xref:System.Xml.Linq.XDocument> zadejte nebo serializovat <xref:System.Xml.XmlDocument.DocumentElement%2A> místo.</span><span class="sxs-lookup"><span data-stu-id="eb212-141">You can use either an <xref:System.Xml.Linq.XDocument> type, or serialize the <xref:System.Xml.XmlDocument.DocumentElement%2A> instead.</span></span>

 <span data-ttu-id="eb212-142">Pokud ASMX webovými službami jsou upgraduje a migrovat vedle sebe ke službám WCF, vyhněte se dva typy mapování na stejné jméno v klientovi.</span><span class="sxs-lookup"><span data-stu-id="eb212-142">If ASMX Web services are being upgraded and migrated side-by-side to WCF services, avoid mapping two types to the same name on the client.</span></span> <span data-ttu-id="eb212-143">To způsobí, že výjimka v serializátory Pokud je používán stejného typu <xref:System.Web.Services.WebMethodAttribute> a <xref:System.ServiceModel.ServiceContractAttribute>:</span><span class="sxs-lookup"><span data-stu-id="eb212-143">This causes an exception in serializers if the same type is used in a <xref:System.Web.Services.WebMethodAttribute> and a <xref:System.ServiceModel.ServiceContractAttribute>:</span></span>

-   <span data-ttu-id="eb212-144">Pokud nejprve přidáte službu WCF, volání metody na webovou službu ASMX způsobí, že výjimka v <xref:System.Web.UI.ObjectConverter.ConvertValue%28System.Object%2CSystem.Type%2CSystem.String%29> vzhledem k tomu, že má přednost před definice stylu WCF objednávky v proxy serveru.</span><span class="sxs-lookup"><span data-stu-id="eb212-144">If WCF service is added first, invoking the method on ASMX Web Service causes exception in <xref:System.Web.UI.ObjectConverter.ConvertValue%28System.Object%2CSystem.Type%2CSystem.String%29> because the WCF style definition of the order in the proxy takes precedence.</span></span>

-   <span data-ttu-id="eb212-145">Pokud nejprve přidá ASMX webovou službu, volání metody na službu WCF způsobí, že výjimka v <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> vzhledem k tomu, že má přednost před definice stylu webové služby objednávky v proxy serveru.</span><span class="sxs-lookup"><span data-stu-id="eb212-145">If ASMX Web Service is added first, invoking method on WCF service causes exception in <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> because the Web Service style definition of the order in the proxy takes precedence.</span></span>

 <span data-ttu-id="eb212-146">Existují významné rozdíly v chování mezi <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> a technologie ASP.NET AJAX <xref:System.Web.Script.Serialization.JavaScriptSerializer>.</span><span class="sxs-lookup"><span data-stu-id="eb212-146">There are significant differences in behavior between the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> and the ASP.NET AJAX <xref:System.Web.Script.Serialization.JavaScriptSerializer>.</span></span> <span data-ttu-id="eb212-147">Například <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> představuje slovník jako pole párů klíč/hodnota, že technologie ASP.NET AJAX <xref:System.Web.Script.Serialization.JavaScriptSerializer> představuje slovník jako skutečné objekty JSON.</span><span class="sxs-lookup"><span data-stu-id="eb212-147">For example, the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> represents a dictionary as an array of key/value pairs, whereas the ASP.NET AJAX <xref:System.Web.Script.Serialization.JavaScriptSerializer> represents a dictionary as actual JSON objects.</span></span> <span data-ttu-id="eb212-148">Takže tady je slovník reprezentovány v rozhraní ASP.NET AJAX.</span><span class="sxs-lookup"><span data-stu-id="eb212-148">So the following is the dictionary represented in ASP.NET AJAX.</span></span>

```
Dictionary<string, int> d = new Dictionary<string, int>();
d.Add("one", 1);
d.Add("two", 2);
```

 <span data-ttu-id="eb212-149">Tento slovník je reprezentován v objektech JSON, jak je znázorněno v následujícím seznamu:</span><span class="sxs-lookup"><span data-stu-id="eb212-149">This dictionary is represented in JSON objects as shown in the following list:</span></span>

-   <span data-ttu-id="eb212-150">[{"Klíče": "Jedna", "Value": 1}, {"Klíče": "Dvě", "Value": 2}] ve <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer></span><span class="sxs-lookup"><span data-stu-id="eb212-150">[{"Key":"one","Value":1},{"Key":"two","Value":2}] by the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer></span></span>

-   <span data-ttu-id="eb212-151">{"jedna": 1, "dvě": 2} pomocí technologie ASP.NET AJAX <xref:System.Web.Script.Serialization.JavaScriptSerializer></span><span class="sxs-lookup"><span data-stu-id="eb212-151">{"one":1,"two":2} by the ASP.NET AJAX <xref:System.Web.Script.Serialization.JavaScriptSerializer></span></span>

 <span data-ttu-id="eb212-152"><xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> Účinnější v tom smyslu, že dokáže zpracovat slovníky kde typ klíče není řetězec, zatímco <xref:System.Web.Script.Serialization.JavaScriptSerializer> nelze.</span><span class="sxs-lookup"><span data-stu-id="eb212-152">The <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> is more powerful in the sense that it can handle dictionaries where the key type is not string, while the <xref:System.Web.Script.Serialization.JavaScriptSerializer> cannot.</span></span> <span data-ttu-id="eb212-153">Ale je více vhodných JSON.</span><span class="sxs-lookup"><span data-stu-id="eb212-153">But the latter is more JSON-friendly.</span></span>

 <span data-ttu-id="eb212-154">Významné rozdíly mezi těmito serializátory jsou shrnuty v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="eb212-154">The significant differences between these serializers are summarized in the following table.</span></span>

|<span data-ttu-id="eb212-155">Kategorie rozdíly</span><span class="sxs-lookup"><span data-stu-id="eb212-155">Category of Differences</span></span>|<span data-ttu-id="eb212-156">DataContractJsonSerializer</span><span class="sxs-lookup"><span data-stu-id="eb212-156">DataContractJsonSerializer</span></span>|<span data-ttu-id="eb212-157">ASP.NET AJAX JavaScriptSerializer</span><span class="sxs-lookup"><span data-stu-id="eb212-157">ASP.NET AJAX JavaScriptSerializer</span></span>|
|-----------------------------|--------------------------------|---------------------------------------|
|<span data-ttu-id="eb212-158">Deserializace prázdné vyrovnávací paměti (nové byte[0]) do <xref:System.Object> (nebo <xref:System.Uri>, nebo některé jiné třídy).</span><span class="sxs-lookup"><span data-stu-id="eb212-158">Deserializing the empty buffer (new byte[0]) into <xref:System.Object> (or <xref:System.Uri>, or some other classes).</span></span>|<span data-ttu-id="eb212-159">SerializationException</span><span class="sxs-lookup"><span data-stu-id="eb212-159">SerializationException</span></span>|<span data-ttu-id="eb212-160">null</span><span class="sxs-lookup"><span data-stu-id="eb212-160">null</span></span>|
|<span data-ttu-id="eb212-161">Serializace <xref:System.DBNull.Value></span><span class="sxs-lookup"><span data-stu-id="eb212-161">Serialization of <xref:System.DBNull.Value></span></span>|<span data-ttu-id="eb212-162">{} (nebo {"__type": "#System"})</span><span class="sxs-lookup"><span data-stu-id="eb212-162">{} (or {"__type":"#System"})</span></span>|<span data-ttu-id="eb212-163">Null</span><span class="sxs-lookup"><span data-stu-id="eb212-163">Null</span></span>|
|<span data-ttu-id="eb212-164">Serializace soukromé členy typů [Serializable].</span><span class="sxs-lookup"><span data-stu-id="eb212-164">Serialization of the private members of [Serializable] types.</span></span>|<span data-ttu-id="eb212-165">serializovat</span><span class="sxs-lookup"><span data-stu-id="eb212-165">serialized</span></span>|<span data-ttu-id="eb212-166">nelze serializovat.</span><span class="sxs-lookup"><span data-stu-id="eb212-166">not serialized</span></span>|
|<span data-ttu-id="eb212-167">Serializace veřejné vlastnosti <xref:System.Runtime.Serialization.ISerializable> typy.</span><span class="sxs-lookup"><span data-stu-id="eb212-167">Serialization of the public properties of <xref:System.Runtime.Serialization.ISerializable> types.</span></span>|<span data-ttu-id="eb212-168">nelze serializovat.</span><span class="sxs-lookup"><span data-stu-id="eb212-168">not serialized</span></span>|<span data-ttu-id="eb212-169">serializovat</span><span class="sxs-lookup"><span data-stu-id="eb212-169">serialized</span></span>|
|<span data-ttu-id="eb212-170">"Rozšíření" formátu JSON</span><span class="sxs-lookup"><span data-stu-id="eb212-170">"Extensions" of JSON</span></span>|<span data-ttu-id="eb212-171">Dodržuje specifikaci formátu JSON, která vyžaduje uvozovky na názvy členů objektu ({"a": "hello"}).</span><span class="sxs-lookup"><span data-stu-id="eb212-171">Adheres to the JSON specification, which requires quotes on object member names ({"a":"hello"}).</span></span>|<span data-ttu-id="eb212-172">Podporuje názvy členů objektu bez uvozovek ({a: "hello"}).</span><span class="sxs-lookup"><span data-stu-id="eb212-172">Supports the names of object members without quotes ({a:"hello"}).</span></span>|
|<span data-ttu-id="eb212-173"><xref:System.DateTime> Koordinovaný světový čas (UTC)</span><span class="sxs-lookup"><span data-stu-id="eb212-173"><xref:System.DateTime> Coordinated Universal Time (UTC)</span></span>|<span data-ttu-id="eb212-174">Nepodporuje formát "\\/Date(123456789U)\\/" nebo "\\/Date\\(\d+ (U&#124;(\\+\\-[\d{4}]))?\\) \\\\/)".</span><span class="sxs-lookup"><span data-stu-id="eb212-174">Does not support format "\\/Date(123456789U)\\/" or "\\/Date\\(\d+(U&#124;(\\+\\-[\d{4}]))?\\)\\\\/)".</span></span>|<span data-ttu-id="eb212-175">Podporuje formát "\\/Date(123456789U)\\/" a "\\/Date\\(\d+ (U&#124;(\\+\\-[\d{4}]))?\\) \\ \\/) "jako hodnoty data a času.</span><span class="sxs-lookup"><span data-stu-id="eb212-175">Supports format "\\/Date(123456789U)\\/" and "\\/Date\\(\d+(U&#124;(\\+\\-[\d{4}]))?\\)\\\\/)" as DateTime values.</span></span>|
|<span data-ttu-id="eb212-176">Reprezentace slovníky</span><span class="sxs-lookup"><span data-stu-id="eb212-176">Representation of dictionaries</span></span>|<span data-ttu-id="eb212-177">Celou řadu komponent\<K, V >, zpracovává typy klíčů, které nejsou řetězce.</span><span class="sxs-lookup"><span data-stu-id="eb212-177">An array of KeyValuePair\<K,V>, handles key types that are not strings.</span></span>|<span data-ttu-id="eb212-178">Jako skutečné objekty JSON -, ale pouze typy klíčů obslužné rutiny, které jsou řetězce.</span><span class="sxs-lookup"><span data-stu-id="eb212-178">As actual JSON objects - but only handles key types that are strings.</span></span>|
|<span data-ttu-id="eb212-179">Řídicí znaky</span><span class="sxs-lookup"><span data-stu-id="eb212-179">Escaped characters</span></span>|<span data-ttu-id="eb212-180">Vždy s řídicí sekvence dopředné lomítko (/); nikdy umožňuje uvozeny řídicími znaky neplatné znaky JSON, jako je například "\n".</span><span class="sxs-lookup"><span data-stu-id="eb212-180">Always with an escape forward slash (/); never allows un-escaped invalid JSON characters, such as "\n".</span></span>|<span data-ttu-id="eb212-181">S řídicí sekvence dopředné lomítko (/) pro hodnoty data a času.</span><span class="sxs-lookup"><span data-stu-id="eb212-181">With an escape forward slash (/) for DateTime values.</span></span>|

## <a name="see-also"></a><span data-ttu-id="eb212-182">Viz také:</span><span class="sxs-lookup"><span data-stu-id="eb212-182">See also</span></span>
- [<span data-ttu-id="eb212-183">Postupy: Použití konfigurace k přidání koncového bodu ASP.NET AJAX</span><span class="sxs-lookup"><span data-stu-id="eb212-183">How to: Use Configuration to Add an ASP.NET AJAX Endpoint</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md)
