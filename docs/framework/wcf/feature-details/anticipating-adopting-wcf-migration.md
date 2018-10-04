---
title: 'Očekávání přechodu na Windows Communication Foundation: usnadnění budoucí migrace'
ms.date: 03/30/2017
ms.assetid: f49664d9-e9e0-425c-a259-93f0a569d01b
ms.openlocfilehash: 171a31b375eae4c032849c2a1c2090f5d9ff856f
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/04/2018
ms.locfileid: "48580638"
---
# <a name="anticipating-adopting-the-windows-communication-foundation-easing-future-migration"></a><span data-ttu-id="899fe-102">Očekávání přechodu na Windows Communication Foundation: usnadnění budoucí migrace</span><span class="sxs-lookup"><span data-stu-id="899fe-102">Anticipating Adopting the Windows Communication Foundation: Easing Future Migration</span></span>
<span data-ttu-id="899fe-103">Aby jednodušší budoucí migrace z nové aplikace ASP.NET na WCF, postupujte podle předchozí doporučení, jakož i následující doporučení.</span><span class="sxs-lookup"><span data-stu-id="899fe-103">To ensure an easier future migration of new ASP.NET applications to WCF, follow the preceding recommendations as well as the following recommendations.</span></span>  
  
## <a name="protocols"></a><span data-ttu-id="899fe-104">Protokoly</span><span class="sxs-lookup"><span data-stu-id="899fe-104">Protocols</span></span>  
 <span data-ttu-id="899fe-105">Zakážete podporu protokolu SOAP 1.2 ASP.NET 2.0:</span><span class="sxs-lookup"><span data-stu-id="899fe-105">Disable ASP.NET 2.0’s support for SOAP 1.2:</span></span>  
  
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
  
 <span data-ttu-id="899fe-106">Tím se doporučuje, protože vyžaduje zprávy, které odpovídají různé protokoly, jako je protokol SOAP 1.1 a SOAP 1.2, přejděte pomocí různých koncových bodů WCF.</span><span class="sxs-lookup"><span data-stu-id="899fe-106">Doing so is advisable because WCF requires messages conforming to different protocols, like SOAP 1.1 and SOAP 1.2, to go by using different endpoints.</span></span> <span data-ttu-id="899fe-107">Pokud webového rozhraní ASP.NET 2.0, služba je nakonfigurována pro podporu protokolu SOAP 1.1 a SOAP 1.2, což je výchozí konfigurace, pak jej nelze migrovat vpřed na jednom koncovém bodu WCF na původní adrese, která by byla jistě být kompatibilní se všemi ASP.NET Web existující klienti služby.</span><span class="sxs-lookup"><span data-stu-id="899fe-107">If an ASP.NET 2.0 Web service is configured to support both SOAP 1.1 and SOAP 1.2, which is the default configuration, then it cannot be migrated forward to a single WCF endpoint at the original address that would be certainly be compatible with all of the ASP.NET Web service’s existing clients.</span></span> <span data-ttu-id="899fe-108">Také výběrem SOAP 1.2 místo 1.1 více vážně omezí zákazníků služby.</span><span class="sxs-lookup"><span data-stu-id="899fe-108">Also choosing SOAP 1.2 instead of 1.1 will more severely restrict the clientele of the service.</span></span>  
  
