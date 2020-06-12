---
ms.openlocfilehash: aab7d8538c875e35c832acc2a6c64beb84d4fb47
ms.sourcegitcommit: 1cbd77da54405ea7dba343ac0334fb03237d25d2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/11/2020
ms.locfileid: "84702432"
---
### <a name="winforms-methods-now-throw-argumentexception"></a>Metody WinForms teď vyvolávají výjimku ArgumentException.

Některé metody model Windows Forms nyní vyvolají <xref:System.ArgumentException> neplatných argumentů, kde dříve neexistovaly.

#### <a name="change-description"></a>Popis změny

Dřív předávání argumentů neočekávaného nebo nesprávného typu určitým model Windows Forms metodám by způsobilo neurčitý stav. Počínaje rozhraním .NET 5,0 tyto metody nyní vyvolají <xref:System.ArgumentException> při předání neplatných argumentů.

Vyvolání <xref:System.ArgumentException> vyhovuje chování modulu runtime .NET. Vylepšuje také možnosti ladění tím, že jednoznačně komunikuje, který argument je neplatný.

Následující tabulka uvádí ovlivněné metody a parametry:

| Metoda | Název parametru | Podmínka | Přidaná verze |
|-|-|-|-|
| <xref:System.Windows.Forms.TabControl.GetToolTipText(System.Object)?displayProperty=fullName> | `item` | Argument není typu <xref:System.Windows.Forms.TabPage> . | 5,0 Preview 1 |
| <xref:System.Windows.Forms.DataFormats.GetFormat(System.String)?displayProperty=fullName> | `format` | Argument je `null` , <xref:System.String.Empty?displayProperty=nameWithType> nebo mezera. | 5,0 Preview 5 |

#### <a name="version-introduced"></a>Představená verze

.NET 5,0

#### <a name="recommended-action"></a>Doporučená akce

- Aktualizujte kód, abyste zabránili předávání neplatných argumentů.
- V případě potřeby zpracujte <xref:System.ArgumentException> při volání metody.

#### <a name="category"></a>Kategorie

Windows Forms

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

- <xref:System.Windows.Forms.TabControl.GetToolTipText(System.Object)?displayProperty=fullName>
- <xref:System.Windows.Forms.DataFormats.GetFormat(System.String)?displayProperty=fullName>

<!-- 

#### Affected APIs

- `M:System.Windows.Forms.TabControl.GetToolTipText(System.Object)`
- `M:System.Windows.Forms.DataFormats.GetFormat(System.String)`

-->
