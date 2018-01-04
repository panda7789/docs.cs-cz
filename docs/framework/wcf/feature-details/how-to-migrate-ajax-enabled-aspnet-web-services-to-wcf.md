---
title: "Postupy: Migrace webových služeb ASP.NET s podporou AJAXu na službu WCF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1428df4d-b18f-4e6d-bd4d-79ab3dd5147c
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2ca8dbbffdb48c33160e3c4f7495057b9ce60c13
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf"></a>Postupy: Migrace webových služeb ASP.NET s podporou AJAXu na službu WCF
Toto téma popisuje postupy k migraci základní služby prvku ASP.NET AJAX ekvivalentní podporou AJAXU [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] služby. Ukazuje, jak vytvořit funkčně srovnatelný [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] verzi služby prvku ASP.NET AJAX. Tyto dvě služby je pak možné použít vedle sebe, nebo [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby lze použít k nahrazení služba ASP.NET AJAX.  
  
 Migrace na existující službu prvku ASP.NET AJAX [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služba AJAX nabízí následující výhody:  
  
-   Vaše služba AJAX můžou zpřístupnit jako SOAP služby s minimálními další konfigurace.  
  
-   Můžete využívat výhod [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] funkce, jako je trasování a tak dále.  
  
 V následujících postupech se předpokládá, že používáte [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].  
  
 Kód, který vyplývá z postupů uvedených v tomto tématu najdete v příkladu postupy.  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]vystavení [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] přes koncový bod povolený AJAX, podívejte [postupy: použití konfigurace k přidání koncového bodu ASP.NET AJAX](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md) tématu.  
  
### <a name="to-create-and-test-the-aspnet-web-service-application"></a>Vytvoření a testování aplikace ASP.NET – webové služby  
  
1.  Otevřete [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].  
  
2.  Z **soubor** nabídce vyberte možnost **nový**, pak **projektu**, pak **webové**a potom vyberte **aplikaci webové služby ASP.NET** .  
  
3.  Název projektu `ASPHello` a klikněte na tlačítko **OK**.  
  
4.  Zrušením komentáře u řádku v souboru Service1.asmx.cs, který obsahuje `System.Web.Script.Services.ScriptService]` povolit AJAX pro tuto službu.  
  
5.  Z **sestavení** nabídce vyberte možnost **sestavit řešení**.  
  
6.  Z **ladění** nabídce vyberte možnost **spustit bez ladění**.  
  
7.  Na webové stránce generované, vyberte `HelloWorld` operaci.  
  
8.  Klikněte **Invoke** tlačítko `HelloWorld` zkušební stránku. Měli byste obdržet následující odpověď XML.  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <string xmlns="http://tempuri.org/">Hello World</string>  
    ```  
  
9. Tato odezva potvrdí, že teď máte funkční služba ASP.NET AJAX a, zejména v případě, že služba nyní vystavila koncový bod v Service1.asmx/HelloWorld, která reaguje na HTTP POST požadavky a vrátí XML.  
  
     Teď jste se převést tuto službu používat [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služba AJAX.  
  
### <a name="to-create-an-equivalent-wcf-ajax-service-application"></a>Chcete-li vytvořit ekvivalentní aplikace služby WCF AJAX  
  
1.  Klikněte pravým tlačítkem myši **ASPHello** projektu a vyberte **přidat**, pak **nová položka**a potom **podporou AJAXU služby WCF**.  
  
2.  Název služby `WCFHello` a klikněte na tlačítko **přidat**.  
  
3.  Otevřete soubor WCFHello.svc.cs.  
  
4.  Z Service1.asmx.cs, zkopírujte následující implementace `HelloWorld` operaci.  
  
    ```  
    public string HelloWorld()  
    {  
         return "Hello World";  
    }  
    ```  
  
5.  Vložte zkopírovaný provádění `HelloWorld` operace do souboru WCFHello.svc.cs místo následující kód.  
  
    ```  
    public void DoWork()  
    {  
          // Add your operation implementation here  
          return;  
    }  
    ```  
  
6.  Zadejte `Namespace` atribut pro <xref:System.ServiceModel.ServiceContractAttribute> jako `WCFHello`.  
  
    ```  
    [ServiceContract(Namespace="WCFHello")]  
    [AspNetCompatibilityRequirements(RequirementsMode=AspNetCompatibilityRequirementsMode.Required)]  
    public class WCFHello  
    { … }  
    ```  
  
7.  Přidat <xref:System.ServiceModel.Web.WebInvokeAttribute> k `HelloWorld` operace a sadu <xref:System.ServiceModel.Web.WebInvokeAttribute.ResponseFormat%2A> vlastnost vrátit <xref:System.ServiceModel.Web.WebMessageFormat.Xml>. Všimněte si, že, není-li nastavit, výchozí hodnota je návratový typ <xref:System.ServiceModel.Web.WebMessageFormat.Json>.  
  
    ```  
    [OperationContract]  
    [WebInvoke(ResponseFormat=WebMessageFormat.Xml)]  
    public string HelloWorld()  
    {  
        return "Hello World";  
    }  
    ```  
  
8.  Z **sestavení** nabídce vyberte možnost **sestavit řešení**.  
  
9. Otevřete soubor WCFHello.svc a z **ladění** nabídce vyberte možnost **spustit bez ladění**.  
  
10. Služba teď zpřístupní koncový bod v `WCFHello.svc/HelloWorld`, která reaguje na požadavky HTTP POST. Požadavky HTTP POST nelze testovat z prohlížeče, ale koncový bod vrátí následující XML XML.  
  
    ```xml  
    <string xmlns="http://schemas.microsoft.com/2003/10/Serialization/">Hello World</string>  
    ```  
  
11. `WCFHello.svc/HelloWorld` a `Service1.aspx/HelloWorld` koncové body jsou funkčně rovnocenné.  
  
## <a name="example"></a>Příklad  
 Kód, který vyplývá z postupů uvedených v tomto tématu najdete v následujícím příkladu.  
  
```  
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
  
 <xref:System.Xml.XmlDocument> Typ není podporován <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> protože není serializovatelný pomocí <xref:System.Xml.Serialization.XmlSerializer>. Můžete použít buď <xref:System.Xml.Linq.XDocument> zadejte nebo serializovat <xref:System.Xml.XmlDocument.DocumentElement%2A> místo.  
  
 Pokud ASMX webové služby se provádí upgrade a migrace souběžného k [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby, vyhněte se dva typy mapování se stejným názvem v klientovi. Tím dojde k výjimce v serializátorů Pokud stejný typ se používá v <xref:System.Web.Services.WebMethodAttribute> a <xref:System.ServiceModel.ServiceContractAttribute>:  
  
-   Pokud [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] nejprve přidání služby, vyvolání metody webové služby ASMX způsobí, že výjimka v <xref:System.Web.UI.ObjectConverter.ConvertValue%28System.Object%2CSystem.Type%2CSystem.String%29> protože [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] definici stylu pořadí v proxy serveru má přednost před.  
  
-   Pokud nejprve přidáte ASMX webové služby, volání metody na [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služba způsobuje výjimka v <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> definici stylu webové služby v pořadí proxy serveru má přednost před.  
  
 Existují významné rozdíly v chování mezi <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> a prvku ASP.NET AJAX <xref:System.Web.Script.Serialization.JavaScriptSerializer>. Například <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> představuje slovník jako pole dvojic klíč/hodnota, zatímco prvku ASP.NET AJAX <xref:System.Web.Script.Serialization.JavaScriptSerializer> představuje slovník jako skutečných objektů JSON. Tak, aby následující slovníku v prvku ASP.NET AJAX.  
  
```  
Dictionary<string, int> d = new Dictionary<string, int>();  
d.Add("one", 1);  
d.Add("two", 2);  
```  
  
 Tohoto slovníku je reprezentována v objekty JSON, jak je znázorněno v následujícím seznamu:  
  
-   [{"Klíč": "1", "Value": 1}, {"Klíč": "Dva", "Value": 2}] pomocí<xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>  
  
-   {"1": 1, "dva": 2} pomocí prvku ASP.NET AJAX<xref:System.Web.Script.Serialization.JavaScriptSerializer>  
  
 <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> Účinnější v tom smyslu, že je můžete zpracovat slovník kde klíče typem není řetězec, zatímco <xref:System.Web.Script.Serialization.JavaScriptSerializer> nelze. Ale k tomu je JSON popisný.  
  
 Významné rozdíly mezi tyto serializátorů jsou shrnuty v následující tabulce.  
  
|Kategorie rozdílů|DataContractJsonSerializer|ASP.NET AJAX JavaScriptSerializer|  
|-----------------------------|--------------------------------|---------------------------------------|  
|Při deserializaci prázdný vyrovnávací paměti (nové byte[0]) do <xref:System.Object> (nebo <xref:System.Uri>, nebo některé jiné třídy).|Serializationexception –|null|  
|Serializace<xref:System.DBNull.Value>|{} (nebo {"__type": "#System"})|Null|  
|Serializace soukromých členů typů [Serializable].|serializovat|nelze serializovat.|  
|Serializace veřejné vlastnosti <xref:System.Runtime.Serialization.ISerializable> typy.|nelze serializovat.|serializovat|  
|"Rozšíření" JSON|Dodržuje specifikaci JSON, která vyžaduje uvozovky na člen názvy objektů ({"a": "hello"}).|Podporuje názvy členové objektu bez uvozovek ({a: "text hello"}).|  
|<xref:System.DateTime>Koordinovaný světový čas (UTC)|Formát není podporován "\\/Date(123456789U)\\/" nebo "\\/Date\\(\d+ (P &#124; (\\+\\-[\d\{4\]}))?\\) \\\\/)".|Podporuje formát "\\/Date(123456789U)\\/" a "\\/Date\\(\d+ (P &#124; (\\+\\-[\d\{4\]}))?\\) \\ \\nebo) "jako hodnoty data a času.|  
|Reprezentace slovníků|Pole KeyValuePair\<tisíc, V >, zpracovává typy klíčů, které nejsou typu řetězec.|Jako skutečných objektů JSON -, ale pouze klíče typy obslužných rutin, které jsou řetězce.|  
|Uvozený znaků|Vždy s escape dopředné lomítko (/); nikdy umožňuje zrušení uvozený neplatné znaky JSON, jako je například "\n".|Pomocí escape dopředné lomítko (/) pro hodnoty data a času.|  
  
## <a name="see-also"></a>Viz také  
 [Postupy: Použití konfigurace k přidání koncového bodu ASP.NET AJAX](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md)
