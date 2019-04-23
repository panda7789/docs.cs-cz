---
title: Postup konfiguračního kanálu
ms.date: 03/30/2017
ms.assetid: 3b749493-bd8a-4ccb-893e-5948901a1486
ms.openlocfilehash: 5bee4c7cc2c2e64c6e0d8d0ec2634f9500cd9d51
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2019
ms.locfileid: "59975868"
---
# <a name="configuration-channel-factory"></a><span data-ttu-id="233f3-102">Postup konfiguračního kanálu</span><span class="sxs-lookup"><span data-stu-id="233f3-102">Configuration Channel Factory</span></span>
<span data-ttu-id="233f3-103">Tento příklad zahrnuje použití <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601>.</span><span class="sxs-lookup"><span data-stu-id="233f3-103">This sample covers the usage of the <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601>.</span></span> <span data-ttu-id="233f3-104"><xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> Umožňuje centrální správu z konfigurace klienta WCF.</span><span class="sxs-lookup"><span data-stu-id="233f3-104">The <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> allows central management of WCF client configuration.</span></span> <span data-ttu-id="233f3-105">To může být užitečné v situacích, ve kterých je konfigurace vybrané nebo změnit po dobu načítání domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="233f3-105">This can also be useful in scenarios in which configuration is selected or changed after the application domain load time.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="233f3-106">Demonstruje</span><span class="sxs-lookup"><span data-stu-id="233f3-106">Demonstrates</span></span>
 <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601>

## <a name="discussion"></a><span data-ttu-id="233f3-107">Diskuse</span><span class="sxs-lookup"><span data-stu-id="233f3-107">Discussion</span></span>
 <span data-ttu-id="233f3-108">Tento příklad ukazuje způsob použití <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> přidat konkrétní konfigurační soubor do klientské aplikace, aniž byste museli používat výchozí konfigurační soubor aplikace.</span><span class="sxs-lookup"><span data-stu-id="233f3-108">This sample shows how to use <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> to add a particular configuration file to a client application, without having to use the default application configuration file.</span></span>

 <span data-ttu-id="233f3-109">Vzorek se skládá ze dvou projektů.</span><span class="sxs-lookup"><span data-stu-id="233f3-109">The sample consists of two projects.</span></span> <span data-ttu-id="233f3-110">První projekt je jednoduchou službu, na kterém běží odpovídání na zprávy přicházející z klientů.</span><span class="sxs-lookup"><span data-stu-id="233f3-110">The first project is a simple service that runs to reply to messages coming from the clients.</span></span> <span data-ttu-id="233f3-111">Je druhý projekt klientské aplikace, který vytváří dvě <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> objektů pomocí <xref:System.Configuration.ExeConfigurationFileMap> Test.config konfiguračního souboru a použije je ke komunikaci se službou.</span><span class="sxs-lookup"><span data-stu-id="233f3-111">The second project is a client application that builds two <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> objects using a <xref:System.Configuration.ExeConfigurationFileMap> for the Test.config configuration file and uses them to communicate with the service.</span></span> <span data-ttu-id="233f3-112">Oba klienti komunikaci se službou pomocí zadané v Test.config konfigurace.</span><span class="sxs-lookup"><span data-stu-id="233f3-112">Both clients communicate with the service using the configuration specified in Test.config.</span></span>

 <span data-ttu-id="233f3-113">Následující kód přidá vlastní konfigurační soubor do klientské aplikace.</span><span class="sxs-lookup"><span data-stu-id="233f3-113">The following code adds a custom configuration file to a client application.</span></span>

```csharp
ExeConfigurationFileMap fileMap = new ExeConfigurationFileMap();
fileMap.ExeConfigFilename = "Test.config";
Configuration newConfiguration = ConfigurationManager.OpenMappedExeConfiguration(fileMap, ConfigurationUserLevel.None);

ConfigurationChannelFactory<ICalculatorChannel> factory1 = new ConfigurationChannelFactory<ICalculatorChannel>("endpoint1", newConfiguration, new EndpointAddress("http://localhost:8000/servicemodelsamples/service"));
ICalculatorChannel client1 = factory1.CreateChannel();
```

#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="233f3-114">Chcete-li nastavit, sestavte a spusťte ukázku</span><span class="sxs-lookup"><span data-stu-id="233f3-114">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="233f3-115">Otevřete Visual Studio 2012 s oprávněními správce.</span><span class="sxs-lookup"><span data-stu-id="233f3-115">Open Visual Studio 2012 with administrator privileges.</span></span>

2. <span data-ttu-id="233f3-116">Klikněte pravým tlačítkem na řešení ConfigurationChannelFactory (2 projektů) a pak vyberte **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="233f3-116">Right-click the ConfigurationChannelFactory solution (2 projects) and then select **Properties**.</span></span>

3. <span data-ttu-id="233f3-117">V **společné vlastnosti**vyberte **spouštěný projekt**a potom klikněte na tlačítko **více projektů po spuštění**.</span><span class="sxs-lookup"><span data-stu-id="233f3-117">In **Common Properties**, select **Startup Project**, and then click **Multiple startup projects**.</span></span>

4. <span data-ttu-id="233f3-118">Přesunout **služby** projekt na začátku seznamu, se **akce 'Start'** a poté přesuňte **klienta** projektu po **služby**projektu, také se **akce 'Start'**, takže **klienta** projektu se spustí až po **služby** projektu.</span><span class="sxs-lookup"><span data-stu-id="233f3-118">Move the **Service** project to the beginning of the list, with the **Action ‘Start’**, and then move the **Client** project after the **Service** project, also with the **Action ‘Start’**, so the **Client** project is executed after the **Service** project.</span></span>

5. <span data-ttu-id="233f3-119">Klikněte na tlačítko **OK**a potom stiskněte klávesu F5 (nebo CTRL + F5) ke spuštění ukázky.</span><span class="sxs-lookup"><span data-stu-id="233f3-119">Click **OK**, and then press F5 (or CTRL+F5) to run the sample.</span></span>

> [!IMPORTANT]
>  <span data-ttu-id="233f3-120">Vzorky mohou již být nainstalováno na svém počítači.</span><span class="sxs-lookup"><span data-stu-id="233f3-120">The samples may already be installed on your machine.</span></span> <span data-ttu-id="233f3-121">Před pokračováním zkontrolujte následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="233f3-121">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="233f3-122">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="233f3-122">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="233f3-123">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="233f3-123">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\ConfigurationChannelFactory`
