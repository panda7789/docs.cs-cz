---
title: 'Očekávání přechodu na Windows Communication Foundation: Usnadnění budoucí migrace'
ms.date: 03/30/2017
ms.assetid: f49664d9-e9e0-425c-a259-93f0a569d01b
ms.openlocfilehash: b43f509bd49ebe89d7ed0be4c37b3ed179aaeb8c
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84576496"
---
# <a name="anticipating-adopting-the-windows-communication-foundation-easing-future-migration"></a><span data-ttu-id="f0f1e-102">Očekávání přechodu na Windows Communication Foundation: Usnadnění budoucí migrace</span><span class="sxs-lookup"><span data-stu-id="f0f1e-102">Anticipating Adopting the Windows Communication Foundation: Easing Future Migration</span></span>
<span data-ttu-id="f0f1e-103">Chcete-li zajistit snazší budoucí migraci nových aplikací ASP.NET do služby WCF, postupujte podle předchozích doporučení a také následujících doporučení.</span><span class="sxs-lookup"><span data-stu-id="f0f1e-103">To ensure an easier future migration of new ASP.NET applications to WCF, follow the preceding recommendations as well as the following recommendations.</span></span>  
  
## <a name="protocols"></a><span data-ttu-id="f0f1e-104">Protokoly</span><span class="sxs-lookup"><span data-stu-id="f0f1e-104">Protocols</span></span>  
 <span data-ttu-id="f0f1e-105">Zakažte podporu ASP.NET 2.0 pro SOAP 1,2:</span><span class="sxs-lookup"><span data-stu-id="f0f1e-105">Disable ASP.NET 2.0’s support for SOAP 1.2:</span></span>  
  
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
  
 <span data-ttu-id="f0f1e-106">Doporučuje se to proto, že WCF vyžaduje zprávy, které odpovídají různým protokolům, jako jsou SOAP 1,1 a SOAP 1,2, pro přechod pomocí různých koncových bodů.</span><span class="sxs-lookup"><span data-stu-id="f0f1e-106">Doing so is advisable because WCF requires messages conforming to different protocols, like SOAP 1.1 and SOAP 1.2, to go by using different endpoints.</span></span> <span data-ttu-id="f0f1e-107">Pokud je webová služba ASP.NET 2,0 nakonfigurovaná tak, aby podporovala SOAP 1,1 i SOAP 1,2, což je výchozí konfigurace, pak nemůže být migrována do jednoho koncového bodu WCF na původní adrese, která by byla určitě kompatibilní se všemi stávajícími klienty webové služby ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="f0f1e-107">If an ASP.NET 2.0 Web service is configured to support both SOAP 1.1 and SOAP 1.2, which is the default configuration, then it cannot be migrated forward to a single WCF endpoint at the original address that would be certainly be compatible with all of the ASP.NET Web service’s existing clients.</span></span> <span data-ttu-id="f0f1e-108">Také výběr protokolu SOAP 1,2 namísto 1,1 bude vážně omezovat Clientele služby.</span><span class="sxs-lookup"><span data-stu-id="f0f1e-108">Also choosing SOAP 1.2 instead of 1.1 will more severely restrict the clientele of the service.</span></span>  
  
