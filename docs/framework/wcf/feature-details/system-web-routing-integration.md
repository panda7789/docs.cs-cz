---
title: System.Web.Routing Integration
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 31fe2a4f-5c47-4e5d-8ee1-84c524609d41
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 73ec25ab5376841b2970fedf17ad1de176923f16
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="systemwebrouting-integration"></a>System.Web.Routing Integration
Při hostování [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] služby v Internetové informační služby (IIS) umístit soubor .svc ve virtuálním adresáři. Tento soubor .svc určuje vytváření hostitele služby a také třídu, která implementuje službu používat. Při zasílání požadavků na službu zadáte soubor .svc v identifikátoru URI, například: http://contoso.com/EmployeeServce.svc. Tento typ identifikátoru URI pro programátory, kteří vytvářejí služby REST není optimální. Identifikátory URI pro služby REST zadejte konkrétní prostředek a obvykle nemají žádné rozšíření. <xref:System.Web.Routing> Funkce integrace umožňuje hostování [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby REST, která reaguje na identifikátory URI bez přípony. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]směrování najdete [směrování ASP.NET](http://go.microsoft.com/fwlink/?LinkId=184660) a [AspNetRouteIntegration](../../../../docs/framework/wcf/samples/aspnetrouteintegration.md) ukázka.  
  
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
  
 Tento kód načte modul a obslužná rutina vyžaduje pro směrování. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Směrování](../../../../docs/framework/wcf/feature-details/routing.md). Je nutné také nastavit `aspNetCompatibilityEnabled` atribut `true` v `<serviceHostingEnvironment>` element, jak je znázorněno v následujícím příkladu.  
  
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
 [Model programování webových služeb HTTP WCF](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)  
 [Směrování ASP.NET](http://go.microsoft.com/fwlink/?LinkId=184660)
