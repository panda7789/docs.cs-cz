---
title: 'Postupy: Určení, kdy dojde k aktualizaci textu TextBox ve zdroji'
description: Řízení časování aktualizací zdrojů vazby pomocí vlastnosti UpdateSourceTrigger v Windows Presentation Foundation (WPF).
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- source updates [WPF], timing of
- data binding [WPF], timing of source updates
- timing of source updates [WPF]
ms.assetid: ffb7b96a-351d-4c68-81e7-054033781c64
ms.openlocfilehash: 8f6eb5beb0d14a951f6e6cf6eb81e130f5a3e194
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622780"
---
# <a name="how-to-control-when-the-textbox-text-updates-the-source"></a>Postupy: Určení, kdy dojde k aktualizaci textu TextBox ve zdroji
Toto téma popisuje, jak použít <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> vlastnost k řízení časování aktualizací zdroje vazby. Téma <xref:System.Windows.Controls.TextBox> jako příklad používá ovládací prvek.

## <a name="example"></a>Příklad
 <xref:System.Windows.Controls.TextBox.Text%2A?displayProperty=nameWithType>Vlastnost má výchozí <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> hodnotu <xref:System.Windows.Data.UpdateSourceTrigger.LostFocus> . To znamená, že pokud má aplikace <xref:System.Windows.Controls.TextBox> vlastnost s vazbou na data <xref:System.Windows.Controls.TextBox.Text%2A?displayProperty=nameWithType> , text, který zadáte do, <xref:System.Windows.Controls.TextBox> neaktualizuje zdroj, dokud se nezobrazují <xref:System.Windows.Controls.TextBox> fokus (například když kliknete na tlačítko mimo <xref:System.Windows.Controls.TextBox> ).

 Pokud chcete, aby se zdroj aktualizoval při psaní, nastavte <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> vazbu na <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged> . V následujícím příkladu zvýrazněné řádky kódu ukazují, že `Text` vlastnosti obou i <xref:System.Windows.Controls.TextBox> <xref:System.Windows.Controls.TextBlock> jsou vázané na stejnou zdrojovou vlastnost. <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>Vlastnost <xref:System.Windows.Controls.TextBox> vazby je nastavena na hodnotu <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged> .

 [!code-xaml[SimpleBinding#USTHowTo](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleBinding/VisualBasic/Page1.xaml?highlight=33-39,41-42)]

 Výsledkem je, že se <xref:System.Windows.Controls.TextBlock> zobrazí stejný text (protože změny zdrojového kódu), když uživatel zadá text do <xref:System.Windows.Controls.TextBox> , jak je znázorněno na následujícím snímku obrazovky ukázky:

 ![Snímek obrazovky, který zobrazuje jednoduchou datovou vazbu.](./media/how-to-control-when-the-textbox-text-updates-the-source/data-binding-simple-binding-sample.png)

 Pokud máte dialog nebo formulář s možností úprav a chcete odložit aktualizace zdroje, dokud uživatel nedokončí úpravy polí a klikne na tlačítko OK, můžete nastavit <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> hodnotu vašich vazeb na <xref:System.Windows.Data.UpdateSourceTrigger.Explicit> , jako v následujícím příkladu:

 [!code-xaml[UpdateSource#2](~/samples/snippets/csharp/VS_Snippets_Wpf/UpdateSource/CSharp/Window1.xaml#2)]

 Když nastavíte <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> hodnotu na <xref:System.Windows.Data.UpdateSourceTrigger.Explicit> , hodnota zdroje se změní pouze v případě, že aplikace volá <xref:System.Windows.Data.BindingExpression.UpdateSource%2A> metodu. Následující příklad ukazuje, jak volat <xref:System.Windows.Data.BindingExpression.UpdateSource%2A> pro `itemNameTextBox` :

 [!code-csharp[UpdateSource#1](~/samples/snippets/csharp/VS_Snippets_Wpf/UpdateSource/CSharp/Window1.xaml.cs#1)]
 [!code-vb[UpdateSource#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/UpdateSource/VisualBasic/Window1.xaml.vb#1)]

> [!NOTE]
> Stejný postup můžete použít pro vlastnosti jiných ovládacích prvků, ale mějte na paměti, že většina dalších vlastností má výchozí <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> hodnotu <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged> . Další informace najdete na <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> stránce vlastností.

> [!NOTE]
> <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>Vlastnost se zabývá aktualizacemi zdroje, a proto je relevantní pouze <xref:System.Windows.Data.BindingMode.TwoWay> pro <xref:System.Windows.Data.BindingMode.OneWayToSource> vazby nebo. Aby <xref:System.Windows.Data.BindingMode.TwoWay> <xref:System.Windows.Data.BindingMode.OneWayToSource> vazby a fungovaly, musí zdrojový objekt poskytnout oznámení o změně vlastnosti. Další informace najdete v ukázkách citovaných v tomto tématu. Kromě toho se můžete podívat na [oznámení o změně vlastnosti implementovat](how-to-implement-property-change-notification.md).

## <a name="see-also"></a>Viz také:

- [– postupy](data-binding-how-to-topics.md)
