---
title: "Kódování možnost instance"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 89e4b029-4f68-438c-8117-9b21fe094ef4
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 5803b034eeecac66aa20951c5167b9e666f1fa8c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="instance-encoding-option"></a><span data-ttu-id="6c0f5-102">Kódování možnost instance</span><span class="sxs-lookup"><span data-stu-id="6c0f5-102">Instance Encoding Option</span></span>
<span data-ttu-id="6c0f5-103">**Instance kódování možnost** vlastnost úložiště Instance pracovního postupu SQL umožňuje určit, zda zprostředkovatel trvalost SQL by měl komprimovat informace stavu instance pracovního postupu pomocí algoritmu GZip před uložením informace do databáze trvalost.</span><span class="sxs-lookup"><span data-stu-id="6c0f5-103">The **Instance Encoding Option** property of the SQL Workflow Instance Store lets you specify whether the SQL persistence provider should compress the workflow instance state information using the GZip algorithm before saving the information into the persistence database.</span></span> <span data-ttu-id="6c0f5-104">Povolené hodnoty pro tuto vlastnost jsou: GZip a None.</span><span class="sxs-lookup"><span data-stu-id="6c0f5-104">The allowed values for this property are: GZip and None.</span></span> <span data-ttu-id="6c0f5-105">Výchozí hodnota je žádné.</span><span class="sxs-lookup"><span data-stu-id="6c0f5-105">The default value is None.</span></span> <span data-ttu-id="6c0f5-106">Následující seznam popisuje tyto možnosti.</span><span class="sxs-lookup"><span data-stu-id="6c0f5-106">The following list describes these options.</span></span>  
  
1.  <span data-ttu-id="6c0f5-107">**GZip**.</span><span class="sxs-lookup"><span data-stu-id="6c0f5-107">**GZip**.</span></span> <span data-ttu-id="6c0f5-108">Zprostředkovatel trvalost kóduje informace o stavu pomocí algoritmu GZip před uložením informace o stavu v databázi trvalost.</span><span class="sxs-lookup"><span data-stu-id="6c0f5-108">The persistence provider encodes the state information using the GZip algorithm before persisting the state information in the persistence database.</span></span>  
  
2.  <span data-ttu-id="6c0f5-109">**Žádný**.</span><span class="sxs-lookup"><span data-stu-id="6c0f5-109">**None**.</span></span> <span data-ttu-id="6c0f5-110">Zprostředkovatel trvalost neprovádí kódování informace o stavu před uložením informace do databáze trvalost.</span><span class="sxs-lookup"><span data-stu-id="6c0f5-110">The persistence provider does not encode the state information before saving the information into the persistence database.</span></span>  
  
 <span data-ttu-id="6c0f5-111">Kódování instance informace o stavu pracovního postupu pomocí GZip snižuje využití paměti v databázi SQL a také snižuje spotřeba síťových, pokud se databáze nachází v jiném počítači v síti z počítače, na která hostitele služby pracovního postupu spuštěna.</span><span class="sxs-lookup"><span data-stu-id="6c0f5-111">Encoding workflow instance state information using the GZip reduces memory consumption in the SQL database and also reduces network consumption if the database resides on a different computer on the network from the computer on which the workflow service host is running.</span></span> <span data-ttu-id="6c0f5-112">Obecné pokyny je nastavit **Instance kódování možnost** vlastnost **žádné** Pokud stav instance pracovního postupu je malá.</span><span class="sxs-lookup"><span data-stu-id="6c0f5-112">A general guidance is to set the **Instance Encoding Option** property to **None** if the workflow instance state is small.</span></span>
