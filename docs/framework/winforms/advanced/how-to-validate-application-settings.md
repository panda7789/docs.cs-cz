---
title: 'Postupy: Ověření nastavení aplikace'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- validating application settings
- application settings [Windows Forms], Windows Forms
- application settings [Windows Forms], validating
ms.assetid: 9f145ada-4267-436a-aa4c-c4dcffd0afb7
ms.openlocfilehash: b3b2447b570f0635942183dcc62c0e4ed73800d1
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/13/2019
ms.locfileid: "70972249"
---
# <a name="how-to-validate-application-settings"></a><span data-ttu-id="64544-102">Postupy: Ověření nastavení aplikace</span><span class="sxs-lookup"><span data-stu-id="64544-102">How to: Validate Application Settings</span></span>

<span data-ttu-id="64544-103">Toto téma ukazuje, jak ověřit nastavení aplikace před tím, než budou trvalá.</span><span class="sxs-lookup"><span data-stu-id="64544-103">This topic demonstrates how to validate application settings before they are persisted.</span></span>

<span data-ttu-id="64544-104">Vzhledem k tomu, že nastavení aplikace jsou silného typu, máte jistotu, že uživatelé nemůžou přiřadit k danému nastavení data nesprávného typu.</span><span class="sxs-lookup"><span data-stu-id="64544-104">Because application settings are strongly typed, you have some confidence that users cannot assign data of an incorrect type to a given setting.</span></span> <span data-ttu-id="64544-105">Uživatel se ale stále může pokusit přiřadit hodnotu k nastavení, které spadá mimo přijatelné hranice – například zadáním data narození, které nastane v budoucnu.</span><span class="sxs-lookup"><span data-stu-id="64544-105">However, a user still may attempt to assign a value to a setting that falls outside of acceptable bounds—for example, supplying a birth date that occurs in the future.</span></span> <span data-ttu-id="64544-106"><xref:System.Configuration.ApplicationSettingsBase>, nadřazená třída všech tříd nastavení aplikace zpřístupňuje čtyři události, aby bylo možné tuto kontrolu vazeb povolit.</span><span class="sxs-lookup"><span data-stu-id="64544-106"><xref:System.Configuration.ApplicationSettingsBase>, the parent class of all application settings classes, exposes four events to enable such bounds checking.</span></span> <span data-ttu-id="64544-107">Zpracování těchto událostí vloží veškerý ověřovací kód do jednoho umístění, nikoli v celém projektu.</span><span class="sxs-lookup"><span data-stu-id="64544-107">Handling these events puts all of your validation code in a single location, rather than scattering it throughout your project.</span></span>

<span data-ttu-id="64544-108">Událost, kterou použijete, závisí na tom, kdy potřebujete ověřit nastavení, jak je popsáno v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="64544-108">The event you use depends upon when you need to validate your settings, as described in the following table.</span></span>

|<span data-ttu-id="64544-109">Událost</span><span class="sxs-lookup"><span data-stu-id="64544-109">Event</span></span>|<span data-ttu-id="64544-110">Výskyt a použití</span><span class="sxs-lookup"><span data-stu-id="64544-110">Occurrence and use</span></span>|
|-----------|------------------------|
|<xref:System.Configuration.ApplicationSettingsBase.SettingsLoaded>|<span data-ttu-id="64544-111">Vyvolá se po počátečním načtení skupiny vlastností nastavení.</span><span class="sxs-lookup"><span data-stu-id="64544-111">Occurs after the initial loading of a settings property group.</span></span><br /><br /> <span data-ttu-id="64544-112">Tuto událost použijte k ověření počátečních hodnot pro celou skupinu vlastností předtím, než se použijí v rámci aplikace.</span><span class="sxs-lookup"><span data-stu-id="64544-112">Use this event to validate initial values for the entire property group before they are used within the application.</span></span>|
|<xref:System.Configuration.ApplicationSettingsBase.SettingChanging>|<span data-ttu-id="64544-113">Proběhne před změnou hodnoty vlastnosti s jedním nastavením.</span><span class="sxs-lookup"><span data-stu-id="64544-113">Occurs before the value of a single settings property is changed.</span></span><br /><br /> <span data-ttu-id="64544-114">Pomocí této události lze před změnou ověřit jednu vlastnost.</span><span class="sxs-lookup"><span data-stu-id="64544-114">Use this event to validate a single property before it is changed.</span></span> <span data-ttu-id="64544-115">Může uživatelům poskytnout okamžitou zpětnou vazbu ohledně jejich akcí a možností.</span><span class="sxs-lookup"><span data-stu-id="64544-115">It can provide immediate feedback to users regarding their actions and choices.</span></span>|
|<xref:System.Configuration.ApplicationSettingsBase.PropertyChanged>|<span data-ttu-id="64544-116">Nastane po změně hodnoty vlastnosti s jedním nastavením.</span><span class="sxs-lookup"><span data-stu-id="64544-116">Occurs after the value of a single settings property is changed.</span></span><br /><br /> <span data-ttu-id="64544-117">Tuto událost použijte k ověření jedné vlastnosti poté, co se změní.</span><span class="sxs-lookup"><span data-stu-id="64544-117">Use this event to validate a single property after it is changed.</span></span> <span data-ttu-id="64544-118">Tato událost se používá zřídka pro ověřování, pokud není vyžadován zdlouhavý proces asynchronního ověření.</span><span class="sxs-lookup"><span data-stu-id="64544-118">This event is rarely used for validation unless a lengthy, asynchronous validation process is required.</span></span>|
|<xref:System.Configuration.ApplicationSettingsBase.SettingsSaving>|<span data-ttu-id="64544-119">Vyvolá se před uložením skupiny vlastností nastavení.</span><span class="sxs-lookup"><span data-stu-id="64544-119">Occurs before the settings property group is stored.</span></span><br /><br /> <span data-ttu-id="64544-120">Tuto událost použijte k ověření hodnot pro celou skupinu vlastností před jejich uložením na disk.</span><span class="sxs-lookup"><span data-stu-id="64544-120">Use this event to validate values for the entire property group before they are persisted to disk.</span></span>|

