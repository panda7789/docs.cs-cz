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
# <a name="systemwebrouting-integration"></a><span data-ttu-id="46414-102">System.Web.Routing Integration</span><span class="sxs-lookup"><span data-stu-id="46414-102">System.Web.Routing Integration</span></span>
<span data-ttu-id="46414-103">Při hostování služby WCF (Windows Communication Foundation) v Internetové informační službě (IIS) umístíte soubor SVC do virtuálního adresáře.</span><span class="sxs-lookup"><span data-stu-id="46414-103">When hosting a Windows Communication Foundation (WCF) service in Internet Information Service (IIS) you place a .svc file in the virtual directory.</span></span> <span data-ttu-id="46414-104">Tento soubor SVC určuje hostitelskou továrnu služby, která má být používána, a také třídu, která službu implementuje.</span><span class="sxs-lookup"><span data-stu-id="46414-104">This .svc file specifies the service host factory to use as well as the class that implements the service.</span></span> <span data-ttu-id="46414-105">Při vytváření požadavků na službu zadáte soubor .svc v `http://contoso.com/EmployeeServce.svc`identifikátoru URI, například: .</span><span class="sxs-lookup"><span data-stu-id="46414-105">When making requests to the service you specify the .svc file in the URI, for example: `http://contoso.com/EmployeeServce.svc`.</span></span> <span data-ttu-id="46414-106">Pro programátory, kteří píší služby REST, není tento typ identifikátoru URI optimální.</span><span class="sxs-lookup"><span data-stu-id="46414-106">For programmers writing REST services, this type of URI is not optimal.</span></span> <span data-ttu-id="46414-107">Identifikátory URI pro služby REST určují konkrétní prostředek a obvykle nemají žádná rozšíření.</span><span class="sxs-lookup"><span data-stu-id="46414-107">URIs for REST services specify a specific resource and normally do not have any extensions.</span></span> <span data-ttu-id="46414-108">Funkce <xref:System.Web.Routing> integrace umožňuje hostovat službu WCF REST, která reaguje na identifikátory URI bez rozšíření.</span><span class="sxs-lookup"><span data-stu-id="46414-108">The <xref:System.Web.Routing> integration feature allows you to host a WCF REST service that responds to URIs without an extension.</span></span> <span data-ttu-id="46414-109">Další informace o směrování naleznete [v tématu ASP.NET Routing](https://docs.microsoft.com/previous-versions/aspnet/cc668201(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="46414-109">For more information about routing see [ASP.NET Routing](https://docs.microsoft.com/previous-versions/aspnet/cc668201(v=vs.100)).</span></span>  
  
## <a name="using-systemwebrouting-integration"></a><span data-ttu-id="46414-110">Použití integrace System.Web.Routing</span><span class="sxs-lookup"><span data-stu-id="46414-110">Using System.Web.Routing Integration</span></span>  
 <span data-ttu-id="46414-111">Chcete-li <xref:System.Web.Routing> použít funkci integrace, použijte třídu <xref:System.ServiceModel.Activation.ServiceRoute> k vytvoření jedné <xref:System.Web.Routing.RouteTable> nebo více tras a jejich přidání do souboru Global.asax.</span><span class="sxs-lookup"><span data-stu-id="46414-111">To use the <xref:System.Web.Routing> integration feature, you use the <xref:System.ServiceModel.Activation.ServiceRoute> class to create one or more routes and add them to the <xref:System.Web.Routing.RouteTable> in a Global.asax file.</span></span> <span data-ttu-id="46414-112">Tyto trasy určují relativní identifikátory URI, na které služba reaguje.</span><span class="sxs-lookup"><span data-stu-id="46414-112">These routes specify the relative URIs that the service responds to.</span></span> <span data-ttu-id="46414-113">Následující příklad ukazuje, jak to provést.</span><span class="sxs-lookup"><span data-stu-id="46414-113">The following example shows how to do this.</span></span>  
  
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
  
 <span data-ttu-id="46414-114">To směruje všechny požadavky s relativní URI, který `Service` začíná zákazníci ke službě.</span><span class="sxs-lookup"><span data-stu-id="46414-114">This routes all requests with a relative URI that begins with Customers to the `Service` service.</span></span>  
  
 <span data-ttu-id="46414-115">V souboru Web.config musíte `System.Web.Routing.UrlRoutingModule` přidat `runAllManagedModulesForAllRequests` modul, `true`nastavit atribut `UrlRoutingHandler` na aplikaci a přidat obslužnou rutinu `<system.webServer>` k prvku, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="46414-115">In your Web.config file you must add the `System.Web.Routing.UrlRoutingModule` module, set the `runAllManagedModulesForAllRequests` attribute to `true`, and add the `UrlRoutingHandler` handler to the `<system.webServer>` element as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="46414-116">Tím se načte modul a obslužná rutina potřebná pro směrování.</span><span class="sxs-lookup"><span data-stu-id="46414-116">This loads a module and handler required for routing.</span></span> <span data-ttu-id="46414-117">Další informace naleznete v tématu [Směrování](../../../../docs/framework/wcf/feature-details/routing.md).</span><span class="sxs-lookup"><span data-stu-id="46414-117">For more information, see [Routing](../../../../docs/framework/wcf/feature-details/routing.md).</span></span> <span data-ttu-id="46414-118">Je také nutné `aspNetCompatibilityEnabled` nastavit `true` atribut `<serviceHostingEnvironment>` v prvku, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="46414-118">You must also set the `aspNetCompatibilityEnabled` attribute to `true` in the `<serviceHostingEnvironment>` element as shown in the following example.</span></span>  
  
```xml  
<system.serviceModel>  
    <serviceHostingEnvironment aspNetCompatibilityEnabled="true"/>  
        <!-- ... -->  
    </system.serviceModel>  
```  
  
 <span data-ttu-id="46414-119">Třída, která implementuje službu musí povolit ASP.NET požadavky na kompatibilitu, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="46414-119">The class that implements the service must enable ASP.NET compatibility requirements as shown in the following example.</span></span>  
  
```csharp
[ServiceContract]  
[AspNetCompatibilityRequirements(RequirementsMode=AspNetCompatibilityRequirementsMode.Allowed)]  
    public class Service  
    {  
        // ...  
    }  
```  
  
## <a name="see-also"></a><span data-ttu-id="46414-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="46414-120">See also</span></span>

- [<span data-ttu-id="46414-121">Programovací model webových služeb HTTP WCF</span><span class="sxs-lookup"><span data-stu-id="46414-121">WCF Web HTTP Programming Model</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
- <span data-ttu-id="46414-122">[ASP.NET směrování](https://docs.microsoft.com/previous-versions/aspnet/cc668201(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="46414-122">[ASP.NET Routing](https://docs.microsoft.com/previous-versions/aspnet/cc668201(v=vs.100))</span></span>
