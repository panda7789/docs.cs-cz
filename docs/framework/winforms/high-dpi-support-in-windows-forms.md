---
title: Podpora vysoké DPI ve Windows Forms
ms.date: 05/16/2017
helpviewer_keywords:
- High DPI in Windows Forms
- Dynamic rescaling in Windows Forms
- Windows Forms layout
- Windows Forms dynamic resizing
ms.assetid: 075ea4c3-900c-4f8a-9dd2-13ea6804346b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1641702c7b1c3d3b0e83c59a96529de70f699d17
ms.sourcegitcommit: 69bf8b719d4c289eec7b45336d0b933dd7927841
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2019
ms.locfileid: "57843606"
---
# <a name="high-dpi-support-in-windows-forms"></a>Podpora vysoké DPI ve Windows Forms

Od verze rozhraní .NET Framework 4.7, Windows Forms obsahuje vylepšení pro běžné vysokého nastavení DPI a scénáře dynamických DPI. Zde jsou některé z nich:

- Vylepšení ve škálování a rozložení počtu Windows Forms ovládací prvky, jako <xref:System.Windows.Forms.MonthCalendar> ovládacího prvku a <xref:System.Windows.Forms.CheckedListBox> ovládacího prvku.

- Škálování jednoho průchodu.  V rozhraní .NET Framework 4.6 a dřívějších verzích škálování se provádí prostřednictvím několik průchodů, která způsobila některé ovládací prvky škálovat víc než bylo nutné.

- Podpora pro dynamické DPI scénáře, ve kterých uživatel změní DPI nebo škálovací faktor po aplikace modelu Windows Forms byl spuštěn.

Ve verzích rozhraní .NET Framework počínaje .NET Framework 4.7 rozšířenou podporu vysoké rozlišení DPI je přihlašovaná funkce. Musíte nakonfigurovat aplikaci využívat jejich výhod.

## <a name="configuring-your-windows-forms-app-for-high-dpi-support"></a>Konfigurace aplikace Windows Forms pro podporu vysoké rozlišení DPI

Nové funkce Windows Forms, které podporují vysokou rozpoznání nastavení dpi jsou k dispozici pouze v aplikacích, které cílí .NET Framework 4.7 a běží na operačních systémech Windows od verze Windows 10 Creators Update.

Kromě toho Konfigurace vysoké rozlišení DPI podpory ve vaší aplikaci Windows Forms, je nutné takto:

- Deklarujte kompatibilitu s Windows 10.

  Chcete-li to provést, přidejte následující do souboru manifestu:

  ```xml
  <compatibility xmlns="urn:schemas-microsoft-com:compatibility.v1">
    <application>
      <!-- Windows 10 compatibility -->
      <supportedOS Id="{8e0f7a12-bfb3-4fe8-b9a5-48fd50a15a9a}" />
    </application>
  </compatibility>
  ```

- Povolit sledování DPI podle monitoru *app.config* souboru.

  Windows Forms zavádí nový [ `<System.Windows.Forms.ApplicationConfigurationSection>` ](../configure-apps/file-schema/winforms/index.md) element na podporu nových funkcí a od verze rozhraní .NET Framework 4.7 přidání vlastního nastavení. Abyste mohli využívat nové funkce, které podporují vysoké rozlišení DPI, přidejte následující konfigurační soubor aplikace.

  ```xml
  <System.Windows.Forms.ApplicationConfigurationSection>
    <add key="DpiAwareness" value="PerMonitorV2" />
  </System.Windows.Forms.ApplicationConfigurationSection>
  ```

  > [!IMPORTANT]
  > V předchozích verzích rozhraní .NET Framework použít manifest přidává vysoké rozlišení DPI. Tento přístup je už se nedoporučuje, protože přepisuje nastaveních definovaných v souboru app.config.

- Zavolejte statickou <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> metody.

  To by mělo být prvním volání metoda ve vstupní bod aplikace. Příklad:

  ```csharp
  static void Main()
  {
      Application.EnableVisualStyles();
      Application.SetCompatibleTextRenderingDefault(false);
      Application.Run(new Form2());
  }
  ```

## <a name="opting-out-of-individual-high-dpi-features"></a>Výslovné odhlášení z jednotlivých funkcí vysoké rozlišení DPI

