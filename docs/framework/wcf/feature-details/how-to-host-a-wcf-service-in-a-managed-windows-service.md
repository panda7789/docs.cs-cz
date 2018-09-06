---
title: 'Postupy: Hostování služby WCF ve spravované službě Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8e37363b-4dad-4fb6-907f-73c30fac1d9a
ms.openlocfilehash: edbc67ddf20eee6ebbe9091faa43bc1de91809d2
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43786164"
---
# <a name="how-to-host-a-wcf-service-in-a-managed-windows-service"></a><span data-ttu-id="6f910-102">Postupy: Hostování služby WCF ve spravované službě Windows</span><span class="sxs-lookup"><span data-stu-id="6f910-102">How to: Host a WCF Service in a Managed Windows Service</span></span>

<span data-ttu-id="6f910-103">Toto téma popisuje základní kroky potřebné k vytvoření služby Windows Communication Foundation (WCF), který je hostitelem služby Windows.</span><span class="sxs-lookup"><span data-stu-id="6f910-103">This topic outlines the basic steps required to create a Windows Communication Foundation (WCF) service that is hosted by a Windows Service.</span></span> <span data-ttu-id="6f910-104">Ve scénáři zajišťuje hostování možnost, která je dlouho běžící služby WCF hostované mimo Internetové informační služby (IIS) v zabezpečeném prostředí, který není zpráva aktivuje spravované služby Windows.</span><span class="sxs-lookup"><span data-stu-id="6f910-104">The scenario is enabled by the managed Windows service hosting option that is a long-running WCF service hosted outside of Internet Information Services (IIS) in a secure environment that is not message activated.</span></span> <span data-ttu-id="6f910-105">Doba platnosti služby je místo toho řídí operační systém.</span><span class="sxs-lookup"><span data-stu-id="6f910-105">The lifetime of the service is controlled instead by the operating system.</span></span> <span data-ttu-id="6f910-106">Tato možnost hostování je k dispozici ve všech verzích Windows.</span><span class="sxs-lookup"><span data-stu-id="6f910-106">This hosting option is available in all versions of Windows.</span></span>

<span data-ttu-id="6f910-107">Windows services můžete spravovat pomocí Microsoft.ManagementConsole.SnapIn v konzole Microsoft Management Console (MMC) a dá se nespustí automaticky při spuštění systému.</span><span class="sxs-lookup"><span data-stu-id="6f910-107">Windows services can be managed with the Microsoft.ManagementConsole.SnapIn in Microsoft Management Console (MMC) and can be configured to start up automatically when the system boots up.</span></span> <span data-ttu-id="6f910-108">Tato možnost hostování se skládá z registrace domény aplikace (AppDomain), který je hostitelem služby WCF je spravovaná služba Windows tak, že doba platnosti procesu služby se řídí podle správce řízení služeb (SCM) pro služby Windows.</span><span class="sxs-lookup"><span data-stu-id="6f910-108">This hosting option consists of registering the application domain (AppDomain) that hosts a WCF service as a managed Windows service so that the process lifetime of the service is controlled by the Service Control Manager (SCM) for Windows services.</span></span>

