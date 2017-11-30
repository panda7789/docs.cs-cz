---
title: "Nastavení aplikace pro vlastní ovládací prvky"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- custom controls [Windows Forms], application settings
- application settings [Windows Forms], custom controls
ms.assetid: f44afb74-76cc-44f2-890a-44b7cdc211a1
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3f8292ac459a2943376229ef62466b0a772430dc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="application-settings-for-custom-controls"></a>Nastavení aplikace pro vlastní ovládací prvky
Musíte provést určité úlohy poskytnout vlastní ovládací prvky umožňuje zachovat nastavení aplikace, když jsou ovládací prvky jsou hostované v aplikacích třetích stran.  
  
 Většina dokumentace o funkci nastavení aplikace je zapsán za předpokladu, že vytváříte samostatné aplikace. Ale pokud vytváříte ovládací prvek, který bude hostitelem jinými vývojáři ve svých aplikacích, budete muset provést několik další kroky pro ovládací prvek pro zachování jeho nastavení správně.  
  
## <a name="application-settings-and-custom-controls"></a>Nastavení aplikace a vlastních ovládacích prvků  
 Pro ovládací prvek se správně zachovat jeho nastavení, musí zapouzdřovat proces tak, že vytvoříte vlastní vyhrazené aplikace nastavení obálkové třídy odvozené od <xref:System.Configuration.ApplicationSettingsBase>. Kromě toho musí implementovat třídu hlavní ovládacího prvku <xref:System.Configuration.IPersistComponentSettings>. Rozhraní obsahuje několik vlastností, jakož i dvě metody, <xref:System.Configuration.IPersistComponentSettings.LoadComponentSettings%2A> a <xref:System.Configuration.IPersistComponentSettings.SaveComponentSettings%2A>. Pokud přidáte vlastní ovládací prvek na formuláři pomocí **Návrhář formulářů Windows** v sadě Visual Studio, Windows Forms zavolá <xref:System.Configuration.IPersistComponentSettings.LoadComponentSettings%2A> automaticky při inicializaci ovládacího prvku; musí volat <xref:System.Configuration.IPersistComponentSettings.SaveComponentSettings%2A> sami v `Dispose` Metoda vlastního ovládacího prvku.  
  
 Kromě toho byste měli implementovat následující pořadí pro nastavení aplikace pro vlastní ovládací prvky pro práci správně v prostředí návrhu třeba v sadě Visual Studio:  
  
1.  Třída nastavení vlastní aplikaci s konstruktor, který přebírá <xref:System.ComponentModel.IComponent> jako jeden parametr. Tato třída slouží k uložení a načtení všech nastavení aplikace. Když vytvoříte novou instanci této třídy, předejte vlastního ovládacího prvku pomocí konstruktoru.  
  
2.  Vytvořit tuto třídu vlastní nastavení po ovládacího prvku byla vytvořena a umístěna ve formuláři, například v formuláře <xref:System.Windows.Forms.Form.Load> obslužné rutiny události.  
  
 Pokyny pro vytvoření třídy vlastní nastavení, v tématu [postupy: vytvoření nastavení aplikace](../../../../docs/framework/winforms/advanced/how-to-create-application-settings.md).  
  
## <a name="settings-keys-and-shared-settings"></a>Nastavení klíče a sdíleným nastavením  
 Některé ovládací prvky můžete použít více než jednou. v rámci stejného formuláře. Ve většině případů, můžete tyto ovládací prvky se zachovat jejich vlastní nastavení. Pomocí <xref:System.Configuration.IPersistComponentSettings.SettingsKey%2A> vlastnost na <xref:System.Configuration.IPersistComponentSettings>, můžete zadat do jedinečného řetězce, který slouží k rozlišení více verzí ovládacího prvku ve formuláři.  
  
 Nejjednodušší způsob, jak implementovat <xref:System.Configuration.IPersistComponentSettings.SettingsKey%2A> je použití <xref:System.Windows.Forms.Control.Name%2A> vlastnost ovládacího prvku pro <xref:System.Configuration.IPersistComponentSettings.SettingsKey%2A>. Při spouštění nebo uložit nastavení ovládacího prvku, předáte hodnotu <xref:System.Configuration.IPersistComponentSettings.SettingsKey%2A> na <xref:System.Configuration.ApplicationSettingsBase.SettingsKey%2A> vlastnost <xref:System.Configuration.ApplicationSettingsBase> třídy. Nastavení aplikace používá tento jedinečný klíč při zůstala zachována nastavení uživatele do formátu XML. Následující příklad kódu ukazuje způsob `<userSettings>` části může hledat instanci vlastního ovládacího prvku s názvem `CustomControl1` , uloží nastavení pro jeho `Text` vlastnost.  
  
```xml  
<userSettings>  
    <CustomControl1>  
        <setting name="Text" serializedAs="string">  
            <value>Hello, World</value>  
        </setting>  
    </CustomControl1>  
</userSettings>  
```  
  
 Všechny instance ovládacího prvku, který není zadat hodnotu <xref:System.Configuration.ApplicationSettingsBase.SettingsKey%2A> budou sdílet stejné nastavení.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Configuration.ApplicationSettingsBase>  
 <xref:System.Configuration.IPersistComponentSettings>  
 [Architektura nastavení aplikace](../../../../docs/framework/winforms/advanced/application-settings-architecture.md)
