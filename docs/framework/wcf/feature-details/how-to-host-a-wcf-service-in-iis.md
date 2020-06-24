---
title: 'Postupy: Hostování služby WCF v IIS'
description: Naučte se, jak vytvořit službu WCF, která je hostovaná ve službě Internetová informační služba (IIS). Službu IIS můžete použít jenom s přenosem HTTP.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b044b1c9-c1e5-4c9f-84d8-0f02f4537f8b
ms.openlocfilehash: 63549b85f7bcdd4f246005401694db8827248038
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/23/2020
ms.locfileid: "85246906"
---
# <a name="how-to-host-a-wcf-service-in-iis"></a><span data-ttu-id="06636-104">Postupy: Hostování služby WCF v IIS</span><span class="sxs-lookup"><span data-stu-id="06636-104">How to: Host a WCF Service in IIS</span></span>
<span data-ttu-id="06636-105">Toto téma popisuje základní kroky potřebné k vytvoření služby Windows Communication Foundation (WCF), která je hostovaná v Internetová informační služba (IIS).</span><span class="sxs-lookup"><span data-stu-id="06636-105">This topic outlines the basic steps required to create a Windows Communication Foundation (WCF) service that is hosted in Internet Information Services (IIS).</span></span> <span data-ttu-id="06636-106">V tomto tématu se předpokládá, že jste obeznámeni se službou IIS a rozumíte tomu, jak pomocí nástroje pro správu služby IIS vytvářet a spravovat aplikace IIS.</span><span class="sxs-lookup"><span data-stu-id="06636-106">This topic assumes you are familiar with IIS and understand how to use the IIS management tool to create and manage IIS applications.</span></span> <span data-ttu-id="06636-107">Další informace o službě IIS najdete v tématu [Internetová informační služba](https://www.iis.net/).</span><span class="sxs-lookup"><span data-stu-id="06636-107">For more information about IIS see [Internet Information Services](https://www.iis.net/).</span></span> <span data-ttu-id="06636-108">Služba WCF, která běží v prostředí služby IIS, má plně výhodu funkcí služby IIS, jako je recyklace procesů, nečinné vypnutí, monitorování stavu procesu a aktivace na základě zpráv.</span><span class="sxs-lookup"><span data-stu-id="06636-108">A WCF service that runs in the IIS environment takes full advantage of IIS features, such as process recycling, idle shutdown, process health monitoring, and message-based activation.</span></span> <span data-ttu-id="06636-109">Tato možnost hostování vyžaduje, aby služba IIS byla správně nakonfigurovaná, ale nevyžaduje, aby se veškerý hostitelský kód napsal jako součást aplikace.</span><span class="sxs-lookup"><span data-stu-id="06636-109">This hosting option requires that IIS be properly configured, but it does not require that any hosting code be written as part of the application.</span></span> <span data-ttu-id="06636-110">Službu IIS můžete použít jenom s přenosem HTTP.</span><span class="sxs-lookup"><span data-stu-id="06636-110">You can use IIS hosting only with an HTTP transport.</span></span>  
  
 <span data-ttu-id="06636-111">Další informace o tom, jak WCF a ASP.NET spolupracují, najdete v tématu [služby WCF a ASP.NET](wcf-services-and-aspnet.md).</span><span class="sxs-lookup"><span data-stu-id="06636-111">For more information about how WCF and ASP.NET interact, see [WCF Services and ASP.NET](wcf-services-and-aspnet.md).</span></span> <span data-ttu-id="06636-112">Další informace o konfiguraci zabezpečení najdete v tématu [zabezpečení](security.md).</span><span class="sxs-lookup"><span data-stu-id="06636-112">For more information about configuring security, see [Security](security.md).</span></span>  
  
 <span data-ttu-id="06636-113">Zdrojovou kopii tohoto příkladu naleznete v tématu [hostování služby IIS pomocí vloženého kódu](../samples/iis-hosting-using-inline-code.md).</span><span class="sxs-lookup"><span data-stu-id="06636-113">For the source copy of this example, see [IIS Hosting Using Inline Code](../samples/iis-hosting-using-inline-code.md).</span></span>  
  
### <a name="to-create-a-service-hosted-by-iis"></a><span data-ttu-id="06636-114">Vytvoření služby hostované službou IIS</span><span class="sxs-lookup"><span data-stu-id="06636-114">To create a service hosted by IIS</span></span>  
  
1. <span data-ttu-id="06636-115">Ověřte, že je služba IIS v počítači nainstalovaná a spuštěná.</span><span class="sxs-lookup"><span data-stu-id="06636-115">Confirm that IIS is installed and running on your computer.</span></span> <span data-ttu-id="06636-116">Další informace o instalaci a konfiguraci služby IIS najdete v tématu [instalace a konfigurace služby iis 7,0](https://docs.microsoft.com/iis/install/installing-iis-7/installing-necessary-iis-components-on-windows-vista) .</span><span class="sxs-lookup"><span data-stu-id="06636-116">For more information about installing and configuring IIS see [Installing and Configuring IIS 7.0](https://docs.microsoft.com/iis/install/installing-iis-7/installing-necessary-iis-components-on-windows-vista)</span></span>  
  
2. <span data-ttu-id="06636-117">Vytvořte novou složku pro soubory aplikace nazvané "IISHostedCalcService", ujistěte se, že ASP.NET má přístup k obsahu složky, a pomocí nástroje pro správu služby IIS vytvořte novou aplikaci IIS, která je fyzicky umístěná v tomto adresáři aplikace.</span><span class="sxs-lookup"><span data-stu-id="06636-117">Create a new folder for your application files called "IISHostedCalcService", ensure that ASP.NET has access to the contents of the folder, and use the IIS management tool to create a new IIS application that is physically located in this application directory.</span></span> <span data-ttu-id="06636-118">Při vytváření aliasu pro adresář aplikace použijte "IISHostedCalc".</span><span class="sxs-lookup"><span data-stu-id="06636-118">When creating an alias for the application directory use "IISHostedCalc".</span></span>  
  
3. <span data-ttu-id="06636-119">V adresáři aplikace vytvořte nový soubor s názvem Service. svc.</span><span class="sxs-lookup"><span data-stu-id="06636-119">Create a new file named "service.svc" in the application directory.</span></span> <span data-ttu-id="06636-120">Upravte tento soubor přidáním následujícího @ServiceHost elementu.</span><span class="sxs-lookup"><span data-stu-id="06636-120">Edit this file by adding the following @ServiceHost element.</span></span>  
  
   ```
   <%@ServiceHost language=c# Debug="true" Service="Microsoft.ServiceModel.Samples.CalculatorService"%>
   ```  
  
4. <span data-ttu-id="06636-121">Vytvořte podadresář App_Code v adresáři aplikace.</span><span class="sxs-lookup"><span data-stu-id="06636-121">Create an App_Code subdirectory within the application directory.</span></span>  
  
5. <span data-ttu-id="06636-122">V podadresáři App_Code vytvořte soubor kódu s názvem Service.cs.</span><span class="sxs-lookup"><span data-stu-id="06636-122">Create a code file named Service.cs in the App_Code subdirectory.</span></span>  
  
6. <span data-ttu-id="06636-123">Do horní části souboru Service.cs přidejte následující příkazy using.</span><span class="sxs-lookup"><span data-stu-id="06636-123">Add the following using statements to the top of the Service.cs file.</span></span>  
  
    ```csharp  
    using System;  
    using System.ServiceModel;  
    ```  
  
7. <span data-ttu-id="06636-124">Po příkazech using přidejte následující deklaraci oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="06636-124">Add the following namespace declaration after the using statements.</span></span>  
  
    ```csharp  
    namespace Microsoft.ServiceModel.Samples  
    {  
    }  
    ```  
  
8. <span data-ttu-id="06636-125">Definujte kontrakt služby uvnitř deklarace oboru názvů, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="06636-125">Define the service contract inside the namespace declaration as shown in the following code.</span></span>  
  
     [!code-csharp[c_HowTo_HostInIIS#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/cs/source.cs#11)]
     [!code-vb[c_HowTo_HostInIIS#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostiniis/vb/source.vb#11)]  
  
9. <span data-ttu-id="06636-126">Po definici kontraktu služby, jak je znázorněno v následujícím kódu, implementujte kontrakt služby.</span><span class="sxs-lookup"><span data-stu-id="06636-126">Implement the service contract after the service contract definition as shown in the following code.</span></span>  
  
     [!code-csharp[c_HowTo_HostInIIS#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/cs/source.cs#12)]
     [!code-vb[c_HowTo_HostInIIS#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostiniis/vb/source.vb#12)]  
  
10. <span data-ttu-id="06636-127">Vytvořte soubor s názvem "Web.config" v adresáři aplikace a přidejte do souboru následující konfigurační kód.</span><span class="sxs-lookup"><span data-stu-id="06636-127">Create a file named "Web.config" in the application directory and add the following configuration code into the file.</span></span> <span data-ttu-id="06636-128">Infrastruktura WCF za běhu používá informace k vytvoření koncového bodu, se kterým můžou klientské aplikace komunikovat.</span><span class="sxs-lookup"><span data-stu-id="06636-128">At runtime, the WCF infrastructure uses the information to construct an endpoint that client applications can communicate with.</span></span>  
  
     [!code-xml[c_HowTo_HostInIIS#100](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/common/web.config#100)]
  
     <span data-ttu-id="06636-129">Tento příklad explicitně určuje koncové body v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="06636-129">This example explicitly specifies endpoints in the configuration file.</span></span> <span data-ttu-id="06636-130">Pokud do služby nepřidáte žádné koncové body, modul runtime přidá pro vás výchozí koncové body.</span><span class="sxs-lookup"><span data-stu-id="06636-130">If you do not add any endpoints to the service, the runtime adds default endpoints for you.</span></span> <span data-ttu-id="06636-131">Další informace o výchozích koncových bodech, vazbách a chování najdete v tématu [zjednodušená konfigurace](../simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="06636-131">For more information about default endpoints, bindings, and behaviors see [Simplified Configuration](../simplified-configuration.md) and [Simplified Configuration for WCF Services](../samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
11. <span data-ttu-id="06636-132">Abyste se ujistili, že je služba hostovaná správně, otevřete instanci aplikace Internet Explorer a přejděte na adresu URL služby:`http://localhost/IISHostedCalc/Service.svc`</span><span class="sxs-lookup"><span data-stu-id="06636-132">To make sure the service is hosted correctly, open an instance of Internet Explorer and browse to the service's URL: `http://localhost/IISHostedCalc/Service.svc`</span></span>  
  
## <a name="example"></a><span data-ttu-id="06636-133">Příklad</span><span class="sxs-lookup"><span data-stu-id="06636-133">Example</span></span>  
 <span data-ttu-id="06636-134">Následuje úplný seznam kódu pro službu IIS Hosted Kalkulačka.</span><span class="sxs-lookup"><span data-stu-id="06636-134">The following is a complete listing of the code for the IIS hosted calculator service.</span></span>  
  
 [!code-csharp[C_HowTo_HostInIIS#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/cs/source.cs#1)]
 [!code-vb[C_HowTo_HostInIIS#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostiniis/vb/source.vb#1)]
 [!code-xml[c_HowTo_HostInIIS#100](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/common/web.config#100)]  
  
## <a name="see-also"></a><span data-ttu-id="06636-135">Viz také</span><span class="sxs-lookup"><span data-stu-id="06636-135">See also</span></span>

- [<span data-ttu-id="06636-136">Hostování v Internetové informační službě</span><span class="sxs-lookup"><span data-stu-id="06636-136">Hosting in Internet Information Services</span></span>](hosting-in-internet-information-services.md)
- [<span data-ttu-id="06636-137">Služby hostování</span><span class="sxs-lookup"><span data-stu-id="06636-137">Hosting Services</span></span>](../hosting-services.md)
- [<span data-ttu-id="06636-138">Služby WCF a ASP.NET</span><span class="sxs-lookup"><span data-stu-id="06636-138">WCF Services and ASP.NET</span></span>](wcf-services-and-aspnet.md)
- [<span data-ttu-id="06636-139">Zabezpečení</span><span class="sxs-lookup"><span data-stu-id="06636-139">Security</span></span>](security.md)
- <span data-ttu-id="06636-140">[Funkce hostování technologie Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677189(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="06636-140">[Windows Server App Fabric Hosting Features](https://docs.microsoft.com/previous-versions/appfabric/ee677189(v=azure.10))</span></span>
