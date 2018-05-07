---
title: Zabezpečení
ms.date: 03/30/2017
ms.assetid: 737ec121-bfc5-4b75-a504-2d53c2c8af39
ms.openlocfilehash: b8fd870bcd14b8a80861914448f75fafe6af2863
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="security"></a>Zabezpečení
Ukládání Instance SQL pracovního postupu používá tyto role zabezpečení databáze zabezpečený přístup k informacím stavu instance v databázi trvalost.  
  
-   **System.Activities.DurableInstancing.InstanceStoreUsers**. Tato role má ke čtení a oprávnění k zápisu do veřejné zobrazení a provádění práva uložené procedury, které se podílejí vytváření, načítání a ukládání instancí.  
  
-   **System.Activities.DurableInstancing.InstanceStoreObservers**. Tato role má přístup jen pro čtení k veřejné zobrazení.  
  
-   **System.Activities.DurableInstancing.WorkflowActivationUsers**. Tato role má práva provádění uložené procedury, které jsou součástí procesu aktivace instance. Další informace o aktivaci instance najdete v tématu [Instance aktivace](../../../docs/framework/windows-workflow-foundation/instance-activation.md). Uživatelský účet, pod kterým obecné hostitele (například službu správy pracovního postupu [!INCLUDE[dublin](../../../includes/dublin-md.md)]) spustí musí být přidaní do této role databáze.  
  
 Další informace o zabezpečení pro trvalost úložiště s Windows Server App Fabric najdete v tématu [konfigurace zabezpečení pro úložiště trvalosti v App Fabric](http://go.microsoft.com/fwlink/?LinkId=201208)  
  
> [!CAUTION]
>  Klient, který má přístup k vlastní data instance v úložišti instance má přístup k další instance v úložišti stejné instanci. Instance úložiště nepodporuje zadání oprávnění zabezpečení na úrovni instance. Doporučujeme vytvořit samostatnou instanci úložiště a mapování různých skupin nebo uživatelů do mají přístup do různých úložišť.
