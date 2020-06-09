---
title: 'Postupy: Migrace webových služeb ASP.NET s podporou AJAXu na službu WCF'
ms.date: 03/30/2017
ms.assetid: 1428df4d-b18f-4e6d-bd4d-79ab3dd5147c
ms.openlocfilehash: 6f356f47922945218e02271371d9ddea36ecc5a2
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84597004"
---
# <a name="how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf"></a>Postupy: Migrace webových služeb ASP.NET s podporou AJAXu na službu WCF
V tomto tématu jsou popsány postupy pro migraci základní služby ASP.NET AJAX do ekvivalentní služby Windows Communication Foundation WCF (AJAX Enabled). Ukazuje, jak vytvořit funkčně ekvivalentní verzi WCF služby ASP.NET AJAX. Tyto dvě služby se pak dají použít souběžně nebo službu WCF můžete použít k nahrazení služby ASP.NET AJAX.

 Migrace stávající služby ASP.NET AJAX do služby WCF AJAX přináší následující výhody:

- Službu AJAX můžete vystavit jako službu SOAP s minimální dodatečnou konfigurací.

- Můžete využít výhod funkcí WCF, jako je trasování a tak dále.

 V následujících postupech se předpokládá, že používáte Visual Studio 2012.

 Kód, který je výsledkem postupů popsaných v tomto tématu, je uveden v příkladu, který následuje po postupech.

 Další informace o vystavení služby WCF prostřednictvím koncového bodu s povoleným AJAX naleznete v tématu [How to: use Configuration to Add the ASP.NET AJAX Endpoint](how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md) .

### <a name="to-create-and-test-the-aspnet-web-service-application"></a>Vytvoření a otestování aplikace webové služby ASP.NET

1. Otevřete Visual Studio 2012.

2. V nabídce **soubor** vyberte možnost **Nový**, **projekt**, pak **Web**a pak vyberte možnost **aplikace webové služby ASP.NET**.

3. Pojmenujte projekt `ASPHello` a klikněte na tlačítko **OK**.

4. Odkomentujte řádek v souboru Service1.asmx.cs, který obsahuje `System.Web.Script.Services.ScriptService]` pro povolení AJAX pro tuto službu.

5. V nabídce **sestavení** vyberte **Sestavit řešení**.

6. V nabídce **Ladit** vyberte **Spustit bez ladění**.

7. Na vygenerované webové stránce vyberte `HelloWorld` operaci.

8. Klikněte na tlačítko **vyvolat** na `HelloWorld` stránce test. Měla by se zobrazit následující odpověď XML.

    ```xml
    <?xml version="1.0" encoding="utf-8" ?>
    <string xmlns="http://tempuri.org/">Hello World</string>
    ```

9. Tato odpověď potvrzuje, že teď máte funkční službu ASP.NET AJAX, a zejména to, že služba nyní nastavila koncový bod na Service1. asmx/HelloWorld, který reaguje na požadavky HTTP POST a vrací XML.

     Nyní jste připraveni tuto službu převést na používání služby WCF AJAX.

### <a name="to-create-an-equivalent-wcf-ajax-service-application"></a>Vytvoření ekvivalentní aplikace služby WCF AJAX

1. Klikněte pravým tlačítkem na projekt **ASPHello** a vyberte **Přidat**, **Nová položka**a potom **službu WCF s podporou jazyka AJAX**.

2. Pojmenujte službu `WCFHello` a klikněte na **Přidat**.

3. Otevřete soubor WCFHello.svc.cs.

4. Z Service1.asmx.cs zkopírujte následující implementaci `HelloWorld` operace.

    ```csharp
    public string HelloWorld()
    {
        return "Hello World";
    }
    ```

5. Vložte do `HelloWorld` souboru WCFHello.svc.cs na místo následujícího kódu a vložte do něj zkopírovanou implementaci operace.

    ```csharp
    public void DoWork()
    {
          // Add your operation implementation here
          return;
    }
    ```

6. Zadejte `Namespace` atribut <xref:System.ServiceModel.ServiceContractAttribute> jako `WCFHello` .

    ```csharp
    [ServiceContract(Namespace="WCFHello")]
    [AspNetCompatibilityRequirements(RequirementsMode=AspNetCompatibilityRequirementsMode.Required)]
    public class WCFHello
    { … }
    ```

7. Přidejte <xref:System.ServiceModel.Web.WebInvokeAttribute> k `HelloWorld` operaci a nastavte <xref:System.ServiceModel.Web.WebInvokeAttribute.ResponseFormat%2A> vlastnost, která se má vrátit <xref:System.ServiceModel.Web.WebMessageFormat.Xml> . Všimněte si, že pokud není nastavena, výchozí návratový typ je <xref:System.ServiceModel.Web.WebMessageFormat.Json> .

    ```csharp
    [OperationContract]
    [WebInvoke(ResponseFormat=WebMessageFormat.Xml)]
    public string HelloWorld()
    {
        return "Hello World";
    }
    ```

8. V nabídce **sestavení** vyberte **Sestavit řešení**.

9. Otevřete soubor WCFHello. svc a v nabídce **ladění** vyberte **Spustit bez ladění**.

