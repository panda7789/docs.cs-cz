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
# <a name="high-dpi-support-in-windows-forms"></a><span data-ttu-id="ccba0-104">Podpora vysokého rozlišení DPI v model Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ccba0-104">High DPI support in Windows Forms</span></span>

<span data-ttu-id="ccba0-105">Počínaje .NET Framework 4,7 obsahuje model Windows Forms vylepšení běžných scénářů s vysokým rozlišením DPI a dynamickým DPI.</span><span class="sxs-lookup"><span data-stu-id="ccba0-105">Starting with the .NET Framework 4.7, Windows Forms includes enhancements for common high DPI and dynamic DPI scenarios.</span></span> <span data-ttu-id="ccba0-106">Zde jsou některé z nich:</span><span class="sxs-lookup"><span data-stu-id="ccba0-106">These include:</span></span>

- <span data-ttu-id="ccba0-107">Vylepšení škálování a rozložení mnoha model Windows Formsch ovládacích prvků, jako jsou <xref:System.Windows.Forms.MonthCalendar> ovládací prvky a <xref:System.Windows.Forms.CheckedListBox> ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="ccba0-107">Improvements in the scaling and layout of a number of Windows Forms controls, such as the <xref:System.Windows.Forms.MonthCalendar> control and the <xref:System.Windows.Forms.CheckedListBox> control.</span></span>

- <span data-ttu-id="ccba0-108">Škálování s jedním průchodem.</span><span class="sxs-lookup"><span data-stu-id="ccba0-108">Single-pass scaling.</span></span>  <span data-ttu-id="ccba0-109">V .NET Framework 4,6 a starších verzích bylo škálování provedeno prostřednictvím několika průchodů, což způsobilo, že některé ovládací prvky byly zvětšeny, než bylo nutné.</span><span class="sxs-lookup"><span data-stu-id="ccba0-109">In the .NET Framework 4.6 and earlier versions, scaling was performed through multiple passes, which caused some controls to be scaled more than was necessary.</span></span>

- <span data-ttu-id="ccba0-110">Podpora pro scénáře dynamického rozlišení DPI, ve kterých uživatel po spuštění model Windows Forms aplikace změní faktor DPI nebo měřítko.</span><span class="sxs-lookup"><span data-stu-id="ccba0-110">Support for dynamic DPI scenarios in which the user changes the DPI or scale factor after a Windows Forms application has been launched.</span></span>

<span data-ttu-id="ccba0-111">Ve verzích .NET Framework počínaje .NET Framework 4,7 je vylepšená podpora vysokého rozlišení DPI funkce výslovného souhlasu.</span><span class="sxs-lookup"><span data-stu-id="ccba0-111">In versions of the .NET Framework starting with the .NET Framework 4.7, enhanced high DPI support is an opt-in feature.</span></span> <span data-ttu-id="ccba0-112">Aby bylo možné aplikaci využít, je nutné ji nakonfigurovat.</span><span class="sxs-lookup"><span data-stu-id="ccba0-112">You must configure your application to take advantage of it.</span></span>

## <a name="configuring-your-windows-forms-app-for-high-dpi-support"></a><span data-ttu-id="ccba0-113">Konfigurace aplikace model Windows Forms pro podporu s vysokým rozlišením DPI</span><span class="sxs-lookup"><span data-stu-id="ccba0-113">Configuring your Windows Forms app for high DPI support</span></span>

<span data-ttu-id="ccba0-114">Nové funkce model Windows Forms s podporou vysokého rozlišení DPI jsou k dispozici pouze v aplikacích, které cílí na .NET Framework 4,7 a jsou spuštěny v operačních systémech Windows počínaje aktualizací Windows 10 Creators Update.</span><span class="sxs-lookup"><span data-stu-id="ccba0-114">The new Windows Forms features that support high DPI awareness are available only in applications that target the .NET Framework 4.7 and are running on Windows operating systems starting with the Windows 10 Creators Update.</span></span>

<span data-ttu-id="ccba0-115">K nakonfigurování podpory vysokého rozlišení DPI v aplikaci model Windows Forms je třeba provést následující akce:</span><span class="sxs-lookup"><span data-stu-id="ccba0-115">In addition, to configure high DPI support in your Windows Forms application, you must do the following:</span></span>

