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
# <a name="systemwebrouting-integration"></a><span data-ttu-id="535e6-102">System.Web.Routing Integration</span><span class="sxs-lookup"><span data-stu-id="535e6-102">System.Web.Routing Integration</span></span>
<span data-ttu-id="535e6-103">Při hostování [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] služby v Internetové informační služby (IIS) umístit soubor .svc ve virtuálním adresáři.</span><span class="sxs-lookup"><span data-stu-id="535e6-103">When hosting a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] service in Internet Information Service (IIS) you place a .svc file in the virtual directory.</span></span> <span data-ttu-id="535e6-104">Tento soubor .svc určuje vytváření hostitele služby a také třídu, která implementuje službu používat.</span><span class="sxs-lookup"><span data-stu-id="535e6-104">This .svc file specifies the service host factory to use as well as the class that implements the service.</span></span> <span data-ttu-id="535e6-105">Při zasílání požadavků na službu zadáte soubor .svc v identifikátoru URI, například: http://contoso.com/EmployeeServce.svc.</span><span class="sxs-lookup"><span data-stu-id="535e6-105">When making requests to the service you specify the .svc file in the URI, for example: http://contoso.com/EmployeeServce.svc.</span></span> <span data-ttu-id="535e6-106">Tento typ identifikátoru URI pro programátory, kteří vytvářejí služby REST není optimální.</span><span class="sxs-lookup"><span data-stu-id="535e6-106">For programmers writing REST services this type of URI is not optimal.</span></span> <span data-ttu-id="535e6-107">Identifikátory URI pro služby REST zadejte konkrétní prostředek a obvykle nemají žádné rozšíření.</span><span class="sxs-lookup"><span data-stu-id="535e6-107">URIs for REST services specify a specific resource and normally do not have any extensions.</span></span> <span data-ttu-id="535e6-108"><xref:System.Web.Routing> Funkce integrace umožňuje hostování [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby REST, která reaguje na identifikátory URI bez přípony.</span><span class="sxs-lookup"><span data-stu-id="535e6-108">The <xref:System.Web.Routing> integration feature allows you to host a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] REST service that responds to URIs without an extension.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="535e6-109">směrování najdete [směrování ASP.NET](http://go.microsoft.com/fwlink/?LinkId=184660) a [AspNetRouteIntegration](../../../../docs/framework/wcf/samples/aspnetrouteintegration.md) ukázka.</span><span class="sxs-lookup"><span data-stu-id="535e6-109"> routing see [ASP.NET Routing](http://go.microsoft.com/fwlink/?LinkId=184660) and the [AspNetRouteIntegration](../../../../docs/framework/wcf/samples/aspnetrouteintegration.md) sample.</span></span>  
  
## <a name="using-systemwebrouting-integration"></a><span data-ttu-id="535e6-110">Pomocí integrace System.Web.Routing</span><span class="sxs-lookup"><span data-stu-id="535e6-110">Using System.Web.Routing Integration</span></span>  
 <span data-ttu-id="535e6-111">Použít <xref:System.Web.Routing> funkce integrace použijete <xref:System.ServiceModel.Activation.ServiceRoute> třídy vytvořit jednu nebo víc tras a přidat je do <xref:System.Web.Routing.RouteTable> v souboru Global.asax.</span><span class="sxs-lookup"><span data-stu-id="535e6-111">To use the <xref:System.Web.Routing> integration feature, you use the <xref:System.ServiceModel.Activation.ServiceRoute> class to create one or more routes and add them to the <xref:System.Web.Routing.RouteTable> in a Global.asax file.</span></span> <span data-ttu-id="535e6-112">Tyto trasy zadejte relativní identifikátory URI, který služba reaguje na.</span><span class="sxs-lookup"><span data-stu-id="535e6-112">These routes specify the relative URIs that the service responds to.</span></span> <span data-ttu-id="535e6-113">Následující příklad ukazuje, jak to provést.</span><span class="sxs-lookup"><span data-stu-id="535e6-113">The following example shows how to do this.</span></span>  
  
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
  
 <span data-ttu-id="535e6-114">To směrovat všechny požadavky s relativní identifikátor URI, který začíná s zákazníkům `Service` služby.</span><span class="sxs-lookup"><span data-stu-id="535e6-114">This routes all requests with a relative URI that begins with Customers to the `Service` service.</span></span>  
  
 <span data-ttu-id="535e6-115">V souboru Web.config je třeba přidat `System.Web.Routing.UrlRoutingModule` nastaven, `runAllManagedModulesForAllRequests` atribut `true`a přidejte `UrlRoutingHandler` obslužná rutina `<system.webServer>` element, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="535e6-115">In your Web.config file you must add the `System.Web.Routing.UrlRoutingModule` module, set the `runAllManagedModulesForAllRequests` attribute to `true`, and add the `UrlRoutingHandler` handler to the `<system.webServer>` element as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="535e6-116">Tento kód načte modul a obslužná rutina vyžaduje pro směrování.</span><span class="sxs-lookup"><span data-stu-id="535e6-116">This loads a module and handler required for routing.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="535e6-117">[Směrování](../../../../docs/framework/wcf/feature-details/routing.md).</span><span class="sxs-lookup"><span data-stu-id="535e6-117"> [Routing](../../../../docs/framework/wcf/feature-details/routing.md).</span></span> <span data-ttu-id="535e6-118">Je nutné také nastavit `aspNetCompatibilityEnabled` atribut `true` v `<serviceHostingEnvironment>` element, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="535e6-118">You must also set the `aspNetCompatibilityEnabled` attribute to `true` in the `<serviceHostingEnvironment>` element as shown in the following example.</span></span>  
  
```xml  
<system.serviceModel>  
    <serviceHostingEnvironment aspNetCompatibilityEnabled="true"/>  
        <!-- ... -->  
    </system.serviceModel>  
```  
  
 <span data-ttu-id="535e6-119">Třídu, která implementuje služby musíte povolit požadavky na kompatibilitu ASP.NET, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="535e6-119">The class that implements the service must enable ASP.NET compatibility requirements as shown in the following example.</span></span>  
  
```  
[ServiceContract]  
[AspNetCompatibilityRequirements(RequirementsMode=AspNetCompatibilityRequirementsMode.Allowed)]  
    public class Service  
    {  
        // ...  
    }  
```  
  
## <a name="see-also"></a><span data-ttu-id="535e6-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="535e6-120">See Also</span></span>  
 [<span data-ttu-id="535e6-121">Model programování webových služeb HTTP WCF</span><span class="sxs-lookup"><span data-stu-id="535e6-121">WCF Web HTTP Programming Model</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)  
 [<span data-ttu-id="535e6-122">Směrování ASP.NET</span><span class="sxs-lookup"><span data-stu-id="535e6-122">ASP.NET Routing</span></span>](http://go.microsoft.com/fwlink/?LinkId=184660)
