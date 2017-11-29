---
title: "Atributy nastavení aplikace"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- application settings [Windows Forms], attributes
- attributes [Windows Forms], application settings
- wrapper classes [Windows Forms], application settings
ms.assetid: 53caa66c-a9fb-43a5-953c-ad092590098d
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 1879ac6704619092c4c0d9cd6fab0356ea07a13d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="application-settings-attributes"></a>Atributy nastavení aplikace
Architektura nastavení aplikace obsahuje mnoho atributů, které mohou být použity buď obálkovou třídu nastavení aplikace nebo jeho jednotlivé vlastnosti. Tyto atributy se zkontrolují v době běhu aplikace nastavení infrastruktury, často konkrétně poskytovatel nastavení, aby bylo možné přizpůsobit funguje stanovené potřebám vlastní obálky.  
  
 Následující tabulka obsahuje seznam atributy, které mohou být použity pro obálkovou třídu nastavení aplikace a tato třída jednotlivé vlastnosti. Podle definice pouze atribut jeden obor –**UserScopedSettingAttribute** nebo **atribut ApplicationScopedSettingAttribute**– musí použít u každého nastavení vlastností.  
  
> [!NOTE]
>  Vlastní nastavení poskytovatele, odvozené od <xref:System.Configuration.SettingsProvider> třídy, je potřeba jenom rozpoznat následující tři atributy: **atribut ApplicationScopedSettingAttribute**, **UserScopedSettingAttribute**, a **DefaultSettingValueAttribute**.  
  
|Atribut|cíl|Popis|  
|---------------|------------|-----------------|  
|<xref:System.Configuration.SettingsProviderAttribute>|Obě|Určuje krátký název poskytovatele nastavení chcete použít pro trvalost.<br /><br /> Pokud je tento atribut není zadaný, výchozí zprostředkovatel <xref:System.Configuration.LocalFileSettingsProvider>, předpokládá se.|  
|<xref:System.Configuration.UserScopedSettingAttribute>|Obě|Definuje vlastnost jako nastavení uživatelských aplikací.|  
|<xref:System.Configuration.ApplicationScopedSettingAttribute>|Obě|Definuje vlastnost jako nastavení aplikace s rozsahem aplikace.|  
|<xref:System.Configuration.DefaultSettingValueAttribute>|Vlastnost|Určuje řetězec, který lze deserializovat zprostředkovatelem do pevně výchozí hodnoty pro tuto vlastnost.<br /><br /> <xref:System.Configuration.LocalFileSettingsProvider> Nevyžaduje, aby tento atribut a přepíše libovolná hodnota zadaná tímto atributem Pokud je hodnota nenastavili jako trvalé.|  
|<xref:System.Configuration.SettingsDescriptionAttribute>|Vlastnost|Poskytuje popisný test pro individuální nastavení, používá primárně nástroje pro spuštění a návrhu.|  
|<xref:System.Configuration.SettingsGroupNameAttribute>|Třída|Poskytuje explicitní název pro skupinu nastavení. Pokud tento atribut nebyl nalezen, <xref:System.Configuration.ApplicationSettingsBase> používá název třídy obálku.|  
|<xref:System.Configuration.SettingsGroupDescriptionAttribute>|Třída|Poskytuje popisný testu pro skupinu nastavení, používá primárně nástroje pro spuštění a návrhu.|  
|<xref:System.Configuration.SettingsManageabilityAttribute>|Obě|Určuje nula nebo více možností správy služeb, které by měly být zadané nastavení skupina nebo vlastnost. Jsou k dispozici služby popsaného <xref:System.Configuration.SettingsManageability> výčtu.|  
|<xref:System.Configuration.SpecialSettingAttribute>|Vlastnost|Označuje, že nastavení patří do speciální předdefinované kategorie, jako je například připojovací řetězec, která navrhuje speciální zpracování zprostředkovatelem nastavení. Jsou definovány předdefinovaných kategorií pro tento atribut <xref:System.Configuration.SpecialSetting> výčtu.|  
|<xref:System.Configuration.SettingsSerializeAsAttribute>|Obě|Určuje upřednostňovaný serializace mechanismus pro nastavení skupina nebo vlastnost. Mechanismy dostupné serializace jsou definovány <xref:System.Configuration.SettingsSerializeAs> výčtu.|  
|<xref:System.Configuration.NoSettingsVersionUpgradeAttribute>|Vlastnost|Určuje, že nastavení poskytovatele měli vypnout všechny funkce upgradu aplikace pro vlastnost označena.|  
  
 *Třída* udává, že atribut lze použít pouze pro třídu obálky nastavení aplikace. *Vlastnost* označuje, že atribut může být použité jenom nastavení vlastnosti. *Obě* udává, že atribut lze použít buď úrovni.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Configuration.ApplicationSettingsBase>  
 <xref:System.Configuration.SettingsProvider>  
 [Architektura nastavení aplikace](../../../../docs/framework/winforms/advanced/application-settings-architecture.md)  
 [Postupy: vytvoření nastavení aplikace](http://msdn.microsoft.com/en-us/53b3af80-1c02-4e35-99c6-787663148945)
