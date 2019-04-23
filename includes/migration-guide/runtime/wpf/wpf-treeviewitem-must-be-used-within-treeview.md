---
ms.openlocfilehash: 88e00454894c8404fd48e92404e35ae27fa056f6
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59235225"
---
### <a name="wpf-treeviewitem-must-be-used-within-a-treeview"></a>Musí být použita WPF TreeViewItem v objektu TreeView

|   |   |
|---|---|
|Podrobnosti|Změna byla zavedena v 4.5, který omezuje využití <xref:System.Windows.Controls.TreeViewItem?displayProperty=name> prvky mimo <xref:System.Windows.Controls.TreeView?displayProperty=name>. To manifesty za následujících podmínek:<ul><li><xref:System.Windows.Controls.TreeViewItem?displayProperty=name>pro vizuální nadřazený není panel. (A <xref:System.Windows.Controls.TreeViewItem?displayProperty=name> vygenerovaný pro <xref:System.Windows.Controls.TreeView?displayProperty=name> bude mít jako jeho nadřazený objekt panel)</li><li><xref:System.Windows.Controls.TreeViewItem?displayProperty=name> Je potomkem <xref:System.Windows.Controls.VirtualizingStackPanel?displayProperty=name> funguje jako &quot;položky hostitele&quot; pro ovládací prvek seznamu (ListBox ovládacího prvku DataGrid, ListView, atd.). Virtualizace nemusí být povolená.</li><li><xref:System.Windows.Controls.VirtualizingStackPanel?displayProperty=name> Je položka posouvání (<code>ScrollUnit=&quot;Item&quot;</code>).</li><li>Někdo volá <code>VirtualizingStackPanel.MakeVisible(v)</code> posouvat element <code>v</code> do zobrazení. To lze provést explicitně nebo implicitně různými způsoby; možná nejběžnější stejně, jako je jednoduše kliknutím na <code>v</code> o fokus klávesnice.</li><li>Vizuál nadřazeného řetězce z <code>v</code> k <xref:System.Windows.Controls.VirtualizingStackPanel?displayProperty=name> prochází <xref:System.Windows.Controls.TreeViewItem?displayProperty=name>.</li></ul>Jinými slovy, zobrazuje při <xref:System.Windows.Controls.TreeViewItem?displayProperty=name> se používá mimo <xref:System.Windows.Controls.TreeView?displayProperty=name>, a uživatel klikne na potomkem <xref:System.Windows.Controls.TreeViewItem?displayProperty=name> pro přivedení do zobrazení. Pokud <xref:System.Windows.Controls.TreeViewItem?displayProperty=name> nemá žádné focusable následníky, nikdy zobrazí se vám tento problém. Je například situace, kdy dosáhnete, když <xref:System.Windows.Controls.TreeViewItem?displayProperty=name> kořenovou šablonu DataTemplate. Při dosažení tohoto problému, je k InvalidCastException, ke které dochází v rámci WPF.|
|Doporučení|Oprava hotfix bude k dispozici pro tento.|
|Rozsah|Vedlejší|
|Version|4.5|
|Type|Modul runtime|
