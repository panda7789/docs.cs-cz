---
title: "Postupy: Ověření nastavení aplikace"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- validating application settings
- application settings [Windows Forms], Windows Forms
- application settings [Windows Forms], validating
ms.assetid: 9f145ada-4267-436a-aa4c-c4dcffd0afb7
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e12620a5079efaba4faa9101253a3a586965b7e5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-validate-application-settings"></a><span data-ttu-id="2b511-102">Postupy: Ověření nastavení aplikace</span><span class="sxs-lookup"><span data-stu-id="2b511-102">How to: Validate Application Settings</span></span>
<span data-ttu-id="2b511-103">Toto téma ukazuje, jak ověřit nastavení aplikace předtím, než jsou nastavené jako trvalé.</span><span class="sxs-lookup"><span data-stu-id="2b511-103">This topic demonstrates how to validate application settings before they are persisted.</span></span>  
  
 <span data-ttu-id="2b511-104">Vzhledem k tomu, že nastavení aplikace jsou silného typu, máte některé jistotu, že uživatelé nelze přiřadit nesprávný typ dat daného nastavení.</span><span class="sxs-lookup"><span data-stu-id="2b511-104">Because application settings are strongly typed, you have some confidence that users cannot assign data of an incorrect type to a given setting.</span></span> <span data-ttu-id="2b511-105">Ale uživatel stále se pokusit o přiřazení hodnoty k nastavení, která spadá mimo přijatelný rozsah – například zadávání datum narození, který se nachází v budoucnu.</span><span class="sxs-lookup"><span data-stu-id="2b511-105">However, a user still may attempt to assign a value to a setting that falls outside of acceptable bounds—for example, supplying a birth date that occurs in the future.</span></span> <span data-ttu-id="2b511-106"><xref:System.Configuration.ApplicationSettingsBase>, nadřazenou třídu všechny třídy nastavení aplikace, zpřístupní čtyři události povolit takové hranice kontrola.</span><span class="sxs-lookup"><span data-stu-id="2b511-106"><xref:System.Configuration.ApplicationSettingsBase>, the parent class of all application settings classes, exposes four events to enable such bounds checking.</span></span> <span data-ttu-id="2b511-107">Zpracování těchto událostí vloží všechny ověřovacího kódu na jednom místě, nikoli rozptylu v rámci projektu.</span><span class="sxs-lookup"><span data-stu-id="2b511-107">Handling these events puts all of your validation code in a single location, rather than scattering it throughout your project.</span></span>  
  
 <span data-ttu-id="2b511-108">Události, kterou použijete, závisí na když potřebujete ověřit nastavení, jak je popsáno v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="2b511-108">The event you use depends upon when you need to validate your settings, as described in the following table.</span></span>  
  
