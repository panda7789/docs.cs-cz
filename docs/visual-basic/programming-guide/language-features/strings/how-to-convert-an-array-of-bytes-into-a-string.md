---
title: 'Postupy: Převod pole bajtů na řetězec'
ms.date: 07/20/2015
helpviewer_keywords:
- string conversion [Visual Basic], arrays
- byte arrays [Visual Basic], converting to strings
- examples [Visual Basic], strings
- arrays [Visual Basic], converting to strings
ms.assetid: d0dc8317-9ab3-4324-99f7-3f5788c0e72a
ms.openlocfilehash: 6dbbaafedeca4d2cea625a300d764f61bb575750
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410616"
---
# <a name="how-to-convert-an-array-of-bytes-into-a-string-in-visual-basic"></a><span data-ttu-id="6bd0d-102">Postupy: Převod pole bajtů na řetězec v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="6bd0d-102">How to: Convert an Array of Bytes into a String in Visual Basic</span></span>
<span data-ttu-id="6bd0d-103">Toto téma ukazuje, jak převést bajty z bajtového pole na řetězec.</span><span class="sxs-lookup"><span data-stu-id="6bd0d-103">This topic shows how to convert the bytes from a byte array into a string.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6bd0d-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="6bd0d-104">Example</span></span>  
 <span data-ttu-id="6bd0d-105">Tento příklad používá <xref:System.Text.Encoding.GetString%2A> metodu <xref:System.Text.Encoding.Unicode%2A?displayProperty=nameWithType> třídy Encoding k převodu všech bajtů z pole bajtů do řetězce.</span><span class="sxs-lookup"><span data-stu-id="6bd0d-105">This example uses the <xref:System.Text.Encoding.GetString%2A> method of the <xref:System.Text.Encoding.Unicode%2A?displayProperty=nameWithType> encoding class to convert all the bytes from a byte array into a string.</span></span>  
  
 [!code-vb[VbVbalrStrings#72](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#72)]  
  
 <span data-ttu-id="6bd0d-106">Můžete vybrat z několika možností kódování pro převod pole bajtů na řetězec:</span><span class="sxs-lookup"><span data-stu-id="6bd0d-106">You can choose from several encoding options to convert a byte array into a string:</span></span>  
  
- <span data-ttu-id="6bd0d-107"><xref:System.Text.Encoding.ASCII%2A?displayProperty=nameWithType>: Získá kódování znakové sady ASCII (7 bitů).</span><span class="sxs-lookup"><span data-stu-id="6bd0d-107"><xref:System.Text.Encoding.ASCII%2A?displayProperty=nameWithType>: Gets an encoding for the ASCII (7-bit) character set.</span></span>  
  
- <span data-ttu-id="6bd0d-108"><xref:System.Text.Encoding.BigEndianUnicode%2A?displayProperty=nameWithType>: Získá kódování formátu UTF-16 pomocí pořadí bajtů big-endian.</span><span class="sxs-lookup"><span data-stu-id="6bd0d-108"><xref:System.Text.Encoding.BigEndianUnicode%2A?displayProperty=nameWithType>: Gets an encoding for the UTF-16 format using the big-endian byte order.</span></span>  
  
- <span data-ttu-id="6bd0d-109"><xref:System.Text.Encoding.Default%2A?displayProperty=nameWithType>: Získá kódování pro aktuální znakovou stránku ANSI systému.</span><span class="sxs-lookup"><span data-stu-id="6bd0d-109"><xref:System.Text.Encoding.Default%2A?displayProperty=nameWithType>: Gets an encoding for the system's current ANSI code page.</span></span>  
  
- <span data-ttu-id="6bd0d-110"><xref:System.Text.Encoding.Unicode%2A?displayProperty=nameWithType>: Získá kódování pro formát UTF-16 pomocí pořadí bajtů ve formátu Little endian.</span><span class="sxs-lookup"><span data-stu-id="6bd0d-110"><xref:System.Text.Encoding.Unicode%2A?displayProperty=nameWithType>: Gets an encoding for the UTF-16 format using the little-endian byte order.</span></span>  
  
- <span data-ttu-id="6bd0d-111"><xref:System.Text.Encoding.UTF32%2A?displayProperty=nameWithType>: Získá kódování formátu UTF-32 pomocí pořadí bajtů ve formátu Little endian.</span><span class="sxs-lookup"><span data-stu-id="6bd0d-111"><xref:System.Text.Encoding.UTF32%2A?displayProperty=nameWithType>: Gets an encoding for the UTF-32 format using the little-endian byte order.</span></span>  
  
- <span data-ttu-id="6bd0d-112"><xref:System.Text.Encoding.UTF7%2A?displayProperty=nameWithType>: Získá kódování pro formát UTF-7.</span><span class="sxs-lookup"><span data-stu-id="6bd0d-112"><xref:System.Text.Encoding.UTF7%2A?displayProperty=nameWithType>: Gets an encoding for the UTF-7 format.</span></span>  
  
- <span data-ttu-id="6bd0d-113"><xref:System.Text.Encoding.UTF8%2A?displayProperty=nameWithType>: Získá kódování pro formát UTF-8.</span><span class="sxs-lookup"><span data-stu-id="6bd0d-113"><xref:System.Text.Encoding.UTF8%2A?displayProperty=nameWithType>: Gets an encoding for the UTF-8 format.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6bd0d-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="6bd0d-114">See also</span></span>

- <xref:System.Text.Encoding?displayProperty=nameWithType>
- <xref:System.Text.Encoding.GetString%2A>
- [<span data-ttu-id="6bd0d-115">Postupy: Převod řetězců na pole bajtů v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="6bd0d-115">How to: Convert Strings into an Array of Bytes in Visual Basic</span></span>](how-to-convert-strings-into-an-array-of-bytes.md)
