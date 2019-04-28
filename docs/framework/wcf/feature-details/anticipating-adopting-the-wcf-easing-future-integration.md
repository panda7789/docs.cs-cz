---
title: 'Očekávání přechodu na Windows Communication Foundation: usnadnění budoucí integrace'
ms.date: 03/30/2017
ms.assetid: 3028bba8-6355-4ee0-9ecd-c56e614cb474
ms.openlocfilehash: c6e749c32947a4159d6bfd56c4d30a06f6ef0b7f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61650554"
---
# <a name="anticipating-adopting-the-windows-communication-foundation-easing-future-integration"></a><span data-ttu-id="bb9da-102">Očekávání přechodu na Windows Communication Foundation: usnadnění budoucí integrace</span><span class="sxs-lookup"><span data-stu-id="bb9da-102">Anticipating Adopting the Windows Communication Foundation: Easing Future Integration</span></span>
<span data-ttu-id="bb9da-103">Pokud používáte ASP.NET a předvídat pomocí technologie WCF v budoucnu, toto téma obsahuje pokyny pro zajištění, že nové technologie ASP.NET webové služby bude fungovat dobře spolu s aplikací služby WCF.</span><span class="sxs-lookup"><span data-stu-id="bb9da-103">If you use ASP.NET today, and anticipate using WCF in the future, this topic provides guidance to ensure that new ASP.NET Web services will work well together with WCF applications.</span></span>  
  
## <a name="general-recommendations"></a><span data-ttu-id="bb9da-104">Obecná doporučení</span><span class="sxs-lookup"><span data-stu-id="bb9da-104">General Recommendations</span></span>  
 <span data-ttu-id="bb9da-105">Osvojte si technologii ASP.NET 2.0 pro všechny nové služby.</span><span class="sxs-lookup"><span data-stu-id="bb9da-105">Adopt ASP.NET 2.0 for any new services.</span></span> <span data-ttu-id="bb9da-106">To zajistí přístup k vylepšení a rozšíření na novou verzi.</span><span class="sxs-lookup"><span data-stu-id="bb9da-106">Doing so will provide access to the improvements and enhancements of the new version.</span></span> <span data-ttu-id="bb9da-107">Ale vám také umožní možnost použití komponent v technologii ASP.NET 2.0 společně s WCF komponenty ve stejné aplikaci.</span><span class="sxs-lookup"><span data-stu-id="bb9da-107">However, it will also allow for the possibility of using ASP.NET 2.0 components together with WCF components in the same application.</span></span>  
  
## <a name="protocols"></a><span data-ttu-id="bb9da-108">Protokoly</span><span class="sxs-lookup"><span data-stu-id="bb9da-108">Protocols</span></span>  
 <span data-ttu-id="bb9da-109">Použití nového zařízení technologie ASP.NET 2.0 pro ověřování shody WS-I Basic Profile 1.1:</span><span class="sxs-lookup"><span data-stu-id="bb9da-109">Use ASP.NET 2.0’s new facility for validating conformity to the WS-I Basic Profile 1.1:</span></span>  
  
```csharp  
[WebService(Namespace = "http://tempuri.org/")]  
[WebServiceBinding(  
     ConformsTo = WsiProfiles.BasicProfile1_1,  
     EmitConformanceClaims=true)]  
public interface IEcho  
```  
  
 <span data-ttu-id="bb9da-110">Webových služeb ASP.NET, které odpovídají WS-I Basic Profile 1.1 pomocí WCF předdefinovaných vazeb, bude spolupracují se službou WCF klienti <xref:System.ServiceModel.BasicHttpBinding>.</span><span class="sxs-lookup"><span data-stu-id="bb9da-110">ASP.NET Web services that conform to WS-I Basic Profile 1.1 will be interoperable with WCF clients by using WCF predefined binding, <xref:System.ServiceModel.BasicHttpBinding>.</span></span>  
  
## <a name="service-development"></a><span data-ttu-id="bb9da-111">Vývoj služby</span><span class="sxs-lookup"><span data-stu-id="bb9da-111">Service Development</span></span>  
 <span data-ttu-id="bb9da-112">Vyhněte se použití <xref:System.Web.Services.Protocols.SoapDocumentServiceAttribute> atribut zprávy směruje do metody podle plně kvalifikovaný název elementu těla zprávy protokolu SOAP a ne záhlaví SOAPAction HTTP.</span><span class="sxs-lookup"><span data-stu-id="bb9da-112">Avoid using the <xref:System.Web.Services.Protocols.SoapDocumentServiceAttribute> attribute to have messages routed to methods based on the fully-qualified name of the body element of the SOAP message rather than the SOAPAction HTTP header.</span></span> <span data-ttu-id="bb9da-113">Záhlaví SOAPAction HTTP WCF používá pro směrování zpráv.</span><span class="sxs-lookup"><span data-stu-id="bb9da-113">WCF uses the SOAPAction HTTP header for routing messages.</span></span>  
  
