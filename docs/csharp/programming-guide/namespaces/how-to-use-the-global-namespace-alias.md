---
title: 'Postupy: Použít globální průvodce C# programováním aliasu oboru názvů'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- aliases [C#]
- namespaces [C#], global namespace qualifier
- global namespace [C#]
ms.assetid: 98a1d89b-3c5a-44f7-8400-c4a3c0ec22a9
ms.openlocfilehash: f44bb1f010f154973fc6982882c9b5a09528da76
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2019
ms.locfileid: "68629441"
---
# <a name="how-to-use-the-global-namespace-alias-c-programming-guide"></a><span data-ttu-id="f3b5f-102">Postupy: Použití aliasu globálního oboru názvůC# (Průvodce programováním)</span><span class="sxs-lookup"><span data-stu-id="f3b5f-102">How to: Use the Global Namespace Alias (C# Programming Guide)</span></span>
<span data-ttu-id="f3b5f-103">Možnost přístupu ke členu v globálním [oboru názvů](../../../csharp/language-reference/keywords/namespace.md) je užitečná v případě, že člen může být skrytý jinou entitou se stejným názvem.</span><span class="sxs-lookup"><span data-stu-id="f3b5f-103">The ability to access a member in the global [namespace](../../../csharp/language-reference/keywords/namespace.md) is useful when the member might be hidden by another entity of the same name.</span></span>  
  
 <span data-ttu-id="f3b5f-104">Například v `Console` následujícím kódu se přeloží na `TestApp.Console` místo <xref:System> na `Console` typ v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="f3b5f-104">For example, in the following code, `Console` resolves to `TestApp.Console` instead of to the `Console` type in the <xref:System> namespace.</span></span>  
  
 [!code-csharp[csProgGuide#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/using.cs#1)]  
  
 [!code-csharp[csProgGuideNamespaces#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#1)]  
  
 <span data-ttu-id="f3b5f-105">Použití `System.Console` stále způsobí chybu, `System` protože obor názvů je skrytý třídou `TestApp.System`:</span><span class="sxs-lookup"><span data-stu-id="f3b5f-105">Using `System.Console` still results in an error because the `System` namespace is hidden by the class `TestApp.System`:</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#2)]  
  
 <span data-ttu-id="f3b5f-106">Tuto chybu však můžete obejít pomocí `global::System.Console`, například takto:</span><span class="sxs-lookup"><span data-stu-id="f3b5f-106">However, you can work around this error by using `global::System.Console`, like this:</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#3)]  
  
 <span data-ttu-id="f3b5f-107">Když je `global`levý identifikátor, hledání správného identifikátoru začíná na globálním oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="f3b5f-107">When the left identifier is `global`, the search for the right identifier starts at the global namespace.</span></span> <span data-ttu-id="f3b5f-108">Například následující deklarace je odkazována `TestApp` jako člen globálního prostoru.</span><span class="sxs-lookup"><span data-stu-id="f3b5f-108">For example, the following declaration is referencing `TestApp` as a member of the global space.</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#4)]  
  
 <span data-ttu-id="f3b5f-109">Nedoporučujeme vytvářet vlastní obory `System` názvů nazvané a je nepravděpodobné, že narazíte na kód, ve kterém k tomu došlo.</span><span class="sxs-lookup"><span data-stu-id="f3b5f-109">Obviously, creating your own namespaces called `System` is not recommended, and it is unlikely you will encounter any code in which this has happened.</span></span> <span data-ttu-id="f3b5f-110">Ve větších projektech je však velmi reálnou možností, že k duplikaci oboru názvů může dojít v jednom nebo jiném formuláři.</span><span class="sxs-lookup"><span data-stu-id="f3b5f-110">However, in larger projects, it is a very real possibility that namespace duplication may occur in one form or another.</span></span> <span data-ttu-id="f3b5f-111">V těchto situacích je kvalifikátor globálního oboru názvů vaší zárukou, že můžete zadat kořenový obor názvů.</span><span class="sxs-lookup"><span data-stu-id="f3b5f-111">In these situations, the global namespace qualifier is your guarantee that you can specify the root namespace.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f3b5f-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="f3b5f-112">Example</span></span>  
 <span data-ttu-id="f3b5f-113">V tomto příkladu je použit obor `System` názvů pro zahrnutí třídy `TestClass` , `global::System.Console` a musí být použit k odkazování `System` na `System.Console` třídu, která je skryta oborem názvů.</span><span class="sxs-lookup"><span data-stu-id="f3b5f-113">In this example, the namespace `System` is used to include the class `TestClass` therefore, `global::System.Console` must be used to reference the `System.Console` class, which is hidden by the `System` namespace.</span></span> <span data-ttu-id="f3b5f-114">Alias `colAlias` se také používá pro odkazování na obor názvů `System.Collections`; proto instance <xref:System.Collections.Hashtable?displayProperty=nameWithType> byla vytvořena pomocí tohoto aliasu namísto oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="f3b5f-114">Also, the alias `colAlias` is used to refer to the namespace `System.Collections`; therefore, the instance of a <xref:System.Collections.Hashtable?displayProperty=nameWithType> was created using this alias instead of the namespace.</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#5)]  
  
<span data-ttu-id="f3b5f-115">**A 1**
**B 2**
**C 3**</span><span class="sxs-lookup"><span data-stu-id="f3b5f-115">**A 1**
**B 2**
**C 3**</span></span>

## <a name="see-also"></a><span data-ttu-id="f3b5f-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f3b5f-116">See also</span></span>

- [<span data-ttu-id="f3b5f-117">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="f3b5f-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="f3b5f-118">Obory názvů</span><span class="sxs-lookup"><span data-stu-id="f3b5f-118">Namespaces</span></span>](../../../csharp/programming-guide/namespaces/index.md)
- [<span data-ttu-id="f3b5f-119">:: – operátor</span><span class="sxs-lookup"><span data-stu-id="f3b5f-119">:: Operator</span></span>](../../../csharp/language-reference/operators/namespace-alias-qualifier.md)
- [<span data-ttu-id="f3b5f-120">extern</span><span class="sxs-lookup"><span data-stu-id="f3b5f-120">extern</span></span>](../../../csharp/language-reference/keywords/extern.md)
