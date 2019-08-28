---
title: Postup konfiguračního kanálu
ms.date: 03/30/2017
ms.assetid: 3b749493-bd8a-4ccb-893e-5948901a1486
ms.openlocfilehash: 1b74c15599ebc932a2a0ed46d646b54bec986794
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2019
ms.locfileid: "70045645"
---
# <a name="configuration-channel-factory"></a><span data-ttu-id="421c2-102">Postup konfiguračního kanálu</span><span class="sxs-lookup"><span data-stu-id="421c2-102">Configuration Channel Factory</span></span>
<span data-ttu-id="421c2-103">Tato ukázka se zabývá využitím <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601>.</span><span class="sxs-lookup"><span data-stu-id="421c2-103">This sample covers the usage of the <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601>.</span></span> <span data-ttu-id="421c2-104"><xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> Umožňuje centrální správu konfigurace klienta WCF.</span><span class="sxs-lookup"><span data-stu-id="421c2-104">The <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> allows central management of WCF client configuration.</span></span> <span data-ttu-id="421c2-105">To může být užitečné také ve scénářích, kdy je konfigurace vybrána nebo změněna po dobu načtení domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="421c2-105">This can also be useful in scenarios in which configuration is selected or changed after the application domain load time.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="421c2-106">Demonstruje</span><span class="sxs-lookup"><span data-stu-id="421c2-106">Demonstrates</span></span>
 <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601>

## <a name="discussion"></a><span data-ttu-id="421c2-107">Účely</span><span class="sxs-lookup"><span data-stu-id="421c2-107">Discussion</span></span>
 <span data-ttu-id="421c2-108">V této ukázce se dozvíte <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> , jak použít k přidání konkrétního konfiguračního souboru do klientské aplikace, aniž byste museli použít výchozí konfigurační soubor aplikace.</span><span class="sxs-lookup"><span data-stu-id="421c2-108">This sample shows how to use <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> to add a particular configuration file to a client application, without having to use the default application configuration file.</span></span>

 <span data-ttu-id="421c2-109">Vzorek se skládá ze dvou projektů.</span><span class="sxs-lookup"><span data-stu-id="421c2-109">The sample consists of two projects.</span></span> <span data-ttu-id="421c2-110">Prvním projektem je jednoduchá služba, která se používá k odpovědi na zprávy přicházející od klientů.</span><span class="sxs-lookup"><span data-stu-id="421c2-110">The first project is a simple service that runs to reply to messages coming from the clients.</span></span> <span data-ttu-id="421c2-111">Druhý projekt je klientská aplikace, která vytváří dva <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> objekty <xref:System.Configuration.ExeConfigurationFileMap> pomocí nástroje pro konfigurační soubor test. config a používá je ke komunikaci se službou.</span><span class="sxs-lookup"><span data-stu-id="421c2-111">The second project is a client application that builds two <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> objects using a <xref:System.Configuration.ExeConfigurationFileMap> for the Test.config configuration file and uses them to communicate with the service.</span></span> <span data-ttu-id="421c2-112">Oba klienti komunikují se službou pomocí konfigurace zadané v souboru Test. config.</span><span class="sxs-lookup"><span data-stu-id="421c2-112">Both clients communicate with the service using the configuration specified in Test.config.</span></span>

 <span data-ttu-id="421c2-113">Následující kód přidá vlastní konfigurační soubor do klientské aplikace.</span><span class="sxs-lookup"><span data-stu-id="421c2-113">The following code adds a custom configuration file to a client application.</span></span>

```csharp
ExeConfigurationFileMap fileMap = new ExeConfigurationFileMap();
fileMap.ExeConfigFilename = "Test.config";
Configuration newConfiguration = ConfigurationManager.OpenMappedExeConfiguration(fileMap, ConfigurationUserLevel.None);

ConfigurationChannelFactory<ICalculatorChannel> factory1 = new ConfigurationChannelFactory<ICalculatorChannel>("endpoint1", newConfiguration, new EndpointAddress("http://localhost:8000/servicemodelsamples/service"));
ICalculatorChannel client1 = factory1.CreateChannel();
```

#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="421c2-114">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="421c2-114">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="421c2-115">Otevřete Visual Studio 2012 s oprávněními správce.</span><span class="sxs-lookup"><span data-stu-id="421c2-115">Open Visual Studio 2012 with administrator privileges.</span></span>

2. <span data-ttu-id="421c2-116">Klikněte pravým tlačítkem na řešení ConfigurationChannelFactory (2 projekty) a pak vyberte **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="421c2-116">Right-click the ConfigurationChannelFactory solution (2 projects) and then select **Properties**.</span></span>

3. <span data-ttu-id="421c2-117">V nabídce **běžné vlastnosti**vyberte možnost **projekt po spuštění**a pak klikněte na **více projektů po spuštění**.</span><span class="sxs-lookup"><span data-stu-id="421c2-117">In **Common Properties**, select **Startup Project**, and then click **Multiple startup projects**.</span></span>

4. <span data-ttu-id="421c2-118">Přesuňte projekt **služby** na začátek seznamu a **akci ' spustit '** a poté přesuňte **klientský** projekt po projektu **služby** , a to i v **akci ' Start '** , takže se spustí projekt **klienta** . po projektu **služby** .</span><span class="sxs-lookup"><span data-stu-id="421c2-118">Move the **Service** project to the beginning of the list, with the **Action ‘Start’**, and then move the **Client** project after the **Service** project, also with the **Action ‘Start’**, so the **Client** project is executed after the **Service** project.</span></span>

5. <span data-ttu-id="421c2-119">Klikněte na **OK**a potom stisknutím klávesy F5 (nebo CTRL + F5) spusťte ukázku.</span><span class="sxs-lookup"><span data-stu-id="421c2-119">Click **OK**, and then press F5 (or CTRL+F5) to run the sample.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="421c2-120">Ukázky už můžou být na vašem počítači nainstalované.</span><span class="sxs-lookup"><span data-stu-id="421c2-120">The samples may already be installed on your machine.</span></span> <span data-ttu-id="421c2-121">Než budete pokračovat, vyhledejte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="421c2-121">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="421c2-122">Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek.</span><span class="sxs-lookup"><span data-stu-id="421c2-122">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="421c2-123">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="421c2-123">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\ConfigurationChannelFactory`
