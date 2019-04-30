---
title: Aktivit primitiv v WF
ms.date: 03/30/2017
ms.assetid: 8e9009d1-236e-4d8e-86fc-e43132bf6dfc
ms.openlocfilehash: d87125d8d85fa33a49651dfabb840881b0e216ce
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61780702"
---
# <a name="primitives-activities-in-wf"></a><span data-ttu-id="0d50e-102">Aktivit primitiv v WF</span><span class="sxs-lookup"><span data-stu-id="0d50e-102">Primitives Activities in WF</span></span>
[!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] <span data-ttu-id="0d50e-103">poskytuje několik poskytované systémem aktivity, které poskytují vhodný mechanismus pro provádění běžných úloh.</span><span class="sxs-lookup"><span data-stu-id="0d50e-103">provides several system-provided activities that provide a convenient mechanism for performing common tasks.</span></span>  
  
|<span data-ttu-id="0d50e-104">Aktivita</span><span class="sxs-lookup"><span data-stu-id="0d50e-104">Activity</span></span>|<span data-ttu-id="0d50e-105">Popis</span><span class="sxs-lookup"><span data-stu-id="0d50e-105">Description</span></span>|  
|--------------|-----------------|  
|<xref:System.Activities.Statements.Assign>|<span data-ttu-id="0d50e-106">Přiřadí hodnotu k proměnné v aktuálním oboru.</span><span class="sxs-lookup"><span data-stu-id="0d50e-106">Assigns a value to a variable at the current scope.</span></span>|  
|<xref:System.Activities.Statements.Delay>|<span data-ttu-id="0d50e-107">Jedna cesta spuštění se zařadí do stavu nečinnosti, potenciálně umožňující pracovní postup bude odpojen.</span><span class="sxs-lookup"><span data-stu-id="0d50e-107">Puts one path of execution into an idle state, possibly allowing the workflow to be unloaded.</span></span>|  
|<xref:System.Activities.Statements.InvokeDelegate>|<span data-ttu-id="0d50e-108">Spouští delegáta, který je odvozen od <xref:System.Activities.ActivityDelegate> a je přístupný jako vlastnost.</span><span class="sxs-lookup"><span data-stu-id="0d50e-108">Executes a delegate that derives from <xref:System.Activities.ActivityDelegate> and is exposed as a property.</span></span>|  
|<xref:System.Activities.Statements.InvokeMethod>|<span data-ttu-id="0d50e-109">Provede veřejnou metodu objektu CLR.</span><span class="sxs-lookup"><span data-stu-id="0d50e-109">Executes a public method of a CLR object.</span></span>|  
|<xref:System.Activities.Statements.WriteLine>|<span data-ttu-id="0d50e-110">Zapíše zadaný řetězec na konzole nebo zadané <xref:System.IO.TextWriter> objektu.</span><span class="sxs-lookup"><span data-stu-id="0d50e-110">Writes a specified string to the console or a specified <xref:System.IO.TextWriter> object.</span></span>|