<span data-ttu-id="6f910-109">Kód služby obsahuje implementace služby kontraktu služby, služby Windows třídy a třídu Instalační služby.</span><span class="sxs-lookup"><span data-stu-id="6f910-109">The service code includes a service implementation of the service contract, a Windows Service class, and an installer class.</span></span> <span data-ttu-id="6f910-110">Třída implementace služby `CalculatorService`, je služba WCF.</span><span class="sxs-lookup"><span data-stu-id="6f910-110">The service implementation class, `CalculatorService`, is a WCF service.</span></span> <span data-ttu-id="6f910-111">`CalculatorWindowsService` Je služba Windows.</span><span class="sxs-lookup"><span data-stu-id="6f910-111">The `CalculatorWindowsService` is a Windows service.</span></span> <span data-ttu-id="6f910-112">K získání způsobilosti jako služba Windows, třída dědí z `ServiceBase` a implementuje `OnStart` a `OnStop` metody.</span><span class="sxs-lookup"><span data-stu-id="6f910-112">To qualify as a Windows service, the class inherits from `ServiceBase` and implements the `OnStart` and `OnStop` methods.</span></span> <span data-ttu-id="6f910-113">V `OnStart`, <xref:System.ServiceModel.ServiceHost> se vytvoří pro `CalculatorService` zadejte a otevřít.</span><span class="sxs-lookup"><span data-stu-id="6f910-113">In `OnStart`, a <xref:System.ServiceModel.ServiceHost> is created for the `CalculatorService` type and opened.</span></span> <span data-ttu-id="6f910-114">V `OnStop`, služba je zastaven a odstraněn.</span><span class="sxs-lookup"><span data-stu-id="6f910-114">In `OnStop`, the service is stopped and disposed.</span></span> <span data-ttu-id="6f910-115">Hostitel je také odpovídají za poskytování základní adresu k hostiteli služby, který je nakonfigurovaný v nastavení aplikace.</span><span class="sxs-lookup"><span data-stu-id="6f910-115">The host is also responsible for providing a base address to the service host, which has been configured in application settings.</span></span> <span data-ttu-id="6f910-116">Instalační třída, která dědí z <xref:System.Configuration.Install.Installer>, umožňuje programu nainstalovat jako službu Windows pomocí nástroje Installutil.exe.</span><span class="sxs-lookup"><span data-stu-id="6f910-116">The installer class, which inherits from <xref:System.Configuration.Install.Installer>, allows the program to be installed as a Windows service by the Installutil.exe tool.</span></span>

## <a name="construct-the-service-and-provide-the-hosting-code"></a><span data-ttu-id="6f910-117">Vytvoření služby a zadejte kód hostování</span><span class="sxs-lookup"><span data-stu-id="6f910-117">Construct the service and provide the hosting code</span></span>

1.  <span data-ttu-id="6f910-118">Vytvořit novou sadu Visual Studio **konzolovou aplikaci** projekt s názvem **služby**.</span><span class="sxs-lookup"><span data-stu-id="6f910-118">Create a new Visual Studio **Console app** project called **Service**.</span></span>

2.  <span data-ttu-id="6f910-119">Přejmenujte soubor Program.cs Service.cs.</span><span class="sxs-lookup"><span data-stu-id="6f910-119">Rename Program.cs to Service.cs.</span></span>

3.  <span data-ttu-id="6f910-120">Změna oboru názvů `Microsoft.ServiceModel.Samples`.</span><span class="sxs-lookup"><span data-stu-id="6f910-120">Change the namespace to `Microsoft.ServiceModel.Samples`.</span></span>

4.  <span data-ttu-id="6f910-121">Přidejte odkazy na následující sestavení:</span><span class="sxs-lookup"><span data-stu-id="6f910-121">Add references to the following assemblies:</span></span>

    - <span data-ttu-id="6f910-122">System.ServiceModel.dll</span><span class="sxs-lookup"><span data-stu-id="6f910-122">System.ServiceModel.dll</span></span>

    - <span data-ttu-id="6f910-123">System.ServiceProcess.dll</span><span class="sxs-lookup"><span data-stu-id="6f910-123">System.ServiceProcess.dll</span></span>

    - <span data-ttu-id="6f910-124">System.Configuration.Install.dll</span><span class="sxs-lookup"><span data-stu-id="6f910-124">System.Configuration.Install.dll</span></span>

