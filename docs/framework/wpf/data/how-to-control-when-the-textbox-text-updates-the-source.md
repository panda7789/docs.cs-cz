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
ms.openlocfilehash: b211eb67e3bac95f74255935a39cc0d6aec61531
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/12/2019
ms.locfileid: "73974789"
---
# <a name="how-to-control-when-the-textbox-text-updates-the-source"></a>Postupy: Určení, kdy dojde k aktualizaci textu TextBox ve zdroji
Toto téma popisuje, jak použít vlastnost <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> k řízení časování aktualizací zdroje vazby. Téma jako příklad používá ovládací prvek <xref:System.Windows.Controls.TextBox>.

## <a name="example"></a>Příklad
 Vlastnost <xref:System.Windows.Controls.TextBox.Text%2A?displayProperty=nameWithType> má výchozí hodnotu <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> <xref:System.Windows.Data.UpdateSourceTrigger.LostFocus>. To znamená, že pokud má aplikace <xref:System.Windows.Controls.TextBox> s vlastností <xref:System.Windows.Controls.TextBox.Text%2A?displayProperty=nameWithType> vázaná na data, text, který zadáte do <xref:System.Windows.Controls.TextBox>, neaktualizuje zdroj, dokud <xref:System.Windows.Controls.TextBox> ztratí fokus (například když kliknete mimo <xref:System.Windows.Controls.TextBox>).

 Pokud chcete, aby se zdroj aktualizoval při psaní, nastavte <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> vazby na <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>. V následujícím příkladu zvýrazněné řádky kódu ukazují, že `Text` vlastnosti <xref:System.Windows.Controls.TextBox> a <xref:System.Windows.Controls.TextBlock> jsou vázány na stejnou zdrojovou vlastnost. Vlastnost <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> vazby <xref:System.Windows.Controls.TextBox> je nastavena na <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>.

 [!code-xaml[SimpleBinding#USTHowTo](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleBinding/VisualBasic/Page1.xaml?highlight=33-39,41-42)]

 V důsledku toho <xref:System.Windows.Controls.TextBlock> zobrazí stejný text (protože změny zdrojového kódu), když uživatel zadá text do <xref:System.Windows.Controls.TextBox>, jak je znázorněno na následujícím snímku obrazovky ukázky:

 ![Snímek obrazovky, který zobrazuje jednoduchou datovou vazbu.](./media/how-to-control-when-the-textbox-text-updates-the-source/data-binding-simple-binding-sample.png)

 Máte-li dialog nebo formulář s možností úprav a chcete odložit aktualizace zdroje, dokud uživatel nedokončí úpravy polí a klikne na tlačítko OK, můžete nastavit <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> hodnoty vašich vazeb na <xref:System.Windows.Data.UpdateSourceTrigger.Explicit>, jako v následujícím příkladu:

 [!code-xaml[UpdateSource#2](~/samples/snippets/csharp/VS_Snippets_Wpf/UpdateSource/CSharp/Window1.xaml#2)]

 Když nastavíte <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> hodnotu na <xref:System.Windows.Data.UpdateSourceTrigger.Explicit>, hodnota zdroje se změní pouze v případě, že aplikace volá metodu <xref:System.Windows.Data.BindingExpression.UpdateSource%2A>. Následující příklad ukazuje, jak volat <xref:System.Windows.Data.BindingExpression.UpdateSource%2A> pro `itemNameTextBox`:

 [!code-csharp[UpdateSource#1](~/samples/snippets/csharp/VS_Snippets_Wpf/UpdateSource/CSharp/Window1.xaml.cs#1)]
 [!code-vb[UpdateSource#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/UpdateSource/VisualBasic/Window1.xaml.vb#1)]

> [!NOTE]
> Stejný postup můžete použít pro vlastnosti jiných ovládacích prvků, ale mějte na paměti, že většina dalších vlastností má výchozí <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> hodnotu <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>. Další informace najdete na stránce vlastností <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>.

> [!NOTE]
> Vlastnost <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> pracuje se zdrojovými aktualizacemi a proto je relevantní pouze pro vazby <xref:System.Windows.Data.BindingMode.TwoWay> nebo <xref:System.Windows.Data.BindingMode.OneWayToSource>. Aby vazby <xref:System.Windows.Data.BindingMode.TwoWay> a <xref:System.Windows.Data.BindingMode.OneWayToSource> fungovaly, musí zdrojový objekt poskytnout oznámení o změně vlastnosti. Další informace najdete v ukázkách citovaných v tomto tématu. Kromě toho se můžete podívat na [oznámení o změně vlastnosti implementovat](how-to-implement-property-change-notification.md).

## <a name="see-also"></a>Viz také:

- [Témata s postupy](data-binding-how-to-topics.md)
