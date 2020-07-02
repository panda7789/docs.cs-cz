---
ms.openlocfilehash: af8cb9435be078351e3430dc8ded3f7cac377948
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620109"
---
### <a name="wpf-treeviewitem-must-be-used-within-a-treeview"></a>TreeViewItem WPF se musí použít v prvku TreeView.

#### <a name="details"></a>Podrobnosti

Byla představena změna v 4,5, která omezuje použití <xref:System.Windows.Controls.TreeViewItem?displayProperty=fullName> elementů mimo <xref:System.Windows.Controls.TreeView?displayProperty=fullName> . Tyto manifesty se nacházejí v následujících podmínkách:<ul><li><xref:System.Windows.Controls.TreeViewItem?displayProperty=fullName>vizuální nadřazený prvek není panel. ( <xref:System.Windows.Controls.TreeViewItem?displayProperty=fullName> Vygenerovaný pro A <xref:System.Windows.Controls.TreeView?displayProperty=fullName> bude mít panel jako svůj nadřazený prvek)</li><li><xref:System.Windows.Controls.TreeViewItem?displayProperty=fullName>Je potomkem <xref:System.Windows.Controls.VirtualizingStackPanel?displayProperty=fullName> působícího jako &quot; hostitel položek &quot; ovládacího prvku seznam (ListBox, DataGrid, ListView atd.). Virtualizace není nutné povolit.</li><li><xref:System.Windows.Controls.VirtualizingStackPanel?displayProperty=fullName>Je posun položky ( <code>ScrollUnit=&quot;Item&quot;</code> ).</li><li>Někdo volá <code>VirtualizingStackPanel.MakeVisible(v)</code> , aby se element přesunul na <code>v</code> zobrazení. To lze provést explicitně nebo implicitně řadou způsobů; Nejběžnějším způsobem je jednoduše kliknout na tlačítko <code>v</code> a dát mu fokus klávesnice.</li><li>Vizuální – nadřazený řetězec od <code>v</code> do <xref:System.Windows.Controls.VirtualizingStackPanel?displayProperty=fullName> průchodu přes <xref:System.Windows.Controls.TreeViewItem?displayProperty=fullName> .</li></ul>Jinými slovy se zobrazuje, když <xref:System.Windows.Controls.TreeViewItem?displayProperty=fullName> se používá mimo a <xref:System.Windows.Controls.TreeView?displayProperty=fullName> a uživatel klikne na následníka <xref:System.Windows.Controls.TreeViewItem?displayProperty=fullName> pro, aby se zobrazila. Pokud <xref:System.Windows.Controls.TreeViewItem?displayProperty=fullName> nemá žádného člena s fokusem, tento problém se vám nikdy nezobrazuje. Příkladem situace, kdy je dosaženo, je, že je <xref:System.Windows.Controls.TreeViewItem?displayProperty=fullName> kořenovým adresářem objektu DataTemplate. V případě, že k tomuto problému dojde, existuje InvalidCastException, ke kterému dochází v rámci platformy WPF.

#### <a name="suggestion"></a>Návrh

Pro tuto instalaci bude k dispozici oprava hotfix.

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   |Vedlejší|
|Verze|4.5|
|Typ|Modul runtime|
