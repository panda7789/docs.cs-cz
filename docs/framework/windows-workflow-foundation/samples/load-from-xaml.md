---
title: Načtení z XAML
ms.date: 03/30/2017
ms.assetid: 1f103ef6-7bed-4f16-ae52-9e665c5a43d7
ms.openlocfilehash: c46c9020f07731d3d833332d77fd46a162ccb6dc
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74715952"
---
# <a name="load-from-xaml"></a><span data-ttu-id="8b3c8-102">Načtení z XAML</span><span class="sxs-lookup"><span data-stu-id="8b3c8-102">Load From XAML</span></span>
<span data-ttu-id="8b3c8-103">Tato ukázka předvádí, jak dynamicky načíst pracovní postup XAML bez nutnosti spuštění nástroje XamlBuildTask.</span><span class="sxs-lookup"><span data-stu-id="8b3c8-103">This sample demonstrates how to dynamically load a XAML workflow without having to run the XamlBuildTask tool.</span></span> <span data-ttu-id="8b3c8-104">Místo toho ukázka volá metodu <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A>.</span><span class="sxs-lookup"><span data-stu-id="8b3c8-104">Instead, the sample calls the <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A> method.</span></span> <span data-ttu-id="8b3c8-105">Ukázka je klientská aplikace Windows Presentation Foundation (WPF), která načte pracovní postupy XAML pomocí třídy <xref:System.Activities.XamlIntegration.ActivityXamlServices> a provede je.</span><span class="sxs-lookup"><span data-stu-id="8b3c8-105">The sample is a Windows Presentation Foundation (WPF) client application that loads XAML workflows using the <xref:System.Activities.XamlIntegration.ActivityXamlServices> class and executes them.</span></span> <span data-ttu-id="8b3c8-106">Po načtení pomocí <xref:System.Activities.XamlIntegration.ActivityXamlServices> třídy se vrátí <xref:System.Activities.DynamicActivity%601>, který lze spustit.</span><span class="sxs-lookup"><span data-stu-id="8b3c8-106">After they have been loaded using the <xref:System.Activities.XamlIntegration.ActivityXamlServices> class, a <xref:System.Activities.DynamicActivity%601> is returned that can be executed.</span></span>

#### <a name="to-use-this-sample"></a><span data-ttu-id="8b3c8-107">Použití této ukázky</span><span class="sxs-lookup"><span data-stu-id="8b3c8-107">To use this sample</span></span>

1. <span data-ttu-id="8b3c8-108">Pomocí sady Visual Studio 2010 otevřete soubor řešení LoadFromXAML. sln.</span><span class="sxs-lookup"><span data-stu-id="8b3c8-108">Using Visual Studio 2010, open the LoadFromXAML.sln solution file.</span></span>

2. <span data-ttu-id="8b3c8-109">Pro sestavení řešení stiskněte kombinaci kláves CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="8b3c8-109">To build the solution, press CTRL+SHIFT+B.</span></span>

3. <span data-ttu-id="8b3c8-110">Pokud chcete řešení spustit, stiskněte klávesy CTRL + F5.</span><span class="sxs-lookup"><span data-stu-id="8b3c8-110">To run the solution, press CTRL+F5.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8b3c8-111">Ukázky už můžou být na vašem počítači nainstalované.</span><span class="sxs-lookup"><span data-stu-id="8b3c8-111">The samples may already be installed on your machine.</span></span> <span data-ttu-id="8b3c8-112">Než budete pokračovat, vyhledejte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="8b3c8-112">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="8b3c8-113">Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Samples.</span><span class="sxs-lookup"><span data-stu-id="8b3c8-113">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="8b3c8-114">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="8b3c8-114">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\DynamicActivity\LoadFromXAML`
