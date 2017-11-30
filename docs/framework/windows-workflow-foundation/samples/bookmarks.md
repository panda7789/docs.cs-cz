---
title: Bookmarks2
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 035fadb2-49fa-4ac7-b398-daf138f66e87
caps.latest.revision: "11"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: d3a1e0a966fcd5d89cc30456b46a11ae7d54731e
ms.sourcegitcommit: 5177d6ae2e9baf026f07ee0631556700a5a193f7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/28/2017
---
# <a name="bookmarks"></a><span data-ttu-id="b8041-102">Záložky</span><span class="sxs-lookup"><span data-stu-id="b8041-102">Bookmarks</span></span>
<span data-ttu-id="b8041-103">Tento příklad znázorňuje, jak psát vlastní aktivity, která vytvoří záložku, která bude přijímat externí vstup.</span><span class="sxs-lookup"><span data-stu-id="b8041-103">This sample demonstrates how to write a custom activity that creates a bookmark to receive external input.</span></span> <span data-ttu-id="b8041-104">Ukázka zahrnuje také základní konzolovou aplikaci, která používá vlastní aktivity v pracovním postupu a ukazuje, jak zjišťovat a obnovit záložky přidružené spuštěné instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="b8041-104">The sample also includes a basic console application that uses the custom activity in a workflow and shows how to discover and resume bookmarks associated with a running workflow instance.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="b8041-105">záložky, najdete v části [záložky](../../../../docs/framework/windows-workflow-foundation/bookmarks.md).</span><span class="sxs-lookup"><span data-stu-id="b8041-105"> bookmarks, see [Bookmarks](../../../../docs/framework/windows-workflow-foundation/bookmarks.md).</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="b8041-106">Pokud chcete nastavit, sestavit a spustit ukázku</span><span class="sxs-lookup"><span data-stu-id="b8041-106">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="b8041-107">Otevřete Bookmarks.sln ukázkové řešení v [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b8041-107">Open the Bookmarks.sln sample solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="b8041-108">Sestavte řešení, stiskněte CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="b8041-108">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="b8041-109">Chcete-li spustit ukázku, stiskněte CTRLl + F5.</span><span class="sxs-lookup"><span data-stu-id="b8041-109">To run the sample, press CTRLl + F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="b8041-110">Ukázky může být již nainstalována na váš počítač.</span><span class="sxs-lookup"><span data-stu-id="b8041-110">The samples may already be installed on your machine.</span></span> <span data-ttu-id="b8041-111">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="b8041-111">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="b8041-112">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="b8041-112">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="b8041-113">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="b8041-113">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\CodeBodied\Bookmarks`