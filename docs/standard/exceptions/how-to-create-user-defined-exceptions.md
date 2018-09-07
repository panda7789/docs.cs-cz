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
ms.openlocfilehash: dca313fad896ac1c8eac37c853657bea44a8b777
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43869171"
---
# <a name="how-to-create-user-defined-exceptions"></a><span data-ttu-id="8f7fd-102">Jak vytvořit uživatelsky definovaných výjimek</span><span class="sxs-lookup"><span data-stu-id="8f7fd-102">How to create user-defined exceptions</span></span>

<span data-ttu-id="8f7fd-103">.NET poskytuje hierarchii tříd výjimek, takže v konečném důsledku odvozené ze základní třídy <xref:System.Exception>.</span><span class="sxs-lookup"><span data-stu-id="8f7fd-103">.NET provides a hierarchy of exception classes ultimately derived from the base class <xref:System.Exception>.</span></span> <span data-ttu-id="8f7fd-104">Ale pokud žádná z předdefinovaných výjimek nevyhovuje vašim potřebám, můžete vytvořit vlastní výjimky třídy odvozené z <xref:System.Exception> třídy.</span><span class="sxs-lookup"><span data-stu-id="8f7fd-104">However, if none of the predefined exceptions meets your needs, you can create your own exception classes by deriving from the <xref:System.Exception> class.</span></span>

<span data-ttu-id="8f7fd-105">Při vytváření vlastních výjimek, ukončit uživatelem definované výjimky se slovem "Výjimka" název třídy a implementovat tři běžné konstruktory, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="8f7fd-105">When creating your own exceptions, end the class name of the user-defined exception with the word "Exception," and implement the three common constructors, as shown in the following example.</span></span> <span data-ttu-id="8f7fd-106">Příklad definuje novou třídu výjimek s názvem `EmployeeListNotFoundException`.</span><span class="sxs-lookup"><span data-stu-id="8f7fd-106">The example defines a new exception class named `EmployeeListNotFoundException`.</span></span> <span data-ttu-id="8f7fd-107">Třída je odvozena z <xref:System.Exception> a zahrnuje tři konstruktory.</span><span class="sxs-lookup"><span data-stu-id="8f7fd-107">The class is derived from <xref:System.Exception> and includes three constructors.</span></span>

[!code-cpp[dg_exceptionDesign#14](../../../samples/snippets/cpp/VS_Snippets_CLR/dg_exceptionDesign/cpp/example2.cpp#14)]
[!code-csharp[dg_exceptionDesign#14](../../../samples/snippets/csharp/VS_Snippets_CLR/dg_exceptionDesign/cs/example2.cs#14)]
[!code-vb[dg_exceptionDesign#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/dg_exceptionDesign/vb/example2.vb#14)]  

> [!NOTE]
> <span data-ttu-id="8f7fd-108">V situacích, kdy používáte vzdálenou komunikaci Ujistěte se, že metadata pro všechny uživatelsky definovaných výjimek je k dispozici na serveru (volaný) a klient (objektu proxy nebo volající).</span><span class="sxs-lookup"><span data-stu-id="8f7fd-108">In situations where you are using remoting, you must ensure that the metadata for any user-defined exceptions is available at the server (callee) and to the client (the proxy object or caller).</span></span> <span data-ttu-id="8f7fd-109">Další informace najdete v tématu [osvědčené postupy pro výjimky](best-practices-for-exceptions.md).</span><span class="sxs-lookup"><span data-stu-id="8f7fd-109">For more information, see [Best practices for exceptions](best-practices-for-exceptions.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="8f7fd-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8f7fd-110">See also</span></span>

- [<span data-ttu-id="8f7fd-111">Výjimky</span><span class="sxs-lookup"><span data-stu-id="8f7fd-111">Exceptions</span></span>](index.md)
