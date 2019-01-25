---
title: 'Postupy: Určení, kdy dojde k aktualizaci textu TextBox ve zdroji'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- source updates [WPF], timing of
- data binding [WPF], timing of source updates
- timing of source updates [WPF]
ms.assetid: ffb7b96a-351d-4c68-81e7-054033781c64
ms.openlocfilehash: e43f5c84a4e93e35f0d8350442870239408fdc7a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54690368"
---
# <a name="how-to-control-when-the-textbox-text-updates-the-source"></a>Postupy: Určení, kdy dojde k aktualizaci textu TextBox ve zdroji
Toto téma popisuje způsob použití <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> vlastností pro řízení časování aktualizací zdroje vazby. Téma používá <xref:System.Windows.Controls.TextBox> ovládací prvek jako příklad.  
  
## <a name="example"></a>Příklad  
 <xref:System.Windows.Controls.TextBox>.<xref:System.Windows.Controls.TextBox.Text%2A> Vlastnost má výchozí <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> hodnotu <xref:System.Windows.Data.UpdateSourceTrigger.LostFocus>. To znamená, že pokud má aplikace <xref:System.Windows.Controls.TextBox> s vázaný na data <xref:System.Windows.Controls.TextBox>.<xref:System.Windows.Controls.TextBox.Text%2A> vlastnost, text, který zadáte do <xref:System.Windows.Controls.TextBox> neaktualizuje zdroje do <xref:System.Windows.Controls.TextBox> ztratí fokus (například po kliknutí na klávesou <xref:System.Windows.Controls.TextBox>).  
  
 Pokud chcete zdroj, který má být aktualizována při psaní, nastavte <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> vazby ke <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>. V následujícím příkladu zvýrazněné řádky kódu ukazují, že `Text` vlastnosti obou <xref:System.Windows.Controls.TextBox> a <xref:System.Windows.Controls.TextBlock> je vázána na stejnou vlastnost source. <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> Vlastnost <xref:System.Windows.Controls.TextBox> vazby je nastavena na <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>.  
  
 [!code-xaml[SimpleBinding#USTHowTo](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleBinding/VisualBasic/Page1.xaml?highlight=33-39,41-42)]  
  
 V důsledku toho <xref:System.Windows.Controls.TextBlock> zobrazí stejný text (protože mění se zdroj), protože uživatel zadá text do <xref:System.Windows.Controls.TextBox>, jak je znázorněno v následujícím snímku obrazovky ukázky:  
  
 ![Snímek obrazovky pro ukázka jednoduché datové vazby](../../../../docs/framework/wpf/data/media/databindingsimplebindingsample2.png "DataBindingSimpleBindingSample2")  
  
 Pokud máte dialogové okno nebo upravovat uživatele formuláře a chcete odložit zdroj aktualizace, dokud uživatel je dokončení úprav pole a klikne na tlačítko "OK", můžete nastavit <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> hodnotu vazby na <xref:System.Windows.Data.UpdateSourceTrigger.Explicit>, jako v následujícím příkladu:  
  
 [!code-xaml[UpdateSource#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/UpdateSource/CSharp/Window1.xaml#2)]  
  
 Při nastavení <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> hodnota, která se <xref:System.Windows.Data.UpdateSourceTrigger.Explicit>, zdrojová hodnota změní jenom v případě aplikace volá <xref:System.Windows.Data.BindingExpression.UpdateSource%2A> metody. Následující příklad ukazuje, jak volat <xref:System.Windows.Data.BindingExpression.UpdateSource%2A> pro `itemNameTextBox`:  
  
 [!code-csharp[UpdateSource#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/UpdateSource/CSharp/Window1.xaml.cs#1)]
 [!code-vb[UpdateSource#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UpdateSource/VisualBasic/Window1.xaml.vb#1)]  
  
> [!NOTE]
>  Můžete použít stejný postup pro vlastnosti jiných ovládacích prvků, ale mějte na paměti, že většinu dalších vlastností mají výchozí <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> hodnotu <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>. Další informace najdete v tématu <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> stránku vlastností.  
  
> [!NOTE]
>  <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> Vlastnost se zabývá aktualizací zdroje a proto je platné pouze pro <xref:System.Windows.Data.BindingMode.TwoWay> nebo <xref:System.Windows.Data.BindingMode.OneWayToSource> vazby. Pro <xref:System.Windows.Data.BindingMode.TwoWay> a <xref:System.Windows.Data.BindingMode.OneWayToSource> vazby pro práci, musí objekt zdroje k poskytování oznámení změn vlastností. Mohou odkazovat na vzorcích, uvedeným v tomto tématu pro další informace. Kromě toho se můžete podívat na [implementace oznámení změn vlastností](../../../../docs/framework/wpf/data/how-to-implement-property-change-notification.md).  
  
## <a name="see-also"></a>Viz také:
- [Témata s postupy](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
