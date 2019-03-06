---
title: 'Postupy: Vytvoření rozšíření pomocí prvku ScrollViewer'
ms.date: 03/30/2017
helpviewer_keywords:
- controls [WPF], Expander
- ScrollViewer control [WPF], with Expander control
- Expander control [WPF], creating
- controls [WPF], ScrollViewer
ms.assetid: 2ad124d2-2406-4157-aaf2-64e067298f01
ms.openlocfilehash: 9e7c023ec371dd6695ffba3368502e5b593c4608
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57369536"
---
# <a name="how-to-create-an-expander-with-a-scrollviewer"></a>Postupy: Vytvoření rozšíření pomocí prvku ScrollViewer
Tento příklad ukazuje, jak vytvořit <xref:System.Windows.Controls.Expander> ovládací prvek, který obsahuje komplexní obsah, jako je například image a text. V příkladu také vloží obsah <xref:System.Windows.Controls.Expander> v <xref:System.Windows.Controls.ScrollViewer> ovládacího prvku.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak vytvořit <xref:System.Windows.Controls.Expander>. V příkladu se používá <xref:System.Windows.Controls.Primitives.BulletDecorator> ovládací prvek, který obsahuje obrázek a text, aby bylo možné definovat <xref:System.Windows.Controls.HeaderedContentControl.Header%2A>. A <xref:System.Windows.Controls.ScrollViewer> ovládacího prvku poskytuje metodu pro posouvání rozšířené obsahu.  
  
 Všimněte si, že v příkladu je nastavena <xref:System.Windows.FrameworkElement.Height%2A> vlastnost <xref:System.Windows.Controls.ScrollViewer> místo na obsah. Pokud <xref:System.Windows.FrameworkElement.Height%2A> nastavená na obsah, <xref:System.Windows.Controls.ScrollViewer> neumožňuje uživateli, aby posouval obsah. <xref:System.Windows.FrameworkElement.Width%2A> Je nastavena na <xref:System.Windows.Controls.Expander> ovládacího prvku a toto nastavení platí pro <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> a rozšířené obsah.  
  
 [!code-xaml[ExpanderRichContent#CreateExpander](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpanderRichContent/CSharp/Window1.xaml#createexpander)]  
  
 [!code-csharp[ExpanderRichContent#CreateExpanderCode](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpanderRichContent/CSharp/Window1.xaml.cs#createexpandercode)]  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Windows.Controls.Expander>
- [Přehled rozšíření](expander-overview.md)
- [Témata s postupy](expander-how-to-topics.md)
