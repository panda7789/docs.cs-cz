---
title: 'Postupy: Poskytnutí nápovědy v aplikaci Windows'
ms.date: 03/30/2017
helpviewer_keywords:
- Help [Windows Forms], Windows applications
- HTML Help [Windows Forms], Windows Forms
- Windows applications [Windows Forms], providing Help
- HelpProvider component [Windows Forms]
- forms [Windows Forms], providing Help
ms.assetid: 7c4e5cec-2bd2-4f0b-8d75-c2b88929bd61
ms.openlocfilehash: 19bf6a8de3f9ddd5babd149747df87c54b456aeb
ms.sourcegitcommit: 0d0a6e96737dfe24d3257b7c94f25d9500f383ea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2019
ms.locfileid: "65211369"
---
# <a name="how-to-provide-help-in-a-windows-application"></a><span data-ttu-id="4d7d8-102">Postupy: Poskytnutí nápovědy v aplikaci Windows</span><span class="sxs-lookup"><span data-stu-id="4d7d8-102">How to: Provide Help in a Windows Application</span></span>

<span data-ttu-id="4d7d8-103">Lze použít <xref:System.Windows.Forms.HelpProvider> součásti pro připojení témata nápovědy v souboru nápovědy k určité ovládací prvky v modelu Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="4d7d8-103">You can use of the <xref:System.Windows.Forms.HelpProvider> component to attach Help topics within a Help file to specific controls on Windows Forms.</span></span> <span data-ttu-id="4d7d8-104">Soubor nápovědy může být ve formátu HTML nebo HTMLHelp 1.x nebo větší formátu.</span><span class="sxs-lookup"><span data-stu-id="4d7d8-104">The Help file can be either HTML or HTMLHelp 1.x or greater format.</span></span>

## <a name="provide-help"></a><span data-ttu-id="4d7d8-105">Poskytnutí nápovědy</span><span class="sxs-lookup"><span data-stu-id="4d7d8-105">Provide Help</span></span>

1. <span data-ttu-id="4d7d8-106">V sadě Visual Studio z **nástrojů**, přetáhněte <xref:System.Windows.Forms.HelpProvider> komponentu do formuláře.</span><span class="sxs-lookup"><span data-stu-id="4d7d8-106">In Visual Studio, from the **Toolbox**, drag a <xref:System.Windows.Forms.HelpProvider> component to your form.</span></span>

     <span data-ttu-id="4d7d8-107">Komponenta se bude nacházet na hlavním panelu v dolní části Návrháře formulářů Windows.</span><span class="sxs-lookup"><span data-stu-id="4d7d8-107">The component will reside in the tray at the bottom of the Windows Forms Designer.</span></span>

2. <span data-ttu-id="4d7d8-108">V **vlastnosti** okno, nastaveno <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> vlastnost v souboru nápovědy chm, .col nebo htm.</span><span class="sxs-lookup"><span data-stu-id="4d7d8-108">In the **Properties** window, set the <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> property to the .chm, .col, or .htm Help file.</span></span>

3. <span data-ttu-id="4d7d8-109">Vyberte jiný ovládací prvek na formuláři máte a v **vlastnosti** okno, nastaveno <xref:System.Windows.Forms.HelpProvider.SetHelpKeyword%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="4d7d8-109">Select another control you have on your form, and in the **Properties** window, set the <xref:System.Windows.Forms.HelpProvider.SetHelpKeyword%2A> property.</span></span>

     <span data-ttu-id="4d7d8-110">Jedná se o řetězec, který předává <xref:System.Windows.Forms.HelpProvider> komponentu do souboru nápovědy k výzvě příslušné téma nápovědy.</span><span class="sxs-lookup"><span data-stu-id="4d7d8-110">This is the string passed through the <xref:System.Windows.Forms.HelpProvider> component to your Help file to summon the appropriate Help topic.</span></span>

