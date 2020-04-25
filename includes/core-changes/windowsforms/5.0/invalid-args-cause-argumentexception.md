---
ms.openlocfilehash: 5212c5d9513a8ef5f51693857d0ddb60db4e49b9
ms.sourcegitcommit: c2c1269a81ffdcfc8675bcd9a8505b1a11ffb271
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/25/2020
ms.locfileid: "82158389"
---
### <a name="winforms-methods-now-throw-argumentexception"></a>Metody WinForms teď vyvolávají výjimku ArgumentException.

Některé metody model Windows Forms nyní vyvolají <xref:System.ArgumentException> neplatných argumentů, kde dříve neexistovaly.

#### <a name="change-description"></a>Popis změny

Dřív předávání argumentů neočekávaného nebo nesprávného typu určitým model Windows Forms metodám by způsobilo neurčitý stav. Počínaje rozhraním .NET 5,0 tyto metody nyní vyvolají <xref:System.ArgumentException> při předání neplatných argumentů.

<xref:System.ArgumentException> Vyvolání vyhovuje chování modulu runtime .NET. Vylepšuje také možnosti ladění tím, že jednoznačně komunikuje, který argument je neplatný.

Následující tabulka uvádí ovlivněné metody a parametry:

| Metoda | Název parametru | Podmínka | Přidaná verze |
|-|-|-|
| <xref:System.Windows.Forms.TabControl.GetToolTipText(System.Object)?displayProperty=fullName> | `item` | Argument není typu <xref:System.Windows.Forms.TabPage>. | 5,0 Preview 1 |

#### <a name="version-introduced"></a>Představená verze

.NET 5,0 Preview 1

#### <a name="recommended-action"></a>Doporučená akce

- Aktualizujte kód, abyste zabránili předávání neplatných argumentů.
- V případě potřeby zpracujte <xref:System.ArgumentException> při volání metody.

#### <a name="category"></a>Kategorie

Windows Forms

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

- <xref:System.Windows.Forms.TabControl.GetToolTipText(System.Object)?displayProperty=fullName>

<!-- 

### Affected APIs

- `M:System.Windows.Forms.TabControl.GetToolTipText(System.Object)`

-->
