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
# <a name="how-to-control-when-the-textbox-text-updates-the-source"></a><span data-ttu-id="c23f2-102">Postupy: Určení, kdy dojde k aktualizaci textu TextBox ve zdroji</span><span class="sxs-lookup"><span data-stu-id="c23f2-102">How to: Control When the TextBox Text Updates the Source</span></span>
<span data-ttu-id="c23f2-103">Toto téma popisuje postup použití <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> vlastnost řídit načasování vazby zdroj aktualizací.</span><span class="sxs-lookup"><span data-stu-id="c23f2-103">This topic describes how to use the <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> property to control the timing of binding source updates.</span></span> <span data-ttu-id="c23f2-104">Používá tématu <xref:System.Windows.Controls.TextBox> ovládací prvek jako příklad.</span><span class="sxs-lookup"><span data-stu-id="c23f2-104">The topic uses the <xref:System.Windows.Controls.TextBox> control as an example.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c23f2-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="c23f2-105">Example</span></span>  
 <span data-ttu-id="c23f2-106"><xref:System.Windows.Controls.TextBox>.<xref:System.Windows.Controls.TextBox.Text%2A> Vlastnost má výchozí <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> hodnotu <xref:System.Windows.Data.UpdateSourceTrigger.LostFocus>.</span><span class="sxs-lookup"><span data-stu-id="c23f2-106">The <xref:System.Windows.Controls.TextBox>.<xref:System.Windows.Controls.TextBox.Text%2A> property has a default <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> value of <xref:System.Windows.Data.UpdateSourceTrigger.LostFocus>.</span></span> <span data-ttu-id="c23f2-107">To znamená, že pokud má aplikace <xref:System.Windows.Controls.TextBox> s daty připojeného <xref:System.Windows.Controls.TextBox>.<xref:System.Windows.Controls.TextBox.Text%2A> vlastnost, kterou zadáte do text <xref:System.Windows.Controls.TextBox> neaktualizuje zdroji až <xref:System.Windows.Controls.TextBox> ztratí fokus (například když kliknete na tlačítko mimo <xref:System.Windows.Controls.TextBox>).</span><span class="sxs-lookup"><span data-stu-id="c23f2-107">This means if an application has a <xref:System.Windows.Controls.TextBox> with a data-bound <xref:System.Windows.Controls.TextBox>.<xref:System.Windows.Controls.TextBox.Text%2A> property, the text you type into the <xref:System.Windows.Controls.TextBox> does not update the source until the <xref:System.Windows.Controls.TextBox> loses focus (for instance, when you click away from the <xref:System.Windows.Controls.TextBox>).</span></span>  
  
 <span data-ttu-id="c23f2-108">Pokud chcete, aby zdroj k získání aktualizovat, protože při psaní, nastavte <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> vazby ke <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>.</span><span class="sxs-lookup"><span data-stu-id="c23f2-108">If you want the source to get updated as you are typing, set the <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> of the binding to <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>.</span></span> <span data-ttu-id="c23f2-109">V následujícím příkladu `Text` vlastnosti obou <xref:System.Windows.Controls.TextBox> a <xref:System.Windows.Controls.TextBlock> je vázána na stejnou vlastnost zdroje.</span><span class="sxs-lookup"><span data-stu-id="c23f2-109">In the following example, the `Text` properties of both the <xref:System.Windows.Controls.TextBox> and the <xref:System.Windows.Controls.TextBlock> are bound to the same source property.</span></span> <span data-ttu-id="c23f2-110"><xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> Vlastnost <xref:System.Windows.Controls.TextBox> vazba je nastaven na <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>.</span><span class="sxs-lookup"><span data-stu-id="c23f2-110">The <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> property of the <xref:System.Windows.Controls.TextBox> binding is set to <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>.</span></span>  
  
 [!code-xaml[SimpleBinding#USTHowTo](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleBinding/VisualBasic/Page1.xaml#usthowto)]  
  
 <span data-ttu-id="c23f2-111">V důsledku toho <xref:System.Windows.Controls.TextBlock> ukazuje stejný text (protože zdroji změní) jako uživatel zadá text do <xref:System.Windows.Controls.TextBox>, jak vidíte na následujícím snímku obrazovky vzorku:</span><span class="sxs-lookup"><span data-stu-id="c23f2-111">As a result, the <xref:System.Windows.Controls.TextBlock> shows the same text (because the source changes) as the user enters text into the <xref:System.Windows.Controls.TextBox>, as illustrated by the following screenshot of the sample:</span></span>  
  
 <span data-ttu-id="c23f2-112">![Jednoduché datové vazby – snímek obrazovky](../../../../docs/framework/wpf/data/media/databindingsimplebindingsample2.png "DataBindingSimpleBindingSample2")</span><span class="sxs-lookup"><span data-stu-id="c23f2-112">![Simple data binding sample screen shot](../../../../docs/framework/wpf/data/media/databindingsimplebindingsample2.png "DataBindingSimpleBindingSample2")</span></span>  
  
 <span data-ttu-id="c23f2-113">Pokud máte, zobrazí se dialogové okno nebo uživatel upravovat formulář a chcete odložení aktualizací zdroj, dokud se uživatel je dokončení úprav pole a klikne na tlačítko "OK", můžete nastavit <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> hodnotu vaší vazby na <xref:System.Windows.Data.UpdateSourceTrigger.Explicit>, jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="c23f2-113">If you have a dialog or a user-editable form and you want to defer source updates until the user is finished editing the fields and clicks "OK", you can set the <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> value of your bindings to <xref:System.Windows.Data.UpdateSourceTrigger.Explicit>, as in the following example:</span></span>  
  
 [!code-xaml[UpdateSource#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/UpdateSource/CSharp/Window1.xaml#2)]  
  
 <span data-ttu-id="c23f2-114">Když nastavíte <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> hodnotu <xref:System.Windows.Data.UpdateSourceTrigger.Explicit>, zdrojové hodnoty změní jenom v případě aplikace volá <xref:System.Windows.Data.BindingExpression.UpdateSource%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="c23f2-114">When you set the <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> value to <xref:System.Windows.Data.UpdateSourceTrigger.Explicit>, the source value only changes when the application calls the <xref:System.Windows.Data.BindingExpression.UpdateSource%2A> method.</span></span> <span data-ttu-id="c23f2-115">Následující příklad ukazuje způsob volání <xref:System.Windows.Data.BindingExpression.UpdateSource%2A> pro `itemNameTextBox`:</span><span class="sxs-lookup"><span data-stu-id="c23f2-115">The following example shows how to call <xref:System.Windows.Data.BindingExpression.UpdateSource%2A> for `itemNameTextBox`:</span></span>  
  
 [!code-csharp[UpdateSource#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/UpdateSource/CSharp/Window1.xaml.cs#1)]
 [!code-vb[UpdateSource#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UpdateSource/VisualBasic/Window1.xaml.vb#1)]  
  
> [!NOTE]
>  <span data-ttu-id="c23f2-116">Stejný postup použijte pro vlastnosti jiných ovládacích prvků, ale mějte na paměti, že většina ostatní vlastnosti mají výchozí <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> hodnotu <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>.</span><span class="sxs-lookup"><span data-stu-id="c23f2-116">You can use the same technique for properties of other controls, but keep in mind that most other properties have a default <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> value of <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>.</span></span> <span data-ttu-id="c23f2-117">Další informace najdete v tématu <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> stránku vlastností.</span><span class="sxs-lookup"><span data-stu-id="c23f2-117">For more information, see the <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> property page.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c23f2-118"><xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> Vlastnost zdroje aktualizace se zabývá a proto je platné pouze pro <xref:System.Windows.Data.BindingMode.TwoWay> nebo <xref:System.Windows.Data.BindingMode.OneWayToSource> vazby.</span><span class="sxs-lookup"><span data-stu-id="c23f2-118">The <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> property deals with source updates and therefore is only relevant for <xref:System.Windows.Data.BindingMode.TwoWay> or <xref:System.Windows.Data.BindingMode.OneWayToSource> bindings.</span></span> <span data-ttu-id="c23f2-119">Pro <xref:System.Windows.Data.BindingMode.TwoWay> a <xref:System.Windows.Data.BindingMode.OneWayToSource> vazby pracovat, je nutné objekt zdroje poskytují oznámení o změnách vlastnost.</span><span class="sxs-lookup"><span data-stu-id="c23f2-119">For <xref:System.Windows.Data.BindingMode.TwoWay> and <xref:System.Windows.Data.BindingMode.OneWayToSource> bindings to work, the source object needs to provide property change notifications.</span></span> <span data-ttu-id="c23f2-120">Najdete ukázky citovalo v tomto tématu pro další informace.</span><span class="sxs-lookup"><span data-stu-id="c23f2-120">You can refer to the samples cited in this topic for more information.</span></span> <span data-ttu-id="c23f2-121">Kromě toho můžete se podívat na [oznámení o změně vlastnost implementace](../../../../docs/framework/wpf/data/how-to-implement-property-change-notification.md).</span><span class="sxs-lookup"><span data-stu-id="c23f2-121">In addition, you can look at [Implement Property Change Notification](../../../../docs/framework/wpf/data/how-to-implement-property-change-notification.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c23f2-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="c23f2-122">See Also</span></span>  
 [<span data-ttu-id="c23f2-123">Témata s postupy</span><span class="sxs-lookup"><span data-stu-id="c23f2-123">How-to Topics</span></span>](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
