---
title: Načtení z XAML
ms.date: 03/30/2017
ms.assetid: 1f103ef6-7bed-4f16-ae52-9e665c5a43d7
ms.openlocfilehash: 783e26b05d23baa7842c4414c92d4e78262dd9ec
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/04/2018
ms.locfileid: "48580677"
---
# <a name="load-from-xaml"></a><span data-ttu-id="86380-102">Načtení z XAML</span><span class="sxs-lookup"><span data-stu-id="86380-102">Load From XAML</span></span>
<span data-ttu-id="86380-103">Tato ukázka předvádí, jak dynamicky načíst pracovní postup XAML bez nutnosti spuštění XamlBuildTask nástroj.</span><span class="sxs-lookup"><span data-stu-id="86380-103">This sample demonstrates how to dynamically load a XAML workflow without having to run the XamlBuildTask tool.</span></span> <span data-ttu-id="86380-104">Místo toho, ukázka zavolá <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="86380-104">Instead, the sample calls the <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A> method.</span></span> <span data-ttu-id="86380-105">Ukázka je klientská aplikace Windows Presentation Foundation (WPF), která načte pracovní postupy XAML pomocí <xref:System.Activities.XamlIntegration.ActivityXamlServices> třídy a spustí je.</span><span class="sxs-lookup"><span data-stu-id="86380-105">The sample is a Windows Presentation Foundation (WPF) client application that loads XAML workflows using the <xref:System.Activities.XamlIntegration.ActivityXamlServices> class and executes them.</span></span> <span data-ttu-id="86380-106">Po jejich byly načteny pomocí <xref:System.Activities.XamlIntegration.ActivityXamlServices> třídy, <xref:System.Activities.DynamicActivity%601> je vrácena, které mohou být provedeny.</span><span class="sxs-lookup"><span data-stu-id="86380-106">After they have been loaded using the <xref:System.Activities.XamlIntegration.ActivityXamlServices> class, a <xref:System.Activities.DynamicActivity%601> is returned that can be executed.</span></span>

#### <a name="to-use-this-sample"></a><span data-ttu-id="86380-107">Pro fungování této ukázky</span><span class="sxs-lookup"><span data-stu-id="86380-107">To use this sample</span></span>

1.  <span data-ttu-id="86380-108">Pomocí sady Visual Studio 2010, otevřete soubor řešení LoadFromXAML.sln.</span><span class="sxs-lookup"><span data-stu-id="86380-108">Using Visual Studio 2010, open the LoadFromXAML.sln solution file.</span></span>

2.  <span data-ttu-id="86380-109">Abyste mohli sestavit řešení, stiskněte kombinaci kláves CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="86380-109">To build the solution, press CTRL+SHIFT+B.</span></span>

3.  <span data-ttu-id="86380-110">Abyste mohli spustit řešení, stiskněte CTRL + F5.</span><span class="sxs-lookup"><span data-stu-id="86380-110">To run the solution, press CTRL+F5.</span></span>

> [!IMPORTANT]
>  <span data-ttu-id="86380-111">Vzorky mohou již být nainstalováno na svém počítači.</span><span class="sxs-lookup"><span data-stu-id="86380-111">The samples may already be installed on your machine.</span></span> <span data-ttu-id="86380-112">Před pokračováním zkontrolujte následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="86380-112">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="86380-113">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="86380-113">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="86380-114">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="86380-114">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\DynamicActivity\LoadFromXAML`