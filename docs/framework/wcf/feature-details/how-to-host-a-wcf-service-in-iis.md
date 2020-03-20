---
title: 'Postupy: Hostování služby WCF v IIS'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b044b1c9-c1e5-4c9f-84d8-0f02f4537f8b
ms.openlocfilehash: 580b380a6c6349c6a4efa26e3eefe38bd660fa1b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184925"
---
# <a name="how-to-host-a-wcf-service-in-iis"></a><span data-ttu-id="d92ff-102">Postupy: Hostování služby WCF v IIS</span><span class="sxs-lookup"><span data-stu-id="d92ff-102">How to: Host a WCF Service in IIS</span></span>
<span data-ttu-id="d92ff-103">Toto téma popisuje základní kroky potřebné k vytvoření služby WCF (Windows Communication Foundation), která je hostována v Internetové informační službě (IIS).</span><span class="sxs-lookup"><span data-stu-id="d92ff-103">This topic outlines the basic steps required to create a Windows Communication Foundation (WCF) service that is hosted in Internet Information Services (IIS).</span></span> <span data-ttu-id="d92ff-104">Toto téma předpokládá, že jste se známe se sestáleji se sestálecí mise a rozumíte tomu, jak pomocí nástroje pro správu iis vytvářet a spravovat aplikace iis.</span><span class="sxs-lookup"><span data-stu-id="d92ff-104">This topic assumes you are familiar with IIS and understand how to use the IIS management tool to create and manage IIS applications.</span></span> <span data-ttu-id="d92ff-105">Další informace o službě IIS naleznete v [tématu Internetová informační služba](https://www.iis.net/).</span><span class="sxs-lookup"><span data-stu-id="d92ff-105">For more information about IIS see [Internet Information Services](https://www.iis.net/).</span></span> <span data-ttu-id="d92ff-106">Služba WCF spuštěná v prostředí služby IIS plně využívá výhod funkcí služby IIS, jako je recyklace procesů, nečinné vypnutí, monitorování stavu procesů a aktivace založená na zprávách.</span><span class="sxs-lookup"><span data-stu-id="d92ff-106">A WCF service that runs in the IIS environment takes full advantage of IIS features, such as process recycling, idle shutdown, process health monitoring, and message-based activation.</span></span> <span data-ttu-id="d92ff-107">Tato možnost hostování vyžaduje, aby byla služba IIS správně nakonfigurována, ale nevyžaduje, aby byl jako součást aplikace zapsán žádný kód pro hostování.</span><span class="sxs-lookup"><span data-stu-id="d92ff-107">This hosting option requires that IIS be properly configured, but it does not require that any hosting code be written as part of the application.</span></span> <span data-ttu-id="d92ff-108">Službu IIS můžete používat pouze s přenosem HTTP.</span><span class="sxs-lookup"><span data-stu-id="d92ff-108">You can use IIS hosting only with an HTTP transport.</span></span>  
  
 <span data-ttu-id="d92ff-109">Další informace o interakci wcf a ASP.NET naleznete v tématu [WCF Services a ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md).</span><span class="sxs-lookup"><span data-stu-id="d92ff-109">For more information about how WCF and ASP.NET interact, see [WCF Services and ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md).</span></span> <span data-ttu-id="d92ff-110">Další informace o konfiguraci zabezpečení naleznete v [tématu Zabezpečení](../../../../docs/framework/wcf/feature-details/security.md).</span><span class="sxs-lookup"><span data-stu-id="d92ff-110">For more information about configuring security, see [Security](../../../../docs/framework/wcf/feature-details/security.md).</span></span>  
  
 <span data-ttu-id="d92ff-111">Zdrojovou kopii tohoto příkladu naleznete v tématu [IIS Hosting Using Inline Code](../../../../docs/framework/wcf/samples/iis-hosting-using-inline-code.md).</span><span class="sxs-lookup"><span data-stu-id="d92ff-111">For the source copy of this example, see [IIS Hosting Using Inline Code](../../../../docs/framework/wcf/samples/iis-hosting-using-inline-code.md).</span></span>  
  
### <a name="to-create-a-service-hosted-by-iis"></a><span data-ttu-id="d92ff-112">Vytvoření služby hostované službou IIS</span><span class="sxs-lookup"><span data-stu-id="d92ff-112">To create a service hosted by IIS</span></span>  
  
1. <span data-ttu-id="d92ff-113">Zkontrolujte, zda je v počítači nainstalována a spuštěna i ii.</span><span class="sxs-lookup"><span data-stu-id="d92ff-113">Confirm that IIS is installed and running on your computer.</span></span> <span data-ttu-id="d92ff-114">Další informace o instalaci a konfiguraci služby IIS naleznete v [tématu Instalace a konfigurace služby IIS 7.0](https://docs.microsoft.com/iis/install/installing-iis-7/installing-necessary-iis-components-on-windows-vista)</span><span class="sxs-lookup"><span data-stu-id="d92ff-114">For more information about installing and configuring IIS see [Installing and Configuring IIS 7.0](https://docs.microsoft.com/iis/install/installing-iis-7/installing-necessary-iis-components-on-windows-vista)</span></span>  
  
2. <span data-ttu-id="d92ff-115">Vytvořte novou složku pro soubory aplikace s názvem "IISHostedCalcService", ujistěte se, že ASP.NET má přístup k obsahu složky a pomocí nástroje pro správu služby IIS vytvořte novou aplikaci služby IIS, která je fyzicky umístěna v tomto adresáři aplikace.</span><span class="sxs-lookup"><span data-stu-id="d92ff-115">Create a new folder for your application files called "IISHostedCalcService", ensure that ASP.NET has access to the contents of the folder, and use the IIS management tool to create a new IIS application that is physically located in this application directory.</span></span> <span data-ttu-id="d92ff-116">Při vytváření aliasu pro adresář aplikace použijte "IISHostedCalc".</span><span class="sxs-lookup"><span data-stu-id="d92ff-116">When creating an alias for the application directory use "IISHostedCalc".</span></span>  
  
3. <span data-ttu-id="d92ff-117">Vytvořte nový soubor s názvem service.svc v adresáři aplikace.</span><span class="sxs-lookup"><span data-stu-id="d92ff-117">Create a new file named "service.svc" in the application directory.</span></span> <span data-ttu-id="d92ff-118">Upravte tento soubor @ServiceHost přidáním následujícího prvku.</span><span class="sxs-lookup"><span data-stu-id="d92ff-118">Edit this file by adding the following @ServiceHost element.</span></span>  
  
   ```
   <%@ServiceHost language=c# Debug="true" Service="Microsoft.ServiceModel.Samples.CalculatorService"%>
   ```  
  
4. <span data-ttu-id="d92ff-119">Vytvořte App_Code podadresář v adresáři aplikace.</span><span class="sxs-lookup"><span data-stu-id="d92ff-119">Create an App_Code subdirectory within the application directory.</span></span>  
  
5. <span data-ttu-id="d92ff-120">Vytvořte kódový soubor s názvem Service.cs v podadresáři App_Code.</span><span class="sxs-lookup"><span data-stu-id="d92ff-120">Create a code file named Service.cs in the App_Code subdirectory.</span></span>  
  
6. <span data-ttu-id="d92ff-121">Přidejte následující příkazy pomocí do horní části souboru Service.cs.</span><span class="sxs-lookup"><span data-stu-id="d92ff-121">Add the following using statements to the top of the Service.cs file.</span></span>  
  
    ```csharp  
    using System;  
    using System.ServiceModel;  
    ```  
  
7. <span data-ttu-id="d92ff-122">Za příkazy using přidejte následující deklaraci oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="d92ff-122">Add the following namespace declaration after the using statements.</span></span>  
  
    ```csharp  
    namespace Microsoft.ServiceModel.Samples  
    {  
    }  
    ```  
  
8. <span data-ttu-id="d92ff-123">Definujte servisní smlouvu uvnitř deklarace oboru názvů, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="d92ff-123">Define the service contract inside the namespace declaration as shown in the following code.</span></span>  
  
     [!code-csharp[c_HowTo_HostInIIS#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/cs/source.cs#11)]
     [!code-vb[c_HowTo_HostInIIS#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostiniis/vb/source.vb#11)]  
  
9. <span data-ttu-id="d92ff-124">Implementujte servisní smlouvu po definici servisní smlouvy, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="d92ff-124">Implement the service contract after the service contract definition as shown in the following code.</span></span>  
  
     [!code-csharp[c_HowTo_HostInIIS#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/cs/source.cs#12)]
     [!code-vb[c_HowTo_HostInIIS#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostiniis/vb/source.vb#12)]  
  
10. <span data-ttu-id="d92ff-125">Vytvořte soubor s názvem "Web.config" v adresáři aplikace a přidejte do něj následující konfigurační kód.</span><span class="sxs-lookup"><span data-stu-id="d92ff-125">Create a file named "Web.config" in the application directory and add the following configuration code into the file.</span></span> <span data-ttu-id="d92ff-126">Za běhu wcf infrastruktury používá informace k vytvoření koncového bodu, který klientské aplikace mohou komunikovat.</span><span class="sxs-lookup"><span data-stu-id="d92ff-126">At runtime, the WCF infrastructure uses the information to construct an endpoint that client applications can communicate with.</span></span>  
  
     [!code-xml[c_HowTo_HostInIIS#100](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/common/web.config#100)]
  
     <span data-ttu-id="d92ff-127">Tento příklad explicitně určuje koncové body v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="d92ff-127">This example explicitly specifies endpoints in the configuration file.</span></span> <span data-ttu-id="d92ff-128">Pokud do služby nepřidáte žádné koncové body, runtime přidá výchozí koncové body za vás.</span><span class="sxs-lookup"><span data-stu-id="d92ff-128">If you do not add any endpoints to the service, the runtime adds default endpoints for you.</span></span> <span data-ttu-id="d92ff-129">Další informace o výchozích koncových bodech, vazbách a chováních naleznete v [tématu Zjednodušená konfigurace](../../../../docs/framework/wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="d92ff-129">For more information about default endpoints, bindings, and behaviors see [Simplified Configuration](../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
11. <span data-ttu-id="d92ff-130">Chcete-li se ujistit, že je služba hostována správně, otevřete instanci aplikace Internet Explorer a přejděte na adresu URL služby:`http://localhost/IISHostedCalc/Service.svc`</span><span class="sxs-lookup"><span data-stu-id="d92ff-130">To make sure the service is hosted correctly, open an instance of Internet Explorer and browse to the service's URL: `http://localhost/IISHostedCalc/Service.svc`</span></span>  
  
## <a name="example"></a><span data-ttu-id="d92ff-131">Příklad</span><span class="sxs-lookup"><span data-stu-id="d92ff-131">Example</span></span>  
 <span data-ttu-id="d92ff-132">Následuje úplný seznam kódu služby Kalkulačka hostovaná službou IIS.</span><span class="sxs-lookup"><span data-stu-id="d92ff-132">The following is a complete listing of the code for the IIS hosted calculator service.</span></span>  
  
 [!code-csharp[C_HowTo_HostInIIS#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/cs/source.cs#1)]
 [!code-vb[C_HowTo_HostInIIS#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostiniis/vb/source.vb#1)]
 [!code-xml[c_HowTo_HostInIIS#100](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/common/web.config#100)]  
  
## <a name="see-also"></a><span data-ttu-id="d92ff-133">Viz také</span><span class="sxs-lookup"><span data-stu-id="d92ff-133">See also</span></span>

- [<span data-ttu-id="d92ff-134">Hostování v Internetové informační službě</span><span class="sxs-lookup"><span data-stu-id="d92ff-134">Hosting in Internet Information Services</span></span>](../../../../docs/framework/wcf/feature-details/hosting-in-internet-information-services.md)
- [<span data-ttu-id="d92ff-135">Služby hostování</span><span class="sxs-lookup"><span data-stu-id="d92ff-135">Hosting Services</span></span>](../../../../docs/framework/wcf/hosting-services.md)
- [<span data-ttu-id="d92ff-136">Služby WCF a ASP.NET</span><span class="sxs-lookup"><span data-stu-id="d92ff-136">WCF Services and ASP.NET</span></span>](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md)
- [<span data-ttu-id="d92ff-137">Zabezpečení</span><span class="sxs-lookup"><span data-stu-id="d92ff-137">Security</span></span>](../../../../docs/framework/wcf/feature-details/security.md)
- <span data-ttu-id="d92ff-138">[Funkce hostování prostředků pro aplikace systému Windows Server](https://docs.microsoft.com/previous-versions/appfabric/ee677189(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="d92ff-138">[Windows Server App Fabric Hosting Features](https://docs.microsoft.com/previous-versions/appfabric/ee677189(v=azure.10))</span></span>
