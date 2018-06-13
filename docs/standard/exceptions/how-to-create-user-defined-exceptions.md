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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 90bf9d6dbfebf8f7c1aa22e5844cf4e30b89b8d6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33572798"
---
# <a name="how-to-create-user-defined-exceptions"></a><span data-ttu-id="4204e-102">Jak vytvořit uživatelem definované výjimky</span><span class="sxs-lookup"><span data-stu-id="4204e-102">How to create user-defined exceptions</span></span>

<span data-ttu-id="4204e-103">Rozhraní .NET poskytuje hierarchii tříd výjimek nakonec odvozených od základní třídy <xref:System.Exception>.</span><span class="sxs-lookup"><span data-stu-id="4204e-103">.NET provides a hierarchy of exception classes ultimately derived from the base class <xref:System.Exception>.</span></span> <span data-ttu-id="4204e-104">Ale pokud žádná z předdefinované výjimky vyhovuje vašim potřebám, můžete vytvořit vlastní třídy výjimek odvozené z <xref:System.Exception> třídy.</span><span class="sxs-lookup"><span data-stu-id="4204e-104">However, if none of the predefined exceptions meets your needs, you can create your own exception classes by deriving from the <xref:System.Exception> class.</span></span>

<span data-ttu-id="4204e-105">Při vytváření vlastní výjimky, ukončení název třídy uživatelem definované výjimky slovem "Výjimky" a implementovat tři běžné konstruktory, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="4204e-105">When creating your own exceptions, end the class name of the user-defined exception with the word "Exception," and implement the three common constructors, as shown in the following example.</span></span> <span data-ttu-id="4204e-106">V příkladu definuje novou třídu výjimky s názvem `EmployeeListNotFoundException`.</span><span class="sxs-lookup"><span data-stu-id="4204e-106">The example defines a new exception class named `EmployeeListNotFoundException`.</span></span> <span data-ttu-id="4204e-107">Odvození třídy z <xref:System.Exception> a zahrnuje tři konstruktory.</span><span class="sxs-lookup"><span data-stu-id="4204e-107">The class is derived from <xref:System.Exception> and includes three constructors.</span></span>

[!code-cpp[dg_exceptionDesign#14](../../../samples/snippets/cpp/VS_Snippets_CLR/dg_exceptionDesign/cpp/example2.cpp#14)]
[!code-csharp[dg_exceptionDesign#14](../../../samples/snippets/csharp/VS_Snippets_CLR/dg_exceptionDesign/cs/example2.cs#14)]
[!code-vb[dg_exceptionDesign#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/dg_exceptionDesign/vb/example2.vb#14)]  

> [!NOTE]
> <span data-ttu-id="4204e-108">V situacích, kdy používáte vzdálenou komunikaci Ujistěte se, že metadata pro uživatelem definované výjimky je k dispozici na serveru (volaný) a klienta (proxy – objekt nebo volající).</span><span class="sxs-lookup"><span data-stu-id="4204e-108">In situations where you are using remoting, you must ensure that the metadata for any user-defined exceptions is available at the server (callee) and to the client (the proxy object or caller).</span></span> <span data-ttu-id="4204e-109">Další informace najdete v tématu [osvědčené postupy pro výjimky](best-practices-for-exceptions.md).</span><span class="sxs-lookup"><span data-stu-id="4204e-109">For more information, see [Best practices for exceptions](best-practices-for-exceptions.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="4204e-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="4204e-110">See Also</span></span>  
[<span data-ttu-id="4204e-111">Výjimky</span><span class="sxs-lookup"><span data-stu-id="4204e-111">Exceptions</span></span>](index.md)
