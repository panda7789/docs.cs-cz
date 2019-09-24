---
ms.openlocfilehash: 843007ac6467584fbe6350b6ea19ef67609d73e2
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/24/2019
ms.locfileid: "71217029"
---
### <a name="controldefaultfont-changed-to-segoe-ui-9pt"></a>`Control.DefaultFont`změněno na`Segoe UI 9pt`

#### <a name="change-description"></a>Změnit popis

V .NET Framework <xref:System.Windows.Forms.Control.DefaultFont?displayProperty=nameWithType> byla vlastnost nastavena na `Microsoft Sans Serif 8pt`. Následující obrázek ukazuje okno, které používá výchozí písmo.

![výchozí písmo ovládacího prvku v .NET Framework](~/docs/images/core-changes/windowsforms/control-defaultfont-changed/defaultfont-framework.png)

V .NET Core Počínaje rozhraním .NET Core 3,0 je nastavená na `Segoe UI 9pt` (stejné písmo jako <xref:System.Drawing.SystemFonts.MessageBoxFont?displayProperty=nameWithType>). V důsledku této změny budou mít formuláře a ovládací prvky velikost přibližně 27% větší, než je výsledkem větší velikost nového výchozího písma. Příklad:

![výchozí ovládací prvek Font-in .NET Core](~/docs/images/core-changes/windowsforms/control-defaultfont-changed/defaultfont-core.png)

Tato změna byla provedena v souladu s [pokyny pro uživatelské rozhraní Windows](https://docs.microsoft.com/windows/win32/uxguide/vis-fonts#fonts-and-colors).

#### <a name="version-introduced"></a>Představená verze

3.0

#### <a name="recommended-action"></a>Doporučená akce

Kvůli změně velikosti formulářů a ovládacích prvků se ujistěte, že se vaše aplikace vykresluje správně.

Chcete-li zachovat původní písmo, nastavte výchozí písmo formuláře na `Microsoft Sans Serif 8pt`hodnotu. Příklad:

```csharp
public MyForm()
{
    InitializeComponent();
    Font = new Font(new FontFamily("Microsoft Sans Serif"), 8f);
}
```

#### <a name="category"></a>Kategorie

- Windows Forms

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

Žádné

<!--

### Affected APIs

- Not detectable via API analysis

-->