- <span data-ttu-id="ccba0-116">Deklarace kompatibility s Windows 10</span><span class="sxs-lookup"><span data-stu-id="ccba0-116">Declare compatibility with Windows 10.</span></span>

  <span data-ttu-id="ccba0-117">Chcete-li to provést, přidejte do souboru manifestu následující:</span><span class="sxs-lookup"><span data-stu-id="ccba0-117">To do this, add the following to your manifest file:</span></span>

  ```xml
  <compatibility xmlns="urn:schemas-microsoft-com:compatibility.v1">
    <application>
      <!-- Windows 10 compatibility -->
      <supportedOS Id="{8e0f7a12-bfb3-4fe8-b9a5-48fd50a15a9a}" />
    </application>
  </compatibility>
  ```

- <span data-ttu-id="ccba0-118">V souboru *app.config* Povolte sledování rozlišení DPI podle monitoru.</span><span class="sxs-lookup"><span data-stu-id="ccba0-118">Enable per-monitor DPI awareness in the *app.config* file.</span></span>

  <span data-ttu-id="ccba0-119">Model Windows Forms zavádí nový [`<System.Windows.Forms.ApplicationConfigurationSection>`](../configure-apps/file-schema/winforms/index.md) prvek pro podporu nových funkcí a přizpůsobení, která začínají .NET Framework 4,7.</span><span class="sxs-lookup"><span data-stu-id="ccba0-119">Windows Forms introduces a new [`<System.Windows.Forms.ApplicationConfigurationSection>`](../configure-apps/file-schema/winforms/index.md) element to support new features and customizations added starting with the .NET Framework 4.7.</span></span> <span data-ttu-id="ccba0-120">Chcete-li využívat nové funkce, které podporují vysoké rozlišení DPI, přidejte následující do konfiguračního souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="ccba0-120">To take advantage of the new features that support high DPI, add the following to your application configuration file.</span></span>

  ```xml
  <System.Windows.Forms.ApplicationConfigurationSection>
    <add key="DpiAwareness" value="PerMonitorV2" />
  </System.Windows.Forms.ApplicationConfigurationSection>
  ```

  > [!IMPORTANT]
  > <span data-ttu-id="ccba0-121">V předchozích verzích .NET Framework jste použili manifest pro přidání podpory s vysokým rozlišením DPI.</span><span class="sxs-lookup"><span data-stu-id="ccba0-121">In previous versions of the .NET Framework, you used the manifest to add high DPI support.</span></span> <span data-ttu-id="ccba0-122">Tento přístup se už nedoporučuje, protože přepisuje nastavení definovaná v souboru app.config.</span><span class="sxs-lookup"><span data-stu-id="ccba0-122">This approach is no longer recommended, since it overrides settings defined on the app.config file.</span></span>

- <span data-ttu-id="ccba0-123">Zavolejte statickou <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> metodu.</span><span class="sxs-lookup"><span data-stu-id="ccba0-123">Call the static <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> method.</span></span>

  <span data-ttu-id="ccba0-124">Mělo by se jednat o první volání metody v vstupním bodě vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="ccba0-124">This should be the first method call in your application entry point.</span></span> <span data-ttu-id="ccba0-125">Příklad:</span><span class="sxs-lookup"><span data-stu-id="ccba0-125">For example:</span></span>

  ```csharp
  static void Main()
  {
      Application.EnableVisualStyles();
      Application.SetCompatibleTextRenderingDefault(false);
      Application.Run(new Form2());
  }
  ```

## <a name="opting-out-of-individual-high-dpi-features"></a><span data-ttu-id="ccba0-126">Vypnutí jednotlivých funkcí vysokého rozlišení DPI</span><span class="sxs-lookup"><span data-stu-id="ccba0-126">Opting out of individual high DPI features</span></span>

<span data-ttu-id="ccba0-127">Nastavením `DpiAwareness` hodnoty `PerMonitorV2` povolíte všechny funkce pro sledování vysokého rozlišení DPI podporované .NET Frameworkmi verzemi počínaje .NET Framework 4,7.</span><span class="sxs-lookup"><span data-stu-id="ccba0-127">Setting the `DpiAwareness` value to `PerMonitorV2` enables all high DPI awareness features supported by .NET Framework versions starting with the .NET Framework 4.7.</span></span> <span data-ttu-id="ccba0-128">Obvykle je to vhodné pro většinu model Windows Formsch aplikací.</span><span class="sxs-lookup"><span data-stu-id="ccba0-128">Typically, this is adequate for most Windows Forms applications.</span></span> <span data-ttu-id="ccba0-129">Je však možné, že budete chtít odhlásit z jedné nebo více jednotlivých funkcí.</span><span class="sxs-lookup"><span data-stu-id="ccba0-129">However, you may want to opt out of one or more individual features.</span></span> <span data-ttu-id="ccba0-130">Nejdůležitějším důvodem pro to je, že váš stávající kód aplikace již tuto funkci zpracovává.</span><span class="sxs-lookup"><span data-stu-id="ccba0-130">The most important reason for doing this is that your existing application code already handles that feature.</span></span>  <span data-ttu-id="ccba0-131">Například pokud vaše aplikace zpracovává automatické škálování, možná budete chtít zakázat funkci automatické změny velikosti následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="ccba0-131">For example, if your application handles auto scaling, you might want to disable the auto-resizing feature as follows:</span></span>

