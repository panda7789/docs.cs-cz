---
ms.openlocfilehash: b0c4e9617677cf95e3a059b57f3d50ddfb072f4a
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/14/2020
ms.locfileid: "75936993"
---
### <a name="default-control-font-changed-to-segoe-ui-9-pt"></a>Výchozí písmo ovládacího prvku se změnilo na Segoe UI 9 bodů.

#### <a name="change-description"></a>Popis změny

V .NET Framework byla vlastnost <xref:System.Windows.Forms.Control.DefaultFont?displayProperty=nameWithType> nastavena na `Microsoft Sans Serif 8 pt`. Následující obrázek ukazuje okno, které používá výchozí písmo.

![Výchozí písmo ovládacího prvku v .NET Framework](~/docs/images/core-changes/windowsforms/control-defaultfont-changed/defaultfont-framework.png)

Počínaje platformou .NET Core 3,0 je výchozí písmo nastavené na `Segoe UI 9 pt` (stejné písmo jako <xref:System.Drawing.SystemFonts.MessageBoxFont?displayProperty=nameWithType>). V důsledku této změny mají formuláře a ovládací prvky velikost přibližně 27% větší, než je větší velikost nového výchozího písma. Příklad:

![Výchozí písmo ovládacího prvku v .NET Core](~/docs/images/core-changes/windowsforms/control-defaultfont-changed/defaultfont-core.png)

Tato změna byla provedena v souladu s [pokyny pro uživatelské prostředí systému Windows (UX)](/windows/win32/uxguide/vis-fonts#fonts-and-colors).

#### <a name="version-introduced"></a>Představená verze

3,0

#### <a name="recommended-action"></a>Doporučená akce

Kvůli změně velikosti formulářů a ovládacích prvků se ujistěte, že se vaše aplikace vykresluje správně.

Chcete-li zachovat původní písmo, nastavte výchozí písmo formuláře na `Microsoft Sans Serif 8 pt`. Příklad:

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
