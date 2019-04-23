---
title: Zakázání sledování DPI v sadě Visual Studio
description: Tento článek popisuje omezení návrháře formulářů Windows na monitorech HDPI a jak spustit aplikaci Visual Studio jako nepodporující DPI proces.
ms.date: 04/05/2019
ms.prod: visual-studio-windows
ms.technology: vs-ide-designers
author: gewarren
ms.author: gewarren
ms.custom: seoapril2019
ms.openlocfilehash: e52debea382033417afe0bd47f899af1666192bc
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59181376"
---
# <a name="disable-dpi-awareness-in-visual-studio"></a><span data-ttu-id="e0de2-103">Zakázání sledování DPI v sadě Visual Studio</span><span class="sxs-lookup"><span data-stu-id="e0de2-103">Disable DPI-awareness in Visual Studio</span></span>

<span data-ttu-id="e0de2-104">Visual Studio je bodů na palec (DPI) vědět aplikaci, což znamená, že zobrazení škáluje automaticky.</span><span class="sxs-lookup"><span data-stu-id="e0de2-104">Visual Studio is a dots per inch (DPI) aware application, which means the display scales automatically.</span></span> <span data-ttu-id="e0de2-105">Pokud aplikace uvádí, že není s ohledem na DPI, škáluje operační systém aplikace jako rastrový obrázek.</span><span class="sxs-lookup"><span data-stu-id="e0de2-105">If an application states that it's not DPI-aware, the operating system scales the application as a bitmap.</span></span> <span data-ttu-id="e0de2-106">Toto chování se také nazývá virtualizace DPI.</span><span class="sxs-lookup"><span data-stu-id="e0de2-106">This behavior is also called DPI virtualization.</span></span> <span data-ttu-id="e0de2-107">Aplikace stále domnívá, že se spouští ve 100 % škálování nebo 96 dpi.</span><span class="sxs-lookup"><span data-stu-id="e0de2-107">The application still thinks that it's running at 100% scaling, or 96 dpi.</span></span>

<span data-ttu-id="e0de2-108">Tento článek popisuje omezení návrháře formulářů Windows na monitorech HDPI a jak spustit aplikaci Visual Studio jako nepodporující DPI proces.</span><span class="sxs-lookup"><span data-stu-id="e0de2-108">This article discusses the limitations of Windows Forms Designer on HDPI monitors and how to run Visual Studio as a DPI-unaware process.</span></span>

## <a name="windows-forms-designer-on-hdpi-monitors"></a><span data-ttu-id="e0de2-109">Návrhář formulářů Windows na monitorech HDPI</span><span class="sxs-lookup"><span data-stu-id="e0de2-109">Windows Forms Designer on HDPI monitors</span></span>

<span data-ttu-id="e0de2-110">**Návrháře formulářů Windows** v sadě Visual Studio nemá škálování podpory.</span><span class="sxs-lookup"><span data-stu-id="e0de2-110">The **Windows Forms Designer** in Visual Studio doesn't have scaling support.</span></span> <span data-ttu-id="e0de2-111">To způsobí, že problémy zobrazení při otevření některé formulářů v **Návrháře formulářů Windows** na vysokým počtem bodů na palec (HDPI) monitorování.</span><span class="sxs-lookup"><span data-stu-id="e0de2-111">This causes display issues when you open some forms in the **Windows Forms Designer** on high dots per inch (HDPI) monitors.</span></span> <span data-ttu-id="e0de2-112">Příklady můžete ovládací prvky se zobrazí překrytí, jak je znázorněno na následujícím obrázku:</span><span class="sxs-lookup"><span data-stu-id="e0de2-112">For examples, controls can appear to overlap as shown in the following image:</span></span>

![Návrhář formulářů Windows na monitoru HDPI](./media/disable-dpi-awareness-visual-studio/win-forms-designer-hdpi.png)

<span data-ttu-id="e0de2-114">Když otevřete formulář v nástrojích pro **Návrháře formulářů Windows** v sadě Visual Studio na monitoru HDPI, aplikace Visual Studio zobrazí žlutý informační pruh v horní části návrháře:</span><span class="sxs-lookup"><span data-stu-id="e0de2-114">When you open a form in the **Windows Forms Designer** in Visual Studio on an HDPI monitor, Visual Studio displays a yellow informational bar at the top of the designer:</span></span>

