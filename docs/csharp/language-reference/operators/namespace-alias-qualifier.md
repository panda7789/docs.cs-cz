---
title: ':: operátor - C# odkaz'
ms.date: 08/09/2019
f1_keywords:
- ::_CSharpKeyword
- global_CSharpKeyword
helpviewer_keywords:
- ':: operator [C#]'
- namespace alias qualifier [C#]
- namespace [C#]
- global keyword [C#]
ms.assetid: 698b5a73-85cf-4e0e-9e8e-6496887f8527
ms.openlocfilehash: 84c418627462f83630fe5072a0b0e2089f6588f6
ms.sourcegitcommit: 2514f4e3655081dcfe1b22470c0c28500f952c42
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "79507123"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="350cd-102">:: operátor (odkaz C#)</span><span class="sxs-lookup"><span data-stu-id="350cd-102">:: operator (C# reference)</span></span>

<span data-ttu-id="350cd-103">Kvalifikátor `::` aliasu oboru názvů použijte pro přístup k členovi aliasového oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="350cd-103">Use the namespace alias qualifier `::` to access a member of an aliased namespace.</span></span> <span data-ttu-id="350cd-104">`::` Kvalifikátor lze použít pouze mezi dvěma identifikátory.</span><span class="sxs-lookup"><span data-stu-id="350cd-104">You can use the `::` qualifier only between two identifiers.</span></span> <span data-ttu-id="350cd-105">Identifikátor levé ruky může být libovolný z následujících aliasů:</span><span class="sxs-lookup"><span data-stu-id="350cd-105">The left-hand identifier can be any of the following aliases:</span></span>

- <span data-ttu-id="350cd-106">Alias oboru názvů vytvořený [direktivou using alias](../keywords/using-directive.md):</span><span class="sxs-lookup"><span data-stu-id="350cd-106">A namespace alias created with a [using alias directive](../keywords/using-directive.md):</span></span>

  ```csharp
  using forwinforms = System.Drawing;
  using forwpf = System.Windows;
  
  public class Converters
  {
      public static forwpf::Point Convert(forwinforms::Point point) => new forwpf::Point(point.X, point.Y);
  }
  ```

- <span data-ttu-id="350cd-107">[Extern alias](../keywords/extern-alias.md).</span><span class="sxs-lookup"><span data-stu-id="350cd-107">An [extern alias](../keywords/extern-alias.md).</span></span>
- <span data-ttu-id="350cd-108">Alias, `global` což je globální alias oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="350cd-108">The `global` alias, which is the global namespace alias.</span></span> <span data-ttu-id="350cd-109">Globální obor názvů je obor názvů, který obsahuje obory názvů a typy, které nejsou deklarovány uvnitř pojmenovaného oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="350cd-109">The global namespace is the namespace that contains namespaces and types that are not declared inside a named namespace.</span></span> <span data-ttu-id="350cd-110">Při použití `::` s kvalifikátorem `global` alias vždy odkazuje na globální obor `global` názvů, i když existuje uživatelem definovaný alias oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="350cd-110">When used with the `::` qualifier, the `global` alias always references the global namespace, even if there is the user-defined `global` namespace alias.</span></span>

  <span data-ttu-id="350cd-111">Následující příklad používá `global` alias pro přístup <xref:System> k oboru názvů .NET, který je členem globálního oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="350cd-111">The following example uses the `global` alias to access the .NET <xref:System> namespace, which is a member of the global namespace.</span></span> <span data-ttu-id="350cd-112">Bez `global` aliasu by byl `System` přístup k uživatelem definovanému oboru názvů, který je členem oboru `MyCompany.MyProduct` názvů:</span><span class="sxs-lookup"><span data-stu-id="350cd-112">Without the `global` alias, the user-defined `System` namespace, which is a member of the `MyCompany.MyProduct` namespace, would be accessed:</span></span>

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
  > <span data-ttu-id="350cd-113">Klíčové `global` slovo je alias globálního oboru názvů pouze v případě, `::` že se jedná o identifikátor kvalifikátoru na levostranné straně.</span><span class="sxs-lookup"><span data-stu-id="350cd-113">The `global` keyword is the global namespace alias only when it's the left-hand identifier of the `::` qualifier.</span></span>

<span data-ttu-id="350cd-114">Token můžete také použít pro přístup k členu aliasovaného oboru názvů. [ `.` ](member-access-operators.md#member-access-expression-)</span><span class="sxs-lookup"><span data-stu-id="350cd-114">You can also use the [`.` token](member-access-operators.md#member-access-expression-) to access a member of an aliased namespace.</span></span> <span data-ttu-id="350cd-115">Token se `.` však také používá pro přístup k členu typu.</span><span class="sxs-lookup"><span data-stu-id="350cd-115">However, the `.` token is also used to access a type member.</span></span> <span data-ttu-id="350cd-116">Kvalifikátor `::` zajišťuje, že jeho levý identifikátor vždy odkazuje na alias oboru názvů, i když existuje typ nebo obor názvů se stejným názvem.</span><span class="sxs-lookup"><span data-stu-id="350cd-116">The `::` qualifier ensures that its left-hand identifier always references a namespace alias, even if there exists a type or namespace with the same name.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="350cd-117">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="350cd-117">C# language specification</span></span>

<span data-ttu-id="350cd-118">Další informace naleznete v části [Kvalifikátory aliasu oboru názvů](~/_csharplang/spec/namespaces.md#namespace-alias-qualifiers) ve [specifikaci jazyka C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="350cd-118">For more information, see the [Namespace alias qualifiers](~/_csharplang/spec/namespaces.md#namespace-alias-qualifiers) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="350cd-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="350cd-119">See also</span></span>

- [<span data-ttu-id="350cd-120">Referenční dokumentace k jazyku C#</span><span class="sxs-lookup"><span data-stu-id="350cd-120">C# reference</span></span>](../index.md)
- [<span data-ttu-id="350cd-121">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="350cd-121">C# operators</span></span>](index.md)
- [<span data-ttu-id="350cd-122">Používání oboru názvů</span><span class="sxs-lookup"><span data-stu-id="350cd-122">Using namespaces</span></span>](../../programming-guide/namespaces/using-namespaces.md)
