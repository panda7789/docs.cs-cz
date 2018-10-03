---
title: Zakázání sledování DPI v sadě Visual Studio
description: Tento článek popisuje omezení pro návrháře formulářů Windows na monitorech HDPI a jak spustit aplikaci Visual Studio jako nepodporující DPI proces.
ms.date: 08/14/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-designers
author: gewarren
ms.author: gewarren
ms.openlocfilehash: 7ecffedbe536f293945227d817e507f012816737
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/02/2018
ms.locfileid: "48037038"
---
# <a name="disable-dpi-awareness-in-visual-studio"></a><span data-ttu-id="2bf8b-103">Zakázání sledování DPI v sadě Visual Studio</span><span class="sxs-lookup"><span data-stu-id="2bf8b-103">Disable DPI-awareness in Visual Studio</span></span>

<span data-ttu-id="2bf8b-104">Visual Studio je bodů na palec (DPI) vědět aplikaci, což znamená, že zobrazení škáluje automaticky.</span><span class="sxs-lookup"><span data-stu-id="2bf8b-104">Visual Studio is a dots per inch (DPI) aware application, which means the display scales automatically.</span></span> <span data-ttu-id="2bf8b-105">Pokud aplikace uvádí, že není s ohledem na DPI, škáluje operační systém aplikace jako rastrový obrázek.</span><span class="sxs-lookup"><span data-stu-id="2bf8b-105">If an application states that it's not DPI-aware, the operating system scales the application as a bitmap.</span></span> <span data-ttu-id="2bf8b-106">Toto chování se také nazývá virtualizace DPI.</span><span class="sxs-lookup"><span data-stu-id="2bf8b-106">This behavior is also called DPI virtualization.</span></span> <span data-ttu-id="2bf8b-107">Aplikace stále domnívá, že se spouští ve 100 % škálování nebo 96 dpi.</span><span class="sxs-lookup"><span data-stu-id="2bf8b-107">The application still thinks that it's running at 100% scaling, or 96 dpi.</span></span>

## <a name="windows-forms-designer-on-hdpi-monitors"></a><span data-ttu-id="2bf8b-108">Návrhář formulářů Windows na monitorech HDPI</span><span class="sxs-lookup"><span data-stu-id="2bf8b-108">Windows Forms Designer on HDPI monitors</span></span>

<span data-ttu-id="2bf8b-109">**Návrháře formulářů Windows** v sadě Visual Studio nemá škálování podpory.</span><span class="sxs-lookup"><span data-stu-id="2bf8b-109">The **Windows Forms Designer** in Visual Studio doesn't have scaling support.</span></span> <span data-ttu-id="2bf8b-110">To způsobí, že problémy zobrazení při otevření některé formulářů v **Návrháře formulářů Windows** na vysokým počtem bodů na palec (HDPI) monitorování.</span><span class="sxs-lookup"><span data-stu-id="2bf8b-110">This causes display issues when you open some forms in the **Windows Forms Designer** on high dots per inch (HDPI) monitors.</span></span> <span data-ttu-id="2bf8b-111">Příklady můžete ovládací prvky se zobrazí překrytí, jak je znázorněno na následujícím obrázku:</span><span class="sxs-lookup"><span data-stu-id="2bf8b-111">For examples, controls can appear to overlap as shown in the following image:</span></span>

![Návrhář formulářů Windows na monitoru HDPI](media/disable-dpi-awareness-visual-studio/win-forms-designer-hdpi.png)

<span data-ttu-id="2bf8b-113">V sadě Visual Studio 2017 verze 15,8 a novější, když otevřete formulář v nástrojích pro **Návrháře formulářů Windows** na monitoru HDPI sady Visual Studio zobrazí žlutý informační pruh v horní části návrháře:</span><span class="sxs-lookup"><span data-stu-id="2bf8b-113">In Visual Studio 2017 version 15.8 and later, when you open a form in the **Windows Forms Designer** on an HDPI monitor, Visual Studio displays a yellow informational bar at the top of the designer:</span></span>

