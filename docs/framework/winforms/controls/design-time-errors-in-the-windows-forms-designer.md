---
title: Chyby při návrhu v Návrháři formulářů Windows
ms.date: 03/30/2017
f1_keywords:
- DTELErrorList
- WhyDTELPage
helpviewer_keywords:
- errors [Windows Forms Designer]
- design-time errors [Windows Forms Designer]
ms.assetid: ad408380-825a-46d8-9a4a-531b130b88ce
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: cce9baf1523391e281593428b633c401103b42b5
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/24/2019
ms.locfileid: "70015975"
---
# <a name="design-time-errors-in-the-windows-forms-designer"></a><span data-ttu-id="5debf-102">Chyby v době návrhu v Návrhář formulářů</span><span class="sxs-lookup"><span data-stu-id="5debf-102">Design-time errors in the Windows Forms Designer</span></span>

<span data-ttu-id="5debf-103">Toto téma vysvětluje význam a použití seznamu chyb v době návrhu, který se zobrazí v aplikaci Visual Studio, když se Návrhář formulářů nepodařilo načíst.</span><span class="sxs-lookup"><span data-stu-id="5debf-103">This topic explains the meaning and use of the design-time error list that appears in Visual Studio when the Windows Forms Designer fails to load.</span></span> <span data-ttu-id="5debf-104">Pokud se zobrazí tento seznam chyb, neměli byste ho interpretovat jako chybu v návrháři, ale jako pomůcku pro opravu chyb v kódu.</span><span class="sxs-lookup"><span data-stu-id="5debf-104">If this error list appears, you should not interpret it as a bug in the designer, but as an aid to correcting errors in your code.</span></span>

<span data-ttu-id="5debf-105">Základní porozumění tomuto seznamu chyb vám pomůže ladit aplikace tím, že poskytuje podrobné informace o chybách a navrhuje možná řešení.</span><span class="sxs-lookup"><span data-stu-id="5debf-105">A basic understanding of this error list will help you debug your applications by providing detailed information about the errors and suggesting possible solutions.</span></span>

## <a name="the-design-time-error-list-interface"></a><span data-ttu-id="5debf-106">Rozhraní seznamu chyb v době návrhu</span><span class="sxs-lookup"><span data-stu-id="5debf-106">The design-time error list interface</span></span>

<span data-ttu-id="5debf-107">Pokud se Návrhář formulářů nepodařilo načíst, zobrazí se v Návrháři seznam chyb.</span><span class="sxs-lookup"><span data-stu-id="5debf-107">If the Windows Forms Designer fails to load, an error list appears in the designer.</span></span> <span data-ttu-id="5debf-108">Chyby jsou seskupené do kategorií.</span><span class="sxs-lookup"><span data-stu-id="5debf-108">The errors are grouped into categories.</span></span> <span data-ttu-id="5debf-109">Například pokud máte čtyři instance nedeklarovaných proměnných, budou seskupeny do stejné kategorie chyb.</span><span class="sxs-lookup"><span data-stu-id="5debf-109">For example, if you have four instances of undeclared variables, these will be grouped into the same error category.</span></span> <span data-ttu-id="5debf-110">Každá kategorie chyb obsahuje stručný popis, který shrnuje chybu.</span><span class="sxs-lookup"><span data-stu-id="5debf-110">Each error category includes a brief description that summarizes the error.</span></span>

<span data-ttu-id="5debf-111">Kategorii chyb můžete rozbalit nebo sbalit buď kliknutím na záhlaví kategorie chyby, nebo kliknutím na dvojitou šipku rozbalení/sbalení.</span><span class="sxs-lookup"><span data-stu-id="5debf-111">You can expand or collapse an error category by either clicking on the error category heading or by clicking the expand/collapse chevron.</span></span> <span data-ttu-id="5debf-112">Po rozbalení kategorie chyby se zobrazí následující další Help:</span><span class="sxs-lookup"><span data-stu-id="5debf-112">When you expand an error category, the following additional help is displayed:</span></span>

- <span data-ttu-id="5debf-113">Instance této chyby</span><span class="sxs-lookup"><span data-stu-id="5debf-113">Instances of this error.</span></span>

- <span data-ttu-id="5debf-114">Pomůžete s touto chybou.</span><span class="sxs-lookup"><span data-stu-id="5debf-114">Help with this error.</span></span>

- <span data-ttu-id="5debf-115">Příspěvky o této chybě ve fórech</span><span class="sxs-lookup"><span data-stu-id="5debf-115">Forum posts about this error.</span></span>

### <a name="instances-of-this-error"></a><span data-ttu-id="5debf-116">Instance této chyby</span><span class="sxs-lookup"><span data-stu-id="5debf-116">Instances of this error</span></span>

<span data-ttu-id="5debf-117">Další Help seznam všech výskytů chyby v aktuálním projektu.</span><span class="sxs-lookup"><span data-stu-id="5debf-117">The additional help list all instances of the error in your current project.</span></span> <span data-ttu-id="5debf-118">Mnoho chyb zahrnuje přesné umístění v následujícím formátu: *[název projektu]* *[název formuláře]* řádek: *[řádek číslo]* sloupec: *[číslo sloupce]* .</span><span class="sxs-lookup"><span data-stu-id="5debf-118">Many errors include an exact location in the following format: *[Project Name]* *[Form Name]* Line:*[Line Number]* Column:*[Column Number]*.</span></span> <span data-ttu-id="5debf-119">Odkaz **Přejít na kód** přejde do umístění ve vašem kódu, kde dojde k chybě.</span><span class="sxs-lookup"><span data-stu-id="5debf-119">The **Go to code** link takes you to the location in your code where the error occurs.</span></span>

