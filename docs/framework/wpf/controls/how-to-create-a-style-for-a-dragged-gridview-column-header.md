---
title: "Postupy: Vytvoření stylu pro přetahované záhlaví sloupce GridView"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: ListView controls [WPF], styling
ms.assetid: 0b999645-0313-4b33-80b9-19ece08b5459
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 503683de875b8853e219139800eef2a5417a1574
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-style-for-a-dragged-gridview-column-header"></a>Postupy: Vytvoření stylu pro přetahované záhlaví sloupce GridView
Tento příklad ukazuje, jak změnit vzhled taženou <xref:System.Windows.Controls.GridViewColumnHeader> když uživatel změní pozici sloupce.  
  
## <a name="example"></a>Příklad  
 Když přetáhněte záhlaví sloupce na jiné místo v <xref:System.Windows.Controls.ListView> používající <xref:System.Windows.Controls.GridView> sloupec pro režim zobrazení, se přesune do nového umístění. Při přetahování na záhlaví sloupce, zobrazí se plovoucí kopie záhlaví kromě původní hlavičku. V záhlaví sloupce <xref:System.Windows.Controls.GridView> je reprezentována <xref:System.Windows.Controls.GridViewColumnHeader> objektu.  
  
 Chcete-li přizpůsobit vzhled plovoucí a původní hlavičky, můžete nastavit <xref:System.Windows.Controls.ControlTemplate.Triggers%2A> změnit <xref:System.Windows.Controls.GridViewColumnHeader> <xref:System.Windows.Style>. Tyto <xref:System.Windows.Controls.ControlTemplate.Triggers%2A> se použijí při <xref:System.Windows.Controls.Primitives.ButtonBase.IsPressed%2A> hodnota vlastnosti je `true` a <xref:System.Windows.Controls.GridViewColumnHeader.Role%2A> hodnota vlastnosti je <xref:System.Windows.Controls.GridViewColumnHeaderRole.Floating>.  
  
 Když uživatel tlačítka myši a obsahuje, zatímco myši pozastaví na <xref:System.Windows.Controls.GridViewColumnHeader>, <xref:System.Windows.Controls.Primitives.ButtonBase.IsPressed%2A> hodnotu vlastnosti změny `true`. Podobně když uživatel zahájí operaci přetažení <xref:System.Windows.Controls.GridViewColumnHeader.Role%2A> změny vlastností do <xref:System.Windows.Controls.GridViewColumnHeaderRole.Floating>.  
  
 Následující příklad ukazuje, jak nastavit <xref:System.Windows.Controls.ControlTemplate.Triggers%2A> změnit <xref:System.Windows.Controls.Control.Foreground%2A> a <xref:System.Windows.Controls.Control.Background%2A> barvy původní a plovoucí hlaviček, když uživatel nastavuje tažením sloupce do nového umístění.  
  
 [!code-xaml[ListViewHeaderRoleStyle#GVCHControlTemplateStart](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewHeaderRoleStyle/CS/Window1.xaml#gvchcontroltemplatestart)]  
[!code-xaml[ListViewHeaderRoleStyle#ControlTemplateTriggersStart](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewHeaderRoleStyle/CS/Window1.xaml#controltemplatetriggersstart)]  
[!code-xaml[ListViewHeaderRoleStyle#IsPressed](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewHeaderRoleStyle/CS/Window1.xaml#ispressed)]  
[!code-xaml[ListViewHeaderRoleStyle#Floating](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewHeaderRoleStyle/CS/Window1.xaml#floating)]  
[!code-xaml[ListViewHeaderRoleStyle#ControlTemplateTriggersEnd](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewHeaderRoleStyle/CS/Window1.xaml#controltemplatetriggersend)]  
[!code-xaml[ListViewHeaderRoleStyle#GVCHControlTemplateEnd](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewHeaderRoleStyle/CS/Window1.xaml#gvchcontroltemplateend)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Controls.GridViewColumnHeader>  
 <xref:System.Windows.Controls.GridViewColumnHeaderRole>  
 <xref:System.Windows.Controls.ListView>  
 <xref:System.Windows.Controls.GridView>  
 [Postupy: témata](../../../../docs/framework/wpf/controls/listview-how-to-topics.md)  
 [ListView – přehled](../../../../docs/framework/wpf/controls/listview-overview.md)  
 [Rutina GridView – přehled](../../../../docs/framework/wpf/controls/gridview-overview.md)
