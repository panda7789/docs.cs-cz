---
title: 'Postupy: Vytvoření stylu pro přetahované záhlaví sloupce GridView'
ms.date: 03/30/2017
helpviewer_keywords:
- ListView controls [WPF], styling
ms.assetid: 0b999645-0313-4b33-80b9-19ece08b5459
ms.openlocfilehash: dd347781451c9e574fed97c1a553c25bda1b8d7a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54545394"
---
# <a name="how-to-create-a-style-for-a-dragged-gridview-column-header"></a>Postupy: Vytvoření stylu pro přetahované záhlaví sloupce GridView
Tento příklad ukazuje, jak změnit vzhled Přetahované <xref:System.Windows.Controls.GridViewColumnHeader> když uživatel změní pozici sloupce.  
  
## <a name="example"></a>Příklad  
 Při přetažení záhlaví sloupce do jiného umístění v <xref:System.Windows.Controls.ListView> , která používá <xref:System.Windows.Controls.GridView> sloupec pro režim zobrazení, se přesune do nového umístění. Při přetahování na záhlaví sloupce, se zobrazí kromě originální kopii záhlaví s plovoucí desetinnou čárkou. V záhlaví sloupce <xref:System.Windows.Controls.GridView> je reprezentována <xref:System.Windows.Controls.GridViewColumnHeader> objektu.  
  
 Chcete-li přizpůsobit vzhled s plovoucí desetinnou čárkou a původní záhlaví, můžete nastavit <xref:System.Windows.Controls.ControlTemplate.Triggers%2A> upravit <xref:System.Windows.Controls.GridViewColumnHeader> <xref:System.Windows.Style>. Tyto <xref:System.Windows.Controls.ControlTemplate.Triggers%2A> se použije, když <xref:System.Windows.Controls.Primitives.ButtonBase.IsPressed%2A> hodnota vlastnosti je `true` a <xref:System.Windows.Controls.GridViewColumnHeader.Role%2A> hodnota vlastnosti je <xref:System.Windows.Controls.GridViewColumnHeaderRole.Floating>.  
  
 Když uživatel stiskne tlačítko myši a obsahuje při pozastavení ukazatele myši na <xref:System.Windows.Controls.GridViewColumnHeader>, <xref:System.Windows.Controls.Primitives.ButtonBase.IsPressed%2A> změní hodnota vlastnosti `true`. Podobně, když uživatel začne operace přetažení <xref:System.Windows.Controls.GridViewColumnHeader.Role%2A> vlastnost se změní na <xref:System.Windows.Controls.GridViewColumnHeaderRole.Floating>.  
  
 Následující příklad ukazuje, jak nastavit <xref:System.Windows.Controls.ControlTemplate.Triggers%2A> změnit <xref:System.Windows.Controls.Control.Foreground%2A> a <xref:System.Windows.Controls.Control.Background%2A> barvy s plovoucí desetinnou čárkou a původní záhlaví, když uživatel přetáhne sloupce do nového umístění.  
  
 [!code-xaml[ListViewHeaderRoleStyle#GVCHControlTemplateStart](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewHeaderRoleStyle/CS/Window1.xaml#gvchcontroltemplatestart)]  
[!code-xaml[ListViewHeaderRoleStyle#ControlTemplateTriggersStart](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewHeaderRoleStyle/CS/Window1.xaml#controltemplatetriggersstart)]  
[!code-xaml[ListViewHeaderRoleStyle#IsPressed](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewHeaderRoleStyle/CS/Window1.xaml#ispressed)]  
[!code-xaml[ListViewHeaderRoleStyle#Floating](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewHeaderRoleStyle/CS/Window1.xaml#floating)]  
[!code-xaml[ListViewHeaderRoleStyle#ControlTemplateTriggersEnd](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewHeaderRoleStyle/CS/Window1.xaml#controltemplatetriggersend)]  
[!code-xaml[ListViewHeaderRoleStyle#GVCHControlTemplateEnd](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewHeaderRoleStyle/CS/Window1.xaml#gvchcontroltemplateend)]  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Windows.Controls.GridViewColumnHeader>
- <xref:System.Windows.Controls.GridViewColumnHeaderRole>
- <xref:System.Windows.Controls.ListView>
- <xref:System.Windows.Controls.GridView>
- [Témata s postupy](../../../../docs/framework/wpf/controls/listview-how-to-topics.md)
- [ListView – přehled](../../../../docs/framework/wpf/controls/listview-overview.md)
- [GridView – přehled](../../../../docs/framework/wpf/controls/gridview-overview.md)