## <a name="service-development"></a><span data-ttu-id="899fe-109">Vývoj služby</span><span class="sxs-lookup"><span data-stu-id="899fe-109">Service Development</span></span>  
 <span data-ttu-id="899fe-110">WCF umožňuje definování kontraktů služby s použitím <xref:System.ServiceModel.ServiceContractAttribute> rozhraní nebo tříd.</span><span class="sxs-lookup"><span data-stu-id="899fe-110">WCF allows you to define service contracts by applying the <xref:System.ServiceModel.ServiceContractAttribute> either to interfaces or to classes.</span></span> <span data-ttu-id="899fe-111">Doporučujeme použít atribut rozhraní, nikoli třída, protože to uděláte tak vytvoří definici kontraktu, která může být libovolný počet tříd různě implementována.</span><span class="sxs-lookup"><span data-stu-id="899fe-111">It is recommended to apply the attribute to an interface rather than to a class, because doing so creates a definition of a contract that can be variously implemented by any number of classes.</span></span> <span data-ttu-id="899fe-112">Technologie ASP.NET 2.0 podporuje možnost použít <xref:System.Web.Services.WebService> atribut rozhraní, stejně jako třídy.</span><span class="sxs-lookup"><span data-stu-id="899fe-112">ASP.NET 2.0 supports the option of applying the <xref:System.Web.Services.WebService> attribute to interfaces as well as classes.</span></span> <span data-ttu-id="899fe-113">Jak již bylo zmíněno, existuje ale vadu v technologii ASP.NET 2.0, podle kterého parametru Namespace <xref:System.Web.Services.WebService> atribut nemá žádný vliv při použití atributu na rozhraní namísto třídy.</span><span class="sxs-lookup"><span data-stu-id="899fe-113">However, as mentioned already, there is a defect in ASP.NET 2.0, by which the Namespace parameter of the <xref:System.Web.Services.WebService> attribute has no effect when that attribute is applied to an interface rather than a class.</span></span> <span data-ttu-id="899fe-114">Protože je obecně vhodné změnit obor názvů služby z výchozí hodnoty `http://tempuri.org`, pomocí parametru Namespace <xref:System.Web.Services.WebService> atribut, jeden by měl pokračovat definování webových služeb ASP.NET s použitím <xref:System.ServiceModel.ServiceContractAttribute> Atribut rozhraní nebo tříd.</span><span class="sxs-lookup"><span data-stu-id="899fe-114">Since it is generally advisable to modify the namespace of a service from the default value, `http://tempuri.org`, using the Namespace parameter of the <xref:System.Web.Services.WebService> attribute, one should continue defining ASP.NET Web Services by applying the <xref:System.ServiceModel.ServiceContractAttribute> attribute either to interfaces or to classes.</span></span>  
  
-   <span data-ttu-id="899fe-115">Metody, které jsou definovány těchto rozhraní je možné máte jako malým množstvím kódu.</span><span class="sxs-lookup"><span data-stu-id="899fe-115">Have as little code as possible in the methods by which those interfaces are defined.</span></span> <span data-ttu-id="899fe-116">Požádejte svou práci do jiné třídy delegáta.</span><span class="sxs-lookup"><span data-stu-id="899fe-116">Have them delegate their work to other classes.</span></span> <span data-ttu-id="899fe-117">Nový typ služby WCF pak rovněž delegovat práci nepotřebují důležité do těchto tříd.</span><span class="sxs-lookup"><span data-stu-id="899fe-117">New WCF service types could then also delegate their substantive work to those classes.</span></span>  
  
-   <span data-ttu-id="899fe-118">Zadat explicitní názvy pro operace využívání služby `MessageName` parametr <xref:System.Web.Services.WebMethodAttribute>.</span><span class="sxs-lookup"><span data-stu-id="899fe-118">Provide explicit names for the operations of a service using the `MessageName` parameter of the <xref:System.Web.Services.WebMethodAttribute>.</span></span>  
  
    ```  
    [WebMethod(MessageName="ExplicitName")]  
    string Echo(string input);  
    ```  
  
     <span data-ttu-id="899fe-119">To je důležité, protože se liší od výchozí názvy poskytnutých WCF výchozí názvy pro operace v technologii ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="899fe-119">Doing so is important, because the default names for operations in ASP.NET are different from the default names supplied by WCF.</span></span> <span data-ttu-id="899fe-120">Poskytnutím explicitní názvy neměli spoléhat na výchozí hodnoty.</span><span class="sxs-lookup"><span data-stu-id="899fe-120">By providing explicit names, you avoid relying on the default ones.</span></span>  
  
