---
title: Ukázka kompenzovatelná aktivita
ms.date: 03/30/2017
ms.assetid: 58f4898c-b2b8-44a4-9a73-3bef4da6d5ba
ms.openlocfilehash: 3bf1d120cd700830a98f53495f7e9989ffec73db
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/13/2018
ms.locfileid: "45557649"
---
# <a name="compensable-activity-sample"></a><span data-ttu-id="b8337-102">Ukázka kompenzovatelná aktivita</span><span class="sxs-lookup"><span data-stu-id="b8337-102">Compensable Activity Sample</span></span>
<span data-ttu-id="b8337-103">Tato ukázka předvádí, jak používat `CompensableActivity` aktivity k definování práce, která musí být provedeno pro danou akci během normálního provádění a práci, kterou je potřeba udělat, aby se nahradit tuto akci v případě potřeby později.</span><span class="sxs-lookup"><span data-stu-id="b8337-103">This sample demonstrates how to use the `CompensableActivity` activity to define the work to be done for a given action during normal execution and the work that is necessary to be done to compensate that action, if necessary at a later time.</span></span>  <span data-ttu-id="b8337-104">První část vzorek ukazuje, jak kompenzovatelná pracovní jednotky je možné definovat ve Windows Workflow Foundation (WF) pomocí `CompensableActivity` aktivity a jak jsou provedeny v úspěšného spuštění.</span><span class="sxs-lookup"><span data-stu-id="b8337-104">The first part of the sample shows how units of compensable work can be defined in Windows Workflow Foundation (WF) using a `CompensableActivity` activity and how they are executed in a successful run.</span></span>  <span data-ttu-id="b8337-105">Druhá část vzorek ukazuje, jak stejné jednotky kompenzovatelná pracovní automaticky postará o kompenzaci při dosažení neočekávané události a zrušení instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="b8337-105">The second part of the sample shows how the same units of compensable work automatically take care of compensation when an unexpected event is hit and the workflow instance is canceled.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="b8337-106">Chcete-li nastavit, sestavte a spusťte ukázku</span><span class="sxs-lookup"><span data-stu-id="b8337-106">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="b8337-107">Pomocí sady Visual Studio 2010, otevřete CompensableActivity.sln.</span><span class="sxs-lookup"><span data-stu-id="b8337-107">Using Visual Studio 2010, open the CompensableActivity.sln.</span></span>  
  
2.  <span data-ttu-id="b8337-108">Sestavte řešení stisknutím kombinace kláves CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="b8337-108">Build the solution by pressing CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="b8337-109">Stisknutím klávesy F5 spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="b8337-109">Run the application by pressing F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="b8337-110">Vzorky mohou již být nainstalováno na svém počítači.</span><span class="sxs-lookup"><span data-stu-id="b8337-110">The samples may already be installed on your machine.</span></span> <span data-ttu-id="b8337-111">Před pokračováním zkontrolujte následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="b8337-111">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="b8337-112">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="b8337-112">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="b8337-113">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="b8337-113">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Compensation\BasicCompensableActivity`