```xml
<System.Windows.Forms.ApplicationConfigurationSection>
  <add key="DpiAwareness" value="PerMonitorV2" />
  <add key="EnableWindowsFormsHighDpiAutoResizing" value="false" />
</System.Windows.Forms.ApplicationConfigurationSection>
```

<span data-ttu-id="ccba0-132">Seznam jednotlivých klíčů a jejich hodnot naleznete v tématu [model Windows Forms přidání konfiguračního prvku](../configure-apps/file-schema/winforms/windows-forms-add-configuration-element.md).</span><span class="sxs-lookup"><span data-stu-id="ccba0-132">For a list of individual keys and their values, see [Windows Forms Add Configuration Element](../configure-apps/file-schema/winforms/windows-forms-add-configuration-element.md).</span></span>

## <a name="new-dpi-change-events"></a><span data-ttu-id="ccba0-133">Nové události změny v DPI</span><span class="sxs-lookup"><span data-stu-id="ccba0-133">New DPI change events</span></span>

<span data-ttu-id="ccba0-134">Počínaje .NET Framework 4,7, tři nové události umožňují programově zpracovat dynamické změny v DPI:</span><span class="sxs-lookup"><span data-stu-id="ccba0-134">Starting with the .NET Framework 4.7, three new events allow you to programmatically handle dynamic DPI changes:</span></span>

- <span data-ttu-id="ccba0-135"><xref:System.Windows.Forms.Control.DpiChangedAfterParent>, který se aktivuje, když se změní nastavení DPI pro ovládací prvek programově po události změny DPI nadřazeného ovládacího prvku nebo formuláře.</span><span class="sxs-lookup"><span data-stu-id="ccba0-135"><xref:System.Windows.Forms.Control.DpiChangedAfterParent>, which is fired when the DPI setting for a control is changed programmatically after a DPI change event for it's parent control or form has occurred.</span></span>
- <span data-ttu-id="ccba0-136"><xref:System.Windows.Forms.Control.DpiChangedBeforeParent>, který se aktivuje, když se nastavení DPI pro ovládací prvek změní programově předtím, než dojde k události změny v DPI pro svůj nadřazený ovládací prvek nebo formulář.</span><span class="sxs-lookup"><span data-stu-id="ccba0-136"><xref:System.Windows.Forms.Control.DpiChangedBeforeParent>, which is fired when the DPI setting for a control is changed programmatically before a DPI change event for its parent control or form has occurred.</span></span>
- <span data-ttu-id="ccba0-137"><xref:System.Windows.Forms.Form.DpiChanged>, který se aktivuje, když se změní nastavení DPI na zobrazovacím zařízení, ve kterém je formulář aktuálně zobrazený.</span><span class="sxs-lookup"><span data-stu-id="ccba0-137"><xref:System.Windows.Forms.Form.DpiChanged>, which is fired when the DPI setting changes on the display device where the form is currently displayed.</span></span>

## <a name="new-helper-methods-and-properties"></a><span data-ttu-id="ccba0-138">Nové pomocné metody a vlastnosti</span><span class="sxs-lookup"><span data-stu-id="ccba0-138">New helper methods and properties</span></span>

<span data-ttu-id="ccba0-139">.NET Framework 4,7 také přidává řadu nových pomocných metod a vlastností, které poskytují informace o škálování DPI a umožňují provádět škálování DPI.</span><span class="sxs-lookup"><span data-stu-id="ccba0-139">The .NET Framework 4.7 also adds a number of new helper methods and properties that provide information about DPI scaling and allow you to perform DPI scaling.</span></span> <span data-ttu-id="ccba0-140">Zde jsou některé z nich:</span><span class="sxs-lookup"><span data-stu-id="ccba0-140">These include:</span></span>

- <span data-ttu-id="ccba0-141"><xref:System.Windows.Forms.Control.LogicalToDeviceUnits%2A>, který převede hodnotu z logické na pixely zařízení.</span><span class="sxs-lookup"><span data-stu-id="ccba0-141"><xref:System.Windows.Forms.Control.LogicalToDeviceUnits%2A>, which converts a value from logical to device pixels.</span></span>

