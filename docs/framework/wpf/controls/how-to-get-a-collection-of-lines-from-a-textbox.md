---
title: 'Postupy: Získání kolekce řádků z objektu TextBox'
ms.date: 03/30/2017
helpviewer_keywords:
- lines [WPF], getting collection of
- TextBox control [WPF], getting collection of lines
ms.assetid: a12f529d-b926-47f6-92bf-cad5f17b532a
ms.openlocfilehash: a63470c6f0db72340f482bf638910685aa3f461f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54561761"
---
# <a name="how-to-get-a-collection-of-lines-from-a-textbox"></a>Postupy: Získání kolekce řádků z objektu TextBox
Tento příklad ukazuje, jak získání kolekce řádků z textu <xref:System.Windows.Controls.TextBox>.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje jednoduchý způsob, který přijímá <xref:System.Windows.Controls.TextBox> jako argument a vrátí <xref:System.Collections.Specialized.StringCollection> obsahující řádky textu v **TextBox**.  <xref:System.Windows.Controls.TextBox.LineCount%2A> Vlastnost se používá k určení, kolik řádků se v tuto chvíli **textového pole**a <xref:System.Windows.Controls.TextBox.GetLineText%2A> metoda se pak použije k extrakci každého řádku a přidat ho do kolekce řádků.  
  
 [!code-csharp[TextBox_MiscCode#_TextBox_GetLines](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_textbox_getlines)]  
  
## <a name="see-also"></a>Viz také:
- [TextBox – přehled](../../../../docs/framework/wpf/controls/textbox-overview.md)
- [RichTextBox – přehled](../../../../docs/framework/wpf/controls/richtextbox-overview.md)
