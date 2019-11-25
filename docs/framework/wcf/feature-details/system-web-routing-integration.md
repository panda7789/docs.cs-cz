---
title: System.Web.Routing Integration
ms.date: 03/30/2017
ms.assetid: 31fe2a4f-5c47-4e5d-8ee1-84c524609d41
ms.openlocfilehash: 85137689a31573dc10e8f7384007830ab40d31df
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/12/2019
ms.locfileid: "73976040"
---
# <a name="systemwebrouting-integration"></a>System.Web.Routing Integration
Při hostování služby Windows Communication Foundation (WCF) v internetové informační službě (IIS) umístíte soubor. svc do virtuálního adresáře. Tento soubor. svc určuje objekt pro vytváření hostitele služby, který se má použít, i třídu, která implementuje službu. Při provádění požadavků na službu zadáte soubor. svc v identifikátoru URI, například: `http://contoso.com/EmployeeServce.svc`. Pro programátory, kteří píší služby REST, tento typ identifikátoru URI není optimální. Identifikátory URI pro služby REST určují konkrétní prostředek a obvykle nemají žádná rozšíření. Funkce integrace <xref:System.Web.Routing> umožňuje hostovat službu WCF REST, která reaguje na identifikátory URI bez rozšíření. Další informace o směrování najdete v tématu [směrování ASP.NET](https://go.microsoft.com/fwlink/?LinkId=184660).  
  
## <a name="using-systemwebrouting-integration"></a>Použití integrace System. Web. Routing  
 Chcete-li použít funkci <xref:System.Web.Routing> Integration, použijte třídu <xref:System.ServiceModel.Activation.ServiceRoute> k vytvoření jedné nebo více tras a přidejte je do <xref:System.Web.Routing.RouteTable> v souboru Global. asax. Tyto trasy určují relativní identifikátory URI, na které služba reaguje. Následující příklad ukazuje, jak to provést.  
  
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
  
 Tím se směrují všechny požadavky s relativním identifikátorem URI, který začíná zákazníky služby `Service`.  
  
 V souboru Web. config je nutné přidat modul `System.Web.Routing.UrlRoutingModule`, nastavit atribut `runAllManagedModulesForAllRequests` na `true`a přidat obslužnou rutinu `UrlRoutingHandler` do prvku `<system.webServer>`, jak je znázorněno v následujícím příkladu.  
  
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
  
 Tím se načte modul a obslužná rutina, která se vyžaduje pro směrování. Další informace najdete v tématu [Směrování](../../../../docs/framework/wcf/feature-details/routing.md). Musíte také nastavit atribut `aspNetCompatibilityEnabled`, aby `true` v prvku `<serviceHostingEnvironment>`, jak je znázorněno v následujícím příkladu.  
  
```xml  
<system.serviceModel>  
    <serviceHostingEnvironment aspNetCompatibilityEnabled="true"/>  
        <!-- ... -->  
    </system.serviceModel>  
```  
  
 Třída, která implementuje službu, musí povolit požadavky kompatibility ASP.NET, jak je znázorněno v následujícím příkladu.  
  
```csharp 
[ServiceContract]  
[AspNetCompatibilityRequirements(RequirementsMode=AspNetCompatibilityRequirementsMode.Allowed)]  
    public class Service  
    {  
        // ...  
    }  
```  
  
## <a name="see-also"></a>Viz také:

- [Programovací model webových služeb HTTP WCF](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
- [ASP.NET směrování](https://go.microsoft.com/fwlink/?LinkId=184660)
