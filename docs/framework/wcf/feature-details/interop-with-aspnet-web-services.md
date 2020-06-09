---
title: Interoperabilita s webovými službami ASP.NET
ms.date: 03/30/2017
ms.assetid: 622422f8-6651-442f-b8be-e654a4aabcac
ms.openlocfilehash: f38209ffe2161e58528a108b29e730665a65da37
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84598863"
---
# <a name="interoperability-with-aspnet-web-services"></a><span data-ttu-id="d281f-102">Interoperabilita s webovými službami ASP.NET</span><span class="sxs-lookup"><span data-stu-id="d281f-102">Interoperability with ASP.NET Web Services</span></span>
<span data-ttu-id="d281f-103">Vzájemná spolupráce mezi webovými službami ASP.NET Web Services a Windows Communication Foundation (WCF) je možné dosáhnout tím, že zajistíte, aby služby implementované pomocí obou technologií splňovaly specifikaci 1,1 profilu WS-I Basic.</span><span class="sxs-lookup"><span data-stu-id="d281f-103">Interoperability between ASP.NET Web services and Windows Communication Foundation (WCF) Web services can be achieved by ensuring that services implemented using both technologies conform to the WS-I Basic Profile 1.1 specification.</span></span> <span data-ttu-id="d281f-104">Webové služby ASP.NET, které odpovídají profilu WS-I Basic Profile 1,1, se vzájemně spolupracují s klienty WCF pomocí vazby poskytované systémem služby WCF <xref:System.ServiceModel.BasicHttpBinding> .</span><span class="sxs-lookup"><span data-stu-id="d281f-104">ASP.NET Web services that conform to WS-I Basic Profile 1.1 are interoperable with WCF clients by using WCF system-provided binding, <xref:System.ServiceModel.BasicHttpBinding>.</span></span>  
  
 <span data-ttu-id="d281f-105">Použijte možnost ASP.NET 2,0 pro přidání <xref:System.Web.Services.WebService> atributů a <xref:System.Web.Services.WebMethodAttribute> k rozhraní, nikoli ke třídě, a zápis třídy pro implementaci rozhraní, jak je znázorněno v následujícím ukázkovém kódu.</span><span class="sxs-lookup"><span data-stu-id="d281f-105">Use ASP.NET 2.0 option of adding the <xref:System.Web.Services.WebService> and <xref:System.Web.Services.WebMethodAttribute> attributes to an interface rather than to a class, and writing a class to implement the interface, as shown in the following sample code.</span></span>  
  
```csharp
[WebService]  
public interface IEcho  
{  
    [WebMethod]  
    string Echo(string input);  
}  
  
public class Service : IEcho  
{  
  
   public string Echo(string input)  
   {  
        return input;  
    }  
}  
```  
  
 <span data-ttu-id="d281f-106">Použití této možnosti je preferované, protože rozhraní s <xref:System.Web.Services.WebService> atributem představuje kontrakt pro operace prováděné službou, které lze znovu použít s různými třídami, které mohou implementovat stejný kontrakt různými způsoby.</span><span class="sxs-lookup"><span data-stu-id="d281f-106">Using this option is preferred, because the interface with the <xref:System.Web.Services.WebService> attribute constitutes a contract for the operations performed by the service that can be reused with various classes that might implement that same contract in different ways.</span></span>  
  
 <span data-ttu-id="d281f-107">Nepoužívejte <xref:System.Web.Services.Protocols.SoapDocumentServiceAttribute> atribut ke směrování zpráv na metody založené na plně kvalifikovaném názvu prvku těla zprávy SOAP, nikoli v `SOAPAction` hlavičce protokolu HTTP.</span><span class="sxs-lookup"><span data-stu-id="d281f-107">Avoid using the <xref:System.Web.Services.Protocols.SoapDocumentServiceAttribute> attribute to have messages routed to methods based on the fully-qualified name of the body element of the SOAP message rather than the `SOAPAction` HTTP header.</span></span> <span data-ttu-id="d281f-108">WCF používá `SOAPAction` hlavičku protokolu HTTP pro zprávy směrování.</span><span class="sxs-lookup"><span data-stu-id="d281f-108">WCF uses the `SOAPAction` HTTP header for routing messages.</span></span>  
  
 <span data-ttu-id="d281f-109">KÓD XML, do kterého <xref:System.Xml.Serialization.XmlSerializer> je ve výchozím nastavení serializován typ, je sémanticky totožný s XML, do kterého je <xref:System.Runtime.Serialization.DataContractSerializer> serializován typ, za předpokladu, že obor názvů XML je explicitně definován.</span><span class="sxs-lookup"><span data-stu-id="d281f-109">The XML into which <xref:System.Xml.Serialization.XmlSerializer> serializes a type by default is semantically identical to the XML into which the <xref:System.Runtime.Serialization.DataContractSerializer> serializes a type, provided the namespace for the XML is explicitly defined.</span></span> <span data-ttu-id="d281f-110">Při definování datového typu pro použití s ASP. NETWeb Services při předvídání přijímání služby WCF postupujte takto:</span><span class="sxs-lookup"><span data-stu-id="d281f-110">When defining a data type for use with ASP.NETWeb services in anticipation of adopting WCF, do the following:</span></span>  
  
