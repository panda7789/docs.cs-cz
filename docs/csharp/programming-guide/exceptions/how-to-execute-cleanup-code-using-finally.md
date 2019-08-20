---
title: 'Postupy: Spustit čistící kód pomocí Průvodce pro C# nakonec programování'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- try/finally blocks [C#]
- exceptions [C#], try/finally block
- exception handling [C#], try/finally block
ms.assetid: 1b1e5aef-3f32-4a88-9d39-b5fffb33bdaf
ms.openlocfilehash: e6adbb864b0450cdd1dbfcc56abdbad2034c5c7a
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69590244"
---
# <a name="how-to-execute-cleanup-code-using-finally-c-programming-guide"></a><span data-ttu-id="ad6dd-102">Postupy: Spustit čistící kód pomocí finally (C# Průvodce programováním)</span><span class="sxs-lookup"><span data-stu-id="ad6dd-102">How to: Execute Cleanup Code Using finally (C# Programming Guide)</span></span>
<span data-ttu-id="ad6dd-103">Účelem `finally` příkazu je zajistit, aby bylo nutné vyčistit objekty, obvykle objekty, které jsou uchovávány v externích prostředcích, dochází okamžitě, i když je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="ad6dd-103">The purpose of a `finally` statement is to ensure that the necessary cleanup of objects, usually objects that are holding external resources, occurs immediately, even if an exception is thrown.</span></span> <span data-ttu-id="ad6dd-104">Jedním z příkladů takového vyčištění je volání <xref:System.IO.Stream.Close%2A> <xref:System.IO.FileStream> ihned po použití namísto čekání na uvolnění objektu modulem CLR (Common Language Runtime), a to takto:</span><span class="sxs-lookup"><span data-stu-id="ad6dd-104">One example of such cleanup is calling <xref:System.IO.Stream.Close%2A> on a <xref:System.IO.FileStream> immediately after use instead of waiting for the object to be garbage collected by the common language runtime, as follows:</span></span>  
  
 [!code-csharp[csProgGuideExceptions#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#16)]  
  
## <a name="example"></a><span data-ttu-id="ad6dd-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="ad6dd-105">Example</span></span>  
 <span data-ttu-id="ad6dd-106">Chcete-li převést předchozí kód do `try-catch-finally` příkazu, je kód pro vyčištění oddělen od pracovního kódu, jak je znázorněno níže.</span><span class="sxs-lookup"><span data-stu-id="ad6dd-106">To turn the previous code into a `try-catch-finally` statement, the cleanup code is separated from the working code, as follows.</span></span>  
  
 [!code-csharp[csProgGuideExceptions#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#17)]  
  
 <span data-ttu-id="ad6dd-107">Vzhledem k tomu, že výjimka může nastat kdykoli v `try` rámci bloku `OpenWrite()` před voláním nebo se `OpenWrite()` může stát, že by volání nebylo úspěšné, nezaručujeme, že soubor je otevřený, když se ho pokusíme zavřít.</span><span class="sxs-lookup"><span data-stu-id="ad6dd-107">Because an exception can occur at any time within the `try` block before the `OpenWrite()` call, or the `OpenWrite()` call itself could fail, we are not guaranteed that the file is open when we try to close it.</span></span> <span data-ttu-id="ad6dd-108">Blok přidá kontrolu pro ujištění <xref:System.IO.FileStream> , že objekt `null` není před voláním <xref:System.IO.Stream.Close%2A> metody. `finally`</span><span class="sxs-lookup"><span data-stu-id="ad6dd-108">The `finally` block adds a check to make sure that the <xref:System.IO.FileStream> object is not `null` before you call the <xref:System.IO.Stream.Close%2A> method.</span></span> <span data-ttu-id="ad6dd-109">Bez kontroly může blok vyvolat svou vlastní <xref:System.NullReferenceException>hodnotu, ale vyvolání výjimek v `finally` blocích by se mělo vyhnout, pokud je to možné. `finally` `null`</span><span class="sxs-lookup"><span data-stu-id="ad6dd-109">Without the `null` check, the `finally` block could throw its own <xref:System.NullReferenceException>, but throwing exceptions in `finally` blocks should be avoided if it is possible.</span></span>  
  
 <span data-ttu-id="ad6dd-110">Připojení k databázi je dalším vhodným kandidátem na uzavření v `finally` bloku.</span><span class="sxs-lookup"><span data-stu-id="ad6dd-110">A database connection is another good candidate for being closed in a `finally` block.</span></span> <span data-ttu-id="ad6dd-111">Vzhledem k tomu, že počet připojení povolených pro databázový server je někdy omezený, měli byste připojení databáze co nejrychleji zavřít.</span><span class="sxs-lookup"><span data-stu-id="ad6dd-111">Because the number of connections allowed to a database server is sometimes limited, you should close database connections as quickly as possible.</span></span> <span data-ttu-id="ad6dd-112">Pokud je vyvolána výjimka před zavřením připojení, jedná se o `finally` jiný případ, kdy použití bloku je lepší než čekání na uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="ad6dd-112">If an exception is thrown before you can close your connection, this is another case where using the `finally` block is better than waiting for garbage collection.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad6dd-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ad6dd-113">See also</span></span>

- [<span data-ttu-id="ad6dd-114">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="ad6dd-114">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="ad6dd-115">Výjimky a jejich zpracování</span><span class="sxs-lookup"><span data-stu-id="ad6dd-115">Exceptions and Exception Handling</span></span>](./index.md)
- [<span data-ttu-id="ad6dd-116">Zpracování výjimek</span><span class="sxs-lookup"><span data-stu-id="ad6dd-116">Exception Handling</span></span>](./exception-handling.md)
- [<span data-ttu-id="ad6dd-117">using – příkaz</span><span class="sxs-lookup"><span data-stu-id="ad6dd-117">using Statement</span></span>](../../language-reference/keywords/using-statement.md)
- [<span data-ttu-id="ad6dd-118">try-catch</span><span class="sxs-lookup"><span data-stu-id="ad6dd-118">try-catch</span></span>](../../language-reference/keywords/try-catch.md)
- [<span data-ttu-id="ad6dd-119">try-finally</span><span class="sxs-lookup"><span data-stu-id="ad6dd-119">try-finally</span></span>](../../language-reference/keywords/try-finally.md)
- [<span data-ttu-id="ad6dd-120">try-catch-finally</span><span class="sxs-lookup"><span data-stu-id="ad6dd-120">try-catch-finally</span></span>](../../language-reference/keywords/try-catch-finally.md)
