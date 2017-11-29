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
ms.openlocfilehash: a2461c507c0d2a27f1c2bdfe85327d11318b17ee
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="high-dpi-support-in-windows-forms"></a><span data-ttu-id="f8d8b-102">Vysoká DPI podpora v rozhraní Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f8d8b-102">High DPI support in Windows Forms</span></span>

<span data-ttu-id="f8d8b-103">Od verze 4.7 rozhraní .NET Framework, Windows Forms obsahuje vylepšení pro běžné vysoké DPI a scénáře dynamických DPI.</span><span class="sxs-lookup"><span data-stu-id="f8d8b-103">Starting with the .NET Framework 4.7, Windows Forms includes enhancements for common high DPI and dynamic DPI scenarios.</span></span> <span data-ttu-id="f8d8b-104">Mezi ně patří:</span><span class="sxs-lookup"><span data-stu-id="f8d8b-104">These include:</span></span> 

- <span data-ttu-id="f8d8b-105">Ovládací prvky vylepšení v oblasti škálování a rozložení počtu Windows Forms, jako například <xref:System.Windows.Forms.MonthCalendar> řízení a <xref:System.Windows.Forms.CheckedListBox> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="f8d8b-105">Improvements in the scaling and layout of a number of Windows Forms controls, such as the <xref:System.Windows.Forms.MonthCalendar> control and the <xref:System.Windows.Forms.CheckedListBox> control.</span></span> 

- <span data-ttu-id="f8d8b-106">Jednoho průchodu škálování.</span><span class="sxs-lookup"><span data-stu-id="f8d8b-106">Single-pass scaling.</span></span>  <span data-ttu-id="f8d8b-107">V rozhraní .NET Framework 4.6 a dřívějších verzích škálování probíhalo prostřednictvím více úpravami, které způsobila některé ovládací prvky měnit jejich velikost více než bylo nezbytné.</span><span class="sxs-lookup"><span data-stu-id="f8d8b-107">In the .NET Framework 4.6 and earlier versions, scaling was performed through multiple passes, which caused some controls to be scaled more than was necessary.</span></span>

- <span data-ttu-id="f8d8b-108">Podpora pro dynamické DPI scénáře, ve kterých uživatel změní Multi-Factor DPI nebo škálování po byla spuštěna aplikace Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="f8d8b-108">Support for dynamic DPI scenarios in which the user changes the DPI or scale factor after a Windows Forms application has been launched.</span></span>

<span data-ttu-id="f8d8b-109">Ve verzích rozhraní .NET Framework od verze 4.7 rozhraní .NET Framework je lepší podporu vysoké DPI funkce opt-in.</span><span class="sxs-lookup"><span data-stu-id="f8d8b-109">In versions of the .NET Framework starting with the .NET Framework 4.7, enhanced high DPI support is an opt-in feature.</span></span> <span data-ttu-id="f8d8b-110">Musíte nakonfigurovat vaše aplikace a využívat jejich výhod.</span><span class="sxs-lookup"><span data-stu-id="f8d8b-110">You must configure your application to take advantage of it.</span></span>

## <a name="configuring-your-windows-forms-app-for-high-dpi-support"></a><span data-ttu-id="f8d8b-111">Konfigurace aplikace Windows Forms podpora vysoké DPI</span><span class="sxs-lookup"><span data-stu-id="f8d8b-111">Configuring your Windows Forms app for high DPI support</span></span>

<span data-ttu-id="f8d8b-112">Nové funkce Windows Forms, které podporují vysokou sledování bodů na PALEC jsou k dispozici jenom v aplikacích, které cílí rozhraní .NET Framework 4.7 a běží na operační systémy Windows od verze Windows 10 Creators Update.</span><span class="sxs-lookup"><span data-stu-id="f8d8b-112">The new Windows Forms features that support high DPI awareness are available only in applications that target the .NET Framework 4.7 and are running on Windows operating systems starting with the Windows 10 Creators Update.</span></span> 

<span data-ttu-id="f8d8b-113">Kromě toho Konfigurace vysoké DPI podpory v aplikaci Windows Forms, je musí provést následující:</span><span class="sxs-lookup"><span data-stu-id="f8d8b-113">In addition, to configure high DPI support in your Windows Forms application, you must do the following:</span></span>