## <a name="service-development"></a><span data-ttu-id="f0f1e-109">Vývoj služeb</span><span class="sxs-lookup"><span data-stu-id="f0f1e-109">Service Development</span></span>  
 <span data-ttu-id="f0f1e-110">Služba WCF umožňuje definovat kontrakty služby použitím <xref:System.ServiceModel.ServiceContractAttribute> rozhraní nebo na třídy.</span><span class="sxs-lookup"><span data-stu-id="f0f1e-110">WCF allows you to define service contracts by applying the <xref:System.ServiceModel.ServiceContractAttribute> either to interfaces or to classes.</span></span> <span data-ttu-id="f0f1e-111">Doporučuje se použít atribut na rozhraní, nikoli na třídu, protože tím vznikne definice kontraktu, který může být různým způsobem implementován libovolným počtem tříd.</span><span class="sxs-lookup"><span data-stu-id="f0f1e-111">It is recommended to apply the attribute to an interface rather than to a class, because doing so creates a definition of a contract that can be variously implemented by any number of classes.</span></span> <span data-ttu-id="f0f1e-112">ASP.NET 2,0 podporuje možnost použití <xref:System.Web.Services.WebService> atributu na rozhraní i třídy.</span><span class="sxs-lookup"><span data-stu-id="f0f1e-112">ASP.NET 2.0 supports the option of applying the <xref:System.Web.Services.WebService> attribute to interfaces as well as classes.</span></span> <span data-ttu-id="f0f1e-113">Jak již bylo zmíněno, existuje vada v ASP.NET 2,0, kdy parametr namespace <xref:System.Web.Services.WebService> atributu nemá žádný vliv, pokud je tento atribut použit na rozhraní, nikoli na třídu.</span><span class="sxs-lookup"><span data-stu-id="f0f1e-113">However, as mentioned already, there is a defect in ASP.NET 2.0, by which the Namespace parameter of the <xref:System.Web.Services.WebService> attribute has no effect when that attribute is applied to an interface rather than a class.</span></span> <span data-ttu-id="f0f1e-114">Vzhledem k tomu, že je obecně vhodné změnit obor názvů služby z výchozí hodnoty, `http://tempuri.org` použijte parametr oboru názvů <xref:System.Web.Services.WebService> atributu, jeden by měl pokračovat v definování ASP.NET webových služeb použitím <xref:System.ServiceModel.ServiceContractAttribute> atributu buď na rozhraní nebo na třídy.</span><span class="sxs-lookup"><span data-stu-id="f0f1e-114">Since it is generally advisable to modify the namespace of a service from the default value, `http://tempuri.org`, using the Namespace parameter of the <xref:System.Web.Services.WebService> attribute, one should continue defining ASP.NET Web Services by applying the <xref:System.ServiceModel.ServiceContractAttribute> attribute either to interfaces or to classes.</span></span>  
  
- <span data-ttu-id="f0f1e-115">Musí mít co nejmenší kód v metodách, pomocí kterých jsou tato rozhraní definována.</span><span class="sxs-lookup"><span data-stu-id="f0f1e-115">Have as little code as possible in the methods by which those interfaces are defined.</span></span> <span data-ttu-id="f0f1e-116">Přidělí jim svou práci na jiné třídy.</span><span class="sxs-lookup"><span data-stu-id="f0f1e-116">Have them delegate their work to other classes.</span></span> <span data-ttu-id="f0f1e-117">Nové typy služeb WCF by pak mohly delegovat svou podstatnou práci na tyto třídy.</span><span class="sxs-lookup"><span data-stu-id="f0f1e-117">New WCF service types could then also delegate their substantive work to those classes.</span></span>  
  
- <span data-ttu-id="f0f1e-118">Zadejte explicitní názvy operací služby pomocí `MessageName` parametru <xref:System.Web.Services.WebMethodAttribute> .</span><span class="sxs-lookup"><span data-stu-id="f0f1e-118">Provide explicit names for the operations of a service using the `MessageName` parameter of the <xref:System.Web.Services.WebMethodAttribute>.</span></span>  
  
    ```csharp  
    [WebMethod(MessageName="ExplicitName")]  
    string Echo(string input);  
    ```  
  
     <span data-ttu-id="f0f1e-119">To je důležité, protože výchozí názvy pro operace v ASP.NET se liší od výchozích názvů dodaných službou WCF.</span><span class="sxs-lookup"><span data-stu-id="f0f1e-119">Doing so is important, because the default names for operations in ASP.NET are different from the default names supplied by WCF.</span></span> <span data-ttu-id="f0f1e-120">Zadáním explicitních názvů předejdete tomu, že se spoléháte na výchozí hodnoty.</span><span class="sxs-lookup"><span data-stu-id="f0f1e-120">By providing explicit names, you avoid relying on the default ones.</span></span>  
  
