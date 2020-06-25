---
title: Podpora vysokého rozlišení DPI
description: Přečtěte si o podpoře v model Windows Forms pro běžné scénáře s vysokým ROZLIŠENÍm a dynamickým DPI. Naučíte se také, jak nakonfigurovat aplikace model Windows Forms pro zajištění vysoké úrovně DPI.
ms.date: 05/16/2017
helpviewer_keywords:
- High DPI in Windows Forms
- Dynamic rescaling in Windows Forms
- Windows Forms layout
- Windows Forms dynamic resizing
ms.assetid: 075ea4c3-900c-4f8a-9dd2-13ea6804346b
ms.openlocfilehash: a9e0766307095da447c772de5a3065c18b7b7154
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325645"
---
# <a name="high-dpi-support-in-windows-forms"></a>Podpora vysokého rozlišení DPI v model Windows Forms

Počínaje .NET Framework 4,7 obsahuje model Windows Forms vylepšení běžných scénářů s vysokým rozlišením DPI a dynamickým DPI. Zde jsou některé z nich:

- Vylepšení škálování a rozložení mnoha model Windows Formsch ovládacích prvků, jako jsou <xref:System.Windows.Forms.MonthCalendar> ovládací prvky a <xref:System.Windows.Forms.CheckedListBox> ovládací prvek.

- Škálování s jedním průchodem.  V .NET Framework 4,6 a starších verzích bylo škálování provedeno prostřednictvím několika průchodů, což způsobilo, že některé ovládací prvky byly zvětšeny, než bylo nutné.

- Podpora pro scénáře dynamického rozlišení DPI, ve kterých uživatel po spuštění model Windows Forms aplikace změní faktor DPI nebo měřítko.

Ve verzích .NET Framework počínaje .NET Framework 4,7 je vylepšená podpora vysokého rozlišení DPI funkce výslovného souhlasu. Aby bylo možné aplikaci využít, je nutné ji nakonfigurovat.

## <a name="configuring-your-windows-forms-app-for-high-dpi-support"></a>Konfigurace aplikace model Windows Forms pro podporu s vysokým rozlišením DPI

Nové funkce model Windows Forms s podporou vysokého rozlišení DPI jsou k dispozici pouze v aplikacích, které cílí na .NET Framework 4,7 a jsou spuštěny v operačních systémech Windows počínaje aktualizací Windows 10 Creators Update.

K nakonfigurování podpory vysokého rozlišení DPI v aplikaci model Windows Forms je třeba provést následující akce:

- Deklarace kompatibility s Windows 10

  Chcete-li to provést, přidejte do souboru manifestu následující:

  ```xml
  <compatibility xmlns="urn:schemas-microsoft-com:compatibility.v1">
    <application>
      <!-- Windows 10 compatibility -->
      <supportedOS Id="{8e0f7a12-bfb3-4fe8-b9a5-48fd50a15a9a}" />
    </application>
  </compatibility>
  ```

- V souboru *app.config* Povolte sledování rozlišení DPI podle monitoru.

  Model Windows Forms zavádí nový [`<System.Windows.Forms.ApplicationConfigurationSection>`](../configure-apps/file-schema/winforms/index.md) prvek pro podporu nových funkcí a přizpůsobení, která začínají .NET Framework 4,7. Chcete-li využívat nové funkce, které podporují vysoké rozlišení DPI, přidejte následující do konfiguračního souboru aplikace.

  ```xml
  <System.Windows.Forms.ApplicationConfigurationSection>
    <add key="DpiAwareness" value="PerMonitorV2" />
  </System.Windows.Forms.ApplicationConfigurationSection>
  ```

  > [!IMPORTANT]
  > V předchozích verzích .NET Framework jste použili manifest pro přidání podpory s vysokým rozlišením DPI. Tento přístup se už nedoporučuje, protože přepisuje nastavení definovaná v souboru app.config.

- Zavolejte statickou <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> metodu.

  Mělo by se jednat o první volání metody v vstupním bodě vaší aplikace. Příklad:

  ```csharp
  static void Main()
  {
      Application.EnableVisualStyles();
      Application.SetCompatibleTextRenderingDefault(false);
      Application.Run(new Form2());
  }
  ```

## <a name="opting-out-of-individual-high-dpi-features"></a>Vypnutí jednotlivých funkcí vysokého rozlišení DPI