<span data-ttu-id="64544-121">Obvykle nebudete používat všechny tyto události v rámci stejné aplikace pro účely ověření.</span><span class="sxs-lookup"><span data-stu-id="64544-121">Typically, you will not use all of these events within the same application for validation purposes.</span></span> <span data-ttu-id="64544-122">Například je často možné splnit všechny požadavky na ověření tím, že zpracuje pouze <xref:System.Configuration.ApplicationSettingsBase.SettingChanging> událost.</span><span class="sxs-lookup"><span data-stu-id="64544-122">For example, it is often possible to fulfill all validation requirements by handling only the <xref:System.Configuration.ApplicationSettingsBase.SettingChanging> event.</span></span>

<span data-ttu-id="64544-123">Obslužná rutina události obvykle provádí jednu z následujících akcí, když zjistí neplatnou hodnotu:</span><span class="sxs-lookup"><span data-stu-id="64544-123">An event handler generally performs one of the following actions when it detects an invalid value:</span></span>

- <span data-ttu-id="64544-124">Automaticky poskytuje hodnotu známou jako správnou, jako je například výchozí hodnota.</span><span class="sxs-lookup"><span data-stu-id="64544-124">Automatically supplies a value known to be correct, such as the default value.</span></span>

- <span data-ttu-id="64544-125">Znovu zadá dotaz na informace o uživateli kódu serveru.</span><span class="sxs-lookup"><span data-stu-id="64544-125">Re-queries the user of server code for information.</span></span>

- <span data-ttu-id="64544-126">Pro události, které byly vyvolány před jejich <xref:System.Configuration.ApplicationSettingsBase.SettingChanging> přidruženými akcemi <xref:System.ComponentModel.CancelEventArgs> , jako například a <xref:System.Configuration.ApplicationSettingsBase.SettingsSaving>, používá argument pro zrušení operace.</span><span class="sxs-lookup"><span data-stu-id="64544-126">For events raised before their associated actions, such as <xref:System.Configuration.ApplicationSettingsBase.SettingChanging> and <xref:System.Configuration.ApplicationSettingsBase.SettingsSaving>, uses the <xref:System.ComponentModel.CancelEventArgs> argument to cancel the operation.</span></span>

