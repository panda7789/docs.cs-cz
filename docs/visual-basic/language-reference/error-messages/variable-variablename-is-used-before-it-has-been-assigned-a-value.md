---
title: Proměnná '<variablename>' je použita před tím, než jí byla přiřazena hodnota.
ms.date: 07/20/2015
f1_keywords:
- vbc42104
- BC42104
helpviewer_keywords:
- BC42104
ms.assetid: 6909aa0b-b4a1-46f5-a18c-ba3e565c1dd8
ms.openlocfilehash: 46551a917aeb794c8d35985076b67a315386f628
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58819356"
---
# <a name="variable-variablename-is-used-before-it-has-been-assigned-a-value"></a><span data-ttu-id="3bd2d-102">Proměnná '\<NázevProměnné >' se použije dřív, než jí byla přiřazena hodnota</span><span class="sxs-lookup"><span data-stu-id="3bd2d-102">Variable '\<variablename>' is used before it has been assigned a value</span></span>
<span data-ttu-id="3bd2d-103">Proměnná '\<NázevProměnné >' se použije dřív, než jí byla přiřazena hodnota.</span><span class="sxs-lookup"><span data-stu-id="3bd2d-103">Variable '\<variablename>' is used before it has been assigned a value.</span></span> <span data-ttu-id="3bd2d-104">Výjimka nulového odkazu by mohlo způsobit v době běhu.</span><span class="sxs-lookup"><span data-stu-id="3bd2d-104">A null reference exception could result at run time.</span></span>  
  
 <span data-ttu-id="3bd2d-105">Aplikace má alespoň jednu možných cest pomocí jeho kód, který načte proměnnou předtím, než je k němu přiřazen žádnou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="3bd2d-105">An application has at least one possible path through its code that reads a variable before any value is assigned to it.</span></span>  
  
 <span data-ttu-id="3bd2d-106">Pokud proměnnou nikdy byla přiřazena hodnota, obsahuje výchozí hodnotu pro jeho datového typu.</span><span class="sxs-lookup"><span data-stu-id="3bd2d-106">If a variable has never been assigned a value, it holds the default value for its data type.</span></span> <span data-ttu-id="3bd2d-107">Pro datový typ odkazu, je tato výchozí hodnota [nic](../../../visual-basic/language-reference/nothing.md).</span><span class="sxs-lookup"><span data-stu-id="3bd2d-107">For a reference data type, that default value is [Nothing](../../../visual-basic/language-reference/nothing.md).</span></span> <span data-ttu-id="3bd2d-108">Čtení odkaz na proměnnou, která má hodnotu `Nothing` může způsobit, že <xref:System.NullReferenceException> v některých případech.</span><span class="sxs-lookup"><span data-stu-id="3bd2d-108">Reading a reference variable that has a value of `Nothing` can cause a <xref:System.NullReferenceException> in some circumstances.</span></span>  
  
 <span data-ttu-id="3bd2d-109">Ve výchozím nastavení tato zpráva je upozornění.</span><span class="sxs-lookup"><span data-stu-id="3bd2d-109">By default, this message is a warning.</span></span> <span data-ttu-id="3bd2d-110">Další informace o zobrazení nebo skrytí upozornění zpracování upozornění jako chyby, najdete v části [Konfigurace upozornění v jazyce Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="3bd2d-110">For more information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="3bd2d-111">**ID chyby:** BC42104</span><span class="sxs-lookup"><span data-stu-id="3bd2d-111">**Error ID:** BC42104</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="3bd2d-112">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="3bd2d-112">To correct this error</span></span>  
  
-   <span data-ttu-id="3bd2d-113">Zkontrolujte logiku toku řízení a ujistěte se, že proměnná obsahuje platnou hodnotu před řízení se předá jakýkoli příkaz, který čte ho.</span><span class="sxs-lookup"><span data-stu-id="3bd2d-113">Check your control flow logic and make sure the variable has a valid value before control passes to any statement that reads it.</span></span>  
  
-   <span data-ttu-id="3bd2d-114">Jedním ze způsobů zaručí, že má proměnná vždy platná hodnota je inicializovat ho jako součást její deklarace.</span><span class="sxs-lookup"><span data-stu-id="3bd2d-114">One way to guarantee that the variable always has a valid value is to initialize it as part of its declaration.</span></span> <span data-ttu-id="3bd2d-115">Naleznete v části "Inicializace" v [Dim – příkaz](../../../visual-basic/language-reference/statements/dim-statement.md).</span><span class="sxs-lookup"><span data-stu-id="3bd2d-115">See "Initialization" in [Dim Statement](../../../visual-basic/language-reference/statements/dim-statement.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3bd2d-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3bd2d-116">See also</span></span>

- [<span data-ttu-id="3bd2d-117">Příkaz Dim</span><span class="sxs-lookup"><span data-stu-id="3bd2d-117">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)
- [<span data-ttu-id="3bd2d-118">Deklarace proměnné</span><span class="sxs-lookup"><span data-stu-id="3bd2d-118">Variable Declaration</span></span>](../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [<span data-ttu-id="3bd2d-119">Řešení potíží s proměnnými</span><span class="sxs-lookup"><span data-stu-id="3bd2d-119">Troubleshooting Variables</span></span>](../../../visual-basic/programming-guide/language-features/variables/troubleshooting-variables.md)
