---
title: 'Postupy: vyhledávání v řetězci Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], finding
- strings [Visual Basic], searching
- examples [Visual Basic], strings
ms.assetid: ae4c79e0-08ea-489f-bdb2-5eb6d355f284
ms.openlocfilehash: fe9e50dc5458fdf8546094e5f41c2f001f1d2791
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/01/2019
ms.locfileid: "71700065"
---
# <a name="how-to-search-within-a-string-visual-basic"></a><span data-ttu-id="a9eaf-102">Postupy: vyhledávání v řetězci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a9eaf-102">How to: search within a string (Visual Basic)</span></span>

<span data-ttu-id="a9eaf-103">Tento článek ukazuje příklad, jak hledat v řetězci v Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="a9eaf-103">This article shows an example of how to search within a string in Visual Basic.</span></span>

## <a name="example"></a><span data-ttu-id="a9eaf-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="a9eaf-104">Example</span></span>

<span data-ttu-id="a9eaf-105">Tento příklad volá metodu <xref:System.String.IndexOf%2A> u objektu <xref:System.String>, aby nahlásila index prvního výskytu podřetězce:</span><span class="sxs-lookup"><span data-stu-id="a9eaf-105">This example calls the <xref:System.String.IndexOf%2A> method on a <xref:System.String> object to report the index of the first occurrence of a substring:</span></span>

 [!code-vb[VbVbalrStrings#71](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#71)]

## <a name="robust-programming"></a><span data-ttu-id="a9eaf-106">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="a9eaf-106">Robust programming</span></span>

<span data-ttu-id="a9eaf-107">Metoda <xref:System.String.IndexOf%2A> vrací umístění prvního znaku prvního výskytu podřetězce.</span><span class="sxs-lookup"><span data-stu-id="a9eaf-107">The <xref:System.String.IndexOf%2A> method returns the location of the first character of the first occurrence of the substring.</span></span> <span data-ttu-id="a9eaf-108">Index je založen na 0, což znamená, že první znak řetězce má index 0.</span><span class="sxs-lookup"><span data-stu-id="a9eaf-108">The index is 0-based, which means the first character of a string has an index of 0.</span></span>

<span data-ttu-id="a9eaf-109">Pokud <xref:System.String.IndexOf%2A> nenajde podřetězec, vrátí-1.</span><span class="sxs-lookup"><span data-stu-id="a9eaf-109">If <xref:System.String.IndexOf%2A> does not find the substring, it returns -1.</span></span>

<span data-ttu-id="a9eaf-110">Metoda <xref:System.String.IndexOf%2A> rozlišuje velká a malá písmena a používá aktuální jazykovou verzi.</span><span class="sxs-lookup"><span data-stu-id="a9eaf-110">The <xref:System.String.IndexOf%2A> method is case-sensitive and uses the current culture.</span></span>

<span data-ttu-id="a9eaf-111">Pro zajištění optimálního řízení chyb může být vhodné uzavřít hledání řetězce v bloku `Try` příkazu [Try... Zachytit... Finally](../../../language-reference/statements/try-catch-finally-statement.md) – konstrukce příkazu.</span><span class="sxs-lookup"><span data-stu-id="a9eaf-111">For optimal error control, you might want to enclose the string search in the `Try` block of a [Try...Catch...Finally Statement](../../../language-reference/statements/try-catch-finally-statement.md) construction.</span></span>

## <a name="see-also"></a><span data-ttu-id="a9eaf-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a9eaf-112">See also</span></span>

- <xref:System.String.IndexOf%2A>
- [<span data-ttu-id="a9eaf-113">Příkaz Try...Catch...Finally</span><span class="sxs-lookup"><span data-stu-id="a9eaf-113">Try...Catch...Finally Statement</span></span>](../../../language-reference/statements/try-catch-finally-statement.md)
- [<span data-ttu-id="a9eaf-114">Seznámení s řetězci v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a9eaf-114">Introduction to Strings in Visual Basic</span></span>](introduction-to-strings.md)
- [<span data-ttu-id="a9eaf-115">Řetězce</span><span class="sxs-lookup"><span data-stu-id="a9eaf-115">Strings</span></span>](index.md)
