---
title: Postup konfiguračního kanálu
ms.date: 03/30/2017
ms.assetid: 3b749493-bd8a-4ccb-893e-5948901a1486
ms.openlocfilehash: fc3a564128e520133c2404a82438e692b1381875
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="configuration-channel-factory"></a><span data-ttu-id="99763-102">Postup konfiguračního kanálu</span><span class="sxs-lookup"><span data-stu-id="99763-102">Configuration Channel Factory</span></span>
<span data-ttu-id="99763-103">Tato ukázka obsahuje využití <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601>.</span><span class="sxs-lookup"><span data-stu-id="99763-103">This sample covers the usage of the <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601>.</span></span> <span data-ttu-id="99763-104"><xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> Umožňuje centrální správu konfigurace klienta WCF.</span><span class="sxs-lookup"><span data-stu-id="99763-104">The <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> allows central management of WCF client configuration.</span></span> <span data-ttu-id="99763-105">To může být užitečný ve scénářích, ve kterých je konfigurace vybrali nebo změnit po doba načítání domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="99763-105">This can also be useful in scenarios in which configuration is selected or changed after the application domain load time.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="99763-106">Demonstruje</span><span class="sxs-lookup"><span data-stu-id="99763-106">Demonstrates</span></span>  
 <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601>  
  
## <a name="discussion"></a><span data-ttu-id="99763-107">Diskusní</span><span class="sxs-lookup"><span data-stu-id="99763-107">Discussion</span></span>  
 <span data-ttu-id="99763-108">Tento příklad ukazuje způsob použití <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> přidat konkrétní konfigurační soubor do klientské aplikace, aniž byste museli použít výchozí konfigurační soubor aplikace.</span><span class="sxs-lookup"><span data-stu-id="99763-108">This sample shows how to use <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> to add a particular configuration file to a client application, without having to use the default application configuration file.</span></span>  
  
 <span data-ttu-id="99763-109">Ukázkový soubor obsahuje dva projekty.</span><span class="sxs-lookup"><span data-stu-id="99763-109">The sample consists of two projects.</span></span> <span data-ttu-id="99763-110">První projekt je jednoduchý služba, která běží na odpovědi na zprávy přicházející z klientů.</span><span class="sxs-lookup"><span data-stu-id="99763-110">The first project is a simple service that runs to reply to messages coming from the clients.</span></span> <span data-ttu-id="99763-111">Druhý projekt je klientská aplikace, která vytvoří dvě <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> objekty pomocí <xref:System.Configuration.ExeConfigurationFileMap> Test.config konfiguračního souboru a použije je k komunikovat se službou.</span><span class="sxs-lookup"><span data-stu-id="99763-111">The second project is a client application that builds two <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> objects using a <xref:System.Configuration.ExeConfigurationFileMap> for the Test.config configuration file and uses them to communicate with the service.</span></span> <span data-ttu-id="99763-112">Oba klienti komunikovat se službou pomocí konfigurace zadaná v Test.config.</span><span class="sxs-lookup"><span data-stu-id="99763-112">Both clients communicate with the service using the configuration specified in Test.config.</span></span>  
  
 <span data-ttu-id="99763-113">Následující kód přidá vlastní konfigurační soubor do klientské aplikace.</span><span class="sxs-lookup"><span data-stu-id="99763-113">The following code adds a custom configuration file to a client application.</span></span>  
  
```  
ExeConfigurationFileMap fileMap = new ExeConfigurationFileMap();  
fileMap.ExeConfigFilename = "Test.config";  
Configuration newConfiguration = ConfigurationManager.OpenMappedExeConfiguration(fileMap, ConfigurationUserLevel.None);  
  
ConfigurationChannelFactory<ICalculatorChannel> factory1 = new ConfigurationChannelFactory<ICalculatorChannel>("endpoint1", newConfiguration, new EndpointAddress("http://localhost:8000/servicemodelsamples/service"));  
ICalculatorChannel client1 = factory1.CreateChannel();  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="99763-114">Pokud chcete nastavit, sestavit a spustit ukázku</span><span class="sxs-lookup"><span data-stu-id="99763-114">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="99763-115">Otevřete [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] s oprávněními správce.</span><span class="sxs-lookup"><span data-stu-id="99763-115">Open [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] with administrator privileges.</span></span>  
  
2.  <span data-ttu-id="99763-116">Klikněte pravým tlačítkem na řešení ConfigurationChannelFactory (2 projektů) a potom vyberte **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="99763-116">Right-click the ConfigurationChannelFactory solution (2 projects) and then select **Properties**.</span></span>  
  
3.  <span data-ttu-id="99763-117">V **společných vlastností**, vyberte **spouštěný projekt**a potom klikněte na **více projektů po spuštění**.</span><span class="sxs-lookup"><span data-stu-id="99763-117">In **Common Properties**, select **Startup Project**, and then click **Multiple startup projects**.</span></span>  
  
4.  <span data-ttu-id="99763-118">Přesunout **služby** projektu na začátek seznamu, s **akce 'Start'** a poté přesuňte **klienta** projektu po **služby**projektu, také s **akce 'Start'**, proto **klienta** projektu se spustí až po **služby** projektu.</span><span class="sxs-lookup"><span data-stu-id="99763-118">Move the **Service** project to the beginning of the list, with the **Action ‘Start’**, and then move the **Client** project after the **Service** project, also with the **Action ‘Start’**, so the **Client** project is executed after the **Service** project.</span></span>  
  
5.  <span data-ttu-id="99763-119">Klikněte na tlačítko **OK**a potom stiskněte klávesu F5 (nebo CTRL + F5) ke spuštění ukázky.</span><span class="sxs-lookup"><span data-stu-id="99763-119">Click **OK**, and then press F5 (or CTRL+F5) to run the sample.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="99763-120">Ukázky může být již nainstalována na váš počítač.</span><span class="sxs-lookup"><span data-stu-id="99763-120">The samples may already be installed on your machine.</span></span> <span data-ttu-id="99763-121">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="99763-121">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="99763-122">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="99763-122">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="99763-123">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="99763-123">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\ConfigurationChannelFactory`
