---
title: Přidání konfiguračního prvku Windows Forms
ms.date: 04/07/2017
helpviewer_keywords:
- Windows Forms Add configuration element
- configuring Windows Forms applications
ms.assetid: 3e3e04de-99d1-4658-b716-44cb669d9589
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5cb0d058cd1ade65bfdc966819c0c41d9c1a9750
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2018
ms.locfileid: "50185989"
---
# <a name="windows-forms-add-configuration-element"></a>Přidání konfiguračního prvku Windows Forms

`<add>` Element přidá předdefinované klíč, který určuje, zda vaše aplikace pro formulář Windows podporuje funkce přidané do aplikací Windows Forms v rozhraní .NET Framework 4.7 nebo novější.

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
| `key`     | Požadovaný atribut. Předdefinované název klíče, který odpovídá konkrétní funkce s možností vlastního nastavení formuláře Windows. |
| `value`   | Požadovaný atribut. Hodnota pro přiřazení `key`. |

### <a name="key-attribute-names-and-associated-values"></a>`key` názvy atributů a přidružené hodnoty

| `key` Jméno | Hodnoty | Popis |
| ---------- | ------ | ----------- |
| "AnchorLayout.DisableSinglePassControlScaling" | "true"&#124;"false" | Určuje, zda se upraví ukotvených ovládacích prvků v jediném kroku. "true" zakážete jeden předat škálování; v opačném případě hodnota false. Naleznete v části "Jedním předat škálování" [poznámky](#Remarks) Další informace. |
| "DpiAwareness" | "PerMonitorV2"&#124;"false" | Označuje, zda je aplikace s ohledem na DPI. Nastavte klíč k "PerMonitorV2" pro podporu sledování Dpi; jinak ji nastavte na hodnotu "false". Rozpoznání nastavení dpi je přihlašovaná funkce; Abyste mohli využívat podporu vysoké rozlišení DPI Windows Forms, byste měli nastavit hodnotu na "PerMonitorV2". Zobrazit [poznámky](#remarks) části Další informace. |
| "CheckedListBox.DisableHighDpiImprovements" | "true"&#124;"false" | Určuje, zda <xref:System.Windows.Forms.CheckedListBox> ovládací prvek využívá výhod změnu měřítka a rozložení vylepšení v rozhraní .NET Framework 4.7. "true" chcete vyjádřit výslovný nesouhlas caling a rozložení vylepšení; jinak, "Nepravda". |
| "DataGridView.DisableHighDpiImprovements" | "true"&#124;"false" | Určuje, zda <xref:System.Windows.Forms.DataGridView> řídit změnu měřítka a rozložení vylepšení v rozhraní .NET Framework 4.7. "true" chcete vyjádřit výslovný nesouhlas rozpoznání nastavení dpi; "false" jinak. |
| "DisableDpiChangedMessageHandling" | "true"&#124;"false" | "true" chcete vyjádřit výslovný nesouhlas příjem zprávy týkající se DPI škálování změny. "false" jinak. Zobrazit [poznámky](#remarks) části Další informace. |
| "EnableWindowsFormsHighDpiAutoResizing" | "true"&#124;"false" | Určuje, zda aplikace modelu Windows Forms velikost automaticky z důvodu změn Škálování DPI. "true" Povolit automatickou změnu velikosti; v opačném případě hodnota false. |
| "Form.DisableSinglePassControlScaling" | "true"&#124;"false" | Určuje, zda <xref:System.Windows.Forms.Form> škálovat v jediném kroku. "true" zakážete jednoho průchodu škálování; v opačném případě hodnota false. Naleznete v části "Jedním předat škálování" [poznámky](#Remarks) Další informace. |
| "MonthCalendar.DisableSinglePassControlScaling" | "true"&#124;"false" | Určuje, zda <xref:System.Windows.Forms.MonthCalendar> ovládací prvek je škálování v jediném kroku. "true" zakážete jednoho průchodu škálování; v opačném případě hodnota false. Naleznete v části "Jedním předat škálování" [poznámky](#Remarks) Další informace. |
| "Toolstrip.DisableHighDpiImprovements" | "true"&#124;"false" | Určuje, zda <xref:System.Windows.Forms.ToolStrip> ovládací prvek využívá výhod změnu měřítka a rozložení vylepšení v rozhraní .NET Framework 4.7. "true" chcete vyjádřit výslovný nesouhlas rozpoznání nastavení dpi; "false" jinak. |

### <a name="child-elements"></a>Podřízené prvky

Žádné

### <a name="parent-elements"></a>Nadřazené prvky

| Prvek | Popis |
| ------- | ----------- |
| [`<System.Windows.Forms.ApplicationConfigurationSection>`](../../../../../docs/framework/configure-apps/file-schema/winforms/index.md) | Konfiguruje podporu pro nové funkce pro aplikace Windows Forms. |

## <a name="a-nameremarks--remarks"></a><a name="remarks" /> Poznámky

Od verze rozhraní .NET Framework 4.7, `<System.Windows.Forms.ApplicationConfigurationSection>` element umožňuje konfigurace aplikací Windows Forms, abyste mohli využívat funkce přidané v posledních verzích rozhraní .NET Framework. 

`<System.Windows.Forms.ApplicationConfigurationSection>` Element slouží k přidání jednoho nebo více podřízených `<add>` prvky, z nichž každý definuje konkrétní nastavení.  

