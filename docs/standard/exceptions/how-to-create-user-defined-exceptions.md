---
title: 'Postupy: Vytváření uživatelsky definovaných výjimek'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- user-defined exceptions
- exceptions, examples
- exceptions, user-defined
ms.assetid: 25819a5a-f915-4fc8-b924-a76915674e04
ms.openlocfilehash: 6de00490a17fff005dd50a7acc5247089c073f68
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "75708872"
---
# <a name="how-to-create-user-defined-exceptions"></a><span data-ttu-id="63b88-102">Jak vytvořit uživatelem definované výjimky</span><span class="sxs-lookup"><span data-stu-id="63b88-102">How to create user-defined exceptions</span></span>

<span data-ttu-id="63b88-103">Rozhraní .NET poskytuje hierarchii tříd výjimek, <xref:System.Exception>které jsou nakonec odvozeny ze základní třídy .</span><span class="sxs-lookup"><span data-stu-id="63b88-103">.NET provides a hierarchy of exception classes ultimately derived from the base class <xref:System.Exception>.</span></span> <span data-ttu-id="63b88-104">Pokud však žádná z předdefinovaných výjimek nevyhovuje vašim potřebám, můžete vytvořit <xref:System.Exception> vlastní třídy výjimek odvozením z třídy.</span><span class="sxs-lookup"><span data-stu-id="63b88-104">However, if none of the predefined exceptions meets your needs, you can create your own exception classes by deriving from the <xref:System.Exception> class.</span></span>

<span data-ttu-id="63b88-105">Při vytváření vlastní výjimky, konec název třídy uživatelem definované výjimky se slovem "Výjimka" a implementovat tři společné konstruktory, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="63b88-105">When creating your own exceptions, end the class name of the user-defined exception with the word "Exception", and implement the three common constructors, as shown in the following example.</span></span> <span data-ttu-id="63b88-106">Příklad definuje novou třídu `EmployeeListNotFoundException`výjimek s názvem .</span><span class="sxs-lookup"><span data-stu-id="63b88-106">The example defines a new exception class named `EmployeeListNotFoundException`.</span></span> <span data-ttu-id="63b88-107">Třída je odvozena <xref:System.Exception> od a zahrnuje tři konstruktory.</span><span class="sxs-lookup"><span data-stu-id="63b88-107">The class is derived from <xref:System.Exception> and includes three constructors.</span></span>

[!code-cpp[dg_exceptionDesign#14](../../../samples/snippets/cpp/VS_Snippets_CLR/dg_exceptionDesign/cpp/example2.cpp#14)]
[!code-csharp[dg_exceptionDesign#14](../../../samples/snippets/csharp/VS_Snippets_CLR/dg_exceptionDesign/cs/example2.cs#14)]
[!code-vb[dg_exceptionDesign#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/dg_exceptionDesign/vb/example2.vb#14)]  

> [!NOTE]
> <span data-ttu-id="63b88-108">V situacích, kdy používáte vzdálené volání, je nutné zajistit, aby metadata pro všechny uživatelem definované výjimky byla k dispozici na serveru (volaný) a klientovi (objekt proxy nebo volající).</span><span class="sxs-lookup"><span data-stu-id="63b88-108">In situations where you are using remoting, you must ensure that the metadata for any user-defined exceptions is available at the server (callee) and to the client (the proxy object or caller).</span></span> <span data-ttu-id="63b88-109">Další informace naleznete v [tématu Doporučené postupy pro výjimky](best-practices-for-exceptions.md).</span><span class="sxs-lookup"><span data-stu-id="63b88-109">For more information, see [Best practices for exceptions](best-practices-for-exceptions.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="63b88-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="63b88-110">See also</span></span>

- [<span data-ttu-id="63b88-111">Výjimky</span><span class="sxs-lookup"><span data-stu-id="63b88-111">Exceptions</span></span>](index.md)
