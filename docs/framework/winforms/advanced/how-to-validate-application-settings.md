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
ms.openlocfilehash: b7aba4935756fc218a1fadaa1dd9f20a5bc3034f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59317882"
---
# <a name="how-to-validate-application-settings"></a><span data-ttu-id="dc961-102">Postupy: Ověření nastavení aplikace</span><span class="sxs-lookup"><span data-stu-id="dc961-102">How to: Validate Application Settings</span></span>
<span data-ttu-id="dc961-103">Toto téma ukazuje, jak ověřit nastavení aplikace předtím, než jsou trvalé.</span><span class="sxs-lookup"><span data-stu-id="dc961-103">This topic demonstrates how to validate application settings before they are persisted.</span></span>  
  
 <span data-ttu-id="dc961-104">Nastavení aplikace jsou silného typu, takže máte některé jistotu, že uživatelé nejde přiřadit data nesprávný typ daného nastavení.</span><span class="sxs-lookup"><span data-stu-id="dc961-104">Because application settings are strongly typed, you have some confidence that users cannot assign data of an incorrect type to a given setting.</span></span> <span data-ttu-id="dc961-105">Však uživatel stále může pokus o přiřazení hodnoty k nastavení, která spadá mimo přijatelné meze – například poskytnutí datum narození, která nastane v budoucnosti.</span><span class="sxs-lookup"><span data-stu-id="dc961-105">However, a user still may attempt to assign a value to a setting that falls outside of acceptable bounds—for example, supplying a birth date that occurs in the future.</span></span> <span data-ttu-id="dc961-106"><xref:System.Configuration.ApplicationSettingsBase>, nadřazené třídu všechny třídy nastavení aplikace, zpřístupní čtyři události umožňující takové kontroly hranic.</span><span class="sxs-lookup"><span data-stu-id="dc961-106"><xref:System.Configuration.ApplicationSettingsBase>, the parent class of all application settings classes, exposes four events to enable such bounds checking.</span></span> <span data-ttu-id="dc961-107">Zpracování těchto událostí umístí všechny ověřovací kód na jednom místě, nikoli rozptylu v celém projektu.</span><span class="sxs-lookup"><span data-stu-id="dc961-107">Handling these events puts all of your validation code in a single location, rather than scattering it throughout your project.</span></span>  
  
 <span data-ttu-id="dc961-108">Události, kterou použijete, závisí na když budete chtít ověřit nastavení, jak je popsáno v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="dc961-108">The event you use depends upon when you need to validate your settings, as described in the following table.</span></span>  
  
