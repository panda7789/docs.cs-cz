---
title: "Chyby v rámci doby návrhu v Návrháři formulářů Windows"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- DTELErrorList
- WhyDTELPage
helpviewer_keywords:
- errors [Windows Forms Designer]
- design-time errors [Windows Forms Designer]
ms.assetid: ad408380-825a-46d8-9a4a-531b130b88ce
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 819b624e2abac09aea804311d661f78e2a1f5a7c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="design-time-errors-in-the-windows-forms-designer"></a><span data-ttu-id="7602d-102">Chyby v rámci doby návrhu v Návrháři formulářů Windows</span><span class="sxs-lookup"><span data-stu-id="7602d-102">Design-Time Errors in the Windows Forms Designer</span></span>
<span data-ttu-id="7602d-103">Toto téma vysvětluje význam a používání seznamu chyb návrhu, které se zobrazí v sadě Microsoft Visual Studio po Návrhář formulářů Windows nepodaří načíst.</span><span class="sxs-lookup"><span data-stu-id="7602d-103">This topic explains the meaning and use of the design-time error list that appears in Microsoft Visual Studio when the Windows Forms Designer fails to load.</span></span> <span data-ttu-id="7602d-104">Pokud se zobrazí tento seznam chyb, by neměl interpretovat jako chyby v návrháři, ale jako pomůcku při opravách chyb v kódu.</span><span class="sxs-lookup"><span data-stu-id="7602d-104">If this error list appears, you should not interpret it as a bug in the designer, but as an aid to correcting errors in your code.</span></span>  
  
 <span data-ttu-id="7602d-105">Základní znalosti o tento seznam chyb můžete ladit aplikace tak, že poskytuje podrobné informace o chybách a návrhy možná řešení.</span><span class="sxs-lookup"><span data-stu-id="7602d-105">A basic understanding of this error list will help you debug your applications by providing detailed information about the errors and suggesting possible solutions.</span></span>  
  
## <a name="the-design-time-error-list-interface"></a><span data-ttu-id="7602d-106">Rozhraní seznamu Chyba v době návrhu</span><span class="sxs-lookup"><span data-stu-id="7602d-106">The Design-Time Error List Interface</span></span>  
 <span data-ttu-id="7602d-107">Pokud návrhář formulářů Windows se nepodaří načíst, Chyba při seznamu se zobrazí v návrháři.</span><span class="sxs-lookup"><span data-stu-id="7602d-107">If the Windows Forms Designer fails to load, an error list will appear in the designer.</span></span> <span data-ttu-id="7602d-108">Chyby jsou seskupené do kategorií.</span><span class="sxs-lookup"><span data-stu-id="7602d-108">The errors are grouped into categories.</span></span> <span data-ttu-id="7602d-109">Například pokud máte čtyři instancí nedeklarované proměnných, tyto budou seskupeny do stejné kategorie chyby.</span><span class="sxs-lookup"><span data-stu-id="7602d-109">For example, if you have four instances of undeclared variables, these will be grouped into the same error category.</span></span> <span data-ttu-id="7602d-110">Každá kategorie chyby zahrnuje stručný popis, který shrnuje chyba.</span><span class="sxs-lookup"><span data-stu-id="7602d-110">Each error category includes a brief description that summarizes the error.</span></span>  
  
 <span data-ttu-id="7602d-111">Můžete rozbalit nebo sbalit chyba kategorie, buď kliknutím na záhlaví kategorie chyby nebo kliknutím na dvojitou šipku Rozbalit/sbalit.</span><span class="sxs-lookup"><span data-stu-id="7602d-111">You can expand or collapse an error category by either clicking on the error category heading or by clicking the expand/collapse chevron.</span></span> <span data-ttu-id="7602d-112">Pokud rozbalíte kategorii chyby, zobrazí se následující další nápovědu:</span><span class="sxs-lookup"><span data-stu-id="7602d-112">When you expand an error category, the following additional help is displayed:</span></span>  
  
-   <span data-ttu-id="7602d-113">Instance této chyby.</span><span class="sxs-lookup"><span data-stu-id="7602d-113">Instances of this error.</span></span>  
  
