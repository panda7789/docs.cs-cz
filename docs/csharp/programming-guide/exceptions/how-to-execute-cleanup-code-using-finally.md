---
title: Jak spustit kód vyčištění pomocí finally - C# Programovací průvodce
ms.date: 07/20/2015
helpviewer_keywords:
- try/finally blocks [C#]
- exceptions [C#], try/finally block
- exception handling [C#], try/finally block
ms.assetid: 1b1e5aef-3f32-4a88-9d39-b5fffb33bdaf
ms.openlocfilehash: d1ba761e64053d656ad4cd004133fc455a57c6f6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75705272"
---
# <a name="how-to-execute-cleanup-code-using-finally-c-programming-guide"></a><span data-ttu-id="bcc59-102">Jak spustit vyčištění kódu pomocí finally (C# Programovací průvodce)</span><span class="sxs-lookup"><span data-stu-id="bcc59-102">How to execute cleanup code using finally (C# Programming Guide)</span></span>
<span data-ttu-id="bcc59-103">Účelem příkazu `finally` je zajistit, aby nezbytné vyčištění objektů, obvykle objekty, které jsou v držení externích prostředků, dojde okamžitě, i v případě, že je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="bcc59-103">The purpose of a `finally` statement is to ensure that the necessary cleanup of objects, usually objects that are holding external resources, occurs immediately, even if an exception is thrown.</span></span> <span data-ttu-id="bcc59-104">Jedním z příkladů takového <xref:System.IO.Stream.Close%2A> vyčištění <xref:System.IO.FileStream> je volání na ihned po použití namísto čekání na objekt, který má být uvolněna systémem runtime společného jazyka, takto:</span><span class="sxs-lookup"><span data-stu-id="bcc59-104">One example of such cleanup is calling <xref:System.IO.Stream.Close%2A> on a <xref:System.IO.FileStream> immediately after use instead of waiting for the object to be garbage collected by the common language runtime, as follows:</span></span>  
  
 [!code-csharp[csProgGuideExceptions#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#16)]  
  
## <a name="example"></a><span data-ttu-id="bcc59-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="bcc59-105">Example</span></span>  
 <span data-ttu-id="bcc59-106">Chcete-li změnit předchozí `try-catch-finally` kód na příkaz, kód vyčištění je oddělen od pracovního kódu, následujícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="bcc59-106">To turn the previous code into a `try-catch-finally` statement, the cleanup code is separated from the working code, as follows.</span></span>  
  
 [!code-csharp[csProgGuideExceptions#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#17)]  
  
 <span data-ttu-id="bcc59-107">Vzhledem k tomu, že `try` k výjimce může dojít kdykoli v rámci bloku před voláním `OpenWrite()` nebo samotné `OpenWrite()` volání může selhat, není zaručeno, že soubor je otevřen při pokusu o jeho zavření.</span><span class="sxs-lookup"><span data-stu-id="bcc59-107">Because an exception can occur at any time within the `try` block before the `OpenWrite()` call, or the `OpenWrite()` call itself could fail, we are not guaranteed that the file is open when we try to close it.</span></span> <span data-ttu-id="bcc59-108">Blok `finally` přidá kontrolu, abyste se <xref:System.IO.FileStream> ujistili, že objekt není `null` před voláním <xref:System.IO.Stream.Close%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="bcc59-108">The `finally` block adds a check to make sure that the <xref:System.IO.FileStream> object is not `null` before you call the <xref:System.IO.Stream.Close%2A> method.</span></span> <span data-ttu-id="bcc59-109">Bez `null` kontroly `finally` by blok mohl <xref:System.NullReferenceException>vyvolat vlastní , `finally` ale vyvolání výjimky v blocích je třeba se vyhnout, pokud je to možné.</span><span class="sxs-lookup"><span data-stu-id="bcc59-109">Without the `null` check, the `finally` block could throw its own <xref:System.NullReferenceException>, but throwing exceptions in `finally` blocks should be avoided if it is possible.</span></span>  
  
 <span data-ttu-id="bcc59-110">Připojení k databázi je dalším dobrým `finally` kandidátem pro zavření v bloku.</span><span class="sxs-lookup"><span data-stu-id="bcc59-110">A database connection is another good candidate for being closed in a `finally` block.</span></span> <span data-ttu-id="bcc59-111">Vzhledem k tomu, že počet připojení povolených k databázovému serveru je někdy omezen, měli byste co nejrychleji ukončit připojení k databázi.</span><span class="sxs-lookup"><span data-stu-id="bcc59-111">Because the number of connections allowed to a database server is sometimes limited, you should close database connections as quickly as possible.</span></span> <span data-ttu-id="bcc59-112">Pokud je vyvolána výjimka před ukončením připojení, je `finally` to jiný případ, kdy pomocí bloku je lepší než čekání na uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="bcc59-112">If an exception is thrown before you can close your connection, this is another case where using the `finally` block is better than waiting for garbage collection.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bcc59-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="bcc59-113">See also</span></span>

- [<span data-ttu-id="bcc59-114">Programovací příručka jazyka C#</span><span class="sxs-lookup"><span data-stu-id="bcc59-114">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="bcc59-115">Výjimky a zpracování výjimek</span><span class="sxs-lookup"><span data-stu-id="bcc59-115">Exceptions and Exception Handling</span></span>](./index.md)
- [<span data-ttu-id="bcc59-116">Zpracování výjimek</span><span class="sxs-lookup"><span data-stu-id="bcc59-116">Exception Handling</span></span>](./exception-handling.md)
- [<span data-ttu-id="bcc59-117">using – příkaz</span><span class="sxs-lookup"><span data-stu-id="bcc59-117">using Statement</span></span>](../../language-reference/keywords/using-statement.md)
- [<span data-ttu-id="bcc59-118">try-catch</span><span class="sxs-lookup"><span data-stu-id="bcc59-118">try-catch</span></span>](../../language-reference/keywords/try-catch.md)
- [<span data-ttu-id="bcc59-119">try-finally</span><span class="sxs-lookup"><span data-stu-id="bcc59-119">try-finally</span></span>](../../language-reference/keywords/try-finally.md)
- [<span data-ttu-id="bcc59-120">try-catch-finally</span><span class="sxs-lookup"><span data-stu-id="bcc59-120">try-catch-finally</span></span>](../../language-reference/keywords/try-catch-finally.md)
