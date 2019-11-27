---
title: Datové typy znaků
ms.date: 07/20/2015
helpviewer_keywords:
- data types [Visual Basic], character
- String data type [Visual Basic], character data types
- character data types [Visual Basic]
- Char data type [Visual Basic], character data types
- data types [Visual Basic], choosing
ms.assetid: 902479ef-1679-47fc-9911-0c1c5008226c
ms.openlocfilehash: edd1d3a41dd878649aa422256b7858d7bce366e1
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346385"
---
# <a name="character-data-types-visual-basic"></a><span data-ttu-id="6f9d6-102">Datové typy znaků (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6f9d6-102">Character Data Types (Visual Basic)</span></span>
<span data-ttu-id="6f9d6-103">Visual Basic poskytuje *znakové datové typy* pro práci s tisknutelnými a zobrazitelnými znaky.</span><span class="sxs-lookup"><span data-stu-id="6f9d6-103">Visual Basic provides *character data types* to deal with printable and displayable characters.</span></span> <span data-ttu-id="6f9d6-104">I když se zaměří se znaky Unicode, `Char` obsahovat jeden znak, zatímco `String` obsahuje neomezený počet znaků.</span><span class="sxs-lookup"><span data-stu-id="6f9d6-104">While they both deal with Unicode characters, `Char` holds a single character whereas `String` contains an indefinite number of characters.</span></span>  
  
 <span data-ttu-id="6f9d6-105">Tabulku, která zobrazuje souběžné porovnání Visual Basicch datových typů, najdete v tématu [datové typy](../../../../visual-basic/language-reference/data-types/index.md).</span><span class="sxs-lookup"><span data-stu-id="6f9d6-105">For a table that displays a side-by-side comparison of the Visual Basic data types, see [Data Types](../../../../visual-basic/language-reference/data-types/index.md).</span></span>  
  
## <a name="char-type"></a><span data-ttu-id="6f9d6-106">Typ znaku</span><span class="sxs-lookup"><span data-stu-id="6f9d6-106">Char Type</span></span>  
 <span data-ttu-id="6f9d6-107">Datový typ `Char` je jeden dvoubajtový (16bitový) znak Unicode.</span><span class="sxs-lookup"><span data-stu-id="6f9d6-107">The `Char` data type is a single two-byte (16-bit) Unicode character.</span></span> <span data-ttu-id="6f9d6-108">Pokud proměnná vždy ukládá přesně jeden znak, deklarujte ho jako `Char`.</span><span class="sxs-lookup"><span data-stu-id="6f9d6-108">If a variable always stores exactly one character, declare it as `Char`.</span></span> <span data-ttu-id="6f9d6-109">Příklad:</span><span class="sxs-lookup"><span data-stu-id="6f9d6-109">For example:</span></span>  
  
 [!code-vb[VbVbalrCharTypes#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrchartypes/vb/module1.vb#1)]
  
 <span data-ttu-id="6f9d6-110">Každá možná hodnota v `Char` nebo v proměnné `String` je *bod kódu*nebo kód znaku v sadě znaků Unicode.</span><span class="sxs-lookup"><span data-stu-id="6f9d6-110">Each possible value in a `Char` or `String` variable is a *code point*, or character code, in the Unicode character set.</span></span> <span data-ttu-id="6f9d6-111">Mezi znaky Unicode patří základní znaková sada ASCII, různá další písmena abecedy, zvýraznění, symboly měn, zlomky, diakritická znaménka a matematické a technické symboly.</span><span class="sxs-lookup"><span data-stu-id="6f9d6-111">Unicode characters include the basic ASCII character set, various other alphabet letters, accents, currency symbols, fractions, diacritics, and mathematical and technical symbols.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6f9d6-112">Znaková sada Unicode rezervuje body kódu D800 prostřednictvím DFFF (55296 až 55551 desítk) pro *náhradní páry*, které vyžadují, aby hodnoty 2 16-bit představovaly jediný bod kódu.</span><span class="sxs-lookup"><span data-stu-id="6f9d6-112">The Unicode character set reserves the code points D800 through DFFF (55296 through 55551 decimal) for *surrogate pairs*, which require two 16-bit values to represent a single code point.</span></span> <span data-ttu-id="6f9d6-113">Proměnná `Char` nemůže obsahovat náhradní pár a `String` používá dvě pozice k uchování takového páru.</span><span class="sxs-lookup"><span data-stu-id="6f9d6-113">A `Char` variable cannot hold a surrogate pair, and a `String` uses two positions to hold such a pair.</span></span>  
  
 <span data-ttu-id="6f9d6-114">Další informace naleznete v tématu [char data Type](../../../../visual-basic/language-reference/data-types/char-data-type.md).</span><span class="sxs-lookup"><span data-stu-id="6f9d6-114">For more information, see [Char Data Type](../../../../visual-basic/language-reference/data-types/char-data-type.md).</span></span>  
  
## <a name="string-type"></a><span data-ttu-id="6f9d6-115">Typ řetězce</span><span class="sxs-lookup"><span data-stu-id="6f9d6-115">String Type</span></span>  
 <span data-ttu-id="6f9d6-116">Datový typ `String` je sekvence nula nebo více dvoubajtových (16 bitů) znaků Unicode.</span><span class="sxs-lookup"><span data-stu-id="6f9d6-116">The `String` data type is a sequence of zero or more two-byte (16-bit) Unicode characters.</span></span> <span data-ttu-id="6f9d6-117">Pokud proměnná může obsahovat nekonečný počet znaků, deklarujte ji jako `String`.</span><span class="sxs-lookup"><span data-stu-id="6f9d6-117">If a variable can contain an indefinite number of characters, declare it as `String`.</span></span> <span data-ttu-id="6f9d6-118">Příklad:</span><span class="sxs-lookup"><span data-stu-id="6f9d6-118">For example:</span></span>  
  
 [!code-vb[VbVbalrCharTypes#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrchartypes/vb/module1.vb#2)]
  
 <span data-ttu-id="6f9d6-119">Další informace najdete v tématu [datový typ String](../../../../visual-basic/language-reference/data-types/string-data-type.md).</span><span class="sxs-lookup"><span data-stu-id="6f9d6-119">For more information, see [String Data Type](../../../../visual-basic/language-reference/data-types/string-data-type.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f9d6-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6f9d6-120">See also</span></span>

- [<span data-ttu-id="6f9d6-121">Základní datové typy</span><span class="sxs-lookup"><span data-stu-id="6f9d6-121">Elementary Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)
- [<span data-ttu-id="6f9d6-122">Složené datové typy</span><span class="sxs-lookup"><span data-stu-id="6f9d6-122">Composite Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)
- [<span data-ttu-id="6f9d6-123">Obecné typy v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="6f9d6-123">Generic Types in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [<span data-ttu-id="6f9d6-124">Typy hodnot a odkazové typy</span><span class="sxs-lookup"><span data-stu-id="6f9d6-124">Value Types and Reference Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
- [<span data-ttu-id="6f9d6-125">Převody typu v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="6f9d6-125">Type Conversions in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [<span data-ttu-id="6f9d6-126">Řešení potíží s datovými typy</span><span class="sxs-lookup"><span data-stu-id="6f9d6-126">Troubleshooting Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [<span data-ttu-id="6f9d6-127">Znaky typu</span><span class="sxs-lookup"><span data-stu-id="6f9d6-127">Type Characters</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)
