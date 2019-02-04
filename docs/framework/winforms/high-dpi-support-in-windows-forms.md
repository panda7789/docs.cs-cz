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
ms.openlocfilehash: 8b5ad28fbfd668819b0bcab30c33892679b4bd8c
ms.sourcegitcommit: b8ace47d839f943f785b89e2fff8092b0bf8f565
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/03/2019
ms.locfileid: "55674916"
---
# <a name="high-dpi-support-in-windows-forms"></a><span data-ttu-id="53a5d-102">Podpora vysoké DPI ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="53a5d-102">High DPI support in Windows Forms</span></span>

<span data-ttu-id="53a5d-103">Od verze rozhraní .NET Framework 4.7, Windows Forms obsahuje vylepšení pro běžné vysokého nastavení DPI a scénáře dynamických DPI.</span><span class="sxs-lookup"><span data-stu-id="53a5d-103">Starting with the .NET Framework 4.7, Windows Forms includes enhancements for common high DPI and dynamic DPI scenarios.</span></span> <span data-ttu-id="53a5d-104">Zde jsou některé z nich:</span><span class="sxs-lookup"><span data-stu-id="53a5d-104">These include:</span></span> 

- <span data-ttu-id="53a5d-105">Vylepšení ve škálování a rozložení počtu Windows Forms ovládací prvky, jako <xref:System.Windows.Forms.MonthCalendar> ovládacího prvku a <xref:System.Windows.Forms.CheckedListBox> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="53a5d-105">Improvements in the scaling and layout of a number of Windows Forms controls, such as the <xref:System.Windows.Forms.MonthCalendar> control and the <xref:System.Windows.Forms.CheckedListBox> control.</span></span> 

- <span data-ttu-id="53a5d-106">Škálování jednoho průchodu.</span><span class="sxs-lookup"><span data-stu-id="53a5d-106">Single-pass scaling.</span></span>  <span data-ttu-id="53a5d-107">V rozhraní .NET Framework 4.6 a dřívějších verzích škálování se provádí prostřednictvím několik průchodů, která způsobila některé ovládací prvky škálovat víc než bylo nutné.</span><span class="sxs-lookup"><span data-stu-id="53a5d-107">In the .NET Framework 4.6 and earlier versions, scaling was performed through multiple passes, which caused some controls to be scaled more than was necessary.</span></span>

- <span data-ttu-id="53a5d-108">Podpora pro dynamické DPI scénáře, ve kterých uživatel změní DPI nebo škálovací faktor po aplikace modelu Windows Forms byl spuštěn.</span><span class="sxs-lookup"><span data-stu-id="53a5d-108">Support for dynamic DPI scenarios in which the user changes the DPI or scale factor after a Windows Forms application has been launched.</span></span>

<span data-ttu-id="53a5d-109">Ve verzích rozhraní .NET Framework počínaje .NET Framework 4.7 rozšířenou podporu vysoké rozlišení DPI je přihlašovaná funkce.</span><span class="sxs-lookup"><span data-stu-id="53a5d-109">In versions of the .NET Framework starting with the .NET Framework 4.7, enhanced high DPI support is an opt-in feature.</span></span> <span data-ttu-id="53a5d-110">Musíte nakonfigurovat aplikaci využívat jejich výhod.</span><span class="sxs-lookup"><span data-stu-id="53a5d-110">You must configure your application to take advantage of it.</span></span>

## <a name="configuring-your-windows-forms-app-for-high-dpi-support"></a><span data-ttu-id="53a5d-111">Konfigurace aplikace Windows Forms pro podporu vysoké rozlišení DPI</span><span class="sxs-lookup"><span data-stu-id="53a5d-111">Configuring your Windows Forms app for high DPI support</span></span>

<span data-ttu-id="53a5d-112">Nové funkce Windows Forms, které podporují vysokou rozpoznání nastavení dpi jsou k dispozici pouze v aplikacích, které cílí .NET Framework 4.7 a běží na operačních systémech Windows od verze Windows 10 Creators Update.</span><span class="sxs-lookup"><span data-stu-id="53a5d-112">The new Windows Forms features that support high DPI awareness are available only in applications that target the .NET Framework 4.7 and are running on Windows operating systems starting with the Windows 10 Creators Update.</span></span> 

<span data-ttu-id="53a5d-113">Kromě toho Konfigurace vysoké rozlišení DPI podpory ve vaší aplikaci Windows Forms, je nutné takto:</span><span class="sxs-lookup"><span data-stu-id="53a5d-113">In addition, to configure high DPI support in your Windows Forms application, you must do the following:</span></span>

