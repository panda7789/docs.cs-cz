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
ms.openlocfilehash: 405de333ce936a864047e827e60f56a930059e26
ms.sourcegitcommit: ee5b798427f81237a3c23d1fd81fff7fdc21e8d3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/28/2020
ms.locfileid: "84143602"
---
# <a name="how-to-provide-help-in-a-windows-application"></a><span data-ttu-id="e2373-102">Postupy: Poskytnutí nápovědy v aplikaci Windows</span><span class="sxs-lookup"><span data-stu-id="e2373-102">How to: Provide Help in a Windows Application</span></span>

<span data-ttu-id="e2373-103">Pomocí komponenty můžete v <xref:System.Windows.Forms.HelpProvider> souboru nápovědy připojit témata nápovědy ke konkrétním ovládacím prvkům na model Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="e2373-103">You can make use of the <xref:System.Windows.Forms.HelpProvider> component to attach Help topics within a Help file to specific controls on Windows Forms.</span></span> <span data-ttu-id="e2373-104">Soubor Help může být HTML nebo HTMLHelp 1. x nebo vyšší.</span><span class="sxs-lookup"><span data-stu-id="e2373-104">The Help file can be either HTML or HTMLHelp 1.x or greater format.</span></span>

## <a name="provide-help"></a><span data-ttu-id="e2373-105">Poskytnout pomocníka</span><span class="sxs-lookup"><span data-stu-id="e2373-105">Provide Help</span></span>

1. <span data-ttu-id="e2373-106">V sadě Visual Studio, z **panelu nástrojů**přetáhněte <xref:System.Windows.Forms.HelpProvider> komponentu do formuláře.</span><span class="sxs-lookup"><span data-stu-id="e2373-106">In Visual Studio, from the **Toolbox**, drag a <xref:System.Windows.Forms.HelpProvider> component to your form.</span></span>

     <span data-ttu-id="e2373-107">Komponenta se bude nacházet v zásobníku v dolní části Návrhář formulářů.</span><span class="sxs-lookup"><span data-stu-id="e2373-107">The component will reside in the tray at the bottom of the Windows Forms Designer.</span></span>

2. <span data-ttu-id="e2373-108">V okně **vlastnosti** nastavte <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> vlastnost na soubor Help. chm,. slo nebo. htm.</span><span class="sxs-lookup"><span data-stu-id="e2373-108">In the **Properties** window, set the <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> property to the .chm, .col, or .htm Help file.</span></span>

3. <span data-ttu-id="e2373-109">Vyberte jiný ovládací prvek, který máte ve formuláři, a v okně **vlastnosti** nastavte <xref:System.Windows.Forms.HelpProvider.SetHelpKeyword%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="e2373-109">Select another control you have on your form, and in the **Properties** window, set the <xref:System.Windows.Forms.HelpProvider.SetHelpKeyword%2A> property.</span></span>

     <span data-ttu-id="e2373-110">Toto je řetězec předaný <xref:System.Windows.Forms.HelpProvider> komponentě souboru nápovědy k předvolání příslušného tématu nápovědy.</span><span class="sxs-lookup"><span data-stu-id="e2373-110">This is the string passed through the <xref:System.Windows.Forms.HelpProvider> component to your Help file to summon the appropriate Help topic.</span></span>

