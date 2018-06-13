---
title: Pomocí rozhraní .NET Framework 3.0 nebo rozhraní .NET Framework 3.5 aktivity v pracovním postupu rozhraní .NET Framework 4.5
ms.date: 03/30/2017
ms.assetid: 6c53fd4c-5dd0-4fb4-ab6b-111302629548
ms.openlocfilehash: ab2e93918617bd1ca21fb32878d446db0dd2ef16
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33514896"
---
# <a name="using-a-net-framework-30-or-net-framework-35-activity-in-a-net-framework-45-workflow"></a><span data-ttu-id="798a7-102">Pomocí rozhraní .NET Framework 3.0 nebo rozhraní .NET Framework 3.5 aktivity v pracovním postupu rozhraní .NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="798a7-102">Using a .NET Framework 3.0 or .NET Framework 3.5 Activity in a .NET Framework 4.5 Workflow</span></span>
<span data-ttu-id="798a7-103"><xref:System.Activities.Statements.Interop> Aktivity umožňuje spouštění rozhraní .NET Framework 3.0 Windows Workflow Foundation (WF) aktivitu v rámci [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)] pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="798a7-103">The <xref:System.Activities.Statements.Interop> activity allows you to run a .NET Framework 3.0 Windows Workflow Foundation (WF) activity within a [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)] workflow.</span></span> <span data-ttu-id="798a7-104">Tento příklad znázorňuje způsob použití <xref:System.Activities.Statements.Interop> aktivity předat jako argument řetězec vlastní [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)] aktivity.</span><span class="sxs-lookup"><span data-stu-id="798a7-104">This sample demonstrates how to use the <xref:System.Activities.Statements.Interop> activity to pass a string as an argument to a custom [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)] activity.</span></span>  
  
## <a name="to-use-this-sample"></a><span data-ttu-id="798a7-105">Pro fungování této ukázky</span><span class="sxs-lookup"><span data-stu-id="798a7-105">To use this sample</span></span>  
  
1.  <span data-ttu-id="798a7-106">Pomocí [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], otevřete soubor řešení SimpleInterop.sln.</span><span class="sxs-lookup"><span data-stu-id="798a7-106">Using [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], open the SimpleInterop.sln solution file.</span></span>  
  
2.  <span data-ttu-id="798a7-107">Sestavte řešení, stiskněte CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="798a7-107">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="798a7-108">Chcete-li spustit řešení, stiskněte CTRL + F5.</span><span class="sxs-lookup"><span data-stu-id="798a7-108">To run the solution, press CTRL+F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="798a7-109">Ukázky může být již nainstalována na váš počítač.</span><span class="sxs-lookup"><span data-stu-id="798a7-109">The samples may already be installed on your machine.</span></span> <span data-ttu-id="798a7-110">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="798a7-110">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="798a7-111">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="798a7-111">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="798a7-112">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="798a7-112">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Migration\SimpleInterop`  
  
## <a name="see-also"></a><span data-ttu-id="798a7-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="798a7-113">See Also</span></span>
