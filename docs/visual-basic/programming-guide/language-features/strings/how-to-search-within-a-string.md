---
title: 'Postupy: vyhledávání v řetězci'
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], finding
- strings [Visual Basic], searching
- examples [Visual Basic], strings
ms.assetid: ae4c79e0-08ea-489f-bdb2-5eb6d355f284
ms.openlocfilehash: 655f746e4e496e1935afcd2a9f9fe36d9e3a2564
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/25/2019
ms.locfileid: "75348425"
---
# <a name="how-to-search-within-a-string-visual-basic"></a><span data-ttu-id="dbe65-102">Postupy: vyhledávání v řetězci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="dbe65-102">How to: search within a string (Visual Basic)</span></span>

<span data-ttu-id="dbe65-103">Tento článek ukazuje příklad, jak hledat v řetězci v Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="dbe65-103">This article shows an example of how to search within a string in Visual Basic.</span></span>

## <a name="example"></a><span data-ttu-id="dbe65-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="dbe65-104">Example</span></span>

<span data-ttu-id="dbe65-105">V tomto příkladu je volána metoda <xref:System.String.IndexOf%2A> na objektu <xref:System.String>, aby se nahlásil index prvního výskytu podřetězce:</span><span class="sxs-lookup"><span data-stu-id="dbe65-105">This example calls the <xref:System.String.IndexOf%2A> method on a <xref:System.String> object to report the index of the first occurrence of a substring:</span></span>

 [!code-vb[VbVbalrStrings#71](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#71)]

## <a name="robust-programming"></a><span data-ttu-id="dbe65-106">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="dbe65-106">Robust programming</span></span>

<span data-ttu-id="dbe65-107">Metoda <xref:System.String.IndexOf%2A> vrací umístění prvního znaku prvního výskytu podřetězce.</span><span class="sxs-lookup"><span data-stu-id="dbe65-107">The <xref:System.String.IndexOf%2A> method returns the location of the first character of the first occurrence of the substring.</span></span> <span data-ttu-id="dbe65-108">Index je založen na 0, což znamená, že první znak řetězce má index 0.</span><span class="sxs-lookup"><span data-stu-id="dbe65-108">The index is 0-based, which means the first character of a string has an index of 0.</span></span>

<span data-ttu-id="dbe65-109">Pokud <xref:System.String.IndexOf%2A> nenajde dílčí řetězec, vrátí-1.</span><span class="sxs-lookup"><span data-stu-id="dbe65-109">If <xref:System.String.IndexOf%2A> does not find the substring, it returns -1.</span></span>

<span data-ttu-id="dbe65-110">Metoda <xref:System.String.IndexOf%2A> rozlišuje velká a malá písmena a používá aktuální jazykovou verzi.</span><span class="sxs-lookup"><span data-stu-id="dbe65-110">The <xref:System.String.IndexOf%2A> method is case-sensitive and uses the current culture.</span></span>

<span data-ttu-id="dbe65-111">Pro zajištění optimálního řízení chyb může být vhodné uzavřít hledání řetězce v `Try` bloku [Try... Zachytit... Finally](../../../language-reference/statements/try-catch-finally-statement.md) – konstrukce příkazu.</span><span class="sxs-lookup"><span data-stu-id="dbe65-111">For optimal error control, you might want to enclose the string search in the `Try` block of a [Try...Catch...Finally Statement](../../../language-reference/statements/try-catch-finally-statement.md) construction.</span></span>

## <a name="see-also"></a><span data-ttu-id="dbe65-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="dbe65-112">See also</span></span>

- <xref:System.String.IndexOf%2A>
- [<span data-ttu-id="dbe65-113">Příkaz Try...Catch...Finally</span><span class="sxs-lookup"><span data-stu-id="dbe65-113">Try...Catch...Finally Statement</span></span>](../../../language-reference/statements/try-catch-finally-statement.md)
- [<span data-ttu-id="dbe65-114">Seznámení s řetězci v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="dbe65-114">Introduction to Strings in Visual Basic</span></span>](introduction-to-strings.md)
- [<span data-ttu-id="dbe65-115">Řetězce</span><span class="sxs-lookup"><span data-stu-id="dbe65-115">Strings</span></span>](index.md)
