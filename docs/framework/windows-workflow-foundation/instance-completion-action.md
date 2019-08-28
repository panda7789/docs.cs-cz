---
title: Akce dokončení instance
ms.date: 03/30/2017
ms.assetid: 90cc99d2-9fef-42fd-bcbf-a56917993721
ms.openlocfilehash: 698ac0ed5a7cbd4f6a5623cf8d9b6fbea1128d0a
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2019
ms.locfileid: "70044333"
---
# <a name="instance-completion-action"></a><span data-ttu-id="39ffb-102">Akce dokončení instance</span><span class="sxs-lookup"><span data-stu-id="39ffb-102">Instance Completion Action</span></span>

<span data-ttu-id="39ffb-103">Vlastnost **Akce dokončení instance** úložiště instance pracovního postupu SQL umožňuje určit, zda jsou data a metadata instancí pracovních postupů po dokončení instancí odstraněny z databáze trvalosti.</span><span class="sxs-lookup"><span data-stu-id="39ffb-103">The **Instance Completion Action** property of the SQL Workflow Instance Store lets you specify whether the data and metadata of workflow instances is deleted from the persistence database after the instances are completed.</span></span> <span data-ttu-id="39ffb-104">Povolené hodnoty pro tuto vlastnost jsou **DeleteAll** a **DeleteNothing**.</span><span class="sxs-lookup"><span data-stu-id="39ffb-104">The allowed values for this property are **DeleteAll** and **DeleteNothing**.</span></span> <span data-ttu-id="39ffb-105">Následující seznam popisuje tyto možnosti:</span><span class="sxs-lookup"><span data-stu-id="39ffb-105">The following list describes these options:</span></span>

- <span data-ttu-id="39ffb-106">**DeleteAll (výchozí).**</span><span class="sxs-lookup"><span data-stu-id="39ffb-106">**DeleteAll (default).**</span></span> <span data-ttu-id="39ffb-107">Pokud je hodnota vlastnosti nastavena na DeleteAll, data a metadata instancí pracovního postupu jsou po dokončení instancí odstraněny z databáze trvalosti.</span><span class="sxs-lookup"><span data-stu-id="39ffb-107">If the value of the property is set to DeleteAll, the data and metadata of workflow instances is deleted from the persistence database after the instances are completed.</span></span>

- <span data-ttu-id="39ffb-108">**DeleteNothing.**</span><span class="sxs-lookup"><span data-stu-id="39ffb-108">**DeleteNothing.**</span></span> <span data-ttu-id="39ffb-109">Pokud je hodnota vlastnosti nastavena na DeleteNothing, data a metadata instancí pracovního postupu jsou uchovávány v databázi trvalosti i po dokončení instancí.</span><span class="sxs-lookup"><span data-stu-id="39ffb-109">If the value of the property is set to DeleteNothing, the data and metadata of workflow instances is kept in the persistence database even after the instances are completed.</span></span>

  > [!CAUTION]
  > <span data-ttu-id="39ffb-110">Uchovávání informací o stavu instance po dokončení instancí způsobí, že databáze trvala velikost.</span><span class="sxs-lookup"><span data-stu-id="39ffb-110">Keeping instance state information after the instances are completed causes the persistence database to grow in size.</span></span> <span data-ttu-id="39ffb-111">Vzhledem k tomu, že velikost databáze rozroste databázové operace, které podsystém trvalosti trvá, je třeba pravidelně vyprázdnit informace o stavu instance z databáze trvalosti, aby služby prováděly na úrovni, která vyhovuje vašim požadavky na výkon.</span><span class="sxs-lookup"><span data-stu-id="39ffb-111">As the size of the database grows the database operations that the persistence subsystem performs take longer, so you need to purge the instance state information from the persistence database periodically to have services perform at the level that satisfy your performance needs.</span></span>