- <span data-ttu-id="53a5d-114">Deklarujte kompatibilitu s Windows 10.</span><span class="sxs-lookup"><span data-stu-id="53a5d-114">Declare compatibility with Windows 10.</span></span>

  <span data-ttu-id="53a5d-115">Chcete-li to provést, přidejte následující do souboru manifestu:</span><span class="sxs-lookup"><span data-stu-id="53a5d-115">To do this, add the following to your manifest file:</span></span>

  ```xml
  <compatibility xmlns="urn:schemas-microsoft-com:compatibility.v1">
    <application>
      <!-- Windows 10 compatibility -->
      <supportedOS Id="{8e0f7a12-bfb3-4fe8-b9a5-48fd50a15a9a}" />
    </application>
  </compatibility>
  ```

- <span data-ttu-id="53a5d-116">Povolit sledování DPI podle monitoru *app.config* souboru.</span><span class="sxs-lookup"><span data-stu-id="53a5d-116">Enable per-monitor DPI awareness in the *app.config* file.</span></span>

  <span data-ttu-id="53a5d-117">Windows Forms zavádí nový [ `<System.Windows.Forms.ApplicationConfigurationSection>` ](../../../docs/framework/configure-apps/file-schema/winforms/index.md) element na podporu nových funkcí a od verze rozhraní .NET Framework 4.7 přidání vlastního nastavení.</span><span class="sxs-lookup"><span data-stu-id="53a5d-117">Windows Forms introduces a new [`<System.Windows.Forms.ApplicationConfigurationSection>`](../../../docs/framework/configure-apps/file-schema/winforms/index.md) element to support new features and customizations added starting with the .NET Framework 4.7.</span></span> <span data-ttu-id="53a5d-118">Abyste mohli využívat nové funkce, které podporují vysoké rozlišení DPI, přidejte následující konfigurační soubor aplikace.</span><span class="sxs-lookup"><span data-stu-id="53a5d-118">To take advantage of the new features that support high DPI, add the following to your application configuration file.</span></span>   

  ```xml
  <System.Windows.Forms.ApplicationConfigurationSection>
    <add key="DpiAwareness" value="PerMonitorV2" />
  </System.Windows.Forms.ApplicationConfigurationSection>      
  ```
   
  > [!IMPORTANT]
  > <span data-ttu-id="53a5d-119">V předchozích verzích rozhraní .NET Framework použít manifest přidává vysoké rozlišení DPI.</span><span class="sxs-lookup"><span data-stu-id="53a5d-119">In previous versions of the .NET Framework, you used the manifest to add high DPI support.</span></span> <span data-ttu-id="53a5d-120">Tento přístup je už se nedoporučuje, protože přepisuje nastaveních definovaných v souboru app.config.</span><span class="sxs-lookup"><span data-stu-id="53a5d-120">This approach is no longer recommended, since it overrides settings defined on the app.config file.</span></span>
   
- <span data-ttu-id="53a5d-121">Zavolejte statickou <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="53a5d-121">Call the static <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> method.</span></span>
   
  <span data-ttu-id="53a5d-122">To by mělo být prvním volání metoda ve vstupní bod aplikace.</span><span class="sxs-lookup"><span data-stu-id="53a5d-122">This should be the first method call in your application entry point.</span></span> <span data-ttu-id="53a5d-123">Příklad:</span><span class="sxs-lookup"><span data-stu-id="53a5d-123">For example:</span></span>
   
  ```csharp
  static void Main()
  {
      Application.EnableVisualStyles();
      Application.SetCompatibleTextRenderingDefault(false);
      Application.Run(new Form2());   
  }
  ```

## <a name="opting-out-of-individual-high-dpi-features"></a><span data-ttu-id="53a5d-124">Výslovné odhlášení z jednotlivých funkcí vysoké rozlišení DPI</span><span class="sxs-lookup"><span data-stu-id="53a5d-124">Opting out of individual high DPI features</span></span>

<span data-ttu-id="53a5d-125">Nastavení `DpiAwareness` hodnota, která se `PerMonitorV2` umožňuje všechny vysokou funkce povědomí o DPI podporovaných verzí rozhraní .NET Framework počínaje .NET Framework 4.7.</span><span class="sxs-lookup"><span data-stu-id="53a5d-125">Setting the `DpiAwareness` value to `PerMonitorV2` enables all high DPI awareness features supported by .NET Framework versions starting with the .NET Framework 4.7.</span></span> <span data-ttu-id="53a5d-126">Obvykle je to dostatečné pro většinu aplikací Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="53a5d-126">Typically, this is adequate for most Windows Forms applications.</span></span> <span data-ttu-id="53a5d-127">Však můžete vyjádřit výslovný nesouhlas jeden nebo více jednotlivých funkcí.</span><span class="sxs-lookup"><span data-stu-id="53a5d-127">However, you may want to opt out of one or more individual features.</span></span> <span data-ttu-id="53a5d-128">Nejdůležitější důvod, proč to je, že váš stávající kód aplikace již zpracovává tuto funkci.</span><span class="sxs-lookup"><span data-stu-id="53a5d-128">The most important reason for doing this is that your existing application code already handles that feature.</span></span>  <span data-ttu-id="53a5d-129">Pokud vaše aplikace se stará o automatické škálování, můžete chtít zakázat funkci automatickou změnu velikosti, následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="53a5d-129">For example, if your application handles auto scaling, you might want to disable the auto-resizing feature as follows:</span></span>

