---
title: 'Postupy: Použití aliasu globálního oboru názvů (Průvodce programováním v C#)'
ms.date: 07/20/2015
helpviewer_keywords:
- aliases [C#]
- namespaces [C#], global namespace qualifier
- global namespace [C#]
ms.assetid: 98a1d89b-3c5a-44f7-8400-c4a3c0ec22a9
ms.openlocfilehash: c15271abb55cb29a200185e4b512a76a4913d848
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44064709"
---
# <a name="how-to-use-the-global-namespace-alias-c-programming-guide"></a><span data-ttu-id="c831f-102">Postupy: Použití aliasu globálního oboru názvů (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="c831f-102">How to: Use the Global Namespace Alias (C# Programming Guide)</span></span>
<span data-ttu-id="c831f-103">Umožňuje přístup ke členu v globální [obor názvů](../../../csharp/language-reference/keywords/namespace.md) je užitečné, když člen může být skryty pomocí jiné entity se stejným názvem.</span><span class="sxs-lookup"><span data-stu-id="c831f-103">The ability to access a member in the global [namespace](../../../csharp/language-reference/keywords/namespace.md) is useful when the member might be hidden by another entity of the same name.</span></span>  
  
 <span data-ttu-id="c831f-104">Například v následujícím kódu `Console` přeloží na `TestApp.Console` místo na `Console` zadejte <xref:System> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="c831f-104">For example, in the following code, `Console` resolves to `TestApp.Console` instead of to the `Console` type in the <xref:System> namespace.</span></span>  
  
 [!code-csharp[csProgGuide#1](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/how-to-use-the-global-namespace-alias_1.cs)]  
  
 [!code-csharp[csProgGuideNamespaces#1](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/how-to-use-the-global-namespace-alias_2.cs)]  
  
 <span data-ttu-id="c831f-105">Pomocí `System.Console` stále dojde k chybě, protože `System` obor názvů je skrytý třídou `TestApp.System`:</span><span class="sxs-lookup"><span data-stu-id="c831f-105">Using `System.Console` still results in an error because the `System` namespace is hidden by the class `TestApp.System`:</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#2](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/how-to-use-the-global-namespace-alias_3.cs)]  
  
 <span data-ttu-id="c831f-106">Nicméně, můžete alternativně vyřešit tuto chybu pomocí `global::System.Console`, tímto způsobem:</span><span class="sxs-lookup"><span data-stu-id="c831f-106">However, you can work around this error by using `global::System.Console`, like this:</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#3](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/how-to-use-the-global-namespace-alias_4.cs)]  
  
 <span data-ttu-id="c831f-107">Pokud je identifikátor levé `global`, vyhledejte správný identifikátor začíná v globálním oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="c831f-107">When the left identifier is `global`, the search for the right identifier starts at the global namespace.</span></span> <span data-ttu-id="c831f-108">Například následující deklaraci odkazuje `TestApp` jako člen globálním prostoru.</span><span class="sxs-lookup"><span data-stu-id="c831f-108">For example, the following declaration is referencing `TestApp` as a member of the global space.</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#4](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/how-to-use-the-global-namespace-alias_5.cs)]  
  
 <span data-ttu-id="c831f-109">Samozřejmě, vytvářet své vlastní obory názvů volá `System` se nedoporučuje, a nepravděpodobné, narazíte na jakýkoli kód, ve kterém se to stalo.</span><span class="sxs-lookup"><span data-stu-id="c831f-109">Obviously, creating your own namespaces called `System` is not recommended, and it is unlikely you will encounter any code in which this has happened.</span></span> <span data-ttu-id="c831f-110">U větších projektů, je však velmi skutečné možnost, duplikace oboru názvů může vyskytovat ve formuláři nebo jiném.</span><span class="sxs-lookup"><span data-stu-id="c831f-110">However, in larger projects, it is a very real possibility that namespace duplication may occur in one form or another.</span></span> <span data-ttu-id="c831f-111">Kvalifikátor globálního oboru názvů v těchto situacích je vaše záruku, že můžete určit kořenový obor názvů.</span><span class="sxs-lookup"><span data-stu-id="c831f-111">In these situations, the global namespace qualifier is your guarantee that you can specify the root namespace.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c831f-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="c831f-112">Example</span></span>  
 <span data-ttu-id="c831f-113">V tomto příkladu, obor názvů `System` je použít k zahrnutí třídy `TestClass` proto `global::System.Console` musí být použita na odkaz `System.Console` třídu, která je skrytý `System` oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="c831f-113">In this example, the namespace `System` is used to include the class `TestClass` therefore, `global::System.Console` must be used to reference the `System.Console` class, which is hidden by the `System` namespace.</span></span> <span data-ttu-id="c831f-114">Také, že alias `colAlias` se používá k odkazování na obor názvů `System.Collections`; proto instanci <xref:System.Collections.Hashtable?displayProperty=nameWithType> byl vytvořen pomocí tento alias místo obor názvů.</span><span class="sxs-lookup"><span data-stu-id="c831f-114">Also, the alias `colAlias` is used to refer to the namespace `System.Collections`; therefore, the instance of a <xref:System.Collections.Hashtable?displayProperty=nameWithType> was created using this alias instead of the namespace.</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#5](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/how-to-use-the-global-namespace-alias_6.cs)]  
  
<span data-ttu-id="c831f-115">**1**
**B 2**
**C 3**</span><span class="sxs-lookup"><span data-stu-id="c831f-115">**A 1**
**B 2**
**C 3**</span></span>

## <a name="see-also"></a><span data-ttu-id="c831f-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="c831f-116">See Also</span></span>

- [<span data-ttu-id="c831f-117">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="c831f-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="c831f-118">Obory názvů</span><span class="sxs-lookup"><span data-stu-id="c831f-118">Namespaces</span></span>](../../../csharp/programming-guide/namespaces/index.md)  
- [<span data-ttu-id="c831f-119">. – operátor</span><span class="sxs-lookup"><span data-stu-id="c831f-119">. Operator</span></span>](../../../csharp/language-reference/operators/member-access-operator.md)  
- [<span data-ttu-id="c831f-120">:: – operátor</span><span class="sxs-lookup"><span data-stu-id="c831f-120">:: Operator</span></span>](../../../csharp/language-reference/operators/namespace-alias-qualifer.md)  
- [<span data-ttu-id="c831f-121">extern</span><span class="sxs-lookup"><span data-stu-id="c831f-121">extern</span></span>](../../../csharp/language-reference/keywords/extern.md)
