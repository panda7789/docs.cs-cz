---
title: "Vysoká DPI podpora v rozhraní Windows Forms"
ms.custom: 
ms.date: 05/16/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- High DPI in Windows Forms
- Dynamic rescaling in Windows Forms
- Windows Forms layout
- Windows Forms dynamic resizing
ms.assetid: 075ea4c3-900c-4f8a-9dd2-13ea6804346b
caps.latest.revision: "3"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a68c9278d4e8092be5c744109e56f7cb52498095
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="high-dpi-support-in-windows-forms"></a>Vysoká DPI podpora v rozhraní Windows Forms

Od verze 4.7 rozhraní .NET Framework, Windows Forms obsahuje vylepšení pro běžné vysoké DPI a scénáře dynamických DPI. Mezi ně patří: 

- Ovládací prvky vylepšení v oblasti škálování a rozložení počtu Windows Forms, jako například <xref:System.Windows.Forms.MonthCalendar> řízení a <xref:System.Windows.Forms.CheckedListBox> ovládacího prvku. 

- Jednoho průchodu škálování.  V rozhraní .NET Framework 4.6 a dřívějších verzích škálování probíhalo prostřednictvím více úpravami, které způsobila některé ovládací prvky měnit jejich velikost více než bylo nezbytné.

- Podpora pro dynamické DPI scénáře, ve kterých uživatel změní Multi-Factor DPI nebo škálování po byla spuštěna aplikace Windows Forms.

Ve verzích rozhraní .NET Framework od verze 4.7 rozhraní .NET Framework je lepší podporu vysoké DPI funkce opt-in. Musíte nakonfigurovat vaše aplikace a využívat jejich výhod.

## <a name="configuring-your-windows-forms-app-for-high-dpi-support"></a>Konfigurace aplikace Windows Forms podpora vysoké DPI

Nové funkce Windows Forms, které podporují vysokou sledování bodů na PALEC jsou k dispozici jenom v aplikacích, které cílí rozhraní .NET Framework 4.7 a běží na operační systémy Windows od verze Windows 10 Creators Update. 

Kromě toho Konfigurace vysoké DPI podpory v aplikaci Windows Forms, je musí provést následující:

- Deklarujte kompatibility s Windows 10.

  Chcete-li to provést, přidejte následující k souboru manifestu:

  ```xml
  <compatibility xmlns="urn:schemas-microsoft.comn:compatibility.v1">
    <application>
      <!-- Windows 10 compatibility -->
      <supportedOS Id="{8e0f7a12-bfb3-4fe8-b9a5-48fd50a15a9a}" />
    </application>
  </compatibility>
  ```

- Povolit sledování DPI za monitorování v *app.config* souboru.

  Windows Forms představuje novou [ `<System.Windows.Forms.ApplicationConfigurationSection>` ](../../../docs/framework/configure-apps/file-schema/winforms/index.md) element pro podporu nových funkcí a přizpůsobení přidat od verze 4.7 rozhraní .NET Framework. Abyste mohli využívat nové funkce, které podporují vysokou DPI, přidejte následující konfigurační soubor aplikace.   

  ```xml
  <System.Windows.Forms.ApplicationConfigurationSection>
    <add key="DpiAwareness" value="PerMonitorV2" />
  </System.Windows.Forms.ApplicationConfigurationSection>      
  ```
   
  > [!IMPORTANT]
  > V předchozích verzích rozhraní .NET Framework používá manifest pro přidání podpory vysoké DPI. Tento přístup je už nedoporučuje, protože přepíše nastavení definované v souboru app.config.
   
- Zavolejte statickou <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> metoda.
   
  To by měl být první volání metody, které ve vaší vstupní bod aplikace. Příklad:
   
  ```csharp
  static void Main()
  {
      Application.EnableVisualStyles();
      Application.SetCompatibleTextRenderingDefault(false);
      Application.Run(new Form2());   
  }
  ```

## <a name="opting-out-of-individual-high-dpi-features"></a>Zrušení jednotlivé funkce vysoké DPI

