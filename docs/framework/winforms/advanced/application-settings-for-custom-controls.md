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
ms.workload: dotnet
ms.openlocfilehash: e21a49b26a7493aaec31d5a97e627ce7925f39b3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="application-settings-for-custom-controls"></a><span data-ttu-id="5385d-102">Nastavení aplikace pro vlastní ovládací prvky</span><span class="sxs-lookup"><span data-stu-id="5385d-102">Application Settings for Custom Controls</span></span>
<span data-ttu-id="5385d-103">Musíte provést určité úlohy poskytnout vlastní ovládací prvky umožňuje zachovat nastavení aplikace, když jsou ovládací prvky jsou hostované v aplikacích třetích stran.</span><span class="sxs-lookup"><span data-stu-id="5385d-103">You must complete certain tasks to give your custom controls the ability to persist application settings when the controls are hosted in third-party applications.</span></span>  
  
 <span data-ttu-id="5385d-104">Většina dokumentace o funkci nastavení aplikace je zapsán za předpokladu, že vytváříte samostatné aplikace.</span><span class="sxs-lookup"><span data-stu-id="5385d-104">Most of the documentation about the Application Settings feature is written under the assumption that you are creating a standalone application.</span></span> <span data-ttu-id="5385d-105">Ale pokud vytváříte ovládací prvek, který bude hostitelem jinými vývojáři ve svých aplikacích, budete muset provést několik další kroky pro ovládací prvek pro zachování jeho nastavení správně.</span><span class="sxs-lookup"><span data-stu-id="5385d-105">However, if you are creating a control that other developers will host in their applications, you need to take a few additional steps for your control to persist its settings properly.</span></span>  
  
## <a name="application-settings-and-custom-controls"></a><span data-ttu-id="5385d-106">Nastavení aplikace a vlastních ovládacích prvků</span><span class="sxs-lookup"><span data-stu-id="5385d-106">Application Settings and Custom Controls</span></span>  
 <span data-ttu-id="5385d-107">Pro ovládací prvek se správně zachovat jeho nastavení, musí zapouzdřovat proces tak, že vytvoříte vlastní vyhrazené aplikace nastavení obálkové třídy odvozené od <xref:System.Configuration.ApplicationSettingsBase>.</span><span class="sxs-lookup"><span data-stu-id="5385d-107">For your control to properly persist its settings, it must encapsulate the process by creating its own dedicated applications settings wrapper class, derived from <xref:System.Configuration.ApplicationSettingsBase>.</span></span> <span data-ttu-id="5385d-108">Kromě toho musí implementovat třídu hlavní ovládacího prvku <xref:System.Configuration.IPersistComponentSettings>.</span><span class="sxs-lookup"><span data-stu-id="5385d-108">Additionally, the main control class must implement the <xref:System.Configuration.IPersistComponentSettings>.</span></span> <span data-ttu-id="5385d-109">Rozhraní obsahuje několik vlastností, jakož i dvě metody, <xref:System.Configuration.IPersistComponentSettings.LoadComponentSettings%2A> a <xref:System.Configuration.IPersistComponentSettings.SaveComponentSettings%2A>.</span><span class="sxs-lookup"><span data-stu-id="5385d-109">The interface contains several properties as well as two methods, <xref:System.Configuration.IPersistComponentSettings.LoadComponentSettings%2A> and <xref:System.Configuration.IPersistComponentSettings.SaveComponentSettings%2A>.</span></span> <span data-ttu-id="5385d-110">Pokud přidáte vlastní ovládací prvek na formuláři pomocí **Návrhář formulářů Windows** v sadě Visual Studio, Windows Forms zavolá <xref:System.Configuration.IPersistComponentSettings.LoadComponentSettings%2A> automaticky při inicializaci ovládacího prvku; musí volat <xref:System.Configuration.IPersistComponentSettings.SaveComponentSettings%2A> sami v `Dispose` Metoda vlastního ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="5385d-110">If you add your control to a form using the **Windows Forms Designer** in Visual Studio, Windows Forms will call <xref:System.Configuration.IPersistComponentSettings.LoadComponentSettings%2A> automatically when the control is initialized; you must call <xref:System.Configuration.IPersistComponentSettings.SaveComponentSettings%2A> yourself in the `Dispose` method of your control.</span></span>  
  
 <span data-ttu-id="5385d-111">Kromě toho byste měli implementovat následující pořadí pro nastavení aplikace pro vlastní ovládací prvky pro práci správně v prostředí návrhu třeba v sadě Visual Studio:</span><span class="sxs-lookup"><span data-stu-id="5385d-111">In addition, you should implement the following in order for application settings for custom controls to work properly in design-time environments such as Visual Studio:</span></span>  
  
1.  <span data-ttu-id="5385d-112">Třída nastavení vlastní aplikaci s konstruktor, který přebírá <xref:System.ComponentModel.IComponent> jako jeden parametr.</span><span class="sxs-lookup"><span data-stu-id="5385d-112">A custom application settings class with a constructor that takes an <xref:System.ComponentModel.IComponent> as a single parameter.</span></span> <span data-ttu-id="5385d-113">Tato třída slouží k uložení a načtení všech nastavení aplikace.</span><span class="sxs-lookup"><span data-stu-id="5385d-113">Use this class to save and load all of your application settings.</span></span> <span data-ttu-id="5385d-114">Když vytvoříte novou instanci této třídy, předejte vlastního ovládacího prvku pomocí konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="5385d-114">When you create a new instance of this class, pass your custom control using the constructor.</span></span>  
  
