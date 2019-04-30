---
title: Akce dokončení instance
ms.date: 03/30/2017
ms.assetid: 90cc99d2-9fef-42fd-bcbf-a56917993721
ms.openlocfilehash: 646015fbcdb7c734ae8584c7ca3979d64b81339f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61791115"
---
# <a name="instance-completion-action"></a><span data-ttu-id="abf34-102">Akce dokončení instance</span><span class="sxs-lookup"><span data-stu-id="abf34-102">Instance Completion Action</span></span>
<span data-ttu-id="abf34-103">**Akce dokončení Instance** vlastnost Store Instance pracovního postupu SQL umožňuje určit, zda data a metadata instancí pracovních postupů je odstraněn z databáze stálost po dokončení instance.</span><span class="sxs-lookup"><span data-stu-id="abf34-103">The **Instance Completion Action** property of the SQL Workflow Instance Store lets you specify whether the data and metadata of workflow instances is deleted from the persistence database after the instances are completed.</span></span> <span data-ttu-id="abf34-104">Povolené hodnoty pro tuto vlastnost **DeleteAll** a **DeleteNothing**.</span><span class="sxs-lookup"><span data-stu-id="abf34-104">The allowed values for this property are **DeleteAll** and **DeleteNothing**.</span></span> <span data-ttu-id="abf34-105">Následující seznam popisuje tyto možnosti:</span><span class="sxs-lookup"><span data-stu-id="abf34-105">The following list describes these options:</span></span>  
  
- <span data-ttu-id="abf34-106">**DeleteAll (výchozí).**</span><span class="sxs-lookup"><span data-stu-id="abf34-106">**DeleteAll (default).**</span></span> <span data-ttu-id="abf34-107">Pokud je nastavena hodnota vlastnosti DeleteAll, data a metadata instancí pracovních postupů je odstranit z databáze stálost po dokončení instance.</span><span class="sxs-lookup"><span data-stu-id="abf34-107">If the value of the property is set to DeleteAll, the data and metadata of workflow instances is deleted from the persistence database after the instances are completed.</span></span>  
  
- <span data-ttu-id="abf34-108">**DeleteNothing.**</span><span class="sxs-lookup"><span data-stu-id="abf34-108">**DeleteNothing.**</span></span> <span data-ttu-id="abf34-109">Pokud je nastavena hodnota vlastnosti DeleteNothing, data a metadata instancí pracovních postupů, zůstane databáze trvalosti i po dokončení instance.</span><span class="sxs-lookup"><span data-stu-id="abf34-109">If the value of the property is set to DeleteNothing, the data and metadata of workflow instances is kept in the persistence database even after the instances are completed.</span></span>  
  
    > [!CAUTION]
    >  <span data-ttu-id="abf34-110">Zachování informací o stavu instance instance po dokončení způsobí, že databáze stálost k rozvoji velikosti.</span><span class="sxs-lookup"><span data-stu-id="abf34-110">Keeping instance state information after the instances are completed causes the persistence database to grow in size.</span></span> <span data-ttu-id="abf34-111">Databázových operací, které provádí subsystému trvalost nárůstu velikosti databáze trvat déle, takže je třeba vymazat informace o stavu instance z databáze trvalosti pravidelně, aby se mají provést na úrovni služby, které splňují vaše požadavkům na výkon.</span><span class="sxs-lookup"><span data-stu-id="abf34-111">As the size of the database grows the database operations that the persistence subsystem performs take longer, so you need to purge the instance state information from the persistence database periodically to have services perform at the level that satisfy your performance needs.</span></span>
