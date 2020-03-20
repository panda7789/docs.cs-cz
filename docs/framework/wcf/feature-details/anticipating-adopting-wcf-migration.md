---
title: 'Očekávání přechodu na Windows Communication Foundation: Usnadnění budoucí migrace'
ms.date: 03/30/2017
ms.assetid: f49664d9-e9e0-425c-a259-93f0a569d01b
ms.openlocfilehash: 995bdaaaba96bf8697ea75c1f1a17fa8e51ec2d5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185474"
---
# <a name="anticipating-adopting-the-windows-communication-foundation-easing-future-migration"></a><span data-ttu-id="e59ab-102">Očekávání přechodu na Windows Communication Foundation: Usnadnění budoucí migrace</span><span class="sxs-lookup"><span data-stu-id="e59ab-102">Anticipating Adopting the Windows Communication Foundation: Easing Future Migration</span></span>
<span data-ttu-id="e59ab-103">Chcete-li zajistit snadnější budoucí migraci nových aplikací ASP.NET do WCF, postupujte podle předchozích doporučení a následující doporučení.</span><span class="sxs-lookup"><span data-stu-id="e59ab-103">To ensure an easier future migration of new ASP.NET applications to WCF, follow the preceding recommendations as well as the following recommendations.</span></span>  
  
## <a name="protocols"></a><span data-ttu-id="e59ab-104">Protokoly</span><span class="sxs-lookup"><span data-stu-id="e59ab-104">Protocols</span></span>  
 <span data-ttu-id="e59ab-105">Zakažte ASP.NET 2.0 podpora soap 1.2:</span><span class="sxs-lookup"><span data-stu-id="e59ab-105">Disable ASP.NET 2.0’s support for SOAP 1.2:</span></span>  
  
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
  
 <span data-ttu-id="e59ab-106">To je vhodné, protože WCF vyžaduje zprávy, které odpovídají různým protokolům, jako je SOAP 1.1 a SOAP 1.2, pro použití různých koncových bodů.</span><span class="sxs-lookup"><span data-stu-id="e59ab-106">Doing so is advisable because WCF requires messages conforming to different protocols, like SOAP 1.1 and SOAP 1.2, to go by using different endpoints.</span></span> <span data-ttu-id="e59ab-107">Pokud je webová služba ASP.NET 2.0 nakonfigurována tak, aby podporovala rozhraní SOAP 1.1 i SOAP 1.2, což je výchozí konfigurace, nelze ji migrovat dopředu na jeden koncový bod WCF na původní adrese, která by byla jistě kompatibilní se všemi ASP.NET web stávajících klientů služby.</span><span class="sxs-lookup"><span data-stu-id="e59ab-107">If an ASP.NET 2.0 Web service is configured to support both SOAP 1.1 and SOAP 1.2, which is the default configuration, then it cannot be migrated forward to a single WCF endpoint at the original address that would be certainly be compatible with all of the ASP.NET Web service’s existing clients.</span></span> <span data-ttu-id="e59ab-108">Také výběr SOAP 1.2 namísto 1.1 bude více vážně omezit klientelu služby.</span><span class="sxs-lookup"><span data-stu-id="e59ab-108">Also choosing SOAP 1.2 instead of 1.1 will more severely restrict the clientele of the service.</span></span>  
  
