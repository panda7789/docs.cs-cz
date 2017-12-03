---
title: Modul runtime aktivity v WF
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e5ae8c31-19bc-4655-88b3-6b75cd6a1bd5
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 022f12448d697ba179fb3705f18962e6b0c44239
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="runtime-activities-in-wf"></a><span data-ttu-id="ea0f8-102">Modul runtime aktivity v WF</span><span class="sxs-lookup"><span data-stu-id="ea0f8-102">Runtime Activities in WF</span></span>
[!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)]<span data-ttu-id="ea0f8-103">poskytuje několik poskytované systémem aktivity pro přístup k funkce modulu runtime pracovního postupu, jako je například trvalosti a ukončení.</span><span class="sxs-lookup"><span data-stu-id="ea0f8-103"> provides several system-provided activities for accessing the features of the workflow runtime, such as persistence and termination.</span></span>  
  
|<span data-ttu-id="ea0f8-104">Aktivita</span><span class="sxs-lookup"><span data-stu-id="ea0f8-104">Activity</span></span>|<span data-ttu-id="ea0f8-105">Popis</span><span class="sxs-lookup"><span data-stu-id="ea0f8-105">Description</span></span>|  
|--------------|-----------------|  
|<xref:System.Activities.Statements.Persist>|<span data-ttu-id="ea0f8-106">Výslovně požaduje, aby pracovní postup zachování stavu.</span><span class="sxs-lookup"><span data-stu-id="ea0f8-106">Explicitly requests that the workflow persist its state.</span></span>|  
|<xref:System.Activities.Statements.TerminateWorkflow>|<span data-ttu-id="ea0f8-107">Ukončí spuštěné instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="ea0f8-107">Terminates the running workflow instance.</span></span>|  
|<xref:System.Activities.Statements.NoPersistScope>|<span data-ttu-id="ea0f8-108">Aktivita kontejneru, který brání uložením podřízené aktivity.</span><span class="sxs-lookup"><span data-stu-id="ea0f8-108">A container activity that prevents child activities from persisting.</span></span>|
