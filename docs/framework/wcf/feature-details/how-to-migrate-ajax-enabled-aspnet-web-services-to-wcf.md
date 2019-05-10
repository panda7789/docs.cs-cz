---
title: 'Postupy: Migrace webových služeb ASP.NET s povolenou službou AJAX na WCF'
ms.date: 03/30/2017
ms.assetid: 1428df4d-b18f-4e6d-bd4d-79ab3dd5147c
ms.openlocfilehash: 1650ba6a12a9e81ff398e66a96ee2c70592f2428
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64643691"
---
# <a name="how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf"></a>Postupy: Migrace webových služeb ASP.NET s povolenou službou AJAX na WCF
Toto téma popisuje postupy migrace základní služby technologie ASP.NET AJAX do ekvivalentní služby s povoleným AJAX Windows Communication Foundation (WCF). Ukazuje, jak vytvořit funkčně ekvivalentní verzi WCF služby technologie ASP.NET AJAX. Tyto dvě služby je pak možné použít vedle sebe nebo službu WCF je možné nahradit služby technologie ASP.NET AJAX.

 Migrace stávající technologie ASP.NET AJAX komunikace mezi službami WCF AJAX poskytuje následující výhody:

- Vaše služba AJAX mohou vystavit jako službu SOAP s minimálními další konfiguraci.

- Můžete využívat funkce WCF, jako je sledování a tak dále.

 V následujících postupech se předpokládá, že používáte sadu Visual Studio 2012.

 Kód, které vyplývají z postupů uvedených v tomto tématu najdete v příkladu následující postupy.

 Další informace o vystavení služby WCF přes koncový bod s povoleným AJAX, najdete v článku [jak: Použití konfigurace k přidání koncového bodu ASP.NET AJAX](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md) tématu.

### <a name="to-create-and-test-the-aspnet-web-service-application"></a>Vytvořit a otestovat aplikaci technologie ASP.NET webové služby

1. Open Visual Studio 2012.

2. Z **souboru** nabídce vyberte možnost **nový**, pak **projektu**, pak **webové**a pak vyberte **aplikaci webové služby ASP.NET** .

3. Pojmenujte projekt `ASPHello` a klikněte na tlačítko **OK**.

4. Zrušením komentáře u řádku v souboru Service1.asmx.cs, který obsahuje `System.Web.Script.Services.ScriptService]` umožňující AJAX pro tuto službu.

5. Z **sestavení** nabídce vyberte možnost **sestavit řešení**.

6. Z **ladění** nabídce vyberte možnost **spustit bez ladění**.

7. Na webové stránce vygenerovat, vyberte `HelloWorld` operace.

8. Klikněte na tlačítko **Invoke** tlačítko `HelloWorld` zkušební stránku. Měli byste obdržet odpověď na následující XML.

    ```xml
    <?xml version="1.0" encoding="utf-8" ?>
    <string xmlns="http://tempuri.org/">Hello World</string>
    ```

9. Tato odpověď potvrzuje, že teď máte funkční služba ASP.NET AJAX, konkrétně se, že služba má nyní zpřístupněn koncový bod na Service1.asmx/HelloWorld, který reaguje na HTTP POST požadavků a vrátí XML.

     Nyní jste připraveni k převedení této služby k používání služby WCF AJAX.

### <a name="to-create-an-equivalent-wcf-ajax-service-application"></a>Chcete-li vytvořit rovnocenné aplikace služby WCF AJAX

1. Klikněte pravým tlačítkem myši **ASPHello** projektu a vyberte **přidat**, pak **nová položka**a potom **s povoleným AJAX služba WCF**.

2. Pojmenujte službu `WCFHello` a klikněte na tlačítko **přidat**.

3. Otevřete soubor WCFHello.svc.cs.

4. Z Service1.asmx.cs, zkopírujte následující provádění `HelloWorld` operace.

    ```
    public string HelloWorld()
    {
         return "Hello World";
    }
    ```

5. Vložte zkopírovaný provádění `HelloWorld` operace do souboru WCFHello.svc.cs místo následující kód.

    ```
    public void DoWork()
    {
          // Add your operation implementation here
          return;
    }
    ```

6. Zadejte `Namespace` atributu <xref:System.ServiceModel.ServiceContractAttribute> jako `WCFHello`.

    ```
    [ServiceContract(Namespace="WCFHello")]
    [AspNetCompatibilityRequirements(RequirementsMode=AspNetCompatibilityRequirementsMode.Required)]
    public class WCFHello
    { … }
    ```

7. Přidat <xref:System.ServiceModel.Web.WebInvokeAttribute> k `HelloWorld` operace a sady <xref:System.ServiceModel.Web.WebInvokeAttribute.ResponseFormat%2A> vlastnost vrátit <xref:System.ServiceModel.Web.WebMessageFormat.Xml>. Všimněte si, že, pokud není nastavena, výchozí hodnota je návratový typ <xref:System.ServiceModel.Web.WebMessageFormat.Json>.

    ```
    [OperationContract]
    [WebInvoke(ResponseFormat=WebMessageFormat.Xml)]
    public string HelloWorld()
    {
        return "Hello World";
    }
    ```

8. Z **sestavení** nabídce vyberte možnost **sestavit řešení**.

9. Otevřete soubor WCFHello.svc z a **ladění** nabídce vyberte možnost **spustit bez ladění**.

