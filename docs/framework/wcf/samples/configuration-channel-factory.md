---
title: Postup konfiguračního kanálu
ms.date: 03/30/2017
ms.assetid: 3b749493-bd8a-4ccb-893e-5948901a1486
ms.openlocfilehash: 1a236f1812d3124e83702a97e1877b7fec10be64
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74715494"
---
# <a name="configuration-channel-factory"></a><span data-ttu-id="66075-102">Postup konfiguračního kanálu</span><span class="sxs-lookup"><span data-stu-id="66075-102">Configuration Channel Factory</span></span>
<span data-ttu-id="66075-103">Tato ukázka pokrývá použití <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601>.</span><span class="sxs-lookup"><span data-stu-id="66075-103">This sample covers the usage of the <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601>.</span></span> <span data-ttu-id="66075-104"><xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> umožňuje centrální správu konfigurace klienta WCF.</span><span class="sxs-lookup"><span data-stu-id="66075-104">The <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> allows central management of WCF client configuration.</span></span> <span data-ttu-id="66075-105">To může být užitečné také ve scénářích, kdy je konfigurace vybrána nebo změněna po dobu načtení domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="66075-105">This can also be useful in scenarios in which configuration is selected or changed after the application domain load time.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="66075-106">Demonstruje</span><span class="sxs-lookup"><span data-stu-id="66075-106">Demonstrates</span></span>
 <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601>

## <a name="discussion"></a><span data-ttu-id="66075-107">Účely</span><span class="sxs-lookup"><span data-stu-id="66075-107">Discussion</span></span>
 <span data-ttu-id="66075-108">V této ukázce se dozvíte, jak pomocí <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> přidat konkrétní konfigurační soubor do klientské aplikace, aniž byste museli použít výchozí konfigurační soubor aplikace.</span><span class="sxs-lookup"><span data-stu-id="66075-108">This sample shows how to use <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> to add a particular configuration file to a client application, without having to use the default application configuration file.</span></span>

 <span data-ttu-id="66075-109">Vzorek se skládá ze dvou projektů.</span><span class="sxs-lookup"><span data-stu-id="66075-109">The sample consists of two projects.</span></span> <span data-ttu-id="66075-110">Prvním projektem je jednoduchá služba, která se používá k odpovědi na zprávy přicházející od klientů.</span><span class="sxs-lookup"><span data-stu-id="66075-110">The first project is a simple service that runs to reply to messages coming from the clients.</span></span> <span data-ttu-id="66075-111">Druhý projekt je klientská aplikace, která vytváří dva <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> objekty pomocí <xref:System.Configuration.ExeConfigurationFileMap> pro konfigurační soubor test. config a používá je ke komunikaci se službou.</span><span class="sxs-lookup"><span data-stu-id="66075-111">The second project is a client application that builds two <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> objects using a <xref:System.Configuration.ExeConfigurationFileMap> for the Test.config configuration file and uses them to communicate with the service.</span></span> <span data-ttu-id="66075-112">Oba klienti komunikují se službou pomocí konfigurace zadané v souboru Test. config.</span><span class="sxs-lookup"><span data-stu-id="66075-112">Both clients communicate with the service using the configuration specified in Test.config.</span></span>

 <span data-ttu-id="66075-113">Následující kód přidá vlastní konfigurační soubor do klientské aplikace.</span><span class="sxs-lookup"><span data-stu-id="66075-113">The following code adds a custom configuration file to a client application.</span></span>

```csharp
ExeConfigurationFileMap fileMap = new ExeConfigurationFileMap();
fileMap.ExeConfigFilename = "Test.config";
Configuration newConfiguration = ConfigurationManager.OpenMappedExeConfiguration(fileMap, ConfigurationUserLevel.None);

ConfigurationChannelFactory<ICalculatorChannel> factory1 = new ConfigurationChannelFactory<ICalculatorChannel>("endpoint1", newConfiguration, new EndpointAddress("http://localhost:8000/servicemodelsamples/service"));
ICalculatorChannel client1 = factory1.CreateChannel();
```

#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="66075-114">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="66075-114">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="66075-115">Otevřete Visual Studio 2012 s oprávněními správce.</span><span class="sxs-lookup"><span data-stu-id="66075-115">Open Visual Studio 2012 with administrator privileges.</span></span>

2. <span data-ttu-id="66075-116">Klikněte pravým tlačítkem na řešení ConfigurationChannelFactory (2 projekty) a pak vyberte **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="66075-116">Right-click the ConfigurationChannelFactory solution (2 projects) and then select **Properties**.</span></span>

3. <span data-ttu-id="66075-117">V nabídce **běžné vlastnosti**vyberte možnost **projekt po spuštění**a pak klikněte na **více projektů po spuštění**.</span><span class="sxs-lookup"><span data-stu-id="66075-117">In **Common Properties**, select **Startup Project**, and then click **Multiple startup projects**.</span></span>

4. <span data-ttu-id="66075-118">Přesuňte projekt **služby** na začátek seznamu a **akci ' Start '** a poté přesuňte **klientský** projekt za projekt **služby** , a to také pomocí **akce ' spustit '** , takže se **klientský** projekt spustí po projektu **služby** .</span><span class="sxs-lookup"><span data-stu-id="66075-118">Move the **Service** project to the beginning of the list, with the **Action ‘Start’**, and then move the **Client** project after the **Service** project, also with the **Action ‘Start’**, so the **Client** project is executed after the **Service** project.</span></span>

5. <span data-ttu-id="66075-119">Klikněte na **OK**a potom stisknutím klávesy F5 (nebo CTRL + F5) spusťte ukázku.</span><span class="sxs-lookup"><span data-stu-id="66075-119">Click **OK**, and then press F5 (or CTRL+F5) to run the sample.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="66075-120">Ukázky už můžou být na vašem počítači nainstalované.</span><span class="sxs-lookup"><span data-stu-id="66075-120">The samples may already be installed on your machine.</span></span> <span data-ttu-id="66075-121">Než budete pokračovat, vyhledejte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="66075-121">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="66075-122">Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Samples.</span><span class="sxs-lookup"><span data-stu-id="66075-122">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="66075-123">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="66075-123">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\ConfigurationChannelFactory`
