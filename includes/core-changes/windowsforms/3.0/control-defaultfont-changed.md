---
ms.openlocfilehash: 0b2d3c1383246d4259c6d906ecf9dab927f4bdb1
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721509"
---
### <a name="default-control-font-changed-to-segoe-ui-9-pt"></a>Výchozí písmo ovládacího prvku se změnilo na Segoe UI 9 bodů.

#### <a name="change-description"></a>Popis změny

V .NET Framework <xref:System.Windows.Forms.Control.DefaultFont?displayProperty=nameWithType> byla vlastnost nastavena na `Microsoft Sans Serif 8 pt` . Následující obrázek ukazuje okno, které používá výchozí písmo.

![Výchozí písmo ovládacího prvku v .NET Framework](~/docs/images/core-changes/windowsforms/control-defaultfont-changed/defaultfont-framework.png)

Počínaje platformou .NET Core 3,0 je výchozí písmo nastaveno na `Segoe UI 9 pt` (stejné písmo jako <xref:System.Drawing.SystemFonts.MessageBoxFont?displayProperty=nameWithType> ). V důsledku této změny mají formuláře a ovládací prvky velikost přibližně 27% větší, než je větší velikost nového výchozího písma. Například:

![Výchozí písmo ovládacího prvku v .NET Core](~/docs/images/core-changes/windowsforms/control-defaultfont-changed/defaultfont-core.png)

Tato změna byla provedena v souladu s [pokyny pro uživatelské prostředí systému Windows (UX)](/windows/win32/uxguide/vis-fonts#fonts-and-colors).

#### <a name="version-introduced"></a>Představená verze

3.0

#### <a name="recommended-action"></a>Doporučená akce

Kvůli změně velikosti formulářů a ovládacích prvků se ujistěte, že se vaše aplikace vykresluje správně.

Chcete-li zachovat původní písmo, nastavte výchozí písmo formuláře na hodnotu `Microsoft Sans Serif 8 pt` . Například:

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

#### Affected APIs

- Not detectable via API analysis

-->
