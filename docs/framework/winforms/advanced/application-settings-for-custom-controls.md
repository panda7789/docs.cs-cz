---
title: Nastavení aplikace pro vlastní ovládací prvky
ms.date: 03/30/2017
helpviewer_keywords:
- custom controls [Windows Forms], application settings
- application settings [Windows Forms], custom controls
ms.assetid: f44afb74-76cc-44f2-890a-44b7cdc211a1
ms.openlocfilehash: 69a5caef8bab45503b9f34422de8c2ba2e7f01ff
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59317295"
---
# <a name="application-settings-for-custom-controls"></a>Nastavení aplikace pro vlastní ovládací prvky
Je třeba provést určité úlohy poskytnout vlastní ovládací prvky umožňuje zachovat nastavení aplikace, když jsou ovládací prvky jsou hostované v aplikacích třetích stran.  
  
 Většina dokumentace o nastavení aplikace funkcí se zapíše za předpokladu, že vytváříte samostatné aplikace. Ale při vytváření ovládacího prvku, který bude hostitelem jinými vývojáři ve svých aplikacích, budete muset provést několik dalších kroků pro ovládací prvek se zachovat jeho nastavení správně.  
  
## <a name="application-settings-and-custom-controls"></a>Nastavení aplikace a vlastních ovládacích prvků  
 Pro ovládací prvek se správně zachovat jeho nastavení, musí zapouzdřovat procesu tak, že vytvoříte svůj vlastní vyhrazený aplikace nastavení obálkovou třídu odvozenou z <xref:System.Configuration.ApplicationSettingsBase>. Kromě toho musí implementovat třídu hlavní ovládací prvek <xref:System.Configuration.IPersistComponentSettings>. Rozhraní obsahuje několik vlastností a také dvě metody, <xref:System.Configuration.IPersistComponentSettings.LoadComponentSettings%2A> a <xref:System.Configuration.IPersistComponentSettings.SaveComponentSettings%2A>. Pokud přidáte ovládací prvek do formuláře pomocí **Návrháře formulářů Windows** v sadě Visual Studio, Windows Forms zavolá <xref:System.Configuration.IPersistComponentSettings.LoadComponentSettings%2A> automaticky při inicializaci ovládacího prvku, je nutné volat <xref:System.Configuration.IPersistComponentSettings.SaveComponentSettings%2A> vás `Dispose` Metoda ovládacího prvku.  
  
 Kromě toho byste měli implementovat následující pořadí pro nastavení aplikace pro vlastní ovládací prvky, aby správně fungovala v době návrhu prostředí, jako je Visual Studio:  
  
1. Vlastní aplikace nastavení třídu s konstruktorem, který přebírá <xref:System.ComponentModel.IComponent> jako jediný parametr. Tato třída slouží k uložení a načtení všech nastavení aplikace. Když vytvoříte novou instanci této třídy, předejte vlastního ovládacího prvku pomocí konstruktoru.  
  
2. Po ovládací prvek byl vytvořen a umístěné do formuláře, jako například v formuláře vytvořit toto vlastní nastavení třídy <xref:System.Windows.Forms.Form.Load> obslužné rutiny události.  
  
 Pokyny týkající se vytvoření vlastního nastavení třídy naleznete v tématu [jak: Vytvořit nastavení aplikace](how-to-create-application-settings.md).  
  
## <a name="settings-keys-and-shared-settings"></a>Nastavení klíče a sdíleným nastavením  
 Některé ovládací prvky lze použít více než jednou v rámci stejného formuláře. Ve většině případů, měli byste tyto ovládací prvky se zachovat jejich vlastní nastavení. S <xref:System.Configuration.IPersistComponentSettings.SettingsKey%2A> vlastnost <xref:System.Configuration.IPersistComponentSettings>, můžete zadat jedinečný řetězec, který slouží k rozlišení více verzí ovládací prvek na formuláři.  
  
 Nejjednodušší způsob, jak implementovat <xref:System.Configuration.IPersistComponentSettings.SettingsKey%2A> , je použít <xref:System.Windows.Forms.Control.Name%2A> ovládacího prvku pro vlastnosti <xref:System.Configuration.IPersistComponentSettings.SettingsKey%2A>. Při načtení nebo uložení nastavení ovládacího prvku, předejte hodnotu <xref:System.Configuration.IPersistComponentSettings.SettingsKey%2A> k <xref:System.Configuration.ApplicationSettingsBase.SettingsKey%2A> vlastnost <xref:System.Configuration.ApplicationSettingsBase> třídy. Nastavení aplikace používá tento jedinečný klíč při nevyřeší nastavení uživatele do souboru XML. Následující příklad kódu ukazuje jak `<userSettings>` části může hledat instance vlastního ovládacího prvku s názvem `CustomControl1` , která ukládá nastavení pro jeho `Text` vlastnost.  
  
```xml  
<userSettings>  
    <CustomControl1>  
        <setting name="Text" serializedAs="string">  
            <value>Hello, World</value>  
        </setting>  
    </CustomControl1>  
</userSettings>  
```  
  
 Všechny instance ovládacího prvku, který nelze zadat hodnotu <xref:System.Configuration.ApplicationSettingsBase.SettingsKey%2A> budou sdílet stejné nastavení.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Configuration.ApplicationSettingsBase>
- <xref:System.Configuration.IPersistComponentSettings>
- [Architektura nastavení aplikace](application-settings-architecture.md)