![Informační panel v sadě Visual Studio k restartování v DPI nepodporující režim](media/disable-dpi-awareness-visual-studio/scaling-gold-bar.png)

<span data-ttu-id="2bf8b-115">Přečte zprávu **škálování na hlavní obrazovce je nastavena na 200 % (192 dpi). To může způsobit problémů s vykreslováním v okně návrháře.**</span><span class="sxs-lookup"><span data-stu-id="2bf8b-115">The message reads **Scaling on your main display is set to 200% (192 dpi). This might cause rendering problems in the designer window.**</span></span>

<span data-ttu-id="2bf8b-116">Pokud nefungují v návrháři a není potřeba upravit rozložení formuláře, můžete ignorovat informační panel a pokračovat v práci v editoru kódu nebo v jiných typech návrhářů.</span><span class="sxs-lookup"><span data-stu-id="2bf8b-116">If you aren't working in the designer and don't need to adjust the layout of your form, you can ignore the informational bar and continue working in the code editor or in other types of designers.</span></span> <span data-ttu-id="2bf8b-117">Pouze **Návrháře formulářů Windows** má vliv.</span><span class="sxs-lookup"><span data-stu-id="2bf8b-117">Only the **Windows Forms Designer** is affected.</span></span> <span data-ttu-id="2bf8b-118">Pokud potřebujete pracovat **Návrháře formulářů Windows**, následující část vám pomůže [problém pomohl vyřešit](#to-resolve-the-problem).</span><span class="sxs-lookup"><span data-stu-id="2bf8b-118">If you do need to work in the **Windows Forms Designer**, the next section helps you [resolve the problem](#to-resolve-the-problem).</span></span>

## <a name="to-resolve-the-problem"></a><span data-ttu-id="2bf8b-119">Chcete-li vyřešit tento problém</span><span class="sxs-lookup"><span data-stu-id="2bf8b-119">To resolve the problem</span></span>

<span data-ttu-id="2bf8b-120">Existují tři možnosti, jak vyřešit problém zobrazení.</span><span class="sxs-lookup"><span data-stu-id="2bf8b-120">There are three options to resolve the display problem.</span></span>

### <a name="restart-visual-studio-as-a-dpi-unaware-process"></a><span data-ttu-id="2bf8b-121">Restartujte sadu Visual Studio jako nepodporující DPI proces</span><span class="sxs-lookup"><span data-stu-id="2bf8b-121">Restart Visual Studio as a DPI-unaware process</span></span>

<span data-ttu-id="2bf8b-122">Visual Studio můžete restartovat jako nepodporující DPI procesu tak, že vyberete možnost v žlutý informační panel.</span><span class="sxs-lookup"><span data-stu-id="2bf8b-122">You can restart Visual Studio as a DPI-unaware process by selecting the option on the yellow informational bar.</span></span> <span data-ttu-id="2bf8b-123">Toto je upřednostňovaný způsob řešení problému.</span><span class="sxs-lookup"><span data-stu-id="2bf8b-123">This is the preferred way of resolving the problem.</span></span>

<span data-ttu-id="2bf8b-124">Když Visual Studio spustí jako proces nepodporující DPI, vyřešení problémů rozložení návrháře, ale může zobrazit fuzzy písma.</span><span class="sxs-lookup"><span data-stu-id="2bf8b-124">When Visual Studio runs as a DPI-unaware process, the designer layout issues are resolved, but fonts may appear blurry.</span></span> <span data-ttu-id="2bf8b-125">Visual Studio zobrazí různé žlutý informační zprávy při spuštění jako nepodporující DPI proces, který říká **sady Visual Studio je spuštěn jako proces nepodporující DPI. Návrháře WPF a XAML se nemusí zobrazit správně.**</span><span class="sxs-lookup"><span data-stu-id="2bf8b-125">Visual Studio displays a different yellow informational message when it runs as a DPI-unaware process that says **Visual Studio is running as a DPI-unaware process. WPF and XAML designers might not display correctly.**</span></span> <span data-ttu-id="2bf8b-126">Informační panel také nabízí možnost **restartujte Visual Studio jako rozlišením DPI proces**.</span><span class="sxs-lookup"><span data-stu-id="2bf8b-126">The informational bar also provides an option to **Restart Visual Studio as a DPI-aware process**.</span></span>

> [!NOTE]
> - <span data-ttu-id="2bf8b-127">Pokud měl neukotveno okna nástrojů v sadě Visual Studio, pokud jste vybrali možnost restartuje jako proces nepodporující DPI, může změnit umístění těchto oken nástrojů.</span><span class="sxs-lookup"><span data-stu-id="2bf8b-127">If you had undocked tool windows in Visual Studio when you selected the option to restart as a DPI-unaware process, the position of those tool windows may change.</span></span>
> - <span data-ttu-id="2bf8b-128">Pokud používáte výchozí profil jazyka Visual Basic, nebo pokud máte **uložit nové projekty při vytvoření** volba vybraná v **nástroje** > **možnosti**  >  **Projekty a řešení**, Visual Studio nelze znovu otevřít váš projekt, když ho restartuje jako proces nepodporující DPI.</span><span class="sxs-lookup"><span data-stu-id="2bf8b-128">If you use the default Visual Basic profile, or if you have the **Save new projects when created** option deselected in **Tools** > **Options** > **Projects and Solutions**, Visual Studio cannot reopen your project when it restarts as a DPI-unaware process.</span></span> <span data-ttu-id="2bf8b-129">Však můžete otevřít projekt tak, že vyberete ho pod **souboru** > **poslední projekty a řešení**.</span><span class="sxs-lookup"><span data-stu-id="2bf8b-129">However, you can open the project by selecting it under **File** > **Recent Projects and Solutions**.</span></span>

<span data-ttu-id="2bf8b-130">Je důležité restartovat Visual Studio jako rozlišením DPI proces, až budete hotovi, práci **Návrháře formulářů Windows**.</span><span class="sxs-lookup"><span data-stu-id="2bf8b-130">It's important to restart Visual Studio as a DPI-aware process when you're finished working in the **Windows Forms Designer**.</span></span> <span data-ttu-id="2bf8b-131">Když je spuštěn jako proces nepodporující DPI, můžete se podívat fuzzy písma a může se zobrazit problémy v jiné návrháře, jako **návrháře XAML**.</span><span class="sxs-lookup"><span data-stu-id="2bf8b-131">When it's running as a DPI-unaware process, fonts can look blurry and you may see issues in other designers such as the **XAML Designer**.</span></span> <span data-ttu-id="2bf8b-132">Pokud ho zavřete a znovu otevřete Visual Studio, když je spuštěn v režimu nepodporující DPI, stane se rozlišením DPI znovu.</span><span class="sxs-lookup"><span data-stu-id="2bf8b-132">If you close and reopen Visual Studio when it's running in DPI-unaware mode, it becomes DPI-aware again.</span></span> <span data-ttu-id="2bf8b-133">Můžete také kliknout **restartujte Visual Studio jako rozlišením DPI proces** možnost v informační panel.</span><span class="sxs-lookup"><span data-stu-id="2bf8b-133">You can also click the **Restart Visual Studio as a DPI-aware process** option in the informational bar.</span></span>

### <a name="add-a-registry-entry"></a><span data-ttu-id="2bf8b-134">Přidat položku registru</span><span class="sxs-lookup"><span data-stu-id="2bf8b-134">Add a registry entry</span></span>

<span data-ttu-id="2bf8b-135">Visual Studio můžete označit jako nepodporující DPI úpravou registru.</span><span class="sxs-lookup"><span data-stu-id="2bf8b-135">You can mark Visual Studio as DPI-unaware by modifying the registry.</span></span> <span data-ttu-id="2bf8b-136">Otevřít **Editor registru** a přidání položky do **HKEY_CURRENT_USER\SOFTWARE\Microsoft\Windows NT\CurrentVersion\AppCompatFlags\Layers** podklíč:</span><span class="sxs-lookup"><span data-stu-id="2bf8b-136">Open **Registry Editor** and add an entry to the **HKEY_CURRENT_USER\SOFTWARE\Microsoft\Windows NT\CurrentVersion\AppCompatFlags\Layers** subkey:</span></span>

<span data-ttu-id="2bf8b-137">**Položka**: % ProgramFiles (x86) %\Microsoft Visual Studio\2017\Community\Common7\IDE\devenv.exe</span><span class="sxs-lookup"><span data-stu-id="2bf8b-137">**Entry**: %ProgramFiles(x86)%\Microsoft Visual Studio\2017\Community\Common7\IDE\devenv.exe</span></span>

   > [!NOTE]
   > <span data-ttu-id="2bf8b-138">Pokud používáte edici Professional nebo Enterprise sady Visual Studio 2017, nahraďte **komunity** s **Professional** nebo **Enterprise** v položce.</span><span class="sxs-lookup"><span data-stu-id="2bf8b-138">If you're using the Professional or Enterprise edition of Visual Studio 2017, replace **Community** with **Professional** or **Enterprise** in the entry.</span></span>

<span data-ttu-id="2bf8b-139">**Typ**: REG_SZ</span><span class="sxs-lookup"><span data-stu-id="2bf8b-139">**Type**: REG_SZ</span></span>

<span data-ttu-id="2bf8b-140">**Hodnota**: DPIUNAWARE</span><span class="sxs-lookup"><span data-stu-id="2bf8b-140">**Value**: DPIUNAWARE</span></span>

> [!NOTE]
> <span data-ttu-id="2bf8b-141">Visual Studio zůstane v DPI nepodporující režim, dokud odebrání položky registru.</span><span class="sxs-lookup"><span data-stu-id="2bf8b-141">Visual Studio remains in DPI-unaware mode until you remove the registry entry.</span></span>

### <a name="set-your-display-scaling-setting-to-100"></a><span data-ttu-id="2bf8b-142">Nastavte zobrazení škálování nastavení na 100 %</span><span class="sxs-lookup"><span data-stu-id="2bf8b-142">Set your display scaling setting to 100%</span></span>

<span data-ttu-id="2bf8b-143">Pokud chcete nastavit zobrazení nastavení na 100 % změna měřítka ve Windows 10, zadejte **nastavení zobrazení** na hlavním panelu vyhledávacího pole a pak vyberte **změně nastavení zobrazení**.</span><span class="sxs-lookup"><span data-stu-id="2bf8b-143">To set your display scaling setting to 100% in Windows 10, type **display settings** in the task bar search box, and then select **Change display settings**.</span></span> <span data-ttu-id="2bf8b-144">V **nastavení** okno, nastavte **změnit velikost textu, aplikací a dalších položek** k **100 %**.</span><span class="sxs-lookup"><span data-stu-id="2bf8b-144">In the **Settings** window, set **Change the size of text, apps, and other items** to **100%**.</span></span>

<span data-ttu-id="2bf8b-145">Nastavení displeje škálování na 100 % může nežádoucí, protože uživatelské rozhraní může být příliš malá, aby byla použitelná.</span><span class="sxs-lookup"><span data-stu-id="2bf8b-145">Setting your display scaling to 100% may be undesirable, because it can make the user interface too small to be usable.</span></span>

## <a name="see-also"></a><span data-ttu-id="2bf8b-146">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2bf8b-146">See also</span></span>

- [<span data-ttu-id="2bf8b-147">Automatická změna měřítka ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="2bf8b-147">Automatic scaling in Windows Forms</span></span>](automatic-scaling-in-windows-forms.md)