```xml
<System.Windows.Forms.ApplicationConfigurationSection>
  <add key="DpiAwareness" value="PerMonitorV2" />
  <add key="EnableWindowsFormsHighDpiAutoResizing" value="false" /> 
</System.Windows.Forms.ApplicationConfigurationSection>    
```

<span data-ttu-id="53a5d-130">Seznam jednotlivých klíče a jejich hodnoty, najdete v části [přidat Element konfigurace aplikace Windows Forms](../../../docs/framework/configure-apps/file-schema/winforms/windows-forms-add-configuration-element.md).</span><span class="sxs-lookup"><span data-stu-id="53a5d-130">For a list of individual keys and their values, see [Windows Forms Add Configuration Element](../../../docs/framework/configure-apps/file-schema/winforms/windows-forms-add-configuration-element.md).</span></span>

## <a name="new-dpi-change-events"></a><span data-ttu-id="53a5d-131">Nové události změny DPI</span><span class="sxs-lookup"><span data-stu-id="53a5d-131">New DPI change events</span></span>

<span data-ttu-id="53a5d-132">Tři nové události od verze rozhraní .NET Framework 4.7, umožňují programově zpracovávat dynamické DPI změny:</span><span class="sxs-lookup"><span data-stu-id="53a5d-132">Starting with the .NET Framework 4.7, three new events allow you to programmatically handle dynamic DPI changes:</span></span>

- <span data-ttu-id="53a5d-133"><xref:System.Windows.Forms.Control.DpiChangedAfterParent>, která je vyvolána při nastavení hodnoty DPI pro ovládací prvek je programově změnit po události DPI změny pro nadřazený prvek nebo formuláře došlo k chybě.</span><span class="sxs-lookup"><span data-stu-id="53a5d-133"><xref:System.Windows.Forms.Control.DpiChangedAfterParent>, which is fired when the DPI setting for a control is changed programmatically after a DPI change event for it's parent control or form has occurred.</span></span>
- <span data-ttu-id="53a5d-134"><xref:System.Windows.Forms.Control.DpiChangedBeforeParent>, která je vyvolána při nastavení hodnoty DPI pro ovládací prvek se změní prostřednictvím kódu programu před DPI události změn pro jeho nadřazenému ovládacímu prvku nebo formuláře došlo k chybě.</span><span class="sxs-lookup"><span data-stu-id="53a5d-134"><xref:System.Windows.Forms.Control.DpiChangedBeforeParent>, which is fired when the DPI setting for a control is changed programmatically before a DPI change event for its parent control or form has occurred.</span></span>
- <span data-ttu-id="53a5d-135"><xref:System.Windows.Forms.Form.DpiChanged>, která je vyvolána při nastavení hodnoty DPI změní na zobrazovací zařízení, ve kterém se nyní zobrazí formulář.</span><span class="sxs-lookup"><span data-stu-id="53a5d-135"><xref:System.Windows.Forms.Form.DpiChanged>, which is fired when the DPI setting changes on the display device where the form is currently displayed.</span></span>

## <a name="new-helper-methods-and-properties"></a><span data-ttu-id="53a5d-136">Nové pomocné metody a vlastnosti</span><span class="sxs-lookup"><span data-stu-id="53a5d-136">New helper methods and properties</span></span>

<span data-ttu-id="53a5d-137">Rozhraní .NET Framework 4.7 také přidává několik nových pomocné metody a vlastnosti, které poskytují informace o Škálování DPI a umožňují provádět Škálování DPI.</span><span class="sxs-lookup"><span data-stu-id="53a5d-137">The .NET Framework 4.7 also adds a number of new helper methods and properties that provide information about DPI scaling and allow you to perform DPI scaling.</span></span> <span data-ttu-id="53a5d-138">Zde jsou některé z nich:</span><span class="sxs-lookup"><span data-stu-id="53a5d-138">These include:</span></span>

- <span data-ttu-id="53a5d-139"><xref:System.Windows.Forms.Control.LogicalToDeviceUnits%2A>, která převede hodnotu z logické pixelů zařízení.</span><span class="sxs-lookup"><span data-stu-id="53a5d-139"><xref:System.Windows.Forms.Control.LogicalToDeviceUnits%2A>, which converts a value from logical to device pixels.</span></span>