- <span data-ttu-id="f0f1e-121">Neimplementujte operace webové služby ASP.NET s polymorfními metodami, protože WCF nepodporuje implementaci operací pomocí polymorfních metod.</span><span class="sxs-lookup"><span data-stu-id="f0f1e-121">Do not implement ASP.NET Web service operations with polymorphic methods, because WCF does not support implementing operations with polymorphic methods.</span></span>  
  
- <span data-ttu-id="f0f1e-122">Použijte <xref:System.Web.Services.Protocols.SoapDocumentMethodAttribute> k zadání explicitních hodnot hlaviček protokolu HTTP SOAPAction, podle kterých budou požadavky HTTP směrovány na metody.</span><span class="sxs-lookup"><span data-stu-id="f0f1e-122">Use the <xref:System.Web.Services.Protocols.SoapDocumentMethodAttribute> to provide explicit values for the SOAPAction HTTP headers by which HTTP requests will be routed to methods.</span></span>  
  
    ```csharp  
    [WebMethod]  
    [SoapDocumentMethod(RequestElementName="ExplicitAction")]  
    string Echo(string input);  
    ```  
  
     <span data-ttu-id="f0f1e-123">Díky tomuto přístupu se postará, že se musí spoléhat na výchozí hodnoty SOAPAction používané ASP.NET a WCF.</span><span class="sxs-lookup"><span data-stu-id="f0f1e-123">Taking this approach will circumvent having to rely on the default SOAPAction values used by ASP.NET and WCF being the same.</span></span>  
  
- <span data-ttu-id="f0f1e-124">Nepoužívejte rozšíření SOAP.</span><span class="sxs-lookup"><span data-stu-id="f0f1e-124">Avoid using SOAP extensions.</span></span> <span data-ttu-id="f0f1e-125">Pokud jsou požadovány rozšíření SOAP, určete, zda je účel, pro který jsou zvažovány, funkce, která je již součástí služby WCF.</span><span class="sxs-lookup"><span data-stu-id="f0f1e-125">If SOAP extensions are required, then determine whether the purpose for which they are being considered is a feature that is already provided by WCF.</span></span> <span data-ttu-id="f0f1e-126">V takovém případě je vhodné znovu zvážit možnost nepřijmout WCF hned.</span><span class="sxs-lookup"><span data-stu-id="f0f1e-126">If that is indeed the case, then reconsider the choice to not adopt WCF right away.</span></span>  
  
## <a name="state-management"></a><span data-ttu-id="f0f1e-127">Správa stavu</span><span class="sxs-lookup"><span data-stu-id="f0f1e-127">State Management</span></span>  
 <span data-ttu-id="f0f1e-128">Nemusíte se starat o stav ve službách.</span><span class="sxs-lookup"><span data-stu-id="f0f1e-128">Avoid having to maintain state in services.</span></span> <span data-ttu-id="f0f1e-129">Nejen udržují stav za následek ohrožení škálovatelnosti aplikace, ale mechanismy správy stavů ASP.NET a WCF se velmi liší, i když WCF podporuje mechanismy ASP.NET v režimu kompatibility ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="f0f1e-129">Not only does maintaining state tend to compromise the scalability of an application, but the state management mechanisms of ASP.NET and WCF are very different, although WCF does support the ASP.NET mechanisms in ASP.NET compatibility mode.</span></span>  
  
