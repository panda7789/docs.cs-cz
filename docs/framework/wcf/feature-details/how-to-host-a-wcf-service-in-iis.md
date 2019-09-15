---
title: 'Postupy: Hostování služby WCF v IIS'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b044b1c9-c1e5-4c9f-84d8-0f02f4537f8b
ms.openlocfilehash: ad1fb7d289dea3396b4edb4d3b3e9fb7fb1891e3
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/13/2019
ms.locfileid: "70972412"
---
# <a name="how-to-host-a-wcf-service-in-iis"></a><span data-ttu-id="2df69-102">Postupy: Hostování služby WCF v IIS</span><span class="sxs-lookup"><span data-stu-id="2df69-102">How to: Host a WCF Service in IIS</span></span>
<span data-ttu-id="2df69-103">Toto téma popisuje základní kroky potřebné k vytvoření služby Windows Communication Foundation (WCF), která je hostovaná v Internetová informační služba (IIS).</span><span class="sxs-lookup"><span data-stu-id="2df69-103">This topic outlines the basic steps required to create a Windows Communication Foundation (WCF) service that is hosted in Internet Information Services (IIS).</span></span> <span data-ttu-id="2df69-104">V tomto tématu se předpokládá, že jste obeznámeni se službou IIS a rozumíte tomu, jak pomocí nástroje pro správu služby IIS vytvářet a spravovat aplikace IIS.</span><span class="sxs-lookup"><span data-stu-id="2df69-104">This topic assumes you are familiar with IIS and understand how to use the IIS management tool to create and manage IIS applications.</span></span> <span data-ttu-id="2df69-105">Další informace o službě IIS najdete v tématu [Internetová informační služba](https://go.microsoft.com/fwlink/?LinkId=132449).</span><span class="sxs-lookup"><span data-stu-id="2df69-105">For more information about IIS see [Internet Information Services](https://go.microsoft.com/fwlink/?LinkId=132449).</span></span> <span data-ttu-id="2df69-106">Služba WCF, která běží v prostředí služby IIS, má plně výhodu funkcí služby IIS, jako je recyklace procesů, nečinné vypnutí, monitorování stavu procesu a aktivace na základě zpráv.</span><span class="sxs-lookup"><span data-stu-id="2df69-106">A WCF service that runs in the IIS environment takes full advantage of IIS features, such as process recycling, idle shutdown, process health monitoring, and message-based activation.</span></span> <span data-ttu-id="2df69-107">Tato možnost hostování vyžaduje, aby služba IIS byla správně nakonfigurovaná, ale nevyžaduje, aby se veškerý hostitelský kód napsal jako součást aplikace.</span><span class="sxs-lookup"><span data-stu-id="2df69-107">This hosting option requires that IIS be properly configured, but it does not require that any hosting code be written as part of the application.</span></span> <span data-ttu-id="2df69-108">Službu IIS můžete použít jenom s přenosem HTTP.</span><span class="sxs-lookup"><span data-stu-id="2df69-108">You can use IIS hosting only with an HTTP transport.</span></span>  
  
 <span data-ttu-id="2df69-109">Další informace o tom, jak WCF a ASP.NET spolupracují, najdete v tématu [služby WCF a ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md).</span><span class="sxs-lookup"><span data-stu-id="2df69-109">For more information about how WCF and ASP.NET interact, see [WCF Services and ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md).</span></span> <span data-ttu-id="2df69-110">Další informace o konfiguraci zabezpečení najdete v tématu [zabezpečení](../../../../docs/framework/wcf/feature-details/security.md).</span><span class="sxs-lookup"><span data-stu-id="2df69-110">For more information about configuring security, see [Security](../../../../docs/framework/wcf/feature-details/security.md).</span></span>  
  
 <span data-ttu-id="2df69-111">Zdrojovou kopii tohoto příkladu naleznete v tématu [hostování služby IIS pomocí vloženého kódu](../../../../docs/framework/wcf/samples/iis-hosting-using-inline-code.md).</span><span class="sxs-lookup"><span data-stu-id="2df69-111">For the source copy of this example, see [IIS Hosting Using Inline Code](../../../../docs/framework/wcf/samples/iis-hosting-using-inline-code.md).</span></span>  
  
### <a name="to-create-a-service-hosted-by-iis"></a><span data-ttu-id="2df69-112">Vytvoření služby hostované službou IIS</span><span class="sxs-lookup"><span data-stu-id="2df69-112">To create a service hosted by IIS</span></span>  
  
1. <span data-ttu-id="2df69-113">Ověřte, že je služba IIS v počítači nainstalovaná a spuštěná.</span><span class="sxs-lookup"><span data-stu-id="2df69-113">Confirm that IIS is installed and running on your computer.</span></span> <span data-ttu-id="2df69-114">Další informace o instalaci a konfiguraci služby IIS najdete v tématu [instalace a konfigurace služby iis 7,0](https://go.microsoft.com/fwlink/?LinkID=132128) .</span><span class="sxs-lookup"><span data-stu-id="2df69-114">For more information about installing and configuring IIS see [Installing and Configuring IIS 7.0](https://go.microsoft.com/fwlink/?LinkID=132128)</span></span>  
  
2. <span data-ttu-id="2df69-115">Vytvořte novou složku pro soubory aplikace nazvané "IISHostedCalcService", ujistěte se, že ASP.NET má přístup k obsahu složky, a pomocí nástroje pro správu služby IIS vytvořte novou aplikaci IIS, která je fyzicky umístěná v tomto adresáři aplikace.</span><span class="sxs-lookup"><span data-stu-id="2df69-115">Create a new folder for your application files called "IISHostedCalcService", ensure that ASP.NET has access to the contents of the folder, and use the IIS management tool to create a new IIS application that is physically located in this application directory.</span></span> <span data-ttu-id="2df69-116">Při vytváření aliasu pro adresář aplikace použijte "IISHostedCalc".</span><span class="sxs-lookup"><span data-stu-id="2df69-116">When creating an alias for the application directory use "IISHostedCalc".</span></span>  
  
3. <span data-ttu-id="2df69-117">V adresáři aplikace vytvořte nový soubor s názvem Service. svc.</span><span class="sxs-lookup"><span data-stu-id="2df69-117">Create a new file named "service.svc" in the application directory.</span></span> <span data-ttu-id="2df69-118">Upravte tento soubor přidáním následujícího @ServiceHost elementu.</span><span class="sxs-lookup"><span data-stu-id="2df69-118">Edit this file by adding the following @ServiceHost element.</span></span>  
  
   ```
   <%@ServiceHost language=c# Debug="true" Service="Microsoft.ServiceModel.Samples.CalculatorService"%>
   ```  
  
4. <span data-ttu-id="2df69-119">Vytvořte podadresář App_Code v adresáři aplikace.</span><span class="sxs-lookup"><span data-stu-id="2df69-119">Create an App_Code subdirectory within the application directory.</span></span>  
  
5. <span data-ttu-id="2df69-120">V podadresáři App_Code vytvořte soubor kódu s názvem Service.cs.</span><span class="sxs-lookup"><span data-stu-id="2df69-120">Create a code file named Service.cs in the App_Code subdirectory.</span></span>  
  
6. <span data-ttu-id="2df69-121">Do horní části souboru Service.cs přidejte následující příkazy using.</span><span class="sxs-lookup"><span data-stu-id="2df69-121">Add the following using statements to the top of the Service.cs file.</span></span>  
  
    ```csharp  
    using System;  
    using System.ServiceModel;  
    ```  
  
7. <span data-ttu-id="2df69-122">Po příkazech using přidejte následující deklaraci oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="2df69-122">Add the following namespace declaration after the using statements.</span></span>  
  
    ```csharp  
    namespace Microsoft.ServiceModel.Samples  
    {  
    }  
    ```  
  
8. <span data-ttu-id="2df69-123">Definujte kontrakt služby uvnitř deklarace oboru názvů, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="2df69-123">Define the service contract inside the namespace declaration as shown in the following code.</span></span>  
  
     [!code-csharp[c_HowTo_HostInIIS#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/cs/source.cs#11)]
     [!code-vb[c_HowTo_HostInIIS#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostiniis/vb/source.vb#11)]  
  
9. <span data-ttu-id="2df69-124">Po definici kontraktu služby, jak je znázorněno v následujícím kódu, implementujte kontrakt služby.</span><span class="sxs-lookup"><span data-stu-id="2df69-124">Implement the service contract after the service contract definition as shown in the following code.</span></span>  
  
     [!code-csharp[c_HowTo_HostInIIS#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/cs/source.cs#12)]
     [!code-vb[c_HowTo_HostInIIS#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostiniis/vb/source.vb#12)]  
  
10. <span data-ttu-id="2df69-125">Vytvořte soubor s názvem Web. config v adresáři aplikace a přidejte do souboru následující konfigurační kód.</span><span class="sxs-lookup"><span data-stu-id="2df69-125">Create a file named "Web.config" in the application directory and add the following configuration code into the file.</span></span> <span data-ttu-id="2df69-126">Infrastruktura WCF za běhu používá informace k vytvoření koncového bodu, se kterým můžou klientské aplikace komunikovat.</span><span class="sxs-lookup"><span data-stu-id="2df69-126">At runtime, the WCF infrastructure uses the information to construct an endpoint that client applications can communicate with.</span></span>  
  
     [!code-xml[c_HowTo_HostInIIS#100](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/common/web.config#100)]      
  
     <span data-ttu-id="2df69-127">Tento příklad explicitně určuje koncové body v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="2df69-127">This example explicitly specifies endpoints in the configuration file.</span></span> <span data-ttu-id="2df69-128">Pokud do služby nepřidáte žádné koncové body, modul runtime přidá pro vás výchozí koncové body.</span><span class="sxs-lookup"><span data-stu-id="2df69-128">If you do not add any endpoints to the service, the runtime adds default endpoints for you.</span></span> <span data-ttu-id="2df69-129">Další informace o výchozích koncových bodech, vazbách a chování najdete v tématu [zjednodušená konfigurace](../../../../docs/framework/wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="2df69-129">For more information about default endpoints, bindings, and behaviors see [Simplified Configuration](../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
11. <span data-ttu-id="2df69-130">Abyste se ujistili, že je služba hostovaná správně, otevřete instanci aplikace Internet Explorer a přejděte na adresu URL služby:`http://localhost/IISHostedCalc/Service.svc`</span><span class="sxs-lookup"><span data-stu-id="2df69-130">To make sure the service is hosted correctly, open an instance of Internet Explorer and browse to the service's URL: `http://localhost/IISHostedCalc/Service.svc`</span></span>  
  
## <a name="example"></a><span data-ttu-id="2df69-131">Příklad</span><span class="sxs-lookup"><span data-stu-id="2df69-131">Example</span></span>  
 <span data-ttu-id="2df69-132">Následuje úplný seznam kódu pro službu IIS Hosted Kalkulačka.</span><span class="sxs-lookup"><span data-stu-id="2df69-132">The following is a complete listing of the code for the IIS hosted calculator service.</span></span>  
  
 [!code-csharp[C_HowTo_HostInIIS#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/cs/source.cs#1)] 
 [!code-vb[C_HowTo_HostInIIS#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostiniis/vb/source.vb#1)] 
 [!code-xml[c_HowTo_HostInIIS#100](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/common/web.config#100)]  
  
## <a name="see-also"></a><span data-ttu-id="2df69-133">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2df69-133">See also</span></span>

- [<span data-ttu-id="2df69-134">Hostování v Internetové informační službě</span><span class="sxs-lookup"><span data-stu-id="2df69-134">Hosting in Internet Information Services</span></span>](../../../../docs/framework/wcf/feature-details/hosting-in-internet-information-services.md)
- [<span data-ttu-id="2df69-135">Služby hostování</span><span class="sxs-lookup"><span data-stu-id="2df69-135">Hosting Services</span></span>](../../../../docs/framework/wcf/hosting-services.md)
- [<span data-ttu-id="2df69-136">Služby WCF a ASP.NET</span><span class="sxs-lookup"><span data-stu-id="2df69-136">WCF Services and ASP.NET</span></span>](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md)
- [<span data-ttu-id="2df69-137">Zabezpečení</span><span class="sxs-lookup"><span data-stu-id="2df69-137">Security</span></span>](../../../../docs/framework/wcf/feature-details/security.md)
- [<span data-ttu-id="2df69-138">Funkce hostování technologie Windows Server App Fabric</span><span class="sxs-lookup"><span data-stu-id="2df69-138">Windows Server App Fabric Hosting Features</span></span>](https://go.microsoft.com/fwlink/?LinkId=201276)