5.  <span data-ttu-id="6f910-125">Přidejte následující příkazy using do Service.cs.</span><span class="sxs-lookup"><span data-stu-id="6f910-125">Add the following using statements to Service.cs.</span></span>

     [!code-csharp[c_HowTo_HostInNTService#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#0)]
     [!code-vb[c_HowTo_HostInNTService#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#0)]

6.  <span data-ttu-id="6f910-126">Definovat `ICalculator` kontraktu služby, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="6f910-126">Define the `ICalculator` service contract as shown in the following code.</span></span>

     [!code-csharp[c_HowTo_HostInNTService#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#1)]
     [!code-vb[c_HowTo_HostInNTService#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#1)]

7.  <span data-ttu-id="6f910-127">Implementace kontraktu služby ve třídě volá `CalculatorService` jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="6f910-127">Implement the service contract in a class called `CalculatorService` as shown in the following code.</span></span>

     [!code-csharp[c_HowTo_HostInNTService#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#2)]
     [!code-vb[c_HowTo_HostInNTService#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#2)]

8.  <span data-ttu-id="6f910-128">Vytvořit novou třídu s názvem `CalculatorWindowsService` , která dědí z <xref:System.ServiceProcess.ServiceBase> třídy.</span><span class="sxs-lookup"><span data-stu-id="6f910-128">Create a new class called `CalculatorWindowsService` that inherits from the <xref:System.ServiceProcess.ServiceBase> class.</span></span> <span data-ttu-id="6f910-129">Přidat místní proměnnou s názvem `serviceHost` na odkaz <xref:System.ServiceModel.ServiceHost> instance.</span><span class="sxs-lookup"><span data-stu-id="6f910-129">Add a local variable called `serviceHost` to reference the <xref:System.ServiceModel.ServiceHost> instance.</span></span> <span data-ttu-id="6f910-130">Definovat `Main` metodu, která volá `ServiceBase.Run(new CalculatorWindowsService)`</span><span class="sxs-lookup"><span data-stu-id="6f910-130">Define the `Main` method that calls `ServiceBase.Run(new CalculatorWindowsService)`</span></span>

     [!code-csharp[c_HowTo_HostInNTService#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#3)]
     [!code-vb[c_HowTo_HostInNTService#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#3)]

9. <span data-ttu-id="6f910-131">Přepsat <xref:System.ServiceProcess.ServiceBase.OnStart%28System.String%5B%5D%29> metody vytvoření a otevřením nového <xref:System.ServiceModel.ServiceHost> instance, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="6f910-131">Override the <xref:System.ServiceProcess.ServiceBase.OnStart%28System.String%5B%5D%29> method by creating and opening a new <xref:System.ServiceModel.ServiceHost> instance as shown in the following code.</span></span>

     [!code-csharp[c_HowTo_HostInNTService#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#4)]
     [!code-vb[c_HowTo_HostInNTService#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#4)]

10. <span data-ttu-id="6f910-132">Přepsat <xref:System.ServiceProcess.ServiceBase.OnStop%2A> ukončovací metoda <xref:System.ServiceModel.ServiceHost> jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="6f910-132">Override the <xref:System.ServiceProcess.ServiceBase.OnStop%2A> method closing the <xref:System.ServiceModel.ServiceHost> as shown in the following code.</span></span>

     [!code-csharp[c_HowTo_HostInNTService#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#5)]
     [!code-vb[c_HowTo_HostInNTService#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#5)]

11. <span data-ttu-id="6f910-133">Vytvořit novou třídu s názvem `ProjectInstaller` , která dědí z <xref:System.Configuration.Install.Installer> a, který je označený <xref:System.ComponentModel.RunInstallerAttribute> nastavena na `true`.</span><span class="sxs-lookup"><span data-stu-id="6f910-133">Create a new class called `ProjectInstaller` that inherits from <xref:System.Configuration.Install.Installer> and that is marked with the <xref:System.ComponentModel.RunInstallerAttribute> set to `true`.</span></span> <span data-ttu-id="6f910-134">To umožňuje službě Windows a nainstalovat nástroj Installutil.exe.</span><span class="sxs-lookup"><span data-stu-id="6f910-134">This allows the Windows service to be installed by the Installutil.exe tool.</span></span>

     [!code-csharp[c_HowTo_HostInNTService#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#6)]
     [!code-vb[c_HowTo_HostInNTService#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#6)]

12. <span data-ttu-id="6f910-135">Odeberte `Service` třídu, která byla vygenerována při vytváření projektu.</span><span class="sxs-lookup"><span data-stu-id="6f910-135">Remove the `Service` class that was generated when you created the project.</span></span>

13. <span data-ttu-id="6f910-136">Přidání konfiguračního souboru aplikace do projektu.</span><span class="sxs-lookup"><span data-stu-id="6f910-136">Add an application configuration file to the project.</span></span> <span data-ttu-id="6f910-137">Obsah souboru nahraďte následujícím konfiguračním souboru XML.</span><span class="sxs-lookup"><span data-stu-id="6f910-137">Replace the contents of the file with the following configuration XML.</span></span>

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

     <span data-ttu-id="6f910-138">V souboru App.config klikněte pravým tlačítkem myši **Průzkumníka řešení** a vyberte **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="6f910-138">Right click the App.config file in the **Solution Explorer** and select **Properties**.</span></span> <span data-ttu-id="6f910-139">V části **kopírovat do výstupního adresáře** vyberte **kopírovat, pokud je novější**.</span><span class="sxs-lookup"><span data-stu-id="6f910-139">Under **Copy to Output Directory** select **Copy if Newer**.</span></span>

     <span data-ttu-id="6f910-140">Tento příklad explicitně určuje koncové body v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="6f910-140">This example explicitly specifies endpoints in the configuration file.</span></span> <span data-ttu-id="6f910-141">Pokud nemůžete přidat žádné koncové body pro službu, modulu runtime přidá výchozí koncové body za vás.</span><span class="sxs-lookup"><span data-stu-id="6f910-141">If you do not add any endpoints to the service, the runtime adds default endpoints for you.</span></span> <span data-ttu-id="6f910-142">V tomto příkladě vzhledem k tomu, že služba má <xref:System.ServiceModel.Description.ServiceMetadataBehavior> nastavena na `true`, vaše služba má také povoleno publikování metadat.</span><span class="sxs-lookup"><span data-stu-id="6f910-142">In this example, because the service has a <xref:System.ServiceModel.Description.ServiceMetadataBehavior> set to `true`, your service also has publishing metadata enabled.</span></span> <span data-ttu-id="6f910-143">Další informace o výchozí koncové body, vazby a chování najdete v tématu [zjednodušená konfigurace](../../../../docs/framework/wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="6f910-143">For more information about default endpoints, bindings, and behaviors, see [Simplified Configuration](../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>

## <a name="install-and-run-the-service"></a><span data-ttu-id="6f910-144">Instalace a spuštění služby</span><span class="sxs-lookup"><span data-stu-id="6f910-144">Install and run the service</span></span>

1.  <span data-ttu-id="6f910-145">Sestavte řešení k vytvoření `Service.exe` spustitelný soubor.</span><span class="sxs-lookup"><span data-stu-id="6f910-145">Build the solution to create the `Service.exe` executable.</span></span>

2.  <span data-ttu-id="6f910-146">Otevřete Developer Command Prompt pro sadu Visual Studio a přejděte do adresáře projektu.</span><span class="sxs-lookup"><span data-stu-id="6f910-146">Open Developer Command Prompt for Visual Studio and navigate to the project directory.</span></span> <span data-ttu-id="6f910-147">Typ `installutil bin\service.exe` příkazového řádku pro instalaci služby Windows.</span><span class="sxs-lookup"><span data-stu-id="6f910-147">Type `installutil bin\service.exe` at the command prompt to install the Windows service.</span></span>

     <span data-ttu-id="6f910-148">Typ `services.msc` příkazového řádku pro přístup k správce řízení služeb (SCM).</span><span class="sxs-lookup"><span data-stu-id="6f910-148">Type `services.msc` at the command prompt to access the Service Control Manager (SCM).</span></span> <span data-ttu-id="6f910-149">Služba Windows by se zobrazit v služby jako "WCFWindowsServiceSample".</span><span class="sxs-lookup"><span data-stu-id="6f910-149">The Windows service should appear in Services as "WCFWindowsServiceSample".</span></span> <span data-ttu-id="6f910-150">Služby WCF můžete reagovat jen na klienty, pokud je služba Windows spuštěná.</span><span class="sxs-lookup"><span data-stu-id="6f910-150">The WCF service can only respond to clients if the Windows service is running.</span></span> <span data-ttu-id="6f910-151">Spustit službu, klikněte pravým tlačítkem na ho v SCM a vyberte možnost "Spustit" nebo typ **net start WCFWindowsServiceSample** příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="6f910-151">To start the service, right-click it in the SCM and select "Start", or type **net start WCFWindowsServiceSample** at the command prompt.</span></span>

3.  <span data-ttu-id="6f910-152">Pokud provedete změny ve službě, musíte ji zastavit a odinstalujte ho.</span><span class="sxs-lookup"><span data-stu-id="6f910-152">If you make changes to the service, you must first stop it and uninstall it.</span></span> <span data-ttu-id="6f910-153">Zastavte službu, klikněte pravým tlačítkem na službu v SCM a vyberte "Stop", nebo **typ net stop WCFWindowsServiceSample** příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="6f910-153">To stop the service, right-click the service in the SCM and select "Stop", or **type net stop WCFWindowsServiceSample** at the command prompt.</span></span> <span data-ttu-id="6f910-154">Všimněte si, že pokud zastavíte službu Windows a pak spusťte klienta, <xref:System.ServiceModel.EndpointNotFoundException> dojde k výjimce, když se klient pokusí o přístup ke službě.</span><span class="sxs-lookup"><span data-stu-id="6f910-154">Note that if you stop the Windows service and then run a client, an <xref:System.ServiceModel.EndpointNotFoundException> exception occurs when a client attempts to access the service.</span></span> <span data-ttu-id="6f910-155">Chcete-li odinstalovat typ služby Windows **installutil /u bin\service.exe** příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="6f910-155">To uninstall the Windows service type **installutil /u bin\service.exe** at the command prompt.</span></span>

## <a name="example"></a><span data-ttu-id="6f910-156">Příklad</span><span class="sxs-lookup"><span data-stu-id="6f910-156">Example</span></span>

<span data-ttu-id="6f910-157">Tady je úplný seznam všech kód použitý v tomto tématu:</span><span class="sxs-lookup"><span data-stu-id="6f910-157">The following is a complete listing of the code used by this topic:</span></span>

[!code-csharp[c_HowTo_HostInNTService#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#8)]
[!code-vb[c_HowTo_HostInNTService#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#8)]

<span data-ttu-id="6f910-158">Podobně jako možnost "Samoobslužné hostování" hostitelským prostředím služby Windows vyžaduje, že některé kód hostování se zapisují jako součást aplikace.</span><span class="sxs-lookup"><span data-stu-id="6f910-158">Like the "Self-Hosting" option, the Windows service hosting environment requires that some hosting code be written as part of the application.</span></span> <span data-ttu-id="6f910-159">Služba se implementuje jako konzolovou aplikaci a obsahuje vlastní kód hostování.</span><span class="sxs-lookup"><span data-stu-id="6f910-159">The service is implemented as a console application and contains its own hosting code.</span></span> <span data-ttu-id="6f910-160">V jiných hostitelských prostředích, jako je například Windows Process Activation Service (WAS) hostování v Internetové informační služby (IIS), není nutné pro vývojářům umožňuje psát kód hostování.</span><span class="sxs-lookup"><span data-stu-id="6f910-160">In other hosting environments, such as Windows Process Activation Service (WAS) hosting in Internet Information Services (IIS), it is not necessary for developers to write hosting code.</span></span>

## <a name="see-also"></a><span data-ttu-id="6f910-161">Viz také</span><span class="sxs-lookup"><span data-stu-id="6f910-161">See Also</span></span>

- [<span data-ttu-id="6f910-162">Zjednodušená konfigurace</span><span class="sxs-lookup"><span data-stu-id="6f910-162">Simplified Configuration</span></span>](../../../../docs/framework/wcf/simplified-configuration.md)
- [<span data-ttu-id="6f910-163">Hostování ve spravované aplikaci</span><span class="sxs-lookup"><span data-stu-id="6f910-163">Hosting in a Managed Application</span></span>](../../../../docs/framework/wcf/feature-details/hosting-in-a-managed-application.md)
- [<span data-ttu-id="6f910-164">Služby hostování</span><span class="sxs-lookup"><span data-stu-id="6f910-164">Hosting Services</span></span>](../../../../docs/framework/wcf/hosting-services.md)
- [<span data-ttu-id="6f910-165">Hostování funkcí systému Windows Server App Fabric</span><span class="sxs-lookup"><span data-stu-id="6f910-165">Windows Server App Fabric Hosting Features</span></span>](https://go.microsoft.com/fwlink/?LinkId=201276)