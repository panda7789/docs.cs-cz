---
title: Interoperabilita s webovými službami ASP.NET
ms.date: 03/30/2017
ms.assetid: 622422f8-6651-442f-b8be-e654a4aabcac
ms.openlocfilehash: c6fec1d520cd251473d8840b7b1afe879002a04c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59108573"
---
# <a name="interoperability-with-aspnet-web-services"></a><span data-ttu-id="34087-102">Interoperabilita s webovými službami ASP.NET</span><span class="sxs-lookup"><span data-stu-id="34087-102">Interoperability with ASP.NET Web Services</span></span>
<span data-ttu-id="34087-103">Vzájemná funkční spolupráce mezi [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] webových služeb a služeb Windows Communication Foundation (WCF) Web můžete dosáhnout tím, že zajišťuje, že služby implementované pomocí obou technologií odpovídají WS-I Basic Profile 1.1 specifikace.</span><span class="sxs-lookup"><span data-stu-id="34087-103">Interoperability between [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Web services and Windows Communication Foundation (WCF) Web services can be achieved by ensuring that services implemented using both technologies conform to the WS-I Basic Profile 1.1 specification.</span></span> [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] <span data-ttu-id="34087-104">Webové služby, které odpovídají WS-I Basic Profile 1.1 se vzájemná spolupráce s klienty WCF pomocí WCF vazeb poskytovaných systémem, <xref:System.ServiceModel.BasicHttpBinding>.</span><span class="sxs-lookup"><span data-stu-id="34087-104">Web services that conform to WS-I Basic Profile 1.1 are interoperable with WCF clients by using WCF system-provided binding, <xref:System.ServiceModel.BasicHttpBinding>.</span></span>  
  
 <span data-ttu-id="34087-105">Použití [!INCLUDE[vstecasplong](../../../../includes/vstecasplong-md.md)] možnost Přidat <xref:System.Web.Services.WebService> a <xref:System.Web.Services.WebMethodAttribute> atributy rozhraní, nikoli třída a zápis třídu pro implementaci rozhraní, jak je znázorněno v následujícím ukázkovém kódu.</span><span class="sxs-lookup"><span data-stu-id="34087-105">Use [!INCLUDE[vstecasplong](../../../../includes/vstecasplong-md.md)] option of adding the <xref:System.Web.Services.WebService> and <xref:System.Web.Services.WebMethodAttribute> attributes to an interface rather than to a class, and writing a class to implement the interface, as shown in the following sample code.</span></span>  
  
```  
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
  
 <span data-ttu-id="34087-106">Pomocí této možnosti je upřednostňované, protože rozhraní s <xref:System.Web.Services.WebService> atributu tvoří kontrakt operace prováděné na službu, kterou lze opětovně použít s různými třídami, které mohou implementovat tento stejný kontrakt různými způsoby.</span><span class="sxs-lookup"><span data-stu-id="34087-106">Using this option is preferred, because the interface with the <xref:System.Web.Services.WebService> attribute constitutes a contract for the operations performed by the service that can be reused with various classes that might implement that same contract in different ways.</span></span>  
  
 <span data-ttu-id="34087-107">Vyhněte se použití <xref:System.Web.Services.Protocols.SoapDocumentServiceAttribute> atribut zprávy směruje do metody podle plně kvalifikovaný název elementu těla zprávy protokolu SOAP místo `SOAPAction` hlavičky protokolu HTTP.</span><span class="sxs-lookup"><span data-stu-id="34087-107">Avoid using the <xref:System.Web.Services.Protocols.SoapDocumentServiceAttribute> attribute to have messages routed to methods based on the fully-qualified name of the body element of the SOAP message rather than the `SOAPAction` HTTP header.</span></span> <span data-ttu-id="34087-108">Používá WCF `SOAPAction` hlavičku protokolu HTTP pro směrování zpráv.</span><span class="sxs-lookup"><span data-stu-id="34087-108">WCF uses the `SOAPAction` HTTP header for routing messages.</span></span>  
  
 <span data-ttu-id="34087-109">XML, do kterého <xref:System.Xml.Serialization.XmlSerializer> serializuje typu ve výchozím nastavení je sémanticky shodná s XML, do kterého <xref:System.Runtime.Serialization.DataContractSerializer> serializuje typu podle oboru názvů XML není výslovně uveden.</span><span class="sxs-lookup"><span data-stu-id="34087-109">The XML into which <xref:System.Xml.Serialization.XmlSerializer> serializes a type by default is semantically identical to the XML into which the <xref:System.Runtime.Serialization.DataContractSerializer> serializes a type, provided the namespace for the XML is explicitly defined.</span></span> <span data-ttu-id="34087-110">Při definování datový typ pro použití s [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]webové služby na případná přijetí WCF, postupujte takto:</span><span class="sxs-lookup"><span data-stu-id="34087-110">When defining a data type for use with [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]Web services in anticipation of adopting WCF, do the following:</span></span>  
  
-   <span data-ttu-id="34087-111">Definování typů pomocí tříd rozhraní .NET Framework než schématu XML.</span><span class="sxs-lookup"><span data-stu-id="34087-111">Define the type using .NET Framework classes rather than XML Schema.</span></span>  
  
-   <span data-ttu-id="34087-112">Přidat pouze <xref:System.SerializableAttribute> a <xref:System.Xml.Serialization.XmlRootAttribute> na třídu pomocí odkazující k explicitnímu definování oboru názvů typu.</span><span class="sxs-lookup"><span data-stu-id="34087-112">Add only the <xref:System.SerializableAttribute> and the <xref:System.Xml.Serialization.XmlRootAttribute> to the class, using the latter to explicitly define the namespace for the type.</span></span> <span data-ttu-id="34087-113">Nepřidávejte další atributy z <xref:System.Xml.Serialization> obor názvů řídit, jak je třída rozhraní .NET Framework mají být převedeny do jazyka XML.</span><span class="sxs-lookup"><span data-stu-id="34087-113">Do not add additional attributes from the <xref:System.Xml.Serialization> namespace to control how the .NET Framework class is to be translated into XML.</span></span>  
  
-   <span data-ttu-id="34087-114">Přijetím tohoto přístupu by měl být schopen později provést třídy rozhraní .NET v kontraktech dat a uveďte <xref:System.Runtime.Serialization.DataContractAttribute> a <xref:System.Runtime.Serialization.DataMemberAttribute> beze změny výrazně XML, do které třídy serializují pro přenos.</span><span class="sxs-lookup"><span data-stu-id="34087-114">By adopting this approach, you should be able to later make the .NET classes into data contracts with the addition of the <xref:System.Runtime.Serialization.DataContractAttribute> and <xref:System.Runtime.Serialization.DataMemberAttribute> without significantly altering the XML into which the classes are serialized for transmission.</span></span> <span data-ttu-id="34087-115">Typy používané v zprávy podle [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] webové služby může zpracovat jako kontraktů dat aplikací služby WCF, což má za následek, kromě dalších výhod, lepší výkon v aplikacích WCF.</span><span class="sxs-lookup"><span data-stu-id="34087-115">The types used in messages by [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Web services can be processed as data contracts by WCF applications, yielding, among other benefits, better performance in WCF applications.</span></span>  
  
 <span data-ttu-id="34087-116">Vyhněte se použití možnosti ověřování, které jsou k dispozici Internetové informační služby (IIS).</span><span class="sxs-lookup"><span data-stu-id="34087-116">Avoid using the authentication options provided by Internet Information Services (IIS).</span></span> <span data-ttu-id="34087-117">Klienti WCF je nepodporují.</span><span class="sxs-lookup"><span data-stu-id="34087-117">WCF clients do not support them.</span></span> <span data-ttu-id="34087-118">Pokud služba musí být zabezpečená, použijte možnosti poskytované WCF, protože tyto možnosti jsou odolnější a jsou založeny na standardních protokolů.</span><span class="sxs-lookup"><span data-stu-id="34087-118">If a service must be secured, use the options provided by WCF, because these options are robust and are based on standard protocols.</span></span>  
  
## <a name="performance-impact-caused-by-loading-the-servicemodel-httpmodule"></a><span data-ttu-id="34087-119">Dopad na výkon způsobené načítání ServiceModel HttpModule</span><span class="sxs-lookup"><span data-stu-id="34087-119">Performance impact caused by loading the ServiceModel HttpModule</span></span>  
 <span data-ttu-id="34087-120">V rozhraní .NET Framework 3.0 WCF `HttpModule` byla nainstalovaná v kořenovém souboru Web.config tak, aby každá aplikace technologie ASP.NET byla povolena WCF.</span><span class="sxs-lookup"><span data-stu-id="34087-120">In the .NET Framework 3.0, the WCF `HttpModule` was installed in the root Web.config file such that every ASP.NET application was WCF enabled.</span></span> <span data-ttu-id="34087-121">To může ovlivnit výkon, takže můžete odebrat `ServiceModel` pro soubor Web.config, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="34087-121">This might affect performance, so you can remove `ServiceModel` for the Web.config file as shown in the following example.</span></span>  
  
```xml  
<httpModules>  
    <remove name="ServiceModel" />  
<httpModules/>  
```  
  
## <a name="see-also"></a><span data-ttu-id="34087-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="34087-122">See also</span></span>

- [<span data-ttu-id="34087-123">Postupy: Konfigurace služby WCF pro spolupráci s klienty webové služby ASP.NET</span><span class="sxs-lookup"><span data-stu-id="34087-123">How to: Configure WCF Service to Interoperate with ASP.NET Web Service Clients</span></span>](../../../../docs/framework/wcf/feature-details/config-wcf-service-with-aspnet-web-service.md)