<span data-ttu-id="64544-127">Další informace o zpracování událostí naleznete v tématu [Přehled obslužných rutin událostí](../event-handlers-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="64544-127">For more information about event handling, see [Event Handlers Overview](../event-handlers-overview-windows-forms.md).</span></span>

<span data-ttu-id="64544-128">Následující postupy ukazují, jak otestovat platné datum narození pomocí <xref:System.Configuration.ApplicationSettingsBase.SettingChanging> <xref:System.Configuration.ApplicationSettingsBase.SettingsSaving> události nebo.</span><span class="sxs-lookup"><span data-stu-id="64544-128">The following procedures show how to test for a valid birth date using either the <xref:System.Configuration.ApplicationSettingsBase.SettingChanging> or the <xref:System.Configuration.ApplicationSettingsBase.SettingsSaving> event.</span></span> <span data-ttu-id="64544-129">Postupy byly zapsány v rámci předpokladu, že jste již vytvořili nastavení aplikace. v tomto příkladu provedeme kontrolu vazeb u nastavení s názvem `DateOfBirth`.</span><span class="sxs-lookup"><span data-stu-id="64544-129">The procedures were written under the assumption that you have already created your application settings; in this example, we will perform bounds checking on a setting named `DateOfBirth`.</span></span> <span data-ttu-id="64544-130">Další informace o vytváření nastavení naleznete v tématu [How to: Vytvořte nastavení](how-to-create-application-settings.md)aplikace.</span><span class="sxs-lookup"><span data-stu-id="64544-130">For more information about creating settings, see [How to: Create Application Settings](how-to-create-application-settings.md).</span></span>

### <a name="to-obtain-the-application-settings-object"></a><span data-ttu-id="64544-131">Získání objektu nastavení aplikace</span><span class="sxs-lookup"><span data-stu-id="64544-131">To obtain the application settings object</span></span>

- <span data-ttu-id="64544-132">Vyžádejte si odkaz na objekt nastavení aplikace (Obálková instance) tím, že vyplníte jednu z následujících položek s odrážkami:</span><span class="sxs-lookup"><span data-stu-id="64544-132">Obtain a reference to the application settings object (the wrapper instance) by completing one of the following bulleted items:</span></span>

  - <span data-ttu-id="64544-133">Pokud jste vytvořili nastavení pomocí dialogového okna nastavení aplikace Visual Studio v **editoru vlastností**, můžete načíst objekt výchozí nastavení generovaný pro váš jazyk pomocí následujícího výrazu.</span><span class="sxs-lookup"><span data-stu-id="64544-133">If you created your settings using the Visual Studio Application Settings dialog box in the **Property Editor**, you can retrieve the default settings object generated for your language through the following expression.</span></span>

    ```csharp
    Configuration.Settings.Default
    ```

    ```vb
    MySettings.Default
    ```

    <span data-ttu-id="64544-134">-nebo-</span><span class="sxs-lookup"><span data-stu-id="64544-134">-or-</span></span>

  - <span data-ttu-id="64544-135">Pokud jste vývojář Visual Basic a vytvořili jste nastavení aplikace pomocí Návrháře projektu, můžete načíst nastavení pomocí [objektu My. Settings](../../../visual-basic/language-reference/objects/my-settings-object.md).</span><span class="sxs-lookup"><span data-stu-id="64544-135">If you are a Visual Basic developer and you created your application settings using the Project Designer, you can retrieve your settings by using the [My.Settings Object](../../../visual-basic/language-reference/objects/my-settings-object.md).</span></span>

    <span data-ttu-id="64544-136">-nebo-</span><span class="sxs-lookup"><span data-stu-id="64544-136">-or-</span></span>

  - <span data-ttu-id="64544-137">Pokud jste vytvořili nastavení odvozením <xref:System.Configuration.ApplicationSettingsBase> přímo, je nutné vytvořit instanci třídy ručně.</span><span class="sxs-lookup"><span data-stu-id="64544-137">If you created your settings by deriving from <xref:System.Configuration.ApplicationSettingsBase> directly, you need to instantiate your class manually.</span></span>

    ```csharp
    MyCustomSettings settings = new MyCustomSettings();
    ```

    ```vb
    Dim Settings as New MyCustomSettings()
    ```

<span data-ttu-id="64544-138">Následující postupy byly zapsány v rámci předpokladu, že byl objekt nastavení aplikace získán dokončením poslední položky s odrážkami v tomto postupu.</span><span class="sxs-lookup"><span data-stu-id="64544-138">The following procedures were written under the assumption that the application settings object was obtained by completing the last bulleted item in this procedure.</span></span>

### <a name="to-validate-application-settings-when-a-setting-is-changing"></a><span data-ttu-id="64544-139">Ověření nastavení aplikace při změně nastavení</span><span class="sxs-lookup"><span data-stu-id="64544-139">To validate Application Settings when a setting is changing</span></span>

1. <span data-ttu-id="64544-140">Pokud jste C# vývojář, v `Load` události formuláře nebo ovládacího prvku přidejte obslužnou rutinu <xref:System.Configuration.ApplicationSettingsBase.SettingChanging> události pro událost.</span><span class="sxs-lookup"><span data-stu-id="64544-140">If you are a C# developer, in your form or control's `Load` event, add an event handler for the <xref:System.Configuration.ApplicationSettingsBase.SettingChanging> event.</span></span>

    <span data-ttu-id="64544-141">-nebo-</span><span class="sxs-lookup"><span data-stu-id="64544-141">-or-</span></span>

    <span data-ttu-id="64544-142">Pokud jste vývojář Visual Basic, měli byste deklarovat `Settings` proměnnou `WithEvents` pomocí klíčového slova.</span><span class="sxs-lookup"><span data-stu-id="64544-142">If you are a Visual Basic developer, you should declare the `Settings` variable using the `WithEvents` keyword.</span></span>

    ```csharp
    public void Form1_Load(Object sender, EventArgs e)
    {
        settings.SettingChanging += new SettingChangingEventHandler(MyCustomSettings_SettingChanging);
    }
    ```

    ```vb
    Public Sub Form1_Load(sender as Object, e as EventArgs)
        AddHandler settings.SettingChanging, AddressOf MyCustomSettings_SettingChanging
    End Sub
    ```

2. <span data-ttu-id="64544-143">Definujte obslužnou rutinu události a napište do ní kód, který provede kontrolu hranic pro datum narození.</span><span class="sxs-lookup"><span data-stu-id="64544-143">Define the event handler, and write the code inside of it to perform bounds checking on the birth date.</span></span>

    ```csharp
    private void MyCustomSettings_SettingChanging(Object sender, SettingChangingEventArgs e)
    {
        if (e.SettingName.Equals("DateOfBirth"))
        {
            var newDate = (DateTime)e.NewValue;
            if (newDate > DateTime.Now)
            {
                e.Cancel = true;
                // Inform the user.
            }
        }
    }
    ```

    ```vb
    Private Sub MyCustomSettings_SettingChanging(sender as Object, e as SettingChangingEventArgs) Handles Settings.SettingChanging
        If (e.SettingName.Equals("DateOfBirth")) Then
            Dim NewDate as Date = CType(e.NewValue, Date)
            If (NewDate > Date.Now) Then
                e.Cancel = True
                ' Inform the user.
            End If
        End If
    End Sub
    ```

### <a name="to-validate-application-settings-when-a-save-occurs"></a><span data-ttu-id="64544-144">Ověření nastavení aplikace, když dojde k uložení</span><span class="sxs-lookup"><span data-stu-id="64544-144">To validate Application Settings when a Save occurs</span></span>

1. <span data-ttu-id="64544-145">V `Load` události formuláře nebo ovládacího prvku přidejte obslužnou rutinu události <xref:System.Configuration.ApplicationSettingsBase.SettingsSaving> pro událost.</span><span class="sxs-lookup"><span data-stu-id="64544-145">In your form or control's `Load` event, add an event handler for the <xref:System.Configuration.ApplicationSettingsBase.SettingsSaving> event.</span></span>

    ```csharp
    public void Form1_Load(Object sender, EventArgs e)
    {
        settings.SettingsSaving += new SettingsSavingEventHandler(MyCustomSettings_SettingsSaving);
    }
    ```

    ```vb
    Public Sub Form1_Load(Sender as Object, e as EventArgs)
        AddHandler settings.SettingsSaving, AddressOf MyCustomSettings_SettingsSaving
    End Sub
    ```

2. <span data-ttu-id="64544-146">Definujte obslužnou rutinu události a napište do ní kód, který provede kontrolu hranic pro datum narození.</span><span class="sxs-lookup"><span data-stu-id="64544-146">Define the event handler, and write the code inside of it to perform bounds checking on the birth date.</span></span>

    ```csharp
    private void MyCustomSettings_SettingsSaving(Object sender, SettingsSavingEventArgs e)
    {
        if (this["DateOfBirth"] > Date.Now) {
            e.Cancel = true;
        }
    }
    ```

    ```vb
    Private Sub MyCustomSettings_SettingsSaving(Sender as Object, e as SettingsSavingEventArgs)
        If (Me["DateOfBirth"] > Date.Now) Then
            e.Cancel = True
        End If
    End Sub
    ```

## <a name="see-also"></a><span data-ttu-id="64544-147">Viz také:</span><span class="sxs-lookup"><span data-stu-id="64544-147">See also</span></span>

- [<span data-ttu-id="64544-148">Vytváření obslužných rutin událostí ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="64544-148">Creating Event Handlers in Windows Forms</span></span>](../creating-event-handlers-in-windows-forms.md)
- [<span data-ttu-id="64544-149">Postupy: Vytvořit nastavení aplikace</span><span class="sxs-lookup"><span data-stu-id="64544-149">How to: Create Application Settings</span></span>](how-to-create-application-settings.md)