- <span data-ttu-id="d281f-111">Definujte typ pomocí .NET Framework třídy místo schématu XML.</span><span class="sxs-lookup"><span data-stu-id="d281f-111">Define the type using .NET Framework classes rather than XML Schema.</span></span>  
  
- <span data-ttu-id="d281f-112">Přidejte pouze <xref:System.SerializableAttribute> <xref:System.Xml.Serialization.XmlRootAttribute> třídu a ke třídě pomocí druhé k explicitnímu definování oboru názvů pro daný typ.</span><span class="sxs-lookup"><span data-stu-id="d281f-112">Add only the <xref:System.SerializableAttribute> and the <xref:System.Xml.Serialization.XmlRootAttribute> to the class, using the latter to explicitly define the namespace for the type.</span></span> <span data-ttu-id="d281f-113">Nepřidávejte další atributy z <xref:System.Xml.Serialization> oboru názvů, abyste mohli určit, jak se má třída .NET Framework přeložit do XML.</span><span class="sxs-lookup"><span data-stu-id="d281f-113">Do not add additional attributes from the <xref:System.Xml.Serialization> namespace to control how the .NET Framework class is to be translated into XML.</span></span>  
  
- <span data-ttu-id="d281f-114">Přijetím tohoto přístupu byste měli být schopni později převést třídy .NET na kontrakty dat s přidáním <xref:System.Runtime.Serialization.DataContractAttribute> a <xref:System.Runtime.Serialization.DataMemberAttribute> bez významně měnit kód XML, do kterého jsou třídy serializovány pro přenos.</span><span class="sxs-lookup"><span data-stu-id="d281f-114">By adopting this approach, you should be able to later make the .NET classes into data contracts with the addition of the <xref:System.Runtime.Serialization.DataContractAttribute> and <xref:System.Runtime.Serialization.DataMemberAttribute> without significantly altering the XML into which the classes are serialized for transmission.</span></span> <span data-ttu-id="d281f-115">Typy, které se používají ve zprávách pomocí webových služeb ASP.NET, je možné zpracovat jako kontrakty dat aplikacemi WCF, a to mimo jiné výhody a lepší výkon v aplikacích WCF.</span><span class="sxs-lookup"><span data-stu-id="d281f-115">The types used in messages by ASP.NET Web services can be processed as data contracts by WCF applications, yielding, among other benefits, better performance in WCF applications.</span></span>  
  
 <span data-ttu-id="d281f-116">Nepoužívejte možnosti ověřování poskytované Internetová informační služba (IIS).</span><span class="sxs-lookup"><span data-stu-id="d281f-116">Avoid using the authentication options provided by Internet Information Services (IIS).</span></span> <span data-ttu-id="d281f-117">Klienti WCF je nepodporují.</span><span class="sxs-lookup"><span data-stu-id="d281f-117">WCF clients do not support them.</span></span> <span data-ttu-id="d281f-118">Pokud musí být služba zabezpečená, použijte možnosti poskytované službou WCF, protože tyto možnosti jsou robustní a jsou založené na standardních protokolech.</span><span class="sxs-lookup"><span data-stu-id="d281f-118">If a service must be secured, use the options provided by WCF, because these options are robust and are based on standard protocols.</span></span>  
  
## <a name="performance-impact-caused-by-loading-the-servicemodel-httpmodule"></a><span data-ttu-id="d281f-119">Dopad na výkon způsobený načtením modulu pro odeslání ServiceModel</span><span class="sxs-lookup"><span data-stu-id="d281f-119">Performance impact caused by loading the ServiceModel HttpModule</span></span>  
 <span data-ttu-id="d281f-120">V .NET Framework 3,0 byla služba WCF `HttpModule` nainstalována do kořenového souboru Web. config tak, aby každá aplikace ASP.NET byla povolená služba WCF.</span><span class="sxs-lookup"><span data-stu-id="d281f-120">In the .NET Framework 3.0, the WCF `HttpModule` was installed in the root Web.config file such that every ASP.NET application was WCF enabled.</span></span> <span data-ttu-id="d281f-121">To může mít vliv na výkon, takže můžete `ServiceModel` soubor Web. config odebrat, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="d281f-121">This might affect performance, so you can remove `ServiceModel` for the Web.config file as shown in the following example.</span></span>  
  
```xml  
<httpModules>  
    <remove name="ServiceModel" />  
</httpModules>
```  
  
## <a name="see-also"></a><span data-ttu-id="d281f-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="d281f-122">See also</span></span>

- [<span data-ttu-id="d281f-123">Postupy: Konfigurace služby WCF pro spolupráci s klienty webové služby ASP.NET</span><span class="sxs-lookup"><span data-stu-id="d281f-123">How to: Configure WCF Service to Interoperate with ASP.NET Web Service Clients</span></span>](config-wcf-service-with-aspnet-web-service.md)
