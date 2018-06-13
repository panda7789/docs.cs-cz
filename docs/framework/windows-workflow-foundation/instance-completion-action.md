---
title: Instance dokončení akce
ms.date: 03/30/2017
ms.assetid: 90cc99d2-9fef-42fd-bcbf-a56917993721
ms.openlocfilehash: 646015fbcdb7c734ae8584c7ca3979d64b81339f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33513198"
---
# <a name="instance-completion-action"></a><span data-ttu-id="fbedb-102">Instance dokončení akce</span><span class="sxs-lookup"><span data-stu-id="fbedb-102">Instance Completion Action</span></span>
<span data-ttu-id="fbedb-103">**Instance dokončení akce** vlastnost úložiště Instance pracovního postupu SQL umožňuje určit, zda data a metadata instancí pracovního postupu odstraněn z databáze trvalost po dokončení instance.</span><span class="sxs-lookup"><span data-stu-id="fbedb-103">The **Instance Completion Action** property of the SQL Workflow Instance Store lets you specify whether the data and metadata of workflow instances is deleted from the persistence database after the instances are completed.</span></span> <span data-ttu-id="fbedb-104">Povolené hodnoty pro tuto vlastnost jsou **DeleteAll** a **DeleteNothing**.</span><span class="sxs-lookup"><span data-stu-id="fbedb-104">The allowed values for this property are **DeleteAll** and **DeleteNothing**.</span></span> <span data-ttu-id="fbedb-105">Následující seznam popisuje tyto možnosti:</span><span class="sxs-lookup"><span data-stu-id="fbedb-105">The following list describes these options:</span></span>  
  
-   <span data-ttu-id="fbedb-106">**DeleteAll (výchozí).**</span><span class="sxs-lookup"><span data-stu-id="fbedb-106">**DeleteAll (default).**</span></span> <span data-ttu-id="fbedb-107">Pokud je nastavena hodnota vlastnosti DeleteAll, data a metadata instancí pracovního postupu je odstraněn z databáze trvalost po dokončení instance.</span><span class="sxs-lookup"><span data-stu-id="fbedb-107">If the value of the property is set to DeleteAll, the data and metadata of workflow instances is deleted from the persistence database after the instances are completed.</span></span>  
  
-   <span data-ttu-id="fbedb-108">**DeleteNothing.**</span><span class="sxs-lookup"><span data-stu-id="fbedb-108">**DeleteNothing.**</span></span> <span data-ttu-id="fbedb-109">Pokud je nastavena hodnota vlastnosti DeleteNothing, data a metadata instancí pracovního postupu je uložen v databázi trvalost i po dokončení instance.</span><span class="sxs-lookup"><span data-stu-id="fbedb-109">If the value of the property is set to DeleteNothing, the data and metadata of workflow instances is kept in the persistence database even after the instances are completed.</span></span>  
  
    > [!CAUTION]
    >  <span data-ttu-id="fbedb-110">Udržuje informace o stavu instance po instance jsou dokončené příčiny zvětšování velikost databáze trvalost.</span><span class="sxs-lookup"><span data-stu-id="fbedb-110">Keeping instance state information after the instances are completed causes the persistence database to grow in size.</span></span> <span data-ttu-id="fbedb-111">Velikost databáze s růstem databázových operací, které provádí subsystém trvalost trvat déle, takže je třeba vymazat informace o stavu instance z databáze trvalost pravidelně tak, aby měl provést na úrovni služby, které splňují vaše požadavkům na výkon.</span><span class="sxs-lookup"><span data-stu-id="fbedb-111">As the size of the database grows the database operations that the persistence subsystem performs take longer, so you need to purge the instance state information from the persistence database periodically to have services perform at the level that satisfy your performance needs.</span></span>
