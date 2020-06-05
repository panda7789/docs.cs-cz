---
title: Ve vlastnosti '<propertyname>' existují cesty kódu, které nevrací žádnou hodnotu.
ms.date: 07/20/2015
f1_keywords:
- bc42107
- vbc42107
helpviewer_keywords:
- BC42107
ms.assetid: 06800966-9c3b-4844-9f13-83ac95607d32
ms.openlocfilehash: 21a1c4dbab6e26cd1cb848e270bbda9a544c2a67
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400419"
---
# <a name="property-propertyname-doesnt-return-a-value-on-all-code-paths"></a><span data-ttu-id="2777a-102">Ve vlastnosti '\<propertyname>' existují cesty kódu, které nevrací žádnou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="2777a-102">Property '\<propertyname>' doesn't return a value on all code paths</span></span>
<span data-ttu-id="2777a-103">Vlastnost \<propertyname> nevrací hodnotu ve všech cestách kódu.</span><span class="sxs-lookup"><span data-stu-id="2777a-103">Property '\<propertyname>' doesn't return a value on all code paths.</span></span> <span data-ttu-id="2777a-104">Při použití výsledku může při spuštění dojít k výjimce odkazu s hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="2777a-104">A null reference exception could occur at run time when the result is used.</span></span>  
  
 <span data-ttu-id="2777a-105">Procedura vlastnosti `Get` má alespoň jednu možnou cestu prostřednictvím kódu, který nevrací hodnotu.</span><span class="sxs-lookup"><span data-stu-id="2777a-105">A property `Get` procedure has at least one possible path through its code that does not return a value.</span></span>  
  
 <span data-ttu-id="2777a-106">Můžete vrátit hodnotu z `Get` procedury vlastnosti některým z následujících způsobů:</span><span class="sxs-lookup"><span data-stu-id="2777a-106">You can return a value from a property `Get` procedure in any of the following ways:</span></span>  
  
- <span data-ttu-id="2777a-107">Přiřaďte hodnotu k názvu vlastnosti a pak proveďte `Exit Property` příkaz.</span><span class="sxs-lookup"><span data-stu-id="2777a-107">Assign the value to the property name and then perform an `Exit Property` statement.</span></span>  
  
- <span data-ttu-id="2777a-108">Přiřaďte hodnotu k názvu vlastnosti a pak `End Get` příkaz proveďte.</span><span class="sxs-lookup"><span data-stu-id="2777a-108">Assign the value to the property name and then perform the `End Get` statement.</span></span>  
  
- <span data-ttu-id="2777a-109">Zahrňte hodnotu do [příkazu return](../statements/return-statement.md).</span><span class="sxs-lookup"><span data-stu-id="2777a-109">Include the value in a [Return Statement](../statements/return-statement.md).</span></span>  
  
 <span data-ttu-id="2777a-110">Pokud řízení projde `Exit Property` nebo `End Get` a Vy jste k názvu vlastnosti nepřiřadili žádnou hodnotu, `Get` procedura vrátí výchozí hodnotu datového typu vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="2777a-110">If control passes to `Exit Property` or `End Get` and you have not assigned any value to the property name, the `Get` procedure returns the default value of the property's data type.</span></span> <span data-ttu-id="2777a-111">Další informace naleznete v tématu "Behavior" v [příkazu Function](../statements/function-statement.md).</span><span class="sxs-lookup"><span data-stu-id="2777a-111">For more information, see "Behavior" in [Function Statement](../statements/function-statement.md).</span></span>  
  
 <span data-ttu-id="2777a-112">Ve výchozím nastavení je tato zpráva upozornění.</span><span class="sxs-lookup"><span data-stu-id="2777a-112">By default, this message is a warning.</span></span> <span data-ttu-id="2777a-113">Další informace o skrývání upozornění nebo zpracování upozornění jako chyb najdete v tématu [Konfigurace upozornění v Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="2777a-113">For more information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="2777a-114">**ID chyby:** BC42107</span><span class="sxs-lookup"><span data-stu-id="2777a-114">**Error ID:** BC42107</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="2777a-115">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="2777a-115">To correct this error</span></span>  
  
- <span data-ttu-id="2777a-116">Zkontrolujte logiku toku ovládacích prvků a ujistěte se, že přiřadíte hodnotu před všemi příkazy, které způsobují návrat.</span><span class="sxs-lookup"><span data-stu-id="2777a-116">Check your control flow logic and make sure you assign a value before every statement that causes a return.</span></span>  
  
     <span data-ttu-id="2777a-117">Je snazší zaručit, že při každém návratu z této procedury vrátí hodnotu, pokud vždy použijete `Return` příkaz.</span><span class="sxs-lookup"><span data-stu-id="2777a-117">It is easier to guarantee that every return from the procedure returns a value if you always use the `Return` statement.</span></span> <span data-ttu-id="2777a-118">Pokud to uděláte, poslední příkaz před `End Get` by měl být `Return` příkaz.</span><span class="sxs-lookup"><span data-stu-id="2777a-118">If you do this, the last statement before `End Get` should be a `Return` statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2777a-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="2777a-119">See also</span></span>

- [<span data-ttu-id="2777a-120">Procedury vlastnosti</span><span class="sxs-lookup"><span data-stu-id="2777a-120">Property Procedures</span></span>](../../programming-guide/language-features/procedures/property-procedures.md)
- [<span data-ttu-id="2777a-121">Property – příkaz</span><span class="sxs-lookup"><span data-stu-id="2777a-121">Property Statement</span></span>](../statements/property-statement.md)
- [<span data-ttu-id="2777a-122">Get – příkaz</span><span class="sxs-lookup"><span data-stu-id="2777a-122">Get Statement</span></span>](../statements/get-statement.md)