Nastavením `DpiAwareness` hodnoty `PerMonitorV2` povolíte všechny funkce pro sledování vysokého rozlišení DPI podporované .NET Frameworkmi verzemi počínaje .NET Framework 4,7. Obvykle je to vhodné pro většinu model Windows Formsch aplikací. Je však možné, že budete chtít odhlásit z jedné nebo více jednotlivých funkcí. Nejdůležitějším důvodem pro to je, že váš stávající kód aplikace již tuto funkci zpracovává.  Například pokud vaše aplikace zpracovává automatické škálování, možná budete chtít zakázat funkci automatické změny velikosti následujícím způsobem:

```xml
<System.Windows.Forms.ApplicationConfigurationSection>
  <add key="DpiAwareness" value="PerMonitorV2" />
  <add key="EnableWindowsFormsHighDpiAutoResizing" value="false" />
</System.Windows.Forms.ApplicationConfigurationSection>
```

Seznam jednotlivých klíčů a jejich hodnot naleznete v tématu [model Windows Forms přidání konfiguračního prvku](../configure-apps/file-schema/winforms/windows-forms-add-configuration-element.md).

## <a name="new-dpi-change-events"></a>Nové události změny v DPI

Počínaje .NET Framework 4,7, tři nové události umožňují programově zpracovat dynamické změny v DPI:

- <xref:System.Windows.Forms.Control.DpiChangedAfterParent>, který se aktivuje, když se změní nastavení DPI pro ovládací prvek programově po události změny DPI nadřazeného ovládacího prvku nebo formuláře.
- <xref:System.Windows.Forms.Control.DpiChangedBeforeParent>, který se aktivuje, když se nastavení DPI pro ovládací prvek změní programově předtím, než dojde k události změny v DPI pro svůj nadřazený ovládací prvek nebo formulář.
- <xref:System.Windows.Forms.Form.DpiChanged>, který se aktivuje, když se změní nastavení DPI na zobrazovacím zařízení, ve kterém je formulář aktuálně zobrazený.

## <a name="new-helper-methods-and-properties"></a>Nové pomocné metody a vlastnosti

.NET Framework 4,7 také přidává řadu nových pomocných metod a vlastností, které poskytují informace o škálování DPI a umožňují provádět škálování DPI. Zde jsou některé z nich:

- <xref:System.Windows.Forms.Control.LogicalToDeviceUnits%2A>, který převede hodnotu z logické na pixely zařízení.

- <xref:System.Windows.Forms.Control.ScaleBitmapLogicalToDevice%2A>, který škáluje rastrový obrázek na logické rozlišení DPI pro zařízení.

- <xref:System.Windows.Forms.Control.DeviceDpi%2A>, což vrátí DPI pro aktuální zařízení.

## <a name="versioning-considerations"></a>Požadavky na správu verzí

Kromě provozu na .NET Framework 4,7 a Windows 10 Creators Update může být aplikace spuštěná také v prostředí, ve kterém není kompatibilní s vysokým rozlišením DPI. V takovém případě budete muset pro svou aplikaci vytvořit zálohu. To můžete provést k provedení [vlastního vykreslování](./controls/user-drawn-controls.md) pro zpracování škálování.

K tomu je potřeba určit i operační systém, na kterém je vaše aplikace spuštěná. To lze provést pomocí kódu podobného následujícímu:

```csharp
// Create a reference to the OS version of Windows 10 Creators Update.
Version OsMinVersion = new Version(10, 0, 15063, 0);

// Access the platform/version of the current OS.
Console.WriteLine(Environment.OSVersion.Platform.ToString());
Console.WriteLine(Environment.OSVersion.VersionString);

// Compare the current version to the minimum required version.
Console.WriteLine(Environment.OSVersion.Version.CompareTo(OsMinVersion));
```

Všimněte si, že aplikace nebude úspěšně detekovat Windows 10, pokud nebyla uvedena jako podporovaný operační systém v manifestu aplikace.

Můžete také ověřit verzi .NET Framework, na které byla aplikace vytvořena:

```csharp
Console.WriteLine(AppDomain.CurrentDomain.SetupInformation.TargetFrameworkName);
```

## <a name="see-also"></a>Viz také

- [model Windows Forms přidat element konfigurace](../configure-apps/file-schema/winforms/windows-forms-add-configuration-element.md)
- [Úprava velikosti a měřítka Windows Forms](adjusting-the-size-and-scale-of-windows-forms.md)
