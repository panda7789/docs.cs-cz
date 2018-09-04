---
title: 'Postupy: Spuštění kódu čištění pomocí příkazu finally (Průvodce programováním v C#)'
ms.date: 07/20/2015
helpviewer_keywords:
- try/finally blocks [C#]
- exceptions [C#], try/finally block
- exception handling [C#], try/finally block
ms.assetid: 1b1e5aef-3f32-4a88-9d39-b5fffb33bdaf
ms.openlocfilehash: 47e9bb368deb077ef10ce474683d81e0cb56cef8
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43552628"
---
# <a name="how-to-execute-cleanup-code-using-finally-c-programming-guide"></a><span data-ttu-id="36a19-102">Postupy: Spuštění kódu čištění pomocí příkazu finally (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="36a19-102">How to: Execute Cleanup Code Using finally (C# Programming Guide)</span></span>
<span data-ttu-id="36a19-103">Účel `finally` příkaz je zajistit, že potřebné vyčištění objektů, obvykle objekty, které blokují dokončení externích zdrojů, začne okamžitě, i v případě, že dojde k výjimce.</span><span class="sxs-lookup"><span data-stu-id="36a19-103">The purpose of a `finally` statement is to ensure that the necessary cleanup of objects, usually objects that are holding external resources, occurs immediately, even if an exception is thrown.</span></span> <span data-ttu-id="36a19-104">Příkladem takových vyčištění je volání <xref:System.IO.Stream.Close%2A> na <xref:System.IO.FileStream> okamžitě po použití místo abyste čekali, objekt, který má být uvolněn z paměti modulem common language runtime, následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="36a19-104">One example of such cleanup is calling <xref:System.IO.Stream.Close%2A> on a <xref:System.IO.FileStream> immediately after use instead of waiting for the object to be garbage collected by the common language runtime, as follows:</span></span>  
  
 [!code-csharp[csProgGuideExceptions#16](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/how-to-execute-cleanup-code-using-finally_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="36a19-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="36a19-105">Example</span></span>  
 <span data-ttu-id="36a19-106">Chcete-li do předchozího kódu `try-catch-finally` prohlášení, kód pro vyčištění je oddělená od funkční kód následujícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="36a19-106">To turn the previous code into a `try-catch-finally` statement, the cleanup code is separated from the working code, as follows.</span></span>  
  
 [!code-csharp[csProgGuideExceptions#17](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/how-to-execute-cleanup-code-using-finally_2.cs)]  
  
 <span data-ttu-id="36a19-107">Protože může dojít k výjimce v každém okamžiku v rámci `try` blokovat před `OpenWrite()` volání, nebo `OpenWrite()` volání sebe sama, může selhat, jsme není zaručeno, že je soubor otevřen při Snažíme se ho zavřít.</span><span class="sxs-lookup"><span data-stu-id="36a19-107">Because an exception can occur at any time within the `try` block before the `OpenWrite()` call, or the `OpenWrite()` call itself could fail, we are not guaranteed that the file is open when we try to close it.</span></span> <span data-ttu-id="36a19-108">`finally` Bloku přidá kontrolu a ujistěte se, že <xref:System.IO.FileStream> objekt není `null` před voláním <xref:System.IO.Stream.Close%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="36a19-108">The `finally` block adds a check to make sure that the <xref:System.IO.FileStream> object is not `null` before you call the <xref:System.IO.Stream.Close%2A> method.</span></span> <span data-ttu-id="36a19-109">Bez `null` zkontrolovat, `finally` bloku může vyvolat vlastní <xref:System.NullReferenceException>, ale vyvolává výjimky `finally` bloky, mělo by se vyhnout, pokud je to možné.</span><span class="sxs-lookup"><span data-stu-id="36a19-109">Without the `null` check, the `finally` block could throw its own <xref:System.NullReferenceException>, but throwing exceptions in `finally` blocks should be avoided if it is possible.</span></span>  
  
 <span data-ttu-id="36a19-110">Připojení k databázi je jiný vhodným kandidátem pro jeho uzavírání `finally` bloku.</span><span class="sxs-lookup"><span data-stu-id="36a19-110">A database connection is another good candidate for being closed in a `finally` block.</span></span> <span data-ttu-id="36a19-111">Vzhledem k tomu, že počet povolených připojení k serveru databáze je někdy omezený, by měl co nejrychleji zavřete připojení k databázi.</span><span class="sxs-lookup"><span data-stu-id="36a19-111">Because the number of connections allowed to a database server is sometimes limited, you should close database connections as quickly as possible.</span></span> <span data-ttu-id="36a19-112">Pokud je vyvolána výjimka, před uzavřením připojení, to je dalším užitečným kdy použití `finally` bloku je obecně lepší než čekání na uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="36a19-112">If an exception is thrown before you can close your connection, this is another case where using the `finally` block is better than waiting for garbage collection.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36a19-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="36a19-113">See Also</span></span>

- [<span data-ttu-id="36a19-114">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="36a19-114">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="36a19-115">Výjimky a jejich zpracování</span><span class="sxs-lookup"><span data-stu-id="36a19-115">Exceptions and Exception Handling</span></span>](../../../csharp/programming-guide/exceptions/index.md)  
- [<span data-ttu-id="36a19-116">Zpracování výjimek</span><span class="sxs-lookup"><span data-stu-id="36a19-116">Exception Handling</span></span>](../../../csharp/programming-guide/exceptions/exception-handling.md)  
- [<span data-ttu-id="36a19-117">using – příkaz</span><span class="sxs-lookup"><span data-stu-id="36a19-117">using Statement</span></span>](../../../csharp/language-reference/keywords/using-statement.md)  
- [<span data-ttu-id="36a19-118">try-catch</span><span class="sxs-lookup"><span data-stu-id="36a19-118">try-catch</span></span>](../../../csharp/language-reference/keywords/try-catch.md)  
- [<span data-ttu-id="36a19-119">try-finally</span><span class="sxs-lookup"><span data-stu-id="36a19-119">try-finally</span></span>](../../../csharp/language-reference/keywords/try-finally.md)  
- [<span data-ttu-id="36a19-120">try-catch-finally</span><span class="sxs-lookup"><span data-stu-id="36a19-120">try-catch-finally</span></span>](../../../csharp/language-reference/keywords/try-catch-finally.md)
