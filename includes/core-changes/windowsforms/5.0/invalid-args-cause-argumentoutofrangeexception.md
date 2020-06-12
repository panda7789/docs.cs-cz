---
ms.openlocfilehash: f42da00487735acdcc60f876c75e1dfd17103008
ms.sourcegitcommit: 1cbd77da54405ea7dba343ac0334fb03237d25d2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/11/2020
ms.locfileid: "84702433"
---
### <a name="winforms-properties-now-throw-argumentoutofrangeexception"></a>Vlastnosti WinForms teď vyvolávají výjimku ArgumentOutOfRangeException.

Některé vlastnosti model Windows Forms nyní vyvolají <xref:System.ArgumentOutOfRangeException> neplatných argumentů, kde dříve neexistovaly.

#### <a name="change-description"></a>Popis změny

Dříve tyto vlastnosti vyvolaly různé výjimky, například <xref:System.NullReferenceException> , <xref:System.IndexOutOfRangeException> nebo <xref:System.ArgumentException> , při předání argumentů mimo rozsah. Počínaje rozhraním .NET 5,0 tyto vlastnosti nyní vyvolají <xref:System.ArgumentOutOfRangeException> při předaném argumentech, které jsou mimo rozsah.

Vyvolání <xref:System.ArgumentOutOfRangeException> vyhovuje chování modulu runtime .NET. Vylepšuje také možnosti ladění tím, že jednoznačně komunikuje, který argument je neplatný.

#### <a name="version-introduced"></a>Představená verze

.NET 5,0

#### <a name="recommended-action"></a>Doporučená akce

- Aktualizujte kód, abyste zabránili předávání neplatných argumentů.
- V případě potřeby <xref:System.ArgumentOutOfRangeException> při nastavování vlastnosti zpracujte.

#### <a name="category"></a>Kategorie

Windows Forms

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

Následující tabulka obsahuje seznam ovlivněných vlastností a parametrů:

> [!div class="mx-tdBreakAll"]
> | Vlastnost | Název parametru | Přidaná verze |
> |-|-|-|
> | <xref:System.Windows.Forms.ListBox.IntegerCollection.Item(System.Int32)?displayProperty=nameWithType> | `index` | 5,0 Preview 5 |
> | <xref:System.Windows.Forms.TreeNode.ImageIndex?displayProperty=nameWithType> | `value` | 5,0 Preview 6 |
> | <xref:System.Windows.Forms.TreeNode.SelectedImageIndex?displayProperty=nameWithType> | `value` | 5,0 Preview 6 |

<!-- 

#### Affected APIs

- `P:System.Windows.Forms.ListBox.IntegerCollection.Item(System.Int32)`
- `P:System.Windows.Forms.TreeNode.ImageIndex`
- `P:System.Windows.Forms.TreeNode.SelectedImageIndex`

-->