-   <span data-ttu-id="7602d-114">Nápověda k této chybě.</span><span class="sxs-lookup"><span data-stu-id="7602d-114">Help with this error.</span></span>  
  
-   <span data-ttu-id="7602d-115">Fórum odešle o této chybě.</span><span class="sxs-lookup"><span data-stu-id="7602d-115">Forum posts about this error.</span></span>  
  
### <a name="instances-of-this-error"></a><span data-ttu-id="7602d-116">Instance této chyby</span><span class="sxs-lookup"><span data-stu-id="7602d-116">Instances of This Error</span></span>  
 <span data-ttu-id="7602d-117">Další nápověda seznam všech instancí chybu v aktuálním projektu.</span><span class="sxs-lookup"><span data-stu-id="7602d-117">The additional help list all instances of the error in your current project.</span></span> <span data-ttu-id="7602d-118">Mnoho chyb zahrnují přesné umístění v následujícím formátu: *[název projektu]* *[název formuláře]* řádku:*[číslo řádku]* sloupce:*[číslo sloupce]*.</span><span class="sxs-lookup"><span data-stu-id="7602d-118">Many errors include an exact location in the following format: *[Project Name]* *[Form Name]* Line:*[Line Number]* Column:*[Column Number]*.</span></span> <span data-ttu-id="7602d-119">**Přejít ke kódu** odkazu přejdete do umístění ve vašem kódu, kde dojde k chybě.</span><span class="sxs-lookup"><span data-stu-id="7602d-119">The **Go to code** link takes you to the location in your code where the error occurs.</span></span>  
  
 <span data-ttu-id="7602d-120">Pokud zásobníku volání je přidružen k chybě, můžete kliknout **zobrazit zásobníkem volání** odkaz, který rozbalí další chyby zobrazíte zásobníku volání.</span><span class="sxs-lookup"><span data-stu-id="7602d-120">If a call stack is associated with the error, you can click the **Show Call Stack** link, which further expands the error to show the call stack.</span></span> <span data-ttu-id="7602d-121">Zkoumání zásobníku může poskytnout cenné informace o ladění.</span><span class="sxs-lookup"><span data-stu-id="7602d-121">Examining the stack can provide valuable debugging information.</span></span> <span data-ttu-id="7602d-122">Například můžete sledovat funkce, které bylo voláno před se stala chyba.</span><span class="sxs-lookup"><span data-stu-id="7602d-122">For example, you can track the functions that were called before the error occurred.</span></span> <span data-ttu-id="7602d-123">V zásobníku volání je volitelný, takže můžete zkopírovat a uložit ho.</span><span class="sxs-lookup"><span data-stu-id="7602d-123">The call stack is selectable so that you can copy and save it.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7602d-124">V jazyce Visual Basic v seznamu chyb návrhu nezobrazí více než jednu chybu, ale může zobrazovat více instancí ke stejné chybě.</span><span class="sxs-lookup"><span data-stu-id="7602d-124">In Visual Basic, the design-time error list does not display more than one error, but it may display multiple instances of the same error.</span></span> <span data-ttu-id="7602d-125">Chyby v jazyce Visual C++, nemají goto kód odkazy nebo čáry číslo odkazy.</span><span class="sxs-lookup"><span data-stu-id="7602d-125">In Visual C++, the errors do not have goto code links/line number links.</span></span>  
  
### <a name="help-with-this-error"></a><span data-ttu-id="7602d-126">Nápověda k této chybě</span><span class="sxs-lookup"><span data-stu-id="7602d-126">Help with This Error</span></span>  
 <span data-ttu-id="7602d-127">Pokud chyba obsahuje odkaz související téma nápovědy MSDN, potřebujete další pomoc obsahují odkaz na téma nápovědy.</span><span class="sxs-lookup"><span data-stu-id="7602d-127">If the error contains a link to an associated MSDN help topic, the additional help will include a link to the help topic.</span></span> <span data-ttu-id="7602d-128">Když kliknete na odkaz, zobrazí se v sadě Visual Studio přidružené téma nápovědy.</span><span class="sxs-lookup"><span data-stu-id="7602d-128">When you click the link, the associated help topic appears in Visual Studio.</span></span>  
  
