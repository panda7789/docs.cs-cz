---
title: 'Postupy: Získání kolekce řádků z objektu TextBox'
ms.date: 03/30/2017
helpviewer_keywords:
- lines [WPF], getting collection of
- TextBox control [WPF], getting collection of lines
ms.assetid: a12f529d-b926-47f6-92bf-cad5f17b532a
ms.openlocfilehash: 64187527da3cfb97343e2036338822d479dd997a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33552737"
---
# <a name="how-to-get-a-collection-of-lines-from-a-textbox"></a>Postupy: Získání kolekce řádků z objektu TextBox
Tento příklad ukazuje, jak získat kolekce řádků textu z <xref:System.Windows.Controls.TextBox>.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje jednoduchý metody, která přijímá <xref:System.Windows.Controls.TextBox> jako argument a vrátí <xref:System.Collections.Specialized.StringCollection> obsahující řádků textu v **TextBox**.  <xref:System.Windows.Controls.TextBox.LineCount%2A> Vlastnost se používá k určení, kolik řádků se právě **TextBox**a <xref:System.Windows.Controls.TextBox.GetLineText%2A> metoda se pak používá k extrahování každého řádku a přidat jej do kolekce řádků.  
  
 [!code-csharp[TextBox_MiscCode#_TextBox_GetLines](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_textbox_getlines)]  
  
## <a name="see-also"></a>Viz také  
 [TextBox – přehled](../../../../docs/framework/wpf/controls/textbox-overview.md)  
 [RichTextBox – přehled](../../../../docs/framework/wpf/controls/richtextbox-overview.md)
