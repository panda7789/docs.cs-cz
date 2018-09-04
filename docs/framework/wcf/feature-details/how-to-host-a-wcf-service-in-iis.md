---
title: 'Postupy: Hostování služby WCF v IIS'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b044b1c9-c1e5-4c9f-84d8-0f02f4537f8b
ms.openlocfilehash: 207010f594959708322aed2e630935252c873cf8
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43510752"
---
# <a name="how-to-host-a-wcf-service-in-iis"></a><span data-ttu-id="fd847-102">Postupy: Hostování služby WCF v IIS</span><span class="sxs-lookup"><span data-stu-id="fd847-102">How to: Host a WCF Service in IIS</span></span>
<span data-ttu-id="fd847-103">Toto téma popisuje základní kroky potřebné k vytvoření služby Windows Communication Foundation (WCF), které je hostované v Internetové informační služby (IIS).</span><span class="sxs-lookup"><span data-stu-id="fd847-103">This topic outlines the basic steps required to create a Windows Communication Foundation (WCF) service that is hosted in Internet Information Services (IIS).</span></span> <span data-ttu-id="fd847-104">Toto téma předpokládá se seznámíte se službou IIS a pochopit, jak vytvářet a spravovat aplikace služby IIS pomocí nástroje pro správu služby IIS.</span><span class="sxs-lookup"><span data-stu-id="fd847-104">This topic assumes you are familiar with IIS and understand how to use the IIS management tool to create and manage IIS applications.</span></span> <span data-ttu-id="fd847-105">Další informace o službě IIS najdete v části [Internetová informační služba](https://go.microsoft.com/fwlink/?LinkId=132449).</span><span class="sxs-lookup"><span data-stu-id="fd847-105">For more information about IIS see [Internet Information Services](https://go.microsoft.com/fwlink/?LinkId=132449).</span></span> <span data-ttu-id="fd847-106">Služba WCF, která se spustí v prostředí služby IIS plně využívá funkce služby IIS, jako je například recyklace procesů, nečinnosti vypnutí, monitorování stavu procesu a aktivaci založenou na zprávách.</span><span class="sxs-lookup"><span data-stu-id="fd847-106">A WCF service that runs in the IIS environment takes full advantage of IIS features, such as process recycling, idle shutdown, process health monitoring, and message-based activation.</span></span> <span data-ttu-id="fd847-107">Tato možnost hostování vyžaduje, aby byly správně konfigurovány služby IIS, ale nevyžaduje, že libovolný kód hostování se zapisují jako součást aplikace.</span><span class="sxs-lookup"><span data-stu-id="fd847-107">This hosting option requires that IIS be properly configured, but it does not require that any hosting code be written as part of the application.</span></span> <span data-ttu-id="fd847-108">Můžete použít hostování IIS pouze s přenos pomocí protokolu HTTP.</span><span class="sxs-lookup"><span data-stu-id="fd847-108">You can use IIS hosting only with an HTTP transport.</span></span>  
  
 <span data-ttu-id="fd847-109">Další informace o tom, WCF a [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] pracovat, naleznete v tématu [služby WCF a ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md).</span><span class="sxs-lookup"><span data-stu-id="fd847-109">For more information about how WCF and [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] interact, see [WCF Services and ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md).</span></span> <span data-ttu-id="fd847-110">Další informace o konfiguraci zabezpečení najdete v tématu [zabezpečení](../../../../docs/framework/wcf/feature-details/security.md).</span><span class="sxs-lookup"><span data-stu-id="fd847-110">For more information about configuring security, see [Security](../../../../docs/framework/wcf/feature-details/security.md).</span></span>  
  
 <span data-ttu-id="fd847-111">Pro zdrojovou kopii tohoto příkladu, naleznete v tématu [IIS hostování pomocí vloženého kódu](../../../../docs/framework/wcf/samples/iis-hosting-using-inline-code.md).</span><span class="sxs-lookup"><span data-stu-id="fd847-111">For the source copy of this example, see [IIS Hosting Using Inline Code](../../../../docs/framework/wcf/samples/iis-hosting-using-inline-code.md).</span></span>  
  
### <a name="to-create-a-service-hosted-by-iis"></a><span data-ttu-id="fd847-112">Vytvoření služby hostované službou IIS.</span><span class="sxs-lookup"><span data-stu-id="fd847-112">To create a service hosted by IIS</span></span>  
  
1.  <span data-ttu-id="fd847-113">Zkontrolujte, zda je služba IIS na počítači nainstalovaná a spuštěná.</span><span class="sxs-lookup"><span data-stu-id="fd847-113">Confirm that IIS is installed and running on your computer.</span></span> <span data-ttu-id="fd847-114">Další informace o instalaci a konfiguraci služby IIS najdete v části [instalace a konfigurace služby IIS 7.0](https://go.microsoft.com/fwlink/?LinkID=132128)</span><span class="sxs-lookup"><span data-stu-id="fd847-114">For more information about installing and configuring IIS see [Installing and Configuring IIS 7.0](https://go.microsoft.com/fwlink/?LinkID=132128)</span></span>  
  
2.  <span data-ttu-id="fd847-115">Vytvořte novou složku s názvem "IISHostedCalcService" souborů aplikace, ujistěte se, že [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] má přístup k obsahu složky a vytvořte novou aplikaci služby IIS, který je fyzicky umístěný v této aplikaci pomocí nástroje pro správu služby IIS adresář.</span><span class="sxs-lookup"><span data-stu-id="fd847-115">Create a new folder for your application files called "IISHostedCalcService", ensure that [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] has access to the contents of the folder, and use the IIS management tool to create a new IIS application that is physically located in this application directory.</span></span> <span data-ttu-id="fd847-116">Při vytváření aliasu pro použití aplikací adresáře "IISHostedCalc".</span><span class="sxs-lookup"><span data-stu-id="fd847-116">When creating an alias for the application directory use "IISHostedCalc".</span></span>  
  
3.  <span data-ttu-id="fd847-117">Vytvořte nový soubor s názvem "service.svc" v adresáři aplikace.</span><span class="sxs-lookup"><span data-stu-id="fd847-117">Create a new file named "service.svc" in the application directory.</span></span> <span data-ttu-id="fd847-118">Tento soubor upravit přidáním následujícího kódu @ServiceHost elementu.</span><span class="sxs-lookup"><span data-stu-id="fd847-118">Edit this file by adding the following @ServiceHost element.</span></span>  
  
    ```  
    <%@ServiceHost language=c# Debug="true" Service="Microsoft.ServiceModel.Samples.CalculatorService"%>  
    ```  
  
4.  <span data-ttu-id="fd847-119">Vytvoření App_Code podadresáře v adresáři aplikace.</span><span class="sxs-lookup"><span data-stu-id="fd847-119">Create an App_Code subdirectory within the application directory.</span></span>  
  
5.  <span data-ttu-id="fd847-120">Vytvořte soubor kódu Service.cs v podadresáři App_Code.</span><span class="sxs-lookup"><span data-stu-id="fd847-120">Create a code file named Service.cs in the App_Code subdirectory.</span></span>  
  
6.  <span data-ttu-id="fd847-121">Přidejte následující příkazy using do horní části souboru Service.cs.</span><span class="sxs-lookup"><span data-stu-id="fd847-121">Add the following using statements to the top of the Service.cs file.</span></span>  
  
    ```csharp  
    using System;  
    using System.ServiceModel;  
    ```  
  
7.  <span data-ttu-id="fd847-122">Přidejte následující deklarace oboru názvů po na pomocí příkazů.</span><span class="sxs-lookup"><span data-stu-id="fd847-122">Add the following namespace declaration after the using statements.</span></span>  
  
    ```csharp  
    namespace Microsoft.ServiceModel.Samples  
    {  
    }  
    ```  
  
8.  <span data-ttu-id="fd847-123">Definování kontraktu služby uvnitř deklarace oboru názvů, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="fd847-123">Define the service contract inside the namespace declaration as shown in the following code.</span></span>  
  
     [!code-csharp[c_HowTo_HostInIIS#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/cs/source.cs#11)]
     [!code-vb[c_HowTo_HostInIIS#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostiniis/vb/source.vb#11)]  
  
9. <span data-ttu-id="fd847-124">Implementace kontraktu služby, po servisní smlouvy definice, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="fd847-124">Implement the service contract after the service contract definition as shown in the following code.</span></span>  
  
     [!code-csharp[c_HowTo_HostInIIS#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/cs/source.cs#12)]
     [!code-vb[c_HowTo_HostInIIS#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostiniis/vb/source.vb#12)]  
  
10. <span data-ttu-id="fd847-125">Vytvořte soubor s názvem "Web.config" v adresáři aplikace a přidejte následující kód, konfigurace do souboru.</span><span class="sxs-lookup"><span data-stu-id="fd847-125">Create a file named "Web.config" in the application directory and add the following configuration code into the file.</span></span> <span data-ttu-id="fd847-126">Za běhu infrastruktura WCF používá informace k vytvoření koncového bodu, který můžou klienti komunikovat klientské aplikace.</span><span class="sxs-lookup"><span data-stu-id="fd847-126">At runtime, the WCF infrastructure uses the information to construct an endpoint that client applications can communicate with.</span></span>  
  
     [!code-xml[c_HowTo_HostInIIS#100](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/common/web.config#100)]      
  
     <span data-ttu-id="fd847-127">Tento příklad explicitně určuje koncové body v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="fd847-127">This example explicitly specifies endpoints in the configuration file.</span></span> <span data-ttu-id="fd847-128">Pokud nemůžete přidat žádné koncové body pro službu, modulu runtime přidá výchozí koncové body za vás.</span><span class="sxs-lookup"><span data-stu-id="fd847-128">If you do not add any endpoints to the service, the runtime adds default endpoints for you.</span></span> <span data-ttu-id="fd847-129">Další informace o výchozí koncové body, vazby a chování viz [zjednodušená konfigurace](../../../../docs/framework/wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="fd847-129">For more information about default endpoints, bindings, and behaviors see [Simplified Configuration](../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
11. <span data-ttu-id="fd847-130">Pokud chcete mít jistotu, že služba je hostována správně, spusťte instanci aplikace Internet Explorer a přejděte na adresu URL služby: `http://localhost/IISHostedCalc/Service.svc`</span><span class="sxs-lookup"><span data-stu-id="fd847-130">To make sure the service is hosted correctly, open an instance of Internet Explorer and browse to the service's URL: `http://localhost/IISHostedCalc/Service.svc`</span></span>  
  
## <a name="example"></a><span data-ttu-id="fd847-131">Příklad</span><span class="sxs-lookup"><span data-stu-id="fd847-131">Example</span></span>  
 <span data-ttu-id="fd847-132">Zde je, že úplný výpis kódu pro IIS hostovanou službu kalkulačky.</span><span class="sxs-lookup"><span data-stu-id="fd847-132">The following is a complete listing of the code for the IIS hosted calculator service.</span></span>  
  
 [!code-csharp[C_HowTo_HostInIIS#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/cs/source.cs#1)] 
 [!code-vb[C_HowTo_HostInIIS#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostiniis/vb/source.vb#1)] 
 [!code-xml[c_HowTo_HostInIIS#100](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/common/web.config#100)]  
  
## <a name="see-also"></a><span data-ttu-id="fd847-133">Viz také</span><span class="sxs-lookup"><span data-stu-id="fd847-133">See Also</span></span>  
 [<span data-ttu-id="fd847-134">Hostování v Internetové informační službě</span><span class="sxs-lookup"><span data-stu-id="fd847-134">Hosting in Internet Information Services</span></span>](../../../../docs/framework/wcf/feature-details/hosting-in-internet-information-services.md)  
 [<span data-ttu-id="fd847-135">Služby hostování</span><span class="sxs-lookup"><span data-stu-id="fd847-135">Hosting Services</span></span>](../../../../docs/framework/wcf/hosting-services.md)  
 [<span data-ttu-id="fd847-136">Služby WCF a ASP.NET</span><span class="sxs-lookup"><span data-stu-id="fd847-136">WCF Services and ASP.NET</span></span>](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md)  
 [<span data-ttu-id="fd847-137">Zabezpečení</span><span class="sxs-lookup"><span data-stu-id="fd847-137">Security</span></span>](../../../../docs/framework/wcf/feature-details/security.md)  
 [<span data-ttu-id="fd847-138">Hostování funkcí systému Windows Server App Fabric</span><span class="sxs-lookup"><span data-stu-id="fd847-138">Windows Server App Fabric Hosting Features</span></span>](https://go.microsoft.com/fwlink/?LinkId=201276)
