---
title: Interoperabilita s webovými službami ASP.NET
ms.date: 03/30/2017
ms.assetid: 622422f8-6651-442f-b8be-e654a4aabcac
ms.openlocfilehash: 41810d8044e4b7ff3193950a914edbf1e61cffb1
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2020
ms.locfileid: "81464095"
---
# <a name="interoperability-with-aspnet-web-services"></a><span data-ttu-id="71dc4-102">Interoperabilita s webovými službami ASP.NET</span><span class="sxs-lookup"><span data-stu-id="71dc4-102">Interoperability with ASP.NET Web Services</span></span>
<span data-ttu-id="71dc4-103">Interoperability mezi ASP.NET webovými službami a webovými službami WCF (Windows Communication Foundation) lze dosáhnout zajištěním, aby služby implementované pomocí obou technologií odpovídaly specifikaci WS-I Basic Profile 1.1.</span><span class="sxs-lookup"><span data-stu-id="71dc4-103">Interoperability between ASP.NET Web services and Windows Communication Foundation (WCF) Web services can be achieved by ensuring that services implemented using both technologies conform to the WS-I Basic Profile 1.1 specification.</span></span> <span data-ttu-id="71dc4-104">ASP.NET webové služby, které odpovídají WS-I Základní profil 1.1 jsou interoperabilní s <xref:System.ServiceModel.BasicHttpBinding>wcf klienty pomocí WCF systémem poskytované vazby , .</span><span class="sxs-lookup"><span data-stu-id="71dc4-104">ASP.NET Web services that conform to WS-I Basic Profile 1.1 are interoperable with WCF clients by using WCF system-provided binding, <xref:System.ServiceModel.BasicHttpBinding>.</span></span>  
  
 <span data-ttu-id="71dc4-105">Použijte ASP.NET možnost 2.0 <xref:System.Web.Services.WebService> <xref:System.Web.Services.WebMethodAttribute> přidání atributy a do rozhraní spíše než do třídy a psaní třídy k implementaci rozhraní, jak je znázorněno v následujícím ukázkovém kódu.</span><span class="sxs-lookup"><span data-stu-id="71dc4-105">Use ASP.NET 2.0 option of adding the <xref:System.Web.Services.WebService> and <xref:System.Web.Services.WebMethodAttribute> attributes to an interface rather than to a class, and writing a class to implement the interface, as shown in the following sample code.</span></span>  
  
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
  
 <span data-ttu-id="71dc4-106">Použití této možnosti je upřednostňováno, protože rozhraní s atributem <xref:System.Web.Services.WebService> představuje kontrakt pro operace prováděné službou, které lze znovu použít s různými třídami, které mohou implementovat stejnou smlouvu různými způsoby.</span><span class="sxs-lookup"><span data-stu-id="71dc4-106">Using this option is preferred, because the interface with the <xref:System.Web.Services.WebService> attribute constitutes a contract for the operations performed by the service that can be reused with various classes that might implement that same contract in different ways.</span></span>  
  
 <span data-ttu-id="71dc4-107">Nepoužívejte <xref:System.Web.Services.Protocols.SoapDocumentServiceAttribute> atribut k tomu, aby zprávy byly směrovány na metody založené na plně `SOAPAction` kvalifikovaném názvu prvku body zprávy SOAP, nikoli na hlavičku HTTP.</span><span class="sxs-lookup"><span data-stu-id="71dc4-107">Avoid using the <xref:System.Web.Services.Protocols.SoapDocumentServiceAttribute> attribute to have messages routed to methods based on the fully-qualified name of the body element of the SOAP message rather than the `SOAPAction` HTTP header.</span></span> <span data-ttu-id="71dc4-108">WCF používá `SOAPAction` hlavičku HTTP pro směrování zpráv.</span><span class="sxs-lookup"><span data-stu-id="71dc4-108">WCF uses the `SOAPAction` HTTP header for routing messages.</span></span>  
  
 <span data-ttu-id="71dc4-109">Xml, do <xref:System.Xml.Serialization.XmlSerializer> kterého serializuje typ ve výchozím nastavení je sémanticky identické s XML, do kterého <xref:System.Runtime.Serialization.DataContractSerializer> serializes typu, za předpokladu, že obor názvů pro XML je explicitně definován.</span><span class="sxs-lookup"><span data-stu-id="71dc4-109">The XML into which <xref:System.Xml.Serialization.XmlSerializer> serializes a type by default is semantically identical to the XML into which the <xref:System.Runtime.Serialization.DataContractSerializer> serializes a type, provided the namespace for the XML is explicitly defined.</span></span> <span data-ttu-id="71dc4-110">Při definování datového typu pro použití se službami ASP.NETWeb v očekávání přijetí WCF postupujte takto:</span><span class="sxs-lookup"><span data-stu-id="71dc4-110">When defining a data type for use with ASP.NETWeb services in anticipation of adopting WCF, do the following:</span></span>  
  