- <span data-ttu-id="f8d8b-114">Deklarujte kompatibility s Windows 10.</span><span class="sxs-lookup"><span data-stu-id="f8d8b-114">Declare compatibility with Windows 10.</span></span>

  <span data-ttu-id="f8d8b-115">Chcete-li to provést, přidejte následující k souboru manifestu:</span><span class="sxs-lookup"><span data-stu-id="f8d8b-115">To do this, add the following to your manifest file:</span></span>

  ```xml
  <compatibility xmlns="urn:schemas-microsoft.comn:compatibility.v1">
    <application>
      <!-- Windows 10 compatibility -->
      <supportedOS Id="{8e0f7a12-bfb3-4fe8-b9a5-48fd50a15a9a}" />
    </application>
  </compatibility>
  ```

- <span data-ttu-id="f8d8b-116">Povolit sledování DPI za monitorování v *app.config* souboru.</span><span class="sxs-lookup"><span data-stu-id="f8d8b-116">Enable per-monitor DPI awareness in the *app.config* file.</span></span>

  <span data-ttu-id="f8d8b-117">Windows Forms představuje novou [ `<System.Windows.Forms.ApplicationConfigurationSection>` ](../../../docs/framework/configure-apps/file-schema/winforms/index.md) element pro podporu nových funkcí a přizpůsobení přidat od verze 4.7 rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f8d8b-117">Windows Forms introduces a new [`<System.Windows.Forms.ApplicationConfigurationSection>`](../../../docs/framework/configure-apps/file-schema/winforms/index.md) element to support new features and customizations added starting with the .NET Framework 4.7.</span></span> <span data-ttu-id="f8d8b-118">Abyste mohli využívat nové funkce, které podporují vysokou DPI, přidejte následující konfigurační soubor aplikace.</span><span class="sxs-lookup"><span data-stu-id="f8d8b-118">To take advantage of the new features that support high DPI, add the following to your application configuration file.</span></span>   

  ```xml
  <System.Windows.Forms.ApplicationConfigurationSection>
    <add key="DpiAwareness" value="PerMonitorV2" />
  </System.Windows.Forms.ApplicationConfigurationSection>      
  ```
   
  > [!IMPORTANT]
  > <span data-ttu-id="f8d8b-119">V předchozích verzích rozhraní .NET Framework používá manifest pro přidání podpory vysoké DPI.</span><span class="sxs-lookup"><span data-stu-id="f8d8b-119">In previous versions of the .NET Framework, you used the manifest to add high DPI support.</span></span> <span data-ttu-id="f8d8b-120">Tento přístup je už nedoporučuje, protože přepíše nastavení definované v souboru app.config.</span><span class="sxs-lookup"><span data-stu-id="f8d8b-120">This approach is no longer recommended, since it overrides settings defined on the app.config file.</span></span>
   
- <span data-ttu-id="f8d8b-121">Zavolejte statickou <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="f8d8b-121">Call the static <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> method.</span></span>
   
  <span data-ttu-id="f8d8b-122">To by měl být první volání metody, které ve vaší vstupní bod aplikace.</span><span class="sxs-lookup"><span data-stu-id="f8d8b-122">This should be the first method call in your application entry point.</span></span> <span data-ttu-id="f8d8b-123">Příklad:</span><span class="sxs-lookup"><span data-stu-id="f8d8b-123">For example:</span></span>
   
  ```csharp
  static void Main()
  {
      Application.EnableVisualStyles();
      Application.SetCompatibleTextRenderingDefault(false);
      Application.Run(new Form2());   
  }
  ```

## <a name="opting-out-of-individual-high-dpi-features"></a><span data-ttu-id="f8d8b-124">Zrušení jednotlivé funkce vysoké DPI</span><span class="sxs-lookup"><span data-stu-id="f8d8b-124">Opting out of individual high DPI features</span></span>

<span data-ttu-id="f8d8b-125">Nastavení `DpiAwareness` hodnotu `PerMonitorV2` umožňuje všechny vysoké DPI povědomí o funkcích podporovaných jednotlivými od verze 4.7 rozhraní .NET Framework verze rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f8d8b-125">Setting the `DpiAwareness` value to `PerMonitorV2` enables all high DPI awareness features supported by .NET Framework versions starting with the .NET Framework 4.7.</span></span> <span data-ttu-id="f8d8b-126">Obvykle je to pro většinu aplikací Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="f8d8b-126">Typically, this is adequate for most Windows Forms applications.</span></span> <span data-ttu-id="f8d8b-127">Můžete však vyjádření výslovného nesouhlasu jeden nebo více jednotlivých funkcí.</span><span class="sxs-lookup"><span data-stu-id="f8d8b-127">However, you may want to opt out of one or more individual features.</span></span> <span data-ttu-id="f8d8b-128">Nejdůležitější důvodem pro tento je, že váš stávající kód aplikace již zpracovává této funkce.</span><span class="sxs-lookup"><span data-stu-id="f8d8b-128">The most important reason for doing this is that your existing application code already handles that feature.</span></span>  <span data-ttu-id="f8d8b-129">Pokud vaše aplikace zpracovává automatické škálování, můžete chtít zakázat funkci Změna velikosti automaticky následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="f8d8b-129">For example, if your application handles auto scaling, you might want to disable the auto-resizing feature as follows:</span></span>

