---
title: "Provádění vlastnosti"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 31c009db-397c-4653-87e2-32dc77fa4b13
caps.latest.revision: "14"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: ab7c81f051e6e65509d232479fd9f4ebe00ac99d
ms.sourcegitcommit: 5177d6ae2e9baf026f07ee0631556700a5a193f7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/28/2017
---
# <a name="execution-properties"></a><span data-ttu-id="d0a3e-102">Provádění vlastnosti</span><span class="sxs-lookup"><span data-stu-id="d0a3e-102">Execution Properties</span></span>
<span data-ttu-id="d0a3e-103">Tento příklad ukazuje, jak definovat a provádění vlastnost použijte vlastní aktivity.</span><span class="sxs-lookup"><span data-stu-id="d0a3e-103">This sample shows how to define and use an execution property in a custom activity.</span></span> <span data-ttu-id="d0a3e-104">V tomto příkladu vlastnost provádění Určuje barvu popředí v konzole.</span><span class="sxs-lookup"><span data-stu-id="d0a3e-104">In this example, the execution property determines the console's foreground color.</span></span> <span data-ttu-id="d0a3e-105">Pracovním postupu příklad ukazuje, jak různé logické cesty provádění (větví nástroje <xref:System.Activities.Statements.Parallel> aktivity) můžete udržovat různé konzoly barvy navzdory prokládaná provádění aktivity (napříč větví sady <xref:System.Activities.Statements.Parallel> aktivity).</span><span class="sxs-lookup"><span data-stu-id="d0a3e-105">An example workflow shows how different logical paths of execution (branches of a <xref:System.Activities.Statements.Parallel> activity) can maintain different console colors despite interleaved execution of activities (across the branches of the <xref:System.Activities.Statements.Parallel> activity).</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="d0a3e-106">Pokud chcete nastavit, sestavit a spustit ukázku</span><span class="sxs-lookup"><span data-stu-id="d0a3e-106">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="d0a3e-107">Otevřete ExecutionProperties.sln ukázkové řešení v [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d0a3e-107">Open the ExecutionProperties.sln sample solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d0a3e-108">Zobrazení ThreeColors.xaml před vytvořením řešení zobrazí chybu, protože používá vlastní aktivity musí být vytvořená ve stejnou dobu jako řešení.</span><span class="sxs-lookup"><span data-stu-id="d0a3e-108">Viewing ThreeColors.xaml before building the solution displays an error, because the custom activities used must be built at the same time as the solution.</span></span>  
  
2.  <span data-ttu-id="d0a3e-109">Sestavení a spuštění řešení.</span><span class="sxs-lookup"><span data-stu-id="d0a3e-109">Build and run the solution.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="d0a3e-110">Ukázky může být již nainstalována na váš počítač.</span><span class="sxs-lookup"><span data-stu-id="d0a3e-110">The samples may already be installed on your machine.</span></span> <span data-ttu-id="d0a3e-111">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="d0a3e-111">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="d0a3e-112">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="d0a3e-112">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="d0a3e-113">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="d0a3e-113">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\Code-Bodied\ExecutionProperties`