## <a name="data-representation"></a><span data-ttu-id="bb9da-114">Reprezentace dat</span><span class="sxs-lookup"><span data-stu-id="bb9da-114">Data Representation</span></span>  
 <span data-ttu-id="bb9da-115">XML, do kterého <xref:System.Xml.Serialization.XmlSerializer> serializuje typu ve výchozím nastavení je sémanticky shodná s XML, do kterého <xref:System.Runtime.Serialization.DataContractSerializer> serializuje typu podle oboru názvů XML není výslovně uveden.</span><span class="sxs-lookup"><span data-stu-id="bb9da-115">The XML into which <xref:System.Xml.Serialization.XmlSerializer> serializes a type by default is semantically identical to the XML into which the <xref:System.Runtime.Serialization.DataContractSerializer> serializes a type, provided the namespace for the XML is explicitly defined.</span></span> <span data-ttu-id="bb9da-116">Po definování typu dat pro použití s webovými službami ASP.NET čekat na případná přijetí WCF v budoucnu, postupujte takto:</span><span class="sxs-lookup"><span data-stu-id="bb9da-116">When defining a data type for use with ASP.NET Web services in anticipation of adopting WCF in the future, do the following:</span></span>  
  
1. <span data-ttu-id="bb9da-117">Definování typů pomocí tříd rozhraní .NET Framework než schématu XML.</span><span class="sxs-lookup"><span data-stu-id="bb9da-117">Define the type using .NET Framework classes rather than XML Schema.</span></span>  
  
2. <span data-ttu-id="bb9da-118">Přidat pouze <xref:System.SerializableAttribute> a <xref:System.Xml.Serialization.XmlRootAttribute> na třídu pomocí odkazující k explicitnímu definování oboru názvů typu.</span><span class="sxs-lookup"><span data-stu-id="bb9da-118">Add only the <xref:System.SerializableAttribute> and the <xref:System.Xml.Serialization.XmlRootAttribute> to the class, using the latter to explicitly define the namespace for the type.</span></span> <span data-ttu-id="bb9da-119">Provést žádné přidat další atributy z <xref:System.Xml.Serialization> obor názvů řídit, jak je třída rozhraní .NET Framework mají být převedeny do jazyka XML.</span><span class="sxs-lookup"><span data-stu-id="bb9da-119">Do no add additional attributes from the <xref:System.Xml.Serialization> namespace to control how the .NET Framework class is to be translated into XML.</span></span>  
  
 <span data-ttu-id="bb9da-120">Přijetím tohoto přístupu by měl být schopen později provést třídy rozhraní .NET v kontraktech dat a uveďte <xref:System.Runtime.Serialization.DataContractAttribute> a <xref:System.Runtime.Serialization.DataMemberAttribute> beze změny výrazně XML, do které třídy serializují pro přenos.</span><span class="sxs-lookup"><span data-stu-id="bb9da-120">By adopting this approach, you should be able to later make the .NET classes into data contracts with the addition of the <xref:System.Runtime.Serialization.DataContractAttribute> and <xref:System.Runtime.Serialization.DataMemberAttribute> without significantly altering the XML into which the classes are serialized for transmission.</span></span> <span data-ttu-id="bb9da-121">Typy použité ve zprávách webových služeb ASP.NET s budou moci zpracovat jako kontraktů dat aplikací služby WCF, což má za následek, mezi další výhody, lepší výkon v aplikacích WCF.</span><span class="sxs-lookup"><span data-stu-id="bb9da-121">The types used in messages by ASP.NET Web services will be able to be processed as data contracts by WCF applications, yielding, amongst other benefits, better performance in WCF applications.</span></span>  
  
## <a name="security"></a><span data-ttu-id="bb9da-122">Zabezpečení</span><span class="sxs-lookup"><span data-stu-id="bb9da-122">Security</span></span>  
 <span data-ttu-id="bb9da-123">Vyhněte se použití možnosti ověřování, které jsou k dispozici Internetové informační služby (IIS).</span><span class="sxs-lookup"><span data-stu-id="bb9da-123">Avoid using the authentication options provided by Internet Information Services (IIS).</span></span> <span data-ttu-id="bb9da-124">Klienti WCF je nepodporují.</span><span class="sxs-lookup"><span data-stu-id="bb9da-124">WCF clients do not support them.</span></span> <span data-ttu-id="bb9da-125">Pokud služba musí být zabezpečené, pomocí možností poskytnutých WCF, protože tyto možnosti jsou bohatší a jsou založeny na standardních protokolů.</span><span class="sxs-lookup"><span data-stu-id="bb9da-125">If a service needs to be secured, use the options provided by WCF, because these options are richer and are based on standard protocols.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb9da-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bb9da-126">See also</span></span>

- [<span data-ttu-id="bb9da-127">Očekávání přechodu na Windows Communication Foundation: Usnadnění budoucí migrace</span><span class="sxs-lookup"><span data-stu-id="bb9da-127">Anticipating Adopting the Windows Communication Foundation: Easing Future Migration</span></span>](../../../../docs/framework/wcf/feature-details/anticipating-adopting-wcf-migration.md)
