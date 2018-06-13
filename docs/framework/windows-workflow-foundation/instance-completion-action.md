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
# <a name="instance-completion-action"></a>Instance dokončení akce
**Instance dokončení akce** vlastnost úložiště Instance pracovního postupu SQL umožňuje určit, zda data a metadata instancí pracovního postupu odstraněn z databáze trvalost po dokončení instance. Povolené hodnoty pro tuto vlastnost jsou **DeleteAll** a **DeleteNothing**. Následující seznam popisuje tyto možnosti:  
  
-   **DeleteAll (výchozí).** Pokud je nastavena hodnota vlastnosti DeleteAll, data a metadata instancí pracovního postupu je odstraněn z databáze trvalost po dokončení instance.  
  
-   **DeleteNothing.** Pokud je nastavena hodnota vlastnosti DeleteNothing, data a metadata instancí pracovního postupu je uložen v databázi trvalost i po dokončení instance.  
  
    > [!CAUTION]
    >  Udržuje informace o stavu instance po instance jsou dokončené příčiny zvětšování velikost databáze trvalost. Velikost databáze s růstem databázových operací, které provádí subsystém trvalost trvat déle, takže je třeba vymazat informace o stavu instance z databáze trvalost pravidelně tak, aby měl provést na úrovni služby, které splňují vaše požadavkům na výkon.
