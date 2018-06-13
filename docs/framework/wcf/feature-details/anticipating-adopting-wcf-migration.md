---
title: 'Očekávání přechodu služby Windows Communication Foundation: usnadnění budoucí migrace'
ms.date: 03/30/2017
ms.assetid: f49664d9-e9e0-425c-a259-93f0a569d01b
ms.openlocfilehash: aeafc164d16d9dc60ad0b3012da292e9b0bb38b3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33490042"
---
# <a name="anticipating-adopting-the-windows-communication-foundation-easing-future-migration"></a><span data-ttu-id="cd6c5-102">Očekávání přechodu služby Windows Communication Foundation: usnadnění budoucí migrace</span><span class="sxs-lookup"><span data-stu-id="cd6c5-102">Anticipating Adopting the Windows Communication Foundation: Easing Future Migration</span></span>
<span data-ttu-id="cd6c5-103">Aby jednodušší budoucí migrace nové aplikace ASP.NET na WCF, postupujte podle předchozích doporučení a také následující doporučení.</span><span class="sxs-lookup"><span data-stu-id="cd6c5-103">To ensure an easier future migration of new ASP.NET applications to WCF, follow the preceding recommendations as well as the following recommendations.</span></span>  
  
## <a name="protocols"></a><span data-ttu-id="cd6c5-104">protokoly</span><span class="sxs-lookup"><span data-stu-id="cd6c5-104">Protocols</span></span>  
 <span data-ttu-id="cd6c5-105">Zakažte podporu technologie ASP.NET 2.0 pro SOAP 1.2:</span><span class="sxs-lookup"><span data-stu-id="cd6c5-105">Disable ASP.NET 2.0’s support for SOAP 1.2:</span></span>  
  
```xml  
<configuration>  
     <system.web>  
      <webServices >  
          <protocols>  
           <remove name="HttpSoap12"/>  
          </protocols>    
      </webServices>  
     </system.web>   
</configuration>  
```  
  
 <span data-ttu-id="cd6c5-106">Díky tomu se nedoporučuje, protože vyžaduje zprávy, které odpovídají různé protokoly, jako je SOAP 1.1 a SOAP 1.2 přejít pomocí různých koncových bodů WCF.</span><span class="sxs-lookup"><span data-stu-id="cd6c5-106">Doing so is advisable because WCF requires messages conforming to different protocols, like SOAP 1.1 and SOAP 1.2, to go by using different endpoints.</span></span> <span data-ttu-id="cd6c5-107">Pokud 2.0 ASP.NET – webové služby je nakonfigurován pro podporu protokolu SOAP 1.1 a SOAP 1.2, což je výchozí konfigurace a nemůže být migrovali předat dál na jeden koncový bod WCF na původní adrese, která by určitě být kompatibilní se všemi technologie ASP.NET existující klienti služby.</span><span class="sxs-lookup"><span data-stu-id="cd6c5-107">If an ASP.NET 2.0 Web service is configured to support both SOAP 1.1 and SOAP 1.2, which is the default configuration, then it cannot be migrated forward to a single WCF endpoint at the original address that would be certainly be compatible with all of the ASP.NET Web service’s existing clients.</span></span> <span data-ttu-id="cd6c5-108">Také výběr SOAP 1.2 místo 1.1 více značně omezí zákazníků služby.</span><span class="sxs-lookup"><span data-stu-id="cd6c5-108">Also choosing SOAP 1.2 instead of 1.1 will more severely restrict the clientele of the service.</span></span>  
  
