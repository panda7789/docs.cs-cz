---
title: "Postupy: Hostování služby WCF ve spravované službě Windows"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 8e37363b-4dad-4fb6-907f-73c30fac1d9a
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f4b2c8daa176ef1f9aef24cac3125d59fcc02fa9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-host-a-wcf-service-in-a-managed-windows-service"></a><span data-ttu-id="7a901-102">Postupy: Hostování služby WCF ve spravované službě Windows</span><span class="sxs-lookup"><span data-stu-id="7a901-102">How to: Host a WCF Service in a Managed Windows Service</span></span>
<span data-ttu-id="7a901-103">Toto téma popisuje základní kroky potřebné pro vytvoření [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] služba, která je hostitelem služby systému Windows.</span><span class="sxs-lookup"><span data-stu-id="7a901-103">This topic outlines the basic steps required to create a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] service that is hosted by a Windows Service.</span></span> <span data-ttu-id="7a901-104">Ve spravovaných hostování možnost, která je dlouho běžící služby systému Windows je povoleno scénáři [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby hostované v zabezpečeném prostředí, která není zpráv, ve aktivovat mimo Internetové informační služby (IIS).</span><span class="sxs-lookup"><span data-stu-id="7a901-104">The scenario is enabled by the managed Windows service hosting option that is a long-running [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service hosted outside of Internet Information Services (IIS) in a secure environment that is not message activated.</span></span> <span data-ttu-id="7a901-105">Doba platnosti služby místo toho řídí operační systém.</span><span class="sxs-lookup"><span data-stu-id="7a901-105">The lifetime of the service is controlled instead by the operating system.</span></span> <span data-ttu-id="7a901-106">Tento hostitelský možnost je dostupná ve všech verzích systému Windows.</span><span class="sxs-lookup"><span data-stu-id="7a901-106">This hosting option is available in all versions of Windows.</span></span>  
  
 <span data-ttu-id="7a901-107">Služby systému Windows lze spravovat pomocí Microsoft.ManagementConsole.SnapIn v konzole Microsoft Management Console (MMC) a lze nakonfigurovat automatické spuštění po spuštění systému.</span><span class="sxs-lookup"><span data-stu-id="7a901-107">Windows services can be managed with the Microsoft.ManagementConsole.SnapIn in Microsoft Management Console (MMC) and can be configured to start up automatically when the system boots up.</span></span> <span data-ttu-id="7a901-108">Tato možnost hostování se skládá z registraci domény aplikace (AppDomain), který je hostitelem [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby jako spravovanou službu systému Windows tak, že doba platnosti procesu služby je řízena pomocí ovládacího prvku Správce služeb (SCM) pro služby systému Windows.</span><span class="sxs-lookup"><span data-stu-id="7a901-108">This hosting option consists of registering the application domain (AppDomain) that hosts a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service as a managed Windows service so that the process lifetime of the service is controlled by the Service Control Manager (SCM) for Windows services.</span></span>  
  
 <span data-ttu-id="7a901-109">Kód služby zahrnuje implementace služby kontrakt služby, třídu služby systému Windows a třídu Instalační služby.</span><span class="sxs-lookup"><span data-stu-id="7a901-109">The service code includes a service implementation of the service contract, a Windows Service class, and an installer class.</span></span> <span data-ttu-id="7a901-110">Třídě implementace služby `CalculatorService`, je [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby.</span><span class="sxs-lookup"><span data-stu-id="7a901-110">The service implementation class, `CalculatorService`, is a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service.</span></span> <span data-ttu-id="7a901-111">`CalculatorWindowsService` Je služba systému Windows.</span><span class="sxs-lookup"><span data-stu-id="7a901-111">The `CalculatorWindowsService` is a Windows service.</span></span> <span data-ttu-id="7a901-112">Aby se dosáhlo nároku jako služby systému Windows, třídy dědí z `ServiceBase` a implementuje `OnStart` a `OnStop` metody.</span><span class="sxs-lookup"><span data-stu-id="7a901-112">To qualify as a Windows service, the class inherits from `ServiceBase` and implements the `OnStart` and `OnStop` methods.</span></span> <span data-ttu-id="7a901-113">V `OnStart`, <xref:System.ServiceModel.ServiceHost> se vytvoří `CalculatorService` zadejte a otevřít.</span><span class="sxs-lookup"><span data-stu-id="7a901-113">In `OnStart`, a <xref:System.ServiceModel.ServiceHost> is created for the `CalculatorService` type and opened.</span></span> <span data-ttu-id="7a901-114">V `OnStop`, služba je zastavena a zlikvidován.</span><span class="sxs-lookup"><span data-stu-id="7a901-114">In `OnStop`, the service is stopped and disposed.</span></span> <span data-ttu-id="7a901-115">Hostitel je také zodpovědná za poskytování základní adresa hostitele služby, který byl nakonfigurován v nastavení aplikace.</span><span class="sxs-lookup"><span data-stu-id="7a901-115">The host is also responsible for providing a base address to the service host, which has been configured in application settings.</span></span> <span data-ttu-id="7a901-116">Instalační program třídy, která dědí z <xref:System.Configuration.Install.Installer>, umožňuje program, který chcete nainstalovat nástroj Installutil.exe jako služby systému Windows.</span><span class="sxs-lookup"><span data-stu-id="7a901-116">The installer class, which inherits from <xref:System.Configuration.Install.Installer>, allows the program to be installed as a Windows service by the Installutil.exe tool.</span></span>  
  
### <a name="construct-the-service-and-provide-the-hosting-code"></a><span data-ttu-id="7a901-117">Vytvoření služby a zadejte kód hostování</span><span class="sxs-lookup"><span data-stu-id="7a901-117">Construct the service and provide the hosting code</span></span>  
  
1.  <span data-ttu-id="7a901-118">Vytvořte nový projekt Visual Studio konzolové aplikace s názvem "Služba".</span><span class="sxs-lookup"><span data-stu-id="7a901-118">Create a new Visual Studio Console Application project called "Service".</span></span>  
  
2.  <span data-ttu-id="7a901-119">Přejmenujte Program.cs Service.cs.</span><span class="sxs-lookup"><span data-stu-id="7a901-119">Rename Program.cs to Service.cs.</span></span>  
  
3.  <span data-ttu-id="7a901-120">Změňte obor názvů na Microsoft.ServiceModel.Samples.</span><span class="sxs-lookup"><span data-stu-id="7a901-120">Change the namespace to Microsoft.ServiceModel.Samples.</span></span>  
  
4.  <span data-ttu-id="7a901-121">Přidejte odkazy na následující sestavení.</span><span class="sxs-lookup"><span data-stu-id="7a901-121">Add references to the following assemblies.</span></span>  
  
    -   <span data-ttu-id="7a901-122">System.ServiceModel.dll</span><span class="sxs-lookup"><span data-stu-id="7a901-122">System.ServiceModel.dll</span></span>  
  
    -   <span data-ttu-id="7a901-123">System.ServiceProcess.dll</span><span class="sxs-lookup"><span data-stu-id="7a901-123">System.ServiceProcess.dll</span></span>  
  
    -   <span data-ttu-id="7a901-124">System.Configuration.Install.dll</span><span class="sxs-lookup"><span data-stu-id="7a901-124">System.Configuration.Install.dll</span></span>  
  
5.  <span data-ttu-id="7a901-125">Přidejte následující příkazy using do Service.cs.</span><span class="sxs-lookup"><span data-stu-id="7a901-125">Add the following using statements to Service.cs.</span></span>  
  
     [!code-csharp[c_HowTo_HostInNTService#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#0)]
     [!code-vb[c_HowTo_HostInNTService#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#0)]  
  
6.  <span data-ttu-id="7a901-126">Definování `ICalculator` kontrakt služby, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="7a901-126">Define the `ICalculator` service contract as shown in the following code.</span></span>  
  
     [!code-csharp[c_HowTo_HostInNTService#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#1)]
     [!code-vb[c_HowTo_HostInNTService#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#1)]  
  
7.  <span data-ttu-id="7a901-127">Implementace kontraktu služby ve třídě nazvané `CalculatorService` jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="7a901-127">Implement the service contract in a class called `CalculatorService` as shown in the following code.</span></span>  
  
     [!code-csharp[c_HowTo_HostInNTService#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#2)]
     [!code-vb[c_HowTo_HostInNTService#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#2)]  
  
8.  <span data-ttu-id="7a901-128">Vytvořte novou třídu s názvem `CalculatorWindowsService` který dědí z <xref:System.ServiceProcess.ServiceBase> třídy.</span><span class="sxs-lookup"><span data-stu-id="7a901-128">Create a new class called `CalculatorWindowsService` that inherits from the <xref:System.ServiceProcess.ServiceBase> class.</span></span> <span data-ttu-id="7a901-129">Přidat místní proměnné s názvem `serviceHost` k odkazu <xref:System.ServiceModel.ServiceHost> instance.</span><span class="sxs-lookup"><span data-stu-id="7a901-129">Add a local variable called `serviceHost` to reference the <xref:System.ServiceModel.ServiceHost> instance.</span></span> <span data-ttu-id="7a901-130">Definování `Main` metoda, která volá`ServiceBase.Run(new CalculatorWindowsService)`</span><span class="sxs-lookup"><span data-stu-id="7a901-130">Define the `Main` method that calls `ServiceBase.Run(new CalculatorWindowsService)`</span></span>  
  
     [!code-csharp[c_HowTo_HostInNTService#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#3)]
     [!code-vb[c_HowTo_HostInNTService#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#3)]  
  
9. <span data-ttu-id="7a901-131">Přepsání <xref:System.ServiceProcess.ServiceBase.OnStart%28System.String%5B%5D%29> metoda, při vytváření a otevírání novou <xref:System.ServiceModel.ServiceHost> instance, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="7a901-131">Override the <xref:System.ServiceProcess.ServiceBase.OnStart%28System.String%5B%5D%29> method by creating and opening a new <xref:System.ServiceModel.ServiceHost> instance as shown in the following code.</span></span>  
  
     [!code-csharp[c_HowTo_HostInNTService#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#4)]
     [!code-vb[c_HowTo_HostInNTService#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#4)]  
  
10. <span data-ttu-id="7a901-132">Přepsání <xref:System.ServiceProcess.ServiceBase.OnStop%2A> metoda zavření <xref:System.ServiceModel.ServiceHost> jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="7a901-132">Override the <xref:System.ServiceProcess.ServiceBase.OnStop%2A> method closing the <xref:System.ServiceModel.ServiceHost> as shown in the following code.</span></span>  
  
     [!code-csharp[c_HowTo_HostInNTService#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#5)]
     [!code-vb[c_HowTo_HostInNTService#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#5)]  
  
11. <span data-ttu-id="7a901-133">Vytvořte novou třídu s názvem `ProjectInstaller` který dědí z <xref:System.Configuration.Install.Installer> a který je označený <xref:System.ComponentModel.RunInstallerAttribute> nastavena na `true`.</span><span class="sxs-lookup"><span data-stu-id="7a901-133">Create a new class called `ProjectInstaller` that inherits from <xref:System.Configuration.Install.Installer> and that is marked with the <xref:System.ComponentModel.RunInstallerAttribute> set to `true`.</span></span> <span data-ttu-id="7a901-134">To umožňuje nainstalovat nástroj Installutil.exe služby systému Windows.</span><span class="sxs-lookup"><span data-stu-id="7a901-134">This allows the Windows service to be installed by the Installutil.exe tool.</span></span>  
  
     [!code-csharp[c_HowTo_HostInNTService#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#6)]
     [!code-vb[c_HowTo_HostInNTService#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#6)]  
  
12. <span data-ttu-id="7a901-135">Odeberte `Service` třídu, která byla vygenerována, když vytvoříte projekt.</span><span class="sxs-lookup"><span data-stu-id="7a901-135">Remove the `Service` class that was generated when you created the project.</span></span>  
  
13. <span data-ttu-id="7a901-136">Přidejte konfigurační soubor aplikace do projektu.</span><span class="sxs-lookup"><span data-stu-id="7a901-136">Add an application configuration file to the project.</span></span> <span data-ttu-id="7a901-137">Nahraďte obsah souboru s následující konfigurací XML.</span><span class="sxs-lookup"><span data-stu-id="7a901-137">Replace the contents of the file with the following configuration XML.</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <configuration>  
      <system.serviceModel>    <services>  
          <!-- This section is optional with the new configuration model  
               introduced in .NET Framework 4. -->  
          <service name="Microsoft.ServiceModel.Samples.CalculatorService"  
                   behaviorConfiguration="CalculatorServiceBehavior">  
            <host>  
              <baseAddresses>  
                <add baseAddress="http://localhost:8000/ServiceModelSamples/service"/>  
              </baseAddresses>  
            </host>  
            <!-- this endpoint is exposed at the base address provided by host: http://localhost:8000/ServiceModelSamples/service  -->  
            <endpoint address=""  
                      binding="wsHttpBinding"  
                      contract="Microsoft.ServiceModel.Samples.ICalculator" />  
            <!-- the mex endpoint is exposed at http://localhost:8000/ServiceModelSamples/service/mex -->  
            <endpoint address="mex"  
                      binding="mexHttpBinding"  
                      contract="IMetadataExchange" />  
          </service>  
        </services>  
        <behaviors>  
          <serviceBehaviors>  
            <behavior name="CalculatorServiceBehavior">  
              <serviceMetadata httpGetEnabled="true"/>  
              <serviceDebug includeExceptionDetailInFaults="False"/>  
            </behavior>  
          </serviceBehaviors>  
        </behaviors>  
      </system.serviceModel>  
    </configuration>  
    ```  
  
     <span data-ttu-id="7a901-138">Klikněte pravým tlačítkem v souboru App.config **Průzkumníku řešení** a vyberte **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="7a901-138">Right click the App.config file in the **Solution Explorer** and select **Properties**.</span></span> <span data-ttu-id="7a901-139">V části **kopírovat do výstupního adresáře** vyberte **kopírovat, pokud je novější**.</span><span class="sxs-lookup"><span data-stu-id="7a901-139">Under **Copy to Output Directory** select **Copy if Newer**.</span></span>  
  
     <span data-ttu-id="7a901-140">Tento příklad explicitně určuje koncové body v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="7a901-140">This example explicitly specifies endpoints in the configuration file.</span></span> <span data-ttu-id="7a901-141">Pokud jste ke službě nepřidávejte žádné koncové body, modul runtime přidá výchozí koncové body pro vás.</span><span class="sxs-lookup"><span data-stu-id="7a901-141">If you do not add any endpoints to the service, the runtime adds default endpoints for you.</span></span> <span data-ttu-id="7a901-142">V tomto příkladu protože služba má <xref:System.ServiceModel.Description.ServiceMetadataBehavior> nastavena na `true`, služby má také publikování metadat povolena.</span><span class="sxs-lookup"><span data-stu-id="7a901-142">In this example, because the service has a <xref:System.ServiceModel.Description.ServiceMetadataBehavior> set to `true`, your service also has publishing metadata enabled.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="7a901-143">výchozí koncové body, vazby a chování, viz [zjednodušená konfigurace](../../../../docs/framework/wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="7a901-143"> default endpoints, bindings, and behaviors, see [Simplified Configuration](../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
### <a name="install-and-run-the-service"></a><span data-ttu-id="7a901-144">Nainstalujte a spusťte službu</span><span class="sxs-lookup"><span data-stu-id="7a901-144">Install and run the service</span></span>  
  
1.  <span data-ttu-id="7a901-145">Sestavte řešení Chcete-li vytvořit `Service.exe` spustitelný soubor.</span><span class="sxs-lookup"><span data-stu-id="7a901-145">Build the solution to create the `Service.exe` executable.</span></span>  
  
2.  <span data-ttu-id="7a901-146">Otevřete [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] příkazový řádek a přejděte do adresáře projektu.</span><span class="sxs-lookup"><span data-stu-id="7a901-146">Open the [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] command prompt and navigate to the project directory.</span></span> <span data-ttu-id="7a901-147">Typ `installutil bin\service.exe` příkazového řádku pro instalaci služby Windows.</span><span class="sxs-lookup"><span data-stu-id="7a901-147">Type `installutil bin\service.exe` at the command prompt to install the Windows service.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="7a901-148">Pokud použijete [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] příkazový řádek, ujistěte se, že `%WinDir%\Microsoft.NET\Framework\v4.0.<current version>` adresář je v cestě k systému.</span><span class="sxs-lookup"><span data-stu-id="7a901-148">If you do not use the [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] command prompt, make sure that the `%WinDir%\Microsoft.NET\Framework\v4.0.<current version>` directory is in the system path.</span></span>  
  
     <span data-ttu-id="7a901-149">Typ `services.msc` příkazového řádku pro přístup k správce řízení služeb (SCM).</span><span class="sxs-lookup"><span data-stu-id="7a901-149">Type `services.msc` at the command prompt to access the Service Control Manager (SCM).</span></span> <span data-ttu-id="7a901-150">Služba systému Windows by se zobrazit v služby jako "WCFWindowsServiceSample".</span><span class="sxs-lookup"><span data-stu-id="7a901-150">The Windows service should appear in Services as "WCFWindowsServiceSample".</span></span> <span data-ttu-id="7a901-151">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Služby může odpovědět pouze na klienty, pokud je spuštěná služba Windows.</span><span class="sxs-lookup"><span data-stu-id="7a901-151">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service can only respond to clients if the Windows service is running.</span></span> <span data-ttu-id="7a901-152">Pokud chcete spustit službu, klikněte pravým tlačítkem ji v SCM a vyberte možnost "Start" nebo typ **net start WCFWindowsServiceSample** na příkazovém řádku.</span><span class="sxs-lookup"><span data-stu-id="7a901-152">To start the service, right-click it in the SCM and select "Start", or type **net start WCFWindowsServiceSample** at the command prompt.</span></span>  
  
3.  <span data-ttu-id="7a901-153">Pokud provedete změny ve službě, musíte nejprve zastavte ji a odinstalujte ji.</span><span class="sxs-lookup"><span data-stu-id="7a901-153">If you make changes to the service, you must first stop it and uninstall it.</span></span> <span data-ttu-id="7a901-154">Chcete zastavit službu, klikněte pravým tlačítkem na službu v SCM a zvolte "Stop", nebo **typ net stop WCFWindowsServiceSample** na příkazovém řádku.</span><span class="sxs-lookup"><span data-stu-id="7a901-154">To stop the service, right-click the service in the SCM and select "Stop", or **type net stop WCFWindowsServiceSample** at the command prompt.</span></span> <span data-ttu-id="7a901-155">Všimněte si, že pokud zastavíte službu systému Windows a pak spusťte klienta, <xref:System.ServiceModel.EndpointNotFoundException> když se klient pokusí o přístup ke službě došlo k výjimce.</span><span class="sxs-lookup"><span data-stu-id="7a901-155">Note that if you stop the Windows service and then run a client, an <xref:System.ServiceModel.EndpointNotFoundException> exception occurs when a client attempts to access the service.</span></span> <span data-ttu-id="7a901-156">Chcete-li odinstalovat typ služby Windows **installutil /u bin\service.exe** na příkazovém řádku.</span><span class="sxs-lookup"><span data-stu-id="7a901-156">To uninstall the Windows service type **installutil /u bin\service.exe** at the command prompt.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7a901-157">Příklad</span><span class="sxs-lookup"><span data-stu-id="7a901-157">Example</span></span>  
 <span data-ttu-id="7a901-158">Níže je úplný seznam všech kód použitý v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="7a901-158">The following is a complete listing of the code used by this topic.</span></span>  
  
 [!code-csharp[c_HowTo_HostInNTService#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#8)]
 [!code-vb[c_HowTo_HostInNTService#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#8)]  
  
 <span data-ttu-id="7a901-159">Jako možnost "Samoobslužné hostování" hostování prostředí služby systému Windows vyžaduje, aby některé hostování kódu zapsání jako součást aplikace.</span><span class="sxs-lookup"><span data-stu-id="7a901-159">Like the "Self-Hosting" option, the Windows service hosting environment requires that some hosting code be written as part of the application.</span></span> <span data-ttu-id="7a901-160">Služba je implementovaný jako konzolové aplikace a obsahuje vlastní kód pro hostování.</span><span class="sxs-lookup"><span data-stu-id="7a901-160">The service is implemented as a console application and contains its own hosting code.</span></span> <span data-ttu-id="7a901-161">V jiných hostitelských prostředích, jako je například služba aktivace procesů systému Windows (WAS) hostování v Internetové informační služby (IIS), není nutné pro vývojáře k zápisu hostování kódu.</span><span class="sxs-lookup"><span data-stu-id="7a901-161">In other hosting environments, such as Windows Process Activation Service (WAS) hosting in Internet Information Services (IIS), it is not necessary for developers to write hosting code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a901-162">Viz také</span><span class="sxs-lookup"><span data-stu-id="7a901-162">See Also</span></span>  
 [<span data-ttu-id="7a901-163">Zjednodušená konfigurace</span><span class="sxs-lookup"><span data-stu-id="7a901-163">Simplified Configuration</span></span>](../../../../docs/framework/wcf/simplified-configuration.md)  
 [<span data-ttu-id="7a901-164">Hostování ve spravované aplikaci</span><span class="sxs-lookup"><span data-stu-id="7a901-164">Hosting in a Managed Application</span></span>](../../../../docs/framework/wcf/feature-details/hosting-in-a-managed-application.md)  
 [<span data-ttu-id="7a901-165">Služby hostování</span><span class="sxs-lookup"><span data-stu-id="7a901-165">Hosting Services</span></span>](../../../../docs/framework/wcf/hosting-services.md)  
 [<span data-ttu-id="7a901-166">Hostování funkcí systému Windows Server App Fabric</span><span class="sxs-lookup"><span data-stu-id="7a901-166">Windows Server App Fabric Hosting Features</span></span>](http://go.microsoft.com/fwlink/?LinkId=201276)
