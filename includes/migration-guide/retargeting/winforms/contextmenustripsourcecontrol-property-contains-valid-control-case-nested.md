---
ms.openlocfilehash: 97299ddb9bee89c792ddb3d2b9c37516180996f7
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614568"
---
### <a name="contextmenustripsourcecontrol-property-contains-a-valid-control-in-the-case-of-nested-toolstripmenuitems"></a>Vlastnost ContextMenuStrip. SourceControl obsahuje platný ovládací prvek v případě vnořeného ToolStripMenuItems

#### <a name="details"></a>Podrobnosti

V .NET Framework 4.7.1 a předchozích verzích <xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType> vlastnost nesprávně vrací hodnotu null, pokud uživatel otevře nabídku z vnořených <xref:System.Windows.Forms.ToolStripMenuItem> ovládacích prvků. V .NET Framework 4.7.2 a novějším <xref:System.Windows.Forms.ContextMenuStrip.SourceControl> je vlastnost vždy nastavena na skutečný ovládací prvek zdroje.

#### <a name="suggestion"></a>Návrh

**Jak vyjádřit nebo odhlásit tyto změny** Aby aplikace mohla tyto změny využívat, musí běžet na .NET Framework 4.7.2 nebo novějším. Aplikace může tyto změny využít v jednom z následujících způsobů:

- Cílí na .NET Framework 4.7.2. Tato změna je ve výchozím nastavení povolená v aplikacích model Windows Forms, které cílí na .NET Framework 4.7.2 nebo novějším.
- Cílí na .NET Framework 4.7.1 nebo dřívější verzi a výslovný ze staršího chování přístupnosti přidáním následujícího [přepínače AppContext](https://docs.microsoft.com/dotnet/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element) do `<runtime>` oddílu app.config souboru a jeho nastavením na `false` , jak ukazuje následující příklad.

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue=false"/>
</runtime>
```

Aplikace, které cílí na .NET Framework 4.7.2 nebo novější a chtějí zachovat starší verze správy, se mohou vyjádřit k použití starší hodnoty správy zdrojového kódu explicitně nastavením tohoto přepínače AppContext na `true` .

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   | Edge        |
| Verze | 4.7.2       |
| Typ    | Změna cílení |

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

- <xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType>
