---
title: 'Postupy: migrace kódu webové služby ASP.NET do služby Windows Communication Foundation'
ms.date: 03/30/2017
ms.assetid: e528c64f-c027-4f2e-ada6-d8f3994cf8d6
ms.openlocfilehash: 90a6109a56299ec1bcaff4a35141abc194484772
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-migrate-aspnet-web-service-code-to-the-windows-communication-foundation"></a>Postupy: migrace kódu webové služby ASP.NET do služby Windows Communication Foundation
Následující postup popisuje, jak migrovat webové služby ASP.NET do služby Windows Communication Foundation (WCF).  
  
## <a name="procedure"></a>Postup  
  
#### <a name="to-migrate-aspnet-web-service-code-to-wcf"></a>Migrace kódu webové služby ASP.NET do WCF  
  
1.  Ujistěte se, že o komplexní sadu testů pro službu neexistují.  
  
2.  Generování schématu WSDL pro službu a uložení kopie ve stejné složce jako soubor .asmx služby.  
  
3.  Upgradujte webovou službu ASP.NET na používání rozhraní .NET 2.0. Nejprve nasadit rozhraní .NET Framework 2.0 na aplikaci v IIS a pak použít Visual Studio 2005 pro automatizaci procesu převodu kódu, jak je uvedeno v [podrobné příručce k převodu webové projekty z Visual Studio .NET 2002 nebo 2003 k sadě Visual Studio 2005](http://go.microsoft.com/fwlink/?LinkId=96492). Spusťte sadu testů.  
  
4.  Zadat explicitní hodnoty `Namespace` a `Name` parametry <xref:System.Web.Services.WebService> atributy, pokud již nejsou zadána. Totéž proveďte pro `MessageName` parametr <xref:System.Web.Services.WebMethodAttribute>. Pokud explicitní hodnoty nejsou zadány již pro hlavičky SOAPAction HTTP, které směrují požadavky metody a potom explicitně zadat výchozí hodnota `Action` parametr s <xref:System.Web.Services.Protocols.SoapDocumentMethodAttribute>.  
  
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
  
5.  Testování změn.  
  
6.  Přesuňte všechny podstatné kód v těla metod třídy samostatnou třídu, která původní třída je proveden použití.  
  
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
  
7.  Testování změn.  
  
8.  Přidejte odkazy na sestavení WCF System.ServiceModel a System.Runtime.Serialization do projektu ASP.NET – webové služby.  
  
9. Spustit [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) generovat třídu klienta WCF z schématu WSDL. Přidání modulu generovaná třída řešení.  
  
10. Modul třídy generované v předchozím kroku obsahuje definici rozhraní.  
  
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
  
     Upravte definici třídy služeb ASP.NET Web tak, aby je třída definovaná jako implementace tohoto rozhraní, jak je znázorněno v následujícím ukázkovém kódu.  
  
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
  
11. Kompilace projektu. Pravděpodobně došlo k několika chybám kvůli kód, který vygenerovala v kroku devět, který duplicitní definice typu. Opravte tyto chyby obvykle odstraněním existující definice typů. Testování změn.  
  
12. Odebrat atributy specifické pro ASP.NET, jako <xref:System.Web.Services.WebService>, <xref:System.Web.Services.WebMethodAttribute> a <xref:System.Web.Services.Protocols.SoapDocumentMethodAttribute>.  
  
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
  
13. Konfigurovat třídu, která je nyní typ služby WCF, tak, aby vyžadovala režim kompatibility WCF ASP.NET, pokud webová služba ASP.NET spoléhali na některé z následujících:  
  
    -   <xref:System.Web.HttpContext> Třídy.  
  
    -   Profilů technologie ASP.NET.  
  
    -   Seznamy ACL v souborů .asmx.  
  
    -   Možnosti ověřování služby IIS.  
  
    -   Možnosti zosobnění technologie ASP.NET.  
  
    -   Globalizace ASP.NET.  
  
    ```  
    [System.ServiceModel.AspNetCompatibilityRequirements(  
      RequirementsMode=AspNetCompatbilityRequirementsMode.Required)]  
    public class Adder: AdderSoap  
    ```  
  
14. Původní soubor .asmx a přejmenovat. asmx.old.  
  
15. Vytvořte soubor služby WCF pro službu, poskytněte rozšíření, .asmx a uložte ho do kořenové aplikace ve službě IIS.  
  
    ```xml  
    <%@Service Class="MyOrganization.Adder" %>  
    <%@Assembly Name="MyServiceAssembly" %>   
    ```  
  
16. Přidání konfigurace WCF pro službu jeho souboru Web.config. Konfigurovat službu používat [ \<basicHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md), použijte službu soubor s příponou .asmx vytvořili v předchozích krocích a negeneruje WSDL pro sebe sama, ale pomocí jazyka WSDL z kroku 2. Také nakonfigurujte, aby používal režim kompatibility ASP.NET v případě potřeby.  
  
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
  
17. Uložte konfiguraci.  
  
18. Kompilace projektu.  
  
19. Spusťte sadu testů a ujistěte se, že všechny změny fungovat.  
  
## <a name="see-also"></a>Viz také  
 [Postupy: Migrace kódu klienta webové služby ASP.NET na Windows Communication Foundation](../../../../docs/framework/wcf/feature-details/migrate-asp-net-web-service-client-to-wcf.md)
