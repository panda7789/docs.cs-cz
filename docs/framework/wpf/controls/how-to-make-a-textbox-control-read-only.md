---
title: 'Postupy: Nastavení ovládacího prvku TextBox jen pro čtení'
ms.date: 03/30/2017
helpviewer_keywords:
- read-only TextBox controls [WPF]
- TextBox control read-only
ms.assetid: e707ec59-8b22-473e-b77c-3060a237517a
ms.openlocfilehash: 3784471020210f995c8bb0a377d56a2466d97da1
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57364524"
---
# <a name="how-to-make-a-textbox-control-read-only"></a>Postupy: Nastavení ovládacího prvku TextBox jen pro čtení
Tento příklad ukazuje, jak nakonfigurovat <xref:System.Windows.Controls.TextBox> ovládacího prvku na nepovoluje přidat nebo uživatelského vstupu.  
  
## <a name="example"></a>Příklad  
 Zabránit uživatelům v úpravách obsahu <xref:System.Windows.Controls.TextBox> , nastavte <xref:System.Windows.Controls.Primitives.TextBoxBase.IsReadOnly%2A> atribut **true**.  
  
 [!code-xaml[TextBox_MiscCode#_ReadOnlyTextBoxXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_readonlytextboxxaml)]  
  
 <xref:System.Windows.Controls.Primitives.TextBoxBase.IsReadOnly%2A> Atribut má vliv pouze na vstup uživatele; nemá vliv na nastavení v textu [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] popis <xref:System.Windows.Controls.TextBox> ovládací prvek nebo text nastavují programově pomocí <xref:System.Windows.Controls.TextBox.Text%2A> vlastnost.  
  
 Výchozí hodnota <xref:System.Windows.Controls.Primitives.TextBoxBase.IsReadOnly%2A> je **false**.  
  
## <a name="see-also"></a>Viz také:
- [TextBox – přehled](textbox-overview.md)
- [RichTextBox – přehled](richtextbox-overview.md)
