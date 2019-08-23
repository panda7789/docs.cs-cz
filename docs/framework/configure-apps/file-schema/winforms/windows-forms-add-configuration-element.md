---
title: model Windows Forms přidat element konfigurace
ms.date: 04/07/2017
helpviewer_keywords:
- Windows Forms Add configuration element
- configuring Windows Forms applications
ms.assetid: 3e3e04de-99d1-4658-b716-44cb669d9589
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cb607af0933ea64b7d67f8ed082ffce6e7d21f51
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69913066"
---
# <a name="windows-forms-add-configuration-element"></a>model Windows Forms přidat element konfigurace

`<add>` Element přidá předdefinovaný klíč, který určuje, zda vaše aplikace Windows Form podporuje funkce přidané do aplikace model Windows Forms v .NET Framework 4,7 nebo novějším.

## <a name="syntax"></a>Syntaxe

```xml
<System.Windows.Forms.ApplicationConfigurationSection>
  <add key="key-name" value="key-value" />
</System.Windows.Forms.ApplicationConfigurationSection>
```

## <a name="attributes-and-elements"></a>Atributy a elementy

Následující části popisují atributy, podřízené prvky a nadřazené prvky.

### <a name="attributes"></a>Atributy

| Atribut | Popis |
| --------- | ----------- |
| `key`     | Požadovaný atribut. Předdefinovaný název klíče, který odpovídá konkrétní funkci přizpůsobitelné model Windows Forms. |
| `value`   | Požadovaný atribut. Hodnota, kterou chcete přiřadit `key`. |

### <a name="key-attribute-names-and-associated-values"></a>`key`názvy atributů a přidružené hodnoty

| `key`Jméno | Hodnoty | Popis |
| ---------- | ------ | ----------- |
| "AnchorLayout.DisableSinglePassControlScaling" | "true"&#124;"false" | Označuje, zda jsou ukotvené ovládací prvky v jednom průchodu škálované. "true" pro zakázání rozšíření Single Pass. v opačném případě false. Další informace najdete v části "jednotné průchodové škálování [](#remarks) " v komentářích. |
| "DpiAwareness" | "PerMonitorV2"&#124;"false" | Určuje, zda je aplikace zohledňující rozlišení DPI. Nastavte klíč na "PerMonitorV2", aby se podporovalo sledování dpi; v opačném případě ho nastavte na false. Sledování DPI je funkce výslovného souhlasu; Pokud chcete využít výhod model Windows Forms "vysokému rozlišení DPI, měli byste nastavit jeho hodnotu na" PerMonitorV2 ". Další informace najdete v části [poznámky](#remarks) . |
| "CheckedListBox. DisableHighDpiImprovements" | "true"&#124;"false" | Určuje, zda <xref:System.Windows.Forms.CheckedListBox> ovládací prvek využívá vylepšení škálování a rozložení zavedené v .NET Framework 4,7. "true", chcete-li se odhlásit z vylepšení škálování a rozložení; v opačném případě "false". |
| "DataGridView. DisableHighDpiImprovements" | "true"&#124;"false" | Určuje, zda <xref:System.Windows.Forms.DataGridView> jsou vylepšení škálování a rozložení ovládacího prvku představena v .NET Framework 4,7. "true" pro výslovný souhlas s vědomím DPI; "false" jinak. |
| "DisableDpiChangedMessageHandling" | "true"&#124;"false" | "true" pro odsouhlasení přijímání zpráv souvisejících se změnami škálování DPI; "false" jinak. Další informace najdete v části [poznámky](#remarks) . |
| "EnableWindowsFormsHighDpiAutoResizing" | "true"&#124;"false" | Určuje, zda se automaticky změní velikost aplikace model Windows Forms z důvodu změny měřítka DPI. "true" pro povolení automatické změny velikosti; v opačném případě false. |
| "Form. DisableSinglePassControlScaling" | "true"&#124;"false" | Označuje, zda <xref:System.Windows.Forms.Form> se v jednom průchodu škáluje. "true" pro zákaz škálování s jedním průchodem; v opačném případě false. Další informace najdete v části "jednotné průchodové škálování [](#remarks) " v komentářích. |
| "MonthCalendar. DisableSinglePassControlScaling" | "true"&#124;"false" | Označuje, zda <xref:System.Windows.Forms.MonthCalendar> je ovládací prvek v jednom průchodu zvětšený. "true" pro zákaz škálování s jedním průchodem; v opačném případě false. Další informace najdete v části "jednotné průchodové škálování [](#remarks) " v komentářích. |
| "ToolStrip. DisableHighDpiImprovements" | "true"&#124;"false" | Určuje, zda <xref:System.Windows.Forms.ToolStrip> ovládací prvek využívá vylepšení škálování a rozložení zavedené v .NET Framework 4,7. "true" pro výslovný souhlas s vědomím DPI; "false" jinak. |

### <a name="child-elements"></a>Podřízené prvky

Žádné

### <a name="parent-elements"></a>Nadřazené prvky

| Prvek | Popis |
| ------- | ----------- |
| [`<System.Windows.Forms.ApplicationConfigurationSection>`](index.md) | Nakonfiguruje podporu pro nové funkce aplikace model Windows Forms. |

## <a name="remarks"></a>Poznámky

Počínaje .NET Framework 4,7 `<System.Windows.Forms.ApplicationConfigurationSection>` element umožňuje nakonfigurovat model Windows Forms aplikace, aby využívaly výhody funkcí přidaných v posledních verzích .NET Framework.