10. Služba nyní zpřístupňuje koncový bod na `WCFHello.svc/HelloWorld` , který reaguje na požadavky HTTP POST. Požadavky HTTP POST nelze testovat z prohlížeče, ale koncový bod vrátí XML následující kód XML.

    ```xml
    <string xmlns="http://schemas.microsoft.com/2003/10/Serialization/">Hello World</string>
    ```

11. `WCFHello.svc/HelloWorld`A `Service1.aspx/HelloWorld` koncové body jsou nyní funkčně ekvivalentní.

## <a name="example"></a>Příklad
 Kód, který je výsledkem postupů popsaných v tomto tématu, je uveden v následujícím příkladu.

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

 <xref:System.Xml.XmlDocument>Typ není podporován, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> protože není serializovatelný pomocí <xref:System.Xml.Serialization.XmlSerializer> . Můžete použít buď <xref:System.Xml.Linq.XDocument> typ, nebo <xref:System.Xml.XmlDocument.DocumentElement%2A> místo toho serializovat.

 Pokud jsou webové služby ASMX upgradovány a migrovány souběžně se službami WCF, vyhněte se mapování dvou typů na stejný název na klientovi. To způsobuje výjimku v serializátorech, pokud je stejný typ použit v <xref:System.Web.Services.WebMethodAttribute> a a <xref:System.ServiceModel.ServiceContractAttribute> :

- Pokud je nejprve přidána služba WCF, vyvolá metoda na webové službě ASMX výjimku, <xref:System.Web.UI.ObjectConverter.ConvertValue%28System.Object%2CSystem.Type%2CSystem.String%29> protože má přednost definice stylu WCF pořadí v serveru proxy.

- Pokud je nejprve přidána webová služba ASMX, volání metody ve službě WCF způsobí výjimku, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> protože definice stylu webové služby objednávky v serveru proxy má přednost.

 Mezi a ASP.NET AJAX jsou významné rozdíly v chování <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> <xref:System.Web.Script.Serialization.JavaScriptSerializer> . Například <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> představuje slovník jako pole párů klíč/hodnota, zatímco ASP.NET AJAX <xref:System.Web.Script.Serialization.JavaScriptSerializer> představuje slovník jako skutečné objekty JSON. Následuje slovník představovaný v ASP.NET AJAX.

```csharp
Dictionary<string, int> d = new Dictionary<string, int>();
d.Add("one", 1);
d.Add("two", 2);
```

 Tento slovník je reprezentován v objektech JSON, jak je znázorněno v následujícím seznamu:

- [{"Key": "One"; "value": 1}; {"Key": "Two"; "value": 2}].<xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>

- {"One": 1, "Two": 2} ASP.NET AJAX<xref:System.Web.Script.Serialization.JavaScriptSerializer>

 <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>Je výkonnější v tom smyslu, že může zpracovávat slovníky, kde typ klíče není řetězec, zatímco <xref:System.Web.Script.Serialization.JavaScriptSerializer> nemůže. Ale druhá je srozumitelná pro JSON.

 Významné rozdíly mezi těmito serializátory jsou shrnuty v následující tabulce.

|Kategorie rozdílů|DataContractJsonSerializer|ASP.NET AJAX – JavaScriptSerializer|
|-----------------------------|--------------------------------|---------------------------------------|
|Deserializace prázdné vyrovnávací paměti (New Byte [0]) do <xref:System.Object> (nebo nebo <xref:System.Uri> jiných tříd).|SerializationException|null|
|Serializace<xref:System.DBNull.Value>|{}(nebo {"__type": "#System"})|Null|
|Serializace privátních členů typů [serializovatelných].|serializovat|Neserializované|
|Serializace veřejných vlastností <xref:System.Runtime.Serialization.ISerializable> typů.|Neserializované|serializovat|
|Rozšíření JSON|Dodržuje specifikaci JSON, která vyžaduje uvozovky na názvy členů objektu ({"a": "Hello"}).|Podporuje názvy členů objektů bez uvozovek ({a: "Hello"}).|
|<xref:System.DateTime>Koordinovaný světový čas (UTC)|Nepodporuje formát " \\ /Date (123456789U) \\ /" nebo "/date" \\ \\ (\d + (U&#124; ( \\ + \\ -[\d {4} ]))? \\ ) \\ \\ /)".|Podporuje formát " \\ /Date (123456789U) \\ /" a " \\ /Date" \\ (\d + (U&#124; ( \\ + \\ -[\d {4} ]))? \\ ) \\ \\ /) "jako hodnoty DateTime.|
|Reprezentace slovníků|Pole nenašla \<K,V> zpracovává typy klíčů, které nejsou řetězci.|Jako skutečné objekty JSON – ale zpracovává jenom typy klíčů, které jsou řetězce.|
|Řídicí znaky|Vždy s řídicím lomítkem (/); nikdy nepovoluje řídicí znaky neplatných znaků JSON, například "\n".|S řídicím lomítkem (/) pro hodnoty data a času.|

## <a name="see-also"></a>Viz také

- [Postupy: Použití konfigurace k přidání koncového bodu ASP.NET AJAX](how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md)