- <span data-ttu-id="71dc4-111">Definujte typ pomocí tříd rozhraní .NET Framework, nikoli schématu XML.</span><span class="sxs-lookup"><span data-stu-id="71dc4-111">Define the type using .NET Framework classes rather than XML Schema.</span></span>  
  
- <span data-ttu-id="71dc4-112">Přidejte <xref:System.SerializableAttribute> pouze <xref:System.Xml.Serialization.XmlRootAttribute> a a do třídy, pomocí druhé explicitně definovat obor názvů pro typ.</span><span class="sxs-lookup"><span data-stu-id="71dc4-112">Add only the <xref:System.SerializableAttribute> and the <xref:System.Xml.Serialization.XmlRootAttribute> to the class, using the latter to explicitly define the namespace for the type.</span></span> <span data-ttu-id="71dc4-113">Nepřidávejte další atributy <xref:System.Xml.Serialization> z oboru názvů, abyste řídili, jak má být třída rozhraní .NET Framework přeložena do jazyka XML.</span><span class="sxs-lookup"><span data-stu-id="71dc4-113">Do not add additional attributes from the <xref:System.Xml.Serialization> namespace to control how the .NET Framework class is to be translated into XML.</span></span>  
  
- <span data-ttu-id="71dc4-114">Přijetím tohoto přístupu byste měli být schopni později provést třídy .NET do datových kontraktů s přidáním <xref:System.Runtime.Serialization.DataContractAttribute> a <xref:System.Runtime.Serialization.DataMemberAttribute> bez významné změny XML, do kterého jsou třídy serializovány pro přenos.</span><span class="sxs-lookup"><span data-stu-id="71dc4-114">By adopting this approach, you should be able to later make the .NET classes into data contracts with the addition of the <xref:System.Runtime.Serialization.DataContractAttribute> and <xref:System.Runtime.Serialization.DataMemberAttribute> without significantly altering the XML into which the classes are serialized for transmission.</span></span> <span data-ttu-id="71dc4-115">Typy používané ve zprávách ASP.NET webových služeb mohou být zpracovány jako kontrakty dat aplikacemi WCF, což mimo jiné přináší lepší výkon v aplikacích WCF.</span><span class="sxs-lookup"><span data-stu-id="71dc4-115">The types used in messages by ASP.NET Web services can be processed as data contracts by WCF applications, yielding, among other benefits, better performance in WCF applications.</span></span>  
  
 <span data-ttu-id="71dc4-116">Nepoužívejte možnosti ověřování poskytované Internetovou informační službou (IIS).</span><span class="sxs-lookup"><span data-stu-id="71dc4-116">Avoid using the authentication options provided by Internet Information Services (IIS).</span></span> <span data-ttu-id="71dc4-117">Klienti WCF je nepodporují.</span><span class="sxs-lookup"><span data-stu-id="71dc4-117">WCF clients do not support them.</span></span> <span data-ttu-id="71dc4-118">Pokud musí být služba zabezpečena, použijte možnosti poskytované WCF, protože tyto možnosti jsou robustní a jsou založeny na standardních protokolech.</span><span class="sxs-lookup"><span data-stu-id="71dc4-118">If a service must be secured, use the options provided by WCF, because these options are robust and are based on standard protocols.</span></span>  
  
## <a name="performance-impact-caused-by-loading-the-servicemodel-httpmodule"></a><span data-ttu-id="71dc4-119">Dopad na výkon způsobený načtením modulu ServiceModel HttpModule</span><span class="sxs-lookup"><span data-stu-id="71dc4-119">Performance impact caused by loading the ServiceModel HttpModule</span></span>  
 <span data-ttu-id="71dc4-120">V rozhraní .NET Framework 3.0 `HttpModule` byl wcf nainstalován v kořenovém souboru Web.config tak, aby každá ASP.NET aplikace byla povolena WCF.</span><span class="sxs-lookup"><span data-stu-id="71dc4-120">In the .NET Framework 3.0, the WCF `HttpModule` was installed in the root Web.config file such that every ASP.NET application was WCF enabled.</span></span> <span data-ttu-id="71dc4-121">To může ovlivnit výkon, `ServiceModel` takže můžete odebrat soubor Web.config, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="71dc4-121">This might affect performance, so you can remove `ServiceModel` for the Web.config file as shown in the following example.</span></span>  
  
```xml  
<httpModules>  
    <remove name="ServiceModel" />  
</httpModules>
```  
  
## <a name="see-also"></a><span data-ttu-id="71dc4-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="71dc4-122">See also</span></span>

- [<span data-ttu-id="71dc4-123">Postupy: Konfigurace služby WCF pro spolupráci s klienty webové služby ASP.NET</span><span class="sxs-lookup"><span data-stu-id="71dc4-123">How to: Configure WCF Service to Interoperate with ASP.NET Web Service Clients</span></span>](../../../../docs/framework/wcf/feature-details/config-wcf-service-with-aspnet-web-service.md)
