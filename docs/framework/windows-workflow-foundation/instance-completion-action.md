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
ms.openlocfilehash: 83dec7ef4c911c0bca94caf7cc4c4bf832c8e1b6
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="instance-completion-action"></a>Instance dokončení akce
**Instance dokončení akce** vlastnost úložiště Instance pracovního postupu SQL umožňuje určit, zda data a metadata instancí pracovního postupu odstraněn z databáze trvalost po dokončení instance. Povolené hodnoty pro tuto vlastnost jsou **DeleteAll** a **DeleteNothing**. Následující seznam popisuje tyto možnosti:  
  
-   **DeleteAll (výchozí).** Pokud je nastavena hodnota vlastnosti DeleteAll, data a metadata instancí pracovního postupu je odstraněn z databáze trvalost po dokončení instance.  
  
-   **DeleteNothing.** Pokud je nastavena hodnota vlastnosti DeleteNothing, data a metadata instancí pracovního postupu je uložen v databázi trvalost i po dokončení instance.  
  
    > [!CAUTION]
    >  Udržuje informace o stavu instance po instance jsou dokončené příčiny zvětšování velikost databáze trvalost. Velikost databáze s růstem databázových operací, které provádí subsystém trvalost trvat déle, takže je třeba vymazat informace o stavu instance z databáze trvalost pravidelně tak, aby měl provést na úrovni služby, které splňují vaše požadavkům na výkon.
