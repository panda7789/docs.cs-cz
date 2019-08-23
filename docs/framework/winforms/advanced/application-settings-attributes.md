---
title: Atributy nastavení aplikace
ms.date: 03/30/2017
helpviewer_keywords:
- application settings [Windows Forms], attributes
- attributes [Windows Forms], application settings
- wrapper classes [Windows Forms], application settings
ms.assetid: 53caa66c-a9fb-43a5-953c-ad092590098d
ms.openlocfilehash: b38ed931cab3a333a56dd027d5843b1c8f00dcb9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69916685"
---
# <a name="application-settings-attributes"></a>Atributy nastavení aplikace
Architektura nastavení aplikace poskytuje mnoho atributů, které lze použít buď na obálkovou třídu nastavení aplikace, nebo na její jednotlivé vlastnosti. Tyto atributy jsou zkontrolovány za běhu v infrastruktuře nastavení aplikace, často konkrétně u poskytovatele nastavení, aby bylo možné přizpůsobit jeho fungování na stanovené potřeby vlastní obálky.  
  
 V následující tabulce jsou uvedeny atributy, které lze použít na obálkovou třídu nastavení aplikace, jednotlivé vlastnosti této třídy nebo obojí. Podle definice je nutné použít pouze jeden atribut oboru –**UserScopedSettingAttribute** nebo **atribut ApplicationScopedSettingAttribute**– pro každé vlastnosti a všechna nastavení.  
  
> [!NOTE]
> Vlastní zprostředkovatel nastavení odvozený od <xref:System.Configuration.SettingsProvider> třídy je vyžadován pouze k rozpoznání následujících tří atributů: **Atribut ApplicationScopedSettingAttribute**, **UserScopedSettingAttribute**a **DefaultSettingValueAttribute**.  
  
|Atribut|Target|Popis|  
|---------------|------------|-----------------|  
|<xref:System.Configuration.SettingsProviderAttribute>|Obojí|Určuje krátký název poskytovatele nastavení, který se má použít pro trvalost.<br /><br /> Pokud tento atribut není zadán, předpokládá se výchozí zprostředkovatel <xref:System.Configuration.LocalFileSettingsProvider>.|  
|<xref:System.Configuration.UserScopedSettingAttribute>|Obojí|Definuje vlastnost jako nastavení aplikace s rozsahem uživatele.|  
|<xref:System.Configuration.ApplicationScopedSettingAttribute>|Obojí|Definuje vlastnost jako nastavení aplikace v rozsahu aplikace.|  
|<xref:System.Configuration.DefaultSettingValueAttribute>|Vlastnost|Určuje řetězec, který může poskytovatel deserializovat do pevně zakódované výchozí hodnoty pro tuto vlastnost.<br /><br /> <xref:System.Configuration.LocalFileSettingsProvider> Nepožaduje tento atribut a přepíše libovolnou hodnotu poskytnutou tímto atributem, pokud existuje hodnota, která je již trvale uložena.|  
|<xref:System.Configuration.SettingsDescriptionAttribute>|Vlastnost|Poskytuje popisný test pro individuální nastavení, který se používá hlavně v době běhu a nástroje pro návrh.|  
|<xref:System.Configuration.SettingsGroupNameAttribute>|Třída|Poskytuje explicitní název skupiny nastavení. Pokud tento atribut chybí, <xref:System.Configuration.ApplicationSettingsBase> používá název třídy obálky.|  
|<xref:System.Configuration.SettingsGroupDescriptionAttribute>|Třída|Poskytuje popisný test pro skupinu nastavení, který se používá hlavně za běhu a nástroje pro návrh v době návrhu.|  
|<xref:System.Configuration.SettingsManageabilityAttribute>|Obojí|Určuje žádnou nebo více služeb spravovatelnosti, které by měly být poskytnuty skupině nastavení nebo vlastnosti. Dostupné služby jsou popsány <xref:System.Configuration.SettingsManageability> výčtem.|  
|<xref:System.Configuration.SpecialSettingAttribute>|Vlastnost|Označuje, že nastavení patří do speciální předdefinované kategorie, jako je například připojovací řetězec, který navrhuje speciální zpracování zprostředkovatelem nastavení. Předdefinované kategorie pro tento atribut jsou definovány <xref:System.Configuration.SpecialSetting> výčtem.|  
|<xref:System.Configuration.SettingsSerializeAsAttribute>|Obojí|Určuje preferovaný mechanizmus serializace pro skupinu nastavení nebo vlastnost. Dostupné mechanismy serializace jsou definovány <xref:System.Configuration.SettingsSerializeAs> výčtem.|  
|<xref:System.Configuration.NoSettingsVersionUpgradeAttribute>|Vlastnost|Určuje, že zprostředkovatel nastavení by měl zakázat všechny funkce upgradu aplikace pro označenou vlastnost.|  
  
 *Třída* označuje, že atribut lze použít pouze pro obálkovou třídu nastavení aplikace. *Vlastnost* označuje, že atribut lze použít pouze pro vlastnosti nastavení. *Oba* označují, že atribut lze použít na obě úrovně.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Configuration.ApplicationSettingsBase>
- <xref:System.Configuration.SettingsProvider>
- [Architektura nastavení aplikace](application-settings-architecture.md)
- [Postupy: Vytvořit nastavení aplikace](how-to-create-application-settings.md)