-   <span data-ttu-id="899fe-121">Neprovádějte implementaci operace služby rozhraní ASP.NET Web s polymorfní metody, protože WCF nepodporuje implementaci operace s polymorfní metody.</span><span class="sxs-lookup"><span data-stu-id="899fe-121">Do not implement ASP.NET Web service operations with polymorphic methods, because WCF does not support implementing operations with polymorphic methods.</span></span>  
  
-   <span data-ttu-id="899fe-122">Použití <xref:System.Web.Services.Protocols.SoapDocumentMethodAttribute> zadat explicitní hodnoty záhlaví SOAPAction HTTP, pomocí které protokolu HTTP se budou směrovat požadavky do metody.</span><span class="sxs-lookup"><span data-stu-id="899fe-122">Use the <xref:System.Web.Services.Protocols.SoapDocumentMethodAttribute> to provide explicit values for the SOAPAction HTTP headers by which HTTP requests will be routed to methods.</span></span>  
  
    ```  
    [WebMethod]  
    [SoapDocumentMethod(RequestElementName="ExplicitAction")]  
    string Echo(string input);  
    ```  
  
     <span data-ttu-id="899fe-123">Tento postup zajistí obejde museli spoléhat na výchozí hodnoty SOAPAction používané technologie ASP.NET a WCF se stejné.</span><span class="sxs-lookup"><span data-stu-id="899fe-123">Taking this approach will circumvent having to rely on the default SOAPAction values used by ASP.NET and WCF being the same.</span></span>  
  
-   <span data-ttu-id="899fe-124">Vyhněte se použití rozšíření SOAP.</span><span class="sxs-lookup"><span data-stu-id="899fe-124">Avoid using SOAP extensions.</span></span> <span data-ttu-id="899fe-125">Pokud rozšíření SOAP, pak určete, zda je účely, pro které jsou právě považovány za funkce, která je již poskytované WCF.</span><span class="sxs-lookup"><span data-stu-id="899fe-125">If SOAP extensions are required, then determine whether the purpose for which they are being considered is a feature that is already provided by WCF.</span></span> <span data-ttu-id="899fe-126">Pokud se ve skutečnosti je to tento případ, pak zvažte možnost, které nejsou hned přijmout WCF.</span><span class="sxs-lookup"><span data-stu-id="899fe-126">If that is indeed the case, then reconsider the choice to not adopt WCF right away.</span></span>  
  
## <a name="state-management"></a><span data-ttu-id="899fe-127">Správa stavu</span><span class="sxs-lookup"><span data-stu-id="899fe-127">State Management</span></span>  
 <span data-ttu-id="899fe-128">Vyhněte se nutnosti udržovat stav služby.</span><span class="sxs-lookup"><span data-stu-id="899fe-128">Avoid having to maintain state in services.</span></span> <span data-ttu-id="899fe-129">Pouze nemá zachování stavu vést k ohrožení škálovatelnost aplikace, ale stav mechanismy správy technologie ASP.NET a WCF jsou velmi odlišné, i když WCF podporovat mechanismy ASP.NET v režim kompatibility ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="899fe-129">Not only does maintaining state tend to compromise the scalability of an application, but the state management mechanisms of ASP.NET and WCF are very different, although WCF does support the ASP.NET mechanisms in ASP.NET compatibility mode.</span></span>  
  
