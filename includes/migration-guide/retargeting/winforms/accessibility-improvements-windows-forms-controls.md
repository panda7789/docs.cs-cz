---
ms.openlocfilehash: c8e1c91f4fee8aa896b6617c815fe2a4b6d22f2a
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614573"
---
### <a name="accessibility-improvements-in-windows-forms-controls"></a>Vylepšení usnadnění v ovládacích prvcích model Windows Forms

#### <a name="details"></a>Podrobnosti

Model Windows Forms vylepšuje, jak funguje s technologiemi usnadnění, aby lépe podporovaly model Windows Forms zákazníky. Mezi ně patří následující změny počínaje .NET Framework 4.7.1:

- Změny pro zlepšení zobrazení v režimu Vysoký kontrast.
- Změny pro zlepšení prostředí prohlížeče vlastností. Mezi vylepšení prohlížeče vlastností patří:
- Lepší navigace pomocí klávesnice v různých oknech pro výběr rozevíracího seznamu.
- Byla snížena nepotřebná zastavení tabulátoru.
- Lepší vytváření sestav typů ovládacích prvků.
- Vylepšené chování Předčítání.
- Změny pro implementaci chybějících vzorů usnadnění uživatelského rozhraní v ovládacích prvcích.

#### <a name="suggestion"></a>Návrh

**Jak vyjádřit nebo odhlásit tyto změny** Aby aplikace mohla tyto změny využívat, musí běžet na .NET Framework 4.7.1 nebo novějším. Aplikace může tyto změny využít v jednom z následujících způsobů:

- Zkompiluje se znovu a zacílí na .NET Framework 4.7.1. Tyto změny přístupnosti jsou ve výchozím nastavení povolené v aplikacích model Windows Forms, které cílí na .NET Framework 4.7.1 nebo novějším.
- Výslovný se ze starší verze chování přístupnosti přidáním následujícího [přepínače AppContext](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) do `<runtime>` oddílu souboru app.config a jeho nastavením na `false` , jak ukazuje následující příklad.

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
  <startup>
    <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.7"/>
  </startup>
  <runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true/false;key2=true/false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false" />
  </runtime>
