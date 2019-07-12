---
ms.openlocfilehash: 2674edc595d8e4e1e4c2ee42b39aa59265127462
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/11/2019
ms.locfileid: "67803197"
---
### <a name="intermittently-unable-to-scroll-to-bottom-item-in-itemscontrols-like-listbox-and-datagrid-when-using-custom-datatemplates"></a>Občas schopen přejděte do dolní části položky v ItemsControls (například ListBox a DataGrid) při použití vlastního DataTemplates

|   |   |
|---|---|
|Podrobnosti|V některých případech je příčinou chyb v rozhraní .NET Framework 4.5 ItemsControls (jako je <xref:System.Windows.Controls.ListBox?displayProperty=name>, <xref:System.Windows.Controls.ComboBox?displayProperty=name>, <xref:System.Windows.Controls.DataGrid?displayProperty=name>atd) není stránku posunout, aby jejich dolní položky při použití vlastního DataTemplates. Pokud se posouvání dojde k pokusu o druhém (po posouvání zálohování), bude pracovat se.|
|Doporučení|Tento problém jsme opravili v rozhraní .NET Framework 4.5.2 a může ji adresovat podle upgrade na tuto verzi (nebo novější) rozhraní .NET Framework. Můžete také uživatelům k posledním položkám v těchto kolekcích můžete přetahovat posuvníky, ale možná bude nutné se dvakrát se pokouší provést úspěšně.|
|Scope|Vedlejší|
|Version|4.5|
|type|Modul runtime|

