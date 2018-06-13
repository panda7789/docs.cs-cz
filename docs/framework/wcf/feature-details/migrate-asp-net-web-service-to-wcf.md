---
title: 'Postupy: migrace kódu webové služby ASP.NET do služby Windows Communication Foundation'
ms.date: 03/30/2017
ms.assetid: e528c64f-c027-4f2e-ada6-d8f3994cf8d6
ms.openlocfilehash: 90a6109a56299ec1bcaff4a35141abc194484772
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33496696"
---
# <a name="how-to-migrate-aspnet-web-service-code-to-the-windows-communication-foundation"></a><span data-ttu-id="4f3d1-102">Postupy: migrace kódu webové služby ASP.NET do služby Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="4f3d1-102">How to: Migrate ASP.NET Web Service Code to the Windows Communication Foundation</span></span>
<span data-ttu-id="4f3d1-103">Následující postup popisuje, jak migrovat webové služby ASP.NET do služby Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="4f3d1-103">The following procedure describes how to migrate an ASP.NET Web Service to Windows Communication Foundation (WCF).</span></span>  
  
## <a name="procedure"></a><span data-ttu-id="4f3d1-104">Postup</span><span class="sxs-lookup"><span data-stu-id="4f3d1-104">Procedure</span></span>  
  
#### <a name="to-migrate-aspnet-web-service-code-to-wcf"></a><span data-ttu-id="4f3d1-105">Migrace kódu webové služby ASP.NET do WCF</span><span class="sxs-lookup"><span data-stu-id="4f3d1-105">To migrate ASP.NET Web service code to WCF</span></span>  
  
1.  <span data-ttu-id="4f3d1-106">Ujistěte se, že o komplexní sadu testů pro službu neexistují.</span><span class="sxs-lookup"><span data-stu-id="4f3d1-106">Ensure that a comprehensive set of tests exist for the service.</span></span>  
  
2.  <span data-ttu-id="4f3d1-107">Generování schématu WSDL pro službu a uložení kopie ve stejné složce jako soubor .asmx služby.</span><span class="sxs-lookup"><span data-stu-id="4f3d1-107">Generate the WSDL for the service and save a copy in the same folder as the service’s .asmx file.</span></span>  
  
