---
title: 'Postupy: Získání kolekce řádků z prvku TextBox'
ms.date: 03/30/2017
helpviewer_keywords:
- lines [WPF], getting collection of
- TextBox control [WPF], getting collection of lines
ms.assetid: a12f529d-b926-47f6-92bf-cad5f17b532a
ms.openlocfilehash: b7b2f1c2e071388635fb50b1e3573fd7f44334dd
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59224634"
---
# <a name="how-to-get-a-collection-of-lines-from-a-textbox"></a>Postupy: Získání kolekce řádků z prvku TextBox
Tento příklad ukazuje, jak získání kolekce řádků z textu <xref:System.Windows.Controls.TextBox>.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje jednoduchý způsob, který přijímá <xref:System.Windows.Controls.TextBox> jako argument a vrátí <xref:System.Collections.Specialized.StringCollection> obsahující řádky textu v **TextBox**.  <xref:System.Windows.Controls.TextBox.LineCount%2A> Vlastnost se používá k určení, kolik řádků se v tuto chvíli **textového pole**a <xref:System.Windows.Controls.TextBox.GetLineText%2A> metoda se pak použije k extrakci každého řádku a přidat ho do kolekce řádků.  
  
 [!code-csharp[TextBox_MiscCode#_TextBox_GetLines](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_textbox_getlines)]  
  
## <a name="see-also"></a>Viz také:

- [TextBox – přehled](textbox-overview.md)
- [RichTextBox – přehled](richtextbox-overview.md)
