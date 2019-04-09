---
title: System.Web.Routing Integration
ms.date: 03/30/2017
ms.assetid: 31fe2a4f-5c47-4e5d-8ee1-84c524609d41
ms.openlocfilehash: 3d5c3d7586189e0939fd52bc2b5feac51ae00613
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59097509"
---
# <a name="systemwebrouting-integration"></a><span data-ttu-id="6b87d-102">System.Web.Routing Integration</span><span class="sxs-lookup"><span data-stu-id="6b87d-102">System.Web.Routing Integration</span></span>
<span data-ttu-id="6b87d-103">Při hostování služby Windows Communication Foundation (WCF) v Internetové informační služby (IIS) umístíte souborů .svc ve virtuálním adresáři.</span><span class="sxs-lookup"><span data-stu-id="6b87d-103">When hosting a Windows Communication Foundation (WCF) service in Internet Information Service (IIS) you place a .svc file in the virtual directory.</span></span> <span data-ttu-id="6b87d-104">Tento soubor SVC určuje vytváření hostitele služby používat stejně jako třídy, která implementuje služby.</span><span class="sxs-lookup"><span data-stu-id="6b87d-104">This .svc file specifies the service host factory to use as well as the class that implements the service.</span></span> <span data-ttu-id="6b87d-105">Při zasílání požadavků na službu zadáte souboru SVC v identifikátoru URI, například: `http://contoso.com/EmployeeServce.svc`.</span><span class="sxs-lookup"><span data-stu-id="6b87d-105">When making requests to the service you specify the .svc file in the URI, for example: `http://contoso.com/EmployeeServce.svc`.</span></span> <span data-ttu-id="6b87d-106">Tento typ identifikátoru URI pro programátory, kteří vytvářejí služby REST není ideální.</span><span class="sxs-lookup"><span data-stu-id="6b87d-106">For programmers writing REST services this type of URI is not optimal.</span></span> <span data-ttu-id="6b87d-107">Identifikátory URI pro služby REST zadejte konkrétní prostředek a obvykle nemají žádná rozšíření.</span><span class="sxs-lookup"><span data-stu-id="6b87d-107">URIs for REST services specify a specific resource and normally do not have any extensions.</span></span> <span data-ttu-id="6b87d-108"><xref:System.Web.Routing> Funkci integrace umožňuje, můžete použít k hostování služby WCF REST, která bude reagovat na identifikátory URI bez přípony.</span><span class="sxs-lookup"><span data-stu-id="6b87d-108">The <xref:System.Web.Routing> integration feature allows you to host a WCF REST service that responds to URIs without an extension.</span></span> <span data-ttu-id="6b87d-109">Další informace o směrování najdete v tématu [směrování ASP.NET](https://go.microsoft.com/fwlink/?LinkId=184660).</span><span class="sxs-lookup"><span data-stu-id="6b87d-109">For more information about routing see [ASP.NET Routing](https://go.microsoft.com/fwlink/?LinkId=184660).</span></span>  
  
## <a name="using-systemwebrouting-integration"></a><span data-ttu-id="6b87d-110">Pomocí integrace System.Web.Routing</span><span class="sxs-lookup"><span data-stu-id="6b87d-110">Using System.Web.Routing Integration</span></span>  
 <span data-ttu-id="6b87d-111">Použít <xref:System.Web.Routing> funkci integrace, je použít <xref:System.ServiceModel.Activation.ServiceRoute> třídy k vytvoření jednoho nebo více tras a přidat je do <xref:System.Web.Routing.RouteTable> v souboru Global.asax.</span><span class="sxs-lookup"><span data-stu-id="6b87d-111">To use the <xref:System.Web.Routing> integration feature, you use the <xref:System.ServiceModel.Activation.ServiceRoute> class to create one or more routes and add them to the <xref:System.Web.Routing.RouteTable> in a Global.asax file.</span></span> <span data-ttu-id="6b87d-112">Tyto trasy zadejte relativní identifikátory URI, které služby jsou reaguje na.</span><span class="sxs-lookup"><span data-stu-id="6b87d-112">These routes specify the relative URIs that the service responds to.</span></span> <span data-ttu-id="6b87d-113">Následující příklad ukazuje, jak to provést.</span><span class="sxs-lookup"><span data-stu-id="6b87d-113">The following example shows how to do this.</span></span>  
  
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
  
 <span data-ttu-id="6b87d-114">Ten přesměruje všechny požadavky s relativní identifikátor URI, který začíná s zákazníkům `Service` služby.</span><span class="sxs-lookup"><span data-stu-id="6b87d-114">This routes all requests with a relative URI that begins with Customers to the `Service` service.</span></span>  
  
 <span data-ttu-id="6b87d-115">V souboru Web.config musíte přidat `System.Web.Routing.UrlRoutingModule` modul, nastavte `runAllManagedModulesForAllRequests` atribut `true`a přidejte `UrlRoutingHandler` obslužná rutina `<system.webServer>` elementu, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="6b87d-115">In your Web.config file you must add the `System.Web.Routing.UrlRoutingModule` module, set the `runAllManagedModulesForAllRequests` attribute to `true`, and add the `UrlRoutingHandler` handler to the `<system.webServer>` element as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="6b87d-116">Tento kód načte modul a obslužná rutina vyžaduje pro směrování.</span><span class="sxs-lookup"><span data-stu-id="6b87d-116">This loads a module and handler required for routing.</span></span> <span data-ttu-id="6b87d-117">Další informace najdete v tématu [směrování](../../../../docs/framework/wcf/feature-details/routing.md).</span><span class="sxs-lookup"><span data-stu-id="6b87d-117">For more information, see [Routing](../../../../docs/framework/wcf/feature-details/routing.md).</span></span> <span data-ttu-id="6b87d-118">Musíte taky nastavit `aspNetCompatibilityEnabled` atribut `true` v `<serviceHostingEnvironment>` elementu, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="6b87d-118">You must also set the `aspNetCompatibilityEnabled` attribute to `true` in the `<serviceHostingEnvironment>` element as shown in the following example.</span></span>  
  
```xml  
<system.serviceModel>  
    <serviceHostingEnvironment aspNetCompatibilityEnabled="true"/>  
        <!-- ... -->  
    </system.serviceModel>  
```  
  
 <span data-ttu-id="6b87d-119">Třídy, která implementuje službu musíte povolit požadavky kompatibility ASP.NET, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="6b87d-119">The class that implements the service must enable ASP.NET compatibility requirements as shown in the following example.</span></span>  
  
```  
[ServiceContract]  
[AspNetCompatibilityRequirements(RequirementsMode=AspNetCompatibilityRequirementsMode.Allowed)]  
    public class Service  
    {  
        // ...  
    }  
```  
  
## <a name="see-also"></a><span data-ttu-id="6b87d-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6b87d-120">See also</span></span>

- [<span data-ttu-id="6b87d-121">Model programování webových služeb HTTP WCF</span><span class="sxs-lookup"><span data-stu-id="6b87d-121">WCF Web HTTP Programming Model</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
- [<span data-ttu-id="6b87d-122">ASP.NET Routing</span><span class="sxs-lookup"><span data-stu-id="6b87d-122">ASP.NET Routing</span></span>](https://go.microsoft.com/fwlink/?LinkId=184660)