## <a name="service-development"></a><span data-ttu-id="cd6c5-109">Vývoj pro služby</span><span class="sxs-lookup"><span data-stu-id="cd6c5-109">Service Development</span></span>  
 <span data-ttu-id="cd6c5-110">WCF umožňuje definování kontraktů služby s použitím <xref:System.ServiceModel.ServiceContractAttribute> na rozhraní nebo třídy.</span><span class="sxs-lookup"><span data-stu-id="cd6c5-110">WCF allows you to define service contracts by applying the <xref:System.ServiceModel.ServiceContractAttribute> either to interfaces or to classes.</span></span> <span data-ttu-id="cd6c5-111">Doporučujeme použít atribut rozhraní, nikoli třída, protože je to proto vytvoří definici kontraktu, která může být libovolný počet třídy různě implementována.</span><span class="sxs-lookup"><span data-stu-id="cd6c5-111">It is recommended to apply the attribute to an interface rather than to a class, because doing so creates a definition of a contract that can be variously implemented by any number of classes.</span></span> <span data-ttu-id="cd6c5-112">ASP.NET 2.0 podporuje možnost použít <xref:System.Web.Services.WebService> atribut rozhraní a také třídy.</span><span class="sxs-lookup"><span data-stu-id="cd6c5-112">ASP.NET 2.0 supports the option of applying the <xref:System.Web.Services.WebService> attribute to interfaces as well as classes.</span></span> <span data-ttu-id="cd6c5-113">Jak už bylo zmíněno, je však značit potíže v aplikaci ASP.NET 2.0, podle kterého parametr Namespace <xref:System.Web.Services.WebService> atribut nemá žádný vliv, pokud tento atribut se použije na rozhraní než třídu.</span><span class="sxs-lookup"><span data-stu-id="cd6c5-113">However, as mentioned already, there is a defect in ASP.NET 2.0, by which the Namespace parameter of the <xref:System.Web.Services.WebService> attribute has no effect when that attribute is applied to an interface rather than a class.</span></span> <span data-ttu-id="cd6c5-114">Vzhledem k tomu, že je většinou vhodné změnit obor názvů služby z výchozí hodnoty, http://tempuri.org, pomocí parametru Namespace <xref:System.Web.Services.WebService> atribut jeden by měly pokračovat definování webových služeb ASP.NET s použitím <xref:System.ServiceModel.ServiceContractAttribute> Atribut rozhraní nebo třídy.</span><span class="sxs-lookup"><span data-stu-id="cd6c5-114">Since it is generally advisable to modify the namespace of a service from the default value, http://tempuri.org, using the Namespace parameter of the <xref:System.Web.Services.WebService> attribute, one should continue defining ASP.NET Web Services by applying the <xref:System.ServiceModel.ServiceContractAttribute> attribute either to interfaces or to classes.</span></span>  
  
-   <span data-ttu-id="cd6c5-115">Mají jako málo kód jako možný metody, které jsou definovány těchto rozhraní.</span><span class="sxs-lookup"><span data-stu-id="cd6c5-115">Have as little code as possible in the methods by which those interfaces are defined.</span></span> <span data-ttu-id="cd6c5-116">Kliknul delegovat práci na jiné třídy.</span><span class="sxs-lookup"><span data-stu-id="cd6c5-116">Have them delegate their work to other classes.</span></span> <span data-ttu-id="cd6c5-117">Nové typy služby WCF pak rovněž delegovat práci podstatné do těchto tříd.</span><span class="sxs-lookup"><span data-stu-id="cd6c5-117">New WCF service types could then also delegate their substantive work to those classes.</span></span>  
  
-   <span data-ttu-id="cd6c5-118">Zadat explicitní názvy pro operace služby pomocí `MessageName` parametr <xref:System.Web.Services.WebMethodAttribute>.</span><span class="sxs-lookup"><span data-stu-id="cd6c5-118">Provide explicit names for the operations of a service using the `MessageName` parameter of the <xref:System.Web.Services.WebMethodAttribute>.</span></span>  
  
    ```  
    [WebMethod(MessageName="ExplicitName")]  
    string Echo(string input);  
    ```  
  
     <span data-ttu-id="cd6c5-119">Díky tomu je důležité, protože výchozí názvy pro operace v technologii ASP.NET se liší od výchozí názvy poskytl WCF.</span><span class="sxs-lookup"><span data-stu-id="cd6c5-119">Doing so is important, because the default names for operations in ASP.NET are different from the default names supplied by WCF.</span></span> <span data-ttu-id="cd6c5-120">Poskytnutím explicitní názvy neměli spoléhat na výchozí hodnoty.</span><span class="sxs-lookup"><span data-stu-id="cd6c5-120">By providing explicit names, you avoid relying on the default ones.</span></span>  
  
-   <span data-ttu-id="cd6c5-121">Neimplementuje operace ASP.NET webové služby s polymorfním metodami, protože WCF nepodporuje implementující operace s polymorfním metody.</span><span class="sxs-lookup"><span data-stu-id="cd6c5-121">Do not implement ASP.NET Web service operations with polymorphic methods, because WCF does not support implementing operations with polymorphic methods.</span></span>  
  
