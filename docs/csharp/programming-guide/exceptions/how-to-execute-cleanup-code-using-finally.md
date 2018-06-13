---
title: 'Postupy: Spuštění kódu čištění pomocí příkazu finally (Průvodce programováním v C#)'
ms.date: 07/20/2015
helpviewer_keywords:
- try/finally blocks [C#]
- exceptions [C#], try/finally block
- exception handling [C#], try/finally block
ms.assetid: 1b1e5aef-3f32-4a88-9d39-b5fffb33bdaf
ms.openlocfilehash: 948281af45d04714ed6fc308b60341e87abeb830
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33331705"
---
# <a name="how-to-execute-cleanup-code-using-finally-c-programming-guide"></a><span data-ttu-id="4a2d8-102">Postupy: Spuštění kódu čištění pomocí příkazu finally (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="4a2d8-102">How to: Execute Cleanup Code Using finally (C# Programming Guide)</span></span>
<span data-ttu-id="4a2d8-103">Účel `finally` příkaz je aby se zajistilo nezbytné čištění objektů, obvykle objekty, které jsou externí prostředky, která uchovává okamžitě, i když je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="4a2d8-103">The purpose of a `finally` statement is to ensure that the necessary cleanup of objects, usually objects that are holding external resources, occurs immediately, even if an exception is thrown.</span></span> <span data-ttu-id="4a2d8-104">Příkladem takových čištění volá <xref:System.IO.Stream.Close%2A> na <xref:System.IO.FileStream> okamžitě po použití místo abyste čekali, objekt, který má být uvolnění z paměti modulem common language runtime, následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="4a2d8-104">One example of such cleanup is calling <xref:System.IO.Stream.Close%2A> on a <xref:System.IO.FileStream> immediately after use instead of waiting for the object to be garbage collected by the common language runtime, as follows:</span></span>  
  
 [!code-csharp[csProgGuideExceptions#16](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/how-to-execute-cleanup-code-using-finally_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="4a2d8-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="4a2d8-105">Example</span></span>  
 <span data-ttu-id="4a2d8-106">Chcete-li do předchozí kód `try-catch-finally` příkaz kód čištění je oddělená od kód pracovní následujícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="4a2d8-106">To turn the previous code into a `try-catch-finally` statement, the cleanup code is separated from the working code, as follows.</span></span>  
  
 [!code-csharp[csProgGuideExceptions#17](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/how-to-execute-cleanup-code-using-finally_2.cs)]  
  
 <span data-ttu-id="4a2d8-107">Vzhledem k tomu může dojít k výjimce, kdykoli v rámci `try` před zablokovat `OpenWrite()` volat, nebo `OpenWrite()` volání sebe sama se možná nepovede, jsme se nezaručuje, že soubor je při pokusu o zavřete ho otevřete.</span><span class="sxs-lookup"><span data-stu-id="4a2d8-107">Because an exception can occur at any time within the `try` block before the `OpenWrite()` call, or the `OpenWrite()` call itself could fail, we are not guaranteed that the file is open when we try to close it.</span></span> <span data-ttu-id="4a2d8-108">`finally` Bloku přidá kontrola Ujistěte se, že <xref:System.IO.FileStream> objekt není `null` před voláním <xref:System.IO.Stream.Close%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="4a2d8-108">The `finally` block adds a check to make sure that the <xref:System.IO.FileStream> object is not `null` before you call the <xref:System.IO.Stream.Close%2A> method.</span></span> <span data-ttu-id="4a2d8-109">Bez `null` zkontrolovat, `finally` bloku může vyvolat vlastní <xref:System.NullReferenceException>, ale vyvolávání výjimek `finally` bloky je nutno, pokud je to možné.</span><span class="sxs-lookup"><span data-stu-id="4a2d8-109">Without the `null` check, the `finally` block could throw its own <xref:System.NullReferenceException>, but throwing exceptions in `finally` blocks should be avoided if it is possible.</span></span>  
  
 <span data-ttu-id="4a2d8-110">Připojení k databázi je pro dochází k uzavření jiné vhodným kandidátem `finally` bloku.</span><span class="sxs-lookup"><span data-stu-id="4a2d8-110">A database connection is another good candidate for being closed in a `finally` block.</span></span> <span data-ttu-id="4a2d8-111">Počet připojení povolená pro databázový server, který je někdy omezená, a proto měli co nejrychleji zavřete připojení databáze.</span><span class="sxs-lookup"><span data-stu-id="4a2d8-111">Because the number of connections allowed to a database server is sometimes limited, you should close database connections as quickly as possible.</span></span> <span data-ttu-id="4a2d8-112">Pokud před uzavřením připojení, je vyvolána výjimka, je to jiné případ kde pomocí `finally` bloku je lepší, než čekání uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="4a2d8-112">If an exception is thrown before you can close your connection, this is another case where using the `finally` block is better than waiting for garbage collection.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a2d8-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="4a2d8-113">See Also</span></span>  
 [<span data-ttu-id="4a2d8-114">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="4a2d8-114">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="4a2d8-115">Výjimky a jejich zpracování</span><span class="sxs-lookup"><span data-stu-id="4a2d8-115">Exceptions and Exception Handling</span></span>](../../../csharp/programming-guide/exceptions/index.md)  
 [<span data-ttu-id="4a2d8-116">Zpracování výjimek</span><span class="sxs-lookup"><span data-stu-id="4a2d8-116">Exception Handling</span></span>](../../../csharp/programming-guide/exceptions/exception-handling.md)  
 [<span data-ttu-id="4a2d8-117">using – příkaz</span><span class="sxs-lookup"><span data-stu-id="4a2d8-117">using Statement</span></span>](../../../csharp/language-reference/keywords/using-statement.md)  
 [<span data-ttu-id="4a2d8-118">try-catch</span><span class="sxs-lookup"><span data-stu-id="4a2d8-118">try-catch</span></span>](../../../csharp/language-reference/keywords/try-catch.md)  
 [<span data-ttu-id="4a2d8-119">try-finally</span><span class="sxs-lookup"><span data-stu-id="4a2d8-119">try-finally</span></span>](../../../csharp/language-reference/keywords/try-finally.md)  
 [<span data-ttu-id="4a2d8-120">try-catch-finally</span><span class="sxs-lookup"><span data-stu-id="4a2d8-120">try-catch-finally</span></span>](../../../csharp/language-reference/keywords/try-catch-finally.md)
