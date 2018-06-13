---
title: Získávání Začínáme vytváření vlastních aktivit
ms.date: 03/30/2017
ms.assetid: 3902f5fa-8a43-4048-8a6a-6b15472f90f0
ms.openlocfilehash: 1c455009a0c658429c13da5e93d07c744402dd61
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33513308"
---
# <a name="getting-started-writing-a-custom-activity"></a><span data-ttu-id="a30a1-102">Získávání Začínáme vytváření vlastních aktivit</span><span class="sxs-lookup"><span data-stu-id="a30a1-102">Getting Started Writing a Custom Activity</span></span>
<span data-ttu-id="a30a1-103">Tento příklad znázorňuje, jak definovat jednoduchý vlastní aktivity v jazyce XAML.</span><span class="sxs-lookup"><span data-stu-id="a30a1-103">This sample demonstrates how to define a simple custom activity in XAML.</span></span> <span data-ttu-id="a30a1-104">Aktivita je zadaný název `Rhyme`, a je svou logikou pořadí tří <xref:System.Activities.Statements.WriteLine> aktivity.</span><span class="sxs-lookup"><span data-stu-id="a30a1-104">The activity is given the name `Rhyme`, and its logic is a sequence of three <xref:System.Activities.Statements.WriteLine> activities.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="a30a1-105">Pokud chcete nastavit, sestavit a spustit ukázku</span><span class="sxs-lookup"><span data-stu-id="a30a1-105">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="a30a1-106">Otevřete **Simple.sln** ukázkové řešení v [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a30a1-106">Open the **Simple.sln** sample solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="a30a1-107">Sestavení a spuštění řešení.</span><span class="sxs-lookup"><span data-stu-id="a30a1-107">Build and run the solution.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="a30a1-108">Ukázky může být již nainstalována na váš počítač.</span><span class="sxs-lookup"><span data-stu-id="a30a1-108">The samples may already be installed on your machine.</span></span> <span data-ttu-id="a30a1-109">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="a30a1-109">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="a30a1-110">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="a30a1-110">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="a30a1-111">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="a30a1-111">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\Composite\GettingStarted`