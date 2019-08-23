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
ms.openlocfilehash: 220b86c0de57e60036527bb49f2d8de46390a9ed
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69929781"
---
# <a name="how-to-validate-application-settings"></a>Postupy: Ověření nastavení aplikace

Toto téma ukazuje, jak ověřit nastavení aplikace před tím, než budou trvalá.

Vzhledem k tomu, že nastavení aplikace jsou silného typu, máte jistotu, že uživatelé nemůžou přiřadit k danému nastavení data nesprávného typu. Uživatel se ale stále může pokusit přiřadit hodnotu k nastavení, které spadá mimo přijatelné hranice – například zadáním data narození, které nastane v budoucnu. <xref:System.Configuration.ApplicationSettingsBase>, nadřazená třída všech tříd nastavení aplikace zpřístupňuje čtyři události, aby bylo možné tuto kontrolu vazeb povolit. Zpracování těchto událostí vloží veškerý ověřovací kód do jednoho umístění, nikoli v celém projektu.

Událost, kterou použijete, závisí na tom, kdy potřebujete ověřit nastavení, jak je popsáno v následující tabulce.

|Událost|Výskyt a použití|
|-----------|------------------------|
|<xref:System.Configuration.ApplicationSettingsBase.SettingsLoaded>|Vyvolá se po počátečním načtení skupiny vlastností nastavení.<br /><br /> Tuto událost použijte k ověření počátečních hodnot pro celou skupinu vlastností předtím, než se použijí v rámci aplikace.|
|<xref:System.Configuration.ApplicationSettingsBase.SettingChanging>|Proběhne před změnou hodnoty vlastnosti s jedním nastavením.<br /><br /> Pomocí této události lze před změnou ověřit jednu vlastnost. Může uživatelům poskytnout okamžitou zpětnou vazbu ohledně jejich akcí a možností.|
|<xref:System.Configuration.ApplicationSettingsBase.PropertyChanged>|Nastane po změně hodnoty vlastnosti s jedním nastavením.<br /><br /> Tuto událost použijte k ověření jedné vlastnosti poté, co se změní. Tato událost se používá zřídka pro ověřování, pokud není vyžadován zdlouhavý proces asynchronního ověření.|
|<xref:System.Configuration.ApplicationSettingsBase.SettingsSaving>|Vyvolá se před uložením skupiny vlastností nastavení.<br /><br /> Tuto událost použijte k ověření hodnot pro celou skupinu vlastností před jejich uložením na disk.|

Obvykle nebudete používat všechny tyto události v rámci stejné aplikace pro účely ověření. Například je často možné splnit všechny požadavky na ověření tím, že zpracuje pouze <xref:System.Configuration.ApplicationSettingsBase.SettingChanging> událost.

Obslužná rutina události obvykle provádí jednu z následujících akcí, když zjistí neplatnou hodnotu:

- Automaticky poskytuje hodnotu známou jako správnou, jako je například výchozí hodnota.

- Znovu zadá dotaz na informace o uživateli kódu serveru.

- Pro události, které byly vyvolány před jejich <xref:System.Configuration.ApplicationSettingsBase.SettingChanging> přidruženými akcemi <xref:System.ComponentModel.CancelEventArgs> , jako například a <xref:System.Configuration.ApplicationSettingsBase.SettingsSaving>, používá argument pro zrušení operace.

Další informace o zpracování událostí naleznete v tématu [Přehled obslužných rutin událostí](../event-handlers-overview-windows-forms.md).

Následující postupy ukazují, jak otestovat platné datum narození pomocí <xref:System.Configuration.ApplicationSettingsBase.SettingChanging> <xref:System.Configuration.ApplicationSettingsBase.SettingsSaving> události nebo. Postupy byly zapsány v rámci předpokladu, že jste již vytvořili nastavení aplikace. v tomto příkladu provedeme kontrolu vazeb u nastavení s názvem `DateOfBirth`. Další informace o vytváření nastavení naleznete v tématu [How to: Vytvořte nastavení](how-to-create-application-settings.md)aplikace.

### <a name="to-obtain-the-application-settings-object"></a>Získání objektu nastavení aplikace

- Vyžádejte si odkaz na objekt nastavení aplikace (Obálková instance) tím, že vyplníte jednu z následujících položek s odrážkami:

  - Pokud jste vytvořili nastavení pomocí dialogového okna nastavení aplikace Visual Studio v **editoru vlastností**, můžete načíst objekt výchozí nastavení generovaný pro váš jazyk pomocí následujícího výrazu.

    ```csharp
    Configuration.Settings.Default
    ```

    ```vb
    MySettings.Default
    ```

    -nebo-

  - Pokud jste vývojář Visual Basic a vytvořili jste nastavení aplikace pomocí Návrháře projektu, můžete načíst nastavení pomocí [objektu My. Settings](../../../visual-basic/language-reference/objects/my-settings-object.md).

    -nebo-

  - Pokud jste vytvořili nastavení odvozením <xref:System.Configuration.ApplicationSettingsBase> přímo, je nutné vytvořit instanci třídy ručně.

    ```csharp
    MyCustomSettings settings = new MyCustomSettings();
    ```

    ```vb
    Dim Settings as New MyCustomSettings()
    ```

Následující postupy byly zapsány v rámci předpokladu, že byl objekt nastavení aplikace získán dokončením poslední položky s odrážkami v tomto postupu.

### <a name="to-validate-application-settings-when-a-setting-is-changing"></a>Ověření nastavení aplikace při změně nastavení

1. Pokud jste C# vývojář, v `Load` události formuláře nebo ovládacího prvku přidejte obslužnou rutinu <xref:System.Configuration.ApplicationSettingsBase.SettingChanging> události pro událost.

    -nebo-

    Pokud jste vývojář Visual Basic, měli byste deklarovat `Settings` proměnnou `WithEvents` pomocí klíčového slova.

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

2. Definujte obslužnou rutinu události a napište do ní kód, který provede kontrolu hranic pro datum narození.

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

### <a name="to-validate-application-settings-when-a-save-occurs"></a>Ověření nastavení aplikace, když dojde k uložení

1. V `Load` události formuláře nebo ovládacího prvku přidejte obslužnou rutinu události <xref:System.Configuration.ApplicationSettingsBase.SettingsSaving> pro událost.

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

2. Definujte obslužnou rutinu události a napište do ní kód, který provede kontrolu hranic pro datum narození.

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
