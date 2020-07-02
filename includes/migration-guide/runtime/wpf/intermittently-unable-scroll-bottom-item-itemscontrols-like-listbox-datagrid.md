---
ms.openlocfilehash: b92dc8a1c48e83846c3d9a1d86e66629f31b7722
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622018"
---
### <a name="intermittently-unable-to-scroll-to-bottom-item-in-itemscontrols-like-listbox-and-datagrid-when-using-custom-datatemplates"></a>Při použití vlastních šablon DataTemplates se občas nedá přejít na spodní položku v ItemsControls (například ListBox a DataGrid).

#### <a name="details"></a>Podrobnosti

V některých případech chyby v .NET Framework 4,5 způsobují ItemsControls (například <xref:System.Windows.Controls.ListBox?displayProperty=fullName> , <xref:System.Windows.Controls.ComboBox?displayProperty=fullName> , atd <xref:System.Windows.Controls.DataGrid?displayProperty=fullName> .), aby se při použití vlastních šablon DataTemplate nepřesunuly na jejich spodní položku. Pokud se pokusy o posouvání podruhé (po posunu nahoru), budou fungovat.

#### <a name="suggestion"></a>Návrh

Tento problém byl opraven v .NET Framework 4.5.2 a může se řešit upgradem na tuto verzi (nebo novější verzi) .NET Framework. Další možností je, že uživatelé stále mohou přesouvat posuvníky do konečných položek v těchto kolekcích, ale může se to pokusit provést dvakrát, aby to bylo úspěšné.

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   |Vedlejší|
|Verze|4.5|
|Typ|Modul runtime|
