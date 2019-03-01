---
title: 'Postupy: Převod řetězce na pole bajtů v jazyce Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- string conversion [Visual Basic], arrays
- arrays [Visual Basic], converting strings to
- byte arrays
- examples [Visual Basic], string conversion
- arrays [Visual Basic], byte arrays
ms.assetid: f477d35c-a3fc-4a30-b1d4-cd0d353aae1d
ms.openlocfilehash: a96664f308a711d440f063627665283c5b7fc264
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56967500"
---
# <a name="how-to-convert-strings-into-an-array-of-bytes-in-visual-basic"></a><span data-ttu-id="833ef-102">Postupy: Převod řetězce na pole bajtů v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="833ef-102">How to: Convert Strings into an Array of Bytes in Visual Basic</span></span>
<span data-ttu-id="833ef-103">Toto téma ukazuje, jak převést pole bajtů na řetězec.</span><span class="sxs-lookup"><span data-stu-id="833ef-103">This topic shows how to convert a string into an array of bytes.</span></span>  
  
## <a name="example"></a><span data-ttu-id="833ef-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="833ef-104">Example</span></span>  
 <span data-ttu-id="833ef-105">V tomto příkladu <xref:System.Text.Encoding.GetBytes%2A> metodu <xref:System.Text.Encoding.Unicode%2A?displayProperty=nameWithType> kódování třídy pro převod řetězce na pole bajtů.</span><span class="sxs-lookup"><span data-stu-id="833ef-105">This example uses the <xref:System.Text.Encoding.GetBytes%2A> method of the <xref:System.Text.Encoding.Unicode%2A?displayProperty=nameWithType> encoding class to convert a string into an array of bytes.</span></span>  
  
 [!code-vb[VbVbalrStrings#74](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#74)]  
  
 <span data-ttu-id="833ef-106">Můžete použít jednu z několika možností kódování převést řetězec na bajtové pole:</span><span class="sxs-lookup"><span data-stu-id="833ef-106">You can choose from several encoding options to convert a string into a byte array:</span></span>  
  
-   <span data-ttu-id="833ef-107"><xref:System.Text.Encoding.ASCII%2A?displayProperty=nameWithType>: Získá kódování (7-bit) znakové sady ASCII.</span><span class="sxs-lookup"><span data-stu-id="833ef-107"><xref:System.Text.Encoding.ASCII%2A?displayProperty=nameWithType>: Gets an encoding for the ASCII (7-bit) character set.</span></span>  
  
-   <span data-ttu-id="833ef-108"><xref:System.Text.Encoding.BigEndianUnicode%2A?displayProperty=nameWithType>: Získá kódování ve formátu UTF-16 s využitím pořadí bajtů ve formátu big endian.</span><span class="sxs-lookup"><span data-stu-id="833ef-108"><xref:System.Text.Encoding.BigEndianUnicode%2A?displayProperty=nameWithType>: Gets an encoding for the UTF-16 format using the big-endian byte order.</span></span>  
  
-   <span data-ttu-id="833ef-109"><xref:System.Text.Encoding.Default%2A?displayProperty=nameWithType>: Získá kódování systému aktuální znakovou stránku ANSI.</span><span class="sxs-lookup"><span data-stu-id="833ef-109"><xref:System.Text.Encoding.Default%2A?displayProperty=nameWithType>: Gets an encoding for the system's current ANSI code page.</span></span>  
  
-   <span data-ttu-id="833ef-110"><xref:System.Text.Encoding.Unicode%2A?displayProperty=nameWithType>: Získá kódování ve formátu UTF-16 s využitím pořadí bajtů ve formátu little endian.</span><span class="sxs-lookup"><span data-stu-id="833ef-110"><xref:System.Text.Encoding.Unicode%2A?displayProperty=nameWithType>: Gets an encoding for the UTF-16 format using the little-endian byte order.</span></span>  
  
-   <span data-ttu-id="833ef-111"><xref:System.Text.Encoding.UTF32%2A?displayProperty=nameWithType>: Získá kódování ve formátu UTF-32 s využitím pořadí bajtů ve formátu little endian.</span><span class="sxs-lookup"><span data-stu-id="833ef-111"><xref:System.Text.Encoding.UTF32%2A?displayProperty=nameWithType>: Gets an encoding for the UTF-32 format using the little-endian byte order.</span></span>  
  
-   <span data-ttu-id="833ef-112"><xref:System.Text.Encoding.UTF7%2A?displayProperty=nameWithType>: Získá kódování UTF-7 formátu.</span><span class="sxs-lookup"><span data-stu-id="833ef-112"><xref:System.Text.Encoding.UTF7%2A?displayProperty=nameWithType>: Gets an encoding for the UTF-7 format.</span></span>  
  
-   <span data-ttu-id="833ef-113"><xref:System.Text.Encoding.UTF8%2A?displayProperty=nameWithType>: Získá kódování pro formát UTF-8.</span><span class="sxs-lookup"><span data-stu-id="833ef-113"><xref:System.Text.Encoding.UTF8%2A?displayProperty=nameWithType>: Gets an encoding for the UTF-8 format.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="833ef-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="833ef-114">See also</span></span>
- <xref:System.Text.Encoding?displayProperty=nameWithType>
- <xref:System.Text.Encoding.GetBytes%2A>
- [<span data-ttu-id="833ef-115">Postupy: Převod pole bajtů na řetězec v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="833ef-115">How to: Convert an Array of Bytes into a String in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/strings/how-to-convert-an-array-of-bytes-into-a-string.md)
