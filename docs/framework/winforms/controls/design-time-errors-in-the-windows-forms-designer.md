---
title: Chyby v rámci doby návrhu v Návrháři formulářů Windows
ms.date: 03/30/2017
f1_keywords:
- DTELErrorList
- WhyDTELPage
helpviewer_keywords:
- errors [Windows Forms Designer]
- design-time errors [Windows Forms Designer]
ms.assetid: ad408380-825a-46d8-9a4a-531b130b88ce
ms.openlocfilehash: ec1801a1b695867a7edcd99394feebe1d0f6853a
ms.sourcegitcommit: 2350a091ef6459f0fcfd894301242400374d8558
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/21/2018
ms.locfileid: "46531744"
---
# <a name="design-time-errors-in-the-windows-forms-designer"></a><span data-ttu-id="c5f12-102">Chyby v rámci doby návrhu v Návrháři formulářů Windows</span><span class="sxs-lookup"><span data-stu-id="c5f12-102">Design-Time Errors in the Windows Forms Designer</span></span>
<span data-ttu-id="c5f12-103">Toto téma vysvětluje význam a použití seznamu chyb při návrhu, který se zobrazí v sadě Microsoft Visual Studio, když Návrhář formulářů Windows nepodaří načíst.</span><span class="sxs-lookup"><span data-stu-id="c5f12-103">This topic explains the meaning and use of the design-time error list that appears in Microsoft Visual Studio when the Windows Forms Designer fails to load.</span></span> <span data-ttu-id="c5f12-104">Pokud se zobrazí tento seznam chyb, by neměla interpretovat jako chyba v návrháři, ale jako pomůcka pro opravu chyb v kódu.</span><span class="sxs-lookup"><span data-stu-id="c5f12-104">If this error list appears, you should not interpret it as a bug in the designer, but as an aid to correcting errors in your code.</span></span>  
  
 <span data-ttu-id="c5f12-105">Základní znalosti o tento seznam chyb můžete ladit aplikace tak, že poskytuje podrobné informace o chybách a navrhněte řešení.</span><span class="sxs-lookup"><span data-stu-id="c5f12-105">A basic understanding of this error list will help you debug your applications by providing detailed information about the errors and suggesting possible solutions.</span></span>  
  
## <a name="the-design-time-error-list-interface"></a><span data-ttu-id="c5f12-106">Rozhraní seznam chyb při návrhu</span><span class="sxs-lookup"><span data-stu-id="c5f12-106">The Design-Time Error List Interface</span></span>  
 <span data-ttu-id="c5f12-107">Pokud se nepodaří načíst Návrháře formulářů Windows, seznamu chyb se zobrazí v návrháři.</span><span class="sxs-lookup"><span data-stu-id="c5f12-107">If the Windows Forms Designer fails to load, an error list will appear in the designer.</span></span> <span data-ttu-id="c5f12-108">Chyby jsou seskupené do kategorií.</span><span class="sxs-lookup"><span data-stu-id="c5f12-108">The errors are grouped into categories.</span></span> <span data-ttu-id="c5f12-109">Například pokud máte čtyři instance nedeklarované proměnné, ty budou seskupeny do stejné kategorie chyby.</span><span class="sxs-lookup"><span data-stu-id="c5f12-109">For example, if you have four instances of undeclared variables, these will be grouped into the same error category.</span></span> <span data-ttu-id="c5f12-110">Každá kategorie chyby obsahuje stručný popis, který shrnuje chybu.</span><span class="sxs-lookup"><span data-stu-id="c5f12-110">Each error category includes a brief description that summarizes the error.</span></span>  
  
 <span data-ttu-id="c5f12-111">Můžete rozbalit nebo Sbalit kategorii chyby, kliknutím na záhlaví kategorie chyby nebo kliknutím na dvojitou šipku Rozbalit/sbalit.</span><span class="sxs-lookup"><span data-stu-id="c5f12-111">You can expand or collapse an error category by either clicking on the error category heading or by clicking the expand/collapse chevron.</span></span> <span data-ttu-id="c5f12-112">Když rozbalíte kategorii chyby, zobrazí se následující další pomoc:</span><span class="sxs-lookup"><span data-stu-id="c5f12-112">When you expand an error category, the following additional help is displayed:</span></span>  
  