4. <span data-ttu-id="e2373-111">V okně **vlastnosti** nastavte <xref:System.Windows.Forms.HelpProvider.SetHelpNavigator%2A> vlastnost na hodnotu <xref:System.Windows.Forms.HelpNavigator> výčtu.</span><span class="sxs-lookup"><span data-stu-id="e2373-111">In the **Properties** window, set the <xref:System.Windows.Forms.HelpProvider.SetHelpNavigator%2A> property to a value of the <xref:System.Windows.Forms.HelpNavigator> enumeration.</span></span>

     <span data-ttu-id="e2373-112">To určuje způsob, jakým je vlastnost **HelpKeyword** předána systému help.</span><span class="sxs-lookup"><span data-stu-id="e2373-112">This determines the way in which the **HelpKeyword** property is passed to the Help system.</span></span> <span data-ttu-id="e2373-113">V následující tabulce jsou uvedena možná nastavení a jejich popisy.</span><span class="sxs-lookup"><span data-stu-id="e2373-113">The following table shows the possible settings and their descriptions.</span></span>

    |<span data-ttu-id="e2373-114">Název členu</span><span class="sxs-lookup"><span data-stu-id="e2373-114">Member Name</span></span>|<span data-ttu-id="e2373-115">Popis</span><span class="sxs-lookup"><span data-stu-id="e2373-115">Description</span></span>|
    |-----------------|-----------------|
    |<span data-ttu-id="e2373-116">AssociateIndex</span><span class="sxs-lookup"><span data-stu-id="e2373-116">AssociateIndex</span></span>|<span data-ttu-id="e2373-117">Určuje, že se index zadaného tématu provede v zadané adrese URL.</span><span class="sxs-lookup"><span data-stu-id="e2373-117">Specifies that the index for a specified topic is performed in the specified URL.</span></span>|
    |<span data-ttu-id="e2373-118">Vyhledávání</span><span class="sxs-lookup"><span data-stu-id="e2373-118">Find</span></span>|<span data-ttu-id="e2373-119">Určuje, že se zobrazí stránka vyhledávání v zadané adrese URL.</span><span class="sxs-lookup"><span data-stu-id="e2373-119">Specifies that the search page of a specified URL is displayed.</span></span>|
    |<span data-ttu-id="e2373-120">Index</span><span class="sxs-lookup"><span data-stu-id="e2373-120">Index</span></span>|<span data-ttu-id="e2373-121">Určuje, že se zobrazí index zadané adresy URL.</span><span class="sxs-lookup"><span data-stu-id="e2373-121">Specifies that the index of a specified URL is displayed.</span></span>|
    |<span data-ttu-id="e2373-122">KeywordIndex</span><span class="sxs-lookup"><span data-stu-id="e2373-122">KeywordIndex</span></span>|<span data-ttu-id="e2373-123">Určuje klíčové slovo, které chcete vyhledat, a akci, která se má provést v zadané adrese URL.</span><span class="sxs-lookup"><span data-stu-id="e2373-123">Specifies a keyword to search for and the action to take in the specified URL.</span></span>|
    |<span data-ttu-id="e2373-124">TableOfContents</span><span class="sxs-lookup"><span data-stu-id="e2373-124">TableOfContents</span></span>|<span data-ttu-id="e2373-125">Určuje, že se zobrazí tabulka obsahu souboru nápovědy HTML 1,0.</span><span class="sxs-lookup"><span data-stu-id="e2373-125">Specifies that the table of contents of the HTML 1.0 Help file is displayed.</span></span>|
    |<span data-ttu-id="e2373-126">Téma</span><span class="sxs-lookup"><span data-stu-id="e2373-126">Topic</span></span>|<span data-ttu-id="e2373-127">Určuje, že se zobrazí téma odkazované zadanou adresou URL.</span><span class="sxs-lookup"><span data-stu-id="e2373-127">Specifies that the topic referenced by the specified URL is displayed.</span></span>|

 <span data-ttu-id="e2373-128">V době běhu stiskněte klávesu F1, když ovládací prvek, pro který jste nastavili vlastnosti **HelpKeyword** a **HelpNavigator** – má fokus, otevře se soubor s nápovědu, který se k této <xref:System.Windows.Forms.HelpProvider> komponentě přidruží.</span><span class="sxs-lookup"><span data-stu-id="e2373-128">At run time, pressing F1 when the control—for which you have set the **HelpKeyword** and **HelpNavigator** properties—has focus will open the Help file you associated with that <xref:System.Windows.Forms.HelpProvider> component.</span></span>

 <span data-ttu-id="e2373-129">V současné době vlastnost **HelpNamespace** podporuje soubory Help v následujících třech formátech: HTMLHelp 1. x, HTMLHelp 2,0 a HTML.</span><span class="sxs-lookup"><span data-stu-id="e2373-129">Currently, the **HelpNamespace** property supports Help files in the following three formats: HTMLHelp 1.x, HTMLHelp 2.0, and HTML.</span></span> <span data-ttu-id="e2373-130">Proto můžete vlastnost **HelpNamespace** nastavit na `http://` adresu, jako je například webová stránka.</span><span class="sxs-lookup"><span data-stu-id="e2373-130">Thus, you can set the **HelpNamespace** property to an `http://` address, such as a Web page.</span></span> <span data-ttu-id="e2373-131">Pokud k tomu dojde, otevře se výchozí prohlížeč na webové stránce s řetězcem zadaným ve vlastnosti **HelpKeyword** použité jako kotvy.</span><span class="sxs-lookup"><span data-stu-id="e2373-131">If this is done, it will open the default browser to the Web page with the string specified in the **HelpKeyword** property used as the anchor.</span></span> <span data-ttu-id="e2373-132">Kotva se používá k přechodu na určitou část stránky HTML.</span><span class="sxs-lookup"><span data-stu-id="e2373-132">The anchor is used to jump to a specific part of an HTML page.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e2373-133">Nezapomeňte si ověřit, jestli jsou informace odesílané z klienta před jeho použitím ve vaší aplikaci opatrní.</span><span class="sxs-lookup"><span data-stu-id="e2373-133">Be careful to check any information that is sent from a client before using it in your application.</span></span> <span data-ttu-id="e2373-134">Uživatelé se zlými úmysly se můžou pokusit odeslat nebo vložit spustitelný skript, příkazy SQL nebo jiný kód.</span><span class="sxs-lookup"><span data-stu-id="e2373-134">Malicious users might try to send or inject executable script, SQL statements, or other code.</span></span> <span data-ttu-id="e2373-135">Než zobrazíte vstup uživatele, uložte ho do databáze nebo s ním můžete pracovat, ověřte, že neobsahuje potenciálně nebezpečné informace.</span><span class="sxs-lookup"><span data-stu-id="e2373-135">Before you display a user's input, store it in a database, or work with it, check that it does not contain potentially unsafe information.</span></span> <span data-ttu-id="e2373-136">Obvyklým způsobem, jak zkontrolovat, je použít regulární výraz pro hledání klíčových slov, jako je například "SCRIPT", když obdržíte vstup od uživatele.</span><span class="sxs-lookup"><span data-stu-id="e2373-136">A typical way to check is to use a regular expression to look for keywords such as "SCRIPT" when you receive input from a user.</span></span>

