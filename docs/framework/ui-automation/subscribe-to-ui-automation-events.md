---
title: Přihlášení k odběru událostí automatizace uživatelského rozhraní
description: Podívejte se, jak se přihlásit k odběru událostí vyvolaných zprostředkovateli automatizace uživatelského rozhraní. Vzorový kód Registruje obslužnou rutinu události pro událost vyvolanou při vyvolání ovládacího prvku.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- UI Automation, subscribing to events
- subscribing to UI Automation events
- events, subscribing to
- listening for events
ms.assetid: b688effa-b3e8-4b05-944d-05ed89a245aa
ms.openlocfilehash: 8f456702657c70837c6137e3e60335110361bcd9
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2020
ms.locfileid: "87163530"
---
# <a name="subscribe-to-ui-automation-events"></a>Přihlášení k odběru událostí automatizace uživatelského rozhraní
> [!NOTE]
> Tato dokumentace je určena pro .NET Framework vývojářů, kteří chtějí používat spravované [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované v <xref:System.Windows.Automation> oboru názvů. Nejnovější informace o najdete [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] v tématu [rozhraní API služby Windows Automation: automatizace uživatelského rozhraní](/windows/win32/winauto/entry-uiauto-win32).  
  
 Toto téma ukazuje, jak se přihlásit k odběru událostí vyvolaných zprostředkovateli automatizace uživatelského rozhraní.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu zaregistruje obslužnou rutinu události pro událost, která je vyvolána při vyvolání ovládacího prvku, jako je například tlačítko, a odstraní jej při zavření formuláře aplikace. Událost je identifikována <xref:System.Windows.Automation.AutomationEvent> předaným jako parametr do <xref:System.Windows.Automation.Automation.AddAutomationEventHandler%2A> .  
  
 [!code-csharp[UIAClient_snip#101](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#101)]
 [!code-vb[UIAClient_snip#101](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#101)]  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak použít [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] k přihlášení k odběru události, která je vyvolána při změně fokusu. Obslužná rutina události je odregistrována v metodě, která by mohla být volána při vypnutí aplikace, nebo v případě, že již není vyžadováno oznámení událostí uživatelského rozhraní.  
  
 [!code-csharp[UIAClient_snip#102](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#102)]
 [!code-vb[UIAClient_snip#102](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#102)]  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Automation.Automation.AddAutomationEventHandler%2A>
- <xref:System.Windows.Automation.Automation.RemoveAllEventHandlers%2A>
- <xref:System.Windows.Automation.Automation.RemoveAutomationEventHandler%2A>
- [Přehled událostí automatizace uživatelského rozhraní](ui-automation-events-overview.md)
