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
# <a name="systemwebrouting-integration"></a><span data-ttu-id="2b248-102">System.Web.Routing Integration</span><span class="sxs-lookup"><span data-stu-id="2b248-102">System.Web.Routing Integration</span></span>
<span data-ttu-id="2b248-103">Při hostování služby Windows Communication Foundation (WCF) v internetové informační službě (IIS) umístíte soubor. svc do virtuálního adresáře.</span><span class="sxs-lookup"><span data-stu-id="2b248-103">When hosting a Windows Communication Foundation (WCF) service in Internet Information Service (IIS) you place a .svc file in the virtual directory.</span></span> <span data-ttu-id="2b248-104">Tento soubor. svc určuje objekt pro vytváření hostitele služby, který se má použít, i třídu, která implementuje službu.</span><span class="sxs-lookup"><span data-stu-id="2b248-104">This .svc file specifies the service host factory to use as well as the class that implements the service.</span></span> <span data-ttu-id="2b248-105">Při provádění požadavků na službu zadáte soubor. svc v identifikátoru URI, například: `http://contoso.com/EmployeeServce.svc`.</span><span class="sxs-lookup"><span data-stu-id="2b248-105">When making requests to the service you specify the .svc file in the URI, for example: `http://contoso.com/EmployeeServce.svc`.</span></span> <span data-ttu-id="2b248-106">Pro programátory, kteří píší služby REST, tento typ identifikátoru URI není optimální.</span><span class="sxs-lookup"><span data-stu-id="2b248-106">For programmers writing REST services this type of URI is not optimal.</span></span> <span data-ttu-id="2b248-107">Identifikátory URI pro služby REST určují konkrétní prostředek a obvykle nemají žádná rozšíření.</span><span class="sxs-lookup"><span data-stu-id="2b248-107">URIs for REST services specify a specific resource and normally do not have any extensions.</span></span> <span data-ttu-id="2b248-108">Funkce integrace <xref:System.Web.Routing> umožňuje hostovat službu WCF REST, která reaguje na identifikátory URI bez rozšíření.</span><span class="sxs-lookup"><span data-stu-id="2b248-108">The <xref:System.Web.Routing> integration feature allows you to host a WCF REST service that responds to URIs without an extension.</span></span> <span data-ttu-id="2b248-109">Další informace o směrování najdete v tématu [směrování ASP.NET](https://go.microsoft.com/fwlink/?LinkId=184660).</span><span class="sxs-lookup"><span data-stu-id="2b248-109">For more information about routing see [ASP.NET Routing](https://go.microsoft.com/fwlink/?LinkId=184660).</span></span>  
  
## <a name="using-systemwebrouting-integration"></a><span data-ttu-id="2b248-110">Použití integrace System. Web. Routing</span><span class="sxs-lookup"><span data-stu-id="2b248-110">Using System.Web.Routing Integration</span></span>  
 <span data-ttu-id="2b248-111">Chcete-li použít funkci <xref:System.Web.Routing> Integration, použijte třídu <xref:System.ServiceModel.Activation.ServiceRoute> k vytvoření jedné nebo více tras a přidejte je do <xref:System.Web.Routing.RouteTable> v souboru Global. asax.</span><span class="sxs-lookup"><span data-stu-id="2b248-111">To use the <xref:System.Web.Routing> integration feature, you use the <xref:System.ServiceModel.Activation.ServiceRoute> class to create one or more routes and add them to the <xref:System.Web.Routing.RouteTable> in a Global.asax file.</span></span> <span data-ttu-id="2b248-112">Tyto trasy určují relativní identifikátory URI, na které služba reaguje.</span><span class="sxs-lookup"><span data-stu-id="2b248-112">These routes specify the relative URIs that the service responds to.</span></span> <span data-ttu-id="2b248-113">Následující příklad ukazuje, jak to provést.</span><span class="sxs-lookup"><span data-stu-id="2b248-113">The following example shows how to do this.</span></span>  
  
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
  
 <span data-ttu-id="2b248-114">Tím se směrují všechny požadavky s relativním identifikátorem URI, který začíná zákazníky služby `Service`.</span><span class="sxs-lookup"><span data-stu-id="2b248-114">This routes all requests with a relative URI that begins with Customers to the `Service` service.</span></span>  
  
 <span data-ttu-id="2b248-115">V souboru Web. config je nutné přidat modul `System.Web.Routing.UrlRoutingModule`, nastavit atribut `runAllManagedModulesForAllRequests` na `true`a přidat obslužnou rutinu `UrlRoutingHandler` do prvku `<system.webServer>`, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="2b248-115">In your Web.config file you must add the `System.Web.Routing.UrlRoutingModule` module, set the `runAllManagedModulesForAllRequests` attribute to `true`, and add the `UrlRoutingHandler` handler to the `<system.webServer>` element as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="2b248-116">Tím se načte modul a obslužná rutina, která se vyžaduje pro směrování.</span><span class="sxs-lookup"><span data-stu-id="2b248-116">This loads a module and handler required for routing.</span></span> <span data-ttu-id="2b248-117">Další informace najdete v tématu [Směrování](../../../../docs/framework/wcf/feature-details/routing.md).</span><span class="sxs-lookup"><span data-stu-id="2b248-117">For more information, see [Routing](../../../../docs/framework/wcf/feature-details/routing.md).</span></span> <span data-ttu-id="2b248-118">Musíte také nastavit atribut `aspNetCompatibilityEnabled`, aby `true` v prvku `<serviceHostingEnvironment>`, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="2b248-118">You must also set the `aspNetCompatibilityEnabled` attribute to `true` in the `<serviceHostingEnvironment>` element as shown in the following example.</span></span>  
  
```xml  
<system.serviceModel>  
    <serviceHostingEnvironment aspNetCompatibilityEnabled="true"/>  
        <!-- ... -->  
    </system.serviceModel>  
```  
  
 <span data-ttu-id="2b248-119">Třída, která implementuje službu, musí povolit požadavky kompatibility ASP.NET, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="2b248-119">The class that implements the service must enable ASP.NET compatibility requirements as shown in the following example.</span></span>  
  
```csharp 
[ServiceContract]  
[AspNetCompatibilityRequirements(RequirementsMode=AspNetCompatibilityRequirementsMode.Allowed)]  
    public class Service  
    {  
        // ...  
    }  
```  
  
## <a name="see-also"></a><span data-ttu-id="2b248-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2b248-120">See also</span></span>

- [<span data-ttu-id="2b248-121">Programovací model webových služeb HTTP WCF</span><span class="sxs-lookup"><span data-stu-id="2b248-121">WCF Web HTTP Programming Model</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
- [<span data-ttu-id="2b248-122">ASP.NET směrování</span><span class="sxs-lookup"><span data-stu-id="2b248-122">ASP.NET Routing</span></span>](https://go.microsoft.com/fwlink/?LinkId=184660)
