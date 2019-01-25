---
title: Vlastnost &#39; &lt;propertyname&gt; &#39; kódu&#39;t vrátí hodnotu ve všech cestách kódu.
ms.date: 07/20/2015
f1_keywords:
- bc42107
- vbc42107
helpviewer_keywords:
- BC42107
ms.assetid: 06800966-9c3b-4844-9f13-83ac95607d32
ms.openlocfilehash: b8059ebc9b6c1de685f2f04c3ee362ab8cf6d05e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54611251"
---
# <a name="property-39ltpropertynamegt39-doesn39t-return-a-value-on-all-code-paths"></a><span data-ttu-id="48c45-102">Vlastnost &#39; &lt;propertyname&gt; &#39; kódu&#39;t vrátí hodnotu ve všech cestách kódu.</span><span class="sxs-lookup"><span data-stu-id="48c45-102">Property &#39;&lt;propertyname&gt;&#39; doesn&#39;t return a value on all code paths</span></span>
<span data-ttu-id="48c45-103">Vlastnost "\<propertyname >' nevrací hodnotu ve všech cestách kódu.</span><span class="sxs-lookup"><span data-stu-id="48c45-103">Property '\<propertyname>' doesn't return a value on all code paths.</span></span> <span data-ttu-id="48c45-104">V době běhu při použití vráceného výsledku může dojít k výjimce odkazem s hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="48c45-104">A null reference exception could occur at run time when the result is used.</span></span>  
  
 <span data-ttu-id="48c45-105">Vlastnost `Get` postup obsahuje alespoň jeden možných cest pomocí jejího kódu, která nevrací hodnotu.</span><span class="sxs-lookup"><span data-stu-id="48c45-105">A property `Get` procedure has at least one possible path through its code that does not return a value.</span></span>  
  
 <span data-ttu-id="48c45-106">Může vrátit hodnotu z vlastnosti `Get` postup v některém z následujících způsobů:</span><span class="sxs-lookup"><span data-stu-id="48c45-106">You can return a value from a property `Get` procedure in any of the following ways:</span></span>  
  
-   <span data-ttu-id="48c45-107">Přiřaďte hodnotu k názvu vlastnosti a pak proveďte `Exit Property` příkazu.</span><span class="sxs-lookup"><span data-stu-id="48c45-107">Assign the value to the property name and then perform an `Exit Property` statement.</span></span>  
  
-   <span data-ttu-id="48c45-108">Přiřaďte hodnotu k názvu vlastnosti a pak proveďte `End Get` příkazu.</span><span class="sxs-lookup"><span data-stu-id="48c45-108">Assign the value to the property name and then perform the `End Get` statement.</span></span>  
  
-   <span data-ttu-id="48c45-109">Hodnota v [příkaz Return](../../../visual-basic/language-reference/statements/return-statement.md).</span><span class="sxs-lookup"><span data-stu-id="48c45-109">Include the value in a [Return Statement](../../../visual-basic/language-reference/statements/return-statement.md).</span></span>  
  
 <span data-ttu-id="48c45-110">Pokud řízení se předá `Exit Property` nebo `End Get` a jste ještě nepřiřadili žádné hodnoty názvu vlastnosti `Get` postup vrátí výchozí hodnotu vlastnosti datového typu.</span><span class="sxs-lookup"><span data-stu-id="48c45-110">If control passes to `Exit Property` or `End Get` and you have not assigned any value to the property name, the `Get` procedure returns the default value of the property's data type.</span></span> <span data-ttu-id="48c45-111">Další informace najdete v tématu "Chování" [Function – příkaz](../../../visual-basic/language-reference/statements/function-statement.md).</span><span class="sxs-lookup"><span data-stu-id="48c45-111">For more information, see "Behavior" in [Function Statement](../../../visual-basic/language-reference/statements/function-statement.md).</span></span>  
  
 <span data-ttu-id="48c45-112">Ve výchozím nastavení tato zpráva je upozornění.</span><span class="sxs-lookup"><span data-stu-id="48c45-112">By default, this message is a warning.</span></span> <span data-ttu-id="48c45-113">Další informace o zobrazení nebo skrytí upozornění zpracování upozornění jako chyby, najdete v části [Konfigurace upozornění v jazyce Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="48c45-113">For more information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="48c45-114">**ID chyby:** BC42107</span><span class="sxs-lookup"><span data-stu-id="48c45-114">**Error ID:** BC42107</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="48c45-115">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="48c45-115">To correct this error</span></span>  
  
-   <span data-ttu-id="48c45-116">Zkontrolujte logiku toku řízení a ujistěte se, že přidělíte hodnotu před každý příkaz, který způsobí, že vrácení.</span><span class="sxs-lookup"><span data-stu-id="48c45-116">Check your control flow logic and make sure you assign a value before every statement that causes a return.</span></span>  
  
     <span data-ttu-id="48c45-117">Je snazší zajistit, že každý návrat z procedury vrací hodnotu, pokud vždy používáte `Return` příkazu.</span><span class="sxs-lookup"><span data-stu-id="48c45-117">It is easier to guarantee that every return from the procedure returns a value if you always use the `Return` statement.</span></span> <span data-ttu-id="48c45-118">Pokud to provedete, poslední příkaz před `End Get` by měl být `Return` příkazu.</span><span class="sxs-lookup"><span data-stu-id="48c45-118">If you do this, the last statement before `End Get` should be a `Return` statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48c45-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="48c45-119">See also</span></span>
- [<span data-ttu-id="48c45-120">Procedury vlastnosti</span><span class="sxs-lookup"><span data-stu-id="48c45-120">Property Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)
- [<span data-ttu-id="48c45-121">Příkaz Property</span><span class="sxs-lookup"><span data-stu-id="48c45-121">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)
- [<span data-ttu-id="48c45-122">Příkaz Get</span><span class="sxs-lookup"><span data-stu-id="48c45-122">Get Statement</span></span>](../../../visual-basic/language-reference/statements/get-statement.md)