</configuration>
```

Aplikace, které cílí na .NET Framework 4.7.1 nebo novější a chtějí zachovat starší funkce usnadnění, se můžou přihlásit k používání starších funkcí pro usnadnění přístupu tím, že explicitně nastaví tento přepínač AppContext na `true` .<p/>Přehled automatizace uživatelského rozhraní najdete v tématu [Přehled automatizace uživatelského rozhraní](~/docs/framework/ui-automation/ui-automation-overview.md).<p/>**Přidání podpory pro vzory a vlastnosti automatizace uživatelského rozhraní**<br/>Klienti přístupnosti můžou využít nové funkce usnadnění přístupnosti WinForms pomocí běžných veřejně popsaných vzorů volání. Tyto vzory nejsou specifické pro WinForms. Například klienti přístupnosti můžou volat metodu QueryInterface na rozhraní IAccessible (MAAS) a získat tak rozhraní IServiceProvider. Pokud je toto rozhraní k dispozici, mohou klienti použít metodu QueryService pro vyžádání rozhraní IAccessibleEx. Další informace najdete v tématu [použití IAccessibleEx z klienta](https://docs.microsoft.com/windows/desktop/WinAuto/using-iaccessibleex-from-a-client). Počínaje .NET Framework 4.7.1, IServiceProvider a [IAccessibleEx](https://docs.microsoft.com/windows/desktop/WinAuto/iaccessibleex) (v případě potřeby) jsou k dispozici pro objekty usnadnění přístupnosti WinForms.<p/>.NET Framework 4.7.1 přidává podporu následujících vzorů a vlastností automatizace uživatelského rozhraní:

- <xref:System.Windows.Forms.ToolStripSplitButton> <xref:System.Windows.Forms.ComboBox> Ovládací prvky a podporují [model rozbalení a sbalení](~/docs/framework/ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md).
- <xref:System.Windows.Forms.ToolStripMenuItem>Ovládací prvek má hodnotu vlastnosti [ControlType](~/docs/framework/ui-automation/ui-automation-support-for-the-menubar-control-type.md) <xref:System.Windows.Automation.ControlType.MenuItem?displayProperty=nameWithType> .
- <xref:System.Windows.Forms.ToolStripItem>Ovládací prvek podporuje <xref:System.Windows.Automation.AutomationElement.NameProperty> vlastnost a vzorek pro[rozbalení a sbalení](~/docs/framework/ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md).
- <xref:System.Windows.Forms.ToolStripDropDownItem>Ovládací prvek podporuje <xref:System.Windows.Forms.AccessibleEvents> označení StateChange a NameChange – při rozbalení nebo sbalení rozevíracího seznamu.
- <xref:System.Windows.Forms.ToolStripDropDownButton>Ovládací prvek má hodnotu vlastnosti [ControlType](~/docs/framework/ui-automation/ui-automation-support-for-the-menubar-control-type.md) <xref:System.Windows.Automation.ControlType.MenuItem?displayProperty=nameWithType> .
- <xref:System.Windows.Forms.DataGridViewCheckBoxCell>Ovládací prvek podporuje <xref:System.Windows.Automation.TogglePattern> .
- <xref:System.Windows.Forms.NumericUpDown> <xref:System.Windows.Forms.DomainUpDown> Ovládací prvky a podporují <xref:System.Windows.Automation.AutomationElement.NameProperty> vlastnost [ControlType](~/docs/framework/ui-automation/ui-automation-support-for-the-spinner-control-type.md) <xref:System.Windows.Automation.ControlType.Spinner?displayProperty=nameWithType> .</p>
**Vylepšení ovládacího prvku PropertyGrid** .NET Framework 4.7.1 přidává k ovládacímu prvku PropertyBrowser následující vylepšení:

- Tlačítko **Podrobnosti** v chybovém dialogovém okně, které se zobrazí, když uživatel zadá nesprávnou hodnotu v <xref:System.Windows.Forms.PropertyGrid> ovládacím prvku, podporuje [vzor pro rozbalení a sbalení](~/docs/framework/ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md), oznámení o změně stavu a názvu a vlastnost [ControlType](~/docs/framework/ui-automation/ui-automation-support-for-the-menubar-control-type.md) s hodnotou <xref:System.Windows.Automation.ControlType.MenuItem?displayProperty=nameWithType> .
- Podokno zpráva zobrazené po rozbalení tlačítka **podrobností** v chybovém dialogovém okně je nyní přístupné z klávesnice a umožňuje programu Narrator oznámit obsah chybové zprávy.
- <xref:System.Windows.Forms.AccessibleRole>Řádky v <xref:System.Windows.Forms.PropertyGrid> ovládacím prvku se změnily z &quot; řádku &quot; na &quot; buňku &quot; . Buňka se mapuje na UIA ControlType &quot; DataItem &quot; , což umožňuje podpoře příslušných klávesových zkratek a oznámení mluveného komentáře.
- <xref:System.Windows.Forms.PropertyGrid>Řádky ovládacího prvku, které reprezentují položky záhlaví, pokud <xref:System.Windows.Forms.PropertyGrid> má ovládací prvek <xref:System.Windows.Forms.PropertyGrid.PropertySort> vlastnost nastavenou na <xref:System.Windows.Forms.PropertySort.Categorized?displayProperty=nameWithType> hodnotu vlastnosti [ControlType](~/docs/framework/ui-automation/ui-automation-support-for-the-menubar-control-type.md) <xref:System.Windows.Automation.ControlType.Button?displayProperty=nameWithType> .
- <xref:System.Windows.Forms.PropertyGrid>Ovládací prvky, které reprezentují položky záhlaví, pokud <xref:System.Windows.Forms.PropertyGrid> ovládací prvek má <xref:System.Windows.Forms.PropertyGrid.PropertySort> vlastnost nastavenou na <xref:System.Windows.Forms.PropertySort.Categorized?displayProperty=nameWithType> podporu [vzoru pro rozbalení/sbalení](~/docs/framework/ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md).
- Vylepšená navigace klávesnice mezi mřížkou a panelem nástrojů nad ním Stisknutí &quot; klávesy SHIFT + TAB &quot; teď vybere první tlačítko panelu nástrojů místo celého panelu nástrojů.
- <xref:System.Windows.Forms.PropertyGrid>ovládací prvky zobrazené v režimu Vysoký kontrast nyní nakreslí obdélník výběru kolem tlačítka panelu nástrojů, které odpovídá aktuální <xref:System.Windows.Forms.PropertyGrid.PropertySort> hodnotě vlastnosti.
- <xref:System.Windows.Forms.PropertyGrid>ovládací prvky zobrazené v režimu Vysoký kontrast a s <xref:System.Windows.Forms.PropertyGrid.PropertySort> vlastností nastavenou na se <xref:System.Windows.Forms.PropertySort.Categorized?displayProperty=nameWithType> teď budou zobrazovat pozadí záhlaví kategorií ve vysoce kontrastní barvě.
- <xref:System.Windows.Forms.PropertyGrid>ovládací prvky budou lépe rozlišovat mezi položkami panelu nástrojů s fokusem a položkami panelu nástrojů, které označují aktuální hodnotu <xref:System.Windows.Forms.PropertyGrid.PropertySort> Vlastnosti. Tato oprava se skládá z Vysoký kontrast změny a změny pro jiné scénáře než Vysoký kontrast.
- <xref:System.Windows.Forms.PropertyGrid>ovládací prvky panelu nástrojů, které určují aktuální hodnotu <xref:System.Windows.Forms.PropertyGrid.PropertySort> vlastnosti <xref:System.Windows.Automation.TogglePattern> .
- Vylepšená podpora Narrator pro odlišení vybraného zarovnání ve výběru zarovnání.
- Když <xref:System.Windows.Forms.PropertyGrid> se ve formuláři zobrazí prázdný ovládací prvek, teď se zobrazí fokus tam, kde to ještě nebylo.

**Použití barev definovaných operačním systémem v motivech Vysoký kontrast**

- <xref:System.Windows.Forms.Button> <xref:System.Windows.Forms.CheckBox> Ovládací prvky a s jejich <xref:System.Windows.Forms.ButtonBase.FlatStyle> vlastností nastavenou na <xref:System.Windows.Forms.FlatStyle.System?displayProperty=nameWithType> , což je výchozí styl, nyní používají barvy definované operačním systémem v vysoký kontrast motiv, pokud je vybrán. Dříve byly barvy textu a pozadí Nekontrastní a bylo těžké je přečíst.
- <xref:System.Windows.Forms.Button> <xref:System.Windows.Forms.CheckBox> <xref:System.Windows.Forms.RadioButton> Ovládací prvky,,, <xref:System.Windows.Forms.Label> , <xref:System.Windows.Forms.LinkLabel> a <xref:System.Windows.Forms.GroupBox> s jejich <xref:System.Windows.Forms.Control.Enabled> vlastností nastavenou na **hodnotu false** používaly šedou barvu pro vykreslení textu v vysoký kontrastch motivů, což vede k nízkému kontrastu na pozadí. Nyní tyto ovládací prvky používají &quot; barvu zakázaného textu &quot; definovanou operačním systémem. Tato oprava platí pro ovládací prvky s `FlatStyle` vlastností nastavenou na jinou hodnotu než <xref:System.Windows.Forms.FlatStyle.System?displayProperty=nameWithType> . Druhé ovládací prvky jsou vykreslovány operačním systémem.
- <xref:System.Windows.Forms.DataGridView>nyní vykreslí viditelný obdélník kolem obsahu buňky, která má aktuální fokus. Dřív to nebylo v některých Vysoký kontrast motivech vidět.
- <xref:System.Windows.Forms.ToolStripMenuItem>ovládací prvky s <xref:System.Windows.Forms.ToolStripMenuItem.Enabled> vlastností nastavenou na **hodnotu false** nyní používají &quot; barvu zakázaného textu &quot; definovanou operačním systémem.
- <xref:System.Windows.Forms.ToolStripMenuItem>ovládací prvky s <xref:System.Windows.Forms.ToolStripMenuItem.Checked> vlastností nastavenou na **hodnotu true** nyní vykreslí značku zaškrtnutí v kontrastní barvě systému.  Dříve se barva značky zaškrtnutí nezměnila na dostatečnou a v Vysoký kontrastch motivech není viditelná.
Poznámka: Windows 10 změnil hodnoty pro některé systémové barvy s vysokým kontrastem. Rozhraní model Windows Forms Framework vychází z rozhraní Win32. Pro dosažení co nejlepších výsledků spusťte na nejnovější verzi Windows a přihlaste se k nejnovějším změnám operačního systému přidáním souboru App. manifest do testovací aplikace a zrušením komentáře k následujícímu kódu:

```xml
<!-- Windows 10 -->
<supportedOS Id="{8e0f7a12-bfb3-4fe8-b9a5-48fd50a15a9a}" />
```

**Vylepšená navigace klávesnicí**

- V případě <xref:System.Windows.Forms.ComboBox> , že má ovládací prvek <xref:System.Windows.Forms.ComboBox.DropDownStyle> nastaven na hodnotu <xref:System.Windows.Forms.ComboBoxStyle.DropDownList?displayProperty=nameWithType> a je prvním ovládacím prvkem v pořadí prvků ve formuláři, nyní zobrazí obdélník fokusu, když je nadřazený formulář otevřen pomocí klávesnice. Před touto změnou byl fokus klávesnice na tomto ovládacím prvku, ale ukazatel fokusu nebyl vykreslen.

**Vylepšená podpora Narrator**

- <xref:System.Windows.Forms.MonthCalendar>Ovládací prvek přidal podporu pro technologie pro usnadnění přístupu pro přístup k ovládacímu prvku, včetně možnosti, aby mohl program Narrator číst hodnotu ovládacího prvku, když předtím nemohlo být.

- <xref:System.Windows.Forms.CheckedListBox>Ovládací prvek nyní upozorní nástroj Narrator <xref:System.Windows.Forms.CheckBox.CheckState?displayProperty=nameWithType> , když došlo ke změně vlastnosti. Dříve se v programu Narrator nedostalo oznámení a v důsledku toho nebudou mít uživatelé informováni o tom, že <xref:System.Windows.Forms.CheckBox.CheckState> byla vlastnost aktualizována.
- <xref:System.Windows.Forms.LinkLabel>Ovládací prvek změnil způsob, jakým upozorňuje text na komentář k textu v ovládacím prvku. Dřív tento text oznámila dvakrát a čte &quot; &amp; &quot; symboly jako skutečný text, i když nejsou viditelné pro uživatele. Duplicitní text byl odebrán z oznámení Narrator a také z zbytečných &quot; &amp; &quot; symbolů.
- <xref:System.Windows.Forms.DataGridViewCell>Typy ovládacích prvků nyní správně hlásí stav jen pro čtení do programu Narrator a dalších technologií pro usnadnění.
- Program Narrator teď dokáže číst systémovou nabídku podřízených oken v aplikacích [více dokumentů rozhraní] ~/docs/Framework/WinForms/Advanced/Multiple-Document-Interface-MDI-Applications.MD).
- Program Narrator teď dokáže číst <xref:System.Windows.Forms.ToolStripMenuItem> ovládací prvky s <xref:System.Windows.Forms.ToolStripItem.Enabled?displayProperty=nameWithType> vlastností nastavenou na **hodnotu false**. Dříve se program Narrator nemohl soustředit na zakázané položky nabídky pro čtení obsahu.

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   | Hlavní       |
| Verze | 4,8         |
| Typ    | Změna cílení |

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

- <xref:System.Windows.Forms.ToolStripDropDownButton.CreateAccessibilityInstance?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DomainUpDown.DomainUpDownAccessibleObject.Name?displayProperty=nameWithType>
- [MonthCalendar. AccessibilityObject](xref:System.Windows.Forms.Control.AccessibilityObject)
