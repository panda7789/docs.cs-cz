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
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75708872"
---
# <a name="how-to-create-user-defined-exceptions"></a><span data-ttu-id="ba818-102">Vytvoření uživatelsky definovaných výjimek</span><span class="sxs-lookup"><span data-stu-id="ba818-102">How to create user-defined exceptions</span></span>

<span data-ttu-id="ba818-103">Rozhraní .NET poskytuje hierarchii tříd výjimek, které jsou nakonec odvozeny od <xref:System.Exception>základní třídy.</span><span class="sxs-lookup"><span data-stu-id="ba818-103">.NET provides a hierarchy of exception classes ultimately derived from the base class <xref:System.Exception>.</span></span> <span data-ttu-id="ba818-104">Nicméně pokud žádná z předdefinovaných výjimek nevyhovuje vašim potřebám, můžete vytvořit vlastní třídy výjimek odvozením z třídy <xref:System.Exception>.</span><span class="sxs-lookup"><span data-stu-id="ba818-104">However, if none of the predefined exceptions meets your needs, you can create your own exception classes by deriving from the <xref:System.Exception> class.</span></span>

<span data-ttu-id="ba818-105">Při vytváření vlastních výjimek, ukončete název třídy uživatelsky definované výjimky slovem "Exception" a implementujte tři společné konstruktory, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="ba818-105">When creating your own exceptions, end the class name of the user-defined exception with the word "Exception", and implement the three common constructors, as shown in the following example.</span></span> <span data-ttu-id="ba818-106">Příklad definuje novou třídu výjimky s názvem `EmployeeListNotFoundException`.</span><span class="sxs-lookup"><span data-stu-id="ba818-106">The example defines a new exception class named `EmployeeListNotFoundException`.</span></span> <span data-ttu-id="ba818-107">Třída je odvozena z <xref:System.Exception> a obsahuje tři konstruktory.</span><span class="sxs-lookup"><span data-stu-id="ba818-107">The class is derived from <xref:System.Exception> and includes three constructors.</span></span>

[!code-cpp[dg_exceptionDesign#14](../../../samples/snippets/cpp/VS_Snippets_CLR/dg_exceptionDesign/cpp/example2.cpp#14)]
[!code-csharp[dg_exceptionDesign#14](../../../samples/snippets/csharp/VS_Snippets_CLR/dg_exceptionDesign/cs/example2.cs#14)]
[!code-vb[dg_exceptionDesign#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/dg_exceptionDesign/vb/example2.vb#14)]  

> [!NOTE]
> <span data-ttu-id="ba818-108">V situacích, kdy používáte vzdálenou komunikaci, je nutné zajistit, aby metadata pro všechny výjimky definované uživatelem byly k dispozici na serveru (volaném) a klientovi (objekt proxy nebo volající).</span><span class="sxs-lookup"><span data-stu-id="ba818-108">In situations where you are using remoting, you must ensure that the metadata for any user-defined exceptions is available at the server (callee) and to the client (the proxy object or caller).</span></span> <span data-ttu-id="ba818-109">Další informace najdete v tématu [osvědčené postupy pro výjimky](best-practices-for-exceptions.md).</span><span class="sxs-lookup"><span data-stu-id="ba818-109">For more information, see [Best practices for exceptions](best-practices-for-exceptions.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="ba818-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ba818-110">See also</span></span>

- [<span data-ttu-id="ba818-111">Výjimky</span><span class="sxs-lookup"><span data-stu-id="ba818-111">Exceptions</span></span>](index.md)
