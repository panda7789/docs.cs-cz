---
title: "Interoperabilita s webovými službami ASP.NET"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 622422f8-6651-442f-b8be-e654a4aabcac
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ef174f457114003e5b2783b50040424d9a96945c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="interoperability-with-aspnet-web-services"></a><span data-ttu-id="1cf3e-102">Interoperabilita s webovými službami ASP.NET</span><span class="sxs-lookup"><span data-stu-id="1cf3e-102">Interoperability with ASP.NET Web Services</span></span>
<span data-ttu-id="1cf3e-103">Vzájemná funkční spolupráce mezi [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] webové služby a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] webové služby lze dosáhnout zajistíte, že služby implementovaná pomocí obou technologií odpovídají WS-I Basic Profile 1.1 specifikace.</span><span class="sxs-lookup"><span data-stu-id="1cf3e-103">Interoperability between [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Web services and [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] Web services can be achieved by ensuring that services implemented using both technologies conform to the WS-I Basic Profile 1.1 specification.</span></span> [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]<span data-ttu-id="1cf3e-104">Webové služby, které odpovídají WS-I Basic Profile 1.1 se vzájemná spolupráce s [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klienty pomocí [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] vazby poskytované systémem <xref:System.ServiceModel.BasicHttpBinding>.</span><span class="sxs-lookup"><span data-stu-id="1cf3e-104"> Web services that conform to WS-I Basic Profile 1.1 are interoperable with [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] clients by using [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] system-provided binding, <xref:System.ServiceModel.BasicHttpBinding>.</span></span>  
  
 <span data-ttu-id="1cf3e-105">Použití [!INCLUDE[vstecasplong](../../../../includes/vstecasplong-md.md)] možnost přidání <xref:System.Web.Services.WebService> a <xref:System.Web.Services.WebMethodAttribute> atributy rozhraní, nikoli třída a zápis třídu pro implementaci rozhraní, jak je znázorněno v následujícím ukázkovém kódu.</span><span class="sxs-lookup"><span data-stu-id="1cf3e-105">Use [!INCLUDE[vstecasplong](../../../../includes/vstecasplong-md.md)] option of adding the <xref:System.Web.Services.WebService> and <xref:System.Web.Services.WebMethodAttribute> attributes to an interface rather than to a class, and writing a class to implement the interface, as shown in the following sample code.</span></span>  
  
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
  
 <span data-ttu-id="1cf3e-106">Tato možnost je upřednostňované, protože rozhraní s <xref:System.Web.Services.WebService> atribut se považuje za kontraktu pro operace prováděné na službu, kterou lze opětovně použít s různými třídami, které může implementovat stejné kontraktu různými způsoby.</span><span class="sxs-lookup"><span data-stu-id="1cf3e-106">Using this option is preferred, because the interface with the <xref:System.Web.Services.WebService> attribute constitutes a contract for the operations performed by the service that can be reused with various classes that might implement that same contract in different ways.</span></span>  
  
 <span data-ttu-id="1cf3e-107">Nepoužívejte <xref:System.Web.Services.Protocols.SoapDocumentServiceAttribute> atribut tak, aby měl zprávy směrované na metody založené na plně kvalifikovaný název elementu těla protokolu SOAP zprávy místo `SOAPAction` hlavičky protokolu HTTP.</span><span class="sxs-lookup"><span data-stu-id="1cf3e-107">Avoid using the <xref:System.Web.Services.Protocols.SoapDocumentServiceAttribute> attribute to have messages routed to methods based on the fully-qualified name of the body element of the SOAP message rather than the `SOAPAction` HTTP header.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="1cf3e-108">používá `SOAPAction` hlavičky protokolu HTTP pro směrování zpráv.</span><span class="sxs-lookup"><span data-stu-id="1cf3e-108"> uses the `SOAPAction` HTTP header for routing messages.</span></span>  
  
 <span data-ttu-id="1cf3e-109">Zadaný kód XML, do kterého <xref:System.Xml.Serialization.XmlSerializer> serializuje typu ve výchozím nastavení je sémanticky stejný jako soubor XML, do kterého <xref:System.Runtime.Serialization.DataContractSerializer> serializuje typu zadaný obor názvů pro soubor XML byl explicitně definován.</span><span class="sxs-lookup"><span data-stu-id="1cf3e-109">The XML into which <xref:System.Xml.Serialization.XmlSerializer> serializes a type by default is semantically identical to the XML into which the <xref:System.Runtime.Serialization.DataContractSerializer> serializes a type, provided the namespace for the XML is explicitly defined.</span></span> <span data-ttu-id="1cf3e-110">Při definování datový typ pro použití s [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]webové služby v očekávání přijetí [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], postupujte takto:</span><span class="sxs-lookup"><span data-stu-id="1cf3e-110">When defining a data type for use with [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]Web services in anticipation of adopting [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], do the following:</span></span>  
  
-   <span data-ttu-id="1cf3e-111">Definování typu pomocí třídy rozhraní .NET Framework, nikoli schématu XML.</span><span class="sxs-lookup"><span data-stu-id="1cf3e-111">Define the type using .NET Framework classes rather than XML Schema.</span></span>  
  
-   <span data-ttu-id="1cf3e-112">Přidat pouze <xref:System.SerializableAttribute> a <xref:System.Xml.Serialization.XmlRootAttribute> k třídě, pomocí k tomu explicitně zadat obor názvů pro typ.</span><span class="sxs-lookup"><span data-stu-id="1cf3e-112">Add only the <xref:System.SerializableAttribute> and the <xref:System.Xml.Serialization.XmlRootAttribute> to the class, using the latter to explicitly define the namespace for the type.</span></span> <span data-ttu-id="1cf3e-113">Nepřidávejte další atributy z <xref:System.Xml.Serialization> obor názvů řídit, jak se přeložit na XML třídy rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="1cf3e-113">Do not add additional attributes from the <xref:System.Xml.Serialization> namespace to control how the .NET Framework class is to be translated into XML.</span></span>  
  
-   <span data-ttu-id="1cf3e-114">Přijetím tuto metodu, musí mít možnost později provádět třídy rozhraní .NET do kontrakty dat s přidáním systému <xref:System.Runtime.Serialization.DataContractAttribute> a <xref:System.Runtime.Serialization.DataMemberAttribute> beze změny výrazně XML, do které se serializují třídy pro přenos.</span><span class="sxs-lookup"><span data-stu-id="1cf3e-114">By adopting this approach, you should be able to later make the .NET classes into data contracts with the addition of the <xref:System.Runtime.Serialization.DataContractAttribute> and <xref:System.Runtime.Serialization.DataMemberAttribute> without significantly altering the XML into which the classes are serialized for transmission.</span></span> <span data-ttu-id="1cf3e-115">Typy používané ve zprávách podle [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] webové služby může zpracovat jako kontrakty dat podle [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplikace, mimo jiné, je lepší výkon v [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplikace.</span><span class="sxs-lookup"><span data-stu-id="1cf3e-115">The types used in messages by [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Web services can be processed as data contracts by [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] applications, yielding, among other benefits, better performance in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] applications.</span></span>  
  
 <span data-ttu-id="1cf3e-116">Nepoužívejte možnosti ověřování zadané Internetové informační služby (IIS).</span><span class="sxs-lookup"><span data-stu-id="1cf3e-116">Avoid using the authentication options provided by Internet Information Services (IIS).</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="1cf3e-117">klienti nepodporují je.</span><span class="sxs-lookup"><span data-stu-id="1cf3e-117"> clients do not support them.</span></span> <span data-ttu-id="1cf3e-118">Pokud služba musí být zabezpečená, použijte možnosti poskytované [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], protože tyto možnosti jsou robustní a je založený na standardních protokolů.</span><span class="sxs-lookup"><span data-stu-id="1cf3e-118">If a service must be secured, use the options provided by [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], because these options are robust and are based on standard protocols.</span></span>  
  
## <a name="performance-impact-caused-by-loading-the-servicemodel-httpmodule"></a><span data-ttu-id="1cf3e-119">Dopad na výkon způsobené načítání modulu HTTP ServiceModel</span><span class="sxs-lookup"><span data-stu-id="1cf3e-119">Performance impact caused by loading the ServiceModel HttpModule</span></span>  
 <span data-ttu-id="1cf3e-120">V rozhraní .NET Framework 3.0, WCF `HttpModule` byl nainstalován v kořenovém souboru Web.config, tak, aby každá aplikace ASP.NET byl WCF povolena.</span><span class="sxs-lookup"><span data-stu-id="1cf3e-120">In the .NET Framework 3.0, the WCF `HttpModule` was installed in the root Web.config file such that every ASP.NET application was WCF enabled.</span></span> <span data-ttu-id="1cf3e-121">To může ovlivnit výkon, takže můžete odebrat `ServiceModel` pro soubor Web.config, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="1cf3e-121">This might affect performance, so you can remove `ServiceModel` for the Web.config file as shown in the following example.</span></span>  
  
```xml  
<httpModules>  
    <remove name="ServiceModel" />  
<httpModules/>  
```  
  
## <a name="see-also"></a><span data-ttu-id="1cf3e-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="1cf3e-122">See Also</span></span>  
 [<span data-ttu-id="1cf3e-123">Postupy: Konfigurace služby WCF pro spolupráci s klienty webové služby ASP.NET</span><span class="sxs-lookup"><span data-stu-id="1cf3e-123">How to: Configure WCF Service to Interoperate with ASP.NET Web Service Clients</span></span>](../../../../docs/framework/wcf/feature-details/config-wcf-service-with-aspnet-web-service.md)
