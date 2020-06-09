---
title: 'Očekávání přechodu na Windows Communication Foundation: usnadnění budoucí integrace'
ms.date: 03/30/2017
ms.assetid: 3028bba8-6355-4ee0-9ecd-c56e614cb474
ms.openlocfilehash: 6392194b3124c999031123225dcc28c8de6171e9
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84576522"
---
# <a name="anticipating-adopting-the-windows-communication-foundation-easing-future-integration"></a><span data-ttu-id="f2e3c-102">Očekávání přechodu na Windows Communication Foundation: usnadnění budoucí integrace</span><span class="sxs-lookup"><span data-stu-id="f2e3c-102">Anticipating Adopting the Windows Communication Foundation: Easing Future Integration</span></span>
<span data-ttu-id="f2e3c-103">Pokud používáte ASP.NET ještě dnes a předpokládáte pomocí WCF v budoucnu, toto téma poskytuje pokyny, abyste zajistili, že budou nové webové služby ASP.NET fungovat dobře společně s aplikacemi WCF.</span><span class="sxs-lookup"><span data-stu-id="f2e3c-103">If you use ASP.NET today, and anticipate using WCF in the future, this topic provides guidance to ensure that new ASP.NET Web services will work well together with WCF applications.</span></span>  
  
## <a name="general-recommendations"></a><span data-ttu-id="f2e3c-104">Obecná doporučení</span><span class="sxs-lookup"><span data-stu-id="f2e3c-104">General Recommendations</span></span>  
 <span data-ttu-id="f2e3c-105">Pro všechny nové služby se ASP.NET 2,0.</span><span class="sxs-lookup"><span data-stu-id="f2e3c-105">Adopt ASP.NET 2.0 for any new services.</span></span> <span data-ttu-id="f2e3c-106">Tím zajistíte přístup k vylepšením a vylepšením nové verze.</span><span class="sxs-lookup"><span data-stu-id="f2e3c-106">Doing so will provide access to the improvements and enhancements of the new version.</span></span> <span data-ttu-id="f2e3c-107">Zároveň ale umožní využít komponenty ASP.NET 2,0 společně s komponentami WCF ve stejné aplikaci.</span><span class="sxs-lookup"><span data-stu-id="f2e3c-107">However, it will also allow for the possibility of using ASP.NET 2.0 components together with WCF components in the same application.</span></span>  
  
## <a name="protocols"></a><span data-ttu-id="f2e3c-108">Protokoly</span><span class="sxs-lookup"><span data-stu-id="f2e3c-108">Protocols</span></span>  
 <span data-ttu-id="f2e3c-109">Použijte nové zařízení ASP.NET 2.0 k ověření shody s profilem WS-I Basic 1,1:</span><span class="sxs-lookup"><span data-stu-id="f2e3c-109">Use ASP.NET 2.0’s new facility for validating conformity to the WS-I Basic Profile 1.1:</span></span>  
  
```csharp  
[WebService(Namespace = "http://tempuri.org/")]  
[WebServiceBinding(  
     ConformsTo = WsiProfiles.BasicProfile1_1,  
     EmitConformanceClaims=true)]  
public interface IEcho  
```  
  
 <span data-ttu-id="f2e3c-110">Webové služby ASP.NET, které odpovídají profilu WS-I Basic Profile 1,1, budou spolupracovat s klienty WCF pomocí předdefinované vazby WCF <xref:System.ServiceModel.BasicHttpBinding> .</span><span class="sxs-lookup"><span data-stu-id="f2e3c-110">ASP.NET Web services that conform to WS-I Basic Profile 1.1 will be interoperable with WCF clients by using WCF predefined binding, <xref:System.ServiceModel.BasicHttpBinding>.</span></span>  
  
## <a name="service-development"></a><span data-ttu-id="f2e3c-111">Vývoj služeb</span><span class="sxs-lookup"><span data-stu-id="f2e3c-111">Service Development</span></span>  
 <span data-ttu-id="f2e3c-112">Nepoužívejte <xref:System.Web.Services.Protocols.SoapDocumentServiceAttribute> atribut ke směrování zpráv na metody založené na plně kvalifikovaném názvu prvku těla zprávy SOAP, nikoli v hlavičce SOAPACTION http.</span><span class="sxs-lookup"><span data-stu-id="f2e3c-112">Avoid using the <xref:System.Web.Services.Protocols.SoapDocumentServiceAttribute> attribute to have messages routed to methods based on the fully-qualified name of the body element of the SOAP message rather than the SOAPAction HTTP header.</span></span> <span data-ttu-id="f2e3c-113">WCF používá pro směrování zpráv hlavičku HTTP SOAPAction.</span><span class="sxs-lookup"><span data-stu-id="f2e3c-113">WCF uses the SOAPAction HTTP header for routing messages.</span></span>  
  
