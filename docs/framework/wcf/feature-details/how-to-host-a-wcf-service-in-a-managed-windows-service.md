---
title: 'Postupy: Hostování služby WCF ve spravované službě Windows'
description: Naučte se vytvořit službu WCF, která je hostována službou systému Windows. Tato možnost hostování je k dispozici ve všech verzích Windows.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8e37363b-4dad-4fb6-907f-73c30fac1d9a
ms.openlocfilehash: 4e07aa7aac82fae5cfd1bfc759ef724cf87a873a
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/23/2020
ms.locfileid: "85246933"
---
# <a name="how-to-host-a-wcf-service-in-a-managed-windows-service"></a><span data-ttu-id="a9b67-104">Postupy: Hostování služby WCF ve spravované službě Windows</span><span class="sxs-lookup"><span data-stu-id="a9b67-104">How to: Host a WCF Service in a Managed Windows Service</span></span>

<span data-ttu-id="a9b67-105">Toto téma popisuje základní kroky potřebné k vytvoření služby Windows Communication Foundation (WCF), která je hostována službou systému Windows.</span><span class="sxs-lookup"><span data-stu-id="a9b67-105">This topic outlines the basic steps required to create a Windows Communication Foundation (WCF) service that is hosted by a Windows Service.</span></span> <span data-ttu-id="a9b67-106">Tento scénář je povolený možností hostování spravované služby systému Windows, která je dlouhodobě běžící služba WCF hostovaná mimo službu Internetová informační služba (IIS) v zabezpečeném prostředí, které není aktivovaná zpráva.</span><span class="sxs-lookup"><span data-stu-id="a9b67-106">The scenario is enabled by the managed Windows service hosting option that is a long-running WCF service hosted outside of Internet Information Services (IIS) in a secure environment that is not message activated.</span></span> <span data-ttu-id="a9b67-107">Doba života služby se místo toho řídí operačním systémem.</span><span class="sxs-lookup"><span data-stu-id="a9b67-107">The lifetime of the service is controlled instead by the operating system.</span></span> <span data-ttu-id="a9b67-108">Tato možnost hostování je k dispozici ve všech verzích Windows.</span><span class="sxs-lookup"><span data-stu-id="a9b67-108">This hosting option is available in all versions of Windows.</span></span>

<span data-ttu-id="a9b67-109">Služby systému Windows je možné spravovat pomocí modulu Microsoft. ManagementConsole. snap-in v konzole MMC (Microsoft Management Console) a je možné je nakonfigurovat tak, aby se při spuštění systému automaticky spustily.</span><span class="sxs-lookup"><span data-stu-id="a9b67-109">Windows services can be managed with the Microsoft.ManagementConsole.SnapIn in Microsoft Management Console (MMC) and can be configured to start up automatically when the system boots up.</span></span> <span data-ttu-id="a9b67-110">Tato možnost hostování se skládá z registrace domény aplikace (AppDomain), která je hostitelem služby WCF jako spravované služby systému Windows, aby byla doba životnosti procesu řízena správcem řízení služeb (SCM) pro služby systému Windows.</span><span class="sxs-lookup"><span data-stu-id="a9b67-110">This hosting option consists of registering the application domain (AppDomain) that hosts a WCF service as a managed Windows service so that the process lifetime of the service is controlled by the Service Control Manager (SCM) for Windows services.</span></span>

