---
title: "Očekávání přechodu na Windows Communication Foundation: usnadnění budoucí integrace"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3028bba8-6355-4ee0-9ecd-c56e614cb474
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ccf6e5363da872d3902c12713bd19f5820370428
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="anticipating-adopting-the-windows-communication-foundation-easing-future-integration"></a><span data-ttu-id="ed0b0-102">Očekávání přechodu na Windows Communication Foundation: usnadnění budoucí integrace</span><span class="sxs-lookup"><span data-stu-id="ed0b0-102">Anticipating Adopting the Windows Communication Foundation: Easing Future Integration</span></span>
<span data-ttu-id="ed0b0-103">Pokud jste ještě dnes pomocí technologie ASP.NET a předvídat pomocí [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] v budoucnu, toto téma obsahuje pokyny k zajištění, že nové rozhraní ASP.NET Web services bude fungovat dobře společně s [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplikace.</span><span class="sxs-lookup"><span data-stu-id="ed0b0-103">If you use ASP.NET today, and anticipate using [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] in the future, this topic provides guidance to ensure that new ASP.NET Web services will work well together with [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] applications.</span></span>  
  
## <a name="general-recommendations"></a><span data-ttu-id="ed0b0-104">Obecná doporučení</span><span class="sxs-lookup"><span data-stu-id="ed0b0-104">General Recommendations</span></span>  
 <span data-ttu-id="ed0b0-105">Přijmout technologii ASP.NET 2.0 pro všechny nové služby.</span><span class="sxs-lookup"><span data-stu-id="ed0b0-105">Adopt ASP.NET 2.0 for any new services.</span></span> <span data-ttu-id="ed0b0-106">Díky tomu bude poskytovat přístup k vylepšení a vylepšení nové verze.</span><span class="sxs-lookup"><span data-stu-id="ed0b0-106">Doing so will provide access to the improvements and enhancements of the new version.</span></span> <span data-ttu-id="ed0b0-107">Však bude taky povolit možnost pomocí technologie ASP.NET 2.0 součásti společně s [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] součásti ve stejné aplikaci.</span><span class="sxs-lookup"><span data-stu-id="ed0b0-107">However, it will also allow for the possibility of using ASP.NET 2.0 components together with [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] components in the same application.</span></span>  
  
## <a name="protocols"></a><span data-ttu-id="ed0b0-108">protokoly</span><span class="sxs-lookup"><span data-stu-id="ed0b0-108">Protocols</span></span>  
 <span data-ttu-id="ed0b0-109">Použít technologii ASP.NET 2.0 nové zařízení pro ověřování shody pro služby WS-I Basic Profile 1.1:</span><span class="sxs-lookup"><span data-stu-id="ed0b0-109">Use ASP.NET 2.0’s new facility for validating conformity to the WS-I Basic Profile 1.1:</span></span>  
  
```  
[WebService(Namespace = "http://tempuri.org/")]  
[WebServiceBinding(  
     ConformsTo = WsiProfiles.BasicProfile1_1,  
     EmitConformanceClaims=true)]  
public interface IEcho  
```  
  
 <span data-ttu-id="ed0b0-110">ASP.NET – webové služby, které v souladu s WS-I Basic Profile 1.1 bude vzájemná spolupráce s [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klienty pomocí [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] předdefinované vazby, <xref:System.ServiceModel.BasicHttpBinding>.</span><span class="sxs-lookup"><span data-stu-id="ed0b0-110">ASP.NET Web services that conform to WS-I Basic Profile 1.1 will be interoperable with [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] clients by using [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] predefined binding, <xref:System.ServiceModel.BasicHttpBinding>.</span></span>  
  
## <a name="service-development"></a><span data-ttu-id="ed0b0-111">Vývoj pro služby</span><span class="sxs-lookup"><span data-stu-id="ed0b0-111">Service Development</span></span>  
 <span data-ttu-id="ed0b0-112">Nepoužívejte <xref:System.Web.Services.Protocols.SoapDocumentServiceAttribute> atribut tak, aby měl zprávy směrované na metody založené na plně kvalifikovaný název prvku body zprávu protokolu SOAP a ne záhlaví SOAPAction HTTP.</span><span class="sxs-lookup"><span data-stu-id="ed0b0-112">Avoid using the <xref:System.Web.Services.Protocols.SoapDocumentServiceAttribute> attribute to have messages routed to methods based on the fully-qualified name of the body element of the SOAP message rather than the SOAPAction HTTP header.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="ed0b0-113">záhlaví SOAPAction HTTP používá pro směrování zpráv.</span><span class="sxs-lookup"><span data-stu-id="ed0b0-113"> uses the SOAPAction HTTP header for routing messages.</span></span>  
  
## <a name="data-representation"></a><span data-ttu-id="ed0b0-114">Reprezentace dat</span><span class="sxs-lookup"><span data-stu-id="ed0b0-114">Data Representation</span></span>  
 <span data-ttu-id="ed0b0-115">Zadaný kód XML, do kterého <xref:System.Xml.Serialization.XmlSerializer> serializuje typu ve výchozím nastavení je sémanticky stejný jako soubor XML, do kterého <xref:System.Runtime.Serialization.DataContractSerializer> serializuje typu zadaný obor názvů pro soubor XML byl explicitně definován.</span><span class="sxs-lookup"><span data-stu-id="ed0b0-115">The XML into which <xref:System.Xml.Serialization.XmlSerializer> serializes a type by default is semantically identical to the XML into which the <xref:System.Runtime.Serialization.DataContractSerializer> serializes a type, provided the namespace for the XML is explicitly defined.</span></span> <span data-ttu-id="ed0b0-116">Při definování datový typ pro použití s rozhraním ASP.NET Web services v očekávání přijetí [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] v budoucnu, postupujte takto:</span><span class="sxs-lookup"><span data-stu-id="ed0b0-116">When defining a data type for use with ASP.NET Web services in anticipation of adopting [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] in the future, do the following:</span></span>  
  
1.  <span data-ttu-id="ed0b0-117">Definování typu pomocí třídy rozhraní .NET Framework, nikoli schématu XML.</span><span class="sxs-lookup"><span data-stu-id="ed0b0-117">Define the type using .NET Framework classes rather than XML Schema.</span></span>  
  
2.  <span data-ttu-id="ed0b0-118">Přidat pouze <xref:System.SerializableAttribute> a <xref:System.Xml.Serialization.XmlRootAttribute> k třídě, pomocí k tomu explicitně zadat obor názvů pro typ.</span><span class="sxs-lookup"><span data-stu-id="ed0b0-118">Add only the <xref:System.SerializableAttribute> and the <xref:System.Xml.Serialization.XmlRootAttribute> to the class, using the latter to explicitly define the namespace for the type.</span></span> <span data-ttu-id="ed0b0-119">Provést žádné přidat další atributy z <xref:System.Xml.Serialization> obor názvů řídit, jak se přeložit na XML třídy rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ed0b0-119">Do no add additional attributes from the <xref:System.Xml.Serialization> namespace to control how the .NET Framework class is to be translated into XML.</span></span>  
  
 <span data-ttu-id="ed0b0-120">Přijetím tuto metodu, musí mít možnost později provádět třídy rozhraní .NET do kontrakty dat s přidáním systému <xref:System.Runtime.Serialization.DataContractAttribute> a <xref:System.Runtime.Serialization.DataMemberAttribute> beze změny výrazně XML, do které se serializují třídy pro přenos.</span><span class="sxs-lookup"><span data-stu-id="ed0b0-120">By adopting this approach, you should be able to later make the .NET classes into data contracts with the addition of the <xref:System.Runtime.Serialization.DataContractAttribute> and <xref:System.Runtime.Serialization.DataMemberAttribute> without significantly altering the XML into which the classes are serialized for transmission.</span></span> <span data-ttu-id="ed0b0-121">Typy použité ve zprávách webových služeb ASP.NET, bude moct zpracovat jako kontrakty dat podle [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplikace, je mezi další výhody lepší výkon v [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplikace.</span><span class="sxs-lookup"><span data-stu-id="ed0b0-121">The types used in messages by ASP.NET Web services will be able to be processed as data contracts by [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] applications, yielding, amongst other benefits, better performance in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] applications.</span></span>  
  
## <a name="security"></a><span data-ttu-id="ed0b0-122">Zabezpečení</span><span class="sxs-lookup"><span data-stu-id="ed0b0-122">Security</span></span>  
 <span data-ttu-id="ed0b0-123">Nepoužívejte možnosti ověřování zadané Internetové informační služby (IIS).</span><span class="sxs-lookup"><span data-stu-id="ed0b0-123">Avoid using the authentication options provided by Internet Information Services (IIS).</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="ed0b0-124">klienti nepodporují je.</span><span class="sxs-lookup"><span data-stu-id="ed0b0-124"> clients do not support them.</span></span> <span data-ttu-id="ed0b0-125">Pokud služba musí být zabezpečené, pomocí možnosti poskytované [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], protože tyto možnosti jsou bohatší a je založený na standardních protokolů.</span><span class="sxs-lookup"><span data-stu-id="ed0b0-125">If a service needs to be secured, use the options provided by [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], because these options are richer and are based on standard protocols.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed0b0-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="ed0b0-126">See Also</span></span>  
 [<span data-ttu-id="ed0b0-127">Očekávání přechodu služby Windows Communication Foundation: usnadnění budoucí migrace</span><span class="sxs-lookup"><span data-stu-id="ed0b0-127">Anticipating Adopting the Windows Communication Foundation: Easing Future Migration</span></span>](../../../../docs/framework/wcf/feature-details/anticipating-adopting-wcf-migration.md)
