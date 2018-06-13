---
title: Modul runtime aktivity v WF
ms.date: 03/30/2017
ms.assetid: e5ae8c31-19bc-4655-88b3-6b75cd6a1bd5
ms.openlocfilehash: 7981d3f75c8fd2d0ddd2ae0233f425c2907c270c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33513032"
---
# <a name="runtime-activities-in-wf"></a><span data-ttu-id="73d31-102">Modul runtime aktivity v WF</span><span class="sxs-lookup"><span data-stu-id="73d31-102">Runtime Activities in WF</span></span>
[!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)]<span data-ttu-id="73d31-103"> poskytuje několik poskytované systémem aktivity pro přístup k funkce modulu runtime pracovního postupu, jako je například trvalosti a ukončení.</span><span class="sxs-lookup"><span data-stu-id="73d31-103"> provides several system-provided activities for accessing the features of the workflow runtime, such as persistence and termination.</span></span>  
  
|<span data-ttu-id="73d31-104">Aktivita</span><span class="sxs-lookup"><span data-stu-id="73d31-104">Activity</span></span>|<span data-ttu-id="73d31-105">Popis</span><span class="sxs-lookup"><span data-stu-id="73d31-105">Description</span></span>|  
|--------------|-----------------|  
|<xref:System.Activities.Statements.Persist>|<span data-ttu-id="73d31-106">Výslovně požaduje, aby pracovní postup zachování stavu.</span><span class="sxs-lookup"><span data-stu-id="73d31-106">Explicitly requests that the workflow persist its state.</span></span>|  
|<xref:System.Activities.Statements.TerminateWorkflow>|<span data-ttu-id="73d31-107">Ukončí spuštěné instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="73d31-107">Terminates the running workflow instance.</span></span>|  
|<xref:System.Activities.Statements.NoPersistScope>|<span data-ttu-id="73d31-108">Aktivita kontejneru, který brání uložením podřízené aktivity.</span><span class="sxs-lookup"><span data-stu-id="73d31-108">A container activity that prevents child activities from persisting.</span></span>|
