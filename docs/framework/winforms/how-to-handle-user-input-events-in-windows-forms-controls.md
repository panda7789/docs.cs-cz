---
title: 'Postupy: Zpracování události uživatelského vstupu v ovládacích prvcích Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Windows Forms controls, user input
- user input [Windows Forms], Windows Forms controls
ms.assetid: 3de74dcf-fae3-42d0-92b5-bc04a61a6888
ms.openlocfilehash: e4fa03a07e97fe1d860b281b8e5cece0c41d6c27
ms.sourcegitcommit: 0069cb3de8eed4e92b2195d29e5769a76111acdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/16/2019
ms.locfileid: "56331958"
---
# <a name="how-to-handle-user-input-events-in-windows-forms-controls"></a>Postupy: Zpracování události uživatelského vstupu v ovládacích prvcích Windows Forms
Tento příklad ukazuje, jak zpracovat většinu klávesnice, myši, fokus a ověřovací události, které mohou nastat v ovládacím prvku Windows Forms. Textové pole s názvem `TextBoxInput` přijímá události, když má fokus, a informace o každé události je zapsaný do textového pole s názvem `TextBoxOutput` v pořadí, ve kterém jsou vyvolány události. Aplikace také obsahuje sadu políčka, která umožňuje filtrovat události do sestavy.  
  
## <a name="example"></a>Příklad  
 [!code-cpp[System.Windows.Forms.UserInputWalkthrough#0](../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.UserInputWalkthrough/cpp/form1.cpp#0)]
 [!code-csharp[System.Windows.Forms.UserInputWalkthrough#0](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.UserInputWalkthrough/CS/form1.cs#0)]
 [!code-vb[System.Windows.Forms.UserInputWalkthrough#0](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.UserInputWalkthrough/VB/form1.vb#0)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
-   Odkazy na sestavení systému, System.Drawing a System.Windows.Forms.  
  
 Informace o vytváření tento příklad z příkazového řádku pro Visual Basic nebo Visual C# najdete v tématu [sestavení z příkazového řádku](../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) nebo [sestavení pomocí příkazového řádku csc.exe](../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Tento příklad v sadě Visual Studio můžete také vytvořit vložením kódu do nového projektu.  
  
## <a name="see-also"></a>Viz také:
- [Uživatelský vstup ve Windows Forms](../../../docs/framework/winforms/user-input-in-windows-forms.md)
