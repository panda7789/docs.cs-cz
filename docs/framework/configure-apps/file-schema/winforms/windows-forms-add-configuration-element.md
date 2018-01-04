---
title: "Přidejte konfigurační prvek Windows Forms"
ms.custom: 
ms.date: 04/07/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Forms Add configuration element
- configuring Windows Forms applications
ms.assetid: 3e3e04de-99d1-4658-b716-44cb669d9589
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 331b2238ae87776938422484d34bb68b4653a56e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="windows-forms-add-configuration-element"></a>Přidejte konfigurační prvek Windows Forms

`<add>` Element přidá předdefinované klíč, který určuje, jestli vaše aplikace formuláře Windows podporuje funkce přidané do aplikace Windows Forms rozhraní .NET Framework 4.7 nebo novější.

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
| `key`     | Požadovaný atribut. Předdefinované klíče název, který odpovídá konkrétní přizpůsobitelné funkce Windows Forms. |
| `value`   | Požadovaný atribut. Hodnota pro přiřazení `key`. |

### <a name="key-attribute-names-and-associated-values"></a>`key`názvy atributů a přidružené hodnoty

| `key`Jméno | Hodnoty | Popis |
| ---------- | ------ | ----------- |
| "AnchorLayout.DisableSinglePassControlScaling" | "true" &#124;" false" | Určuje, zda jsou v jednom průchodu škálovat ukotvené ovládací prvky. "true" zakážete jeden předat škálování; jinak hodnota false. Najdete v části "Jedním předat škálování" v [poznámky](#Remarks) Další informace. |
| "DpiAwareness" | "PerMonitorV2" &#124;" false" | Určuje, zda je aplikace využívající technologii DPI. Nastavit klíč k "PerMonitorV2" pro podporu sledování bodů na palec; jinak nastavte ji na hodnotu "false". Sledování bodů na PALEC je funkce přihlášení; Abyste mohli využívat Windows Forms vysoké DPI podpory, byste měli nastavit jeho hodnotu na "PerMonitorV2". Najdete v článku [poznámky](#remarks) části Další informace. |
| "CheckedListBox.DisableHighDpiImprovements" | "true" &#124;" false" | Určuje, zda <xref:System.Windows.Forms.CheckedListBox> ovládací prvek využívá výhod škálování a rozložení vylepšení 4.7 rozhraní .NET Framework. "true" pro vyjádření výslovného nesouhlasu caling a rozložení vylepšení; jinak, "Nepravda". |
| "DataGridView.DisableHighDpiImprovements" | "true" &#124;" false" | Určuje, zda <xref:System.Windows.Forms.DataGridView> řízení škálování a rozložení vylepšení 4.7 rozhraní .NET Framework. "true" pro vyjádření výslovného nesouhlasu sledování bodů na PALEC; "false" jinak. |
| "DisableDpiChangedMessageHandling" | "true" &#124;" false" | "true" pro vyjádření výslovného nesouhlasu přijetí zprávy týkající se DPI škálování změny; "false" jinak. Najdete v článku [poznámky](#remarks) části Další informace. |
| "EnableWindowsFormsHighDpiAutoResizing" | "true" &#124;" false" | Určuje, zda aplikace Windows Forms velikost automaticky z důvodu změn Škálování DPI. "true" Povolit Automatická změna velikosti; jinak hodnota false. |
| "Form.DisableSinglePassControlScaling" | "true" &#124;" false" | Určuje, zda <xref:System.Windows.Forms.Form> bude změněno měřítko při jednom průchodu. "true" zakážete jednoho průchodu škálování; jinak hodnota false. Najdete v části "Jedním předat škálování" v [poznámky](#Remarks) Další informace. |
| "MonthCalendar.DisableSinglePassControlScaling" | "true" &#124;" false" | Určuje, zda <xref:System.Windows.Forms.MonthCalendar> ovládací prvek je škálovat při jednom průchodu. "true" zakážete jednoho průchodu škálování; jinak hodnota false. Najdete v části "Jedním předat škálování" v [poznámky](#Remarks) Další informace. |
| "Toolstrip.DisableHighDpiImprovements" | "true" &#124;" false" | Určuje, zda <xref:System.Windows.Forms.ToolStrip> ovládací prvek využívá výhod škálování a rozložení vylepšení 4.7 rozhraní .NET Framework. "true" pro vyjádření výslovného nesouhlasu sledování bodů na PALEC; "false" jinak. |

### <a name="child-elements"></a>Podřízené prvky

Žádné

### <a name="parent-elements"></a>Nadřazené prvky

| Prvek | Popis |
| ------- | ----------- |
| [`<System.Windows.Forms.ApplicationConfigurationSection>`](../../../../../docs/framework/configure-apps/file-schema/winforms/index.md) | Konfiguruje podporu pro nové funkce aplikace Windows Forms. |

## <a name="a-nameremarks--remarks"></a><a name="remarks" />Poznámky

Od verze 4.7 rozhraní .NET Framework, `<System.Windows.Forms.ApplicationConfigurationSection>` element umožňuje nakonfigurovat aplikace Windows Forms chcete využít výhod funkce přidané v posledních verzích rozhraní .NET Framework. 

`<System.Windows.Forms.ApplicationConfigurationSection>` Element lze přidat jeden nebo více podřízených `<add>` prvky, z nichž každý definuje konkrétní konfigurační nastavení.  

