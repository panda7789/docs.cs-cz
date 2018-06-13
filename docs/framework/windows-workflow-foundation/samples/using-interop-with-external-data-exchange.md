---
title: Pomocí zprostředkovatele komunikace se serverem Exchange externích dat
ms.date: 03/30/2017
ms.assetid: 96f6fe26-5305-494f-9119-7748e0c4b3fa
ms.openlocfilehash: 9571a571137ff0a493be67ee9c607cd46dd47889
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33515369"
---
# <a name="using-interop-with-external-data-exchange"></a><span data-ttu-id="6fb78-102">Pomocí zprostředkovatele komunikace se serverem Exchange externích dat</span><span class="sxs-lookup"><span data-stu-id="6fb78-102">Using Interop with External Data Exchange</span></span>
<span data-ttu-id="6fb78-103"><xref:System.Activities.Statements.Interop> Aktivity můžete použít ke spuštění aktivity z Windows Workflow Foundation (WF) v [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)] a [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] (WF3) a pracovních postupů v rámci modelu Windows Workflow Foundation v [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] (WF4).</span><span class="sxs-lookup"><span data-stu-id="6fb78-103">The <xref:System.Activities.Statements.Interop> activity can be used to execute activities from Windows Workflow Foundation (WF) in [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)] and [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] (WF3), and workflows within Windows Workflow Foundation in [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] (WF4).</span></span> <span data-ttu-id="6fb78-104">Tento příklad ukazuje, jak nakonfigurovat a spustit WF3 pracovní postup, který používá <xref:System.Workflow.Activities.ExternalDataExchangeService> (a odpovídající vlastní aktivity pro volání metod a zpracování událostí) pomocí <xref:System.Activities.Statements.Interop> aktivity v WF4 služby pracovních postupů.</span><span class="sxs-lookup"><span data-stu-id="6fb78-104">This sample shows how to configure and run a WF3 workflow that uses <xref:System.Workflow.Activities.ExternalDataExchangeService> (and corresponding custom activities for calling methods and handling events) by using the <xref:System.Activities.Statements.Interop> activity in a WF4 workflow service.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="6fb78-105">Ukázky může být již nainstalována na váš počítač.</span><span class="sxs-lookup"><span data-stu-id="6fb78-105">The samples may already be installed on your machine.</span></span> <span data-ttu-id="6fb78-106">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="6fb78-106">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="6fb78-107">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="6fb78-107">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="6fb78-108">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="6fb78-108">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Migration\ExternalDataExchange`  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="6fb78-109">Pro fungování této ukázky</span><span class="sxs-lookup"><span data-stu-id="6fb78-109">To use this sample</span></span>  
  
1.  <span data-ttu-id="6fb78-110">Otevřete soubor ExternalDataExchange.sln v [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="6fb78-110">Open the ExternalDataExchange.sln file in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="6fb78-111">Chcete-li sestavit ukázku, stiskněte CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="6fb78-111">To build the sample, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="6fb78-112">Pokud chcete spustit ukázku, stisknutím klávesy F5.</span><span class="sxs-lookup"><span data-stu-id="6fb78-112">To run the sample, press F5.</span></span>
