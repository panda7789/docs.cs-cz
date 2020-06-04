---
title: Omezení
ms.date: 07/20/2015
helpviewer_keywords:
- limits
- limitations [Visual Basic]
- limitations
- limits, Visual Basic code
- Visual Basic code, limitations
ms.assetid: cf1646b7-5d24-48c6-9616-bda8a4849d91
ms.openlocfilehash: 46294b68bda8a5d2d21c0e4efea6a78e6a265ffe
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403184"
---
# <a name="visual-basic-limitations"></a><span data-ttu-id="d0757-102">Omezení jazyka Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d0757-102">Visual Basic Limitations</span></span>
<span data-ttu-id="d0757-103">Starší verze Visual Basic vynutily hranice v kódu, jako je délka názvů proměnných, počet proměnných povolených v modulech a velikost modulu.</span><span class="sxs-lookup"><span data-stu-id="d0757-103">Earlier versions of Visual Basic enforced boundaries in code, such as the length of variable names, the number of variables allowed in modules, and module size.</span></span> <span data-ttu-id="d0757-104">V Visual Basic .NET byla tato omezení odlehčena a poskytuje větší volnost v psaní a uspořádávání kódu.</span><span class="sxs-lookup"><span data-stu-id="d0757-104">In Visual Basic .NET, these restrictions have been relaxed, giving you greater freedom in writing and arranging your code.</span></span>  
  
 <span data-ttu-id="d0757-105">Fyzické limity jsou více závislé na paměti za běhu než při kompilaci.</span><span class="sxs-lookup"><span data-stu-id="d0757-105">Physical limits are dependent more on run-time memory than on compile-time considerations.</span></span> <span data-ttu-id="d0757-106">Pokud použijete obezřetné postupy programování a rozdělíte velké aplikace na více tříd a modulů, je velmi málo pravděpodobné, že zaznamenáte omezení interního Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="d0757-106">If you use prudent programming practices, and divide large applications into multiple classes and modules, then there is very little chance of encountering an internal Visual Basic limitation.</span></span>  
  
 <span data-ttu-id="d0757-107">Níže jsou uvedena některá omezení, která se mohou vyskytnout v extrémních případech:</span><span class="sxs-lookup"><span data-stu-id="d0757-107">The following are some limitations that you might encounter in extreme cases:</span></span>  
  
- <span data-ttu-id="d0757-108">**Délka názvu.**</span><span class="sxs-lookup"><span data-stu-id="d0757-108">**Name Length.**</span></span> <span data-ttu-id="d0757-109">Existuje maximální počet znaků pro název každého deklarovaného programovacího prvku.</span><span class="sxs-lookup"><span data-stu-id="d0757-109">There is a maximum number of characters for the name of every declared programming element.</span></span> <span data-ttu-id="d0757-110">Toto maximum platí pro celý řetězec kvalifikace, pokud je název elementu kvalifikován.</span><span class="sxs-lookup"><span data-stu-id="d0757-110">This maximum applies to an entire qualification string if the element name is qualified.</span></span> <span data-ttu-id="d0757-111">Viz [deklarované názvy elementů](../language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="d0757-111">See [Declared Element Names](../language-features/declared-elements/declared-element-names.md).</span></span>  
  
- <span data-ttu-id="d0757-112">**Délka řádku.**</span><span class="sxs-lookup"><span data-stu-id="d0757-112">**Line Length.**</span></span> <span data-ttu-id="d0757-113">Ve fyzickém řádku zdrojového kódu je maximálně 65535 znaků.</span><span class="sxs-lookup"><span data-stu-id="d0757-113">There is a maximum of 65535 characters in a physical line of source code.</span></span> <span data-ttu-id="d0757-114">Pokud použijete znaky pro pokračování řádku, může být řádek logického zdrojového kódu delší.</span><span class="sxs-lookup"><span data-stu-id="d0757-114">The logical source code line can be longer if you use line continuation characters.</span></span> <span data-ttu-id="d0757-115">Viz [How to: break and kombinovat příkazy v kódu](how-to-break-and-combine-statements-in-code.md).</span><span class="sxs-lookup"><span data-stu-id="d0757-115">See [How to: Break and Combine Statements in Code](how-to-break-and-combine-statements-in-code.md).</span></span>  
  
- <span data-ttu-id="d0757-116">**Dimenze pole.**</span><span class="sxs-lookup"><span data-stu-id="d0757-116">**Array Dimensions.**</span></span> <span data-ttu-id="d0757-117">Existuje maximální počet dimenzí, které lze deklarovat pro pole.</span><span class="sxs-lookup"><span data-stu-id="d0757-117">There is a maximum number of dimensions you can declare for an array.</span></span> <span data-ttu-id="d0757-118">Tím se omezí počet indexů, které můžete použít k určení prvku pole.</span><span class="sxs-lookup"><span data-stu-id="d0757-118">This limits how many indexes you can use to specify an array element.</span></span> <span data-ttu-id="d0757-119">Zobrazení [dimenzí pole v Visual Basic](../language-features/arrays/array-dimensions.md).</span><span class="sxs-lookup"><span data-stu-id="d0757-119">See [Array Dimensions in Visual Basic](../language-features/arrays/array-dimensions.md).</span></span>  
  
- <span data-ttu-id="d0757-120">**Délka řetězce.**</span><span class="sxs-lookup"><span data-stu-id="d0757-120">**String Length.**</span></span> <span data-ttu-id="d0757-121">Existuje maximální počet znaků Unicode, které lze uložit v jednom řetězci.</span><span class="sxs-lookup"><span data-stu-id="d0757-121">There is a maximum number of Unicode characters you can store in a single string.</span></span> <span data-ttu-id="d0757-122">Viz [datový typ String](../../language-reference/data-types/string-data-type.md).</span><span class="sxs-lookup"><span data-stu-id="d0757-122">See [String Data Type](../../language-reference/data-types/string-data-type.md).</span></span>  
  
- <span data-ttu-id="d0757-123">**Délka řetězce prostředí.**</span><span class="sxs-lookup"><span data-stu-id="d0757-123">**Environment String Length.**</span></span> <span data-ttu-id="d0757-124">Pro libovolný řetězec prostředí použité jako argument příkazového řádku je k dispozici maximálně 32768 znaků.</span><span class="sxs-lookup"><span data-stu-id="d0757-124">There is a maximum of 32768 characters for any environment string used as a command-line argument.</span></span> <span data-ttu-id="d0757-125">Toto omezení se vztahuje na všechny platformy.</span><span class="sxs-lookup"><span data-stu-id="d0757-125">This is a limitation on all platforms.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0757-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="d0757-126">See also</span></span>

- [<span data-ttu-id="d0757-127">Struktura programu a konvence kódu</span><span class="sxs-lookup"><span data-stu-id="d0757-127">Program Structure and Code Conventions</span></span>](program-structure-and-code-conventions.md)
- [<span data-ttu-id="d0757-128">Zásady vytváření názvů jazyka Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d0757-128">Visual Basic Naming Conventions</span></span>](naming-conventions.md)
