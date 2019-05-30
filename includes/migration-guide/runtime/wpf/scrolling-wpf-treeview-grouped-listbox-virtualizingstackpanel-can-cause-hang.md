---
ms.openlocfilehash: 53fc2a51a7995e9b6ad43e28429313d2aea9abf1
ms.sourcegitcommit: 4735bb7741555bcb870d7b42964d3774f4897a6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/30/2019
ms.locfileid: "66379243"
---
### <a name="scrolling-a-wpf-treeview-or-grouped-listbox-in-a-virtualizingstackpanel-can-result-in-an-unresponsive-application"></a>Posouvání prvku WPF TreeView nebo seskupené ListBox v VirtualizingStackPanel může vést k aplikaci reagovat

|   |   |
|---|---|
|Podrobnosti|V rozhraní .NET Framework 4.5, posouvání WPF <xref:System.Windows.Controls.TreeView?displayProperty=name> ve virtualizovaných zásobníku může způsobit panel aplikace přestane reagovat, pokud nejsou okraje v zobrazení (mezi položkami v <xref:System.Windows.Controls.TreeView?displayProperty=name>, například, nebo v elementu ItemsPresenter). Kromě toho v některých případech různé velikosti položky v zobrazení může způsobit nestabilitu i v případě, že neexistují žádné okraje.|
|Doporučení|Upgradem na rozhraní .NET Framework 4.5.1 se lze vyvarovat této chyby. Okraje Alternativně je možné odebrat ze zobrazení kolekce (jako je <xref:System.Windows.Controls.TreeView?displayProperty=name>s) v rámci zásobníku virtualizované panelů, je-li všechny obsažené položky mají stejnou velikost.|
|Scope|Hlavní|
|Version|4.5|
|Type|Modul runtime|
|Ovlivněná rozhraní API|<ul><li><xref:System.Windows.Controls.VirtualizingStackPanel.SetIsVirtualizing(System.Windows.DependencyObject,System.Boolean)?displayProperty=nameWithType></li></ul>|