## <a name="data-representation"></a><span data-ttu-id="f2e3c-114">Reprezentace dat</span><span class="sxs-lookup"><span data-stu-id="f2e3c-114">Data Representation</span></span>  
 <span data-ttu-id="f2e3c-115">KÓD XML, do kterého <xref:System.Xml.Serialization.XmlSerializer> je ve výchozím nastavení serializován typ, je sémanticky totožný s XML, do kterého je <xref:System.Runtime.Serialization.DataContractSerializer> serializován typ, za předpokladu, že obor názvů XML je explicitně definován.</span><span class="sxs-lookup"><span data-stu-id="f2e3c-115">The XML into which <xref:System.Xml.Serialization.XmlSerializer> serializes a type by default is semantically identical to the XML into which the <xref:System.Runtime.Serialization.DataContractSerializer> serializes a type, provided the namespace for the XML is explicitly defined.</span></span> <span data-ttu-id="f2e3c-116">Při definování datového typu pro použití s webovými službami ASP.NET při předvídání budoucího přijetí WCF v budoucnu udělejte toto:</span><span class="sxs-lookup"><span data-stu-id="f2e3c-116">When defining a data type for use with ASP.NET Web services in anticipation of adopting WCF in the future, do the following:</span></span>  
  
1. <span data-ttu-id="f2e3c-117">Definujte typ pomocí .NET Framework třídy místo schématu XML.</span><span class="sxs-lookup"><span data-stu-id="f2e3c-117">Define the type using .NET Framework classes rather than XML Schema.</span></span>  
  
2. <span data-ttu-id="f2e3c-118">Přidejte pouze <xref:System.SerializableAttribute> <xref:System.Xml.Serialization.XmlRootAttribute> třídu a ke třídě pomocí druhé k explicitnímu definování oboru názvů pro daný typ.</span><span class="sxs-lookup"><span data-stu-id="f2e3c-118">Add only the <xref:System.SerializableAttribute> and the <xref:System.Xml.Serialization.XmlRootAttribute> to the class, using the latter to explicitly define the namespace for the type.</span></span> <span data-ttu-id="f2e3c-119">Neprovádějte přidávání dalších atributů z <xref:System.Xml.Serialization> oboru názvů, abyste mohli řídit, jak se má třída .NET Framework přeložit do XML.</span><span class="sxs-lookup"><span data-stu-id="f2e3c-119">Do no add additional attributes from the <xref:System.Xml.Serialization> namespace to control how the .NET Framework class is to be translated into XML.</span></span>  
  
 <span data-ttu-id="f2e3c-120">Přijetím tohoto přístupu byste měli být schopni později převést třídy .NET na kontrakty dat s přidáním <xref:System.Runtime.Serialization.DataContractAttribute> a <xref:System.Runtime.Serialization.DataMemberAttribute> bez významně měnit kód XML, do kterého jsou třídy serializovány pro přenos.</span><span class="sxs-lookup"><span data-stu-id="f2e3c-120">By adopting this approach, you should be able to later make the .NET classes into data contracts with the addition of the <xref:System.Runtime.Serialization.DataContractAttribute> and <xref:System.Runtime.Serialization.DataMemberAttribute> without significantly altering the XML into which the classes are serialized for transmission.</span></span> <span data-ttu-id="f2e3c-121">Typy používané ve zprávách podle ASP.NET webové služby budou možné zpracovávat jako kontrakty dat aplikacemi WCF, a to mimo jiné výhody a lepší výkon v aplikacích WCF.</span><span class="sxs-lookup"><span data-stu-id="f2e3c-121">The types used in messages by ASP.NET Web services will be able to be processed as data contracts by WCF applications, yielding, amongst other benefits, better performance in WCF applications.</span></span>  
  
## <a name="security"></a><span data-ttu-id="f2e3c-122">Zabezpečení</span><span class="sxs-lookup"><span data-stu-id="f2e3c-122">Security</span></span>  
 <span data-ttu-id="f2e3c-123">Nepoužívejte možnosti ověřování poskytované Internetová informační služba (IIS).</span><span class="sxs-lookup"><span data-stu-id="f2e3c-123">Avoid using the authentication options provided by Internet Information Services (IIS).</span></span> <span data-ttu-id="f2e3c-124">Klienti WCF je nepodporují.</span><span class="sxs-lookup"><span data-stu-id="f2e3c-124">WCF clients do not support them.</span></span> <span data-ttu-id="f2e3c-125">Pokud musí být služba zabezpečená, použijte možnosti poskytované službou WCF, protože tyto možnosti jsou bohatší a jsou založené na standardních protokolech.</span><span class="sxs-lookup"><span data-stu-id="f2e3c-125">If a service needs to be secured, use the options provided by WCF, because these options are richer and are based on standard protocols.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2e3c-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="f2e3c-126">See also</span></span>

- [<span data-ttu-id="f2e3c-127">Očekávání přechodu na Windows Communication Foundation: Usnadnění budoucí migrace</span><span class="sxs-lookup"><span data-stu-id="f2e3c-127">Anticipating Adopting the Windows Communication Foundation: Easing Future Migration</span></span>](anticipating-adopting-wcf-migration.md)
