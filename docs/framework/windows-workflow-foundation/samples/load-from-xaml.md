---
title: Načtení z XAML
ms.date: 03/30/2017
ms.assetid: 1f103ef6-7bed-4f16-ae52-9e665c5a43d7
ms.openlocfilehash: 2f45beb398e6d6b91bf7444dd590b862ff8c7515
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2019
ms.locfileid: "70038088"
---
# <a name="load-from-xaml"></a><span data-ttu-id="b4507-102">Načtení z XAML</span><span class="sxs-lookup"><span data-stu-id="b4507-102">Load From XAML</span></span>
<span data-ttu-id="b4507-103">Tato ukázka předvádí, jak dynamicky načíst pracovní postup XAML bez nutnosti spuštění nástroje XamlBuildTask.</span><span class="sxs-lookup"><span data-stu-id="b4507-103">This sample demonstrates how to dynamically load a XAML workflow without having to run the XamlBuildTask tool.</span></span> <span data-ttu-id="b4507-104">Místo toho ukázka volá <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A> metodu.</span><span class="sxs-lookup"><span data-stu-id="b4507-104">Instead, the sample calls the <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A> method.</span></span> <span data-ttu-id="b4507-105">Ukázka je klientská aplikace Windows Presentation Foundation (WPF), která načte pracovní postupy XAML pomocí <xref:System.Activities.XamlIntegration.ActivityXamlServices> třídy a provede je.</span><span class="sxs-lookup"><span data-stu-id="b4507-105">The sample is a Windows Presentation Foundation (WPF) client application that loads XAML workflows using the <xref:System.Activities.XamlIntegration.ActivityXamlServices> class and executes them.</span></span> <span data-ttu-id="b4507-106">Poté, co byly načteny pomocí <xref:System.Activities.XamlIntegration.ActivityXamlServices> třídy <xref:System.Activities.DynamicActivity%601> , je vráceno, které lze provést.</span><span class="sxs-lookup"><span data-stu-id="b4507-106">After they have been loaded using the <xref:System.Activities.XamlIntegration.ActivityXamlServices> class, a <xref:System.Activities.DynamicActivity%601> is returned that can be executed.</span></span>

#### <a name="to-use-this-sample"></a><span data-ttu-id="b4507-107">Použití této ukázky</span><span class="sxs-lookup"><span data-stu-id="b4507-107">To use this sample</span></span>

1. <span data-ttu-id="b4507-108">Pomocí sady Visual Studio 2010 otevřete soubor řešení LoadFromXAML. sln.</span><span class="sxs-lookup"><span data-stu-id="b4507-108">Using Visual Studio 2010, open the LoadFromXAML.sln solution file.</span></span>

2. <span data-ttu-id="b4507-109">Pro sestavení řešení stiskněte kombinaci kláves CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="b4507-109">To build the solution, press CTRL+SHIFT+B.</span></span>

3. <span data-ttu-id="b4507-110">Pokud chcete řešení spustit, stiskněte klávesy CTRL + F5.</span><span class="sxs-lookup"><span data-stu-id="b4507-110">To run the solution, press CTRL+F5.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b4507-111">Ukázky už můžou být na vašem počítači nainstalované.</span><span class="sxs-lookup"><span data-stu-id="b4507-111">The samples may already be installed on your machine.</span></span> <span data-ttu-id="b4507-112">Než budete pokračovat, vyhledejte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="b4507-112">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="b4507-113">Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek.</span><span class="sxs-lookup"><span data-stu-id="b4507-113">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="b4507-114">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="b4507-114">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\DynamicActivity\LoadFromXAML`
