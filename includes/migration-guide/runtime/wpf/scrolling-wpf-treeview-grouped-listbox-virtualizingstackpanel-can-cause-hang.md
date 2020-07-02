---
ms.openlocfilehash: 1be68c2968d0eaa9024007bcf37abf9e44c36f1c
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622053"
---
### <a name="scrolling-a-wpf-treeview-or-grouped-listbox-in-a-virtualizingstackpanel-can-cause-a-hang"></a>Posouvání zobrazení stromu WPF nebo seskupeného seznamu ve VirtualizingStackPanel může způsobit zablokování

#### <a name="details"></a>Podrobnosti

V .NET Framework v 4.5 může posouvání WPF <xref:System.Windows.Controls.TreeView?displayProperty=fullName> na virtualizovaném panelu zásobníku způsobit zablokování, pokud jsou v zobrazení okraje (například mezi položkami v <xref:System.Windows.Controls.TreeView?displayProperty=fullName> , například nebo na prvku ItemsPresenter). V některých případech mohou různé velikosti položek v zobrazení způsobit nestabilitu i v případě, že nejsou k dispozici žádné okraje.

#### <a name="suggestion"></a>Návrh

Tato chyba se může vyhnout upgradem na .NET Framework 4.5.1. Alternativně lze marže odebrat z kolekce zobrazení (například <xref:System.Windows.Controls.TreeView?displayProperty=fullName> s) v rámci virtualizovaných panelů zásobníku, pokud všechny obsažené položky mají stejnou velikost.

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   |Hlavní|
|Verze|4.5|
|Typ|Modul runtime

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

-<xref:System.Windows.Controls.VirtualizingStackPanel.SetIsVirtualizing(System.Windows.DependencyObject,System.Boolean)?displayProperty=nameWithType></li></ul>|