<span data-ttu-id="e2373-137">Můžete také použít <xref:System.Windows.Forms.HelpProvider> komponentu k zobrazení místní nápovědy, i když je máte nakonfigurovanou tak, aby zobrazovala soubory nápovědy pro ovládací prvky na model Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="e2373-137">You can also use the <xref:System.Windows.Forms.HelpProvider> component to show pop-up Help, even if you have it configured to display Help files for the controls on your Windows Forms.</span></span> <span data-ttu-id="e2373-138">Další informace najdete v tématu [Postup: zobrazení místní nápovědy](how-to-display-pop-up-help.md).</span><span class="sxs-lookup"><span data-stu-id="e2373-138">For more information, see [How to: Display Pop-up Help](how-to-display-pop-up-help.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e2373-139">Viz také</span><span class="sxs-lookup"><span data-stu-id="e2373-139">See also</span></span>

- [<span data-ttu-id="e2373-140">Postupy: Zobrazení místní nápovědy</span><span class="sxs-lookup"><span data-stu-id="e2373-140">How to: Display Pop-up Help</span></span>](how-to-display-pop-up-help.md)
- [<span data-ttu-id="e2373-141">Nápověda ovládacího prvku pomocí ToolTips</span><span class="sxs-lookup"><span data-stu-id="e2373-141">Control Help Using ToolTips</span></span>](control-help-using-tooltips.md)
- [<span data-ttu-id="e2373-142">Integrace uživatelské nápovědy v modelu Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e2373-142">Integrating User Help in Windows Forms</span></span>](integrating-user-help-in-windows-forms.md)
- [<span data-ttu-id="e2373-143">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e2373-143">Windows Forms</span></span>](../index.md)
