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
ms.openlocfilehash: d1d624d7550a1135431b7fffc7450e3a510855a7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966454"
---
# <a name="how-to-control-when-the-textbox-text-updates-the-source"></a>Postupy: Určení, kdy dojde k aktualizaci zdroje textem TextBox
Toto téma popisuje, jak použít <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> vlastnost k řízení časování aktualizací zdroje vazby. Téma jako příklad používá <xref:System.Windows.Controls.TextBox> ovládací prvek.  
  
## <a name="example"></a>Příklad  
 Rozhraní <xref:System.Windows.Controls.TextBox>.<xref:System.Windows.Controls.TextBox.Text%2A> vlastnost má výchozí <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> <xref:System.Windows.Data.UpdateSourceTrigger.LostFocus>hodnotu. To znamená, že aplikace má <xref:System.Windows.Controls.TextBox> s datovou vazbou. <xref:System.Windows.Controls.TextBox><xref:System.Windows.Controls.TextBox.Text%2A> vlastnost: text, který zadáte do <xref:System.Windows.Controls.TextBox> , neaktualizuje zdroj, <xref:System.Windows.Controls.TextBox> dokud nezmizí fokus (například když kliknete na tlačítko mimo <xref:System.Windows.Controls.TextBox>).  
  
 Pokud chcete, aby se zdroj aktualizoval při psaní, nastavte <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> vazbu na. <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged> V následujícím příkladu zvýrazněné řádky kódu ukazují, že `Text` vlastnosti <xref:System.Windows.Controls.TextBox> obou <xref:System.Windows.Controls.TextBlock> i jsou vázané na stejnou zdrojovou vlastnost. Vlastnost vazby je nastavena na <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>hodnotu. <xref:System.Windows.Controls.TextBox> <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>  
  
 [!code-xaml[SimpleBinding#USTHowTo](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleBinding/VisualBasic/Page1.xaml?highlight=33-39,41-42)]  
  
 Výsledkem je, že se <xref:System.Windows.Controls.TextBlock> zobrazí stejný text (protože změny zdrojového kódu) <xref:System.Windows.Controls.TextBox>, když uživatel zadá text do, jak je znázorněno na následujícím snímku obrazovky ukázky:  
  
 ![Snímek obrazovky, který zobrazuje jednoduchou datovou vazbu.](./media/how-to-control-when-the-textbox-text-updates-the-source/data-binding-simple-binding-sample.png)  
  
 Pokud máte dialog nebo formulář s možností úprav a chcete odložit aktualizace zdroje, dokud uživatel nedokončí úpravy polí a klikne na tlačítko OK, můžete nastavit <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> hodnotu vašich vazeb na <xref:System.Windows.Data.UpdateSourceTrigger.Explicit>, jako v následujícím příkladu:  
  
 [!code-xaml[UpdateSource#2](~/samples/snippets/csharp/VS_Snippets_Wpf/UpdateSource/CSharp/Window1.xaml#2)]  
  
 Když nastavíte <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> hodnotu na <xref:System.Windows.Data.UpdateSourceTrigger.Explicit>, hodnota zdroje se změní pouze v <xref:System.Windows.Data.BindingExpression.UpdateSource%2A> případě, že aplikace volá metodu. Následující příklad ukazuje, jak volat <xref:System.Windows.Data.BindingExpression.UpdateSource%2A> pro: `itemNameTextBox`  
  
 [!code-csharp[UpdateSource#1](~/samples/snippets/csharp/VS_Snippets_Wpf/UpdateSource/CSharp/Window1.xaml.cs#1)]
 [!code-vb[UpdateSource#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/UpdateSource/VisualBasic/Window1.xaml.vb#1)]  
  
> [!NOTE]
> Stejný postup můžete použít pro vlastnosti jiných ovládacích prvků, ale mějte na paměti, že většina dalších vlastností má výchozí <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>hodnotu. Další informace najdete na <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> stránce vlastností.  
  
> [!NOTE]
> Vlastnost se zabývá aktualizacemi zdroje, a proto je relevantní pouze <xref:System.Windows.Data.BindingMode.TwoWay> pro vazby nebo <xref:System.Windows.Data.BindingMode.OneWayToSource>. <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> Aby vazby <xref:System.Windows.Data.BindingMode.OneWayToSource> a fungovaly, musí zdrojový objekt poskytnout oznámení o změně vlastnosti. <xref:System.Windows.Data.BindingMode.TwoWay> Další informace najdete v ukázkách citovaných v tomto tématu. Kromě toho se můžete podívat na [oznámení o změně vlastnosti implementovat](how-to-implement-property-change-notification.md).  
  
## <a name="see-also"></a>Viz také:

- [Témata s postupy](data-binding-how-to-topics.md)
