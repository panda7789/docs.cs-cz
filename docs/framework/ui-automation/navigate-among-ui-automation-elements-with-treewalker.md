---
title: Pohyb mezi elementy automatizace uživatelského rozhraní pomocí třídy TreeWalker
description: Podívejte se na příklad kódu, který ukazuje, jak navigovat mezi prvky automatizace uživatelského rozhraní pomocí třídy třídy TreeWalker.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- classes, TreeWalker
- TreeWalker class
- elements, navigating among
- UI Automation, navigating among elements
ms.assetid: afcd21dc-2ffa-48c9-9332-51269f44b7e9
ms.openlocfilehash: e1784862433083f15d600ea2ec39aee2323bbd12
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2020
ms.locfileid: "87168020"
---
# <a name="navigate-among-ui-automation-elements-with-treewalker"></a>Pohyb mezi elementy automatizace uživatelského rozhraní pomocí třídy TreeWalker
> [!NOTE]
> Tato dokumentace je určena pro .NET Framework vývojářů, kteří chtějí používat spravované [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované v <xref:System.Windows.Automation> oboru názvů. Nejnovější informace o najdete [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] v tématu [rozhraní API služby Windows Automation: automatizace uživatelského rozhraní](/windows/win32/winauto/entry-uiauto-win32).  
  
 Toto téma obsahuje příklad kódu, který ukazuje, jak navigovat mezi [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] prvky pomocí <xref:System.Windows.Automation.TreeWalker> třídy.  
  
## <a name="example"></a>Příklad  
 Následující příklad používá <xref:System.Windows.Automation.TreeWalker.GetParent%2A> ke [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] stromové struktuře, dokud nenajde kořenový prvek nebo plochu. Prvek těsně pod, který je nadřazeným oknem zadaného elementu.  
  
 [!code-csharp[UIAFocusTracker_snip#102](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAFocusTracker_snip/CSharp/FocusTracker.cs#102)]
 [!code-vb[UIAFocusTracker_snip#102](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAFocusTracker_snip/VisualBasic/FocusTracker.vb#102)]  
  
## <a name="example"></a>Příklad  
 Následující příklad používá <xref:System.Windows.Automation.TreeWalker.GetFirstChild%2A> a <xref:System.Windows.Automation.TreeWalker.GetNextSibling%2A> k vytvoření <xref:System.Windows.Forms.TreeView> , který zobrazuje celý podstrom [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] prvků, které jsou v zobrazení ovládacího prvku a jsou povoleny.  
  
 [!code-csharp[UIAClient_snip#174](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#174)]
 [!code-vb[UIAClient_snip#174](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#174)]  
  
## <a name="see-also"></a>Viz také

- [Získání elementů automatizace uživatelského rozhraní](obtaining-ui-automation-elements.md)
