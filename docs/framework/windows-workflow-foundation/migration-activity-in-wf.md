---
title: Aktivita migrace v WF
ms.date: 03/30/2017
ms.assetid: 4ad46db7-5744-410e-8fac-6c3b325b1dd0
ms.openlocfilehash: 26fdb80c081fc49986be6cba4c6df91ade8b0b66
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69944722"
---
# <a name="migration-activity-in-wf"></a><span data-ttu-id="4c2e5-102">Aktivita migrace v WF</span><span class="sxs-lookup"><span data-stu-id="4c2e5-102">Migration Activity in WF</span></span>
[!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)]<span data-ttu-id="4c2e5-103">poskytuje aktivitu pro provádění aktivit, které jsou odvozeny z aktivity v rámci pracovního postupu, <xref:System.Activities.Activity>na kterém je založena. <xref:System.Activities.Statements.Interop></span><span class="sxs-lookup"><span data-stu-id="4c2e5-103">provides the <xref:System.Activities.Statements.Interop> activity for executing activities that derive from Activity within a workflow that is based on <xref:System.Activities.Activity>.</span></span> <span data-ttu-id="4c2e5-104">Další informace najdete v části [pokyny k migraci](migration-guidance.md) .</span><span class="sxs-lookup"><span data-stu-id="4c2e5-104">For more information, see the [Migration Guidance](migration-guidance.md) section.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4c2e5-105">Tato <xref:System.Activities.Statements.Interop> aktivita se nezobrazí v sadě nástrojů návrháře pracovních postupů, pokud nemá projekt pracovního postupu nastavenou **cílovou architekturu** na **.NET Framework 4** nebo vyšší.</span><span class="sxs-lookup"><span data-stu-id="4c2e5-105">The <xref:System.Activities.Statements.Interop> activity does not appear in the workflow designer toolbox unless the workflow's project has its **Target Framework** setting set to **.Net Framework 4** or higher.</span></span>
