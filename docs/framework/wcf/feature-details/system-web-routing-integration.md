---
title: System.Web.Routing Integration
ms.date: 03/30/2017
ms.assetid: 31fe2a4f-5c47-4e5d-8ee1-84c524609d41
ms.openlocfilehash: 5bd405d66dcad597bbe6f452703d25372fdb7682
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="systemwebrouting-integration"></a>System.Web.Routing Integration
Při hostování služby Windows Communication Foundation (WCF) v Internetové informační služby (IIS) můžete umístit soubor .svc ve virtuálním adresáři. Tento soubor .svc určuje vytváření hostitele služby a také třídu, která implementuje službu používat. Při zasílání požadavků na službu zadáte soubor .svc v identifikátoru URI, například: http://contoso.com/EmployeeServce.svc. Tento typ identifikátoru URI pro programátory, kteří vytvářejí služby REST není optimální. Identifikátory URI pro služby REST zadejte konkrétní prostředek a obvykle nemají žádné rozšíření. <xref:System.Web.Routing> Funkce integrace umožňuje hostování služby WCF REST, která reaguje na identifikátory URI bez přípony. Další informace o směrování najdete [směrování ASP.NET](http://go.microsoft.com/fwlink/?LinkId=184660) a [AspNetRouteIntegration](../../../../docs/framework/wcf/samples/aspnetrouteintegration.md) ukázka.  
  
## <a name="using-systemwebrouting-integration"></a>Pomocí integrace System.Web.Routing  
 Použít <xref:System.Web.Routing> funkce integrace použijete <xref:System.ServiceModel.Activation.ServiceRoute> třídy vytvořit jednu nebo víc tras a přidat je do <xref:System.Web.Routing.RouteTable> v souboru Global.asax. Tyto trasy zadejte relativní identifikátory URI, který služba reaguje na. Následující příklad ukazuje, jak to provést.  
  
```  
<%@ Application Language="C#" %>  
<%@ Import Namespace="System.Web.Routing" %>  
<%@ Import Namespace="System.ServiceModel.Activation" %>  
<%@ Import Namespace="System.ServiceModel.Web " %>  
  
<script RunAt="server">  
    void Application_Start(object sender, EventArgs e)  
    {  
        RegisterRoutes(RouteTable.Routes);  
    }  
  
    private void RegisterRoutes(RouteCollection routes)  
    {  
        routes.Add(new ServiceRoute("Customers", new WebServiceHostFactory(), typeof(Service)));   
   }  
</script>  
```  
  
 To směrovat všechny požadavky s relativní identifikátor URI, který začíná s zákazníkům `Service` služby.  
  
 V souboru Web.config je třeba přidat `System.Web.Routing.UrlRoutingModule` nastaven, `runAllManagedModulesForAllRequests` atribut `true`a přidejte `UrlRoutingHandler` obslužná rutina `<system.webServer>` element, jak je znázorněno v následujícím příkladu.  
  
```xml  
<system.webServer>  
      <modules runAllManagedModulesForAllRequests="true">  
        <add name="UrlRoutingModule" type="System.Web.Routing.UrlRoutingModule, System.Web, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a" />  
      </modules>  
      <handlers>  
        <add name="UrlRoutingHandler" preCondition="integratedMode" verb="*" path="UrlRouting.axd"/>  
      </handlers>  
    </system.webServer>  
```  
  
 Tento kód načte modul a obslužná rutina vyžaduje pro směrování. Další informace najdete v tématu [směrování](../../../../docs/framework/wcf/feature-details/routing.md). Je nutné také nastavit `aspNetCompatibilityEnabled` atribut `true` v `<serviceHostingEnvironment>` element, jak je znázorněno v následujícím příkladu.  
  
```xml  
<system.serviceModel>  
    <serviceHostingEnvironment aspNetCompatibilityEnabled="true"/>  
        <!-- ... -->  
    </system.serviceModel>  
```  
  
 Třídu, která implementuje služby musíte povolit požadavky na kompatibilitu ASP.NET, jak je znázorněno v následujícím příkladu.  
  
```  
[ServiceContract]  
[AspNetCompatibilityRequirements(RequirementsMode=AspNetCompatibilityRequirementsMode.Allowed)]  
    public class Service  
    {  
        // ...  
    }  
```  
  
## <a name="see-also"></a>Viz také  
 [Programovací model webových služeb HTTP WCF](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)  
 [Směrování ASP.NET](http://go.microsoft.com/fwlink/?LinkId=184660)
