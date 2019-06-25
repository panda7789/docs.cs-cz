---
title: Zabezpečení
ms.date: 03/30/2017
ms.assetid: 737ec121-bfc5-4b75-a504-2d53c2c8af39
ms.openlocfilehash: cbfb82c2db329725d3445e1a88b54e01d5813f36
ms.sourcegitcommit: 127343afce8422bfa944c8b0c4ecc8f79f653255
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2019
ms.locfileid: "67348403"
---
# <a name="security"></a>Zabezpečení
Store Instance SQL pracovní postup používá Tyhle role zabezpečení databázi zabezpečit přístup k informacím o stavu instance databáze trvalosti.  
  
- **System.Activities.DurableInstancing.InstanceStoreUsers**. Tato role má ke čtení a oprávnění k zápisu do veřejné zobrazení a spuštění práva k uložené procedury, které jsou zahrnuty při vytváření, načítání a ukládání instancí.  
  
- **System.Activities.DurableInstancing.InstanceStoreObservers**. Tato role má oprávnění jen pro čtení k veřejné zobrazení.  
  
- **System.Activities.DurableInstancing.WorkflowActivationUsers**. Tato role má práva spuštění uložené procedury, které jsou součástí procesu aktivace instance. Další informace o aktivaci instance najdete v tématu [aktivace Instance](instance-activation.md). Uživatelský účet, pod kterým běží obecný hostitele (jako je například služba pracovního postupu správy funkce hostování služby Windows Server AppFabric) by měl být přidán k této roli databáze.  
  
 Další informace o zabezpečení pro úložiště trvalosti pomocí systému Windows Server App Fabric najdete v tématu [konfiguraci zabezpečení pro trvalého úložiště v prostředcích infrastruktury aplikace](https://go.microsoft.com/fwlink/?LinkId=201208)  
  
> [!CAUTION]
>  Klient, který má přístup k vlastní instance data v úložišti instancí má přístup do všech ostatních instancích ve stejném úložišti instancí. V úložišti instancí nepodporuje zadání oprávnění zabezpečení na úrovni instance. By měl vytvořit samostatnou instanci úložišť a mapovat různé skupiny/uživatele mít přístup do různých úložišť.