2.  <span data-ttu-id="5385d-115">Vytvořit tuto třídu vlastní nastavení po ovládacího prvku byla vytvořena a umístěna ve formuláři, například v formuláře <xref:System.Windows.Forms.Form.Load> obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="5385d-115">Create this custom settings class after the control has been created and placed on a form, such as in the form's <xref:System.Windows.Forms.Form.Load> event handler.</span></span>  
  
 <span data-ttu-id="5385d-116">Pokyny pro vytvoření třídy vlastní nastavení, v tématu [postupy: vytvoření nastavení aplikace](../../../../docs/framework/winforms/advanced/how-to-create-application-settings.md).</span><span class="sxs-lookup"><span data-stu-id="5385d-116">For instructions on creating a custom settings class, see [How to: Create Application Settings](../../../../docs/framework/winforms/advanced/how-to-create-application-settings.md).</span></span>  
  
## <a name="settings-keys-and-shared-settings"></a><span data-ttu-id="5385d-117">Nastavení klíče a sdíleným nastavením</span><span class="sxs-lookup"><span data-stu-id="5385d-117">Settings Keys and Shared Settings</span></span>  
 <span data-ttu-id="5385d-118">Některé ovládací prvky můžete použít více než jednou. v rámci stejného formuláře.</span><span class="sxs-lookup"><span data-stu-id="5385d-118">Some controls can be used multiple times within the same form.</span></span> <span data-ttu-id="5385d-119">Ve většině případů, můžete tyto ovládací prvky se zachovat jejich vlastní nastavení.</span><span class="sxs-lookup"><span data-stu-id="5385d-119">Most of the time, you will want these controls to persist their own individual settings.</span></span> <span data-ttu-id="5385d-120">Pomocí <xref:System.Configuration.IPersistComponentSettings.SettingsKey%2A> vlastnost na <xref:System.Configuration.IPersistComponentSettings>, můžete zadat do jedinečného řetězce, který slouží k rozlišení více verzí ovládacího prvku ve formuláři.</span><span class="sxs-lookup"><span data-stu-id="5385d-120">With the <xref:System.Configuration.IPersistComponentSettings.SettingsKey%2A> property on <xref:System.Configuration.IPersistComponentSettings>, you can supply a unique string that acts to disambiguate multiple versions of a control on a form.</span></span>  
  
 <span data-ttu-id="5385d-121">Nejjednodušší způsob, jak implementovat <xref:System.Configuration.IPersistComponentSettings.SettingsKey%2A> je použití <xref:System.Windows.Forms.Control.Name%2A> vlastnost ovládacího prvku pro <xref:System.Configuration.IPersistComponentSettings.SettingsKey%2A>.</span><span class="sxs-lookup"><span data-stu-id="5385d-121">The simplest way to implement <xref:System.Configuration.IPersistComponentSettings.SettingsKey%2A> is to use the <xref:System.Windows.Forms.Control.Name%2A> property of the control for the <xref:System.Configuration.IPersistComponentSettings.SettingsKey%2A>.</span></span> <span data-ttu-id="5385d-122">Při spouštění nebo uložit nastavení ovládacího prvku, předáte hodnotu <xref:System.Configuration.IPersistComponentSettings.SettingsKey%2A> na <xref:System.Configuration.ApplicationSettingsBase.SettingsKey%2A> vlastnost <xref:System.Configuration.ApplicationSettingsBase> třídy.</span><span class="sxs-lookup"><span data-stu-id="5385d-122">When you load or save the control's settings, you pass the value of <xref:System.Configuration.IPersistComponentSettings.SettingsKey%2A> on to the <xref:System.Configuration.ApplicationSettingsBase.SettingsKey%2A> property of the <xref:System.Configuration.ApplicationSettingsBase> class.</span></span> <span data-ttu-id="5385d-123">Nastavení aplikace používá tento jedinečný klíč při zůstala zachována nastavení uživatele do formátu XML.</span><span class="sxs-lookup"><span data-stu-id="5385d-123">Application Settings uses this unique key when it persists the user's settings to XML.</span></span> <span data-ttu-id="5385d-124">Následující příklad kódu ukazuje způsob `<userSettings>` části může hledat instanci vlastního ovládacího prvku s názvem `CustomControl1` , uloží nastavení pro jeho `Text` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="5385d-124">The following code example shows how a `<userSettings>` section may look for an instance of a custom control named `CustomControl1` that saves a setting for its `Text` property.</span></span>  
  
```xml  
<userSettings>  
    <CustomControl1>  
        <setting name="Text" serializedAs="string">  
            <value>Hello, World</value>  
        </setting>  
    </CustomControl1>  
</userSettings>  
```  
  
 <span data-ttu-id="5385d-125">Všechny instance ovládacího prvku, který není zadat hodnotu <xref:System.Configuration.ApplicationSettingsBase.SettingsKey%2A> budou sdílet stejné nastavení.</span><span class="sxs-lookup"><span data-stu-id="5385d-125">Any instances of a control that do not supply a value for <xref:System.Configuration.ApplicationSettingsBase.SettingsKey%2A> will share the same settings.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5385d-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="5385d-126">See Also</span></span>  
 <xref:System.Configuration.ApplicationSettingsBase>  
 <xref:System.Configuration.IPersistComponentSettings>  
 [<span data-ttu-id="5385d-127">Architektura nastavení aplikace</span><span class="sxs-lookup"><span data-stu-id="5385d-127">Application Settings Architecture</span></span>](../../../../docs/framework/winforms/advanced/application-settings-architecture.md)