## <a name="service-development"></a><span data-ttu-id="e59ab-109">Vývoj služeb</span><span class="sxs-lookup"><span data-stu-id="e59ab-109">Service Development</span></span>  
 <span data-ttu-id="e59ab-110">WCF umožňuje definovat servisní smlouvy <xref:System.ServiceModel.ServiceContractAttribute> použitím buď rozhraní nebo třídy.</span><span class="sxs-lookup"><span data-stu-id="e59ab-110">WCF allows you to define service contracts by applying the <xref:System.ServiceModel.ServiceContractAttribute> either to interfaces or to classes.</span></span> <span data-ttu-id="e59ab-111">Doporučuje se použít atribut rozhraní spíše než na třídu, protože tím vytvoří definici smlouvy, která může být různě implementována libovolným počtem tříd.</span><span class="sxs-lookup"><span data-stu-id="e59ab-111">It is recommended to apply the attribute to an interface rather than to a class, because doing so creates a definition of a contract that can be variously implemented by any number of classes.</span></span> <span data-ttu-id="e59ab-112">ASP.NET 2.0 podporuje možnost <xref:System.Web.Services.WebService> použití atributu rozhraní i tříd.</span><span class="sxs-lookup"><span data-stu-id="e59ab-112">ASP.NET 2.0 supports the option of applying the <xref:System.Web.Services.WebService> attribute to interfaces as well as classes.</span></span> <span data-ttu-id="e59ab-113">Však jak již bylo zmíněno, je vada v ASP.NET 2.0, podle kterého Namespace parametr <xref:System.Web.Services.WebService> atribut nemá žádný vliv, pokud je tento atribut použit rozhraní spíše než třídy.</span><span class="sxs-lookup"><span data-stu-id="e59ab-113">However, as mentioned already, there is a defect in ASP.NET 2.0, by which the Namespace parameter of the <xref:System.Web.Services.WebService> attribute has no effect when that attribute is applied to an interface rather than a class.</span></span> <span data-ttu-id="e59ab-114">Vzhledem k tomu, `http://tempuri.org`že je obecně vhodné změnit obor názvů služby z <xref:System.Web.Services.WebService> výchozí hodnoty , pomocí parametru Obor <xref:System.ServiceModel.ServiceContractAttribute> názvů atributu, je třeba pokračovat v definování ASP.NET webových služeb použitím atributu buď na rozhraní, nebo na třídy.</span><span class="sxs-lookup"><span data-stu-id="e59ab-114">Since it is generally advisable to modify the namespace of a service from the default value, `http://tempuri.org`, using the Namespace parameter of the <xref:System.Web.Services.WebService> attribute, one should continue defining ASP.NET Web Services by applying the <xref:System.ServiceModel.ServiceContractAttribute> attribute either to interfaces or to classes.</span></span>  
  
- <span data-ttu-id="e59ab-115">Mají co nejméně kódu v metodách, kterými jsou definovány tyto rozhraní.</span><span class="sxs-lookup"><span data-stu-id="e59ab-115">Have as little code as possible in the methods by which those interfaces are defined.</span></span> <span data-ttu-id="e59ab-116">Nechte je delegovat svou práci na jiné třídy.</span><span class="sxs-lookup"><span data-stu-id="e59ab-116">Have them delegate their work to other classes.</span></span> <span data-ttu-id="e59ab-117">Nové typy služeb WCF pak mohou také delegovat svou věcnou práci na tyto třídy.</span><span class="sxs-lookup"><span data-stu-id="e59ab-117">New WCF service types could then also delegate their substantive work to those classes.</span></span>  
  
- <span data-ttu-id="e59ab-118">Zadejte explicitní názvy pro operace `MessageName` služby <xref:System.Web.Services.WebMethodAttribute>pomocí parametru .</span><span class="sxs-lookup"><span data-stu-id="e59ab-118">Provide explicit names for the operations of a service using the `MessageName` parameter of the <xref:System.Web.Services.WebMethodAttribute>.</span></span>  
  
    ```csharp  
    [WebMethod(MessageName="ExplicitName")]  
    string Echo(string input);  
    ```  
  
     <span data-ttu-id="e59ab-119">Je to důležité, protože výchozí názvy operací v ASP.NET se liší od výchozích názvů poskytnutých WCF.</span><span class="sxs-lookup"><span data-stu-id="e59ab-119">Doing so is important, because the default names for operations in ASP.NET are different from the default names supplied by WCF.</span></span> <span data-ttu-id="e59ab-120">Poskytnutím explicitních názvů se vyhnete spoléhání se na výchozí názvy.</span><span class="sxs-lookup"><span data-stu-id="e59ab-120">By providing explicit names, you avoid relying on the default ones.</span></span>  
  