Element umožňuje přidat jeden nebo více podřízených `<add>` elementů, z nichž každý definuje konkrétní nastavení konfigurace. `<System.Windows.Forms.ApplicationConfigurationSection>`

Přehled model Windows Forms podpory vysokého rozlišení DPI najdete v tématu [Podpora vysokého počtu dpi v model Windows Forms](../../../winforms/high-dpi-support-in-windows-forms.md).

### <a name="dpiawareness"></a>DpiAwareness

Model Windows Forms aplikace, které běží na verzích Windows počínaje verzí Windows 10 Creators Edition a cílové verze .NET Framework počínaje .NET Framework 4,7, se dají nakonfigurovat tak, aby využívaly vylepšení vysokého rozlišení DPI, které přináší .NET Framework 4,7. Zde jsou některé z nich:

- Podpora pro scénáře dynamického rozlišení DPI, ve kterých uživatel po spuštění model Windows Forms aplikace změní faktor DPI nebo měřítko.

- Vylepšení škálování a rozložení mnoha model Windows Formsch ovládacích prvků, jako jsou <xref:System.Windows.Forms.MonthCalendar> ovládací prvky <xref:System.Windows.Forms.CheckedListBox> a ovládací prvek.

Zvyšování vysokého rozlišení DPI je funkce výslovného souhlasu; ve výchozím nastavení `DpiAwareness` je `false`hodnota. Můžete se rozhodnout, že model Windows Forms ' podpora pro sledování dpi nastavením hodnoty tohoto klíče do `PerMonitorV2` konfiguračního souboru aplikace. Pokud je zapnuté sledování DPI, povolí se i všechny jednotlivé funkce DPI. Zde jsou některé z nich:

- DPI změněné zprávy, které jsou ovládány `DisableDpiChangedMessageHandling` klíčem.

- Podpora dynamického dpi, která je ovládána `EnableWindowsFormsHighDpiAutoResizing` klíčem.

- Škálování ovládacího prvku `Form.DisableSinglePassControlScaling` s jedním předáním, které je ovládáno pro jednotlivé <xref:System.Windows.Forms.Form> ovládací prvky, `AnchorLayout.DisableSinglePassControlScaling` klíčem `MonthCalendar.DisableSinglePassControlScaling` pro ukotvené <xref:System.Windows.Forms.MonthCalendar> ovládací prvky a klíčem pro ovládací prvek

- Vylepšení vysokého měřítka a rozložení dpi, která jsou ovládána `CheckListBox.DisableHighDpiImprovements` klíčem <xref:System.Windows.Forms.CheckedListBox> pro ovládací prvek, `Toolstrip.DisableHighDpiImprovements` `DataGridView.DisableHighDpiImprovements` klíčem <xref:System.Windows.Forms.DataGridView> ovládacího prvku a klíčem pro <xref:System.Windows.Forms.ToolStrip> ovládací prvek.

Jedno výchozí nastavení pro výslovný souhlas poskytované nastavením `DpiAwareness` na `PerMonitorV2` je obecně dostačující pro nové aplikace model Windows Forms. Nicméně můžete vyjádřit výslovný souhlas s individuálními vylepšeními vysokého rozlišení DPI přidáním odpovídajícího klíče do konfiguračního souboru aplikace. Chcete-li například využít výhod všech nových funkcí DPI kromě podpory dynamického DPI, přidejte do konfiguračního souboru aplikace následující:

```xml
<System.Windows.Forms.ApplicationConfigurationSection>
   <add key="DpiAwareness" value="PerMonitorV2" />
   <!-- Disable dynamic DPI support -->
   <add key="EnableWindowsFormsHighDpiAutoResizing" value="false" />
</System.Windows.Forms.ApplicationConfigurationSection>
```

Obvykle se odhlásíte od konkrétní funkce, protože jste se rozhodli ji programově zpracovat.

Další informace o využití vysoké podpory DPI v aplikacích model Windows Forms najdete v tématu [Podpora vysokého počtu dpi v model Windows Forms](../../../winforms/high-dpi-support-in-windows-forms.md).

### <a name="disabledpichangedmessagehandling"></a>DisableDpiChangedMessageHandling

Počínaje .NET Framework 4,7 model Windows Forms ovládací prvky vyvolávají množství událostí souvisejících se změnami v měřítku DPI. Mezi ně patří <xref:System.Windows.Forms.Control.DpiChangedAfterParent>události <xref:System.Windows.Forms.Control.DpiChangedBeforeParent>, a <xref:System.Windows.Forms.Form.DpiChanged> . Hodnota `DisableDpiChangedMessageHandling` klíče určuje, zda jsou tyto události vyvolány v aplikaci model Windows Forms.

### <a name="single-pass-scaling"></a>Škálování s jedním průchodem

Škálování jednoho nebo více průchodů ovlivňuje vnímanou odezvu uživatelského rozhraní a vizuální vzhled prvků uživatelského rozhraní, když se škálují. Počínaje .NET Framework 4,7 používá model Windows Forms škálování Single Pass. V předchozích verzích .NET Framework bylo škálování provedeno prostřednictvím několika průchodů, což způsobilo, že některé ovládací prvky mají větší velikost, než bylo nutné. Škálování v jednom průchodu by mělo být zakázané, jenom když vaše aplikace závisí na starém chování.

## <a name="see-also"></a>Viz také:

- [Konfigurační oddíl pro model Windows Forms](index.md)
- [Podpora vysokého rozlišení DPI v model Windows Forms](../../../winforms/high-dpi-support-in-windows-forms.md)
