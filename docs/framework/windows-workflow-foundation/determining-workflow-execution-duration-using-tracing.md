---
title: "Určení dobu trvání provádění pracovního postupu pomocí trasování"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f04ad0fd-edc7-4cbc-8979-356f2a1131c4
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f2687d045db28974e99b2f2b6a3222924a520720
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="determining-workflow-execution-duration-using-tracing"></a><span data-ttu-id="b1429-102">Určení dobu trvání provádění pracovního postupu pomocí trasování</span><span class="sxs-lookup"><span data-stu-id="b1429-102">Determining Workflow Execution Duration Using Tracing</span></span>
<span data-ttu-id="b1429-103">Toto téma ukazuje, jak určit čas potřebný pro úspěšně dokončila, vlastním hostováním pracovní postup provést pomocí trasování pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="b1429-103">This topic demonstrates how to determine the time it takes for a successfully completed, self-hosted workflow to execute by using workflow tracing.</span></span>  
  
### <a name="to-determine-workflow-application-execution-duration-by-using-workflow-tracing"></a><span data-ttu-id="b1429-104">Chcete-li zjistit dobu trvání provádění pracovního postupu aplikace pomocí trasování pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="b1429-104">To determine workflow application execution duration by using workflow tracing</span></span>  
  
1.  <span data-ttu-id="b1429-105">Otevřete [!INCLUDE[vs2010](../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b1429-105">Open [!INCLUDE[vs2010](../../../includes/vs2010-md.md)].</span></span>  <span data-ttu-id="b1429-106">Vyberte **soubor**, **nové**, **projektu**.</span><span class="sxs-lookup"><span data-stu-id="b1429-106">Select **File**, **New**, **Project**.</span></span>  <span data-ttu-id="b1429-107">V části **C#**, vyberte **pracovního postupu** uzlu.</span><span class="sxs-lookup"><span data-stu-id="b1429-107">Under **C#**, select the **Workflow** node.</span></span>  <span data-ttu-id="b1429-108">Vyberte **pracovního postupu konzolové aplikace** ze seznamu šablon.</span><span class="sxs-lookup"><span data-stu-id="b1429-108">Select **Workflow Console Application** from the list of templates.</span></span>  <span data-ttu-id="b1429-109">Název nového projektu `WorkflowDurationTracing` a klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="b1429-109">Name the new project `WorkflowDurationTracing` and click **OK**.</span></span>  
  
2.  <span data-ttu-id="b1429-110">Otevřete Workflow1.xaml.</span><span class="sxs-lookup"><span data-stu-id="b1429-110">Open Workflow1.xaml.</span></span>  <span data-ttu-id="b1429-111">Přetáhněte <xref:System.Activities.Statements.Delay> aktivity na plochu návrháře.</span><span class="sxs-lookup"><span data-stu-id="b1429-111">Drag a <xref:System.Activities.Statements.Delay> activity onto the designer surface.</span></span> <span data-ttu-id="b1429-112">Vlastnost doba trvání aktivity přiřadíte hodnotu 00:00:10 (deseti sekund).</span><span class="sxs-lookup"><span data-stu-id="b1429-112">Assign the value 00:00:10 (ten seconds) to the Duration property of the activity.</span></span>  
  
3.  <span data-ttu-id="b1429-113">Otevřete Prohlížeč událostí kliknutím **spustit**, **spustit**a zadáním `eventvwr.exe`.</span><span class="sxs-lookup"><span data-stu-id="b1429-113">Open Event Viewer by clicking **Start**, **Run**, and entering `eventvwr.exe`.</span></span>  
  
4.  <span data-ttu-id="b1429-114">Pokud jste nepovolili trasování pracovního postupu, rozbalte položku **protokoly aplikací a služeb**, **Microsoft**, **Windows**, **serveru aplikace – aplikace** .</span><span class="sxs-lookup"><span data-stu-id="b1429-114">If you haven’t enabled workflow tracing, expand **Applications and Services Logs**, **Microsoft**, **Windows**, **Application Server-Applications**.</span></span> <span data-ttu-id="b1429-115">Vyberte **zobrazení**, **ukazují analytické a ladicí protokoly**.</span><span class="sxs-lookup"><span data-stu-id="b1429-115">Select **View**, **Show Analytic and Debug Logs**.</span></span> <span data-ttu-id="b1429-116">Klikněte pravým tlačítkem na **ladění** a vyberte **povolit protokol**.</span><span class="sxs-lookup"><span data-stu-id="b1429-116">Right-click **Debug** and select **Enable Log**.</span></span> <span data-ttu-id="b1429-117">Ponechte prohlížeče událostí otevřete tak, aby trasování lze zobrazit po spuštění pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="b1429-117">Leave Event Viewer open so that traces can be viewed after the workflow is run.</span></span>  
  
5.  <span data-ttu-id="b1429-118">Spusťte pracovní postup aplikace stisknutím kombinace kláves CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="b1429-118">Execute the workflow application by pressing CTRL+SHIFT+B.</span></span>  
  
6.  <span data-ttu-id="b1429-119">V prohlížeči událostí najdete poslední událost s ID 1009 a zobrazí se zpráva podobná této.</span><span class="sxs-lookup"><span data-stu-id="b1429-119">In Event Viewer, find a recent event with ID 1009 and a message similar to the following.</span></span> <span data-ttu-id="b1429-120">Poznamenejte si dobu, která zprávu protokolu byla zaznamenána.</span><span class="sxs-lookup"><span data-stu-id="b1429-120">Make a note of the time that the message was logged.</span></span>  
  
 <span data-ttu-id="b1429-121">**Nadřazené aktivity '', DisplayName: ", identifikátor InstanceId: '' naplánované podřízené aktivity 'WorkflowDurationTracking.Workflow1', DisplayName: 'Workflow1', identifikátor InstanceId: '1'.**</span><span class="sxs-lookup"><span data-stu-id="b1429-121">**Parent Activity '', DisplayName: '', InstanceId: '' scheduled child Activity 'WorkflowDurationTracking.Workflow1', DisplayName: 'Workflow1', InstanceId: '1'.**</span></span>  
  
7.  <span data-ttu-id="b1429-122">Najít jinou poslední událost s ID 1001 a zobrazí se zpráva podobná této.</span><span class="sxs-lookup"><span data-stu-id="b1429-122">Find another recent event with ID 1001 and a message similar to the following.</span></span>  <span data-ttu-id="b1429-123">Odečtena předchozí čas zprávy od této zprávy protokolováno hodnoty určete dobu trvání provádění pracovního postupu, které by měly být přibližně 10 sekund.</span><span class="sxs-lookup"><span data-stu-id="b1429-123">Subtract the previous message time from this message’s Logged value to determine workflow execution duration, which should be around 10 seconds.</span></span>  
  
 <span data-ttu-id="b1429-124">**Instance pracovního postupu Id: '1bbac57b-3322-498e-9e27-8833fda3a5bf' byla dokončena v uzavřeném stavu.**</span><span class="sxs-lookup"><span data-stu-id="b1429-124">**WorkflowInstance Id: '1bbac57b-3322-498e-9e27-8833fda3a5bf' has completed in the Closed state.**</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1429-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="b1429-125">See Also</span></span>  
 [<span data-ttu-id="b1429-126">Trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="b1429-126">Workflow Tracing</span></span>](../../../docs/framework/windows-workflow-foundation/workflow-tracing.md)  
 [<span data-ttu-id="b1429-127">Windows Server App Fabric monitorování</span><span class="sxs-lookup"><span data-stu-id="b1429-127">Windows Server App Fabric Monitoring</span></span>](http://go.microsoft.com/fwlink/?LinkId=201273)  
 [<span data-ttu-id="b1429-128">Monitorování aplikací pomocí App Fabric</span><span class="sxs-lookup"><span data-stu-id="b1429-128">Monitoring Applications with App Fabric</span></span>](http://go.microsoft.com/fwlink/?LinkId=201275)