|<span data-ttu-id="dc961-109">Událost</span><span class="sxs-lookup"><span data-stu-id="dc961-109">Event</span></span>|<span data-ttu-id="dc961-110">Výskytu a použití</span><span class="sxs-lookup"><span data-stu-id="dc961-110">Occurrence and use</span></span>|  
|-----------|------------------------|  
|<xref:System.Configuration.ApplicationSettingsBase.SettingsLoaded>|<span data-ttu-id="dc961-111">Vyvolá se po počátečním načtení skupiny vlastností nastavení.</span><span class="sxs-lookup"><span data-stu-id="dc961-111">Occurs after the initial loading of a settings property group.</span></span><br /><br /> <span data-ttu-id="dc961-112">Pomocí této události lze ověřit počáteční hodnoty pro skupinu pro celou vlastnost předtím, než se používají v rámci aplikace.</span><span class="sxs-lookup"><span data-stu-id="dc961-112">Use this event to validate initial values for the entire property group before they are used within the application.</span></span>|  
|<xref:System.Configuration.ApplicationSettingsBase.SettingChanging>|<span data-ttu-id="dc961-113">Vyvolá se před změnou hodnoty vlastnosti jednoho nastavení.</span><span class="sxs-lookup"><span data-stu-id="dc961-113">Occurs before the value of a single settings property is changed.</span></span><br /><br /> <span data-ttu-id="dc961-114">Pomocí této události lze ověřit jedné vlastnosti předtím, než se změnilo.</span><span class="sxs-lookup"><span data-stu-id="dc961-114">Use this event to validate a single property before it is changed.</span></span> <span data-ttu-id="dc961-115">To můžete poskytnout okamžitou zpětnou vazbu uživatelům týkající se jejich akce a možnosti.</span><span class="sxs-lookup"><span data-stu-id="dc961-115">It can provide immediate feedback to users regarding their actions and choices.</span></span>|  
|<xref:System.Configuration.ApplicationSettingsBase.PropertyChanged>|<span data-ttu-id="dc961-116">Vyvolá se po změně hodnoty vlastnosti jednoho nastavení.</span><span class="sxs-lookup"><span data-stu-id="dc961-116">Occurs after the value of a single settings property is changed.</span></span><br /><br /> <span data-ttu-id="dc961-117">Pomocí této události lze ověřit jedné vlastnosti poté, co se změnilo.</span><span class="sxs-lookup"><span data-stu-id="dc961-117">Use this event to validate a single property after it is changed.</span></span> <span data-ttu-id="dc961-118">Tato událost se jen zřídka použije pro ověření, pokud proces dlouhý a asynchronní ověření je povinný.</span><span class="sxs-lookup"><span data-stu-id="dc961-118">This event is rarely used for validation unless a lengthy, asynchronous validation process is required.</span></span>|  
|<xref:System.Configuration.ApplicationSettingsBase.SettingsSaving>|<span data-ttu-id="dc961-119">Vyvolá se před uložené skupiny vlastností nastavení.</span><span class="sxs-lookup"><span data-stu-id="dc961-119">Occurs before the settings property group is stored.</span></span><br /><br /> <span data-ttu-id="dc961-120">Pomocí této události lze ověřit hodnoty pro skupinu pro celou vlastnost předtím, než jsou trvalé na disk.</span><span class="sxs-lookup"><span data-stu-id="dc961-120">Use this event to validate values for the entire property group before they are persisted to disk.</span></span>|  
  
 <span data-ttu-id="dc961-121">Nebudou všechny tyto události v rámci stejné aplikace obvykle používají pro účely ověření.</span><span class="sxs-lookup"><span data-stu-id="dc961-121">Typically, you will not use all of these events within the same application for validation purposes.</span></span> <span data-ttu-id="dc961-122">Například, často je možné ke splnění všech požadavků na ověření zpracovává pouze <xref:System.Configuration.ApplicationSettingsBase.SettingChanging> událostí.</span><span class="sxs-lookup"><span data-stu-id="dc961-122">For example, it is often possible to fulfill all validation requirements by handling only the <xref:System.Configuration.ApplicationSettingsBase.SettingChanging> event.</span></span>  
  
 <span data-ttu-id="dc961-123">Obslužná rutina události obvykle provádí, jeden z následujících akcí při zjistí neplatnou hodnotu:</span><span class="sxs-lookup"><span data-stu-id="dc961-123">An event handler generally performs one of the following actions when it detects an invalid value:</span></span>  
  
-   <span data-ttu-id="dc961-124">Automaticky poskytuje hodnotu ví, že je správný, jako je například výchozí hodnota.</span><span class="sxs-lookup"><span data-stu-id="dc961-124">Automatically supplies a value known to be correct, such as the default value.</span></span>  
  
-   <span data-ttu-id="dc961-125">Znovu se dotazuje uživatele serverový kód pro informace.</span><span class="sxs-lookup"><span data-stu-id="dc961-125">Re-queries the user of server code for information.</span></span>  
  
