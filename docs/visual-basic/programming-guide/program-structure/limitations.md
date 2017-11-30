---
title: "Omezení jazyka Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- limits
- limitations [Visual Basic]
- limitations
- limits, Visual Basic code
- Visual Basic code, limitations
ms.assetid: cf1646b7-5d24-48c6-9616-bda8a4849d91
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 97a2e162b9f1a673fbe805a5d2ef1421cd423a4f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="visual-basic-limitations"></a><span data-ttu-id="ac5e1-102">Omezení jazyka Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ac5e1-102">Visual Basic Limitations</span></span>
<span data-ttu-id="ac5e1-103">Starší verze [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] vynutit hranice v kódu, jako je délka názvy proměnných, počet proměnných v moduly a velikost modulu povoleny.</span><span class="sxs-lookup"><span data-stu-id="ac5e1-103">Earlier versions of [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] enforced boundaries in code, such as the length of variable names, the number of variables allowed in modules, and module size.</span></span> <span data-ttu-id="ac5e1-104">V jazyce Visual Basic .NET tato omezení mít byla zmírnit, která poskytuje větší svobodu v psaní a uspořádání kódu.</span><span class="sxs-lookup"><span data-stu-id="ac5e1-104">In Visual Basic .NET, these restrictions have been relaxed, giving you greater freedom in writing and arranging your code.</span></span>  
  
 <span data-ttu-id="ac5e1-105">Fyzické omezení jsou závislé více běhové paměti než v době kompilace aspekty.</span><span class="sxs-lookup"><span data-stu-id="ac5e1-105">Physical limits are dependent more on run-time memory than on compile-time considerations.</span></span> <span data-ttu-id="ac5e1-106">Pokud používáte doporučeno programovací postupy a velké aplikace rozdělte do více tříd a moduly, pak je velmi malé pravděpodobnost vzniku interní [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] omezení.</span><span class="sxs-lookup"><span data-stu-id="ac5e1-106">If you use prudent programming practices, and divide large applications into multiple classes and modules, then there is very little chance of encountering an internal [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] limitation.</span></span>  
  
 <span data-ttu-id="ac5e1-107">Tady jsou některá omezení, které se mohou vyskytnout ve výjimečných případech:</span><span class="sxs-lookup"><span data-stu-id="ac5e1-107">The following are some limitations that you might encounter in extreme cases:</span></span>  
  
-   <span data-ttu-id="ac5e1-108">**Délka názvu.**</span><span class="sxs-lookup"><span data-stu-id="ac5e1-108">**Name Length.**</span></span> <span data-ttu-id="ac5e1-109">Maximální počet znaků pro název každé deklarované programovací element není k dispozici.</span><span class="sxs-lookup"><span data-stu-id="ac5e1-109">There is a maximum number of characters for the name of every declared programming element.</span></span> <span data-ttu-id="ac5e1-110">Tento maximální platí pro řetězec celý kvalifikace v případě, že je kvalifikovaný název elementu.</span><span class="sxs-lookup"><span data-stu-id="ac5e1-110">This maximum applies to an entire qualification string if the element name is qualified.</span></span> <span data-ttu-id="ac5e1-111">V tématu [deklarované názvy elementů](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="ac5e1-111">See [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>  
  
-   <span data-ttu-id="ac5e1-112">**Délka řádku.**</span><span class="sxs-lookup"><span data-stu-id="ac5e1-112">**Line Length.**</span></span> <span data-ttu-id="ac5e1-113">Je delší než 65 535 znaků na fyzické řádku zdrojového kódu.</span><span class="sxs-lookup"><span data-stu-id="ac5e1-113">There is a maximum of 65535 characters in a physical line of source code.</span></span> <span data-ttu-id="ac5e1-114">Řádek kódu logické zdroj může být delší, pokud používáte znaky pokračování řádku.</span><span class="sxs-lookup"><span data-stu-id="ac5e1-114">The logical source code line can be longer if you use line continuation characters.</span></span> <span data-ttu-id="ac5e1-115">V tématu [postupy: přerušení a kombinace příkazů v kódu](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md).</span><span class="sxs-lookup"><span data-stu-id="ac5e1-115">See [How to: Break and Combine Statements in Code](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md).</span></span>  
  
-   <span data-ttu-id="ac5e1-116">**Rozměry pole.**</span><span class="sxs-lookup"><span data-stu-id="ac5e1-116">**Array Dimensions.**</span></span> <span data-ttu-id="ac5e1-117">Je maximální počet dimenzí, které můžou deklarovat pro pole.</span><span class="sxs-lookup"><span data-stu-id="ac5e1-117">There is a maximum number of dimensions you can declare for an array.</span></span> <span data-ttu-id="ac5e1-118">Toto nastavení omezuje počet indexů, můžete použít k určení k elementu pole.</span><span class="sxs-lookup"><span data-stu-id="ac5e1-118">This limits how many indexes you can use to specify an array element.</span></span> <span data-ttu-id="ac5e1-119">V tématu [pole dimenzí v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/arrays/array-dimensions.md).</span><span class="sxs-lookup"><span data-stu-id="ac5e1-119">See [Array Dimensions in Visual Basic](../../../visual-basic/programming-guide/language-features/arrays/array-dimensions.md).</span></span>  
  
-   <span data-ttu-id="ac5e1-120">**Délka řetězce.**</span><span class="sxs-lookup"><span data-stu-id="ac5e1-120">**String Length.**</span></span> <span data-ttu-id="ac5e1-121">Je maximální počet znaků Unicode, kam můžete ukládat v jednom řetězci.</span><span class="sxs-lookup"><span data-stu-id="ac5e1-121">There is a maximum number of Unicode characters you can store in a single string.</span></span> <span data-ttu-id="ac5e1-122">V tématu [řetězcový datový typ](../../../visual-basic/language-reference/data-types/string-data-type.md).</span><span class="sxs-lookup"><span data-stu-id="ac5e1-122">See [String Data Type](../../../visual-basic/language-reference/data-types/string-data-type.md).</span></span>  
  
-   <span data-ttu-id="ac5e1-123">**Délka řetězce prostředí.**</span><span class="sxs-lookup"><span data-stu-id="ac5e1-123">**Environment String Length.**</span></span> <span data-ttu-id="ac5e1-124">Je delší než 32768 znaků pro libovolný řetězec prostředí použít jako argument příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="ac5e1-124">There is a maximum of 32768 characters for any environment string used as a command-line argument.</span></span> <span data-ttu-id="ac5e1-125">Jedná se o omezení na všech platformách.</span><span class="sxs-lookup"><span data-stu-id="ac5e1-125">This is a limitation on all platforms.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac5e1-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="ac5e1-126">See Also</span></span>  
 [<span data-ttu-id="ac5e1-127">Struktura programu a pravidla týkající se kódu</span><span class="sxs-lookup"><span data-stu-id="ac5e1-127">Program Structure and Code Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)  
 [<span data-ttu-id="ac5e1-128">Zásady vytváření názvů jazyka Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ac5e1-128">Visual Basic Naming Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)
