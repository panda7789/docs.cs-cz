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
# <a name="how-to-validate-application-settings"></a>Postupy: Ověření nastavení aplikace
Toto téma ukazuje, jak ověřit nastavení aplikace předtím, než jsou nastavené jako trvalé.  
  
 Vzhledem k tomu, že nastavení aplikace jsou silného typu, máte některé jistotu, že uživatelé nelze přiřadit nesprávný typ dat daného nastavení. Ale uživatel stále se pokusit o přiřazení hodnoty k nastavení, která spadá mimo přijatelný rozsah – například zadávání datum narození, který se nachází v budoucnu. <xref:System.Configuration.ApplicationSettingsBase>, nadřazenou třídu všechny třídy nastavení aplikace, zpřístupní čtyři události povolit takové hranice kontrola. Zpracování těchto událostí vloží všechny ověřovacího kódu na jednom místě, nikoli rozptylu v rámci projektu.  
  
 Události, kterou použijete, závisí na když potřebujete ověřit nastavení, jak je popsáno v následující tabulce.  
  
|Událost|Výskytu a použití|  
|-----------|------------------------|  
|<xref:System.Configuration.ApplicationSettingsBase.SettingsLoaded>|Nastane po počáteční načítání skupinu nastavení vlastností.<br /><br /> Pomocí této události lze ověřit počáteční hodnoty pro skupinu celý vlastnost před použitím v aplikaci.|  
|<xref:System.Configuration.ApplicationSettingsBase.SettingChanging>|Nastane, než je hodnota vlastnosti jednoho nastavení změnit.<br /><br /> Pomocí této události lze ověřit jednu vlastnost, než je změnit. Okamžitou zpětnou vazbu může poskytovat uživatelům o jejich akce a možnosti.|  
|<xref:System.Configuration.ApplicationSettingsBase.PropertyChanged>|Nastane po změně hodnoty vlastnosti jednoho nastavení.<br /><br /> Pomocí této události lze ověřit vlastnosti jediné poté, co se změnilo. Tato událost je málo používané pro ověření, pokud proces ověření náročná, asynchronní není nutné.|  
|<xref:System.Configuration.ApplicationSettingsBase.SettingsSaving>|Nastane před skupina vlastnost nastavení je uložena.<br /><br /> Pomocí této události lze ověřit hodnoty pro skupinu celý vlastnost předtím, než jsou nastavené jako trvalé na disk.|  
  
 Obvykle se všechny tyto události stejné aplikace nebude používat pro účely ověření. Například je často možné ke splnění všech požadavků na ověření pomocí zpracování pouze <xref:System.Configuration.ApplicationSettingsBase.SettingChanging> událostí.  
  
 Obslužné rutiny události obecně provádí, jednu z následujících akcí při zjištění neplatnou hodnotu:  
  
-   Automaticky poskytuje hodnotu známé správné, jako je například výchozí hodnota.  
  
-   Znovu se dotazuje uživatel serverový kód pro informace.  
  
-   Pro události se vyvolalo před jejich přidružených akcí, jako například <xref:System.Configuration.ApplicationSettingsBase.SettingChanging> a <xref:System.Configuration.ApplicationSettingsBase.SettingsSaving>, používá <xref:System.ComponentModel.CancelEventArgs> argument na tlačítko Storno.  
  
 Další informace o zpracování událostí najdete v tématu [Přehled obslužných rutin událostí](../../../../docs/framework/winforms/event-handlers-overview-windows-forms.md).  
  
 Následující postupy ukazují, jak chcete otestovat datum narození platný buď pomocí <xref:System.Configuration.ApplicationSettingsBase.SettingChanging> nebo <xref:System.Configuration.ApplicationSettingsBase.SettingsSaving> událostí. Postupy, byly určeny za předpokladu, že jste již vytvořili nastavení aplikace; v tomto příkladu provedeme hranice probíhá kontrola v nastavení s názvem `DateOfBirth`. Další informace o vytváření nastavení najdete v tématu [postupy: vytvoření nastavení aplikace](../../../../docs/framework/winforms/advanced/how-to-create-application-settings.md).  
  
### <a name="to-obtain-the-application-settings-object"></a>K získání objektu nastavení aplikace  
  
-   Provedením jedné z následujících položek s odrážkami získejte odkaz na objekt nastavení aplikace (instance obálky):  
  
    -   Pokud jste vytvořili pomocí dialogového okna nastavení aplikace Visual Studio v nastavení **Editor vlastností**, můžete načíst objekt nastavení výchozí vygenerované jazyka prostřednictvím následující výraz.  
  
        ```csharp  
        Configuration.Settings.Default   
        ```  
  
        ```vb  
        MySettings.Default   
        ```  
  
         -nebo-  
  
    -   Pokud jste vývojář jazyka Visual Basic a vytvoření nastavení aplikace pomocí Návrháře projektu, můžete načíst nastavení pomocí [My.Settings – objekt](~/docs/visual-basic/language-reference/objects/my-settings-object.md).  
  
         -nebo-  
  
    -   Pokud jste vytvořili nastavení odvozené z <xref:System.Configuration.ApplicationSettingsBase> přímo, budete muset vytvořit instanci třídě ručně.  
  
        ```csharp  
        MyCustomSettings settings = new MyCustomSettings();  
        ```  
  
        ```vb  
        Dim Settings as New MyCustomSettings()  
        ```  
  
 Následující postupy byly napsány za předpokladu, který byl získán objekt nastavení aplikace pomocí poslední položky s odrážkami v tomto postupu.  
  
### <a name="to-validate-application-settings-when-a-setting-is-changing"></a>Když je změna nastavení ověření nastavení aplikace  
  
1.  Pokud jste vývojář v C# v formuláře nebo ovládacího prvku `Load` událostí, přidejte obslužnou rutinu události pro <xref:System.Configuration.ApplicationSettingsBase.SettingChanging> událostí.  
  
     -nebo-  
  
     Pokud jste vývojář jazyka Visual Basic, by měly deklarovat `Settings` proměnné pomocí `WithEvents` – klíčové slovo.  
  
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
  
2.  Definování obslužné rutiny události a napsat kód uvnitř této provést kontrolu na datum narození hranice.  
  
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
  
### <a name="to-validate-application-settings-when-a-save-occurs"></a>Ověření nastavení aplikace při uložení dojde k  
  
1.  Ve formuláři nebo ovládacího prvku `Load` událostí, přidejte obslužnou rutinu události pro <xref:System.Configuration.ApplicationSettingsBase.SettingsSaving> událostí.  
  
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
  
2.  Definování obslužné rutiny události a napsat kód uvnitř této provést kontrolu na datum narození hranice.  
  
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
  
## <a name="see-also"></a>Viz také  
 [Vytváření obslužných rutin událostí ve Windows Forms](../../../../docs/framework/winforms/creating-event-handlers-in-windows-forms.md)  
 [Postupy: Vytváření nastavení aplikace](../../../../docs/framework/winforms/advanced/how-to-create-application-settings.md)