Nastavení `DpiAwareness` hodnota, která se `PerMonitorV2` umožňuje všechny vysokou funkce povědomí o DPI podporovaných verzí rozhraní .NET Framework počínaje .NET Framework 4.7. Obvykle je to dostatečné pro většinu aplikací Windows Forms. Však můžete vyjádřit výslovný nesouhlas jeden nebo více jednotlivých funkcí. Nejdůležitější důvod, proč to je, že váš stávající kód aplikace již zpracovává tuto funkci.  Pokud vaše aplikace se stará o automatické škálování, můžete chtít zakázat funkci automatickou změnu velikosti, následujícím způsobem:

```xml
<System.Windows.Forms.ApplicationConfigurationSection>
  <add key="DpiAwareness" value="PerMonitorV2" />
  <add key="EnableWindowsFormsHighDpiAutoResizing" value="false" />
</System.Windows.Forms.ApplicationConfigurationSection>
```

Seznam jednotlivých klíče a jejich hodnoty, najdete v části [přidat Element konfigurace aplikace Windows Forms](../configure-apps/file-schema/winforms/windows-forms-add-configuration-element.md).

## <a name="new-dpi-change-events"></a>Nové události změny DPI

Tři nové události od verze rozhraní .NET Framework 4.7, umožňují programově zpracovávat dynamické DPI změny:

- <xref:System.Windows.Forms.Control.DpiChangedAfterParent>, která je vyvolána při nastavení hodnoty DPI pro ovládací prvek je programově změnit po události DPI změny pro nadřazený prvek nebo formuláře došlo k chybě.
- <xref:System.Windows.Forms.Control.DpiChangedBeforeParent>, která je vyvolána při nastavení hodnoty DPI pro ovládací prvek se změní prostřednictvím kódu programu před DPI události změn pro jeho nadřazenému ovládacímu prvku nebo formuláře došlo k chybě.
- <xref:System.Windows.Forms.Form.DpiChanged>, která je vyvolána při nastavení hodnoty DPI změní na zobrazovací zařízení, ve kterém se nyní zobrazí formulář.

## <a name="new-helper-methods-and-properties"></a>Nové pomocné metody a vlastnosti

Rozhraní .NET Framework 4.7 také přidává několik nových pomocné metody a vlastnosti, které poskytují informace o Škálování DPI a umožňují provádět Škálování DPI. Zde jsou některé z nich:

- <xref:System.Windows.Forms.Control.LogicalToDeviceUnits%2A>, která převede hodnotu z logické pixelů zařízení.

- <xref:System.Windows.Forms.Control.ScaleBitmapLogicalToDevice%2A>, která se škáluje rastrový obrázek na logické DPI pro zařízení.

- <xref:System.Windows.Forms.Control.DeviceDpi%2A>, který vrátí DPI pro aktuální zařízení.

## <a name="versioning-considerations"></a>Aspekty správy verzí

Kromě spuštění v rozhraní .NET Framework 4.7 a Windows 10 Creators Update, může aplikace také spustit v prostředí, ve kterém není kompatibilní s vysokou vylepšení DPI. V takovém případě budete potřebovat k vývoji jako základní pro vaši aplikaci. Lze to provést [vlastního vykreslení](./controls/user-drawn-controls.md) zpracování škálování.

Provedete to tak, musíte také určit operační systém, na kterém je spuštěná aplikace. Můžete to udělat s kódem, jako je následující:

```csharp
// Create a reference to the OS version of Windows 10 Creators Update.
Version OsMinVersion = new Version(10, 0, 15063, 0);

// Access the platform/version of the current OS.
Console.WriteLine(Environment.OSVersion.Platform.ToString());
Console.WriteLine(Environment.OSVersion.VersionString);

// Compare the current version to the minimum required version.
Console.WriteLine(Environment.OSVersion.Version.CompareTo(OsMinVersion));
```

Všimněte si, že vaše aplikace nezjistí úspěšně Windows 10 Pokud nebyl uveden jako podporovaný operační systém v manifestu aplikace.

Můžete také zkontrolovat verzi rozhraní .NET Framework, kterou byla aplikace vytvořena proti:

```csharp
Console.WriteLine(AppDomain.CurrentDomain.SetupInformation.TargetFrameworkName);
```

## <a name="see-also"></a>Viz také:

- [Přidání konfiguračního prvku Windows Forms](../configure-apps/file-schema/winforms/windows-forms-add-configuration-element.md)
- [Úprava velikosti a měřítka Windows Forms](adjusting-the-size-and-scale-of-windows-forms.md)
