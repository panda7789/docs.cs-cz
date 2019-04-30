---
title: 'Postupy: Kontrola viditelnosti objektu GridSplitter'
ms.date: 03/30/2017
helpviewer_keywords:
- GridSplitter control [WPF], ensuring visibility of
ms.assetid: 0a62a964-89c8-48f0-9023-5df721a8cf47
ms.openlocfilehash: b7543d14ba39d854b5a2c3f4d0d19b9a457ea89b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61770848"
---
# <a name="how-to-make-sure-that-a-gridsplitter-is-visible"></a>Postupy: Kontrola viditelnosti objektu GridSplitter
Tento příklad ukazuje, jak Ujistěte se, že <xref:System.Windows.Controls.GridSplitter> jiné ovládací prvky v není skrytý ovládací prvek <xref:System.Windows.Controls.Grid>.  
  
## <a name="example"></a>Příklad  
 <xref:System.Windows.Controls.Panel.Children%2A> z <xref:System.Windows.Controls.Grid> ovládací prvek se zobrazují v pořadí, že jsou definovány v značek nebo kódu. <xref:System.Windows.Controls.GridSplitter> ovládací prvky lze skrýt ovládací prvky, pokud není definován jako poslední prvky v <xref:System.Windows.Controls.Panel.Children%2A> kolekce nebo pokud poskytnete další ovládací prvky a vyšší <xref:System.Windows.Controls.Panel.ZIndexProperty>.  
  
 Aby se zabránilo skryté <xref:System.Windows.Controls.GridSplitter> ovládací prvky, proveďte jednu z následujících akcí.  
  
- Ujistěte se, že <xref:System.Windows.Controls.GridSplitter> ovládací prvky jsou poslední <xref:System.Windows.Controls.Panel.Children%2A> přidán do <xref:System.Windows.Controls.Grid>. Následující příklad ukazuje <xref:System.Windows.Controls.GridSplitter> jako po posledním prvku v <xref:System.Windows.Controls.Panel.Children%2A> kolekce <xref:System.Windows.Controls.Grid>.  
  
 [!code-xaml[GridSplitterSnips#GridSplitterLastChild](~/samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterSnips/CSharp/Window1.xaml#gridsplitterlastchild)]  
  
- Nastavte <xref:System.Windows.Controls.Panel.ZIndexProperty> na <xref:System.Windows.Controls.GridSplitter> vyšší než ovládací prvek, který by jinak skrýt. Následující příklad dává <xref:System.Windows.Controls.GridSplitter> řídit vyšší <xref:System.Windows.Controls.Panel.ZIndexProperty> než <xref:System.Windows.Controls.Button> ovládacího prvku.  
  
 [!code-xaml[GridSplitterSnips#GridSplitterZIndex](~/samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterSnips/CSharp/Window1.xaml#gridsplitterzindex)]  
  
- Nastavit okraje ovládacího prvku, který by jinak skrýt <xref:System.Windows.Controls.GridSplitter> tak, aby <xref:System.Windows.Controls.GridSplitter> je přístupný. Následující příklad nastaví na ovládací prvek, který by jinak překrytí a skrýt okraje <xref:System.Windows.Controls.GridSplitter>.  
  
 [!code-xaml[GridSplitterSnips#GridSplitterMargin](~/samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterSnips/CSharp/Window1.xaml#gridsplittermargin)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Controls.GridSplitter>
- [Témata s postupy](gridsplitter-how-to-topics.md)
