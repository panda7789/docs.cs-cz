---
title: "Období detekce spustitelného instancí"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4ea5c787-b638-47fd-bfc8-ede8c2898ce6
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 2a78f8404d5e6b9d63c9455d059dcbb9a76f8c18
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="runnable-instances-detection-period"></a><span data-ttu-id="f588d-102">Období detekce spustitelného instancí</span><span class="sxs-lookup"><span data-stu-id="f588d-102">Runnable Instances Detection Period</span></span>
<span data-ttu-id="f588d-103">Ukládání Instance pracovního postupu SQL spustí interní úloh, která pravidelně probudí a zjistí spustitelného nebo activatable instancí v databázi trvalost.</span><span class="sxs-lookup"><span data-stu-id="f588d-103">The SQL Workflow Instance Store runs an internal task that periodically wakes up and detects runnable or activatable instances in the persistence database.</span></span> <span data-ttu-id="f588d-104">**Spustitelného období zjišťování instancí** vlastnost úložiště Instance pracovního postupu SQL určuje časové období, po jejímž uplynutí ukládání Instance pracovního postupu SQL spustí úlohu detekce ke zjištění všech spustitelného nebo activatable pracovního postupu instance v databázi trvalost předchozího cyklu zjišťování.</span><span class="sxs-lookup"><span data-stu-id="f588d-104">The **Runnable Instances Detection Period** property of the SQL Workflow Instance Store specifies the time period after which the SQL Workflow Instance Store runs a detection task to detect any runnable or activatable workflow instances in the persistence database after the previous detection cycle.</span></span>  
  
 <span data-ttu-id="f588d-105">Nastavení kratší interval pro tuto vlastnost zkracuje dobu mezi vypršení platnosti časovač přidružený instanci pracovního postupu a signalizace událostí a následné načítání instance.</span><span class="sxs-lookup"><span data-stu-id="f588d-105">Setting a shorter interval for this property reduces the time between the expiration of a timer associated with a workflow instance and the signaling of the event and subsequent loading of the instance.</span></span> <span data-ttu-id="f588d-106">Však také zvyšuje zatížení na hostiteli a nemusí být žádoucí ve scénářích, kde jsou výjimečných trvanlivý časovače nebo selhání hostitele.</span><span class="sxs-lookup"><span data-stu-id="f588d-106">However, it also increases the processing load on a host and may not be desirable in scenarios where durable timers and/or host failures are rare.</span></span> <span data-ttu-id="f588d-107">Typ vlastnosti je časový interval a hodnota vlastnosti odpovídá formátu: hh: mm:.</span><span class="sxs-lookup"><span data-stu-id="f588d-107">The type of the property is TimeSpan and the value of the property follows the format: hh:mm:ss.</span></span> <span data-ttu-id="f588d-108">Minimální hodnota této vlastnosti je 00:00:01.</span><span class="sxs-lookup"><span data-stu-id="f588d-108">The minimum value for this property is 00:00:01.</span></span> <span data-ttu-id="f588d-109">Výchozí hodnota pro vlastnost je 00:00:05.</span><span class="sxs-lookup"><span data-stu-id="f588d-109">The default value for the property is 00:00:05.</span></span>  
  
 <span data-ttu-id="f588d-110">Další informace najdete v zjišťování a aktivace instance pracovního postupu spustitelného a activatable [Instance aktivace](../../../docs/framework/windows-workflow-foundation/instance-activation.md).</span><span class="sxs-lookup"><span data-stu-id="f588d-110">For more information detecting and activating runnable and activatable workflow instances, see [Instance Activation](../../../docs/framework/windows-workflow-foundation/instance-activation.md).</span></span>