-   <span data-ttu-id="c5f12-113">Instance této chyby.</span><span class="sxs-lookup"><span data-stu-id="c5f12-113">Instances of this error.</span></span>  
  
-   <span data-ttu-id="c5f12-114">Nápověda k této chybě.</span><span class="sxs-lookup"><span data-stu-id="c5f12-114">Help with this error.</span></span>  
  
-   <span data-ttu-id="c5f12-115">Fórum příspěvky o této chybě.</span><span class="sxs-lookup"><span data-stu-id="c5f12-115">Forum posts about this error.</span></span>  
  
### <a name="instances-of-this-error"></a><span data-ttu-id="c5f12-116">Instance této chyby</span><span class="sxs-lookup"><span data-stu-id="c5f12-116">Instances of This Error</span></span>  
 <span data-ttu-id="c5f12-117">Další nápověda seznam všech instancí chybu v aktuálním projektu.</span><span class="sxs-lookup"><span data-stu-id="c5f12-117">The additional help list all instances of the error in your current project.</span></span> <span data-ttu-id="c5f12-118">Mnoho chyb obsahovat přesné umístění v následujícím formátu: *[název projektu]* *[název formuláře]* řádku:*[číslo]* sloupec:*– sloupec číslo*.</span><span class="sxs-lookup"><span data-stu-id="c5f12-118">Many errors include an exact location in the following format: *[Project Name]* *[Form Name]* Line:*[Line Number]* Column:*[Column Number]*.</span></span> <span data-ttu-id="c5f12-119">**Přejít ke kódu** odkaz vás nasměruje na umístění ve vašem kódu, kde dojde k chybě.</span><span class="sxs-lookup"><span data-stu-id="c5f12-119">The **Go to code** link takes you to the location in your code where the error occurs.</span></span>  
  
 <span data-ttu-id="c5f12-120">Pokud zásobníku volání je spojen s chybou, můžete kliknout **zobrazit zásobník volání** propojení, které dále rozšiřujících chyby, chcete-li zobrazit zásobník volání.</span><span class="sxs-lookup"><span data-stu-id="c5f12-120">If a call stack is associated with the error, you can click the **Show Call Stack** link, which further expands the error to show the call stack.</span></span> <span data-ttu-id="c5f12-121">Zkoumání zásobník může poskytnout cenné informace o ladění.</span><span class="sxs-lookup"><span data-stu-id="c5f12-121">Examining the stack can provide valuable debugging information.</span></span> <span data-ttu-id="c5f12-122">Můžete například sledovat, funkce, které byly volány předtím, než došlo k chybě.</span><span class="sxs-lookup"><span data-stu-id="c5f12-122">For example, you can track the functions that were called before the error occurred.</span></span> <span data-ttu-id="c5f12-123">Zásobník volání je volitelný, takže můžete zkopírovat a uložit ho.</span><span class="sxs-lookup"><span data-stu-id="c5f12-123">The call stack is selectable so that you can copy and save it.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c5f12-124">V jazyce Visual Basic v seznamu chyb při návrhu nezobrazí více než jednu chybu, ale může zobrazovat více instancí stejné chybě.</span><span class="sxs-lookup"><span data-stu-id="c5f12-124">In Visual Basic, the design-time error list does not display more than one error, but it may display multiple instances of the same error.</span></span> <span data-ttu-id="c5f12-125">Chyby v aplikaci Visual C++, nemají goto code odkazy nebo odkazy na čísla řádku.</span><span class="sxs-lookup"><span data-stu-id="c5f12-125">In Visual C++, the errors do not have goto code links/line number links.</span></span>  
  
### <a name="help-with-this-error"></a><span data-ttu-id="c5f12-126">Nápověda k této chybě</span><span class="sxs-lookup"><span data-stu-id="c5f12-126">Help with This Error</span></span>  
 <span data-ttu-id="c5f12-127">Pokud chyba obsahuje odkaz na související téma nápovědy MSDN, další pomoc bude obsahovat odkaz na téma nápovědy.</span><span class="sxs-lookup"><span data-stu-id="c5f12-127">If the error contains a link to an associated MSDN help topic, the additional help will include a link to the help topic.</span></span> <span data-ttu-id="c5f12-128">Když kliknete na odkaz, zobrazí se v sadě Visual Studio související téma nápovědy.</span><span class="sxs-lookup"><span data-stu-id="c5f12-128">When you click the link, the associated help topic appears in Visual Studio.</span></span>  
  
