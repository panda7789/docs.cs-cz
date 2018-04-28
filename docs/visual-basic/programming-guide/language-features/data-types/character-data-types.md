---
title: Datové typy znaků (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- data types [Visual Basic], character
- String data type [Visual Basic], character data types
- character data types [Visual Basic]
- Char data type [Visual Basic], character data types
- data types [Visual Basic], choosing
ms.assetid: 902479ef-1679-47fc-9911-0c1c5008226c
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: afd368c00444f136c6d69b02a733c82f0c8eafe0
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2018
---
# <a name="character-data-types-visual-basic"></a><span data-ttu-id="2ed57-102">Datové typy znaků (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2ed57-102">Character Data Types (Visual Basic)</span></span>
<span data-ttu-id="2ed57-103">Visual Basic poskytuje *znak datové typy* jak nakládat s tiskových a zobrazitelné znaků.</span><span class="sxs-lookup"><span data-stu-id="2ed57-103">Visual Basic provides *character data types* to deal with printable and displayable characters.</span></span> <span data-ttu-id="2ed57-104">Při obě řešit znaky znakové sady Unicode, `Char` obsahují jeden znak, zatímco `String` obsahuje nekonečný počet znaků.</span><span class="sxs-lookup"><span data-stu-id="2ed57-104">While they both deal with Unicode characters, `Char` holds a single character whereas `String` contains an indefinite number of characters.</span></span>  
  
 <span data-ttu-id="2ed57-105">Tabulka, která zobrazuje porovnání vedle sebe Visual Basic – datové typy, najdete v části [datové typy](../../../../visual-basic/language-reference/data-types/data-type-summary.md).</span><span class="sxs-lookup"><span data-stu-id="2ed57-105">For a table that displays a side-by-side comparison of the Visual Basic data types, see [Data Types](../../../../visual-basic/language-reference/data-types/data-type-summary.md).</span></span>  
  
## <a name="char-type"></a><span data-ttu-id="2ed57-106">Znakový typ</span><span class="sxs-lookup"><span data-stu-id="2ed57-106">Char Type</span></span>  
 <span data-ttu-id="2ed57-107">`Char` Datový typ je jeden znak Unicode (16 bitů) dva bajtů.</span><span class="sxs-lookup"><span data-stu-id="2ed57-107">The `Char` data type is a single two-byte (16-bit) Unicode character.</span></span> <span data-ttu-id="2ed57-108">Pokud proměnnou vždy obsahuje přesně jeden znak, deklarujte ji jako `Char`.</span><span class="sxs-lookup"><span data-stu-id="2ed57-108">If a variable always stores exactly one character, declare it as `Char`.</span></span> <span data-ttu-id="2ed57-109">Příklad:</span><span class="sxs-lookup"><span data-stu-id="2ed57-109">For example:</span></span>  
  
 [!code-vb[VbVbalrCharTypes#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrchartypes/vb/module1.vb#1)]
  
 <span data-ttu-id="2ed57-110">Každý možné hodnoty ve `Char` nebo `String` proměnná *code bodu*, nebo kód znaku ve znakové sadě Unicode.</span><span class="sxs-lookup"><span data-stu-id="2ed57-110">Each possible value in a `Char` or `String` variable is a *code point*, or character code, in the Unicode character set.</span></span> <span data-ttu-id="2ed57-111">Znaky znakové sady Unicode obsahovat základní znakové sadě ASCII, různé další písmena abecedy, akcenty, tyto symboly, zlomků, znaky s diakritikou a matematické a technické symboly.</span><span class="sxs-lookup"><span data-stu-id="2ed57-111">Unicode characters include the basic ASCII character set, various other alphabet letters, accents, currency symbols, fractions, diacritics, and mathematical and technical symbols.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2ed57-112">Znak Unicode nastavení rezervy kód ukazuje D800 prostřednictvím DFFF (55296 prostřednictvím 55551 decimal) pro *náhradního páry*, vyžadující dvě hodnoty 16bitové představuje jeden kód bod.</span><span class="sxs-lookup"><span data-stu-id="2ed57-112">The Unicode character set reserves the code points D800 through DFFF (55296 through 55551 decimal) for *surrogate pairs*, which require two 16-bit values to represent a single code point.</span></span> <span data-ttu-id="2ed57-113">A `Char` proměnné nemůže přidržet pár náhradní a `String` používá dvě místa k uložení těchto pár.</span><span class="sxs-lookup"><span data-stu-id="2ed57-113">A `Char` variable cannot hold a surrogate pair, and a `String` uses two positions to hold such a pair.</span></span>  
  
 <span data-ttu-id="2ed57-114">Další informace najdete v tématu [Char – datový typ](../../../../visual-basic/language-reference/data-types/char-data-type.md).</span><span class="sxs-lookup"><span data-stu-id="2ed57-114">For more information, see [Char Data Type](../../../../visual-basic/language-reference/data-types/char-data-type.md).</span></span>  
  
## <a name="string-type"></a><span data-ttu-id="2ed57-115">String – typ</span><span class="sxs-lookup"><span data-stu-id="2ed57-115">String Type</span></span>  
 <span data-ttu-id="2ed57-116">`String` Datový typ je posloupnost nula nebo více znaků Unicode (16 bitů) dva bajtů.</span><span class="sxs-lookup"><span data-stu-id="2ed57-116">The `String` data type is a sequence of zero or more two-byte (16-bit) Unicode characters.</span></span> <span data-ttu-id="2ed57-117">Pokud proměnná může obsahovat nekonečný počet znaků, deklarujte ji jako `String`.</span><span class="sxs-lookup"><span data-stu-id="2ed57-117">If a variable can contain an indefinite number of characters, declare it as `String`.</span></span> <span data-ttu-id="2ed57-118">Příklad:</span><span class="sxs-lookup"><span data-stu-id="2ed57-118">For example:</span></span>  
  
 [!code-vb[VbVbalrCharTypes#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrchartypes/vb/module1.vb#2)]
  
 <span data-ttu-id="2ed57-119">Další informace najdete v tématu [String – datový typ](../../../../visual-basic/language-reference/data-types/string-data-type.md).</span><span class="sxs-lookup"><span data-stu-id="2ed57-119">For more information, see [String Data Type](../../../../visual-basic/language-reference/data-types/string-data-type.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ed57-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="2ed57-120">See Also</span></span>  
 [<span data-ttu-id="2ed57-121">Základní datové typy</span><span class="sxs-lookup"><span data-stu-id="2ed57-121">Elementary Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)  
 [<span data-ttu-id="2ed57-122">Složené datové typy</span><span class="sxs-lookup"><span data-stu-id="2ed57-122">Composite Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)  
 [<span data-ttu-id="2ed57-123">Obecné typy v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="2ed57-123">Generic Types in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [<span data-ttu-id="2ed57-124">Typy hodnot a odkazové typy</span><span class="sxs-lookup"><span data-stu-id="2ed57-124">Value Types and Reference Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)  
 [<span data-ttu-id="2ed57-125">Převody typů v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="2ed57-125">Type Conversions in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)  
 [<span data-ttu-id="2ed57-126">Řešení potíží s datovými typy</span><span class="sxs-lookup"><span data-stu-id="2ed57-126">Troubleshooting Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 [<span data-ttu-id="2ed57-127">Znaky typu</span><span class="sxs-lookup"><span data-stu-id="2ed57-127">Type Characters</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)