<span data-ttu-id="a9b67-111">Kód služby zahrnuje implementaci služby servisního kontraktu, třídy služby systému Windows a instalační třídy.</span><span class="sxs-lookup"><span data-stu-id="a9b67-111">The service code includes a service implementation of the service contract, a Windows Service class, and an installer class.</span></span> <span data-ttu-id="a9b67-112">Třída implementace služby, `CalculatorService` , je služba WCF.</span><span class="sxs-lookup"><span data-stu-id="a9b67-112">The service implementation class, `CalculatorService`, is a WCF service.</span></span> <span data-ttu-id="a9b67-113">`CalculatorWindowsService`Je služba systému Windows.</span><span class="sxs-lookup"><span data-stu-id="a9b67-113">The `CalculatorWindowsService` is a Windows service.</span></span> <span data-ttu-id="a9b67-114">Chcete-li se kvalifikovat jako služba systému Windows, třída dědí z `ServiceBase` a `OnStart` implementuje `OnStop` metody a.</span><span class="sxs-lookup"><span data-stu-id="a9b67-114">To qualify as a Windows service, the class inherits from `ServiceBase` and implements the `OnStart` and `OnStop` methods.</span></span> <span data-ttu-id="a9b67-115">V je `OnStart` <xref:System.ServiceModel.ServiceHost> vytvořen pro `CalculatorService` typ a otevřen.</span><span class="sxs-lookup"><span data-stu-id="a9b67-115">In `OnStart`, a <xref:System.ServiceModel.ServiceHost> is created for the `CalculatorService` type and opened.</span></span> <span data-ttu-id="a9b67-116">V nástroji `OnStop` je služba zastavená a vyřazená.</span><span class="sxs-lookup"><span data-stu-id="a9b67-116">In `OnStop`, the service is stopped and disposed.</span></span> <span data-ttu-id="a9b67-117">Hostitel taky zodpovídá za poskytnutí základní adresy pro hostitele služby, který je nakonfigurovaný v nastavení aplikace.</span><span class="sxs-lookup"><span data-stu-id="a9b67-117">The host is also responsible for providing a base address to the service host, which has been configured in application settings.</span></span> <span data-ttu-id="a9b67-118">Instalační třída, která dědí z <xref:System.Configuration.Install.Installer> , umožňuje programu instalovat program jako službu systému Windows pomocí nástroje Installutil.exe.</span><span class="sxs-lookup"><span data-stu-id="a9b67-118">The installer class, which inherits from <xref:System.Configuration.Install.Installer>, allows the program to be installed as a Windows service by the Installutil.exe tool.</span></span>

## <a name="construct-the-service-and-provide-the-hosting-code"></a><span data-ttu-id="a9b67-119">Sestavte službu a poskytněte hostující kód</span><span class="sxs-lookup"><span data-stu-id="a9b67-119">Construct the service and provide the hosting code</span></span>

1. <span data-ttu-id="a9b67-120">Vytvořte nový projekt **konzolové aplikace** sady Visual Studio s názvem **Service**.</span><span class="sxs-lookup"><span data-stu-id="a9b67-120">Create a new Visual Studio **Console app** project called **Service**.</span></span>

2. <span data-ttu-id="a9b67-121">Přejmenujte Program.cs na Service.cs.</span><span class="sxs-lookup"><span data-stu-id="a9b67-121">Rename Program.cs to Service.cs.</span></span>

3. <span data-ttu-id="a9b67-122">Změňte obor názvů na `Microsoft.ServiceModel.Samples` .</span><span class="sxs-lookup"><span data-stu-id="a9b67-122">Change the namespace to `Microsoft.ServiceModel.Samples`.</span></span>

4. <span data-ttu-id="a9b67-123">Přidejte odkazy na následující sestavení:</span><span class="sxs-lookup"><span data-stu-id="a9b67-123">Add references to the following assemblies:</span></span>

    - <span data-ttu-id="a9b67-124">System.ServiceModel.dll</span><span class="sxs-lookup"><span data-stu-id="a9b67-124">System.ServiceModel.dll</span></span>

    - <span data-ttu-id="a9b67-125">System.ServiceProcess.dll</span><span class="sxs-lookup"><span data-stu-id="a9b67-125">System.ServiceProcess.dll</span></span>

    - <span data-ttu-id="a9b67-126">System.Configuration.Install.dll</span><span class="sxs-lookup"><span data-stu-id="a9b67-126">System.Configuration.Install.dll</span></span>