|<span data-ttu-id="2b511-109">Událost</span><span class="sxs-lookup"><span data-stu-id="2b511-109">Event</span></span>|<span data-ttu-id="2b511-110">Výskytu a použití</span><span class="sxs-lookup"><span data-stu-id="2b511-110">Occurrence and use</span></span>|  
|-----------|------------------------|  
|<xref:System.Configuration.ApplicationSettingsBase.SettingsLoaded>|<span data-ttu-id="2b511-111">Nastane po počáteční načítání skupinu nastavení vlastností.</span><span class="sxs-lookup"><span data-stu-id="2b511-111">Occurs after the initial loading of a settings property group.</span></span><br /><br /> <span data-ttu-id="2b511-112">Pomocí této události lze ověřit počáteční hodnoty pro skupinu celý vlastnost před použitím v aplikaci.</span><span class="sxs-lookup"><span data-stu-id="2b511-112">Use this event to validate initial values for the entire property group before they are used within the application.</span></span>|  
|<xref:System.Configuration.ApplicationSettingsBase.SettingChanging>|<span data-ttu-id="2b511-113">Nastane, než je hodnota vlastnosti jednoho nastavení změnit.</span><span class="sxs-lookup"><span data-stu-id="2b511-113">Occurs before the value of a single settings property is changed.</span></span><br /><br /> <span data-ttu-id="2b511-114">Pomocí této události lze ověřit jednu vlastnost, než je změnit.</span><span class="sxs-lookup"><span data-stu-id="2b511-114">Use this event to validate a single property before it is changed.</span></span> <span data-ttu-id="2b511-115">Okamžitou zpětnou vazbu může poskytovat uživatelům o jejich akce a možnosti.</span><span class="sxs-lookup"><span data-stu-id="2b511-115">It can provide immediate feedback to users regarding their actions and choices.</span></span>|  
|<xref:System.Configuration.ApplicationSettingsBase.PropertyChanged>|<span data-ttu-id="2b511-116">Nastane po změně hodnoty vlastnosti jednoho nastavení.</span><span class="sxs-lookup"><span data-stu-id="2b511-116">Occurs after the value of a single settings property is changed.</span></span><br /><br /> <span data-ttu-id="2b511-117">Pomocí této události lze ověřit vlastnosti jediné poté, co se změnilo.</span><span class="sxs-lookup"><span data-stu-id="2b511-117">Use this event to validate a single property after it is changed.</span></span> <span data-ttu-id="2b511-118">Tato událost je málo používané pro ověření, pokud proces ověření náročná, asynchronní není nutné.</span><span class="sxs-lookup"><span data-stu-id="2b511-118">This event is rarely used for validation unless a lengthy, asynchronous validation process is required.</span></span>|  
|<xref:System.Configuration.ApplicationSettingsBase.SettingsSaving>|<span data-ttu-id="2b511-119">Nastane před skupina vlastnost nastavení je uložena.</span><span class="sxs-lookup"><span data-stu-id="2b511-119">Occurs before the settings property group is stored.</span></span><br /><br /> <span data-ttu-id="2b511-120">Pomocí této události lze ověřit hodnoty pro skupinu celý vlastnost předtím, než jsou nastavené jako trvalé na disk.</span><span class="sxs-lookup"><span data-stu-id="2b511-120">Use this event to validate values for the entire property group before they are persisted to disk.</span></span>|  
  
 <span data-ttu-id="2b511-121">Obvykle se všechny tyto události stejné aplikace nebude používat pro účely ověření.</span><span class="sxs-lookup"><span data-stu-id="2b511-121">Typically, you will not use all of these events within the same application for validation purposes.</span></span> <span data-ttu-id="2b511-122">Například je často možné ke splnění všech požadavků na ověření pomocí zpracování pouze <xref:System.Configuration.ApplicationSettingsBase.SettingChanging> událostí.</span><span class="sxs-lookup"><span data-stu-id="2b511-122">For example, it is often possible to fulfill all validation requirements by handling only the <xref:System.Configuration.ApplicationSettingsBase.SettingChanging> event.</span></span>  
  
 <span data-ttu-id="2b511-123">Obslužné rutiny události obecně provádí, jednu z následujících akcí při zjištění neplatnou hodnotu:</span><span class="sxs-lookup"><span data-stu-id="2b511-123">An event handler generally performs one of the following actions when it detects an invalid value:</span></span>  
  
-   <span data-ttu-id="2b511-124">Automaticky poskytuje hodnotu známé správné, jako je například výchozí hodnota.</span><span class="sxs-lookup"><span data-stu-id="2b511-124">Automatically supplies a value known to be correct, such as the default value.</span></span>  
  
-   <span data-ttu-id="2b511-125">Znovu se dotazuje uživatel serverový kód pro informace.</span><span class="sxs-lookup"><span data-stu-id="2b511-125">Re-queries the user of server code for information.</span></span>  
  
