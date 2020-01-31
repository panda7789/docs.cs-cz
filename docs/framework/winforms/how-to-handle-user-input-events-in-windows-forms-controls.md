---
title: Zpracování událostí vstupu uživatele v ovládacích prvcích
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Windows Forms controls, user input
- user input [Windows Forms], Windows Forms controls
ms.assetid: 3de74dcf-fae3-42d0-92b5-bc04a61a6888
ms.openlocfilehash: 19adeb6c803c76cba4139841f58087487d523a50
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76739419"
---
# <a name="how-to-handle-user-input-events-in-windows-forms-controls"></a>Postupy: Obsluha událostí uživatelského vstupu v ovládacích prvcích Windows Forms
Tento příklad ukazuje, jak zpracovat většinu událostí klávesnice, myši, fokusu a ověřování, které mohou nastat v ovládacím prvku model Windows Forms. Textové pole s názvem `TextBoxInput` přijímá události, když má fokus, a informace o každé události jsou zapsány do textového pole s názvem `TextBoxOutput` v pořadí, ve kterém jsou události vyvolány. Aplikace taky obsahuje sadu zaškrtávacích políček, která se dají použít k filtrování událostí, které se mají ohlásit.  
  
## <a name="example"></a>Příklad  
 [!code-cpp[System.Windows.Forms.UserInputWalkthrough#0](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.UserInputWalkthrough/cpp/form1.cpp#0)]
 [!code-csharp[System.Windows.Forms.UserInputWalkthrough#0](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.UserInputWalkthrough/CS/form1.cs#0)]
 [!code-vb[System.Windows.Forms.UserInputWalkthrough#0](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.UserInputWalkthrough/VB/form1.vb#0)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
- Odkazy na sestavení System, System. Drawing a System. Windows. Forms.  
  
## <a name="see-also"></a>Viz také:

- [Uživatelský vstup ve Windows Forms](user-input-in-windows-forms.md)