## <a name="exception-handling"></a><span data-ttu-id="f0f1e-130">Zpracování výjimek</span><span class="sxs-lookup"><span data-stu-id="f0f1e-130">Exception Handling</span></span>  
 <span data-ttu-id="f0f1e-131">V návrhu struktur datových typů, které mají být zasílány a přijímány službou, také Navrhněte struktury, které reprezentují různé typy výjimek, které mohou nastat v rámci služby, které může chtít předat klientovi.</span><span class="sxs-lookup"><span data-stu-id="f0f1e-131">In designing the structures of the data types to be sent and received by a service, also design structures to represent the various types of exceptions that might occur within a service that one might wish to convey to a client.</span></span>  
  
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
  
 <span data-ttu-id="f0f1e-132">Poskytněte takové třídy schopnost serializace do XML:</span><span class="sxs-lookup"><span data-stu-id="f0f1e-132">Give such classes the ability to serialize themselves to XML:</span></span>  
  
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
  
 <span data-ttu-id="f0f1e-133">Třídy pak mohou být použity k poskytnutí podrobností pro explicitně vygenerované <xref:System.Web.Services.Protocols.SoapException> instance:</span><span class="sxs-lookup"><span data-stu-id="f0f1e-133">The classes can then be used to provide the details for explicitly thrown <xref:System.Web.Services.Protocols.SoapException> instances:</span></span>  
  
```csharp  
AnticipatedException exception = new AnticipatedException();  
exception.AnticipatedExceptionInformation = "…";  
throw new SoapException(  
     "Fault occurred",  
     SoapException.ClientFaultCode,  
     Context.Request.Url.AbsoluteUri,  
     exception.ToXML());  
```  
  
 <span data-ttu-id="f0f1e-134">Tyto třídy výjimek budou snadno použitelné s <xref:System.ServiceModel.FaultException%601> třídou WCF k vyvolání nového`FaultException<AnticipatedException>(anticipatedException);`</span><span class="sxs-lookup"><span data-stu-id="f0f1e-134">These exception classes will be readily reusable with the WCF <xref:System.ServiceModel.FaultException%601> class to throw a new `FaultException<AnticipatedException>(anticipatedException);`</span></span>  
  
## <a name="security"></a><span data-ttu-id="f0f1e-135">Zabezpečení</span><span class="sxs-lookup"><span data-stu-id="f0f1e-135">Security</span></span>  
 <span data-ttu-id="f0f1e-136">Níže jsou uvedená některá doporučení zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="f0f1e-136">The following are some security recommendations.</span></span>  
  
- <span data-ttu-id="f0f1e-137">Nepoužívejte profily ASP.NET 2,0, protože by je bylo možné použít při migraci služby na WCF.</span><span class="sxs-lookup"><span data-stu-id="f0f1e-137">Avoid using ASP.NET 2.0 Profiles, as using them would restrict the use of ASP.NET Integration Mode if the service was migrated to WCF.</span></span>  
  
- <span data-ttu-id="f0f1e-138">Nepoužívejte seznamy ACL k řízení přístupu ke službám, protože webové služby ASP.NET podporují seznamy ACL pomocí služby Internetová informační služba (IIS), služba WCF nefunguje – protože webové služby ASP.NET závisejí na službě IIS pro hostování a služba WCF nemusí nutně být hostovaná ve službě IIS.</span><span class="sxs-lookup"><span data-stu-id="f0f1e-138">Avoid using ACLs to control access to services, as ASP.NET Web services supports ACLs using Internet Information Services (IIS), WCF does not—because ASP.NET Web services depend on IIS for hosting, and WCF does not necessarily have to be hosted in IIS.</span></span>  
  
- <span data-ttu-id="f0f1e-139">Zvažte použití zprostředkovatelů rolí ASP.NET 2,0 pro autorizaci přístupu k prostředkům služby.</span><span class="sxs-lookup"><span data-stu-id="f0f1e-139">Do consider using ASP.NET 2.0 Role Providers for authorizing access to the resources of a service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0f1e-140">Viz také</span><span class="sxs-lookup"><span data-stu-id="f0f1e-140">See also</span></span>

- [<span data-ttu-id="f0f1e-141">Očekávání přechodu na Windows Communication Foundation: Usnadnění budoucí integrace</span><span class="sxs-lookup"><span data-stu-id="f0f1e-141">Anticipating Adopting the Windows Communication Foundation: Easing Future Integration</span></span>](anticipating-adopting-the-wcf-easing-future-integration.md)