-   <span data-ttu-id="cd6c5-122">Použití <xref:System.Web.Services.Protocols.SoapDocumentMethodAttribute> zadat explicitní hodnoty pro hlavičky SOAPAction HTTP, pomocí které protokolu HTTP, budou směrovány požadavky na metody.</span><span class="sxs-lookup"><span data-stu-id="cd6c5-122">Use the <xref:System.Web.Services.Protocols.SoapDocumentMethodAttribute> to provide explicit values for the SOAPAction HTTP headers by which HTTP requests will be routed to methods.</span></span>  
  
    ```  
    [WebMethod]  
    [SoapDocumentMethod(RequestElementName="ExplicitAction")]  
    string Echo(string input);  
    ```  
  
     <span data-ttu-id="cd6c5-123">Tento postup trvá obejít museli spoléhat na výchozí hodnoty SOAPAction používané technologie ASP.NET a WCF se stejné.</span><span class="sxs-lookup"><span data-stu-id="cd6c5-123">Taking this approach will circumvent having to rely on the default SOAPAction values used by ASP.NET and WCF being the same.</span></span>  
  
-   <span data-ttu-id="cd6c5-124">Vyhněte se používá rozšíření SOAP.</span><span class="sxs-lookup"><span data-stu-id="cd6c5-124">Avoid using SOAP extensions.</span></span> <span data-ttu-id="cd6c5-125">Pokud rozšíření SOAP, pak určete, zda pro který je právě považována za účelem je funkce, která je již poskytované WCF.</span><span class="sxs-lookup"><span data-stu-id="cd6c5-125">If SOAP extensions are required, then determine whether the purpose for which they are being considered is a feature that is already provided by WCF.</span></span> <span data-ttu-id="cd6c5-126">Pokud tomu tak je skutečně, pak znovu volba není hned přijmout službu WCF.</span><span class="sxs-lookup"><span data-stu-id="cd6c5-126">If that is indeed the case, then reconsider the choice to not adopt WCF right away.</span></span>  
  
## <a name="state-management"></a><span data-ttu-id="cd6c5-127">Stav správy</span><span class="sxs-lookup"><span data-stu-id="cd6c5-127">State Management</span></span>  
 <span data-ttu-id="cd6c5-128">Nemuseli dělat údržbu stavu služby.</span><span class="sxs-lookup"><span data-stu-id="cd6c5-128">Avoid having to maintain state in services.</span></span> <span data-ttu-id="cd6c5-129">Pouze nemá zachování stavu mívají ohrozit škálovatelnost aplikace, ale mechanismy řízení stavu technologie ASP.NET a WCF se velmi liší, i když WCF podporovat mechanismy ASP.NET v režimu kompatibility ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="cd6c5-129">Not only does maintaining state tend to compromise the scalability of an application, but the state management mechanisms of ASP.NET and WCF are very different, although WCF does support the ASP.NET mechanisms in ASP.NET compatibility mode.</span></span>  
  
## <a name="exception-handling"></a><span data-ttu-id="cd6c5-130">Zpracování výjimek</span><span class="sxs-lookup"><span data-stu-id="cd6c5-130">Exception Handling</span></span>  
 <span data-ttu-id="cd6c5-131">Při navrhování struktury typy dat, které mají odesílat a přijímat přes službu, také návrhu struktury k reprezentaci různých typů výjimek, které můžou nastat v rámci služby než chtít předávaným klienta.</span><span class="sxs-lookup"><span data-stu-id="cd6c5-131">In designing the structures of the data types to be sent and received by a service, also design structures to represent the various types of exceptions that might occur within a service that one might wish to convey to a client.</span></span>  
  
```  
[Serializable]  
[XmlRoot(  
     Namespace="ExplicitNamespace", IsNullable=true)]  
    public partial class AnticipatedException {  
  
     private string anticipatedExceptionInformationField;  
  
     public string AnticipatedExceptionInformation {  
      get {  
          return this.anticipatedExceptionInformationField;  
          }  
      set {  
          this.anticipatedExceptionInformationField = value;  
          }  
     }  
}  
```  
  
 <span data-ttu-id="cd6c5-132">Poskytněte těchto tříd možnost sami serializaci do formátu XML:</span><span class="sxs-lookup"><span data-stu-id="cd6c5-132">Give such classes the ability to serialize themselves to XML:</span></span>  
  