4. <span data-ttu-id="4d7d8-111">V **vlastnosti** okno, nastaveno <xref:System.Windows.Forms.HelpProvider.SetHelpNavigator%2A> vlastnost na hodnotu <xref:System.Windows.Forms.HelpNavigator> výčtu.</span><span class="sxs-lookup"><span data-stu-id="4d7d8-111">In the **Properties** window, set the <xref:System.Windows.Forms.HelpProvider.SetHelpNavigator%2A> property to a value of the <xref:System.Windows.Forms.HelpNavigator> enumeration.</span></span>

     <span data-ttu-id="4d7d8-112">Určuje, jakým způsobem **HelpKeyword** vlastnost předána do systému nápovědy.</span><span class="sxs-lookup"><span data-stu-id="4d7d8-112">This determines the way in which the **HelpKeyword** property is passed to the Help system.</span></span> <span data-ttu-id="4d7d8-113">V následující tabulce jsou uvedeny možné nastavení a jejich popisy.</span><span class="sxs-lookup"><span data-stu-id="4d7d8-113">The following table shows the possible settings and their descriptions.</span></span>

    |<span data-ttu-id="4d7d8-114">Název členu</span><span class="sxs-lookup"><span data-stu-id="4d7d8-114">Member Name</span></span>|<span data-ttu-id="4d7d8-115">Popis</span><span class="sxs-lookup"><span data-stu-id="4d7d8-115">Description</span></span>|
    |-----------------|-----------------|
    |<span data-ttu-id="4d7d8-116">AssociateIndex</span><span class="sxs-lookup"><span data-stu-id="4d7d8-116">AssociateIndex</span></span>|<span data-ttu-id="4d7d8-117">Určuje, že index určené téma se provádí v zadané adrese URL.</span><span class="sxs-lookup"><span data-stu-id="4d7d8-117">Specifies that the index for a specified topic is performed in the specified URL.</span></span>|
    |<span data-ttu-id="4d7d8-118">Vyhledávání</span><span class="sxs-lookup"><span data-stu-id="4d7d8-118">Find</span></span>|<span data-ttu-id="4d7d8-119">Určuje, že se zobrazí stránka hledat zadaná adresa URL.</span><span class="sxs-lookup"><span data-stu-id="4d7d8-119">Specifies that the search page of a specified URL is displayed.</span></span>|
    |<span data-ttu-id="4d7d8-120">Index</span><span class="sxs-lookup"><span data-stu-id="4d7d8-120">Index</span></span>|<span data-ttu-id="4d7d8-121">Určuje, že se zobrazí index zadané adresy URL.</span><span class="sxs-lookup"><span data-stu-id="4d7d8-121">Specifies that the index of a specified URL is displayed.</span></span>|
    |<span data-ttu-id="4d7d8-122">KeywordIndex</span><span class="sxs-lookup"><span data-stu-id="4d7d8-122">KeywordIndex</span></span>|<span data-ttu-id="4d7d8-123">Určuje klíčové slovo k vyhledání a akce má být provedena v zadané adrese URL.</span><span class="sxs-lookup"><span data-stu-id="4d7d8-123">Specifies a keyword to search for and the action to take in the specified URL.</span></span>|
    |<span data-ttu-id="4d7d8-124">TableOfContents</span><span class="sxs-lookup"><span data-stu-id="4d7d8-124">TableOfContents</span></span>|<span data-ttu-id="4d7d8-125">Určuje, že se zobrazí obsah souboru nápovědy HTML 1.0.</span><span class="sxs-lookup"><span data-stu-id="4d7d8-125">Specifies that the table of contents of the HTML 1.0 Help file is displayed.</span></span>|
    |<span data-ttu-id="4d7d8-126">Téma</span><span class="sxs-lookup"><span data-stu-id="4d7d8-126">Topic</span></span>|<span data-ttu-id="4d7d8-127">Určuje, že se zobrazí téma odkazuje na zadanou adresu URL.</span><span class="sxs-lookup"><span data-stu-id="4d7d8-127">Specifies that the topic referenced by the specified URL is displayed.</span></span>|

 <span data-ttu-id="4d7d8-128">V době běhu, stisknutím klávesy F1 při ovládacího prvku – pro které jste nastavili **HelpKeyword** a **HelpNavigator** vlastnosti – má fokus, otevře se soubor nápovědy spojený s ním <xref:System.Windows.Forms.HelpProvider> komponenty.</span><span class="sxs-lookup"><span data-stu-id="4d7d8-128">At run time, pressing F1 when the control—for which you have set the **HelpKeyword** and **HelpNavigator** properties—has focus will open the Help file you associated with that <xref:System.Windows.Forms.HelpProvider> component.</span></span>

 <span data-ttu-id="4d7d8-129">V současné době **HelpNamespace** vlastnost podporuje soubory nápovědy ve třech následujících formátech: HTMLHelp 1.x HTMLHelp 2.0 a ve formátu HTML.</span><span class="sxs-lookup"><span data-stu-id="4d7d8-129">Currently, the **HelpNamespace** property supports Help files in the following three formats: HTMLHelp 1.x, HTMLHelp 2.0, and HTML.</span></span> <span data-ttu-id="4d7d8-130">Proto můžete nastavit **HelpNamespace** nastavte na adresu http://, jako je například na webové stránce.</span><span class="sxs-lookup"><span data-stu-id="4d7d8-130">Thus, you can set the **HelpNamespace** property to an http:// address, such as a Web page.</span></span> <span data-ttu-id="4d7d8-131">Pokud to uděláte, otevře se výchozí prohlížeč na webovou stránku s řetězec zadaný v poli **HelpKeyword** vlastnost použit jako ukotvení.</span><span class="sxs-lookup"><span data-stu-id="4d7d8-131">If this is done, it will open the default browser to the Web page with the string specified in the **HelpKeyword** property used as the anchor.</span></span> <span data-ttu-id="4d7d8-132">Ukotvení se používá pro přechod na určitou část stránku HTML.</span><span class="sxs-lookup"><span data-stu-id="4d7d8-132">The anchor is used to jump to a specific part of an HTML page.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="4d7d8-133">Pečlivě zkontrolujte všechny informace odesílané z klienta před jeho použitím v aplikaci.</span><span class="sxs-lookup"><span data-stu-id="4d7d8-133">Be careful to check any information that is sent from a client before using it in your application.</span></span> <span data-ttu-id="4d7d8-134">Uživatelé se zlými úmysly se může pokusit o odeslání nebo vložit spustitelný soubor skriptu, příkazy SQL nebo jiný kód.</span><span class="sxs-lookup"><span data-stu-id="4d7d8-134">Malicious users might try to send or inject executable script, SQL statements, or other code.</span></span> <span data-ttu-id="4d7d8-135">Před zobrazení vstupu uživatele, ukládat v databázi nebo s ním pracovat, zkontrolujte neobsahuje informace o potenciálně nebezpečné.</span><span class="sxs-lookup"><span data-stu-id="4d7d8-135">Before you display a user's input, store it in a database, or work with it, check that it does not contain potentially unsafe information.</span></span> <span data-ttu-id="4d7d8-136">Typické způsob, jak zkontrolovat je použit regulární výraz k vyhledání klíčová slova, jako je "Skript" při přijímání vstupu od uživatele.</span><span class="sxs-lookup"><span data-stu-id="4d7d8-136">A typical way to check is to use a regular expression to look for keywords such as "SCRIPT" when you receive input from a user.</span></span>

