---
title: Datové typy znaků (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- data types [Visual Basic], character
- String data type [Visual Basic], character data types
- character data types [Visual Basic]
- Char data type [Visual Basic], character data types
- data types [Visual Basic], choosing
ms.assetid: 902479ef-1679-47fc-9911-0c1c5008226c
ms.openlocfilehash: 3b031c6e3dc04637128f95ca8e922d3298981287
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43553569"
---
# <a name="character-data-types-visual-basic"></a><span data-ttu-id="6260a-102">Datové typy znaků (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6260a-102">Character Data Types (Visual Basic)</span></span>
<span data-ttu-id="6260a-103">Visual Basic poskytuje *znakové datové typy* řešit tisknutelný a zobrazitelný znaků.</span><span class="sxs-lookup"><span data-stu-id="6260a-103">Visual Basic provides *character data types* to deal with printable and displayable characters.</span></span> <span data-ttu-id="6260a-104">Přestože oba vypořádat se znaky Unicode, `Char` obsahuje jeden znak, zatímco `String` obsahuje nekonečný počet znaků.</span><span class="sxs-lookup"><span data-stu-id="6260a-104">While they both deal with Unicode characters, `Char` holds a single character whereas `String` contains an indefinite number of characters.</span></span>  
  
 <span data-ttu-id="6260a-105">Tabulka, která zobrazuje vedle sebe porovnání datových typů jazyka Visual Basic, naleznete v tématu [datové typy](../../../../visual-basic/language-reference/data-types/index.md).</span><span class="sxs-lookup"><span data-stu-id="6260a-105">For a table that displays a side-by-side comparison of the Visual Basic data types, see [Data Types](../../../../visual-basic/language-reference/data-types/index.md).</span></span>  
  
## <a name="char-type"></a><span data-ttu-id="6260a-106">Znakový typ</span><span class="sxs-lookup"><span data-stu-id="6260a-106">Char Type</span></span>  
 <span data-ttu-id="6260a-107">`Char` Datový typ je jeden znak Unicode (16-bit) dva bajty.</span><span class="sxs-lookup"><span data-stu-id="6260a-107">The `Char` data type is a single two-byte (16-bit) Unicode character.</span></span> <span data-ttu-id="6260a-108">Pokud proměnná uchovává vždy přesně jeden znak, deklarujte ho jako `Char`.</span><span class="sxs-lookup"><span data-stu-id="6260a-108">If a variable always stores exactly one character, declare it as `Char`.</span></span> <span data-ttu-id="6260a-109">Příklad:</span><span class="sxs-lookup"><span data-stu-id="6260a-109">For example:</span></span>  
  
 [!code-vb[VbVbalrCharTypes#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrchartypes/vb/module1.vb#1)]
  
 <span data-ttu-id="6260a-110">Jednotlivé možné vlastnosti v `Char` nebo `String` proměnná je *kódu bodu*, nebo kód znaku ve znakové sadě Unicode.</span><span class="sxs-lookup"><span data-stu-id="6260a-110">Each possible value in a `Char` or `String` variable is a *code point*, or character code, in the Unicode character set.</span></span> <span data-ttu-id="6260a-111">Znaky Unicode obsahovat základní znakové sadě ASCII, různé jiné písmena abecedy, zvýraznění, symboly měny, zlomky, diakritiku a technické a matematické symboly.</span><span class="sxs-lookup"><span data-stu-id="6260a-111">Unicode characters include the basic ASCII character set, various other alphabet letters, accents, currency symbols, fractions, diacritics, and mathematical and technical symbols.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6260a-112">Znaková sada Unicode rezervy kód odkazuje D800 prostřednictvím DFFF (55296 prostřednictvím 55551 decimal) pro *náhradní páry*, které vyžadují dvě hodnoty 16bitové představuje bod jeden kód.</span><span class="sxs-lookup"><span data-stu-id="6260a-112">The Unicode character set reserves the code points D800 through DFFF (55296 through 55551 decimal) for *surrogate pairs*, which require two 16-bit values to represent a single code point.</span></span> <span data-ttu-id="6260a-113">A `Char` proměnná nemůže obsahovat náhradní pár a `String` používá dvě místa k uložení těchto pár.</span><span class="sxs-lookup"><span data-stu-id="6260a-113">A `Char` variable cannot hold a surrogate pair, and a `String` uses two positions to hold such a pair.</span></span>  
  
 <span data-ttu-id="6260a-114">Další informace najdete v tématu [Char – datový typ](../../../../visual-basic/language-reference/data-types/char-data-type.md).</span><span class="sxs-lookup"><span data-stu-id="6260a-114">For more information, see [Char Data Type](../../../../visual-basic/language-reference/data-types/char-data-type.md).</span></span>  
  
## <a name="string-type"></a><span data-ttu-id="6260a-115">String – typ</span><span class="sxs-lookup"><span data-stu-id="6260a-115">String Type</span></span>  
 <span data-ttu-id="6260a-116">`String` Datový typ je posloupnost nula nebo více znaků Unicode (16-bit) dva bajty.</span><span class="sxs-lookup"><span data-stu-id="6260a-116">The `String` data type is a sequence of zero or more two-byte (16-bit) Unicode characters.</span></span> <span data-ttu-id="6260a-117">Pokud proměnná může obsahovat nekonečný počet znaků, deklarujte ho jako `String`.</span><span class="sxs-lookup"><span data-stu-id="6260a-117">If a variable can contain an indefinite number of characters, declare it as `String`.</span></span> <span data-ttu-id="6260a-118">Příklad:</span><span class="sxs-lookup"><span data-stu-id="6260a-118">For example:</span></span>  
  
 [!code-vb[VbVbalrCharTypes#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrchartypes/vb/module1.vb#2)]
  
 <span data-ttu-id="6260a-119">Další informace najdete v tématu [datový typ String](../../../../visual-basic/language-reference/data-types/string-data-type.md).</span><span class="sxs-lookup"><span data-stu-id="6260a-119">For more information, see [String Data Type](../../../../visual-basic/language-reference/data-types/string-data-type.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6260a-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="6260a-120">See Also</span></span>  
 [<span data-ttu-id="6260a-121">Základní datové typy</span><span class="sxs-lookup"><span data-stu-id="6260a-121">Elementary Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)  
 [<span data-ttu-id="6260a-122">Složené datové typy</span><span class="sxs-lookup"><span data-stu-id="6260a-122">Composite Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)  
 [<span data-ttu-id="6260a-123">Obecné typy v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="6260a-123">Generic Types in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [<span data-ttu-id="6260a-124">Typy hodnot a odkazové typy</span><span class="sxs-lookup"><span data-stu-id="6260a-124">Value Types and Reference Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)  
 [<span data-ttu-id="6260a-125">Převody typů v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="6260a-125">Type Conversions in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)  
 [<span data-ttu-id="6260a-126">Řešení potíží s datovými typy</span><span class="sxs-lookup"><span data-stu-id="6260a-126">Troubleshooting Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 [<span data-ttu-id="6260a-127">Znaky typu</span><span class="sxs-lookup"><span data-stu-id="6260a-127">Type Characters</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)
