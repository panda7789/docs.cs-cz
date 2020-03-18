---
ms.openlocfilehash: b0c4e9617677cf95e3a059b57f3d50ddfb072f4a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75936993"
---
### <a name="default-control-font-changed-to-segoe-ui-9-pt"></a>Výchozí řídicí písmo změněno na Segoe UI 9 bodů

#### <a name="change-description"></a>Popis změny

V rozhraní .NET <xref:System.Windows.Forms.Control.DefaultFont?displayProperty=nameWithType> Framework byla `Microsoft Sans Serif 8 pt`vlastnost nastavena na . Na následujícím obrázku je zobrazeno okno, které používá výchozí písmo.

![Výchozí písmo ovládacího prvku v rozhraní .NET Framework](~/docs/images/core-changes/windowsforms/control-defaultfont-changed/defaultfont-framework.png)

Počínaje rozhraním .NET Core 3.0 je `Segoe UI 9 pt` výchozí písmo <xref:System.Drawing.SystemFonts.MessageBoxFont?displayProperty=nameWithType>nastaveno na (stejné písmo jako ). V důsledku této změny formuláře a ovládací prvky jsou velikosti o 27 % větší, aby se zohlednila větší velikost nového výchozího písma. Například:

![Výchozí písmo ovládacího prvku v rozhraní .NET Core](~/docs/images/core-changes/windowsforms/control-defaultfont-changed/defaultfont-core.png)

Tato změna byla provedena tak, aby byla v souladu s [pokyny pro uživatelské prostředí systému Windows (UX).](/windows/win32/uxguide/vis-fonts#fonts-and-colors)

#### <a name="version-introduced"></a>Zavedená verze

3.0

#### <a name="recommended-action"></a>Doporučená akce

Z důvodu změny velikosti formulářů a ovládacích prvků, ujistěte se, že aplikace vykreslí správně.

Chcete-li zachovat původní písmo, nastavte `Microsoft Sans Serif 8 pt`výchozí písmo formuláře na . Například:

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

Žádné.

<!--

### Affected APIs

- Not detectable via API analysis

-->
