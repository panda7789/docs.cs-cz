---
ms.openlocfilehash: 9c2ee4ba66deb7c3b33698963add2b8a7e70069f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "67803197"
---
### <a name="intermittently-unable-to-scroll-to-bottom-item-in-itemscontrols-like-listbox-and-datagrid-when-using-custom-datatemplates"></a>Občas nelze posunout na dolní položku v ItemsControls (jako ListBox a DataGrid) při použití vlastních šablon DataTemplates

|   |   |
|---|---|
|Podrobnosti|V některých případech chyba v rozhraní .NET Framework 4.5 <xref:System.Windows.Controls.ListBox?displayProperty=name>způsobuje <xref:System.Windows.Controls.ComboBox?displayProperty=name> <xref:System.Windows.Controls.DataGrid?displayProperty=name>ItemsControls (jako , , , atd.) není posunout na jejich spodní položku při použití vlastní DataTemplates. Pokud se o posouvání pokusíte podruhé (po posouvání zpět nahoru), bude to fungovat.|
|Návrh|Tento problém byl vyřešen v rozhraní .NET Framework 4.5.2 a může být vyřešen upgradem na tuto verzi (nebo novější verzi) rozhraní .NET Framework. Případně mohou uživatelé stále přetahovat posuvníky na konečné položky v těchto kolekcích, ale může být nutné zkusit dvakrát, aby tak učinily úspěšně.|
|Rozsah|Vedlejší|
|Version|4.5|
|Typ|Modul runtime|