Přehled podpora vysokého nastavení DPI formulářů Windows, naleznete v tématu [vysoké rozlišení DPI podporují ve Windows Forms](../../../../../docs/framework/winforms/high-dpi-support-in-windows-forms.md).

### <a name="dpiawareness"></a>DpiAwareness

Windows Forms aplikace, které jsou spuštěny pod od verze Windows 10 Creators Edition a cílová verze rozhraní .NET Framework verze Windows od verze rozhraní .NET Framework 4.7 je možné nakonfigurovat výhod vysoké rozlišení DPI vylepšení v rozhraní .NET Framework 4.7. Zde jsou některé z nich:

- Podpora pro dynamické DPI scénáře, ve kterých uživatel změní DPI nebo škálovací faktor po aplikace modelu Windows Forms byl spuštěn.

- Vylepšení ve škálování a rozložení počtu Windows Forms ovládací prvky, jako <xref:System.Windows.Forms.MonthCalendar> ovládacího prvku a <xref:System.Windows.Forms.CheckedListBox> ovládacího prvku. 

Vysoká rozpoznání nastavení dpi je přihlašovaná funkce; ve výchozím nastavení hodnotu `DpiAwareness` je `false`. Můžete se rozhodnout do Windows Forms podporu pro rozpoznání nastavení DPI tak, že nastavíte hodnotu tohoto klíče k `PerMonitorV2` v konfiguračním souboru aplikace. Pokud je povoleno sledování DPI, jsou také povoleny všechny jednotlivé funkce DPI. Zde jsou některé z nich:

- DPI změnit zprávy, které jsou řízeny `DisableDpiChangedMessageHandling` klíč.

- Dynamické DPI podpory, které řídí `EnableWindowsFormsHighDpiAutoResizing` klíč.

- Jednoho průchodu změny velikosti ovládacího prvku, který řídí `Form.DisableSinglePassControlScaling` jednotlivce <xref:System.Windows.Forms.Form> ovládací prvky podle `AnchorLayout.DisableSinglePassControlScaling` ukotvených ovládacích prvků a pomocí klíče `MonthCalendar.DisableSinglePassControlScaling` klíče pro <xref:System.Windows.Forms.MonthCalendar> ovládacího prvku 

- Vysoké rozlišení DPI změnu měřítka a rozložení vylepšení, které řídí `CheckListBox.DisableHighDpiImprovements` klíče pro <xref:System.Windows.Forms.CheckedListBox> řízení podle `DataGridView.DisableHighDpiImprovements` klíče pro <xref:System.Windows.Forms.DataGridView> ovládacího prvku a `Toolstrip.DisableHighDpiImprovements` klíče pro <xref:System.Windows.Forms.ToolStrip> ovládacího prvku.  

Jedno výchozí vyjádřit výslovný souhlas nastavení zadat nastavením `DpiAwareness` k `PerMonitorV2` obecně postačuje pro nové aplikace Windows Forms. Však můžete poté zrušit individuální vysoké rozlišení DPI vylepšení přidáním odpovídající klíč do konfiguračního souboru aplikace. Abyste mohli využívat všechny nové featuers DPI kromě podpory dynamického DPI, například by přidejte následující konfigurační soubor aplikace:

```xml
<System.Windows.Forms.ApplicationConfigurationSection>
   <add key="DpiAwareness" value="PerMonitorV2" />
   <!-- Disable dynamic DPI support -->
   <add key="EnableWindowsFormsHighDpiAutoResizing" value="false" />
</System.Windows.Forms.ApplicationConfigurationSection>
```
Obvykle Pokud se rozhodnete konkrétní funkci vzhledem k tomu, že jste se rozhodli zpracovávat prostřednictvím kódu programu.

Další informace o a současně využívat podpora vysokého nastavení DPI v aplikacích Windows Forms, naleznete v tématu [vysoké rozlišení DPI podporují ve Windows Forms](../../../../../docs/framework/winforms/high-dpi-support-in-windows-forms.md).
 
### <a name="disabledpichangedmessagehandling"></a>DisableDpiChangedMessageHandling

Od verze rozhraní .NET Framework 4.7, ovládacích prvků Windows Forms zvýšit počet událostí související se změnami v DPI škálování. Patří mezi ně <xref:System.Windows.Forms.Control.DpiChangedAfterParent>, <xref:System.Windows.Forms.Control.DpiChangedBeforeParent>, a <xref:System.Windows.Forms.Form.DpiChanged> události. Hodnota `DisableDpiChangedMessageHandling` klíč určuje, zda jsou tyto události vyvolány v aplikaci Windows Forms. 

### <a name="single-pass-scaling"></a>Škálování jednoho průchodu

Jeden nebo více pass škálování ovlivňuje ovlivnit vnímanou odezvu uživatelského rozhraní a vzhled prvky uživatelského rozhraní, jak se upraví. Od verze rozhraní .NET Framework 4.7, Windows Forms používá škálování na jednom průchodu. V předchozích verzích rozhraní .NET Framework škálování se provádí prostřednictvím více průchody, která způsobila některé ovládací prvky škálovat víc než bylo nutné. Škálování jednoho průchodu pouze je třeba zakázat Pokud vaše aplikace závisí na staré chování.  

## <a name="see-also"></a>Viz také:
 
[Konfigurační oddíl pro model Windows Forms](../../../../../docs/framework/configure-apps/file-schema/winforms/index.md)   
[Podpora vysokého nastavení DPI ve Windows Forms](../../../../../docs/framework/winforms/high-dpi-support-in-windows-forms.md)