10. Služba teď zpřístupňuje koncový bod na `WCFHello.svc/HelloWorld`, který reaguje na požadavky HTTP POST. Požadavky HTTP POST nelze provést test z prohlížeče, ale koncový bod vrátí následující XML XML.

    ```xml
    <string xmlns="http://schemas.microsoft.com/2003/10/Serialization/">Hello World</string>
    ```

11. `WCFHello.svc/HelloWorld` a `Service1.aspx/HelloWorld` koncové body jsou funkčně ekvivalentní.

## <a name="example"></a>Příklad
 Kód, který je výsledkem postupů uvedených v tomto tématu najdete v následujícím příkladu.

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

 <xref:System.Xml.XmlDocument> Typ není podporován <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> protože to není serializovatelný podle <xref:System.Xml.Serialization.XmlSerializer>. Můžete použít buď <xref:System.Xml.Linq.XDocument> zadejte nebo serializovat <xref:System.Xml.XmlDocument.DocumentElement%2A> místo.

 Pokud ASMX webovými službami jsou upgraduje a migrovat vedle sebe ke službám WCF, vyhněte se dva typy mapování na stejné jméno v klientovi. To způsobí, že výjimka v serializátory Pokud je používán stejného typu <xref:System.Web.Services.WebMethodAttribute> a <xref:System.ServiceModel.ServiceContractAttribute>:

- Pokud nejprve přidáte službu WCF, volání metody na webovou službu ASMX způsobí, že výjimka v <xref:System.Web.UI.ObjectConverter.ConvertValue%28System.Object%2CSystem.Type%2CSystem.String%29> vzhledem k tomu, že má přednost před definice stylu WCF objednávky v proxy serveru.

- Pokud nejprve přidá ASMX webovou službu, volání metody na službu WCF způsobí, že výjimka v <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> vzhledem k tomu, že má přednost před definice stylu webové služby objednávky v proxy serveru.

 Existují významné rozdíly v chování mezi <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> a technologie ASP.NET AJAX <xref:System.Web.Script.Serialization.JavaScriptSerializer>. Například <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> představuje slovník jako pole párů klíč/hodnota, že technologie ASP.NET AJAX <xref:System.Web.Script.Serialization.JavaScriptSerializer> představuje slovník jako skutečné objekty JSON. Takže tady je slovník reprezentovány v rozhraní ASP.NET AJAX.

```
Dictionary<string, int> d = new Dictionary<string, int>();
d.Add("one", 1);
d.Add("two", 2);
```

 Tento slovník je reprezentován v objektech JSON, jak je znázorněno v následujícím seznamu:

- [{"Klíče": "Jedna", "Value": 1}, {"Klíče": "Dvě", "Value": 2}] ve <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>

- {"jedna": 1, "dvě": 2} pomocí technologie ASP.NET AJAX <xref:System.Web.Script.Serialization.JavaScriptSerializer>

 <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> Účinnější v tom smyslu, že dokáže zpracovat slovníky kde typ klíče není řetězec, zatímco <xref:System.Web.Script.Serialization.JavaScriptSerializer> nelze. Ale je více vhodných JSON.

 Významné rozdíly mezi těmito serializátory jsou shrnuty v následující tabulce.

|Kategorie rozdíly|DataContractJsonSerializer|ASP.NET AJAX JavaScriptSerializer|
|-----------------------------|--------------------------------|---------------------------------------|
|Deserializace prázdné vyrovnávací paměti (nové byte[0]) do <xref:System.Object> (nebo <xref:System.Uri>, nebo některé jiné třídy).|SerializationException|null|
|Serializace <xref:System.DBNull.Value>|{} (nebo {"__type": "#System"})|Null|
|Serializace soukromé členy typů [Serializable].|serializovat|nelze serializovat.|
|Serializace veřejné vlastnosti <xref:System.Runtime.Serialization.ISerializable> typy.|nelze serializovat.|serializovat|
|"Rozšíření" formátu JSON|Dodržuje specifikaci formátu JSON, která vyžaduje uvozovky na názvy členů objektu ({"a": "hello"}).|Podporuje názvy členů objektu bez uvozovek ({a: "hello"}).|
|<xref:System.DateTime> Koordinovaný světový čas (UTC)|Nepodporuje formát "\\/Date(123456789U)\\/" nebo "\\/Date\\(\d+ (U&#124;(\\+\\-[\d{4}]))?\\) \\\\/)".|Podporuje formát "\\/Date(123456789U)\\/" a "\\/Date\\(\d+ (U&#124;(\\+\\-[\d{4}]))?\\) \\ \\/) "jako hodnoty data a času.|
|Reprezentace slovníky|Celou řadu komponent\<K, V >, zpracovává typy klíčů, které nejsou řetězce.|Jako skutečné objekty JSON -, ale pouze typy klíčů obslužné rutiny, které jsou řetězce.|
|Řídicí znaky|Vždy s řídicí sekvence dopředné lomítko (/); nikdy umožňuje uvozeny řídicími znaky neplatné znaky JSON, jako je například "\n".|S řídicí sekvence dopředné lomítko (/) pro hodnoty data a času.|

## <a name="see-also"></a>Viz také:

- [Postupy: Použití konfigurace k přidání koncového bodu ASP.NET AJAX](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md)
