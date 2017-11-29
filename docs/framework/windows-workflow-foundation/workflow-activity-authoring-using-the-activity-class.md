---
title: "Vytváření aktivit pracovního postupu pomocí třídy aktivity"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7b7b1c66-f093-43c3-b4d1-7173b46516da
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: f4fc6d0807c07952e9b3abe2861ef04bc225142f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="workflow-activity-authoring-using-the-activity-class"></a>Vytváření aktivit pracovního postupu pomocí třídy aktivity
Nejzákladnější způsob, jak vytvořit, aktivity pomocí [!INCLUDE[wf](../../../includes/wf-md.md)] v [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] je vytvořte třídu, která dědí z <xref:System.Activities.Activity> vytvářející funkce sestavte vlastní aktivity nebo aktivity z [předdefinované knihovna aktivit ](../../../docs/framework/windows-workflow-foundation/net-framework-4-5-built-in-activity-library.md). Toto téma ukazuje, jak vytvořit aktivitu, která zapisuje dvě zprávy do konzoly.  
  
### <a name="to-create-a-custom-activity-using-the-activity-designer"></a>Chcete-li vytvořit vlastní aktivity pomocí Návrhář aktivity  
  
1.  Otevřete [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)].  
  
2.  Vyberte soubor, nový, projektu. Vyberte **Workflow 4.0** pod **Visual C#** v **typy projektů** a vyberte **v2010** uzlu. Vyberte **knihovna aktivit** v **šablony** okno. Název nového projektu HelloActivity.  
  
3.  Otevřete novou aktivitu.  Přetáhněte <xref:System.Activities.Statements.Sequence> aktivity z panelu nástrojů na plochu návrháře.  
  
4.  Přetáhněte <xref:System.Activities.Statements.WriteLine> aktivity do <xref:System.Activities.Statements.Sequence> aktivity. Zadejte `"Hello World"` (s uvozovky) do **Text** pole.  
  
5.  Přetáhněte druhý <xref:System.Activities.Statements.WriteLine> aktivity do <xref:System.Activities.Statements.Sequence> aktivity pod první z nich. Zadejte `"Goodbye"` (s uvozovky) do **Text** pole.