5. <span data-ttu-id="a9b67-127">Do Service.cs přidejte následující příkazy using.</span><span class="sxs-lookup"><span data-stu-id="a9b67-127">Add the following using statements to Service.cs.</span></span>

     [!code-csharp[c_HowTo_HostInNTService#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#0)]
     [!code-vb[c_HowTo_HostInNTService#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#0)]

6. <span data-ttu-id="a9b67-128">Definujte `ICalculator` kontrakt služby, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="a9b67-128">Define the `ICalculator` service contract as shown in the following code.</span></span>

     [!code-csharp[c_HowTo_HostInNTService#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#1)]
     [!code-vb[c_HowTo_HostInNTService#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#1)]

7. <span data-ttu-id="a9b67-129">Implementujte kontrakt služby ve třídě s názvem `CalculatorService` , jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="a9b67-129">Implement the service contract in a class called `CalculatorService` as shown in the following code.</span></span>

     [!code-csharp[c_HowTo_HostInNTService#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#2)]
     [!code-vb[c_HowTo_HostInNTService#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#2)]

8. <span data-ttu-id="a9b67-130">Vytvořte novou třídu s názvem `CalculatorWindowsService` , která dědí z <xref:System.ServiceProcess.ServiceBase> třídy.</span><span class="sxs-lookup"><span data-stu-id="a9b67-130">Create a new class called `CalculatorWindowsService` that inherits from the <xref:System.ServiceProcess.ServiceBase> class.</span></span> <span data-ttu-id="a9b67-131">Přidejte místní proměnnou s názvem `serviceHost` , aby odkazovala na <xref:System.ServiceModel.ServiceHost> instanci.</span><span class="sxs-lookup"><span data-stu-id="a9b67-131">Add a local variable called `serviceHost` to reference the <xref:System.ServiceModel.ServiceHost> instance.</span></span> <span data-ttu-id="a9b67-132">Definujte `Main` metodu, která volá`ServiceBase.Run(new CalculatorWindowsService)`</span><span class="sxs-lookup"><span data-stu-id="a9b67-132">Define the `Main` method that calls `ServiceBase.Run(new CalculatorWindowsService)`</span></span>

     [!code-csharp[c_HowTo_HostInNTService#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#3)]
     [!code-vb[c_HowTo_HostInNTService#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#3)]

9. <span data-ttu-id="a9b67-133">Přepište <xref:System.ServiceProcess.ServiceBase.OnStart%28System.String%5B%5D%29> metodu vytvořením a otevřením nové <xref:System.ServiceModel.ServiceHost> instance, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="a9b67-133">Override the <xref:System.ServiceProcess.ServiceBase.OnStart%28System.String%5B%5D%29> method by creating and opening a new <xref:System.ServiceModel.ServiceHost> instance as shown in the following code.</span></span>

     [!code-csharp[c_HowTo_HostInNTService#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#4)]
     [!code-vb[c_HowTo_HostInNTService#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#4)]

10. <span data-ttu-id="a9b67-134">Přepsat <xref:System.ServiceProcess.ServiceBase.OnStop%2A> metodu, jak je <xref:System.ServiceModel.ServiceHost> znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="a9b67-134">Override the <xref:System.ServiceProcess.ServiceBase.OnStop%2A> method closing the <xref:System.ServiceModel.ServiceHost> as shown in the following code.</span></span>

     [!code-csharp[c_HowTo_HostInNTService#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#5)]
     [!code-vb[c_HowTo_HostInNTService#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#5)]

11. <span data-ttu-id="a9b67-135">Vytvořte novou třídu s názvem `ProjectInstaller` , která dědí z <xref:System.Configuration.Install.Installer> a která je označena atributem <xref:System.ComponentModel.RunInstallerAttribute> na hodnotu `true` .</span><span class="sxs-lookup"><span data-stu-id="a9b67-135">Create a new class called `ProjectInstaller` that inherits from <xref:System.Configuration.Install.Installer> and that is marked with the <xref:System.ComponentModel.RunInstallerAttribute> set to `true`.</span></span> <span data-ttu-id="a9b67-136">To umožňuje instalaci služby systému Windows pomocí nástroje Installutil.exe.</span><span class="sxs-lookup"><span data-stu-id="a9b67-136">This allows the Windows service to be installed by the Installutil.exe tool.</span></span>

     [!code-csharp[c_HowTo_HostInNTService#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#6)]
     [!code-vb[c_HowTo_HostInNTService#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#6)]

12. <span data-ttu-id="a9b67-137">Odeberte `Service` třídu, která byla generována při vytváření projektu.</span><span class="sxs-lookup"><span data-stu-id="a9b67-137">Remove the `Service` class that was generated when you created the project.</span></span>

13. <span data-ttu-id="a9b67-138">Přidejte konfigurační soubor aplikace do projektu.</span><span class="sxs-lookup"><span data-stu-id="a9b67-138">Add an application configuration file to the project.</span></span> <span data-ttu-id="a9b67-139">Nahraďte obsah souboru následujícím kódem XML konfigurace.</span><span class="sxs-lookup"><span data-stu-id="a9b67-139">Replace the contents of the file with the following configuration XML.</span></span>

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

     <span data-ttu-id="a9b67-140">Pravým tlačítkem myši klikněte na soubor App.config v **Průzkumník řešení** a vyberte **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="a9b67-140">Right click the App.config file in the **Solution Explorer** and select **Properties**.</span></span> <span data-ttu-id="a9b67-141">V části **Kopírovat do výstupního adresáře** vyberte **Kopírovat, pokud je novější**.</span><span class="sxs-lookup"><span data-stu-id="a9b67-141">Under **Copy to Output Directory** select **Copy if Newer**.</span></span>

     <span data-ttu-id="a9b67-142">Tento příklad explicitně určuje koncové body v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="a9b67-142">This example explicitly specifies endpoints in the configuration file.</span></span> <span data-ttu-id="a9b67-143">Pokud do služby nepřidáte žádné koncové body, modul runtime přidá pro vás výchozí koncové body.</span><span class="sxs-lookup"><span data-stu-id="a9b67-143">If you do not add any endpoints to the service, the runtime adds default endpoints for you.</span></span> <span data-ttu-id="a9b67-144">Protože je v tomto příkladu služba <xref:System.ServiceModel.Description.ServiceMetadataBehavior> nastavená na `true` , má vaše služba také povolenou metadata publikování.</span><span class="sxs-lookup"><span data-stu-id="a9b67-144">In this example, because the service has a <xref:System.ServiceModel.Description.ServiceMetadataBehavior> set to `true`, your service also has publishing metadata enabled.</span></span> <span data-ttu-id="a9b67-145">Další informace o výchozích koncových bodech, vazbách a chování najdete v tématu [zjednodušená konfigurace](../simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="a9b67-145">For more information about default endpoints, bindings, and behaviors, see [Simplified Configuration](../simplified-configuration.md) and [Simplified Configuration for WCF Services](../samples/simplified-configuration-for-wcf-services.md).</span></span>

## <a name="install-and-run-the-service"></a><span data-ttu-id="a9b67-146">Instalace a spuštění služby</span><span class="sxs-lookup"><span data-stu-id="a9b67-146">Install and run the service</span></span>

1. <span data-ttu-id="a9b67-147">Sestavte řešení pro vytvoření `Service.exe` spustitelného souboru.</span><span class="sxs-lookup"><span data-stu-id="a9b67-147">Build the solution to create the `Service.exe` executable.</span></span>

2. <span data-ttu-id="a9b67-148">Otevřete Developer Command Prompt pro Visual Studio a přejděte do adresáře projektu.</span><span class="sxs-lookup"><span data-stu-id="a9b67-148">Open Developer Command Prompt for Visual Studio and navigate to the project directory.</span></span> <span data-ttu-id="a9b67-149">`installutil bin\service.exe`Do příkazového řádku zadejte příkaz pro instalaci služby systému Windows.</span><span class="sxs-lookup"><span data-stu-id="a9b67-149">Type `installutil bin\service.exe` at the command prompt to install the Windows service.</span></span>

     <span data-ttu-id="a9b67-150">`services.msc`Pro přístup ke Správci řízení služeb (SCM) zadejte na příkazovém řádku.</span><span class="sxs-lookup"><span data-stu-id="a9b67-150">Type `services.msc` at the command prompt to access the Service Control Manager (SCM).</span></span> <span data-ttu-id="a9b67-151">Služba systému Windows by se měla zobrazit v části služby jako "WCFWindowsServiceSample".</span><span class="sxs-lookup"><span data-stu-id="a9b67-151">The Windows service should appear in Services as "WCFWindowsServiceSample".</span></span> <span data-ttu-id="a9b67-152">Služba WCF může reagovat jenom na klienty, pokud je spuštěná služba systému Windows.</span><span class="sxs-lookup"><span data-stu-id="a9b67-152">The WCF service can only respond to clients if the Windows service is running.</span></span> <span data-ttu-id="a9b67-153">Chcete-li službu spustit, klikněte na ni pravým tlačítkem myši a vyberte Start nebo zadejte do příkazového řádku příkaz **net start WCFWindowsServiceSample** .</span><span class="sxs-lookup"><span data-stu-id="a9b67-153">To start the service, right-click it in the SCM and select "Start", or type **net start WCFWindowsServiceSample** at the command prompt.</span></span>

3. <span data-ttu-id="a9b67-154">Pokud provedete změny služby, musíte ji nejdřív zastavit a odinstalovat.</span><span class="sxs-lookup"><span data-stu-id="a9b67-154">If you make changes to the service, you must first stop it and uninstall it.</span></span> <span data-ttu-id="a9b67-155">Chcete-li službu zastavit, klikněte pravým tlačítkem myši na službu v SCM a vyberte stop (zastavit) nebo do příkazového řádku **zadejte net stop WCFWindowsServiceSample** .</span><span class="sxs-lookup"><span data-stu-id="a9b67-155">To stop the service, right-click the service in the SCM and select "Stop", or **type net stop WCFWindowsServiceSample** at the command prompt.</span></span> <span data-ttu-id="a9b67-156">Všimněte si, že pokud zastavíte službu systému Windows a potom spustíte klienta, <xref:System.ServiceModel.EndpointNotFoundException> dojde k výjimce, když se klient pokusí o přístup ke službě.</span><span class="sxs-lookup"><span data-stu-id="a9b67-156">Note that if you stop the Windows service and then run a client, an <xref:System.ServiceModel.EndpointNotFoundException> exception occurs when a client attempts to access the service.</span></span> <span data-ttu-id="a9b67-157">Chcete-li odinstalovat typ služby systému Windows **Installutil/u bin\service.exe** v příkazovém řádku.</span><span class="sxs-lookup"><span data-stu-id="a9b67-157">To uninstall the Windows service type **installutil /u bin\service.exe** at the command prompt.</span></span>

## <a name="example"></a><span data-ttu-id="a9b67-158">Příklad</span><span class="sxs-lookup"><span data-stu-id="a9b67-158">Example</span></span>

<span data-ttu-id="a9b67-159">Následuje úplný seznam kódu používaného v tomto tématu:</span><span class="sxs-lookup"><span data-stu-id="a9b67-159">The following is a complete listing of the code used by this topic:</span></span>

[!code-csharp[c_HowTo_HostInNTService#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#8)]
[!code-vb[c_HowTo_HostInNTService#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#8)]

<span data-ttu-id="a9b67-160">Stejně jako možnost samoobslužné hostování vyžaduje hostující prostředí služby systému Windows, aby byl jako součást aplikace napsán nějaký hostitelský kód.</span><span class="sxs-lookup"><span data-stu-id="a9b67-160">Like the "Self-Hosting" option, the Windows service hosting environment requires that some hosting code be written as part of the application.</span></span> <span data-ttu-id="a9b67-161">Služba je implementována jako Konzolová aplikace a obsahuje svůj vlastní hostitelský kód.</span><span class="sxs-lookup"><span data-stu-id="a9b67-161">The service is implemented as a console application and contains its own hosting code.</span></span> <span data-ttu-id="a9b67-162">V jiných hostitelských prostředích, jako je služba Aktivace procesů systému Windows (WAS) v Internetová informační služba (IIS), není nutné, aby vývojáři mohli psát hostující kód.</span><span class="sxs-lookup"><span data-stu-id="a9b67-162">In other hosting environments, such as Windows Process Activation Service (WAS) hosting in Internet Information Services (IIS), it is not necessary for developers to write hosting code.</span></span>

## <a name="see-also"></a><span data-ttu-id="a9b67-163">Viz také</span><span class="sxs-lookup"><span data-stu-id="a9b67-163">See also</span></span>

- [<span data-ttu-id="a9b67-164">Zjednodušená konfigurace</span><span class="sxs-lookup"><span data-stu-id="a9b67-164">Simplified Configuration</span></span>](../simplified-configuration.md)
- [<span data-ttu-id="a9b67-165">Hostování ve spravované aplikaci</span><span class="sxs-lookup"><span data-stu-id="a9b67-165">Hosting in a Managed Application</span></span>](hosting-in-a-managed-application.md)
- [<span data-ttu-id="a9b67-166">Služby hostování</span><span class="sxs-lookup"><span data-stu-id="a9b67-166">Hosting Services</span></span>](../hosting-services.md)
- <span data-ttu-id="a9b67-167">[Funkce hostování technologie Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677189(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="a9b67-167">[Windows Server App Fabric Hosting Features](https://docs.microsoft.com/previous-versions/appfabric/ee677189(v=azure.10))</span></span>