- <span data-ttu-id="e59ab-121">Neimplementujte operace ASP.NET webové služby pomocí polymorfních metod, protože WCF nepodporuje implementaci operací pomocí polymorfních metod.</span><span class="sxs-lookup"><span data-stu-id="e59ab-121">Do not implement ASP.NET Web service operations with polymorphic methods, because WCF does not support implementing operations with polymorphic methods.</span></span>  
  
- <span data-ttu-id="e59ab-122">Slouží <xref:System.Web.Services.Protocols.SoapDocumentMethodAttribute> k zadání explicitních hodnot pro hlavičky SOAPAction HTTP, kterými budou požadavky HTTP směrovány na metody.</span><span class="sxs-lookup"><span data-stu-id="e59ab-122">Use the <xref:System.Web.Services.Protocols.SoapDocumentMethodAttribute> to provide explicit values for the SOAPAction HTTP headers by which HTTP requests will be routed to methods.</span></span>  
  
    ```csharp  
    [WebMethod]  
    [SoapDocumentMethod(RequestElementName="ExplicitAction")]  
    string Echo(string input);  
    ```  
  
     <span data-ttu-id="e59ab-123">Vezmeme-li tento přístup bude obcházení museli spoléhat na výchozí SOAPAction hodnoty používané ASP.NET a WCF jsou stejné.</span><span class="sxs-lookup"><span data-stu-id="e59ab-123">Taking this approach will circumvent having to rely on the default SOAPAction values used by ASP.NET and WCF being the same.</span></span>  
  
- <span data-ttu-id="e59ab-124">Nepoužívejte rozšíření SOAP.</span><span class="sxs-lookup"><span data-stu-id="e59ab-124">Avoid using SOAP extensions.</span></span> <span data-ttu-id="e59ab-125">Pokud soap rozšíření jsou požadovány, pak určit, zda účel, pro který jsou považovány za je funkce, která je již k dispozici WCF.</span><span class="sxs-lookup"><span data-stu-id="e59ab-125">If SOAP extensions are required, then determine whether the purpose for which they are being considered is a feature that is already provided by WCF.</span></span> <span data-ttu-id="e59ab-126">Pokud tomu tak skutečně je, pak přehodnotit volbu nepřijmout WCF hned.</span><span class="sxs-lookup"><span data-stu-id="e59ab-126">If that is indeed the case, then reconsider the choice to not adopt WCF right away.</span></span>  
  
## <a name="state-management"></a><span data-ttu-id="e59ab-127">Správa státu</span><span class="sxs-lookup"><span data-stu-id="e59ab-127">State Management</span></span>  
 <span data-ttu-id="e59ab-128">Vyhněte se nutnosti udržovat stav ve službách.</span><span class="sxs-lookup"><span data-stu-id="e59ab-128">Avoid having to maintain state in services.</span></span> <span data-ttu-id="e59ab-129">Nejen, že udržování stavu mají tendenci ohrozit škálovatelnost aplikace, ale mechanismy správy stavu ASP.NET a WCF jsou velmi odlišné, i když WCF podporuje ASP.NET mechanismy v režimu kompatibility ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="e59ab-129">Not only does maintaining state tend to compromise the scalability of an application, but the state management mechanisms of ASP.NET and WCF are very different, although WCF does support the ASP.NET mechanisms in ASP.NET compatibility mode.</span></span>  
  
## <a name="exception-handling"></a><span data-ttu-id="e59ab-130">Zpracování výjimek</span><span class="sxs-lookup"><span data-stu-id="e59ab-130">Exception Handling</span></span>  
 <span data-ttu-id="e59ab-131">Při navrhování struktury datových typů, které mají být odeslány a přijaty službou, také návrhové struktury představují různé typy výjimek, které mohou nastat v rámci služby, které by bylo možné chtít předat klientovi.</span><span class="sxs-lookup"><span data-stu-id="e59ab-131">In designing the structures of the data types to be sent and received by a service, also design structures to represent the various types of exceptions that might occur within a service that one might wish to convey to a client.</span></span>  
  