### <a name="forum-posts-about-this-error"></a><span data-ttu-id="7602d-129">Fórum příspěvky o této chybě</span><span class="sxs-lookup"><span data-stu-id="7602d-129">Forum posts about this error</span></span>  
 <span data-ttu-id="7602d-130">Potřebujete další pomoc, bude obsahovat odkaz na MSDN příspěvcích týkající se chyby.</span><span class="sxs-lookup"><span data-stu-id="7602d-130">The additional help will include a link to MSDN forum posts related to the error.</span></span> <span data-ttu-id="7602d-131">Ve fórech vyhledávají podle řetězec chybové zprávy.</span><span class="sxs-lookup"><span data-stu-id="7602d-131">The forums are searched based on the string of the error message.</span></span> <span data-ttu-id="7602d-132">Můžete také zkusit vyhledávání fórech o následující:</span><span class="sxs-lookup"><span data-stu-id="7602d-132">You can also try searching the following forums:</span></span>  
  
-   [<span data-ttu-id="7602d-133">Návrhář fórum pro Windows Forms</span><span class="sxs-lookup"><span data-stu-id="7602d-133">Windows Forms Designer Forum</span></span>](http://go.microsoft.com/fwlink/?LinkId=203524)  
  
-   [<span data-ttu-id="7602d-134">Windows Forms fóra</span><span class="sxs-lookup"><span data-stu-id="7602d-134">Windows Forms Forums</span></span>](http://go.microsoft.com/fwlink/?LinkId=203523)  
  
### <a name="ignore-and-continue"></a><span data-ttu-id="7602d-135">Ignorovat a pokračovat</span><span class="sxs-lookup"><span data-stu-id="7602d-135">Ignore and Continue</span></span>  
 <span data-ttu-id="7602d-136">Můžete chybu ignorovat a pokračovat v načítání návrháře.</span><span class="sxs-lookup"><span data-stu-id="7602d-136">You can choose to ignore the error condition and continue loading the designer.</span></span> <span data-ttu-id="7602d-137">Výběr tato akce může vést k neočekávanému chování.</span><span class="sxs-lookup"><span data-stu-id="7602d-137">Choosing this action may result in unexpected behavior.</span></span> <span data-ttu-id="7602d-138">Například ovládací prvky nacházet na návrhovou plochu.</span><span class="sxs-lookup"><span data-stu-id="7602d-138">For example, controls may not appear on the design surface.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7602d-139">Viz také</span><span class="sxs-lookup"><span data-stu-id="7602d-139">See Also</span></span>  
 [<span data-ttu-id="7602d-140">Řešení potíží s vývoj návrhu</span><span class="sxs-lookup"><span data-stu-id="7602d-140">Troubleshooting Design-Time Development</span></span>](http://msdn.microsoft.com/library/e048d08e-fa7c-4be8-b238-4abaa199a0a6)  
 [<span data-ttu-id="7602d-141">Řešení potíží s komponenty vytváření a řízení</span><span class="sxs-lookup"><span data-stu-id="7602d-141">Troubleshooting Control and Component Authoring</span></span>](../../../../docs/framework/winforms/controls/troubleshooting-control-and-component-authoring.md)  
 [<span data-ttu-id="7602d-142">Vývoj Windows Forms – ovládací prvky v době návrhu</span><span class="sxs-lookup"><span data-stu-id="7602d-142">Developing Windows Forms Controls at Design Time</span></span>](../../../../docs/framework/winforms/controls/developing-windows-forms-controls-at-design-time.md)  
 [<span data-ttu-id="7602d-143">Windows Forms návrháře chybové zprávy</span><span class="sxs-lookup"><span data-stu-id="7602d-143">Windows Forms Designer Error Messages</span></span>](http://msdn.microsoft.com/en-us/cf610bf4-5fe4-471c-bce7-6a05ece07bd2)