### <a name="forum-posts-about-this-error"></a><span data-ttu-id="c5f12-129">Fórum příspěvky o této chybě</span><span class="sxs-lookup"><span data-stu-id="c5f12-129">Forum posts about this error</span></span>  
 <span data-ttu-id="c5f12-130">Další pomoc, bude obsahovat odkaz na příspěvků na fórech MSDN týkající se chyby.</span><span class="sxs-lookup"><span data-stu-id="c5f12-130">The additional help will include a link to MSDN forum posts related to the error.</span></span> <span data-ttu-id="c5f12-131">Fóra budou vyhledány podle řetězec chybové zprávy.</span><span class="sxs-lookup"><span data-stu-id="c5f12-131">The forums are searched based on the string of the error message.</span></span> <span data-ttu-id="c5f12-132">Můžete také zkusit hledání následující fóra:</span><span class="sxs-lookup"><span data-stu-id="c5f12-132">You can also try searching the following forums:</span></span>  
  
-   [<span data-ttu-id="c5f12-133">Fórum Návrháře formulářů Windows</span><span class="sxs-lookup"><span data-stu-id="c5f12-133">Windows Forms Designer Forum</span></span>](https://go.microsoft.com/fwlink/?LinkId=203524)  
  
-   [<span data-ttu-id="c5f12-134">Windows Forms fóra</span><span class="sxs-lookup"><span data-stu-id="c5f12-134">Windows Forms Forums</span></span>](https://go.microsoft.com/fwlink/?LinkId=203523)  
  
### <a name="ignore-and-continue"></a><span data-ttu-id="c5f12-135">Ignorovat a pokračovat</span><span class="sxs-lookup"><span data-stu-id="c5f12-135">Ignore and Continue</span></span>  
 <span data-ttu-id="c5f12-136">Můžete ignorovat chybovou podmínku a pokračovat v načítání návrháře.</span><span class="sxs-lookup"><span data-stu-id="c5f12-136">You can choose to ignore the error condition and continue loading the designer.</span></span> <span data-ttu-id="c5f12-137">Výběrem této akce může způsobit neočekávané chování.</span><span class="sxs-lookup"><span data-stu-id="c5f12-137">Choosing this action may result in unexpected behavior.</span></span> <span data-ttu-id="c5f12-138">Například ovládací prvky se nemusí zobrazit na návrhové ploše.</span><span class="sxs-lookup"><span data-stu-id="c5f12-138">For example, controls may not appear on the design surface.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5f12-139">Viz také</span><span class="sxs-lookup"><span data-stu-id="c5f12-139">See Also</span></span>  
 [<span data-ttu-id="c5f12-140">Řešení potíží s vývojem během návrhu</span><span class="sxs-lookup"><span data-stu-id="c5f12-140">Troubleshooting Design-Time Development</span></span>](https://msdn.microsoft.com/library/e048d08e-fa7c-4be8-b238-4abaa199a0a6)  
 [<span data-ttu-id="c5f12-141">Řešení potíží s vytvářením ovládacích prvků a komponent</span><span class="sxs-lookup"><span data-stu-id="c5f12-141">Troubleshooting Control and Component Authoring</span></span>](../../../../docs/framework/winforms/controls/troubleshooting-control-and-component-authoring.md)  
 [<span data-ttu-id="c5f12-142">Vývoj ovládacích prvků Windows Forms v době návrhu</span><span class="sxs-lookup"><span data-stu-id="c5f12-142">Developing Windows Forms Controls at Design Time</span></span>](../../../../docs/framework/winforms/controls/developing-windows-forms-controls-at-design-time.md)  
 [<span data-ttu-id="c5f12-143">Chybové zprávy Návrháře formulářů Windows</span><span class="sxs-lookup"><span data-stu-id="c5f12-143">Windows Forms Designer Error Messages</span></span>](https://msdn.microsoft.com/library/cf610bf4-5fe4-471c-bce7-6a05ece07bd2)
