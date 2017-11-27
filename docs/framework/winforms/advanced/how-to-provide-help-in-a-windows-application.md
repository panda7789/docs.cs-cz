---
title: "Postupy: Poskytnutí nápovědy v aplikaci Windows"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Help [Windows Forms], Windows applications
- HTML Help [Windows Forms], Windows Forms
- Windows applications [Windows Forms], providing Help
- HelpProvider component [Windows Forms]
- forms [Windows Forms], providing Help
ms.assetid: 7c4e5cec-2bd2-4f0b-8d75-c2b88929bd61
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0f407f1c17c67ec99f4499b89c49932a4ba6d32c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-provide-help-in-a-windows-application"></a><span data-ttu-id="cdd35-102">Postupy: Poskytnutí nápovědy v aplikaci Windows</span><span class="sxs-lookup"><span data-stu-id="cdd35-102">How to: Provide Help in a Windows Application</span></span>
<span data-ttu-id="cdd35-103">Můžete použít nástroje <xref:System.Windows.Forms.HelpProvider> součásti pro připojení ke konkrétní ovládacích prvků ve Windows Forms témata nápovědy v souboru nápovědy.</span><span class="sxs-lookup"><span data-stu-id="cdd35-103">You can use of the <xref:System.Windows.Forms.HelpProvider> component to attach Help topics within a Help file to specific controls on Windows Forms.</span></span> <span data-ttu-id="cdd35-104">Soubor nápovědy může být HTML nebo HTMLHelp 1.x nebo větší formát.</span><span class="sxs-lookup"><span data-stu-id="cdd35-104">The Help file can be either HTML or HTMLHelp 1.x or greater format.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cdd35-105">Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici.</span><span class="sxs-lookup"><span data-stu-id="cdd35-105">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="cdd35-106">Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky.</span><span class="sxs-lookup"><span data-stu-id="cdd35-106">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="cdd35-107">Další informace najdete v tématu [přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="cdd35-107">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-provide-help"></a><span data-ttu-id="cdd35-108">K poskytnutí nápovědy</span><span class="sxs-lookup"><span data-stu-id="cdd35-108">To provide Help</span></span>  
  
1.  <span data-ttu-id="cdd35-109">Z **sada nástrojů**, přetáhněte ji <xref:System.Windows.Forms.HelpProvider> součásti do svého formuláře.</span><span class="sxs-lookup"><span data-stu-id="cdd35-109">From the **Toolbox**, drag a <xref:System.Windows.Forms.HelpProvider> component to your form.</span></span>  
  
     <span data-ttu-id="cdd35-110">Součást se bude nacházet na hlavním panelu v dolní části Návrhář formulářů Windows.</span><span class="sxs-lookup"><span data-stu-id="cdd35-110">The component will reside in the tray at the bottom of the Windows Forms Designer.</span></span>  
  
2.  <span data-ttu-id="cdd35-111">V **vlastnosti** nastavte <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> vlastnost chm., .col nebo .htm souboru nápovědy.</span><span class="sxs-lookup"><span data-stu-id="cdd35-111">In the **Properties** window, set the <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> property to the .chm, .col, or .htm Help file.</span></span>  
  
3.  <span data-ttu-id="cdd35-112">Vyberte jiný ovládací prvek máte ve formuláři a v **vlastnosti** nastavte <xref:System.Windows.Forms.HelpProvider.SetHelpKeyword%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="cdd35-112">Select another control you have on your form, and in the **Properties** window, set the <xref:System.Windows.Forms.HelpProvider.SetHelpKeyword%2A> property.</span></span>  
  
     <span data-ttu-id="cdd35-113">Toto je řetězec předána <xref:System.Windows.Forms.HelpProvider> součásti k souboru nápovědy k výzvě příslušné téma nápovědy.</span><span class="sxs-lookup"><span data-stu-id="cdd35-113">This is the string passed through the <xref:System.Windows.Forms.HelpProvider> component to your Help file to summon the appropriate Help topic.</span></span>  
  