<span data-ttu-id="5debf-120">Pokud je zásobník volání spojen s chybou, můžete kliknout na odkaz **Zobrazit zásobník volání** , který dále rozšiřuje chybu pro zobrazení zásobníku volání.</span><span class="sxs-lookup"><span data-stu-id="5debf-120">If a call stack is associated with the error, you can click the **Show Call Stack** link, which further expands the error to show the call stack.</span></span> <span data-ttu-id="5debf-121">Prozkoumání zásobníku může poskytnout cenné informace o ladění.</span><span class="sxs-lookup"><span data-stu-id="5debf-121">Examining the stack can provide valuable debugging information.</span></span> <span data-ttu-id="5debf-122">Můžete například sledovat funkce, které byly volány před tím, než došlo k chybě.</span><span class="sxs-lookup"><span data-stu-id="5debf-122">For example, you can track the functions that were called before the error occurred.</span></span> <span data-ttu-id="5debf-123">Zásobník volání je možné vybrat, abyste ho mohli zkopírovat a uložit.</span><span class="sxs-lookup"><span data-stu-id="5debf-123">The call stack is selectable so that you can copy and save it.</span></span>

> [!NOTE]
> <span data-ttu-id="5debf-124">V Visual Basic seznam chyb v době návrhu nezobrazuje více než jednu chybu, ale může zobrazit více instancí stejné chyby.</span><span class="sxs-lookup"><span data-stu-id="5debf-124">In Visual Basic, the design-time error list does not display more than one error, but it may display multiple instances of the same error.</span></span> <span data-ttu-id="5debf-125">V vizuálu C++chyby neobsahují odkazy kódu goto nebo odkazy na řádky.</span><span class="sxs-lookup"><span data-stu-id="5debf-125">In Visual C++, the errors do not have goto code links/line number links.</span></span>

### <a name="forum-posts-about-this-error"></a><span data-ttu-id="5debf-126">Příspěvky o této chybě ve fórech</span><span class="sxs-lookup"><span data-stu-id="5debf-126">Forum posts about this error</span></span>

<span data-ttu-id="5debf-127">Další help obsahuje odkaz na příspěvky na fórech související s chybou.</span><span class="sxs-lookup"><span data-stu-id="5debf-127">The additional help includes a link to forum posts related to the error.</span></span> <span data-ttu-id="5debf-128">Fóra se prohledávají na základě řetězce chybové zprávy.</span><span class="sxs-lookup"><span data-stu-id="5debf-128">The forums are searched based on the string of the error message.</span></span> <span data-ttu-id="5debf-129">Můžete si také vyzkoušet hledání na následujících fórech:</span><span class="sxs-lookup"><span data-stu-id="5debf-129">You can also try searching on the following forums:</span></span>

- [<span data-ttu-id="5debf-130">Fórum Návrhář formulářů</span><span class="sxs-lookup"><span data-stu-id="5debf-130">Windows Forms Designer forum</span></span>](https://social.msdn.microsoft.com/Forums/windows/home?forum=winformsdesigner)

- [<span data-ttu-id="5debf-131">Fórum model Windows Forms</span><span class="sxs-lookup"><span data-stu-id="5debf-131">Windows Forms forum</span></span>](https://social.msdn.microsoft.com/Forums/windows/home?category=windowsforms)

### <a name="ignore-and-continue"></a><span data-ttu-id="5debf-132">Ignorovat a pokračovat</span><span class="sxs-lookup"><span data-stu-id="5debf-132">Ignore and continue</span></span>

<span data-ttu-id="5debf-133">Můžete se rozhodnout Ignorovat chybový stav a pokračovat v načítání návrháře.</span><span class="sxs-lookup"><span data-stu-id="5debf-133">You can choose to ignore the error condition and continue loading the designer.</span></span> <span data-ttu-id="5debf-134">Pokud zvolíte tuto akci, může dojít k neočekávanému chování.</span><span class="sxs-lookup"><span data-stu-id="5debf-134">Choosing this action may result in unexpected behavior.</span></span> <span data-ttu-id="5debf-135">Například ovládací prvky se nemusí zobrazit na návrhové ploše.</span><span class="sxs-lookup"><span data-stu-id="5debf-135">For example, controls may not appear on the design surface.</span></span>

## <a name="see-also"></a><span data-ttu-id="5debf-136">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5debf-136">See also</span></span>

- <span data-ttu-id="5debf-137">[Řešení potíží s vývojem v době návrhu](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ms171843(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="5debf-137">[Troubleshooting Design-Time Development](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ms171843(v=vs.120))</span></span>
- [<span data-ttu-id="5debf-138">Řešení potíží s vytvářením ovládacích prvků a komponent</span><span class="sxs-lookup"><span data-stu-id="5debf-138">Troubleshooting Control and Component Authoring</span></span>](troubleshooting-control-and-component-authoring.md)
- [<span data-ttu-id="5debf-139">Vývoj ovládacích prvků Windows Forms v době návrhu</span><span class="sxs-lookup"><span data-stu-id="5debf-139">Developing Windows Forms Controls at Design Time</span></span>](developing-windows-forms-controls-at-design-time.md)
- <span data-ttu-id="5debf-140">[Návrhář formulářů chybové zprávy](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms233640(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="5debf-140">[Windows Forms Designer Error Messages](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms233640(v=vs.100))</span></span>
