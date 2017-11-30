---
title: "Získávání Začínáme vytváření vlastních aktivit"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3902f5fa-8a43-4048-8a6a-6b15472f90f0
caps.latest.revision: "11"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 495cad6d672fd550024cc872bd3cff586326ccbc
ms.sourcegitcommit: 5177d6ae2e9baf026f07ee0631556700a5a193f7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/28/2017
---
# <a name="getting-started-writing-a-custom-activity"></a><span data-ttu-id="96f93-102">Získávání Začínáme vytváření vlastních aktivit</span><span class="sxs-lookup"><span data-stu-id="96f93-102">Getting Started Writing a Custom Activity</span></span>
<span data-ttu-id="96f93-103">Tento příklad znázorňuje, jak definovat jednoduchý vlastní aktivity v jazyce XAML.</span><span class="sxs-lookup"><span data-stu-id="96f93-103">This sample demonstrates how to define a simple custom activity in XAML.</span></span> <span data-ttu-id="96f93-104">Aktivita je zadaný název `Rhyme`, a je svou logikou pořadí tří <xref:System.Activities.Statements.WriteLine> aktivity.</span><span class="sxs-lookup"><span data-stu-id="96f93-104">The activity is given the name `Rhyme`, and its logic is a sequence of three <xref:System.Activities.Statements.WriteLine> activities.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="96f93-105">Pokud chcete nastavit, sestavit a spustit ukázku</span><span class="sxs-lookup"><span data-stu-id="96f93-105">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="96f93-106">Otevřete **Simple.sln** ukázkové řešení v [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="96f93-106">Open the **Simple.sln** sample solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="96f93-107">Sestavení a spuštění řešení.</span><span class="sxs-lookup"><span data-stu-id="96f93-107">Build and run the solution.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="96f93-108">Ukázky může být již nainstalována na váš počítač.</span><span class="sxs-lookup"><span data-stu-id="96f93-108">The samples may already be installed on your machine.</span></span> <span data-ttu-id="96f93-109">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="96f93-109">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="96f93-110">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="96f93-110">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="96f93-111">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="96f93-111">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\Composite\GettingStarted`