4.  <span data-ttu-id="cdd35-114">V **vlastnosti** nastavte <xref:System.Windows.Forms.HelpProvider.SetHelpNavigator%2A> vlastnost na hodnotu <xref:System.Windows.Forms.HelpNavigator> výčtu.</span><span class="sxs-lookup"><span data-stu-id="cdd35-114">In the **Properties** window, set the <xref:System.Windows.Forms.HelpProvider.SetHelpNavigator%2A> property to a value of the <xref:System.Windows.Forms.HelpNavigator> enumeration.</span></span>  
  
     <span data-ttu-id="cdd35-115">Určuje, jakým způsobem **HelpKeyword** předána vlastnost systému nápovědy.</span><span class="sxs-lookup"><span data-stu-id="cdd35-115">This determines the way in which the **HelpKeyword** property is passed to the Help system.</span></span> <span data-ttu-id="cdd35-116">V následující tabulce jsou uvedeny možné nastavení a jejich popisy.</span><span class="sxs-lookup"><span data-stu-id="cdd35-116">The following table shows the possible settings and their descriptions.</span></span>  
  
    |<span data-ttu-id="cdd35-117">Název členu</span><span class="sxs-lookup"><span data-stu-id="cdd35-117">Member Name</span></span>|<span data-ttu-id="cdd35-118">Popis</span><span class="sxs-lookup"><span data-stu-id="cdd35-118">Description</span></span>|  
    |-----------------|-----------------|  
    |<span data-ttu-id="cdd35-119">AssociateIndex</span><span class="sxs-lookup"><span data-stu-id="cdd35-119">AssociateIndex</span></span>|<span data-ttu-id="cdd35-120">Určuje, že index pro zadaný téma se provádí v zadané adrese URL.</span><span class="sxs-lookup"><span data-stu-id="cdd35-120">Specifies that the index for a specified topic is performed in the specified URL.</span></span>|  
    |<span data-ttu-id="cdd35-121">Najít</span><span class="sxs-lookup"><span data-stu-id="cdd35-121">Find</span></span>|<span data-ttu-id="cdd35-122">Určuje, že se zobrazí stránka hledat zadaná adresa URL.</span><span class="sxs-lookup"><span data-stu-id="cdd35-122">Specifies that the search page of a specified URL is displayed.</span></span>|  
    |<span data-ttu-id="cdd35-123">Index</span><span class="sxs-lookup"><span data-stu-id="cdd35-123">Index</span></span>|<span data-ttu-id="cdd35-124">Určuje, že se zobrazí index zadaná adresa URL.</span><span class="sxs-lookup"><span data-stu-id="cdd35-124">Specifies that the index of a specified URL is displayed.</span></span>|  
    |<span data-ttu-id="cdd35-125">KeywordIndex</span><span class="sxs-lookup"><span data-stu-id="cdd35-125">KeywordIndex</span></span>|<span data-ttu-id="cdd35-126">Určuje klíčového slova pro vyhledávání a pro případ v zadané adrese URL.</span><span class="sxs-lookup"><span data-stu-id="cdd35-126">Specifies a keyword to search for and the action to take in the specified URL.</span></span>|  
    |<span data-ttu-id="cdd35-127">TableOfContents</span><span class="sxs-lookup"><span data-stu-id="cdd35-127">TableOfContents</span></span>|<span data-ttu-id="cdd35-128">Určuje, že se zobrazí obsah souboru nápovědy HTML 1.0.</span><span class="sxs-lookup"><span data-stu-id="cdd35-128">Specifies that the table of contents of the HTML 1.0 Help file is displayed.</span></span>|  
    |<span data-ttu-id="cdd35-129">Téma</span><span class="sxs-lookup"><span data-stu-id="cdd35-129">Topic</span></span>|<span data-ttu-id="cdd35-130">Určuje, že se zobrazí v tématu odkazuje na zadanou adresu URL.</span><span class="sxs-lookup"><span data-stu-id="cdd35-130">Specifies that the topic referenced by the specified URL is displayed.</span></span>|  
  
 <span data-ttu-id="cdd35-131">V době běhu, stisknutím klávesy F1 při ovládacího prvku – pro které jste nastavili **HelpKeyword** a **HelpNavigator** vlastnosti – má fokus se otevře soubor nápovědy přidružené který <xref:System.Windows.Forms.HelpProvider> součásti.</span><span class="sxs-lookup"><span data-stu-id="cdd35-131">At run time, pressing F1 when the control—for which you have set the **HelpKeyword** and **HelpNavigator** properties—has focus will open the Help file you associated with that <xref:System.Windows.Forms.HelpProvider> component.</span></span>  
  
 <span data-ttu-id="cdd35-132">V současné době **HelpNamespace** vlastnost podporuje v následujících formátech tři soubory nápovědy: HTMLHelp 1.x HTMLHelp 2.0 a HTML.</span><span class="sxs-lookup"><span data-stu-id="cdd35-132">Currently, the **HelpNamespace** property supports Help files in the following three formats: HTMLHelp 1.x, HTMLHelp 2.0, and HTML.</span></span> <span data-ttu-id="cdd35-133">Proto můžete nastavit **HelpNamespace** vlastnost na adresu http://, jako je například na webové stránce.</span><span class="sxs-lookup"><span data-stu-id="cdd35-133">Thus, you can set the **HelpNamespace** property to an http:// address, such as a Web page.</span></span> <span data-ttu-id="cdd35-134">Když toto dokončíte, otevře výchozí prohlížeč na webovou stránku s řetězec zadaný v poli **HelpKeyword** vlastnost použitá jako ukotvení.</span><span class="sxs-lookup"><span data-stu-id="cdd35-134">If this is done, it will open the default browser to the Web page with the string specified in the **HelpKeyword** property used as the anchor.</span></span> <span data-ttu-id="cdd35-135">Ukotvení se používá k přejít na určitou část stránku HTML.</span><span class="sxs-lookup"><span data-stu-id="cdd35-135">The anchor is used to jump to a specific part of an HTML page.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="cdd35-136">Pečlivě zkontrolujte všechny informace, které se odesílá z klienta před jeho použitím ve vaší aplikaci.</span><span class="sxs-lookup"><span data-stu-id="cdd35-136">Be careful to check any information that is sent from a client before using it in your application.</span></span> <span data-ttu-id="cdd35-137">Uživatelé se zlými úmysly se může pokusit odeslat nebo vložit spustitelný soubor skriptu, příkazy SQL nebo jiný kód.</span><span class="sxs-lookup"><span data-stu-id="cdd35-137">Malicious users might try to send or inject executable script, SQL statements, or other code.</span></span> <span data-ttu-id="cdd35-138">Před zobrazení vstupu uživatele, uložte ho do databáze nebo s ním pracovat, zkontrolujte, zda neobsahuje potenciálně nebezpečného informace.</span><span class="sxs-lookup"><span data-stu-id="cdd35-138">Before you display a user's input, store it in a database, or work with it, check that it does not contain potentially unsafe information.</span></span> <span data-ttu-id="cdd35-139">Typické způsobem kontroly je použijte regulární výraz k vyhledání klíčová slova, jako je například "Skript", když obdrží vstup od uživatele.</span><span class="sxs-lookup"><span data-stu-id="cdd35-139">A typical way to check is to use a regular expression to look for keywords such as "SCRIPT" when you receive input from a user.</span></span>  
  
 <span data-ttu-id="cdd35-140">Můžete také <xref:System.Windows.Forms.HelpProvider> součást zobrazit automaticky otevírané okno nápovědu, i když máte konfigurace. Chcete-li zobrazit soubory nápovědy pro ovládací prvky Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="cdd35-140">You can also use the <xref:System.Windows.Forms.HelpProvider> component to show pop-up Help, even if you have it configured to display Help files for the controls on your Windows Forms.</span></span> <span data-ttu-id="cdd35-141">Další informace najdete v tématu [postupy: zobrazení místní nápovědy](../../../../docs/framework/winforms/advanced/how-to-display-pop-up-help.md).</span><span class="sxs-lookup"><span data-stu-id="cdd35-141">For more information, see [How to: Display Pop-up Help](../../../../docs/framework/winforms/advanced/how-to-display-pop-up-help.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cdd35-142">Viz také</span><span class="sxs-lookup"><span data-stu-id="cdd35-142">See Also</span></span>  
 [<span data-ttu-id="cdd35-143">Postupy: zobrazení místní nápovědy</span><span class="sxs-lookup"><span data-stu-id="cdd35-143">How to: Display Pop-up Help</span></span>](../../../../docs/framework/winforms/advanced/how-to-display-pop-up-help.md)  
 [<span data-ttu-id="cdd35-144">Nápověda ovládacího prvku pomocí ToolTips</span><span class="sxs-lookup"><span data-stu-id="cdd35-144">Control Help Using ToolTips</span></span>](../../../../docs/framework/winforms/advanced/control-help-using-tooltips.md)  
 [<span data-ttu-id="cdd35-145">Integrace uživatelské nápovědy do formulářů Windows</span><span class="sxs-lookup"><span data-stu-id="cdd35-145">Integrating User Help in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/integrating-user-help-in-windows-forms.md)  
 [<span data-ttu-id="cdd35-146">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="cdd35-146">Windows Forms</span></span>](../../../../docs/framework/winforms/index.md)
