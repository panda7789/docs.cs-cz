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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3fa2eb347bc69a89545e6145154306f012e23490
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="instance-completion-action"></a>Instance dokončení akce
**Instance dokončení akce** vlastnost úložiště Instance pracovního postupu SQL umožňuje určit, zda data a metadata instancí pracovního postupu odstraněn z databáze trvalost po dokončení instance. Povolené hodnoty pro tuto vlastnost jsou **DeleteAll** a **DeleteNothing**. Následující seznam popisuje tyto možnosti:  
  
-   **DeleteAll (výchozí).** Pokud je nastavena hodnota vlastnosti DeleteAll, data a metadata instancí pracovního postupu je odstraněn z databáze trvalost po dokončení instance.  
  
-   **DeleteNothing.** Pokud je nastavena hodnota vlastnosti DeleteNothing, data a metadata instancí pracovního postupu je uložen v databázi trvalost i po dokončení instance.  
  
    > [!CAUTION]
    >  Udržuje informace o stavu instance po instance jsou dokončené příčiny zvětšování velikost databáze trvalost. Velikost databáze s růstem databázových operací, které provádí subsystém trvalost trvat déle, takže je třeba vymazat informace o stavu instance z databáze trvalost pravidelně tak, aby měl provést na úrovni služby, které splňují vaše požadavkům na výkon.