Nastavení `DpiAwareness` hodnotu `PerMonitorV2` umožňuje všechny vysoké DPI povědomí o funkcích podporovaných jednotlivými od verze 4.7 rozhraní .NET Framework verze rozhraní .NET Framework. Obvykle je to pro většinu aplikací Windows Forms. Můžete však vyjádření výslovného nesouhlasu jeden nebo více jednotlivých funkcí. Nejdůležitější důvodem pro tento je, že váš stávající kód aplikace již zpracovává této funkce.  Pokud vaše aplikace zpracovává automatické škálování, můžete chtít zakázat funkci Změna velikosti automaticky následujícím způsobem:

```xml
<System.Windows.Forms.ApplicationConfigurationSection>
  <add key="DpiAwareness" value="PerMonitorV2" />
  <add key="EnableWindowsFormsHighDpiAutoResizing" value="false" /> 
</System.Windows.Forms.ApplicationConfigurationSection>    
```

Seznam jednotlivých klíčů a jejich hodnoty, najdete v části [přidejte Element konfigurace aplikace Windows Forms](../../../docs/framework/configure-apps/file-schema/winforms/windows-forms-add-configuration-element.md).

## <a name="new-dpi-change-events"></a>Nové události změny DPI

Od verze 4.7 rozhraní .NET Framework, tři nové události umožňují programově zpracovávat dynamické změny DPI:

- <xref:System.Windows.Forms.Control.DpiChangedAfterParent>, který je aktivována, když DPI nastavení pro ovládací prvek změněna programově po události změn DPI pro jeho nadřazenému ovládacímu prvku nebo formuláře došlo k chybě.
- <xref:System.Windows.Forms.Control.DpiChangedBeforeParent>, který je aktivována, jestliže prostřednictvím kódu programu změně nastavení DPI pro ovládací prvek před událost změna DPI pro jeho nadřazenému ovládacímu prvku nebo formuláře došlo k chybě.
- <xref:System.Windows.Forms.Form.DpiChanged>, který je aktivována, jestliže nastavení DPI změny v zobrazení zařízení, kde je aktuálně zobrazený formuláře.

## <a name="new-helper-methods-and-properties"></a>Nové pomocné metody a vlastnosti

Rozhraní .NET Framework 4.7 také přidá číslo nové pomocné metody a vlastnosti, které poskytují informace o Škálování DPI a slouží k provádění Škálování DPI. Mezi ně patří:

- <xref:System.Windows.Forms.Control.LogicalToDeviceUnits%2A>, která převede hodnotu z logické pixelů zařízení.

- <xref:System.Windows.Forms.Control.ScaleBitmapLogicalToDevice%2A>, který přizpůsobí rastrového obrázku na logické DPI pro zařízení.

- <xref:System.Windows.Forms.Control.DeviceDpi%2A>, která vrací DPI pro aktuální zařízení.

## <a name="versioning-considerations"></a>Aspekty správy verzí

Kromě systémem 4.7 rozhraní .NET Framework a Windows 10 Creators Update, může aplikace také spustit v prostředí, ve kterém není kompatibilní s vysokou vylepšení DPI. V takovém případě budete potřebovat k vývoji zálohu pro aplikaci. Musíte provést [vlastní kreslení](./controls/user-drawn-controls.md) pro zpracování škálování.

To pokud chcete udělat, musíte taky určit operační systém, na kterém aplikace běží. Můžete to udělat pomocí kódu takto:

```csharp
// Create a reference to the OS version of Windows 10 Creators Update.
Version OsMinVersion = new Version(10, 0, 15063, 0);

// Access the platform/version of the current OS.
Console.WriteLine(Environment.OSVersion.Platform.ToString());
Console.WriteLine(Environment.OSVersion.VersionString);

// Compare the current version to the minimum required version.
Console.WriteLine(Environment.OSVersion.Version.CompareTo(OsMinVersion));
```

Všimněte si, že vaše aplikace nerozpozná úspěšně Windows 10 Pokud nebyl uveden jako podporovaný operační systém v manifestu aplikace.

Můžete se taky podívat na verzi rozhraní .NET Framework, která byla vytvořena pro:

```csharp
Console.WriteLine(AppDomain.CurrentDomain.SetupInformation.TargetFrameworkName);
```

## <a name="see-also"></a>Viz také

[Přidejte konfigurační prvek Windows Forms](../../../docs/framework/configure-apps/file-schema/winforms/windows-forms-add-configuration-element.md)  
[Úprava velikosti a měřítka Windows Forms](../../../docs/framework/winforms/adjusting-the-size-and-scale-of-windows-forms.md)
