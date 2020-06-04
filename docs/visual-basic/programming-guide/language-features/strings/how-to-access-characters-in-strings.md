---
title: 'Postupy: Přístup ke znakům v řetězcích'
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], accessing characters
- characters [Visual Basic], accessing in strings
ms.assetid: 02c5206c-ffab-494d-b648-3b2ea358dc34
ms.openlocfilehash: fa5920cfd25f61f6e6c7d5438ef7c0e38a48fa1e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401950"
---
# <a name="how-to-access-characters-in-strings-in-visual-basic"></a><span data-ttu-id="3b3dd-102">Postupy: Přístup ke znakům v řetězcích v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="3b3dd-102">How to: Access Characters in Strings in Visual Basic</span></span>
<span data-ttu-id="3b3dd-103">Tento příklad ukazuje, jak použít <xref:System.String.Chars%2A> vlastnost pro přístup k znaku v zadaném umístění v řetězci.</span><span class="sxs-lookup"><span data-stu-id="3b3dd-103">This example demonstrates how to use the <xref:System.String.Chars%2A> property to access the character at the specified location in a string.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3b3dd-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="3b3dd-104">Example</span></span>  
 <span data-ttu-id="3b3dd-105">Někdy je užitečné mít data o znacích v řetězci a umístění těchto znaků v rámci řetězce.</span><span class="sxs-lookup"><span data-stu-id="3b3dd-105">Sometimes it is useful to have data about the characters in your string and the positions of those characters within your string.</span></span> <span data-ttu-id="3b3dd-106">Řetězec můžete představit jako pole znaků ( `Char` instance); můžete načíst konkrétní znak odkazem na index daného znaku prostřednictvím <xref:System.String.Chars%2A> Vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="3b3dd-106">You can think of a string as an array of characters (`Char` instances); you can retrieve a particular character by referencing the index of that character through the <xref:System.String.Chars%2A> property.</span></span>  
  
 [!code-vb[VbVbalrStrings#49](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#49)]  
  
 <span data-ttu-id="3b3dd-107">`index`Parametr <xref:System.String.Chars%2A> vlastnosti je založený na nule.</span><span class="sxs-lookup"><span data-stu-id="3b3dd-107">The `index` parameter of the <xref:System.String.Chars%2A> property is zero-based.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="3b3dd-108">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="3b3dd-108">Robust Programming</span></span>  
 <span data-ttu-id="3b3dd-109"><xref:System.String.Chars%2A>Vlastnost vrátí znak na zadané pozici.</span><span class="sxs-lookup"><span data-stu-id="3b3dd-109">The <xref:System.String.Chars%2A> property returns the character at the specified position.</span></span> <span data-ttu-id="3b3dd-110">Některé znaky Unicode však mohou být reprezentovány více než jedním znakem.</span><span class="sxs-lookup"><span data-stu-id="3b3dd-110">However, some Unicode characters can be represented by more than one character.</span></span> <span data-ttu-id="3b3dd-111">Další informace o tom, jak pracovat se znaky kódování Unicode, naleznete v tématu [How to: Convert String to Array of Characters](how-to-convert-a-string-to-an-array-of-characters.md).</span><span class="sxs-lookup"><span data-stu-id="3b3dd-111">For more information on how to work with Unicode characters, see [How to: Convert a String to an Array of Characters](how-to-convert-a-string-to-an-array-of-characters.md).</span></span>  
  
 <span data-ttu-id="3b3dd-112"><xref:System.String.Chars%2A>Vlastnost vyvolá <xref:System.IndexOutOfRangeException> výjimku `index` , pokud je parametr větší nebo roven délce řetězce, nebo pokud je menší než nula.</span><span class="sxs-lookup"><span data-stu-id="3b3dd-112">The <xref:System.String.Chars%2A> property throws an <xref:System.IndexOutOfRangeException> exception if the `index` parameter is greater than or equal to the length of the string, or if it is less than zero</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b3dd-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="3b3dd-113">See also</span></span>

- <xref:System.String.Chars%2A>
- [<span data-ttu-id="3b3dd-114">Postupy: Převod řetězce na pole znaků</span><span class="sxs-lookup"><span data-stu-id="3b3dd-114">How to: Convert a String to an Array of Characters</span></span>](how-to-convert-a-string-to-an-array-of-characters.md)
- [<span data-ttu-id="3b3dd-115">Převod mezi řetězci a ostatními datovými typy v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="3b3dd-115">Converting Between Strings and Other Data Types in Visual Basic</span></span>](converting-between-strings-and-other-data-types.md)
- [<span data-ttu-id="3b3dd-116">Řetězce</span><span class="sxs-lookup"><span data-stu-id="3b3dd-116">Strings</span></span>](index.md)
