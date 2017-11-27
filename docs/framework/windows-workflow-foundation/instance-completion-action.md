---
title: "Instance dokončení akce"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 90cc99d2-9fef-42fd-bcbf-a56917993721
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 4d1e0f367ef167e5bf47d0936e0b3200ca7dbe19
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="instance-completion-action"></a><span data-ttu-id="e6bfa-102">Instance dokončení akce</span><span class="sxs-lookup"><span data-stu-id="e6bfa-102">Instance Completion Action</span></span>
<span data-ttu-id="e6bfa-103">**Instance dokončení akce** vlastnost úložiště Instance pracovního postupu SQL umožňuje určit, zda data a metadata instancí pracovního postupu odstraněn z databáze trvalost po dokončení instance.</span><span class="sxs-lookup"><span data-stu-id="e6bfa-103">The **Instance Completion Action** property of the SQL Workflow Instance Store lets you specify whether the data and metadata of workflow instances is deleted from the persistence database after the instances are completed.</span></span> <span data-ttu-id="e6bfa-104">Povolené hodnoty pro tuto vlastnost jsou **DeleteAll** a **DeleteNothing**.</span><span class="sxs-lookup"><span data-stu-id="e6bfa-104">The allowed values for this property are **DeleteAll** and **DeleteNothing**.</span></span> <span data-ttu-id="e6bfa-105">Následující seznam popisuje tyto možnosti:</span><span class="sxs-lookup"><span data-stu-id="e6bfa-105">The following list describes these options:</span></span>  
  
-   <span data-ttu-id="e6bfa-106">**DeleteAll (výchozí).**</span><span class="sxs-lookup"><span data-stu-id="e6bfa-106">**DeleteAll (default).**</span></span> <span data-ttu-id="e6bfa-107">Pokud je nastavena hodnota vlastnosti DeleteAll, data a metadata instancí pracovního postupu je odstraněn z databáze trvalost po dokončení instance.</span><span class="sxs-lookup"><span data-stu-id="e6bfa-107">If the value of the property is set to DeleteAll, the data and metadata of workflow instances is deleted from the persistence database after the instances are completed.</span></span>  
  
-   <span data-ttu-id="e6bfa-108">**DeleteNothing.**</span><span class="sxs-lookup"><span data-stu-id="e6bfa-108">**DeleteNothing.**</span></span> <span data-ttu-id="e6bfa-109">Pokud je nastavena hodnota vlastnosti DeleteNothing, data a metadata instancí pracovního postupu je uložen v databázi trvalost i po dokončení instance.</span><span class="sxs-lookup"><span data-stu-id="e6bfa-109">If the value of the property is set to DeleteNothing, the data and metadata of workflow instances is kept in the persistence database even after the instances are completed.</span></span>  
  
    > [!CAUTION]
    >  <span data-ttu-id="e6bfa-110">Udržuje informace o stavu instance po instance jsou dokončené příčiny zvětšování velikost databáze trvalost.</span><span class="sxs-lookup"><span data-stu-id="e6bfa-110">Keeping instance state information after the instances are completed causes the persistence database to grow in size.</span></span> <span data-ttu-id="e6bfa-111">Velikost databáze s růstem databázových operací, které provádí subsystém trvalost trvat déle, takže je třeba vymazat informace o stavu instance z databáze trvalost pravidelně tak, aby měl provést na úrovni služby, které splňují vaše požadavkům na výkon.</span><span class="sxs-lookup"><span data-stu-id="e6bfa-111">As the size of the database grows the database operations that the persistence subsystem performs take longer, so you need to purge the instance state information from the persistence database periodically to have services perform at the level that satisfy your performance needs.</span></span>
