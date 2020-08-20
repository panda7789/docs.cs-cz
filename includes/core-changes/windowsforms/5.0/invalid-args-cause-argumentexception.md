---
ms.openlocfilehash: 9f6703c77e17ac9376aee944b891f4635dc7632e
ms.sourcegitcommit: 0fa2b7b658bf137e813a7f4d09589d64c148ebf5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/14/2020
ms.locfileid: "86309137"
---
### <a name="winforms-methods-now-throw-argumentexception"></a>Metody WinForms teď vyvolávají výjimku ArgumentException.

Některé metody model Windows Forms nyní vyvolají <xref:System.ArgumentException> neplatných argumentů, kde dříve neexistovaly.

#### <a name="change-description"></a>Popis změny

Dřív předávání argumentů neočekávaného nebo nesprávného typu určitým model Windows Forms metodám by způsobilo neurčitý stav. Počínaje rozhraním .NET 5,0 tyto metody nyní vyvolají <xref:System.ArgumentException> při předání neplatných argumentů.

Vyvolání <xref:System.ArgumentException> vyhovuje chování modulu runtime .NET. Vylepšuje také možnosti ladění tím, že jednoznačně komunikuje, který argument je neplatný.

#### <a name="version-introduced"></a>Představená verze

.NET 5,0

#### <a name="recommended-action"></a>Doporučená akce

- Aktualizujte kód, abyste zabránili předávání neplatných argumentů.
- V případě potřeby zpracujte <xref:System.ArgumentException> při volání metody.

#### <a name="category"></a>Kategorie

Windows Forms

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

Následující tabulka uvádí ovlivněné metody a parametry:

| Metoda | Název parametru | Stav | Přidaná verze |
|-|-|-|-|
| <xref:System.Windows.Forms.TabControl.GetToolTipText(System.Object)?displayProperty=fullName> | `item` | Argument není typu <xref:System.Windows.Forms.TabPage> . | Preview 1 |
| <xref:System.Windows.Forms.DataFormats.GetFormat(System.String)?displayProperty=fullName> | `format` | Argument je `null` , <xref:System.String.Empty?displayProperty=nameWithType> nebo mezera. | Preview 5 |
| <xref:System.Windows.Forms.InputLanguageChangedEventArgs.%23ctor(System.Globalization.CultureInfo,System.Byte)> | `culture` | Nelze načíst `InputLanguage` pro určenou jazykovou verzi. | Preview 7 |

<!-- 

#### Affected APIs

- `M:System.Windows.Forms.TabControl.GetToolTipText(System.Object)`
- `M:System.Windows.Forms.DataFormats.GetFormat(System.String)`
- `M:System.Windows.Forms.InputLanguageChangedEventArgs.%23ctor(System.Globalization.CultureInfo,System.Byte)`

-->
