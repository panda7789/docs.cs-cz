---
title: "Postupy: Určení, kdy dojde k aktualizaci textu TextBox ve zdroji"
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
- source updates [WPF], timing of
- data binding [WPF], timing of source updates
- timing of source updates [WPF]
ms.assetid: ffb7b96a-351d-4c68-81e7-054033781c64
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9c503eb3300aba4a44c5a013c62942e7a171ae96
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-control-when-the-textbox-text-updates-the-source"></a>Postupy: Určení, kdy dojde k aktualizaci textu TextBox ve zdroji
Toto téma popisuje postup použití <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> vlastnost řídit načasování vazby zdroj aktualizací. Používá tématu <xref:System.Windows.Controls.TextBox> ovládací prvek jako příklad.  
  
## <a name="example"></a>Příklad  
 <xref:System.Windows.Controls.TextBox>.<xref:System.Windows.Controls.TextBox.Text%2A> Vlastnost má výchozí <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> hodnotu <xref:System.Windows.Data.UpdateSourceTrigger.LostFocus>. To znamená, že pokud má aplikace <xref:System.Windows.Controls.TextBox> s daty připojeného <xref:System.Windows.Controls.TextBox>.<xref:System.Windows.Controls.TextBox.Text%2A> vlastnost, kterou zadáte do text <xref:System.Windows.Controls.TextBox> neaktualizuje zdroji až <xref:System.Windows.Controls.TextBox> ztratí fokus (například když kliknete na tlačítko mimo <xref:System.Windows.Controls.TextBox>).  
  
 Pokud chcete, aby zdroj k získání aktualizovat, protože při psaní, nastavte <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> vazby ke <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>. V následujícím příkladu `Text` vlastnosti obou <xref:System.Windows.Controls.TextBox> a <xref:System.Windows.Controls.TextBlock> je vázána na stejnou vlastnost zdroje. <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> Vlastnost <xref:System.Windows.Controls.TextBox> vazba je nastaven na <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>.  
  
 [!code-xaml[SimpleBinding#USTHowTo](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleBinding/VisualBasic/Page1.xaml#usthowto)]  
  
 V důsledku toho <xref:System.Windows.Controls.TextBlock> ukazuje stejný text (protože zdroji změní) jako uživatel zadá text do <xref:System.Windows.Controls.TextBox>, jak vidíte na následujícím snímku obrazovky vzorku:  
  
 ![Jednoduché datové vazby – snímek obrazovky](../../../../docs/framework/wpf/data/media/databindingsimplebindingsample2.png "DataBindingSimpleBindingSample2")  
  
 Pokud máte, zobrazí se dialogové okno nebo uživatel upravovat formulář a chcete odložení aktualizací zdroj, dokud se uživatel je dokončení úprav pole a klikne na tlačítko "OK", můžete nastavit <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> hodnotu vaší vazby na <xref:System.Windows.Data.UpdateSourceTrigger.Explicit>, jako v následujícím příkladu:  
  
 [!code-xaml[UpdateSource#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/UpdateSource/CSharp/Window1.xaml#2)]  
  
 Když nastavíte <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> hodnotu <xref:System.Windows.Data.UpdateSourceTrigger.Explicit>, zdrojové hodnoty změní jenom v případě aplikace volá <xref:System.Windows.Data.BindingExpression.UpdateSource%2A> metoda. Následující příklad ukazuje způsob volání <xref:System.Windows.Data.BindingExpression.UpdateSource%2A> pro `itemNameTextBox`:  
  
 [!code-csharp[UpdateSource#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/UpdateSource/CSharp/Window1.xaml.cs#1)]
 [!code-vb[UpdateSource#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UpdateSource/VisualBasic/Window1.xaml.vb#1)]  
  
> [!NOTE]
>  Stejný postup použijte pro vlastnosti jiných ovládacích prvků, ale mějte na paměti, že většina ostatní vlastnosti mají výchozí <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> hodnotu <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>. Další informace najdete v tématu <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> stránku vlastností.  
  
> [!NOTE]
>  <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> Vlastnost zdroje aktualizace se zabývá a proto je platné pouze pro <xref:System.Windows.Data.BindingMode.TwoWay> nebo <xref:System.Windows.Data.BindingMode.OneWayToSource> vazby. Pro <xref:System.Windows.Data.BindingMode.TwoWay> a <xref:System.Windows.Data.BindingMode.OneWayToSource> vazby pracovat, je nutné objekt zdroje poskytují oznámení o změnách vlastnost. Najdete ukázky citovalo v tomto tématu pro další informace. Kromě toho můžete se podívat na [oznámení o změně vlastnost implementace](../../../../docs/framework/wpf/data/how-to-implement-property-change-notification.md).  
  
## <a name="see-also"></a>Viz také  
 [Témata s postupy](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