3.  <span data-ttu-id="4f3d1-108">Upgradujte webovou službu ASP.NET na používání rozhraní .NET 2.0.</span><span class="sxs-lookup"><span data-stu-id="4f3d1-108">Upgrade the ASP.NET Web service to use .NET 2.0.</span></span> <span data-ttu-id="4f3d1-109">Nejprve nasadit rozhraní .NET Framework 2.0 na aplikaci v IIS a pak použít Visual Studio 2005 pro automatizaci procesu převodu kódu, jak je uvedeno v [podrobné příručce k převodu webové projekty z Visual Studio .NET 2002 nebo 2003 k sadě Visual Studio 2005](http://go.microsoft.com/fwlink/?LinkId=96492).</span><span class="sxs-lookup"><span data-stu-id="4f3d1-109">First deploy the .NET Framework 2.0 to the application in IIS, and then use Visual Studio 2005 to automate the code conversion process, as documented in [Step-By-Step Guide to Converting Web Projects from Visual Studio .NET 2002/2003 to Visual Studio 2005](http://go.microsoft.com/fwlink/?LinkId=96492).</span></span> <span data-ttu-id="4f3d1-110">Spusťte sadu testů.</span><span class="sxs-lookup"><span data-stu-id="4f3d1-110">Run the set of tests.</span></span>  
  
4.  <span data-ttu-id="4f3d1-111">Zadat explicitní hodnoty `Namespace` a `Name` parametry <xref:System.Web.Services.WebService> atributy, pokud již nejsou zadána.</span><span class="sxs-lookup"><span data-stu-id="4f3d1-111">Provide explicit values for the `Namespace` and `Name` parameters of the <xref:System.Web.Services.WebService> attributes if they are not provided already.</span></span> <span data-ttu-id="4f3d1-112">Totéž proveďte pro `MessageName` parametr <xref:System.Web.Services.WebMethodAttribute>.</span><span class="sxs-lookup"><span data-stu-id="4f3d1-112">Do the same for the `MessageName` parameter of the <xref:System.Web.Services.WebMethodAttribute>.</span></span> <span data-ttu-id="4f3d1-113">Pokud explicitní hodnoty nejsou zadány již pro hlavičky SOAPAction HTTP, které směrují požadavky metody a potom explicitně zadat výchozí hodnota `Action` parametr s <xref:System.Web.Services.Protocols.SoapDocumentMethodAttribute>.</span><span class="sxs-lookup"><span data-stu-id="4f3d1-113">If explicit values are not already provided for the SOAPAction HTTP headers by which requests are routed to methods, then explicitly specify the default value of the `Action` parameter with a <xref:System.Web.Services.Protocols.SoapDocumentMethodAttribute>.</span></span>  
  
    ```  
    [WebService(Namespace = "http://tempuri.org/", Name = "Adder")]  
    public class Adder  
    {  
         [WebMethod(MessageName = "Add")]  
         [SoapDocumentMethod(Action = "http://tempuri.org/Add")]  
         public double Add(SumInput input)  
         {  
              double sum = 0.00;  
              foreach (double inputValue in input.Input)  
              {  
                  sum += inputValue;  
              }  
          return sum;  
         }  
    }  
    ```  
  
5.  <span data-ttu-id="4f3d1-114">Testování změn.</span><span class="sxs-lookup"><span data-stu-id="4f3d1-114">Test the change.</span></span>  
  
6.  <span data-ttu-id="4f3d1-115">Přesuňte všechny podstatné kód v těla metod třídy samostatnou třídu, která původní třída je proveden použití.</span><span class="sxs-lookup"><span data-stu-id="4f3d1-115">Move any substantive code in the bodies of the methods of the class to a separate class that the original class is made to use.</span></span>  
  
    ```  
    [WebService(Namespace = "http://tempuri.org/", Name = "Adder")]  
    public class Adder  
    {  
         [WebMethod(MessageName = "Add")]  
         [SoapDocumentMethod(Action = "http://tempuri.org/Add")]  
         public double Add(SumInput input)  
         {  
              return new ActualAdder().Add(input);  
         }  
    }  
  
    internal class ActualAdder  
    {  
         internal double Add(SumInput input)  
         {  
              double sum = 0.00;  
              foreach (double inputValue in input.Input)  
              {  
                  sum += inputValue;  
              }  
          return sum;  
         }  
    }  
    ```  
  
7.  <span data-ttu-id="4f3d1-116">Testování změn.</span><span class="sxs-lookup"><span data-stu-id="4f3d1-116">Test the change.</span></span>  
  
8.  <span data-ttu-id="4f3d1-117">Přidejte odkazy na sestavení WCF System.ServiceModel a System.Runtime.Serialization do projektu ASP.NET – webové služby.</span><span class="sxs-lookup"><span data-stu-id="4f3d1-117">Add references to WCF assemblies System.ServiceModel and System.Runtime.Serialization to the ASP.NET Web service project.</span></span>  
  
9. <span data-ttu-id="4f3d1-118">Spustit [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) generovat třídu klienta WCF z schématu WSDL.</span><span class="sxs-lookup"><span data-stu-id="4f3d1-118">Run [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) to generate a WCF client class from the WSDL.</span></span> <span data-ttu-id="4f3d1-119">Přidání modulu generovaná třída řešení.</span><span class="sxs-lookup"><span data-stu-id="4f3d1-119">Add the generated class module to the solution.</span></span>  
  
10. <span data-ttu-id="4f3d1-120">Modul třídy generované v předchozím kroku obsahuje definici rozhraní.</span><span class="sxs-lookup"><span data-stu-id="4f3d1-120">The class module generated in the preceding step contains the definition of an interface.</span></span>  
  
    ```  
    [System.ServiceModel.ServiceContractAttribute()]  
    public interface AdderSoap  
    {  
         [System.ServiceModel.OperationContractAttribute(  
          Action="http://tempuri.org/Add",   
          ReplyAction="http://tempuri.org/Add")]  
         AddResponse Add(AddRequest request);  
    }  
    ```  
  
     <span data-ttu-id="4f3d1-121">Upravte definici třídy služeb ASP.NET Web tak, aby je třída definovaná jako implementace tohoto rozhraní, jak je znázorněno v následujícím ukázkovém kódu.</span><span class="sxs-lookup"><span data-stu-id="4f3d1-121">Modify the definition of the ASP.NET Web service class so that the class is defined as implementing that interface, as shown in the following sample code.</span></span>  
  
    ```  
    [WebService(Namespace = "http://tempuri.org/", Name = "Adder")]  
    public class Adder: AdderSoap  
    {  
         [WebMethod(MessageName = "Add")]  
         [SoapDocumentMethod(Action = "http://tempuri.org/Add")]  
         public double Add(SumInput input)  
         {  
              return new ActualAdder().Add(input);  
         }  
  
         public AddResponse Add(AddRequest request)  
         {  
            return new AddResponse(  
            new AddResponseBody(  
            this.Add(request.Body.input)));  
         }  
    }  
    ```  
  
11. <span data-ttu-id="4f3d1-122">Kompilace projektu.</span><span class="sxs-lookup"><span data-stu-id="4f3d1-122">Compile the project.</span></span> <span data-ttu-id="4f3d1-123">Pravděpodobně došlo k několika chybám kvůli kód, který vygenerovala v kroku devět, který duplicitní definice typu.</span><span class="sxs-lookup"><span data-stu-id="4f3d1-123">There may be some errors due to the code generated in step nine that duplicated some type definitions.</span></span> <span data-ttu-id="4f3d1-124">Opravte tyto chyby obvykle odstraněním existující definice typů.</span><span class="sxs-lookup"><span data-stu-id="4f3d1-124">Repair those errors, usually by deleting the pre-existing definitions of the types.</span></span> <span data-ttu-id="4f3d1-125">Testování změn.</span><span class="sxs-lookup"><span data-stu-id="4f3d1-125">Test the change.</span></span>  
  
12. <span data-ttu-id="4f3d1-126">Odebrat atributy specifické pro ASP.NET, jako <xref:System.Web.Services.WebService>, <xref:System.Web.Services.WebMethodAttribute> a <xref:System.Web.Services.Protocols.SoapDocumentMethodAttribute>.</span><span class="sxs-lookup"><span data-stu-id="4f3d1-126">Remove the ASP.NET-specific attributes, such as the <xref:System.Web.Services.WebService>, <xref:System.Web.Services.WebMethodAttribute> and <xref:System.Web.Services.Protocols.SoapDocumentMethodAttribute>.</span></span>  
  
    ```  
    public class Adder: AdderSoap  
    {  
         public double Add(SumInput input)  
         {  
              return new ActualAdder().Add(input);  
         }  
  
         public AddResponse Add(AddRequest request)  
         {  
              return new AddResponse(  
             new AddResponseBody(  
            this.Add(request.Body.input)));  
         }  
    }  
    ```  
  
13. <span data-ttu-id="4f3d1-127">Konfigurovat třídu, která je nyní typ služby WCF, tak, aby vyžadovala režim kompatibility WCF ASP.NET, pokud webová služba ASP.NET spoléhali na některé z následujících:</span><span class="sxs-lookup"><span data-stu-id="4f3d1-127">Configure the class, which is now a WCF service type, to require WCF ASP.NET compatibility mode if the ASP.NET Web service relied on any of the following:</span></span>  
  
    -   <span data-ttu-id="4f3d1-128"><xref:System.Web.HttpContext> Třídy.</span><span class="sxs-lookup"><span data-stu-id="4f3d1-128">The <xref:System.Web.HttpContext> class.</span></span>  
  
    -   <span data-ttu-id="4f3d1-129">Profilů technologie ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="4f3d1-129">The ASP.NET Profiles.</span></span>  
  
    -   <span data-ttu-id="4f3d1-130">Seznamy ACL v souborů .asmx.</span><span class="sxs-lookup"><span data-stu-id="4f3d1-130">ACLs on .asmx files.</span></span>  
  
    -   <span data-ttu-id="4f3d1-131">Možnosti ověřování služby IIS.</span><span class="sxs-lookup"><span data-stu-id="4f3d1-131">IIS authentication options.</span></span>  
  
    -   <span data-ttu-id="4f3d1-132">Možnosti zosobnění technologie ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="4f3d1-132">ASP.NET impersonation options.</span></span>  
  
    -   <span data-ttu-id="4f3d1-133">Globalizace ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="4f3d1-133">ASP.NET globalization.</span></span>  
  
    ```  
    [System.ServiceModel.AspNetCompatibilityRequirements(  
      RequirementsMode=AspNetCompatbilityRequirementsMode.Required)]  
    public class Adder: AdderSoap  
    ```  
  
14. <span data-ttu-id="4f3d1-134">Původní soubor .asmx a přejmenovat. asmx.old.</span><span class="sxs-lookup"><span data-stu-id="4f3d1-134">Rename the original .asmx file to .asmx.old.</span></span>  
  
15. <span data-ttu-id="4f3d1-135">Vytvořte soubor služby WCF pro službu, poskytněte rozšíření, .asmx a uložte ho do kořenové aplikace ve službě IIS.</span><span class="sxs-lookup"><span data-stu-id="4f3d1-135">Create a WCF service file for the service, give it the extension, .asmx, and save it into the application root in IIS.</span></span>  
  
    ```xml  
    <%@Service Class="MyOrganization.Adder" %>  
    <%@Assembly Name="MyServiceAssembly" %>   
    ```  
  
16. <span data-ttu-id="4f3d1-136">Přidání konfigurace WCF pro službu jeho souboru Web.config.</span><span class="sxs-lookup"><span data-stu-id="4f3d1-136">Add a WCF configuration for the service to its Web.config file.</span></span> <span data-ttu-id="4f3d1-137">Konfigurovat službu používat [ \<basicHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md), použijte službu soubor s příponou .asmx vytvořili v předchozích krocích a negeneruje WSDL pro sebe sama, ale pomocí jazyka WSDL z kroku 2.</span><span class="sxs-lookup"><span data-stu-id="4f3d1-137">Configure the service to use the [\<basicHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md), to use the service file with the .asmx extension created in the preceding steps, and to not generate WSDL for itself, but to use the WSDL from step two.</span></span> <span data-ttu-id="4f3d1-138">Také nakonfigurujte, aby používal režim kompatibility ASP.NET v případě potřeby.</span><span class="sxs-lookup"><span data-stu-id="4f3d1-138">Also configure it to use ASP.NET compatibility mode if necessary.</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <configuration>  
     <system.web>  
      <compilation>  
      <buildProviders>  
       <remove extension=".asmx" />  
       <add extension=".asmx"   
        type=  
        "System.ServiceModel.Activation.ServiceBuildProvider,  
        T:System.ServiceModel, Version=2.0.0.0,   
       Culture=neutral,   
       PublicKeyToken=b77a5c561934e089" />  
      </buildProviders>  
      </compilation>  
     </system.web>  
     <system.serviceModel>  
      <services>  
      <service name="MyOrganization.Adder "  
        behaviorConfiguration="AdderBehavior">  
       <endpoint   
        address=""  
        binding="basicHttpBinding"  
        contract="AdderSoap "/>  
       </service>  
      </services>  
      <behaviors>  
      <behavior name="AdderBehavior">  
       <metadataPublishing   
        enableMetadataExchange="true"   
        enableGetWsdl="true"   
        enableHelpPage="true"   
        metadataLocation=  
        "http://MyHost.com/AdderService/Service.WSDL"/>  
      </behavior>  
      </behaviors>  
      <serviceHostingEnvironment   
       aspNetCompatibilityEnabled ="true"/>  
     </system.serviceModel>  
    </configuration>  
    ```  
  
17. <span data-ttu-id="4f3d1-139">Uložte konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="4f3d1-139">Save the configuration.</span></span>  
  
18. <span data-ttu-id="4f3d1-140">Kompilace projektu.</span><span class="sxs-lookup"><span data-stu-id="4f3d1-140">Compile the project.</span></span>  
  
19. <span data-ttu-id="4f3d1-141">Spusťte sadu testů a ujistěte se, že všechny změny fungovat.</span><span class="sxs-lookup"><span data-stu-id="4f3d1-141">Run the set of tests to make sure all the changes work.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f3d1-142">Viz také</span><span class="sxs-lookup"><span data-stu-id="4f3d1-142">See Also</span></span>  
 [<span data-ttu-id="4f3d1-143">Postupy: Migrace kódu klienta webové služby ASP.NET na Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="4f3d1-143">How to: Migrate ASP.NET Web Service Client Code to the Windows Communication Foundation</span></span>](../../../../docs/framework/wcf/feature-details/migrate-asp-net-web-service-client-to-wcf.md)
