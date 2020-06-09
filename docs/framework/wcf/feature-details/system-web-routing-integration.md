---
title: System.Web.Routing Integration
ms.date: 03/30/2017
ms.assetid: 31fe2a4f-5c47-4e5d-8ee1-84c524609d41
ms.openlocfilehash: 059f14c94bb7502a2e4f4616ca2c5e6ac5273afa
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84600734"
---
# <a name="systemwebrouting-integration"></a><span data-ttu-id="ea4a0-102">System.Web.Routing Integration</span><span class="sxs-lookup"><span data-stu-id="ea4a0-102">System.Web.Routing Integration</span></span>
<span data-ttu-id="ea4a0-103">Při hostování služby Windows Communication Foundation (WCF) v internetové informační službě (IIS) umístíte soubor. svc do virtuálního adresáře.</span><span class="sxs-lookup"><span data-stu-id="ea4a0-103">When hosting a Windows Communication Foundation (WCF) service in Internet Information Service (IIS) you place a .svc file in the virtual directory.</span></span> <span data-ttu-id="ea4a0-104">Tento soubor. svc určuje objekt pro vytváření hostitele služby, který se má použít, i třídu, která implementuje službu.</span><span class="sxs-lookup"><span data-stu-id="ea4a0-104">This .svc file specifies the service host factory to use as well as the class that implements the service.</span></span> <span data-ttu-id="ea4a0-105">Při provádění požadavků na službu zadáte soubor. svc v identifikátoru URI, například: `http://contoso.com/EmployeeServce.svc` .</span><span class="sxs-lookup"><span data-stu-id="ea4a0-105">When making requests to the service you specify the .svc file in the URI, for example: `http://contoso.com/EmployeeServce.svc`.</span></span> <span data-ttu-id="ea4a0-106">Pro programátory, kteří napisují služby REST, není tento typ identifikátoru URI optimální.</span><span class="sxs-lookup"><span data-stu-id="ea4a0-106">For programmers writing REST services, this type of URI is not optimal.</span></span> <span data-ttu-id="ea4a0-107">Identifikátory URI pro služby REST určují konkrétní prostředek a obvykle nemají žádná rozšíření.</span><span class="sxs-lookup"><span data-stu-id="ea4a0-107">URIs for REST services specify a specific resource and normally do not have any extensions.</span></span> <span data-ttu-id="ea4a0-108"><xref:System.Web.Routing>Funkce integrace umožňuje hostovat službu WCF REST, která reaguje na identifikátory URI bez rozšíření.</span><span class="sxs-lookup"><span data-stu-id="ea4a0-108">The <xref:System.Web.Routing> integration feature allows you to host a WCF REST service that responds to URIs without an extension.</span></span> <span data-ttu-id="ea4a0-109">Další informace o směrování najdete v tématu [směrování ASP.NET](https://docs.microsoft.com/previous-versions/aspnet/cc668201(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="ea4a0-109">For more information about routing see [ASP.NET Routing](https://docs.microsoft.com/previous-versions/aspnet/cc668201(v=vs.100)).</span></span>  
  
## <a name="using-systemwebrouting-integration"></a><span data-ttu-id="ea4a0-110">Použití integrace System. Web. Routing</span><span class="sxs-lookup"><span data-stu-id="ea4a0-110">Using System.Web.Routing Integration</span></span>  
 <span data-ttu-id="ea4a0-111">Chcete-li použít <xref:System.Web.Routing> integrační funkci, použijte <xref:System.ServiceModel.Activation.ServiceRoute> třídu k vytvoření jedné nebo více tras a přidejte je do <xref:System.Web.Routing.RouteTable> souboru Global. asax.</span><span class="sxs-lookup"><span data-stu-id="ea4a0-111">To use the <xref:System.Web.Routing> integration feature, you use the <xref:System.ServiceModel.Activation.ServiceRoute> class to create one or more routes and add them to the <xref:System.Web.Routing.RouteTable> in a Global.asax file.</span></span> <span data-ttu-id="ea4a0-112">Tyto trasy určují relativní identifikátory URI, na které služba reaguje.</span><span class="sxs-lookup"><span data-stu-id="ea4a0-112">These routes specify the relative URIs that the service responds to.</span></span> <span data-ttu-id="ea4a0-113">Následující příklad ukazuje, jak to provést.</span><span class="sxs-lookup"><span data-stu-id="ea4a0-113">The following example shows how to do this.</span></span>  
  
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
  
 <span data-ttu-id="ea4a0-114">Tím se směrují všechny požadavky s relativním identifikátorem URI, který začíná zákazníky `Service` služby.</span><span class="sxs-lookup"><span data-stu-id="ea4a0-114">This routes all requests with a relative URI that begins with Customers to the `Service` service.</span></span>  
  
 <span data-ttu-id="ea4a0-115">V souboru Web. config je nutné přidat `System.Web.Routing.UrlRoutingModule` modul, nastavit `runAllManagedModulesForAllRequests` atribut na `true` a přidat `UrlRoutingHandler` obslužnou rutinu do `<system.webServer>` prvku, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="ea4a0-115">In your Web.config file you must add the `System.Web.Routing.UrlRoutingModule` module, set the `runAllManagedModulesForAllRequests` attribute to `true`, and add the `UrlRoutingHandler` handler to the `<system.webServer>` element as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="ea4a0-116">Tím se načte modul a obslužná rutina, která se vyžaduje pro směrování.</span><span class="sxs-lookup"><span data-stu-id="ea4a0-116">This loads a module and handler required for routing.</span></span> <span data-ttu-id="ea4a0-117">Další informace najdete v tématu [Směrování](routing.md).</span><span class="sxs-lookup"><span data-stu-id="ea4a0-117">For more information, see [Routing](routing.md).</span></span> <span data-ttu-id="ea4a0-118">Musíte také nastavit `aspNetCompatibilityEnabled` atribut na `true` v `<serviceHostingEnvironment>` prvku, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="ea4a0-118">You must also set the `aspNetCompatibilityEnabled` attribute to `true` in the `<serviceHostingEnvironment>` element as shown in the following example.</span></span>  
  
```xml  
<system.serviceModel>  
    <serviceHostingEnvironment aspNetCompatibilityEnabled="true"/>  
        <!-- ... -->  
    </system.serviceModel>  
```  
  
 <span data-ttu-id="ea4a0-119">Třída, která implementuje službu, musí povolit požadavky kompatibility ASP.NET, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="ea4a0-119">The class that implements the service must enable ASP.NET compatibility requirements as shown in the following example.</span></span>  
  
```csharp
[ServiceContract]  
[AspNetCompatibilityRequirements(RequirementsMode=AspNetCompatibilityRequirementsMode.Allowed)]  
    public class Service  
    {  
        // ...  
    }  
```  
  
## <a name="see-also"></a><span data-ttu-id="ea4a0-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="ea4a0-120">See also</span></span>

- [<span data-ttu-id="ea4a0-121">Programovací model webových služeb HTTP WCF</span><span class="sxs-lookup"><span data-stu-id="ea4a0-121">WCF Web HTTP Programming Model</span></span>](wcf-web-http-programming-model.md)
- <span data-ttu-id="ea4a0-122">[ASP.NET směrování](https://docs.microsoft.com/previous-versions/aspnet/cc668201(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="ea4a0-122">[ASP.NET Routing](https://docs.microsoft.com/previous-versions/aspnet/cc668201(v=vs.100))</span></span>
