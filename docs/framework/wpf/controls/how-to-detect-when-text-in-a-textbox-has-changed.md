---
title: "Postupy: Zjištění, kdy došlo ke změně textu v prvku TextBox"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- TextBox control [WPF], detecting text change
- text change [WPF], detecting
- detecting text change [WPF]
ms.assetid: 1c39ee14-e37f-49fb-a0d1-a9824ca13584
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2ef1da879026d8cbefd6ef1baeb6c315e0ea1c02
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-detect-when-text-in-a-textbox-has-changed"></a>Postupy: Zjištění, kdy došlo ke změně textu v prvku TextBox
Tento příklad ukazuje jeden ze způsobů použití <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> události spuštění metody vždy, když text v <xref:System.Windows.Controls.TextBox> došlo ke změně ovládacího prvku.  
  
 Ve třídě kódu pro [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] obsahující <xref:System.Windows.Controls.TextBox> vložit ovládací prvek, který chcete monitorovat změny, metoda k volání vždy, když <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> je aktivována událost.  Tato metoda musí mít podpis, který odpovídá očekávané pomocí <xref:System.Windows.Controls.TextChangedEventHandler> delegovat.  
  
 Je volána obslužná rutina události vždy, když obsah <xref:System.Windows.Controls.TextBox> řízení se změní, uživatelem nebo prostřednictvím kódu programu.  
  
 **Poznámka:** Tato událost aktivuje, když <xref:System.Windows.Controls.TextBox> řízení se vytvoří a zpočátku zobrazí s textem.  
  
## <a name="example"></a>Příklad  
 V [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] , který definuje váš <xref:System.Windows.Controls.TextBox> řídit, zadejte <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> atributu s hodnotou, která odpovídá názvu metoda obslužná rutina události.  
  
 [!code-xaml[TextBox_MiscCode#_TextChangedXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_textchangedxaml)]  
  
## <a name="example"></a>Příklad  
 Ve třídě kódu pro [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] obsahující <xref:System.Windows.Controls.TextBox> vložit ovládací prvek, který chcete monitorovat změny, metoda k volání vždy, když <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> je aktivována událost.  Tato metoda musí mít podpis, který odpovídá očekávané pomocí <xref:System.Windows.Controls.TextChangedEventHandler> delegovat.  
  
 [!code-csharp[TextBox_MiscCode#_TextChangedEventHandler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_textchangedeventhandler)]
 [!code-vb[TextBox_MiscCode#_TextChangedEventHandler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_MiscCode/VisualBasic/Window1.xaml.vb#_textchangedeventhandler)]  
  
 Je volána obslužná rutina události vždy, když obsah <xref:System.Windows.Controls.TextBox> řízení se změní, uživatelem nebo prostřednictvím kódu programu.  
  
 **Poznámka:** Tato událost aktivuje, když <xref:System.Windows.Controls.TextBox> řízení se vytvoří a zpočátku zobrazí s textem.  
  
 Komentáře  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Controls.TextChangedEventArgs>  
 [TextBox – přehled](../../../../docs/framework/wpf/controls/textbox-overview.md)  
 [RichTextBox – přehled](../../../../docs/framework/wpf/controls/richtextbox-overview.md)
