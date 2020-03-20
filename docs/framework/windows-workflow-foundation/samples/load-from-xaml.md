---
title: Načtení z XAML
ms.date: 03/30/2017
ms.assetid: 1f103ef6-7bed-4f16-ae52-9e665c5a43d7
ms.openlocfilehash: d07ddef8fb982aa0bf707cb688cd23f04bb231d5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79142716"
---
# <a name="load-from-xaml"></a><span data-ttu-id="fb364-102">Načtení z XAML</span><span class="sxs-lookup"><span data-stu-id="fb364-102">Load From XAML</span></span>
<span data-ttu-id="fb364-103">Tato ukázka ukazuje, jak dynamicky načíst pracovní postup XAML bez nutnosti spouštět nástroj XamlBuildTask.</span><span class="sxs-lookup"><span data-stu-id="fb364-103">This sample demonstrates how to dynamically load a XAML workflow without having to run the XamlBuildTask tool.</span></span> <span data-ttu-id="fb364-104">Místo toho ukázka <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A> volá metodu.</span><span class="sxs-lookup"><span data-stu-id="fb364-104">Instead, the sample calls the <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A> method.</span></span> <span data-ttu-id="fb364-105">Ukázka je klientská aplikace WPF (Windows Presentation Foundation), která <xref:System.Activities.XamlIntegration.ActivityXamlServices> načte pracovní postupy XAML pomocí třídy a provede je.</span><span class="sxs-lookup"><span data-stu-id="fb364-105">The sample is a Windows Presentation Foundation (WPF) client application that loads XAML workflows using the <xref:System.Activities.XamlIntegration.ActivityXamlServices> class and executes them.</span></span> <span data-ttu-id="fb364-106">Poté, co byly <xref:System.Activities.XamlIntegration.ActivityXamlServices> načteny <xref:System.Activities.DynamicActivity%601> pomocí třídy, je vrácena, která může být provedena.</span><span class="sxs-lookup"><span data-stu-id="fb364-106">After they have been loaded using the <xref:System.Activities.XamlIntegration.ActivityXamlServices> class, a <xref:System.Activities.DynamicActivity%601> is returned that can be executed.</span></span>

#### <a name="to-use-this-sample"></a><span data-ttu-id="fb364-107">Chcete-li použít tento vzorek</span><span class="sxs-lookup"><span data-stu-id="fb364-107">To use this sample</span></span>

1. <span data-ttu-id="fb364-108">Pomocí sady Visual Studio 2010 otevřete soubor řešení LoadFromXAML.sln.</span><span class="sxs-lookup"><span data-stu-id="fb364-108">Using Visual Studio 2010, open the LoadFromXAML.sln solution file.</span></span>

2. <span data-ttu-id="fb364-109">Chcete-li vytvořit řešení, stiskněte kombinaci kláves CTRL+SHIFT+B.</span><span class="sxs-lookup"><span data-stu-id="fb364-109">To build the solution, press CTRL+SHIFT+B.</span></span>

3. <span data-ttu-id="fb364-110">Chcete-li řešení spustit, stiskněte kombinaci kláves CTRL+F5.</span><span class="sxs-lookup"><span data-stu-id="fb364-110">To run the solution, press CTRL+F5.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="fb364-111">Ukázky mohou být již nainstalovány v počítači.</span><span class="sxs-lookup"><span data-stu-id="fb364-111">The samples may already be installed on your machine.</span></span> <span data-ttu-id="fb364-112">Před pokračováním zkontrolujte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="fb364-112">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="fb364-113">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="fb364-113">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="fb364-114">Tato ukázka je umístěna v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="fb364-114">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\DynamicActivity\LoadFromXAML`
