---
title: "Pomocí vlastních aktivit"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8f356419-681a-4175-ae93-878eee970249
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: e534f9a3e8d0a7d675e43bc03266e4863f95d45d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="using-a-custom-activity"></a>Pomocí vlastních aktivit
Aktivity, které jsou odvozeny od <xref:System.Activities.Activity> nebo jeho podtřídy skládá do větší pracovních postupů, nebo přímo v kódu. Toto téma popisuje, jak chcete použít vlastní aktivity v pracovních postupech, které jsou vytvořené v kódu nebo v návrháři.  
  
> [!NOTE]
>  Můžete použít vlastní aktivity ve stejném projektu, ve kterém jsou definovány, tak dlouho, dokud vlastní aktivity a aktivity, která jej používá kompilované (tj. načíst konkretizujete typem vygenerovaných procesem sestavení) Pokud je zavedený odkazující aktivity dynamicky (např. pomocí ActivityXAMLServices), pak odkazované sestavení musí být umístěny v různých projektu nebo generované návrháře XAML, je potřeba, ručně upravovat, chcete-li povolit tuto funkci.  
  
#### <a name="using-a-custom-activity-to-a-workflow-project"></a>Pomocí vlastních aktivit do pracovního postupu projektu  
  
1.  Přidejte odkaz na projekt knihovny aktivit obsahující vlastní aktivity z projektu hostitele.  
  
2.  Sestavte řešení.  
  
3.  Pokud chcete použít vlastní aktivity v návrháři, vyhledejte vlastní aktivity v sadě nástrojů a přetáhněte aktivitu na plochu návrháře.  
  
4.  V kódu použít vlastní aktivity, přidat pomocí příkazu, který odkazuje na vlastní aktivity projektu a předejte novou instanci třídy na aktivitu, abyste <xref:System.Activities.WorkflowInvoker.Invoke%2A>.
