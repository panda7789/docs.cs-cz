---
title: Postup konfiguračního kanálu
ms.date: 03/30/2017
ms.assetid: 3b749493-bd8a-4ccb-893e-5948901a1486
ms.openlocfilehash: 0f00ba5e217420fe416100071d380e413c3df118
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183952"
---
# <a name="configuration-channel-factory"></a><span data-ttu-id="c45b4-102">Postup konfiguračního kanálu</span><span class="sxs-lookup"><span data-stu-id="c45b4-102">Configuration Channel Factory</span></span>
<span data-ttu-id="c45b4-103">Tento vzorek zahrnuje použití <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601>.</span><span class="sxs-lookup"><span data-stu-id="c45b4-103">This sample covers the usage of the <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601>.</span></span> <span data-ttu-id="c45b4-104">Umožňuje <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> centrální správu konfigurace klienta WCF.</span><span class="sxs-lookup"><span data-stu-id="c45b4-104">The <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> allows central management of WCF client configuration.</span></span> <span data-ttu-id="c45b4-105">To může být také užitečné ve scénářích, ve kterých je konfigurace vybrána nebo změněna po čase načítání domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="c45b4-105">This can also be useful in scenarios in which configuration is selected or changed after the application domain load time.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="c45b4-106">Demonstruje</span><span class="sxs-lookup"><span data-stu-id="c45b4-106">Demonstrates</span></span>
 <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601>

## <a name="discussion"></a><span data-ttu-id="c45b4-107">Diskuse</span><span class="sxs-lookup"><span data-stu-id="c45b4-107">Discussion</span></span>
 <span data-ttu-id="c45b4-108">Tato ukázka ukazuje, jak přidat <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> konkrétní konfigurační soubor do klientské aplikace, aniž byste museli používat výchozí konfigurační soubor aplikace.</span><span class="sxs-lookup"><span data-stu-id="c45b4-108">This sample shows how to use <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> to add a particular configuration file to a client application, without having to use the default application configuration file.</span></span>

 <span data-ttu-id="c45b4-109">Vzorek se skládá ze dvou projektů.</span><span class="sxs-lookup"><span data-stu-id="c45b4-109">The sample consists of two projects.</span></span> <span data-ttu-id="c45b4-110">První projekt je jednoduchá služba, která běží odpovědět na zprávy přicházející od klientů.</span><span class="sxs-lookup"><span data-stu-id="c45b4-110">The first project is a simple service that runs to reply to messages coming from the clients.</span></span> <span data-ttu-id="c45b4-111">Druhý projekt je klientská aplikace, <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> která <xref:System.Configuration.ExeConfigurationFileMap> vytvoří dva objekty pomocí konfiguračního souboru Test.config a používá je ke komunikaci se službou.</span><span class="sxs-lookup"><span data-stu-id="c45b4-111">The second project is a client application that builds two <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> objects using a <xref:System.Configuration.ExeConfigurationFileMap> for the Test.config configuration file and uses them to communicate with the service.</span></span> <span data-ttu-id="c45b4-112">Oba klienti komunikují se službou pomocí konfigurace zadané v souboru Test.config.</span><span class="sxs-lookup"><span data-stu-id="c45b4-112">Both clients communicate with the service using the configuration specified in Test.config.</span></span>

 <span data-ttu-id="c45b4-113">Následující kód přidá do klientské aplikace vlastní konfigurační soubor.</span><span class="sxs-lookup"><span data-stu-id="c45b4-113">The following code adds a custom configuration file to a client application.</span></span>

```csharp
ExeConfigurationFileMap fileMap = new ExeConfigurationFileMap();
fileMap.ExeConfigFilename = "Test.config";
Configuration newConfiguration = ConfigurationManager.OpenMappedExeConfiguration(fileMap, ConfigurationUserLevel.None);

ConfigurationChannelFactory<ICalculatorChannel> factory1 = new ConfigurationChannelFactory<ICalculatorChannel>("endpoint1", newConfiguration, new EndpointAddress("http://localhost:8000/servicemodelsamples/service"));
ICalculatorChannel client1 = factory1.CreateChannel();
```

#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="c45b4-114">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="c45b4-114">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="c45b4-115">Otevřete Visual Studio 2012 s oprávněními správce.</span><span class="sxs-lookup"><span data-stu-id="c45b4-115">Open Visual Studio 2012 with administrator privileges.</span></span>

2. <span data-ttu-id="c45b4-116">Klepněte pravým tlačítkem myši na řešení ConfigurationChannelFactory (2 projekty) a potom vyberte **příkaz Vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="c45b4-116">Right-click the ConfigurationChannelFactory solution (2 projects) and then select **Properties**.</span></span>

3. <span data-ttu-id="c45b4-117">V **pole Společné vlastnosti**vyberte **možnost Projekt po spuštění**a klepněte na tlačítko Více projektů **po spuštění**.</span><span class="sxs-lookup"><span data-stu-id="c45b4-117">In **Common Properties**, select **Startup Project**, and then click **Multiple startup projects**.</span></span>

4. <span data-ttu-id="c45b4-118">Přesuňte projekt **služby** na začátek seznamu s **akcí "Start"** a potom přesuňte projekt **klienta** po projektu **služby,** také s **akcí "Start"**, takže projekt **klienta** je proveden po projektu **služby.**</span><span class="sxs-lookup"><span data-stu-id="c45b4-118">Move the **Service** project to the beginning of the list, with the **Action ‘Start’**, and then move the **Client** project after the **Service** project, also with the **Action ‘Start’**, so the **Client** project is executed after the **Service** project.</span></span>

5. <span data-ttu-id="c45b4-119">Klepněte na **tlačítko OK**a potom spusťte ukázku stisknutím klávesy F5 (nebo CTRL+F5).</span><span class="sxs-lookup"><span data-stu-id="c45b4-119">Click **OK**, and then press F5 (or CTRL+F5) to run the sample.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c45b4-120">Ukázky mohou být již nainstalovány v počítači.</span><span class="sxs-lookup"><span data-stu-id="c45b4-120">The samples may already be installed on your machine.</span></span> <span data-ttu-id="c45b4-121">Před pokračováním zkontrolujte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="c45b4-121">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="c45b4-122">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="c45b4-122">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="c45b4-123">Tato ukázka je umístěna v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="c45b4-123">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\ConfigurationChannelFactory`