![Informační panel v sadě Visual Studio k restartování v DPI nepodporující režim](./media/disable-dpi-awareness-visual-studio/scaling-gold-bar.png)

<span data-ttu-id="e0de2-116">Přečte zprávu **škálování na hlavní obrazovce je nastavena na 200 % (192 dpi). To může způsobit problémů s vykreslováním v okně návrháře.**</span><span class="sxs-lookup"><span data-stu-id="e0de2-116">The message reads **Scaling on your main display is set to 200% (192 dpi). This might cause rendering problems in the designer window.**</span></span>

> [!NOTE]
> <span data-ttu-id="e0de2-117">Tento informační panel byla zavedena v sadě Visual Studio 2017 verze 15.8.</span><span class="sxs-lookup"><span data-stu-id="e0de2-117">This informational bar was introduced in Visual Studio 2017 version 15.8.</span></span>

<span data-ttu-id="e0de2-118">Pokud nefungují v návrháři a není potřeba upravit rozložení formuláře, můžete ignorovat informační panel a pokračovat v práci v editoru kódu nebo v jiných typech návrhářů.</span><span class="sxs-lookup"><span data-stu-id="e0de2-118">If you aren't working in the designer and don't need to adjust the layout of your form, you can ignore the informational bar and continue working in the code editor or in other types of designers.</span></span> <span data-ttu-id="e0de2-119">(Můžete také [zakázat oznámení](#disable-notifications) tak, aby informační panel nebude nadále zobrazovat.) Pouze **Návrháře formulářů Windows** má vliv.</span><span class="sxs-lookup"><span data-stu-id="e0de2-119">(You can also [disable notifications](#disable-notifications) so that the informational bar doesn't continue to appear.) Only the **Windows Forms Designer** is affected.</span></span> <span data-ttu-id="e0de2-120">Pokud potřebujete pracovat **Návrháře formulářů Windows**, následující část vám pomůže [problém pomohl vyřešit](#to-resolve-the-display-problem).</span><span class="sxs-lookup"><span data-stu-id="e0de2-120">If you do need to work in the **Windows Forms Designer**, the next section helps you [resolve the problem](#to-resolve-the-display-problem).</span></span>

## <a name="to-resolve-the-display-problem"></a><span data-ttu-id="e0de2-121">Chcete-li vyřešit problém zobrazení</span><span class="sxs-lookup"><span data-stu-id="e0de2-121">To resolve the display problem</span></span>

<span data-ttu-id="e0de2-122">Existují tři možnosti, jak vyřešit problém zobrazení:</span><span class="sxs-lookup"><span data-stu-id="e0de2-122">There are three options to resolve the display problem:</span></span>

1. [<span data-ttu-id="e0de2-123">Restartujte sadu Visual Studio jako nepodporující DPI proces</span><span class="sxs-lookup"><span data-stu-id="e0de2-123">Restart Visual Studio as a DPI-unaware process</span></span>](#restart-visual-studio-as-a-dpi-unaware-process)
2. [<span data-ttu-id="e0de2-124">Přidat položku registru</span><span class="sxs-lookup"><span data-stu-id="e0de2-124">Add a registry entry</span></span>](#add-a-registry-entry)
3. [<span data-ttu-id="e0de2-125">Nastavte zobrazení škálování nastavení na 100 %</span><span class="sxs-lookup"><span data-stu-id="e0de2-125">Set your display scaling setting to 100%</span></span>](#set-your-display-scaling-setting-to-100)

### <a name="restart-visual-studio-as-a-dpi-unaware-process"></a><span data-ttu-id="e0de2-126">Restartujte sadu Visual Studio jako nepodporující DPI proces</span><span class="sxs-lookup"><span data-stu-id="e0de2-126">Restart Visual Studio as a DPI-unaware process</span></span>

<span data-ttu-id="e0de2-127">Visual Studio můžete restartovat jako nepodporující DPI procesu tak, že vyberete možnost v žlutý informační panel.</span><span class="sxs-lookup"><span data-stu-id="e0de2-127">You can restart Visual Studio as a DPI-unaware process by selecting the option on the yellow informational bar.</span></span> <span data-ttu-id="e0de2-128">Toto je upřednostňovaný způsob řešení problému.</span><span class="sxs-lookup"><span data-stu-id="e0de2-128">This is the preferred way of resolving the problem.</span></span>

<span data-ttu-id="e0de2-129">Když Visual Studio spustí jako proces nepodporující DPI, vyřešení problémů rozložení návrháře, ale může zobrazit fuzzy písma.</span><span class="sxs-lookup"><span data-stu-id="e0de2-129">When Visual Studio runs as a DPI-unaware process, the designer layout issues are resolved, but fonts may appear blurry.</span></span> <span data-ttu-id="e0de2-130">Visual Studio zobrazí různé žlutý informační zprávy při spuštění jako nepodporující DPI proces, který říká **sady Visual Studio je spuštěn jako proces nepodporující DPI. Návrháře WPF a XAML se nemusí zobrazit správně.**</span><span class="sxs-lookup"><span data-stu-id="e0de2-130">Visual Studio displays a different yellow informational message when it runs as a DPI-unaware process that says **Visual Studio is running as a DPI-unaware process. WPF and XAML designers might not display correctly.**</span></span> <span data-ttu-id="e0de2-131">Informační panel také nabízí možnost **restartujte Visual Studio jako rozlišením DPI proces**.</span><span class="sxs-lookup"><span data-stu-id="e0de2-131">The informational bar also provides an option to **Restart Visual Studio as a DPI-aware process**.</span></span>

> [!NOTE]
> - <span data-ttu-id="e0de2-132">Pokud měl neukotveno okna nástrojů v sadě Visual Studio, pokud jste vybrali možnost restartuje jako proces nepodporující DPI, může změnit umístění těchto oken nástrojů.</span><span class="sxs-lookup"><span data-stu-id="e0de2-132">If you had undocked tool windows in Visual Studio when you selected the option to restart as a DPI-unaware process, the position of those tool windows may change.</span></span>
> - <span data-ttu-id="e0de2-133">Pokud používáte výchozí profil jazyka Visual Basic, nebo pokud máte **uložit nové projekty při vytvoření** volba vybraná v **nástroje** > **možnosti**  >  **Projekty a řešení**, Visual Studio nelze znovu otevřít váš projekt, když ho restartuje jako proces nepodporující DPI.</span><span class="sxs-lookup"><span data-stu-id="e0de2-133">If you use the default Visual Basic profile, or if you have the **Save new projects when created** option deselected in **Tools** > **Options** > **Projects and Solutions**, Visual Studio cannot reopen your project when it restarts as a DPI-unaware process.</span></span> <span data-ttu-id="e0de2-134">Však můžete otevřít projekt tak, že vyberete ho pod **souboru** > **poslední projekty a řešení**.</span><span class="sxs-lookup"><span data-stu-id="e0de2-134">However, you can open the project by selecting it under **File** > **Recent Projects and Solutions**.</span></span>

<span data-ttu-id="e0de2-135">Je důležité restartovat Visual Studio jako rozlišením DPI proces, až budete hotovi, práci **Návrháře formulářů Windows**.</span><span class="sxs-lookup"><span data-stu-id="e0de2-135">It's important to restart Visual Studio as a DPI-aware process when you're finished working in the **Windows Forms Designer**.</span></span> <span data-ttu-id="e0de2-136">Když je spuštěn jako proces nepodporující DPI, můžete se podívat fuzzy písma a může se zobrazit problémy v jiné návrháře, jako **návrháře XAML**.</span><span class="sxs-lookup"><span data-stu-id="e0de2-136">When it's running as a DPI-unaware process, fonts can look blurry and you may see issues in other designers such as the **XAML Designer**.</span></span> <span data-ttu-id="e0de2-137">Pokud ho zavřete a znovu otevřete Visual Studio, když je spuštěn v režimu nepodporující DPI, stane se rozlišením DPI znovu.</span><span class="sxs-lookup"><span data-stu-id="e0de2-137">If you close and reopen Visual Studio when it's running in DPI-unaware mode, it becomes DPI-aware again.</span></span> <span data-ttu-id="e0de2-138">Můžete také kliknout **restartujte Visual Studio jako rozlišením DPI proces** možnost v informační panel.</span><span class="sxs-lookup"><span data-stu-id="e0de2-138">You can also click the **Restart Visual Studio as a DPI-aware process** option in the informational bar.</span></span>

### <a name="add-a-registry-entry"></a><span data-ttu-id="e0de2-139">Přidat položku registru</span><span class="sxs-lookup"><span data-stu-id="e0de2-139">Add a registry entry</span></span>

<span data-ttu-id="e0de2-140">Visual Studio můžete označit jako nepodporující DPI úpravou registru.</span><span class="sxs-lookup"><span data-stu-id="e0de2-140">You can mark Visual Studio as DPI-unaware by modifying the registry.</span></span> <span data-ttu-id="e0de2-141">Otevřít **Editor registru** a přidání položky do **HKEY_CURRENT_USER\SOFTWARE\Microsoft\Windows NT\CurrentVersion\AppCompatFlags\Layers** podklíč:</span><span class="sxs-lookup"><span data-stu-id="e0de2-141">Open **Registry Editor** and add an entry to the **HKEY_CURRENT_USER\SOFTWARE\Microsoft\Windows NT\CurrentVersion\AppCompatFlags\Layers** subkey:</span></span>

<span data-ttu-id="e0de2-142">**Položka**: V závislosti na tom, jestli používáte Visual Studio 2017 nebo 2019 použijte jednu z těchto hodnot:</span><span class="sxs-lookup"><span data-stu-id="e0de2-142">**Entry**: Depending on whether you're using Visual Studio 2017 or 2019, use one of these values:</span></span>

- <span data-ttu-id="e0de2-143">C:\Program Files (x86)\Microsoft Visual Studio\2017\Community\Common7\IDE\devenv.exe</span><span class="sxs-lookup"><span data-stu-id="e0de2-143">C:\Program Files (x86)\Microsoft Visual Studio\2017\Community\Common7\IDE\devenv.exe</span></span>
- <span data-ttu-id="e0de2-144">C:\Program Files (x86)\Microsoft Visual Studio\2019\Community\Common7\IDE\devenv.exe</span><span class="sxs-lookup"><span data-stu-id="e0de2-144">C:\Program Files (x86)\Microsoft Visual Studio\2019\Community\Common7\IDE\devenv.exe</span></span>

> [!NOTE]
> <span data-ttu-id="e0de2-145">Pokud používáte edici Professional nebo Enterprise sady Visual Studio, nahraďte **komunity** s **Professional** nebo **Enterprise** v položce.</span><span class="sxs-lookup"><span data-stu-id="e0de2-145">If you're using the Professional or Enterprise edition of Visual Studio, replace **Community** with **Professional** or **Enterprise** in the entry.</span></span> <span data-ttu-id="e0de2-146">Také nahraďte podle potřeby písmeno jednotky.</span><span class="sxs-lookup"><span data-stu-id="e0de2-146">Also replace the drive letter as necessary.</span></span>

<span data-ttu-id="e0de2-147">**Typ**: REG_SZ</span><span class="sxs-lookup"><span data-stu-id="e0de2-147">**Type**: REG_SZ</span></span>

<span data-ttu-id="e0de2-148">**Hodnota**: DPIUNAWARE</span><span class="sxs-lookup"><span data-stu-id="e0de2-148">**Value**: DPIUNAWARE</span></span>

> [!NOTE]
> <span data-ttu-id="e0de2-149">Visual Studio zůstane v DPI nepodporující režim, dokud odebrání položky registru.</span><span class="sxs-lookup"><span data-stu-id="e0de2-149">Visual Studio remains in DPI-unaware mode until you remove the registry entry.</span></span>

### <a name="set-your-display-scaling-setting-to-100"></a><span data-ttu-id="e0de2-150">Nastavte zobrazení škálování nastavení na 100 %</span><span class="sxs-lookup"><span data-stu-id="e0de2-150">Set your display scaling setting to 100%</span></span>

<span data-ttu-id="e0de2-151">Pokud chcete nastavit zobrazení nastavení na 100 % změna měřítka ve Windows 10, zadejte **nastavení zobrazení** na hlavním panelu vyhledávacího pole a pak vyberte **změně nastavení zobrazení**.</span><span class="sxs-lookup"><span data-stu-id="e0de2-151">To set your display scaling setting to 100% in Windows 10, type **display settings** in the task bar search box, and then select **Change display settings**.</span></span> <span data-ttu-id="e0de2-152">V **nastavení** okno, nastavte **změnit velikost textu, aplikací a dalších položek** k **100 %**.</span><span class="sxs-lookup"><span data-stu-id="e0de2-152">In the **Settings** window, set **Change the size of text, apps, and other items** to **100%**.</span></span>

<span data-ttu-id="e0de2-153">Nastavení displeje škálování na 100 % může nežádoucí, protože uživatelské rozhraní může být příliš malá, aby byla použitelná.</span><span class="sxs-lookup"><span data-stu-id="e0de2-153">Setting your display scaling to 100% may be undesirable, because it can make the user interface too small to be usable.</span></span>

## <a name="disable-notifications"></a><span data-ttu-id="e0de2-154">Zakázat oznámení</span><span class="sxs-lookup"><span data-stu-id="e0de2-154">Disable notifications</span></span>

<span data-ttu-id="e0de2-155">Můžete se informováni o DPI škálování problémy v sadě Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="e0de2-155">You can choose not to be notified of DPI scaling issues in Visual Studio.</span></span> <span data-ttu-id="e0de2-156">Můžete chtít zakázat oznámení, pokud nepracujete v návrháři, např.</span><span class="sxs-lookup"><span data-stu-id="e0de2-156">You might want to disable notifications if you aren't working in the designer, for example.</span></span>

<span data-ttu-id="e0de2-157">Chcete-li zakázat oznámení, zvolte **nástroje** > **možnosti** otevřít **možnosti** dialogového okna.</span><span class="sxs-lookup"><span data-stu-id="e0de2-157">To disable notifications, choose **Tools** > **Options** to open the **Options** dialog.</span></span> <span data-ttu-id="e0de2-158">Potom kliknutím na možnost **Návrháře formulářů Windows** > **Obecné**a nastavte **DPI škálování oznámení** k **False**.</span><span class="sxs-lookup"><span data-stu-id="e0de2-158">Then, choose **Windows Forms Designer** > **General**, and set **DPI Scaling Notifications** to **False**.</span></span>

![DPI škálování možnost oznámení v sadě Visual Studio](./media/disable-dpi-awareness-visual-studio/notifications-option.png)

<span data-ttu-id="e0de2-160">Pokud chcete později znovu povolit škálování oznámení, nastavte vlastnost na **True**.</span><span class="sxs-lookup"><span data-stu-id="e0de2-160">If you want to later reenable scaling notifications, set the property to **True**.</span></span>

## <a name="troubleshoot"></a><span data-ttu-id="e0de2-161">Řešení potíží</span><span class="sxs-lookup"><span data-stu-id="e0de2-161">Troubleshoot</span></span>

<span data-ttu-id="e0de2-162">Pokud přechod sledování DPI nefunguje podle očekávání v sadě Visual Studio, zkontrolujte, zda máte `dpiAwareness` hodnotu **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Image File provádění Options\devenv.exe**  podklíče v editoru registru.</span><span class="sxs-lookup"><span data-stu-id="e0de2-162">If the DPI-awareness transition isn't working as expected in Visual Studio, check to see if you have the `dpiAwareness` value in the **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Image File Execution Options\devenv.exe** subkey in Registry Editor.</span></span> <span data-ttu-id="e0de2-163">Odstraňte hodnotu, pokud je k dispozici.</span><span class="sxs-lookup"><span data-stu-id="e0de2-163">Delete the value if it's present.</span></span>

## <a name="see-also"></a><span data-ttu-id="e0de2-164">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e0de2-164">See also</span></span>

- [<span data-ttu-id="e0de2-165">Automatická změna měřítka ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e0de2-165">Automatic scaling in Windows Forms</span></span>](automatic-scaling-in-windows-forms.md)