<span data-ttu-id="4d7d8-137">Můžete také použít <xref:System.Windows.Forms.HelpProvider> součásti k zobrazení místní nápovědy, i v případě, že jste si ji nakonfigurovali zobrazíte soubory nápovědy pro ovládací prvky ve formulářích Windows.</span><span class="sxs-lookup"><span data-stu-id="4d7d8-137">You can also use the <xref:System.Windows.Forms.HelpProvider> component to show pop-up Help, even if you have it configured to display Help files for the controls on your Windows Forms.</span></span> <span data-ttu-id="4d7d8-138">Další informace najdete v tématu [jak: Zobrazení místní nápovědy](how-to-display-pop-up-help.md).</span><span class="sxs-lookup"><span data-stu-id="4d7d8-138">For more information, see [How to: Display Pop-up Help](how-to-display-pop-up-help.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="4d7d8-139">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4d7d8-139">See also</span></span>

- [<span data-ttu-id="4d7d8-140">Postupy: Zobrazení místní nápovědy</span><span class="sxs-lookup"><span data-stu-id="4d7d8-140">How to: Display Pop-up Help</span></span>](how-to-display-pop-up-help.md)
- [<span data-ttu-id="4d7d8-141">Nápověda ovládacího prvku pomocí ToolTips</span><span class="sxs-lookup"><span data-stu-id="4d7d8-141">Control Help Using ToolTips</span></span>](control-help-using-tooltips.md)
- [<span data-ttu-id="4d7d8-142">Integrace uživatelské nápovědy v modelu Windows Forms</span><span class="sxs-lookup"><span data-stu-id="4d7d8-142">Integrating User Help in Windows Forms</span></span>](integrating-user-help-in-windows-forms.md)
- [<span data-ttu-id="4d7d8-143">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="4d7d8-143">Windows Forms</span></span>](../index.md)
