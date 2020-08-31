---
description: ':: operator-reference jazyka C#'
title: ':: operator-reference jazyka C#'
ms.date: 08/09/2019
f1_keywords:
- ::_CSharpKeyword
- global_CSharpKeyword
- global
helpviewer_keywords:
- ':: operator [C#]'
- namespace alias qualifier [C#]
- namespace [C#]
- global keyword [C#]
ms.assetid: 698b5a73-85cf-4e0e-9e8e-6496887f8527
ms.openlocfilehash: 6c901ce083dde6f2e28520fafe3313071ae792c8
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89118322"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="8aced-103">:: operator (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="8aced-103">:: operator (C# reference)</span></span>

<span data-ttu-id="8aced-104">`::`Pro přístup ke členu oboru názvů s aliasem použijte Kvalifikátor aliasu oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="8aced-104">Use the namespace alias qualifier `::` to access a member of an aliased namespace.</span></span> <span data-ttu-id="8aced-105">Kvalifikátor můžete použít `::` jenom mezi dvěma identifikátory.</span><span class="sxs-lookup"><span data-stu-id="8aced-105">You can use the `::` qualifier only between two identifiers.</span></span> <span data-ttu-id="8aced-106">Levý identifikátor může být libovolný z následujících aliasů:</span><span class="sxs-lookup"><span data-stu-id="8aced-106">The left-hand identifier can be any of the following aliases:</span></span>

- <span data-ttu-id="8aced-107">Alias oboru názvů vytvořený pomocí [direktivy aliasu using](../keywords/using-directive.md):</span><span class="sxs-lookup"><span data-stu-id="8aced-107">A namespace alias created with a [using alias directive](../keywords/using-directive.md):</span></span>

  ```csharp
  using forwinforms = System.Drawing;
  using forwpf = System.Windows;
  
  public class Converters
  {
      public static forwpf::Point Convert(forwinforms::Point point) => new forwpf::Point(point.X, point.Y);
  }
  ```

- <span data-ttu-id="8aced-108">[Externí alias](../keywords/extern-alias.md).</span><span class="sxs-lookup"><span data-stu-id="8aced-108">An [extern alias](../keywords/extern-alias.md).</span></span>
- <span data-ttu-id="8aced-109">`global`Alias, který je globálním aliasem oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="8aced-109">The `global` alias, which is the global namespace alias.</span></span> <span data-ttu-id="8aced-110">Globální obor názvů je obor názvů, který obsahuje obory názvů a typy, které nejsou deklarovány uvnitř pojmenovaného oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="8aced-110">The global namespace is the namespace that contains namespaces and types that are not declared inside a named namespace.</span></span> <span data-ttu-id="8aced-111">Při použití s `::` kvalifikátorem se `global` alias vždycky odkazuje na globální obor názvů, a to i v případě, že je k dispozici uživatelsky definovaný `global` alias oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="8aced-111">When used with the `::` qualifier, the `global` alias always references the global namespace, even if there is the user-defined `global` namespace alias.</span></span>

  <span data-ttu-id="8aced-112">Následující příklad používá `global` alias pro přístup k <xref:System> oboru názvů .NET, který je členem globálního oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="8aced-112">The following example uses the `global` alias to access the .NET <xref:System> namespace, which is a member of the global namespace.</span></span> <span data-ttu-id="8aced-113">Bez `global` aliasu `System` by byl k dispozici uživatelsky definovaný obor názvů, který je členem `MyCompany.MyProduct` oboru názvů:</span><span class="sxs-lookup"><span data-stu-id="8aced-113">Without the `global` alias, the user-defined `System` namespace, which is a member of the `MyCompany.MyProduct` namespace, would be accessed:</span></span>

  ```csharp
  namespace MyCompany.MyProduct.System
  {
      class Program
      {
          static void Main() => global::System.Console.WriteLine("Using global alias");
      }

      class Console
      {
          string Suggestion => "Consider renaming this class";
      }
  }
  ```

  > [!NOTE]
  > <span data-ttu-id="8aced-114">`global`Klíčové slovo je globální alias oboru názvů pouze v případě, že se jedná o identifikátor pravého `::` kvalifikátoru.</span><span class="sxs-lookup"><span data-stu-id="8aced-114">The `global` keyword is the global namespace alias only when it's the left-hand identifier of the `::` qualifier.</span></span>

<span data-ttu-id="8aced-115">[ `.` Token](member-access-operators.md#member-access-expression-) můžete použít také pro přístup ke členu oboru názvů s aliasem.</span><span class="sxs-lookup"><span data-stu-id="8aced-115">You can also use the [`.` token](member-access-operators.md#member-access-expression-) to access a member of an aliased namespace.</span></span> <span data-ttu-id="8aced-116">`.`Token se však používá také pro přístup k členu typu.</span><span class="sxs-lookup"><span data-stu-id="8aced-116">However, the `.` token is also used to access a type member.</span></span> <span data-ttu-id="8aced-117">`::`Kvalifikátor zajišťuje, že jeho levý identifikátor vždy odkazuje na alias oboru názvů, a to i v případě, že existuje typ nebo obor názvů se stejným názvem.</span><span class="sxs-lookup"><span data-stu-id="8aced-117">The `::` qualifier ensures that its left-hand identifier always references a namespace alias, even if there exists a type or namespace with the same name.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="8aced-118">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="8aced-118">C# language specification</span></span>

<span data-ttu-id="8aced-119">Další informace najdete v části [kvalifikátory aliasu oboru názvů](~/_csharplang/spec/namespaces.md#namespace-alias-qualifiers) v tématu [specifikace jazyka C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="8aced-119">For more information, see the [Namespace alias qualifiers](~/_csharplang/spec/namespaces.md#namespace-alias-qualifiers) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="8aced-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="8aced-120">See also</span></span>

- [<span data-ttu-id="8aced-121">Referenční dokumentace k jazyku C#</span><span class="sxs-lookup"><span data-stu-id="8aced-121">C# reference</span></span>](../index.md)
- [<span data-ttu-id="8aced-122">Operátory a výrazy v C#</span><span class="sxs-lookup"><span data-stu-id="8aced-122">C# operators and expressions</span></span>](index.md)
- [<span data-ttu-id="8aced-123">Používání oboru názvů</span><span class="sxs-lookup"><span data-stu-id="8aced-123">Using namespaces</span></span>](../../programming-guide/namespaces/using-namespaces.md)