```xml
<System.Windows.Forms.ApplicationConfigurationSection>
  <add key="DpiAwareness" value="PerMonitorV2" />
  <add key="EnableWindowsFormsHighDpiAutoResizing" value="false" /> 
</System.Windows.Forms.ApplicationConfigurationSection>    
```

<span data-ttu-id="f8d8b-130">Seznam jednotlivých klíčů a jejich hodnoty, najdete v části [přidejte Element konfigurace aplikace Windows Forms](../../../docs/framework/configure-apps/file-schema/winforms/windows-forms-add-configuration-element.md).</span><span class="sxs-lookup"><span data-stu-id="f8d8b-130">For a list of individual keys and their values, see [Windows Forms Add Configuration Element](../../../docs/framework/configure-apps/file-schema/winforms/windows-forms-add-configuration-element.md).</span></span>

## <a name="new-dpi-change-events"></a><span data-ttu-id="f8d8b-131">Nové události změny DPI</span><span class="sxs-lookup"><span data-stu-id="f8d8b-131">New DPI change events</span></span>

<span data-ttu-id="f8d8b-132">Od verze 4.7 rozhraní .NET Framework, tři nové události umožňují programově zpracovávat dynamické změny DPI:</span><span class="sxs-lookup"><span data-stu-id="f8d8b-132">Starting with the .NET Framework 4.7, three new events allow you to programmatically handle dynamic DPI changes:</span></span>

- <span data-ttu-id="f8d8b-133"><xref:System.Windows.Forms.Control.DpiChangedAfterParent>, který je aktivována, když DPI nastavení pro ovládací prvek změněna programově po události změn DPI pro jeho nadřazenému ovládacímu prvku nebo formuláře došlo k chybě.</span><span class="sxs-lookup"><span data-stu-id="f8d8b-133"><xref:System.Windows.Forms.Control.DpiChangedAfterParent>, which is fired when the DPI setting for a control is changed programmatically after a DPI change event for it's parent control or form has occurred.</span></span>
- <span data-ttu-id="f8d8b-134"><xref:System.Windows.Forms.Control.DpiChangedBeforeParent>, který je aktivována, jestliže prostřednictvím kódu programu změně nastavení DPI pro ovládací prvek před událost změna DPI pro jeho nadřazenému ovládacímu prvku nebo formuláře došlo k chybě.</span><span class="sxs-lookup"><span data-stu-id="f8d8b-134"><xref:System.Windows.Forms.Control.DpiChangedBeforeParent>, which is fired when the DPI setting for a control is changed programmatically before a DPI change event for its parent control or form has occurred.</span></span>
- <span data-ttu-id="f8d8b-135"><xref:System.Windows.Forms.Form.DpiChanged>, který je aktivována, jestliže nastavení DPI změny v zobrazení zařízení, kde je aktuálně zobrazený formuláře.</span><span class="sxs-lookup"><span data-stu-id="f8d8b-135"><xref:System.Windows.Forms.Form.DpiChanged>, which is fired when the DPI setting changes on the display device where the form is currently displayed.</span></span>

## <a name="new-helper-methods-and-properties"></a><span data-ttu-id="f8d8b-136">Nové pomocné metody a vlastnosti</span><span class="sxs-lookup"><span data-stu-id="f8d8b-136">New helper methods and properties</span></span>

<span data-ttu-id="f8d8b-137">Rozhraní .NET Framework 4.7 také přidá číslo nové pomocné metody a vlastnosti, které poskytují informace o Škálování DPI a slouží k provádění Škálování DPI.</span><span class="sxs-lookup"><span data-stu-id="f8d8b-137">The .NET Framework 4.7 also adds a number of new helper methods and properties that provide information about DPI scaling and allow you to perform DPI scaling.</span></span> <span data-ttu-id="f8d8b-138">Mezi ně patří:</span><span class="sxs-lookup"><span data-stu-id="f8d8b-138">These include:</span></span>

- <span data-ttu-id="f8d8b-139"><xref:System.Windows.Forms.Control.LogicalToDeviceUnits%2A>, která převede hodnotu z logické pixelů zařízení.</span><span class="sxs-lookup"><span data-stu-id="f8d8b-139"><xref:System.Windows.Forms.Control.LogicalToDeviceUnits%2A>, which converts a value from logical to device pixels.</span></span>

