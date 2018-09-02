---
title: Začínáme s vytvářením vlastní aktivity
ms.date: 03/30/2017
ms.assetid: 3902f5fa-8a43-4048-8a6a-6b15472f90f0
ms.openlocfilehash: 4d9c140ca230750ca1119b33252b1edb8796d458
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43405225"
---
# <a name="getting-started-writing-a-custom-activity"></a><span data-ttu-id="e958b-102">Začínáme s vytvářením vlastní aktivity</span><span class="sxs-lookup"><span data-stu-id="e958b-102">Getting Started Writing a Custom Activity</span></span>
<span data-ttu-id="e958b-103">Tento příklad ukazuje, jak definovat jednoduchý vlastní aktivity v XAML.</span><span class="sxs-lookup"><span data-stu-id="e958b-103">This sample demonstrates how to define a simple custom activity in XAML.</span></span> <span data-ttu-id="e958b-104">Aktivita je označen názvem `Rhyme`, a je svou logikou posloupnost tří <xref:System.Activities.Statements.WriteLine> aktivity.</span><span class="sxs-lookup"><span data-stu-id="e958b-104">The activity is given the name `Rhyme`, and its logic is a sequence of three <xref:System.Activities.Statements.WriteLine> activities.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="e958b-105">Chcete-li nastavit, sestavte a spusťte ukázku</span><span class="sxs-lookup"><span data-stu-id="e958b-105">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="e958b-106">Otevřít **Simple.sln** ukázkové řešení v [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e958b-106">Open the **Simple.sln** sample solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="e958b-107">Sestavte a spusťte řešení.</span><span class="sxs-lookup"><span data-stu-id="e958b-107">Build and run the solution.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="e958b-108">Vzorky mohou již být nainstalováno na svém počítači.</span><span class="sxs-lookup"><span data-stu-id="e958b-108">The samples may already be installed on your machine.</span></span> <span data-ttu-id="e958b-109">Před pokračováním zkontrolujte následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="e958b-109">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="e958b-110">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="e958b-110">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="e958b-111">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="e958b-111">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\Composite\GettingStarted`