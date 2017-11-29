---
title: "Postupy: Přístup ke znakům v řetězcích v jazyce Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- strings [Visual Basic], accessing characters
- characters [Visual Basic], accessing in strings
ms.assetid: 02c5206c-ffab-494d-b648-3b2ea358dc34
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 54d604fc08dd97e0e31f9bcec148431374e8ef8f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-access-characters-in-strings-in-visual-basic"></a><span data-ttu-id="d79fe-102">Postupy: Přístup ke znakům v řetězcích v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d79fe-102">How to: Access Characters in Strings in Visual Basic</span></span>
<span data-ttu-id="d79fe-103">Tento příklad ukazuje, jak používat <xref:System.String.Chars%2A> vlastnost, která má přístup ke znakům v zadaném umístění v řetězci.</span><span class="sxs-lookup"><span data-stu-id="d79fe-103">This example demonstrates how to use the <xref:System.String.Chars%2A> property to access the character at the specified location in a string.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d79fe-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="d79fe-104">Example</span></span>  
 <span data-ttu-id="d79fe-105">Někdy je užitečné používat data o znaky v řetězec vašeho a pozice z těchto znaků v rámci vaší řetězec.</span><span class="sxs-lookup"><span data-stu-id="d79fe-105">Sometimes it is useful to have data about the characters in your string and the positions of those characters within your string.</span></span> <span data-ttu-id="d79fe-106">Řetězce si můžete představit jako pole znaků (`Char` instance); určitý znak můžete načíst odkazem index tento znak prostřednictvím <xref:System.String.Chars%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="d79fe-106">You can think of a string as an array of characters (`Char` instances); you can retrieve a particular character by referencing the index of that character through the <xref:System.String.Chars%2A> property.</span></span>  
  
 [!code-vb[VbVbalrStrings#49](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-access-characters-in-strings_1.vb)]  
  
 <span data-ttu-id="d79fe-107">`index` Parametr <xref:System.String.Chars%2A> vlastnost je počítáno od nuly.</span><span class="sxs-lookup"><span data-stu-id="d79fe-107">The `index` parameter of the <xref:System.String.Chars%2A> property is zero-based.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="d79fe-108">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="d79fe-108">Robust Programming</span></span>  
 <span data-ttu-id="d79fe-109"><xref:System.String.Chars%2A> Vlastnost vrátí znak na zadané pozici.</span><span class="sxs-lookup"><span data-stu-id="d79fe-109">The <xref:System.String.Chars%2A> property returns the character at the specified position.</span></span> <span data-ttu-id="d79fe-110">Některé znaky kódování Unicode však může být reprezentovaný více než jeden znak.</span><span class="sxs-lookup"><span data-stu-id="d79fe-110">However, some Unicode characters can be represented by more than one character.</span></span> <span data-ttu-id="d79fe-111">Další informace o tom, jak pracovat s znaky znakové sady Unicode, najdete v části [postupy: převedení řetězce na pole znaků](../../../../visual-basic/programming-guide/language-features/strings/how-to-convert-a-string-to-an-array-of-characters.md).</span><span class="sxs-lookup"><span data-stu-id="d79fe-111">For more information on how to work with Unicode characters, see [How to: Convert a String to an Array of Characters](../../../../visual-basic/programming-guide/language-features/strings/how-to-convert-a-string-to-an-array-of-characters.md).</span></span>  
  
 <span data-ttu-id="d79fe-112"><xref:System.String.Chars%2A> Vlastnost vyvolává <xref:System.IndexOutOfRangeException> výjimka pokud `index` parametr je větší než nebo rovna hodnotě délky řetězce, nebo pokud ji je menší než nula</span><span class="sxs-lookup"><span data-stu-id="d79fe-112">The <xref:System.String.Chars%2A> property throws an <xref:System.IndexOutOfRangeException> exception if the `index` parameter is greater than or equal to the length of the string, or if it is less than zero</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d79fe-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="d79fe-113">See Also</span></span>  
 <xref:System.String.Chars%2A>  
 [<span data-ttu-id="d79fe-114">Postupy: převedení řetězce na pole znaků</span><span class="sxs-lookup"><span data-stu-id="d79fe-114">How to: Convert a String to an Array of Characters</span></span>](../../../../visual-basic/programming-guide/language-features/strings/how-to-convert-a-string-to-an-array-of-characters.md)  
 [<span data-ttu-id="d79fe-115">Převod mezi řetězci a ostatními typy dat v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d79fe-115">Converting Between Strings and Other Data Types in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/strings/converting-between-strings-and-other-data-types.md)  
 [<span data-ttu-id="d79fe-116">Řetězce</span><span class="sxs-lookup"><span data-stu-id="d79fe-116">Strings</span></span>](../../../../visual-basic/programming-guide/language-features/strings/index.md)
