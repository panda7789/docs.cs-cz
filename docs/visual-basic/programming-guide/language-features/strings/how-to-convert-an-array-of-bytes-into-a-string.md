---
title: 'Postupy: Převod pole bajtů na řetězec v jazyce Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- string conversion [Visual Basic], arrays
- byte arrays [Visual Basic], converting to strings
- examples [Visual Basic], strings
- arrays [Visual Basic], converting to strings
ms.assetid: d0dc8317-9ab3-4324-99f7-3f5788c0e72a
ms.openlocfilehash: f0676548bea2d4037f66fb15498c175b2d110d8b
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58826729"
---
# <a name="how-to-convert-an-array-of-bytes-into-a-string-in-visual-basic"></a><span data-ttu-id="a9ade-102">Postupy: Převod pole bajtů na řetězec v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a9ade-102">How to: Convert an Array of Bytes into a String in Visual Basic</span></span>
<span data-ttu-id="a9ade-103">Toto téma ukazuje, jak převést bajty z pole bajtů na řetězec.</span><span class="sxs-lookup"><span data-stu-id="a9ade-103">This topic shows how to convert the bytes from a byte array into a string.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a9ade-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="a9ade-104">Example</span></span>  
 <span data-ttu-id="a9ade-105">V tomto příkladu <xref:System.Text.Encoding.GetString%2A> metodu <xref:System.Text.Encoding.Unicode%2A?displayProperty=nameWithType> kódování pro převod všech bajtů z bajtového pole do řetězce.</span><span class="sxs-lookup"><span data-stu-id="a9ade-105">This example uses the <xref:System.Text.Encoding.GetString%2A> method of the <xref:System.Text.Encoding.Unicode%2A?displayProperty=nameWithType> encoding class to convert all the bytes from a byte array into a string.</span></span>  
  
 [!code-vb[VbVbalrStrings#72](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#72)]  
  
 <span data-ttu-id="a9ade-106">Můžete použít jednu z několika možností kódování převést řetězec na bajtové pole:</span><span class="sxs-lookup"><span data-stu-id="a9ade-106">You can choose from several encoding options to convert a byte array into a string:</span></span>  
  
-   <span data-ttu-id="a9ade-107"><xref:System.Text.Encoding.ASCII%2A?displayProperty=nameWithType>: Získá kódování (7-bit) znakové sady ASCII.</span><span class="sxs-lookup"><span data-stu-id="a9ade-107"><xref:System.Text.Encoding.ASCII%2A?displayProperty=nameWithType>: Gets an encoding for the ASCII (7-bit) character set.</span></span>  
  
-   <span data-ttu-id="a9ade-108"><xref:System.Text.Encoding.BigEndianUnicode%2A?displayProperty=nameWithType>: Získá kódování ve formátu UTF-16 s využitím pořadí bajtů ve formátu big endian.</span><span class="sxs-lookup"><span data-stu-id="a9ade-108"><xref:System.Text.Encoding.BigEndianUnicode%2A?displayProperty=nameWithType>: Gets an encoding for the UTF-16 format using the big-endian byte order.</span></span>  
  
-   <span data-ttu-id="a9ade-109"><xref:System.Text.Encoding.Default%2A?displayProperty=nameWithType>: Získá kódování systému aktuální znakovou stránku ANSI.</span><span class="sxs-lookup"><span data-stu-id="a9ade-109"><xref:System.Text.Encoding.Default%2A?displayProperty=nameWithType>: Gets an encoding for the system's current ANSI code page.</span></span>  
  
-   <span data-ttu-id="a9ade-110"><xref:System.Text.Encoding.Unicode%2A?displayProperty=nameWithType>: Získá kódování ve formátu UTF-16 s využitím pořadí bajtů ve formátu little endian.</span><span class="sxs-lookup"><span data-stu-id="a9ade-110"><xref:System.Text.Encoding.Unicode%2A?displayProperty=nameWithType>: Gets an encoding for the UTF-16 format using the little-endian byte order.</span></span>  
  
-   <span data-ttu-id="a9ade-111"><xref:System.Text.Encoding.UTF32%2A?displayProperty=nameWithType>: Získá kódování ve formátu UTF-32 s využitím pořadí bajtů ve formátu little endian.</span><span class="sxs-lookup"><span data-stu-id="a9ade-111"><xref:System.Text.Encoding.UTF32%2A?displayProperty=nameWithType>: Gets an encoding for the UTF-32 format using the little-endian byte order.</span></span>  
  
-   <span data-ttu-id="a9ade-112"><xref:System.Text.Encoding.UTF7%2A?displayProperty=nameWithType>: Získá kódování UTF-7 formátu.</span><span class="sxs-lookup"><span data-stu-id="a9ade-112"><xref:System.Text.Encoding.UTF7%2A?displayProperty=nameWithType>: Gets an encoding for the UTF-7 format.</span></span>  
  
-   <span data-ttu-id="a9ade-113"><xref:System.Text.Encoding.UTF8%2A?displayProperty=nameWithType>: Získá kódování pro formát UTF-8.</span><span class="sxs-lookup"><span data-stu-id="a9ade-113"><xref:System.Text.Encoding.UTF8%2A?displayProperty=nameWithType>: Gets an encoding for the UTF-8 format.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9ade-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a9ade-114">See also</span></span>

- <xref:System.Text.Encoding?displayProperty=nameWithType>
- <xref:System.Text.Encoding.GetString%2A>
- [<span data-ttu-id="a9ade-115">Postupy: Převod řetězce na pole bajtů v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a9ade-115">How to: Convert Strings into an Array of Bytes in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/strings/how-to-convert-strings-into-an-array-of-bytes.md)
