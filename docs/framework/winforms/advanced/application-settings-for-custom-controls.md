---
title: Nastavení aplikace pro vlastní ovládací prvky
ms.date: 03/30/2017
helpviewer_keywords:
- custom controls [Windows Forms], application settings
- application settings [Windows Forms], custom controls
ms.assetid: f44afb74-76cc-44f2-890a-44b7cdc211a1
ms.openlocfilehash: a4e477ce1c171b514482623595b2c5565564a2cb
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69040462"
---
# <a name="application-settings-for-custom-controls"></a>Nastavení aplikace pro vlastní ovládací prvky
Je nutné provést určité úlohy, abyste měli vlastní ovládací prvky, aby bylo možné zachovat nastavení aplikace, když jsou ovládací prvky hostovány v aplikacích třetích stran.

 Většina dokumentace k funkci nastavení aplikace se zapisuje do předpokladu, že vytváříte samostatnou aplikaci. Pokud však vytváříte ovládací prvek, který budou hostovat jiní vývojáři ve svých aplikacích, je nutné provést několik dalších kroků, aby váš ovládací prvek správně zachoval nastavení.

## <a name="application-settings-and-custom-controls"></a>Nastavení aplikace a vlastní ovládací prvky
 Aby váš ovládací prvek správně zachoval nastavení, musí zapouzdřit proces vytvořením vlastní vyhrazené třídy nastavení vyhrazené aplikace, která je odvozena z <xref:System.Configuration.ApplicationSettingsBase>. Kromě toho musí hlavní třída ovládacího prvku implementovat rozhraní <xref:System.Configuration.IPersistComponentSettings>. Rozhraní obsahuje několik vlastností <xref:System.Configuration.IPersistComponentSettings.LoadComponentSettings%2A> a také dvě metody a. <xref:System.Configuration.IPersistComponentSettings.SaveComponentSettings%2A> Přidáte-li ovládací prvek do formuláře pomocí **Návrhář formulářů** v aplikaci Visual Studio, model Windows Forms bude volána <xref:System.Configuration.IPersistComponentSettings.LoadComponentSettings%2A> automaticky při inicializaci ovládacího prvku; je nutné `Dispose` volat <xref:System.Configuration.IPersistComponentSettings.SaveComponentSettings%2A> sami v metodě ovládacího prvku.

 Kromě toho byste měli implementovat následující, aby nastavení aplikace pro vlastní ovládací prvky pracovala správně v prostředích návrhu, jako je například Visual Studio:

1. Vlastní třída nastavení aplikace s konstruktorem, který přijímá <xref:System.ComponentModel.IComponent> jako jeden parametr. Tuto třídu použijte k uložení a načtení všech nastavení aplikace. Při vytváření nové instance této třídy předejte vlastní ovládací prvek pomocí konstruktoru.

2. Po vytvoření ovládacího prvku a jeho umístění do formuláře, jako je například obslužná rutina <xref:System.Windows.Forms.Form.Load> události formuláře, vytvořte tuto vlastní třídu nastavení.

 Pokyny k vytvoření vlastní třídy nastavení naleznete v tématu [How to: Vytvořte nastavení](how-to-create-application-settings.md)aplikace.

## <a name="settings-keys-and-shared-settings"></a>Nastavení klíčů a sdílených nastavení
 Některé ovládací prvky lze použít několikrát v rámci jednoho formuláře. Ve většině případů budete chtít, aby tyto ovládací prvky zachovaly vlastní individuální nastavení. S vlastností on <xref:System.Configuration.IPersistComponentSettings>můžete zadejte jedinečný řetězec, který slouží k jednoznačnému rozlišení více verzí ovládacího prvku na formuláři. <xref:System.Configuration.IPersistComponentSettings.SettingsKey%2A>

 Nejjednodušší způsob, jak implementovat <xref:System.Configuration.IPersistComponentSettings.SettingsKey%2A> , je <xref:System.Windows.Forms.Control.Name%2A> použít vlastnost ovládacího prvku pro <xref:System.Configuration.IPersistComponentSettings.SettingsKey%2A>. Při načítání nebo ukládání nastavení ovládacího prvku předáte hodnotu <xref:System.Configuration.IPersistComponentSettings.SettingsKey%2A> pro <xref:System.Configuration.ApplicationSettingsBase.SettingsKey%2A> do vlastnosti <xref:System.Configuration.ApplicationSettingsBase> třídy. Nastavení aplikace používá tento jedinečný klíč, když uchovává nastavení uživatele do XML. Následující příklad kódu ukazuje, jak `<userSettings>` může oddíl najít instanci vlastního ovládacího prvku s názvem `CustomControl1` , který ukládá nastavení pro jeho `Text` vlastnost.

```xml
<userSettings>
    <CustomControl1>
        <setting name="Text" serializedAs="string">
            <value>Hello, World</value>
        </setting>
    </CustomControl1>
</userSettings>
```

 Všechny instance ovládacího prvku, který nedodá hodnotu pro <xref:System.Configuration.ApplicationSettingsBase.SettingsKey%2A> , budou sdílet stejné nastavení.

## <a name="see-also"></a>Viz také:

- <xref:System.Configuration.ApplicationSettingsBase>
- <xref:System.Configuration.IPersistComponentSettings>
- [Architektura nastavení aplikace](application-settings-architecture.md)
