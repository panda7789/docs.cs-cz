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
ms.openlocfilehash: e10bad5f746ae8777b9a7d4a65173b8abdeef00f
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64636947"
---
# <a name="how-to-validate-application-settings"></a>Postupy: Ověření nastavení aplikace
Toto téma ukazuje, jak ověřit nastavení aplikace předtím, než jsou trvalé.  
  
 Nastavení aplikace jsou silného typu, takže máte některé jistotu, že uživatelé nejde přiřadit data nesprávný typ daného nastavení. Však uživatel stále může pokus o přiřazení hodnoty k nastavení, která spadá mimo přijatelné meze – například poskytnutí datum narození, která nastane v budoucnosti. <xref:System.Configuration.ApplicationSettingsBase>, nadřazené třídu všechny třídy nastavení aplikace, zpřístupní čtyři události umožňující takové kontroly hranic. Zpracování těchto událostí umístí všechny ověřovací kód na jednom místě, nikoli rozptylu v celém projektu.  
  
 Události, kterou použijete, závisí na když budete chtít ověřit nastavení, jak je popsáno v následující tabulce.  
  
|Událost|Výskytu a použití|  
|-----------|------------------------|  
|<xref:System.Configuration.ApplicationSettingsBase.SettingsLoaded>|Vyvolá se po počátečním načtení skupiny vlastností nastavení.<br /><br /> Pomocí této události lze ověřit počáteční hodnoty pro skupinu pro celou vlastnost předtím, než se používají v rámci aplikace.|  
|<xref:System.Configuration.ApplicationSettingsBase.SettingChanging>|Vyvolá se před změnou hodnoty vlastnosti jednoho nastavení.<br /><br /> Pomocí této události lze ověřit jedné vlastnosti předtím, než se změnilo. To můžete poskytnout okamžitou zpětnou vazbu uživatelům týkající se jejich akce a možnosti.|  
|<xref:System.Configuration.ApplicationSettingsBase.PropertyChanged>|Vyvolá se po změně hodnoty vlastnosti jednoho nastavení.<br /><br /> Pomocí této události lze ověřit jedné vlastnosti poté, co se změnilo. Tato událost se jen zřídka použije pro ověření, pokud proces dlouhý a asynchronní ověření je povinný.|  
|<xref:System.Configuration.ApplicationSettingsBase.SettingsSaving>|Vyvolá se před uložené skupiny vlastností nastavení.<br /><br /> Pomocí této události lze ověřit hodnoty pro skupinu pro celou vlastnost předtím, než jsou trvalé na disk.|  
  
 Nebudou všechny tyto události v rámci stejné aplikace obvykle používají pro účely ověření. Například, často je možné ke splnění všech požadavků na ověření zpracovává pouze <xref:System.Configuration.ApplicationSettingsBase.SettingChanging> událostí.  
  
 Obslužná rutina události obvykle provádí, jeden z následujících akcí při zjistí neplatnou hodnotu:  
  
- Automaticky poskytuje hodnotu ví, že je správný, jako je například výchozí hodnota.  
  
- Znovu se dotazuje uživatele serverový kód pro informace.  
  
- Pro události vyvolané před jejich přidružených akcí, jako například <xref:System.Configuration.ApplicationSettingsBase.SettingChanging> a <xref:System.Configuration.ApplicationSettingsBase.SettingsSaving>, používá <xref:System.ComponentModel.CancelEventArgs> argument pro operaci zrušit.  
  
 Další informace o zpracování událostí naleznete v tématu [Přehled obslužných rutin událostí](../event-handlers-overview-windows-forms.md).  
  
 Následující postupy ukazují, jak otestovat platné datum narození buď pomocí <xref:System.Configuration.ApplicationSettingsBase.SettingChanging> nebo <xref:System.Configuration.ApplicationSettingsBase.SettingsSaving> událostí. Postupy byly určeny za předpokladu, že jste již vytvořili nastavení aplikace; v tomto příkladu budeme provádět kontrolu na nastavení s názvem hranic `DateOfBirth`. Další informace o vytváření nastavení najdete v tématu [jak: Vytvořit nastavení aplikace](how-to-create-application-settings.md).  
  
### <a name="to-obtain-the-application-settings-object"></a>K získání objektu nastavení aplikace  
  
- Získejte odkaz na objekt nastavení aplikace (Obálka instance) dokončení jedné z následujících položek seznamu s odrážkami:  
  
    - Pokud jste vytvořili pomocí dialogového okna nastavení aplikace Visual Studio v nastavení **Editor vlastností**, můžete načíst objekt nastavení výchozí vygenerovaný pro váš jazyk prostřednictvím následující výraz.  
  
        ```csharp  
        Configuration.Settings.Default   
        ```  
  
        ```vb  
        MySettings.Default   
        ```  
  
         -nebo-  
  
    - Pokud jste vývojář Visual Basic a vytvoříte nastavení aplikace pomocí Návrháře projektu, můžete načíst nastavení pomocí [My.Settings – objekt](~/docs/visual-basic/language-reference/objects/my-settings-object.md).  
  
         -nebo-  
  
    - Pokud jste vytvořili nastavení odvozením z <xref:System.Configuration.ApplicationSettingsBase> přímo, budete muset ručně vytvořit instanci své třídy.  
  
        ```csharp  
        MyCustomSettings settings = new MyCustomSettings();  
        ```  
  
        ```vb  
        Dim Settings as New MyCustomSettings()  
        ```  
  
 Následující postupy byly vytvořeny v rámci za předpokladu, že byl získán objekt nastavení aplikace vyplněním poslední seznamy s odrážkami položky v tomto postupu.  
  
### <a name="to-validate-application-settings-when-a-setting-is-changing"></a>Ověření nastavení aplikace při změně nastavení  
  
1. Pokud jste C# vývojářkou formuláře nebo ovládacího prvku `Load` události, přidejte obslužnou rutinu události pro <xref:System.Configuration.ApplicationSettingsBase.SettingChanging> událostí.  
  
     -nebo-  
  
     Pokud jste vývojář Visual Basic, by měla deklarovat `Settings` pomocí proměnných `WithEvents` – klíčové slovo.  
  
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
  
2. Definování obslužné rutiny událostí a psaní kódu v rámci služby tak, aby prováděly hranice kontroluje se datum narození.  
  
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
  
1. Do formuláře nebo ovládacího prvku `Load` události, přidejte obslužnou rutinu události pro <xref:System.Configuration.ApplicationSettingsBase.SettingsSaving> událostí.  
  
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
  
2. Definování obslužné rutiny událostí a psaní kódu v rámci služby tak, aby prováděly hranice kontroluje se datum narození.  
  
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
  
## <a name="see-also"></a>Viz také:

- [Vytváření obslužných rutin událostí ve Windows Forms](../creating-event-handlers-in-windows-forms.md)
- [Postupy: Vytvořit nastavení aplikace](how-to-create-application-settings.md)