- <span data-ttu-id="f8d8b-140"><xref:System.Windows.Forms.Control.ScaleBitmapLogicalToDevice%2A>, který přizpůsobí rastrového obrázku na logické DPI pro zařízení.</span><span class="sxs-lookup"><span data-stu-id="f8d8b-140"><xref:System.Windows.Forms.Control.ScaleBitmapLogicalToDevice%2A>, which scales a bitmap image to the logical DPI for a device.</span></span>

- <span data-ttu-id="f8d8b-141"><xref:System.Windows.Forms.Control.DeviceDpi%2A>, která vrací DPI pro aktuální zařízení.</span><span class="sxs-lookup"><span data-stu-id="f8d8b-141"><xref:System.Windows.Forms.Control.DeviceDpi%2A>, which returns the DPI for the current device.</span></span>

## <a name="versioning-considerations"></a><span data-ttu-id="f8d8b-142">Aspekty správy verzí</span><span class="sxs-lookup"><span data-stu-id="f8d8b-142">Versioning considerations</span></span>

<span data-ttu-id="f8d8b-143">Kromě systémem 4.7 rozhraní .NET Framework a Windows 10 Creators Update, může aplikace také spustit v prostředí, ve kterém není kompatibilní s vysokou vylepšení DPI.</span><span class="sxs-lookup"><span data-stu-id="f8d8b-143">In addition to running on .NET Framework 4.7 and Windows 10 Creators Update, your application may also run in an environment in which it isn't compatible with high DPI improvements.</span></span> <span data-ttu-id="f8d8b-144">V takovém případě budete potřebovat k vývoji zálohu pro aplikaci.</span><span class="sxs-lookup"><span data-stu-id="f8d8b-144">In this case, you'll need to develop a fallback for your application.</span></span> <span data-ttu-id="f8d8b-145">Musíte provést [vlastní kreslení](./controls/user-drawn-controls.md) pro zpracování škálování.</span><span class="sxs-lookup"><span data-stu-id="f8d8b-145">You can do this to perform [custom drawing](./controls/user-drawn-controls.md) to handle scaling.</span></span>

<span data-ttu-id="f8d8b-146">To pokud chcete udělat, musíte taky určit operační systém, na kterém aplikace běží.</span><span class="sxs-lookup"><span data-stu-id="f8d8b-146">To do this, you also need to determine the operating system on which your app is running.</span></span> <span data-ttu-id="f8d8b-147">Můžete to udělat pomocí kódu takto:</span><span class="sxs-lookup"><span data-stu-id="f8d8b-147">You can do that with code like the following:</span></span>

```csharp
// Create a reference to the OS version of Windows 10 Creators Update.
Version OsMinVersion = new Version(10, 0, 15063, 0);

// Access the platform/version of the current OS.
Console.WriteLine(Environment.OSVersion.Platform.ToString());
Console.WriteLine(Environment.OSVersion.VersionString);

// Compare the current version to the minimum required version.
Console.WriteLine(Environment.OSVersion.Version.CompareTo(OsMinVersion));
```

<span data-ttu-id="f8d8b-148">Všimněte si, že vaše aplikace nerozpozná úspěšně Windows 10 Pokud nebyl uveden jako podporovaný operační systém v manifestu aplikace.</span><span class="sxs-lookup"><span data-stu-id="f8d8b-148">Note that your application won't successfully detect Windows 10 if it wasn't listed as a supported operating system in the application manifest.</span></span>

<span data-ttu-id="f8d8b-149">Můžete se taky podívat na verzi rozhraní .NET Framework, která byla vytvořena pro:</span><span class="sxs-lookup"><span data-stu-id="f8d8b-149">You can also check the version of the .NET Framework that the application was built against:</span></span>

```csharp
Console.WriteLine(AppDomain.CurrentDomain.SetupInformation.TargetFrameworkName);
```

## <a name="see-also"></a><span data-ttu-id="f8d8b-150">Viz také</span><span class="sxs-lookup"><span data-stu-id="f8d8b-150">See also</span></span>

[<span data-ttu-id="f8d8b-151">Přidejte konfigurační prvek Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f8d8b-151">Windows Forms Add Configuration Element</span></span>](../../../docs/framework/configure-apps/file-schema/winforms/windows-forms-add-configuration-element.md)  
[<span data-ttu-id="f8d8b-152">Úprava velikosti a měřítka Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f8d8b-152">Adjusting the Size and Scale of Windows Forms</span></span>](../../../docs/framework/winforms/adjusting-the-size-and-scale-of-windows-forms.md)
