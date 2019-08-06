---
title: 'Postupy: Použít globální průvodce C# programováním aliasu oboru názvů'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- aliases [C#]
- namespaces [C#], global namespace qualifier
- global namespace [C#]
ms.assetid: 98a1d89b-3c5a-44f7-8400-c4a3c0ec22a9
ms.openlocfilehash: b163981d3cf6d56ab953757931b0b386a47263ff
ms.sourcegitcommit: bbfcc913c275885381820be28f61efcf8e83eecc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/05/2019
ms.locfileid: "68796290"
---
# <a name="how-to-use-the-global-namespace-alias-c-programming-guide"></a><span data-ttu-id="d7a85-102">Postupy: Použití aliasu globálního oboru názvůC# (Průvodce programováním)</span><span class="sxs-lookup"><span data-stu-id="d7a85-102">How to: Use the Global Namespace Alias (C# Programming Guide)</span></span>
<span data-ttu-id="d7a85-103">Možnost přístupu ke členu v globálním [oboru názvů](../../../csharp/language-reference/keywords/namespace.md) je užitečná v případě, že člen může být skrytý jinou entitou se stejným názvem.</span><span class="sxs-lookup"><span data-stu-id="d7a85-103">The ability to access a member in the global [namespace](../../../csharp/language-reference/keywords/namespace.md) is useful when the member might be hidden by another entity of the same name.</span></span>  
  
 <span data-ttu-id="d7a85-104">Například v `Console` následujícím kódu se přeloží na `TestApp.Console` místo <xref:System> na `Console` typ v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="d7a85-104">For example, in the following code, `Console` resolves to `TestApp.Console` instead of to the `Console` type in the <xref:System> namespace.</span></span>  
  
 [!code-csharp[csProgGuide#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/using.cs#1)]  
  
 [!code-csharp[csProgGuideNamespaces#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#1)]  
  
 <span data-ttu-id="d7a85-105">Použití `System.Console` stále způsobí chybu, `System` protože obor názvů je skrytý třídou `TestApp.System`:</span><span class="sxs-lookup"><span data-stu-id="d7a85-105">Using `System.Console` still results in an error because the `System` namespace is hidden by the class `TestApp.System`:</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#2)]  
  
 <span data-ttu-id="d7a85-106">Tuto chybu však můžete obejít pomocí `global::System.Console`, například takto:</span><span class="sxs-lookup"><span data-stu-id="d7a85-106">However, you can work around this error by using `global::System.Console`, like this:</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#3)]  
  
 <span data-ttu-id="d7a85-107">Když je `global`levý identifikátor, hledání správného identifikátoru začíná na globálním oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="d7a85-107">When the left identifier is `global`, the search for the right identifier starts at the global namespace.</span></span> <span data-ttu-id="d7a85-108">Například následující deklarace je odkazována `TestApp` jako člen globálního prostoru.</span><span class="sxs-lookup"><span data-stu-id="d7a85-108">For example, the following declaration is referencing `TestApp` as a member of the global space.</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#4)]  
  
 <span data-ttu-id="d7a85-109">Nedoporučujeme vytvářet vlastní obory `System` názvů nazvané a je nepravděpodobné, že narazíte na kód, ve kterém k tomu došlo.</span><span class="sxs-lookup"><span data-stu-id="d7a85-109">Obviously, creating your own namespaces called `System` is not recommended, and it is unlikely you will encounter any code in which this has happened.</span></span> <span data-ttu-id="d7a85-110">Ve větších projektech je však velmi reálnou možností, že k duplikaci oboru názvů může dojít v jednom nebo jiném formuláři.</span><span class="sxs-lookup"><span data-stu-id="d7a85-110">However, in larger projects, it is a very real possibility that namespace duplication may occur in one form or another.</span></span> <span data-ttu-id="d7a85-111">V těchto situacích je kvalifikátor globálního oboru názvů vaší zárukou, že můžete zadat kořenový obor názvů.</span><span class="sxs-lookup"><span data-stu-id="d7a85-111">In these situations, the global namespace qualifier is your guarantee that you can specify the root namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7a85-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d7a85-112">See also</span></span>

- [<span data-ttu-id="d7a85-113">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="d7a85-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="d7a85-114">Obory názvů</span><span class="sxs-lookup"><span data-stu-id="d7a85-114">Namespaces</span></span>](../../../csharp/programming-guide/namespaces/index.md)
- [<span data-ttu-id="d7a85-115">:: – operátor</span><span class="sxs-lookup"><span data-stu-id="d7a85-115">:: Operator</span></span>](../../../csharp/language-reference/operators/namespace-alias-qualifier.md)
- [<span data-ttu-id="d7a85-116">extern</span><span class="sxs-lookup"><span data-stu-id="d7a85-116">extern</span></span>](../../../csharp/language-reference/keywords/extern.md)