-   <span data-ttu-id="2b511-126">Pro události se vyvolalo před jejich přidružených akcí, jako například <xref:System.Configuration.ApplicationSettingsBase.SettingChanging> a <xref:System.Configuration.ApplicationSettingsBase.SettingsSaving>, používá <xref:System.ComponentModel.CancelEventArgs> argument na tlačítko Storno.</span><span class="sxs-lookup"><span data-stu-id="2b511-126">For events raised before their associated actions, such as <xref:System.Configuration.ApplicationSettingsBase.SettingChanging> and <xref:System.Configuration.ApplicationSettingsBase.SettingsSaving>, uses the <xref:System.ComponentModel.CancelEventArgs> argument to cancel the operation.</span></span>  
  
 <span data-ttu-id="2b511-127">Další informace o zpracování událostí najdete v tématu [Přehled obslužných rutin událostí](../../../../docs/framework/winforms/event-handlers-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="2b511-127">For more information about event handling, see [Event Handlers Overview](../../../../docs/framework/winforms/event-handlers-overview-windows-forms.md).</span></span>  
  
 <span data-ttu-id="2b511-128">Následující postupy ukazují, jak chcete otestovat datum narození platný buď pomocí <xref:System.Configuration.ApplicationSettingsBase.SettingChanging> nebo <xref:System.Configuration.ApplicationSettingsBase.SettingsSaving> událostí.</span><span class="sxs-lookup"><span data-stu-id="2b511-128">The following procedures show how to test for a valid birth date using either the <xref:System.Configuration.ApplicationSettingsBase.SettingChanging> or the <xref:System.Configuration.ApplicationSettingsBase.SettingsSaving> event.</span></span> <span data-ttu-id="2b511-129">Postupy, byly určeny za předpokladu, že jste již vytvořili nastavení aplikace; v tomto příkladu provedeme hranice probíhá kontrola v nastavení s názvem `DateOfBirth`.</span><span class="sxs-lookup"><span data-stu-id="2b511-129">The procedures were written under the assumption that you have already created your application settings; in this example, we will perform bounds checking on a setting named `DateOfBirth`.</span></span> <span data-ttu-id="2b511-130">Další informace o vytváření nastavení najdete v tématu [postupy: vytvoření nastavení aplikace](../../../../docs/framework/winforms/advanced/how-to-create-application-settings.md).</span><span class="sxs-lookup"><span data-stu-id="2b511-130">For more information about creating settings, see [How to: Create Application Settings](../../../../docs/framework/winforms/advanced/how-to-create-application-settings.md).</span></span>  
  
### <a name="to-obtain-the-application-settings-object"></a><span data-ttu-id="2b511-131">K získání objektu nastavení aplikace</span><span class="sxs-lookup"><span data-stu-id="2b511-131">To obtain the application settings object</span></span>  
  
-   <span data-ttu-id="2b511-132">Provedením jedné z následujících položek s odrážkami získejte odkaz na objekt nastavení aplikace (instance obálky):</span><span class="sxs-lookup"><span data-stu-id="2b511-132">Obtain a reference to the application settings object (the wrapper instance) by completing one of the following bulleted items:</span></span>  
  
    -   <span data-ttu-id="2b511-133">Pokud jste vytvořili pomocí dialogového okna nastavení aplikace Visual Studio v nastavení **Editor vlastností**, můžete načíst objekt nastavení výchozí vygenerované jazyka prostřednictvím následující výraz.</span><span class="sxs-lookup"><span data-stu-id="2b511-133">If you created your settings using the Visual Studio Application Settings dialog box in the **Property Editor**, you can retrieve the default settings object generated for your language through the following expression.</span></span>  
  
        ```csharp  
        Configuration.Settings.Default   
        ```  
  
        ```vb  
        MySettings.Default   
        ```  
  
         <span data-ttu-id="2b511-134">-nebo-</span><span class="sxs-lookup"><span data-stu-id="2b511-134">-or-</span></span>  
  
    -   <span data-ttu-id="2b511-135">Pokud jste vývojář jazyka Visual Basic a vytvoření nastavení aplikace pomocí Návrháře projektu, můžete načíst nastavení pomocí [My.Settings – objekt](~/docs/visual-basic/language-reference/objects/my-settings-object.md).</span><span class="sxs-lookup"><span data-stu-id="2b511-135">If you are a Visual Basic developer and you created your application settings using the Project Designer, you can retrieve your settings by using the [My.Settings Object](~/docs/visual-basic/language-reference/objects/my-settings-object.md).</span></span>  
  
         <span data-ttu-id="2b511-136">-nebo-</span><span class="sxs-lookup"><span data-stu-id="2b511-136">-or-</span></span>  
  
    -   <span data-ttu-id="2b511-137">Pokud jste vytvořili nastavení odvozené z <xref:System.Configuration.ApplicationSettingsBase> přímo, budete muset vytvořit instanci třídě ručně.</span><span class="sxs-lookup"><span data-stu-id="2b511-137">If you created your settings by deriving from <xref:System.Configuration.ApplicationSettingsBase> directly, you need to instantiate your class manually.</span></span>  
  
        ```csharp  
        MyCustomSettings settings = new MyCustomSettings();  
        ```  
  
        ```vb  
        Dim Settings as New MyCustomSettings()  
        ```  
  
 <span data-ttu-id="2b511-138">Následující postupy byly napsány za předpokladu, který byl získán objekt nastavení aplikace pomocí poslední položky s odrážkami v tomto postupu.</span><span class="sxs-lookup"><span data-stu-id="2b511-138">The following procedures were written under the assumption that the application settings object was obtained by completing the last bulleted item in this procedure.</span></span>  
  
### <a name="to-validate-application-settings-when-a-setting-is-changing"></a><span data-ttu-id="2b511-139">Když je změna nastavení ověření nastavení aplikace</span><span class="sxs-lookup"><span data-stu-id="2b511-139">To validate Application Settings when a setting is changing</span></span>  
  
1.  <span data-ttu-id="2b511-140">Pokud jste vývojář v C# v formuláře nebo ovládacího prvku `Load` událostí, přidejte obslužnou rutinu události pro <xref:System.Configuration.ApplicationSettingsBase.SettingChanging> událostí.</span><span class="sxs-lookup"><span data-stu-id="2b511-140">If you are a C# developer, in your form or control's `Load` event, add an event handler for the <xref:System.Configuration.ApplicationSettingsBase.SettingChanging> event.</span></span>  
  
     <span data-ttu-id="2b511-141">-nebo-</span><span class="sxs-lookup"><span data-stu-id="2b511-141">-or-</span></span>  
  
     <span data-ttu-id="2b511-142">Pokud jste vývojář jazyka Visual Basic, by měly deklarovat `Settings` proměnné pomocí `WithEvents` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="2b511-142">If you are a Visual Basic developer, you should declare the `Settings` variable using the `WithEvents` keyword.</span></span>  
  
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
  
2.  <span data-ttu-id="2b511-143">Definování obslužné rutiny události a napsat kód uvnitř této provést kontrolu na datum narození hranice.</span><span class="sxs-lookup"><span data-stu-id="2b511-143">Define the event handler, and write the code inside of it to perform bounds checking on the birth date.</span></span>  
  
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
  
### <a name="to-validate-application-settings-when-a-save-occurs"></a><span data-ttu-id="2b511-144">Ověření nastavení aplikace při uložení dojde k</span><span class="sxs-lookup"><span data-stu-id="2b511-144">To validate Application Settings when a Save occurs</span></span>  
  
1.  <span data-ttu-id="2b511-145">Ve formuláři nebo ovládacího prvku `Load` událostí, přidejte obslužnou rutinu události pro <xref:System.Configuration.ApplicationSettingsBase.SettingsSaving> událostí.</span><span class="sxs-lookup"><span data-stu-id="2b511-145">In your form or control's `Load` event, add an event handler for the <xref:System.Configuration.ApplicationSettingsBase.SettingsSaving> event.</span></span>  
  
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
  
2.  <span data-ttu-id="2b511-146">Definování obslužné rutiny události a napsat kód uvnitř této provést kontrolu na datum narození hranice.</span><span class="sxs-lookup"><span data-stu-id="2b511-146">Define the event handler, and write the code inside of it to perform bounds checking on the birth date.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="2b511-147">Viz také</span><span class="sxs-lookup"><span data-stu-id="2b511-147">See Also</span></span>  
 [<span data-ttu-id="2b511-148">Vytváření obslužných rutin událostí ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="2b511-148">Creating Event Handlers in Windows Forms</span></span>](../../../../docs/framework/winforms/creating-event-handlers-in-windows-forms.md)  
 [<span data-ttu-id="2b511-149">Postupy: Vytváření nastavení aplikace</span><span class="sxs-lookup"><span data-stu-id="2b511-149">How to: Create Application Settings</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-application-settings.md)