```csharp  
[Serializable]  
[XmlRoot(Namespace="ExplicitNamespace", IsNullable=true)]  
public partial class AnticipatedException
{
    private string anticipatedExceptionInformationField;  

    public string AnticipatedExceptionInformation
    {  
        get {
            return this.anticipatedExceptionInformationField;  
        }  
        set {  
            this.anticipatedExceptionInformationField = value;  
        }  
    }  
}  
```  
  
 <span data-ttu-id="e59ab-132">Poznejte těmto třídám možnost serializovat se do XML:</span><span class="sxs-lookup"><span data-stu-id="e59ab-132">Give such classes the ability to serialize themselves to XML:</span></span>  
  
```csharp  
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
  
 <span data-ttu-id="e59ab-133">Třídy pak lze poskytnout podrobnosti pro <xref:System.Web.Services.Protocols.SoapException> explicitně vyvolána instance:</span><span class="sxs-lookup"><span data-stu-id="e59ab-133">The classes can then be used to provide the details for explicitly thrown <xref:System.Web.Services.Protocols.SoapException> instances:</span></span>  
  
```csharp  
AnticipatedException exception = new AnticipatedException();  
exception.AnticipatedExceptionInformation = "…";  
throw new SoapException(  
     "Fault occurred",  
     SoapException.ClientFaultCode,  
     Context.Request.Url.AbsoluteUri,  
     exception.ToXML());  
```  
  
 <span data-ttu-id="e59ab-134">Tyto třídy výjimek budou snadno opakovaně použitelné <xref:System.ServiceModel.FaultException%601> s třídou WCF, aby vyvolaly novou`FaultException<AnticipatedException>(anticipatedException);`</span><span class="sxs-lookup"><span data-stu-id="e59ab-134">These exception classes will be readily reusable with the WCF <xref:System.ServiceModel.FaultException%601> class to throw a new `FaultException<AnticipatedException>(anticipatedException);`</span></span>  
  
## <a name="security"></a><span data-ttu-id="e59ab-135">Zabezpečení</span><span class="sxs-lookup"><span data-stu-id="e59ab-135">Security</span></span>  
 <span data-ttu-id="e59ab-136">Následují některá doporučení zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="e59ab-136">The following are some security recommendations.</span></span>  
  
- <span data-ttu-id="e59ab-137">Nepoužívejte ASP.NET profily 2.0, protože jejich použití by omezilo použití režimu integrace ASP.NET, pokud by služba byla migrována do WCF.</span><span class="sxs-lookup"><span data-stu-id="e59ab-137">Avoid using ASP.NET 2.0 Profiles, as using them would restrict the use of ASP.NET Integration Mode if the service was migrated to WCF.</span></span>  
  
- <span data-ttu-id="e59ab-138">Nepoužívejte přístupové sítě ACL k řízení přístupu ke službám, protože ASP.NET webové služby podporují seznamu ACL používající internetové informační služby (IIS), wcf nikoli – protože ASP.NET webové služby závisí na službě IIS pro hostování a wcf nemusí být nutně hostován ve službě IIS.</span><span class="sxs-lookup"><span data-stu-id="e59ab-138">Avoid using ACLs to control access to services, as ASP.NET Web services supports ACLs using Internet Information Services (IIS), WCF does not—because ASP.NET Web services depend on IIS for hosting, and WCF does not necessarily have to be hosted in IIS.</span></span>  
  
- <span data-ttu-id="e59ab-139">Zvažte použití ASP.NET 2.0 zprostředkovatelé rolí pro autorizaci přístupu k prostředkům služby.</span><span class="sxs-lookup"><span data-stu-id="e59ab-139">Do consider using ASP.NET 2.0 Role Providers for authorizing access to the resources of a service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e59ab-140">Viz také</span><span class="sxs-lookup"><span data-stu-id="e59ab-140">See also</span></span>

- [<span data-ttu-id="e59ab-141">Očekávání přechodu na Windows Communication Foundation: Usnadnění budoucí integrace</span><span class="sxs-lookup"><span data-stu-id="e59ab-141">Anticipating Adopting the Windows Communication Foundation: Easing Future Integration</span></span>](../../../../docs/framework/wcf/feature-details/anticipating-adopting-the-wcf-easing-future-integration.md)
