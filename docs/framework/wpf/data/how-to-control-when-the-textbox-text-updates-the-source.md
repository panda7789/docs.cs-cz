---
title: 'Postupy: Určení, kdy dojde k aktualizaci zdroje textem TextBox'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- source updates [WPF], timing of
- data binding [WPF], timing of source updates
- timing of source updates [WPF]
ms.assetid: ffb7b96a-351d-4c68-81e7-054033781c64
ms.openlocfilehash: 5272a19f69b3caf80fd7d5187c9a6a386cd44621
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62051998"
---
# <a name="how-to-control-when-the-textbox-text-updates-the-source"></a>Postupy: Určení, kdy dojde k aktualizaci zdroje textem TextBox
Toto téma popisuje způsob použití <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> vlastností pro řízení časování aktualizací zdroje vazby. Téma používá <xref:System.Windows.Controls.TextBox> ovládací prvek jako příklad.  
  
## <a name="example"></a>Příklad  
 <xref:System.Windows.Controls.TextBox>.<xref:System.Windows.Controls.TextBox.Text%2A> Vlastnost má výchozí <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> hodnotu <xref:System.Windows.Data.UpdateSourceTrigger.LostFocus>. To znamená, že pokud má aplikace <xref:System.Windows.Controls.TextBox> s vázaný na data <xref:System.Windows.Controls.TextBox>.<xref:System.Windows.Controls.TextBox.Text%2A> vlastnost, text, který zadáte do <xref:System.Windows.Controls.TextBox> neaktualizuje zdroje do <xref:System.Windows.Controls.TextBox> ztratí fokus (například po kliknutí na klávesou <xref:System.Windows.Controls.TextBox>).  
  
 Pokud chcete zdroj, který má být aktualizována při psaní, nastavte <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> vazby ke <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>. V následujícím příkladu zvýrazněné řádky kódu ukazují, že `Text` vlastnosti obou <xref:System.Windows.Controls.TextBox> a <xref:System.Windows.Controls.TextBlock> je vázána na stejnou vlastnost source. <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> Vlastnost <xref:System.Windows.Controls.TextBox> vazby je nastavena na <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>.  
  
 [!code-xaml[SimpleBinding#USTHowTo](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleBinding/VisualBasic/Page1.xaml?highlight=33-39,41-42)]  
  
 V důsledku toho <xref:System.Windows.Controls.TextBlock> zobrazí stejný text (protože mění se zdroj), protože uživatel zadá text do <xref:System.Windows.Controls.TextBox>, jak je znázorněno v následujícím snímku obrazovky ukázky:  
  
 ![Snímek obrazovky ukázkové jednoduchou datovou vazbu](./media/databindingsimplebindingsample2.png "DataBindingSimpleBindingSample2")  
  
 Pokud máte dialogové okno nebo upravovat uživatele formuláře a chcete odložit zdroj aktualizace, dokud uživatel je dokončení úprav pole a klikne na tlačítko "OK", můžete nastavit <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> hodnotu vazby na <xref:System.Windows.Data.UpdateSourceTrigger.Explicit>, jako v následujícím příkladu:  
  
 [!code-xaml[UpdateSource#2](~/samples/snippets/csharp/VS_Snippets_Wpf/UpdateSource/CSharp/Window1.xaml#2)]  
  
 Při nastavení <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> hodnota, která se <xref:System.Windows.Data.UpdateSourceTrigger.Explicit>, zdrojová hodnota změní jenom v případě aplikace volá <xref:System.Windows.Data.BindingExpression.UpdateSource%2A> metody. Následující příklad ukazuje, jak volat <xref:System.Windows.Data.BindingExpression.UpdateSource%2A> pro `itemNameTextBox`:  
  
 [!code-csharp[UpdateSource#1](~/samples/snippets/csharp/VS_Snippets_Wpf/UpdateSource/CSharp/Window1.xaml.cs#1)]
 [!code-vb[UpdateSource#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/UpdateSource/VisualBasic/Window1.xaml.vb#1)]  
  
> [!NOTE]
>  Můžete použít stejný postup pro vlastnosti jiných ovládacích prvků, ale mějte na paměti, že většinu dalších vlastností mají výchozí <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> hodnotu <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>. Další informace najdete v tématu <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> stránku vlastností.  
  
> [!NOTE]
>  <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> Vlastnost se zabývá aktualizací zdroje a proto je platné pouze pro <xref:System.Windows.Data.BindingMode.TwoWay> nebo <xref:System.Windows.Data.BindingMode.OneWayToSource> vazby. Pro <xref:System.Windows.Data.BindingMode.TwoWay> a <xref:System.Windows.Data.BindingMode.OneWayToSource> vazby pro práci, musí objekt zdroje k poskytování oznámení změn vlastností. Mohou odkazovat na vzorcích, uvedeným v tomto tématu pro další informace. Kromě toho se můžete podívat na [implementace oznámení změn vlastností](how-to-implement-property-change-notification.md).  
  
## <a name="see-also"></a>Viz také:

- [Témata s postupy](data-binding-how-to-topics.md)