- <span data-ttu-id="53a5d-140"><xref:System.Windows.Forms.Control.ScaleBitmapLogicalToDevice%2A>, která se škáluje rastrový obrázek na logické DPI pro zařízení.</span><span class="sxs-lookup"><span data-stu-id="53a5d-140"><xref:System.Windows.Forms.Control.ScaleBitmapLogicalToDevice%2A>, which scales a bitmap image to the logical DPI for a device.</span></span>

- <span data-ttu-id="53a5d-141"><xref:System.Windows.Forms.Control.DeviceDpi%2A>, který vrátí DPI pro aktuální zařízení.</span><span class="sxs-lookup"><span data-stu-id="53a5d-141"><xref:System.Windows.Forms.Control.DeviceDpi%2A>, which returns the DPI for the current device.</span></span>

## <a name="versioning-considerations"></a><span data-ttu-id="53a5d-142">Aspekty správy verzí</span><span class="sxs-lookup"><span data-stu-id="53a5d-142">Versioning considerations</span></span>

<span data-ttu-id="53a5d-143">Kromě spuštění v rozhraní .NET Framework 4.7 a Windows 10 Creators Update, může aplikace také spustit v prostředí, ve kterém není kompatibilní s vysokou vylepšení DPI.</span><span class="sxs-lookup"><span data-stu-id="53a5d-143">In addition to running on .NET Framework 4.7 and Windows 10 Creators Update, your application may also run in an environment in which it isn't compatible with high DPI improvements.</span></span> <span data-ttu-id="53a5d-144">V takovém případě budete potřebovat k vývoji jako základní pro vaši aplikaci.</span><span class="sxs-lookup"><span data-stu-id="53a5d-144">In this case, you'll need to develop a fallback for your application.</span></span> <span data-ttu-id="53a5d-145">Lze to provést [vlastního vykreslení](./controls/user-drawn-controls.md) zpracování škálování.</span><span class="sxs-lookup"><span data-stu-id="53a5d-145">You can do this to perform [custom drawing](./controls/user-drawn-controls.md) to handle scaling.</span></span>

<span data-ttu-id="53a5d-146">Provedete to tak, musíte také určit operační systém, na kterém je spuštěná aplikace.</span><span class="sxs-lookup"><span data-stu-id="53a5d-146">To do this, you also need to determine the operating system on which your app is running.</span></span> <span data-ttu-id="53a5d-147">Můžete to udělat s kódem, jako je následující:</span><span class="sxs-lookup"><span data-stu-id="53a5d-147">You can do that with code like the following:</span></span>

```csharp
// Create a reference to the OS version of Windows 10 Creators Update.
Version OsMinVersion = new Version(10, 0, 15063, 0);

// Access the platform/version of the current OS.
Console.WriteLine(Environment.OSVersion.Platform.ToString());
Console.WriteLine(Environment.OSVersion.VersionString);

// Compare the current version to the minimum required version.
Console.WriteLine(Environment.OSVersion.Version.CompareTo(OsMinVersion));
```

<span data-ttu-id="53a5d-148">Všimněte si, že vaše aplikace nezjistí úspěšně Windows 10 Pokud nebyl uveden jako podporovaný operační systém v manifestu aplikace.</span><span class="sxs-lookup"><span data-stu-id="53a5d-148">Note that your application won't successfully detect Windows 10 if it wasn't listed as a supported operating system in the application manifest.</span></span>

<span data-ttu-id="53a5d-149">Můžete také zkontrolovat verzi rozhraní .NET Framework, kterou byla aplikace vytvořena proti:</span><span class="sxs-lookup"><span data-stu-id="53a5d-149">You can also check the version of the .NET Framework that the application was built against:</span></span>

```csharp
Console.WriteLine(AppDomain.CurrentDomain.SetupInformation.TargetFrameworkName);
```

## <a name="see-also"></a><span data-ttu-id="53a5d-150">Viz také:</span><span class="sxs-lookup"><span data-stu-id="53a5d-150">See also</span></span>

- [<span data-ttu-id="53a5d-151">Přidání konfiguračního prvku Windows Forms</span><span class="sxs-lookup"><span data-stu-id="53a5d-151">Windows Forms Add Configuration Element</span></span>](../../../docs/framework/configure-apps/file-schema/winforms/windows-forms-add-configuration-element.md)
- [<span data-ttu-id="53a5d-152">Úprava velikosti a měřítka Windows Forms</span><span class="sxs-lookup"><span data-stu-id="53a5d-152">Adjusting the Size and Scale of Windows Forms</span></span>](../../../docs/framework/winforms/adjusting-the-size-and-scale-of-windows-forms.md)
