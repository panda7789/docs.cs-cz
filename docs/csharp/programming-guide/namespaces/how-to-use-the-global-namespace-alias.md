---
title: 'Postupy: Použití aliasu globálního oboru názvů (Průvodce programováním v C#)'
ms.date: 07/20/2015
helpviewer_keywords:
- aliases [C#]
- namespaces [C#], global namespace qualifier
- global namespace [C#]
ms.assetid: 98a1d89b-3c5a-44f7-8400-c4a3c0ec22a9
ms.openlocfilehash: 74f51d18ddda1ae4706b78aaf713683d2e505d2e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33327239"
---
# <a name="how-to-use-the-global-namespace-alias-c-programming-guide"></a><span data-ttu-id="014f9-102">Postupy: Použití aliasu globálního oboru názvů (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="014f9-102">How to: Use the Global Namespace Alias (C# Programming Guide)</span></span>
<span data-ttu-id="014f9-103">Umožňuje přístup ke členu v globální [obor názvů](../../../csharp/language-reference/keywords/namespace.md) je užitečné, když se člen může být skrytý na základě jiné entity se stejným názvem.</span><span class="sxs-lookup"><span data-stu-id="014f9-103">The ability to access a member in the global [namespace](../../../csharp/language-reference/keywords/namespace.md) is useful when the member might be hidden by another entity of the same name.</span></span>  
  
 <span data-ttu-id="014f9-104">Například v následujícím kódu `Console` přeloží na `TestApp.Console` místo na `Console` zadejte <xref:System> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="014f9-104">For example, in the following code, `Console` resolves to `TestApp.Console` instead of to the `Console` type in the <xref:System> namespace.</span></span>  
  
 [!code-csharp[csProgGuide#1](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/how-to-use-the-global-namespace-alias_1.cs)]  
  
 [!code-csharp[csProgGuideNamespaces#1](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/how-to-use-the-global-namespace-alias_2.cs)]  
  
 <span data-ttu-id="014f9-105">Pomocí `System.Console` stále dojde k chybě, protože `System` obor názvů je skrytý na základě třídy `TestApp.System`:</span><span class="sxs-lookup"><span data-stu-id="014f9-105">Using `System.Console` still results in an error because the `System` namespace is hidden by the class `TestApp.System`:</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#2](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/how-to-use-the-global-namespace-alias_3.cs)]  
  
 <span data-ttu-id="014f9-106">Nicméně, můžete tuto chybu vyřešit pomocí `global::System.Console`, podobné výjimky:</span><span class="sxs-lookup"><span data-stu-id="014f9-106">However, you can work around this error by using `global::System.Console`, like this:</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#3](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/how-to-use-the-global-namespace-alias_4.cs)]  
  
 <span data-ttu-id="014f9-107">Pokud je identifikátor levém `global`, spustí vyhledávání pro identifikátor vpravo v globálním oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="014f9-107">When the left identifier is `global`, the search for the right identifier starts at the global namespace.</span></span> <span data-ttu-id="014f9-108">Například následující prohlášení odkazuje `TestApp` jako člen globálního místa.</span><span class="sxs-lookup"><span data-stu-id="014f9-108">For example, the following declaration is referencing `TestApp` as a member of the global space.</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#4](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/how-to-use-the-global-namespace-alias_5.cs)]  
  
 <span data-ttu-id="014f9-109">Vytvoření vlastní obory názvů samozřejmě nazývané `System` se nedoporučuje, a pravděpodobně narazíte na kód, ve kterém byla odepřena.</span><span class="sxs-lookup"><span data-stu-id="014f9-109">Obviously, creating your own namespaces called `System` is not recommended, and it is unlikely you will encounter any code in which this has happened.</span></span> <span data-ttu-id="014f9-110">V projektech větší, je však velmi reálná možnost, že duplikace oboru názvů, může dojít v jednoho formuláře nebo jiné.</span><span class="sxs-lookup"><span data-stu-id="014f9-110">However, in larger projects, it is a very real possibility that namespace duplication may occur in one form or another.</span></span> <span data-ttu-id="014f9-111">V těchto situacích kvalifikátor globálního oboru názvů je vaše záruku, že je možné zadat kořenového oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="014f9-111">In these situations, the global namespace qualifier is your guarantee that you can specify the root namespace.</span></span>  
  
## <a name="example"></a><span data-ttu-id="014f9-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="014f9-112">Example</span></span>  
 <span data-ttu-id="014f9-113">V tomto příkladu, obor názvů `System` se používá k obsahují třídu `TestClass` proto `global::System.Console` se musí použít k odkazu `System.Console` třídy, která je skrytý na základě `System` oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="014f9-113">In this example, the namespace `System` is used to include the class `TestClass` therefore, `global::System.Console` must be used to reference the `System.Console` class, which is hidden by the `System` namespace.</span></span> <span data-ttu-id="014f9-114">Navíc alias `colAlias` slouží k odkazování na obor názvů `System.Collections`; proto instanci <xref:System.Collections.Hashtable?displayProperty=nameWithType> byla vytvořena pomocí tento alias místo obor názvů.</span><span class="sxs-lookup"><span data-stu-id="014f9-114">Also, the alias `colAlias` is used to refer to the namespace `System.Collections`; therefore, the instance of a <xref:System.Collections.Hashtable?displayProperty=nameWithType> was created using this alias instead of the namespace.</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#5](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/how-to-use-the-global-namespace-alias_6.cs)]  
  
 <span data-ttu-id="014f9-115">**1**</span><span class="sxs-lookup"><span data-stu-id="014f9-115">**A 1**</span></span>  
<span data-ttu-id="014f9-116">**B 2**</span><span class="sxs-lookup"><span data-stu-id="014f9-116">**B 2**</span></span>  
<span data-ttu-id="014f9-117">**C 3**</span><span class="sxs-lookup"><span data-stu-id="014f9-117">**C 3**</span></span>   
## <a name="see-also"></a><span data-ttu-id="014f9-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="014f9-118">See Also</span></span>  
 [<span data-ttu-id="014f9-119">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="014f9-119">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="014f9-120">Obory názvů</span><span class="sxs-lookup"><span data-stu-id="014f9-120">Namespaces</span></span>](../../../csharp/programming-guide/namespaces/index.md)  
 [<span data-ttu-id="014f9-121">. – operátor</span><span class="sxs-lookup"><span data-stu-id="014f9-121">. Operator</span></span>](../../../csharp/language-reference/operators/member-access-operator.md)  
 [<span data-ttu-id="014f9-122">:: – operátor</span><span class="sxs-lookup"><span data-stu-id="014f9-122">:: Operator</span></span>](../../../csharp/language-reference/operators/namespace-alias-qualifer.md)  
 [<span data-ttu-id="014f9-123">extern</span><span class="sxs-lookup"><span data-stu-id="014f9-123">extern</span></span>](../../../csharp/language-reference/keywords/extern.md)