```  
public XmlNode ToXML()  
{  
     XmlSerializer serializer = new XmlSerializer(  
      typeof(AnticipatedException));  
     MemoryStream memoryStream = new MemoryStream();  
     XmlTextWriter writer = new XmlTextWriter(  
     memoryStream, UnicodeEncoding.UTF8);  
     serializer.Serialize(writer, this);  
     XmlDocument document = new XmlDocument();  
     document.LoadXml(new string(  
     UnicodeEncoding.UTF8.GetChars(  
     memoryStream.GetBuffer())).Trim());  
    return document.DocumentElement;  
}  
```  
  
 <span data-ttu-id="cd6c5-133">Třídy pak lze upravit podrobnosti pro explicitně vyvolána <xref:System.Web.Services.Protocols.SoapException> instancí:</span><span class="sxs-lookup"><span data-stu-id="cd6c5-133">The classes can then be used to provide the details for explicitly thrown <xref:System.Web.Services.Protocols.SoapException> instances:</span></span>  
  
```  
AnctipatedException exception = new AnticipatedException();  
exception.AnticipatedExceptionInformation = "…";  
throw new SoapException(  
     "Fault occurred",  
     SoapException.ClientFaultCode,  
     Context.Request.Url.AbsoluteUri,  
     exception.ToXML());  
```  
  
 <span data-ttu-id="cd6c5-134">Tyto třídy výjimek bude snadno opakovaně použitelné s WCF<xref:System.ServiceModel.FaultException%601> třída má být vyvolána nová `FaultException<AnticipatedException>(anticipatedException);`</span><span class="sxs-lookup"><span data-stu-id="cd6c5-134">These exception classes will be readily reusable with the WCF<xref:System.ServiceModel.FaultException%601> class to throw a new `FaultException<AnticipatedException>(anticipatedException);`</span></span>  
  
## <a name="security"></a><span data-ttu-id="cd6c5-135">Zabezpečení</span><span class="sxs-lookup"><span data-stu-id="cd6c5-135">Security</span></span>  
 <span data-ttu-id="cd6c5-136">Následuje několik doporučení zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="cd6c5-136">The following are some security recommendations.</span></span>  
  
-   <span data-ttu-id="cd6c5-137">Vyhněte se použití profilů technologie ASP.NET 2.0, jako je pomocí by omezit použití režimu integrace ASP.NET, pokud došlo k migraci služby WCF.</span><span class="sxs-lookup"><span data-stu-id="cd6c5-137">Avoid using ASP.NET 2.0 Profiles, as using them would restrict the use of ASP.NET Integration Mode if the service was migrated to WCF.</span></span>  
  
-   <span data-ttu-id="cd6c5-138">Nepoužívejte seznamy řízení přístupu k řízení přístupu ke službám, jako rozhraní ASP.NET Web services podporuje seznamy ACL pomocí Internetové informační služby (IIS), WCF nemá – protože webových služeb ASP.NET závisí na službě IIS pro hostování a WCF nutně nemusí být hostovaný ve službě IIS.</span><span class="sxs-lookup"><span data-stu-id="cd6c5-138">Avoid using ACLs to control access to services, as ASP.NET Web services supports ACLs using Internet Information Services (IIS), WCF does not—because ASP.NET Web services depend on IIS for hosting, and WCF does not necessarily have to be hosted in IIS.</span></span>  
  
-   <span data-ttu-id="cd6c5-139">Zvažte použití zprostředkovatelů rolí prostředí ASP.NET 2.0 pro ověřování přístupu k prostředkům služby.</span><span class="sxs-lookup"><span data-stu-id="cd6c5-139">Do consider using ASP.NET 2.0 Role Providers for authorizing access to the resources of a service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd6c5-140">Viz také</span><span class="sxs-lookup"><span data-stu-id="cd6c5-140">See Also</span></span>  
 [<span data-ttu-id="cd6c5-141">Očekávání přechodu na Windows Communication Foundation: Usnadnění budoucí integrace</span><span class="sxs-lookup"><span data-stu-id="cd6c5-141">Anticipating Adopting the Windows Communication Foundation: Easing Future Integration</span></span>](../../../../docs/framework/wcf/feature-details/anticipating-adopting-the-wcf-easing-future-integration.md)
