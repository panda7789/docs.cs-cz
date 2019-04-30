---
title: Modul runtime aktivit v WF
ms.date: 03/30/2017
ms.assetid: e5ae8c31-19bc-4655-88b3-6b75cd6a1bd5
ms.openlocfilehash: 7981d3f75c8fd2d0ddd2ae0233f425c2907c270c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61938096"
---
# <a name="runtime-activities-in-wf"></a><span data-ttu-id="7d8d8-102">Modul runtime aktivit v WF</span><span class="sxs-lookup"><span data-stu-id="7d8d8-102">Runtime Activities in WF</span></span>
[!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] <span data-ttu-id="7d8d8-103">poskytuje několik aktivit poskytované systémem pro přístup k funkcím modulu runtime pracovního postupu, jako je například trvalost a ukončení.</span><span class="sxs-lookup"><span data-stu-id="7d8d8-103">provides several system-provided activities for accessing the features of the workflow runtime, such as persistence and termination.</span></span>  
  
|<span data-ttu-id="7d8d8-104">Aktivita</span><span class="sxs-lookup"><span data-stu-id="7d8d8-104">Activity</span></span>|<span data-ttu-id="7d8d8-105">Popis</span><span class="sxs-lookup"><span data-stu-id="7d8d8-105">Description</span></span>|  
|--------------|-----------------|  
|<xref:System.Activities.Statements.Persist>|<span data-ttu-id="7d8d8-106">Výslovně požaduje, aby pracovní postup zachování stavu.</span><span class="sxs-lookup"><span data-stu-id="7d8d8-106">Explicitly requests that the workflow persist its state.</span></span>|  
|<xref:System.Activities.Statements.TerminateWorkflow>|<span data-ttu-id="7d8d8-107">Ukončí běžící instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="7d8d8-107">Terminates the running workflow instance.</span></span>|  
|<xref:System.Activities.Statements.NoPersistScope>|<span data-ttu-id="7d8d8-108">Aktivita kontejneru, který brání uchování podřízené aktivity.</span><span class="sxs-lookup"><span data-stu-id="7d8d8-108">A container activity that prevents child activities from persisting.</span></span>|
