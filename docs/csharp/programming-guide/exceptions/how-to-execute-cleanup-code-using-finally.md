---
title: Jak spustit čistící kód pomocí Průvodce pro C# nakonec programování
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- try/finally blocks [C#]
- exceptions [C#], try/finally block
- exception handling [C#], try/finally block
ms.assetid: 1b1e5aef-3f32-4a88-9d39-b5fffb33bdaf
ms.openlocfilehash: 00cc7e40220397f4154de5be1e78a894e37374e8
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/25/2019
ms.locfileid: "75346263"
---
# <a name="how-to-execute-cleanup-code-using-finally-c-programming-guide"></a><span data-ttu-id="4f600-102">Jak spustit čistící kód pomocí finally (C# Průvodce programováním)</span><span class="sxs-lookup"><span data-stu-id="4f600-102">How to execute cleanup code using finally (C# Programming Guide)</span></span>
<span data-ttu-id="4f600-103">Účelem příkazu `finally` je zajistit, že nezbytné vyčištění objektů, obvykle objekty, které jsou uchovávány na externích zdrojích, dochází okamžitě, i když je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="4f600-103">The purpose of a `finally` statement is to ensure that the necessary cleanup of objects, usually objects that are holding external resources, occurs immediately, even if an exception is thrown.</span></span> <span data-ttu-id="4f600-104">Jedním z příkladů takového vyčištění je volání <xref:System.IO.Stream.Close%2A> na <xref:System.IO.FileStream> ihned po použití namísto čekání na uvolnění objektu modulem CLR (Common Language Runtime), a to takto:</span><span class="sxs-lookup"><span data-stu-id="4f600-104">One example of such cleanup is calling <xref:System.IO.Stream.Close%2A> on a <xref:System.IO.FileStream> immediately after use instead of waiting for the object to be garbage collected by the common language runtime, as follows:</span></span>  
  
 [!code-csharp[csProgGuideExceptions#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#16)]  
  
## <a name="example"></a><span data-ttu-id="4f600-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="4f600-105">Example</span></span>  
 <span data-ttu-id="4f600-106">Chcete-li převést předchozí kód na příkaz `try-catch-finally`, je kód pro vyčištění oddělen od pracovního kódu, jak je znázorněno níže.</span><span class="sxs-lookup"><span data-stu-id="4f600-106">To turn the previous code into a `try-catch-finally` statement, the cleanup code is separated from the working code, as follows.</span></span>  
  
 [!code-csharp[csProgGuideExceptions#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#17)]  
  
 <span data-ttu-id="4f600-107">Vzhledem k tomu, že výjimka může nastat kdykoli v rámci `try` bloku před voláním `OpenWrite()`, `OpenWrite()` nebo může selhání samotného volání selhat, nezaručujeme, že soubor je otevřený, když ho zkusíme zavřít.</span><span class="sxs-lookup"><span data-stu-id="4f600-107">Because an exception can occur at any time within the `try` block before the `OpenWrite()` call, or the `OpenWrite()` call itself could fail, we are not guaranteed that the file is open when we try to close it.</span></span> <span data-ttu-id="4f600-108">Blok `finally` přidá kontrolu pro ujištění, že objekt <xref:System.IO.FileStream> není `null` před voláním metody <xref:System.IO.Stream.Close%2A>.</span><span class="sxs-lookup"><span data-stu-id="4f600-108">The `finally` block adds a check to make sure that the <xref:System.IO.FileStream> object is not `null` before you call the <xref:System.IO.Stream.Close%2A> method.</span></span> <span data-ttu-id="4f600-109">Bez kontroly `null` může blok `finally` vyvolat svůj vlastní <xref:System.NullReferenceException>, ale vyvolání výjimek v `finally` blocích by se mělo vyhnout, pokud je to možné.</span><span class="sxs-lookup"><span data-stu-id="4f600-109">Without the `null` check, the `finally` block could throw its own <xref:System.NullReferenceException>, but throwing exceptions in `finally` blocks should be avoided if it is possible.</span></span>  
  
 <span data-ttu-id="4f600-110">Připojení k databázi je dalším vhodným kandidátem na uzavření v rámci `finally`ho bloku.</span><span class="sxs-lookup"><span data-stu-id="4f600-110">A database connection is another good candidate for being closed in a `finally` block.</span></span> <span data-ttu-id="4f600-111">Vzhledem k tomu, že počet připojení povolených pro databázový server je někdy omezený, měli byste připojení databáze co nejrychleji zavřít.</span><span class="sxs-lookup"><span data-stu-id="4f600-111">Because the number of connections allowed to a database server is sometimes limited, you should close database connections as quickly as possible.</span></span> <span data-ttu-id="4f600-112">Pokud je vyvolána výjimka předtím, než budete moci uzavřít připojení, jedná se o další případ, kdy použití bloku `finally` je lepší než čekání na uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="4f600-112">If an exception is thrown before you can close your connection, this is another case where using the `finally` block is better than waiting for garbage collection.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f600-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4f600-113">See also</span></span>

- [<span data-ttu-id="4f600-114">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="4f600-114">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="4f600-115">Výjimky a jejich zpracování</span><span class="sxs-lookup"><span data-stu-id="4f600-115">Exceptions and Exception Handling</span></span>](./index.md)
- [<span data-ttu-id="4f600-116">Zpracování výjimek</span><span class="sxs-lookup"><span data-stu-id="4f600-116">Exception Handling</span></span>](./exception-handling.md)
- [<span data-ttu-id="4f600-117">using – příkaz</span><span class="sxs-lookup"><span data-stu-id="4f600-117">using Statement</span></span>](../../language-reference/keywords/using-statement.md)
- [<span data-ttu-id="4f600-118">try-catch</span><span class="sxs-lookup"><span data-stu-id="4f600-118">try-catch</span></span>](../../language-reference/keywords/try-catch.md)
- [<span data-ttu-id="4f600-119">try-finally</span><span class="sxs-lookup"><span data-stu-id="4f600-119">try-finally</span></span>](../../language-reference/keywords/try-finally.md)
- [<span data-ttu-id="4f600-120">try-catch-finally</span><span class="sxs-lookup"><span data-stu-id="4f600-120">try-catch-finally</span></span>](../../language-reference/keywords/try-catch-finally.md)
