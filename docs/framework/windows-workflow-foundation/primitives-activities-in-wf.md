---
title: Primitiva aktivity v WF
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8e9009d1-236e-4d8e-86fc-e43132bf6dfc
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e411d922577dcb9d3ca322d61c0e10911a006027
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="primitives-activities-in-wf"></a><span data-ttu-id="9bb70-102">Primitiva aktivity v WF</span><span class="sxs-lookup"><span data-stu-id="9bb70-102">Primitives Activities in WF</span></span>
[!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)]<span data-ttu-id="9bb70-103">poskytuje několik poskytované systémem aktivity, které poskytují vhodný mechanismus pro provádění běžných úloh.</span><span class="sxs-lookup"><span data-stu-id="9bb70-103"> provides several system-provided activities that provide a convenient mechanism for performing common tasks.</span></span>  
  
|<span data-ttu-id="9bb70-104">Aktivita</span><span class="sxs-lookup"><span data-stu-id="9bb70-104">Activity</span></span>|<span data-ttu-id="9bb70-105">Popis</span><span class="sxs-lookup"><span data-stu-id="9bb70-105">Description</span></span>|  
|--------------|-----------------|  
|<xref:System.Activities.Statements.Assign>|<span data-ttu-id="9bb70-106">Přiřazuje hodnotu proměnné v aktuálním oboru.</span><span class="sxs-lookup"><span data-stu-id="9bb70-106">Assigns a value to a variable at the current scope.</span></span>|  
|<xref:System.Activities.Statements.Delay>|<span data-ttu-id="9bb70-107">Vloží jednu cestu pro provádění do nečinného stavu, může být povolení pracovního postupu jej odpojit.</span><span class="sxs-lookup"><span data-stu-id="9bb70-107">Puts one path of execution into an idle state, possibly allowing the workflow to be unloaded.</span></span>|  
|<xref:System.Activities.Statements.InvokeDelegate>|<span data-ttu-id="9bb70-108">Provede delegáta, který je odvozen od <xref:System.Activities.ActivityDelegate> a je k dispozici jako vlastnost.</span><span class="sxs-lookup"><span data-stu-id="9bb70-108">Executes a delegate that derives from <xref:System.Activities.ActivityDelegate> and is exposed as a property.</span></span>|  
|<xref:System.Activities.Statements.InvokeMethod>|<span data-ttu-id="9bb70-109">Provede veřejnou metodu objektu CLR.</span><span class="sxs-lookup"><span data-stu-id="9bb70-109">Executes a public method of a CLR object.</span></span>|  
|<xref:System.Activities.Statements.WriteLine>|<span data-ttu-id="9bb70-110">Zapíše zadaný řetězec na konzole nebo zadané <xref:System.IO.TextWriter> objektu.</span><span class="sxs-lookup"><span data-stu-id="9bb70-110">Writes a specified string to the console or a specified <xref:System.IO.TextWriter> object.</span></span>|
