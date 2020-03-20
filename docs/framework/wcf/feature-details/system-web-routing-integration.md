---
title: System.Web.Routing Integration
ms.date: 03/30/2017
ms.assetid: 31fe2a4f-5c47-4e5d-8ee1-84c524609d41
ms.openlocfilehash: a80b5c3b336b4fd18b347a25ceaf509baf6461b4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184385"
---
# <a name="systemwebrouting-integration"></a>System.Web.Routing Integration
Při hostování služby WCF (Windows Communication Foundation) v Internetové informační službě (IIS) umístíte soubor SVC do virtuálního adresáře. Tento soubor SVC určuje hostitelskou továrnu služby, která má být používána, a také třídu, která službu implementuje. Při vytváření požadavků na službu zadáte soubor .svc v `http://contoso.com/EmployeeServce.svc`identifikátoru URI, například: . Pro programátory, kteří píší služby REST, není tento typ identifikátoru URI optimální. Identifikátory URI pro služby REST určují konkrétní prostředek a obvykle nemají žádná rozšíření. Funkce <xref:System.Web.Routing> integrace umožňuje hostovat službu WCF REST, která reaguje na identifikátory URI bez rozšíření. Další informace o směrování naleznete [v tématu ASP.NET Routing](https://docs.microsoft.com/previous-versions/aspnet/cc668201(v=vs.100)).  
  
## <a name="using-systemwebrouting-integration"></a>Použití integrace System.Web.Routing  
 Chcete-li <xref:System.Web.Routing> použít funkci integrace, použijte třídu <xref:System.ServiceModel.Activation.ServiceRoute> k vytvoření jedné <xref:System.Web.Routing.RouteTable> nebo více tras a jejich přidání do souboru Global.asax. Tyto trasy určují relativní identifikátory URI, na které služba reaguje. Následující příklad ukazuje, jak to provést.  
  
```aspx-csharp  
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
  
 To směruje všechny požadavky s relativní URI, který `Service` začíná zákazníci ke službě.  
  
 V souboru Web.config musíte `System.Web.Routing.UrlRoutingModule` přidat `runAllManagedModulesForAllRequests` modul, `true`nastavit atribut `UrlRoutingHandler` na aplikaci a přidat obslužnou rutinu `<system.webServer>` k prvku, jak je znázorněno v následujícím příkladu.  
  
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
  
 Tím se načte modul a obslužná rutina potřebná pro směrování. Další informace naleznete v tématu [Směrování](../../../../docs/framework/wcf/feature-details/routing.md). Je také nutné `aspNetCompatibilityEnabled` nastavit `true` atribut `<serviceHostingEnvironment>` v prvku, jak je znázorněno v následujícím příkladu.  
  
```xml  
<system.serviceModel>  
    <serviceHostingEnvironment aspNetCompatibilityEnabled="true"/>  
        <!-- ... -->  
    </system.serviceModel>  
```  
  
 Třída, která implementuje službu musí povolit ASP.NET požadavky na kompatibilitu, jak je znázorněno v následujícím příkladu.  
  
```csharp
[ServiceContract]  
[AspNetCompatibilityRequirements(RequirementsMode=AspNetCompatibilityRequirementsMode.Allowed)]  
    public class Service  
    {  
        // ...  
    }  
```  
  
## <a name="see-also"></a>Viz také

- [Programovací model webových služeb HTTP WCF](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
- [ASP.NET směrování](https://docs.microsoft.com/previous-versions/aspnet/cc668201(v=vs.100))
