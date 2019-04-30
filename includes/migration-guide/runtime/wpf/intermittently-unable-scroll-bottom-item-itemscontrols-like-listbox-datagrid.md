---
ms.openlocfilehash: 9c2ee4ba66deb7c3b33698963add2b8a7e70069f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61649013"
---
### <a name="intermittently-unable-to-scroll-to-bottom-item-in-itemscontrols-like-listbox-and-datagrid-when-using-custom-datatemplates"></a>Občas schopen přejděte do dolní části položky v ItemsControls (například ListBox a DataGrid) při použití vlastního DataTemplates

|   |   |
|---|---|
|Podrobnosti|V některých případech je příčinou chyb v rozhraní .NET Framework 4.5 ItemsControls (jako je <xref:System.Windows.Controls.ListBox?displayProperty=name>, <xref:System.Windows.Controls.ComboBox?displayProperty=name>, <xref:System.Windows.Controls.DataGrid?displayProperty=name>atd) není stránku posunout, aby jejich dolní položky při použití vlastního DataTemplates. Pokud se posouvání dojde k pokusu o druhém (po posouvání zálohování), bude pracovat se.|
|Doporučení|Tento problém jsme opravili v rozhraní .NET Framework 4.5.2 a může ji adresovat podle upgrade na tuto verzi (nebo novější) rozhraní .NET Framework. Můžete také uživatelům k posledním položkám v těchto kolekcích můžete přetahovat posuvníky, ale možná bude nutné se dvakrát se pokouší provést úspěšně.|
|Rozsah|Vedlejší|
|Version|4.5|
|Type|Modul runtime|