-   <span data-ttu-id="dc961-126">Pro události vyvolané před jejich přidružených akcí, jako například <xref:System.Configuration.ApplicationSettingsBase.SettingChanging> a <xref:System.Configuration.ApplicationSettingsBase.SettingsSaving>, používá <xref:System.ComponentModel.CancelEventArgs> argument pro operaci zrušit.</span><span class="sxs-lookup"><span data-stu-id="dc961-126">For events raised before their associated actions, such as <xref:System.Configuration.ApplicationSettingsBase.SettingChanging> and <xref:System.Configuration.ApplicationSettingsBase.SettingsSaving>, uses the <xref:System.ComponentModel.CancelEventArgs> argument to cancel the operation.</span></span>  
  
 <span data-ttu-id="dc961-127">Další informace o zpracování událostí naleznete v tématu [Přehled obslužných rutin událostí](../event-handlers-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="dc961-127">For more information about event handling, see [Event Handlers Overview](../event-handlers-overview-windows-forms.md).</span></span>  
  
 <span data-ttu-id="dc961-128">Následující postupy ukazují, jak otestovat platné datum narození buď pomocí <xref:System.Configuration.ApplicationSettingsBase.SettingChanging> nebo <xref:System.Configuration.ApplicationSettingsBase.SettingsSaving> událostí.</span><span class="sxs-lookup"><span data-stu-id="dc961-128">The following procedures show how to test for a valid birth date using either the <xref:System.Configuration.ApplicationSettingsBase.SettingChanging> or the <xref:System.Configuration.ApplicationSettingsBase.SettingsSaving> event.</span></span> <span data-ttu-id="dc961-129">Postupy byly určeny za předpokladu, že jste již vytvořili nastavení aplikace; v tomto příkladu budeme provádět kontrolu na nastavení s názvem hranic `DateOfBirth`.</span><span class="sxs-lookup"><span data-stu-id="dc961-129">The procedures were written under the assumption that you have already created your application settings; in this example, we will perform bounds checking on a setting named `DateOfBirth`.</span></span> <span data-ttu-id="dc961-130">Další informace o vytváření nastavení najdete v tématu [jak: Vytvořit nastavení aplikace](how-to-create-application-settings.md).</span><span class="sxs-lookup"><span data-stu-id="dc961-130">For more information about creating settings, see [How to: Create Application Settings](how-to-create-application-settings.md).</span></span>  
  
### <a name="to-obtain-the-application-settings-object"></a><span data-ttu-id="dc961-131">K získání objektu nastavení aplikace</span><span class="sxs-lookup"><span data-stu-id="dc961-131">To obtain the application settings object</span></span>  
  
-   <span data-ttu-id="dc961-132">Získejte odkaz na objekt nastavení aplikace (Obálka instance) dokončení jedné z následujících položek seznamu s odrážkami:</span><span class="sxs-lookup"><span data-stu-id="dc961-132">Obtain a reference to the application settings object (the wrapper instance) by completing one of the following bulleted items:</span></span>  
  
    -   <span data-ttu-id="dc961-133">Pokud jste vytvořili pomocí dialogového okna nastavení aplikace Visual Studio v nastavení **Editor vlastností**, můžete načíst objekt nastavení výchozí vygenerovaný pro váš jazyk prostřednictvím následující výraz.</span><span class="sxs-lookup"><span data-stu-id="dc961-133">If you created your settings using the Visual Studio Application Settings dialog box in the **Property Editor**, you can retrieve the default settings object generated for your language through the following expression.</span></span>  
  
        ```csharp  
        Configuration.Settings.Default   
        ```  
  
        ```vb  
        MySettings.Default   
        ```  
  
         <span data-ttu-id="dc961-134">-nebo-</span><span class="sxs-lookup"><span data-stu-id="dc961-134">-or-</span></span>  
  
    -   <span data-ttu-id="dc961-135">Pokud jste vývojář Visual Basic a vytvoříte nastavení aplikace pomocí Návrháře projektu, můžete načíst nastavení pomocí [My.Settings – objekt](~/docs/visual-basic/language-reference/objects/my-settings-object.md).</span><span class="sxs-lookup"><span data-stu-id="dc961-135">If you are a Visual Basic developer and you created your application settings using the Project Designer, you can retrieve your settings by using the [My.Settings Object](~/docs/visual-basic/language-reference/objects/my-settings-object.md).</span></span>  
  
         <span data-ttu-id="dc961-136">-nebo-</span><span class="sxs-lookup"><span data-stu-id="dc961-136">-or-</span></span>  
  
    -   <span data-ttu-id="dc961-137">Pokud jste vytvořili nastavení odvozením z <xref:System.Configuration.ApplicationSettingsBase> přímo, budete muset ručně vytvořit instanci své třídy.</span><span class="sxs-lookup"><span data-stu-id="dc961-137">If you created your settings by deriving from <xref:System.Configuration.ApplicationSettingsBase> directly, you need to instantiate your class manually.</span></span>  
  
        ```csharp  
        MyCustomSettings settings = new MyCustomSettings();  
        ```  
  
        ```vb  
        Dim Settings as New MyCustomSettings()  
        ```  
  
 <span data-ttu-id="dc961-138">Následující postupy byly vytvořeny v rámci za předpokladu, že byl získán objekt nastavení aplikace vyplněním poslední seznamy s odrážkami položky v tomto postupu.</span><span class="sxs-lookup"><span data-stu-id="dc961-138">The following procedures were written under the assumption that the application settings object was obtained by completing the last bulleted item in this procedure.</span></span>  
  
### <a name="to-validate-application-settings-when-a-setting-is-changing"></a><span data-ttu-id="dc961-139">Ověření nastavení aplikace při změně nastavení</span><span class="sxs-lookup"><span data-stu-id="dc961-139">To validate Application Settings when a setting is changing</span></span>  
  
1. <span data-ttu-id="dc961-140">Pokud jste C# vývojářkou formuláře nebo ovládacího prvku `Load` události, přidejte obslužnou rutinu události pro <xref:System.Configuration.ApplicationSettingsBase.SettingChanging> událostí.</span><span class="sxs-lookup"><span data-stu-id="dc961-140">If you are a C# developer, in your form or control's `Load` event, add an event handler for the <xref:System.Configuration.ApplicationSettingsBase.SettingChanging> event.</span></span>  
  
     <span data-ttu-id="dc961-141">-nebo-</span><span class="sxs-lookup"><span data-stu-id="dc961-141">-or-</span></span>  
  
     <span data-ttu-id="dc961-142">Pokud jste vývojář Visual Basic, by měla deklarovat `Settings` pomocí proměnných `WithEvents` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="dc961-142">If you are a Visual Basic developer, you should declare the `Settings` variable using the `WithEvents` keyword.</span></span>  
  
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
  
2. <span data-ttu-id="dc961-143">Definování obslužné rutiny událostí a psaní kódu v rámci služby tak, aby prováděly hranice kontroluje se datum narození.</span><span class="sxs-lookup"><span data-stu-id="dc961-143">Define the event handler, and write the code inside of it to perform bounds checking on the birth date.</span></span>  
  
    ```csharp  
    private void MyCustomSettings_SettingChanging(Object sender, SettingChangingEventArgs e)  
    {  
        if (e.SettingName.Equals("DateOfBirth")) {  
            Date newDate = (Date)e.NewValue;  
            If (newDate > Date.Now) {  
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
  
### <a name="to-validate-application-settings-when-a-save-occurs"></a><span data-ttu-id="dc961-144">Ověření nastavení aplikace při uložení dojde k</span><span class="sxs-lookup"><span data-stu-id="dc961-144">To validate Application Settings when a Save occurs</span></span>  
  
1. <span data-ttu-id="dc961-145">Do formuláře nebo ovládacího prvku `Load` události, přidejte obslužnou rutinu události pro <xref:System.Configuration.ApplicationSettingsBase.SettingsSaving> událostí.</span><span class="sxs-lookup"><span data-stu-id="dc961-145">In your form or control's `Load` event, add an event handler for the <xref:System.Configuration.ApplicationSettingsBase.SettingsSaving> event.</span></span>  
  
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
  
2. <span data-ttu-id="dc961-146">Definování obslužné rutiny událostí a psaní kódu v rámci služby tak, aby prováděly hranice kontroluje se datum narození.</span><span class="sxs-lookup"><span data-stu-id="dc961-146">Define the event handler, and write the code inside of it to perform bounds checking on the birth date.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="dc961-147">Viz také:</span><span class="sxs-lookup"><span data-stu-id="dc961-147">See also</span></span>

- [<span data-ttu-id="dc961-148">Vytváření obslužných rutin událostí ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="dc961-148">Creating Event Handlers in Windows Forms</span></span>](../creating-event-handlers-in-windows-forms.md)
- [<span data-ttu-id="dc961-149">Postupy: Vytvořit nastavení aplikace</span><span class="sxs-lookup"><span data-stu-id="dc961-149">How to: Create Application Settings</span></span>](how-to-create-application-settings.md)