- <span data-ttu-id="ccba0-142"><xref:System.Windows.Forms.Control.ScaleBitmapLogicalToDevice%2A>, který škáluje rastrový obrázek na logické rozlišení DPI pro zařízení.</span><span class="sxs-lookup"><span data-stu-id="ccba0-142"><xref:System.Windows.Forms.Control.ScaleBitmapLogicalToDevice%2A>, which scales a bitmap image to the logical DPI for a device.</span></span>

- <span data-ttu-id="ccba0-143"><xref:System.Windows.Forms.Control.DeviceDpi%2A>, což vrátí DPI pro aktuální zařízení.</span><span class="sxs-lookup"><span data-stu-id="ccba0-143"><xref:System.Windows.Forms.Control.DeviceDpi%2A>, which returns the DPI for the current device.</span></span>

## <a name="versioning-considerations"></a><span data-ttu-id="ccba0-144">Požadavky na správu verzí</span><span class="sxs-lookup"><span data-stu-id="ccba0-144">Versioning considerations</span></span>

<span data-ttu-id="ccba0-145">Kromě provozu na .NET Framework 4,7 a Windows 10 Creators Update může být aplikace spuštěná také v prostředí, ve kterém není kompatibilní s vysokým rozlišením DPI.</span><span class="sxs-lookup"><span data-stu-id="ccba0-145">In addition to running on .NET Framework 4.7 and Windows 10 Creators Update, your application may also run in an environment in which it isn't compatible with high DPI improvements.</span></span> <span data-ttu-id="ccba0-146">V takovém případě budete muset pro svou aplikaci vytvořit zálohu.</span><span class="sxs-lookup"><span data-stu-id="ccba0-146">In this case, you'll need to develop a fallback for your application.</span></span> <span data-ttu-id="ccba0-147">To můžete provést k provedení [vlastního vykreslování](./controls/user-drawn-controls.md) pro zpracování škálování.</span><span class="sxs-lookup"><span data-stu-id="ccba0-147">You can do this to perform [custom drawing](./controls/user-drawn-controls.md) to handle scaling.</span></span>

<span data-ttu-id="ccba0-148">K tomu je potřeba určit i operační systém, na kterém je vaše aplikace spuštěná.</span><span class="sxs-lookup"><span data-stu-id="ccba0-148">To do this, you also need to determine the operating system on which your app is running.</span></span> <span data-ttu-id="ccba0-149">To lze provést pomocí kódu podobného následujícímu:</span><span class="sxs-lookup"><span data-stu-id="ccba0-149">You can do that with code like the following:</span></span>

```csharp
// Create a reference to the OS version of Windows 10 Creators Update.
Version OsMinVersion = new Version(10, 0, 15063, 0);

// Access the platform/version of the current OS.
Console.WriteLine(Environment.OSVersion.Platform.ToString());
Console.WriteLine(Environment.OSVersion.VersionString);

// Compare the current version to the minimum required version.
Console.WriteLine(Environment.OSVersion.Version.CompareTo(OsMinVersion));
```

<span data-ttu-id="ccba0-150">Všimněte si, že aplikace nebude úspěšně detekovat Windows 10, pokud nebyla uvedena jako podporovaný operační systém v manifestu aplikace.</span><span class="sxs-lookup"><span data-stu-id="ccba0-150">Note that your application won't successfully detect Windows 10 if it wasn't listed as a supported operating system in the application manifest.</span></span>

<span data-ttu-id="ccba0-151">Můžete také ověřit verzi .NET Framework, na které byla aplikace vytvořena:</span><span class="sxs-lookup"><span data-stu-id="ccba0-151">You can also check the version of the .NET Framework that the application was built against:</span></span>

```csharp
Console.WriteLine(AppDomain.CurrentDomain.SetupInformation.TargetFrameworkName);
```

## <a name="see-also"></a><span data-ttu-id="ccba0-152">Viz také</span><span class="sxs-lookup"><span data-stu-id="ccba0-152">See also</span></span>

- [<span data-ttu-id="ccba0-153">model Windows Forms přidat element konfigurace</span><span class="sxs-lookup"><span data-stu-id="ccba0-153">Windows Forms Add Configuration Element</span></span>](../configure-apps/file-schema/winforms/windows-forms-add-configuration-element.md)
- [<span data-ttu-id="ccba0-154">Úprava velikosti a měřítka Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ccba0-154">Adjusting the Size and Scale of Windows Forms</span></span>](adjusting-the-size-and-scale-of-windows-forms.md)