Přehled podpory systému Windows Forms vysoké DPI, najdete v tématu [vysoké DPI podporují ve Windows Forms](../../../../../docs/framework/winforms/high-dpi-support-in-windows-forms.md).

### <a name="dpiawareness"></a>DpiAwareness

Windows Forms aplikace, které běží v systému Windows, počínaje systémem Windows 10 Creators Edition a cílové verze rozhraní .NET Framework, počínaje rozhraní .NET Framework 4.7 lze nakonfigurovat, aby využívat vysoké DPI vylepšení byla zavedená v rozhraní .NET Framework 4.7. Mezi ně patří:

- Podpora pro dynamické DPI scénáře, ve kterých uživatel změní Multi-Factor DPI nebo škálování po byla spuštěna aplikace Windows Forms.

- Ovládací prvky vylepšení v oblasti škálování a rozložení počtu Windows Forms, jako například <xref:System.Windows.Forms.MonthCalendar> řízení a <xref:System.Windows.Forms.CheckedListBox> ovládacího prvku. 

Vysoká sledování bodů na PALEC je funkce přihlášení; ve výchozím nastavení má hodnotu `DpiAwareness` je `false`. Se můžete rozhodnout do Windows Forms podpora pro sledování bodů na PALEC nastavením hodnoty tohoto klíče na `PerMonitorV2` v konfiguračním souboru aplikace. Pokud je povoleno sledování bodů na PALEC, jsou také povoleny všechny jednotlivé funkce DPI. Mezi ně patří:

- DPI změnit zprávy, které jsou řízeny `DisableDpiChangedMessageHandling` klíč.

- Dynamické DPI podpory, které řídí `EnableWindowsFormsHighDpiAutoResizing` klíč.

- Jednoho průchodu řízení škálování, které řídí `Form.DisableSinglePassControlScaling` pro jednotlivé <xref:System.Windows.Forms.Form> ovládací prvky, pomocí `AnchorLayout.DisableSinglePassControlScaling` klíčů pro ovládací prvky ukotvené a podle `MonthCalendar.DisableSinglePassControlScaling` klíče pro <xref:System.Windows.Forms.MonthCalendar> ovládací prvek 

- Vysoké DPI škálování a rozložení vylepšení, které řídí `CheckListBox.DisableHighDpiImprovements` klíče pro <xref:System.Windows.Forms.CheckedListBox> řídit, pomocí `DataGridView.DisableHighDpiImprovements` klíče pro <xref:System.Windows.Forms.DataGridView> ovládací prvek a `Toolstrip.DisableHighDpiImprovements` klíče pro <xref:System.Windows.Forms.ToolStrip> ovládací prvek.  

Jeden výchozí výslovný souhlas nastavení zadat nastavením `DpiAwareness` k `PerMonitorV2` je obecně dostačující pro nové aplikace Windows Forms. Však můžete lze pak vyjádření výslovného nesouhlasu s jednotlivých vysoké vylepšení DPI přidáním odpovídající klíč do konfiguračního souboru aplikace. Abyste mohli využívat všechny nové featuers DPI kromě podpory dynamického DPI, například by přidejte následující konfigurační soubor aplikace:

```xml
<System.Windows.Forms.ApplicationConfigurationSection>
   <add key="DpiAwareness" value="PerMonitorV2" />
   <--! Disable dynamic DPI support -->
   <add key="EnableWindowsFormsHighDpiAutoResizing" value="false" />
</System.Windows.Forms.ApplicationConfigurationSection>
```
Obvykle můžete vyjádření výslovného nesouhlasu s konkrétní funkci vzhledem k tomu, že jste se rozhodli ji zpracovat prostřednictvím kódu programu.

Další informace o díky podpora vysoké DPI v aplikacích Windows Forms, najdete v části [vysoké DPI podporují ve Windows Forms](../../../../../docs/framework/winforms/high-dpi-support-in-windows-forms.md).
 
### <a name="disabledpichangedmessagehandling"></a>DisableDpiChangedMessageHandling

Od verze 4.7 rozhraní .NET Framework, ovládací prvky Windows Forms vyvolat určitý počet událostí související se změny v DPI škálování. Patří mezi ně <xref:System.Windows.Forms.Control.DpiChangedAfterParent>, <xref:System.Windows.Forms.Control.DpiChangedBeforeParent>, a <xref:System.Windows.Forms.Form.DpiChanged> události. Hodnota `DisableDpiChangedMessageHandling` klíč určuje, zda tyto události jsou vyvolány v aplikaci Windows Forms. 

### <a name="single-pass-scaling"></a>Škálování jednoho průchodu

Jeden nebo více pass škálování vliv dosahovaný odezvy uživatelského rozhraní a vzhled prvků uživatelského rozhraní, jak se škálovat. Od verze 4.7 rozhraní .NET Framework, Windows Forms používá jednom průchodu škálování. V předchozích verzích rozhraní .NET Framework škálování probíhalo prostřednictvím více úpravami, které způsobila některé ovládací prvky měnit jejich velikost více než bylo nezbytné. Škálování jednoho průchodu jenom je třeba zakázat Pokud vaše aplikace závisí na staré chování.  

## <a name="see-also"></a>Viz také
 
[Windows Forms konfigurační oddíl](../../../../../docs/framework/configure-apps/file-schema/winforms/index.md)   
[Podpora vysoké DPI ve Windows Forms](../../../../../docs/framework/winforms/high-dpi-support-in-windows-forms.md)