## <a name="exception-handling"></a><span data-ttu-id="899fe-130">Zpracování výjimek</span><span class="sxs-lookup"><span data-stu-id="899fe-130">Exception Handling</span></span>  
 <span data-ttu-id="899fe-131">Při navrhování struktury datové typy na odeslané a přijaté službou, také návrh struktury tak, aby představují různé typy výjimek, které mohou nastat v rámci služby, že jedna možná budete chtít sdělit do klienta.</span><span class="sxs-lookup"><span data-stu-id="899fe-131">In designing the structures of the data types to be sent and received by a service, also design structures to represent the various types of exceptions that might occur within a service that one might wish to convey to a client.</span></span>  
  
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
  
 <span data-ttu-id="899fe-132">Umožnit takové třídy sami serializaci do formátu XML:</span><span class="sxs-lookup"><span data-stu-id="899fe-132">Give such classes the ability to serialize themselves to XML:</span></span>  
  
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
  
 <span data-ttu-id="899fe-133">Třídy pak umožňuje zadejte podrobnosti pro explicitně vyvolána <xref:System.Web.Services.Protocols.SoapException> instancí:</span><span class="sxs-lookup"><span data-stu-id="899fe-133">The classes can then be used to provide the details for explicitly thrown <xref:System.Web.Services.Protocols.SoapException> instances:</span></span>  
  
```  
AnctipatedException exception = new AnticipatedException();  
exception.AnticipatedExceptionInformation = "…";  
throw new SoapException(  
     "Fault occurred",  
     SoapException.ClientFaultCode,  
     Context.Request.Url.AbsoluteUri,  
     exception.ToXML());  
```  
  
 <span data-ttu-id="899fe-134">Tyto třídy výjimek bude snadno opakovaně použitelné s WCF<xref:System.ServiceModel.FaultException%601> třídy k vyvolání nové `FaultException<AnticipatedException>(anticipatedException);`</span><span class="sxs-lookup"><span data-stu-id="899fe-134">These exception classes will be readily reusable with the WCF<xref:System.ServiceModel.FaultException%601> class to throw a new `FaultException<AnticipatedException>(anticipatedException);`</span></span>  
  
## <a name="security"></a><span data-ttu-id="899fe-135">Zabezpečení</span><span class="sxs-lookup"><span data-stu-id="899fe-135">Security</span></span>  
 <span data-ttu-id="899fe-136">Následují některá doporučení zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="899fe-136">The following are some security recommendations.</span></span>  
  
-   <span data-ttu-id="899fe-137">Vyhněte se použití profilů ASP.NET 2.0, jako je použití by omezit použití režim integrace ASP.NET Pokud služby byl migrován a WCF.</span><span class="sxs-lookup"><span data-stu-id="899fe-137">Avoid using ASP.NET 2.0 Profiles, as using them would restrict the use of ASP.NET Integration Mode if the service was migrated to WCF.</span></span>  
  
-   <span data-ttu-id="899fe-138">Vyhněte se použití seznamů ACL pro řízení přístupu ke službám, jako rozhraní ASP.NET Web services podporuje seznamy řízení přístupu pomocí Internetové informační služby (IIS), WCF nepodporuje, protože rozhraní ASP.NET Web services závisí na službě IIS pro hostování a WCF nutně nemusí být hostovaná ve službě IIS.</span><span class="sxs-lookup"><span data-stu-id="899fe-138">Avoid using ACLs to control access to services, as ASP.NET Web services supports ACLs using Internet Information Services (IIS), WCF does not—because ASP.NET Web services depend on IIS for hosting, and WCF does not necessarily have to be hosted in IIS.</span></span>  
  
-   <span data-ttu-id="899fe-139">Zvažte použití zprostředkovatele rolí ASP.NET 2.0 pro ověřování přístupu k prostředkům služby.</span><span class="sxs-lookup"><span data-stu-id="899fe-139">Do consider using ASP.NET 2.0 Role Providers for authorizing access to the resources of a service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="899fe-140">Viz také</span><span class="sxs-lookup"><span data-stu-id="899fe-140">See Also</span></span>  
 [<span data-ttu-id="899fe-141">Očekávání přechodu na Windows Communication Foundation: Usnadnění budoucí integrace</span><span class="sxs-lookup"><span data-stu-id="899fe-141">Anticipating Adopting the Windows Communication Foundation: Easing Future Integration</span></span>](../../../../docs/framework/wcf/feature-details/anticipating-adopting-the-wcf-easing-future-integration.md)
