---
title: Akce dokončení instance
ms.date: 03/30/2017
ms.assetid: 90cc99d2-9fef-42fd-bcbf-a56917993721
ms.openlocfilehash: d68f41a586e44f96c9ca26cf8a142a2782adaa36
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64662980"
---
# <a name="instance-completion-action"></a><span data-ttu-id="dae69-102">Akce dokončení instance</span><span class="sxs-lookup"><span data-stu-id="dae69-102">Instance Completion Action</span></span>
<span data-ttu-id="dae69-103">**Akce dokončení Instance** vlastnost Store Instance pracovního postupu SQL umožňuje určit, zda data a metadata instancí pracovních postupů je odstraněn z databáze stálost po dokončení instance.</span><span class="sxs-lookup"><span data-stu-id="dae69-103">The **Instance Completion Action** property of the SQL Workflow Instance Store lets you specify whether the data and metadata of workflow instances is deleted from the persistence database after the instances are completed.</span></span> <span data-ttu-id="dae69-104">Povolené hodnoty pro tuto vlastnost **DeleteAll** a **DeleteNothing**.</span><span class="sxs-lookup"><span data-stu-id="dae69-104">The allowed values for this property are **DeleteAll** and **DeleteNothing**.</span></span> <span data-ttu-id="dae69-105">Následující seznam popisuje tyto možnosti:</span><span class="sxs-lookup"><span data-stu-id="dae69-105">The following list describes these options:</span></span>  
  
- <span data-ttu-id="dae69-106">**DeleteAll (výchozí).**</span><span class="sxs-lookup"><span data-stu-id="dae69-106">**DeleteAll (default).**</span></span> <span data-ttu-id="dae69-107">Pokud je nastavena hodnota vlastnosti DeleteAll, data a metadata instancí pracovních postupů je odstranit z databáze stálost po dokončení instance.</span><span class="sxs-lookup"><span data-stu-id="dae69-107">If the value of the property is set to DeleteAll, the data and metadata of workflow instances is deleted from the persistence database after the instances are completed.</span></span>  
  
- <span data-ttu-id="dae69-108">**DeleteNothing.**</span><span class="sxs-lookup"><span data-stu-id="dae69-108">**DeleteNothing.**</span></span> <span data-ttu-id="dae69-109">Pokud je nastavena hodnota vlastnosti DeleteNothing, data a metadata instancí pracovních postupů, zůstane databáze trvalosti i po dokončení instance.</span><span class="sxs-lookup"><span data-stu-id="dae69-109">If the value of the property is set to DeleteNothing, the data and metadata of workflow instances is kept in the persistence database even after the instances are completed.</span></span>  
  
    > [!CAUTION]
    >  <span data-ttu-id="dae69-110">Zachování informací o stavu instance instance po dokončení způsobí, že databáze stálost k rozvoji velikosti.</span><span class="sxs-lookup"><span data-stu-id="dae69-110">Keeping instance state information after the instances are completed causes the persistence database to grow in size.</span></span> <span data-ttu-id="dae69-111">Databázových operací, které provádí subsystému trvalost nárůstu velikosti databáze trvat déle, takže je třeba vymazat informace o stavu instance z databáze trvalosti pravidelně, aby se mají provést na úrovni služby, které splňují vaše požadavkům na výkon.</span><span class="sxs-lookup"><span data-stu-id="dae69-111">As the size of the database grows the database operations that the persistence subsystem performs take longer, so you need to purge the instance state information from the persistence database periodically to have services perform at the level that satisfy your performance needs.</span></span>
