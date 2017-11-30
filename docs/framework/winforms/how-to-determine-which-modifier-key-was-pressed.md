---
title: "Postupy: Určení modifikační klávesy, která byla stisknuta"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- keyboard input
- shift keys
- events [Windows Forms], mouse
- Keys.ControlKey enumeration member
- keys [Windows Forms], control keys
- user input [Windows Forms], checking for keyboard
- keys [Windows Forms], determining last pressed
- keys [Windows Forms], shift keys
- keys [Windows Forms], modifier keys
- control keys
- keys [Windows Forms], alt keys
- alt keys
- Keys.Shift enumeration member
- events [Windows Forms], keyboard
- keyboards [Windows Forms], keyboard input
- Keys.Alt enumeration member
- modifier keys
ms.assetid: 1e184048-0ae3-4067-a200-d4ba31dbc2cb
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 6fdc93063bbc8c9428f2f01c6cd5c0578e77ab01
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-determine-which-modifier-key-was-pressed"></a>Postupy: Určení modifikační klávesy, která byla stisknuta
Když vytvoříte aplikaci, která podporuje stisknutí kláves uživatele, můžete také monitorovat modifikační klávesy třeba klávesy SHIFT, ALT a CTRL. Při stisknutí modifikační klávesy v kombinaci s jiných klíčů nebo kliknutími myši, vaše aplikace může reagovat správně. Například pokud stisknutí písmeno S to může způsobit jednoduše "s" zobrazí na obrazovce, ale pokud stisknutí kláves CTRL + S, mohou být uloženy aktuálním dokumentu. Pokud zpracováváte <xref:System.Windows.Forms.Control.KeyDown> událostí, <xref:System.Windows.Forms.KeyEventArgs.Modifiers%2A> vlastnost <xref:System.Windows.Forms.KeyEventArgs> obdržel událost obslužné rutiny Určuje, které modifikační klávesy stisknutí. Případně <xref:System.Windows.Forms.KeyEventArgs.KeyData%2A> vlastnost <xref:System.Windows.Forms.KeyEventArgs> Určuje znak, která byla stisknuta stejně jako jakýkoli modifikační klávesy v kombinaci s bitové operace OR. Ale pokud jsou zpracování <xref:System.Windows.Forms.Control.KeyPress> událostí nebo myš událost, obslužné rutiny události neobdrží tyto informace. V takovém případě musíte použít <xref:System.Windows.Forms.Control.ModifierKeys%2A> vlastnost <xref:System.Windows.Forms.Control> třídy. V obou případech je třeba provést bitové operace AND příslušné <xref:System.Windows.Forms.Keys> hodnota a hodnota testování. <xref:System.Windows.Forms.Keys> Výčtu nabízí variace každý modifikační klávesy, proto je důležité provést bitové hodnotě a s správnou hodnotu. Například je reprezentována klávesu SHIFT <xref:System.Windows.Forms.Keys.Shift>, <xref:System.Windows.Forms.Keys.ShiftKey>, <xref:System.Windows.Forms.Keys.RShiftKey> a <xref:System.Windows.Forms.Keys.LShiftKey> správnou hodnotu pro testovací SHIFT, jako je modifikační klávesy <xref:System.Windows.Forms.Keys.Shift>. Podobně testování pro řadič a ALT jako modifikátory můžete využít <xref:System.Windows.Forms.Keys.Control> a <xref:System.Windows.Forms.Keys.Alt> hodnoty v uvedeném pořadí.  
  
> [!NOTE]
>  Programátory v jazyce Visual Basic je přístupný také informace o klíči prostřednictvím <xref:Microsoft.VisualBasic.Devices.Computer.Keyboard%2A> vlastnost  
  
### <a name="to-determine-which-modifier-key-was-pressed"></a>K určení modifikační klávesy, která byla stisknuta  
  
-   Použít bitové hodnotě `AND` operátor s <xref:System.Windows.Forms.Control.ModifierKeys%2A> vlastnosti a hodnotu <xref:System.Windows.Forms.Keys> výčtu k určení, zda stisknutí konkrétní modifikační klávesy. Následující příklad kódu ukazuje, jak určit, zda je v rámci stisknutí klávesy SHIFT <xref:System.Windows.Forms.Control.KeyPress> obslužné rutiny události.  
  
     [!code-cpp[System.Windows.Forms.DetermineModifierKey#5](../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DetermineModifierKey/cpp/form1.cpp#5)]
     [!code-csharp[System.Windows.Forms.DetermineModifierKey#5](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DetermineModifierKey/CS/form1.cs#5)]
     [!code-vb[System.Windows.Forms.DetermineModifierKey#5](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DetermineModifierKey/VB/form1.vb#5)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.Keys>  
 <xref:System.Windows.Forms.Control.ModifierKeys%2A>  
 [Vstup z klávesnice ve Windows Forms aplikace](../../../docs/framework/winforms/keyboard-input-in-a-windows-forms-application.md)  
 [Postupy: určí, zda CapsLock – na v jazyce Visual Basic](http://msdn.microsoft.com/en-us/91e60f5c-dd61-4222-ba5f-39af803afd8c)
