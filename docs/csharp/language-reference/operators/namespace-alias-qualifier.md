---
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
ms.openlocfilehash: f91287ed281a2c6b10bed93cff10b08972a8445e
ms.sourcegitcommit: c37e8d4642fef647ebab0e1c618ecc29ddfe2a0f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/06/2020
ms.locfileid: "87855124"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="ab9ad-102">:: operator (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="ab9ad-102">:: operator (C# reference)</span></span>

<span data-ttu-id="ab9ad-103">`::`Pro přístup ke členu oboru názvů s aliasem použijte Kvalifikátor aliasu oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="ab9ad-103">Use the namespace alias qualifier `::` to access a member of an aliased namespace.</span></span> <span data-ttu-id="ab9ad-104">Kvalifikátor můžete použít `::` jenom mezi dvěma identifikátory.</span><span class="sxs-lookup"><span data-stu-id="ab9ad-104">You can use the `::` qualifier only between two identifiers.</span></span> <span data-ttu-id="ab9ad-105">Levý identifikátor může být libovolný z následujících aliasů:</span><span class="sxs-lookup"><span data-stu-id="ab9ad-105">The left-hand identifier can be any of the following aliases:</span></span>

- <span data-ttu-id="ab9ad-106">Alias oboru názvů vytvořený pomocí [direktivy aliasu using](../keywords/using-directive.md):</span><span class="sxs-lookup"><span data-stu-id="ab9ad-106">A namespace alias created with a [using alias directive](../keywords/using-directive.md):</span></span>

  ```csharp
  using forwinforms = System.Drawing;
  using forwpf = System.Windows;
  
  public class Converters
  {
      public static forwpf::Point Convert(forwinforms::Point point) => new forwpf::Point(point.X, point.Y);
  }
  ```

- <span data-ttu-id="ab9ad-107">[Externí alias](../keywords/extern-alias.md).</span><span class="sxs-lookup"><span data-stu-id="ab9ad-107">An [extern alias](../keywords/extern-alias.md).</span></span>
- <span data-ttu-id="ab9ad-108">`global`Alias, který je globálním aliasem oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="ab9ad-108">The `global` alias, which is the global namespace alias.</span></span> <span data-ttu-id="ab9ad-109">Globální obor názvů je obor názvů, který obsahuje obory názvů a typy, které nejsou deklarovány uvnitř pojmenovaného oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="ab9ad-109">The global namespace is the namespace that contains namespaces and types that are not declared inside a named namespace.</span></span> <span data-ttu-id="ab9ad-110">Při použití s `::` kvalifikátorem se `global` alias vždycky odkazuje na globální obor názvů, a to i v případě, že je k dispozici uživatelsky definovaný `global` alias oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="ab9ad-110">When used with the `::` qualifier, the `global` alias always references the global namespace, even if there is the user-defined `global` namespace alias.</span></span>

  <span data-ttu-id="ab9ad-111">Následující příklad používá `global` alias pro přístup k <xref:System> oboru názvů .NET, který je členem globálního oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="ab9ad-111">The following example uses the `global` alias to access the .NET <xref:System> namespace, which is a member of the global namespace.</span></span> <span data-ttu-id="ab9ad-112">Bez `global` aliasu `System` by byl k dispozici uživatelsky definovaný obor názvů, který je členem `MyCompany.MyProduct` oboru názvů:</span><span class="sxs-lookup"><span data-stu-id="ab9ad-112">Without the `global` alias, the user-defined `System` namespace, which is a member of the `MyCompany.MyProduct` namespace, would be accessed:</span></span>

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
  > <span data-ttu-id="ab9ad-113">`global`Klíčové slovo je globální alias oboru názvů pouze v případě, že se jedná o identifikátor pravého `::` kvalifikátoru.</span><span class="sxs-lookup"><span data-stu-id="ab9ad-113">The `global` keyword is the global namespace alias only when it's the left-hand identifier of the `::` qualifier.</span></span>

<span data-ttu-id="ab9ad-114">[ `.` Token](member-access-operators.md#member-access-expression-) můžete použít také pro přístup ke členu oboru názvů s aliasem.</span><span class="sxs-lookup"><span data-stu-id="ab9ad-114">You can also use the [`.` token](member-access-operators.md#member-access-expression-) to access a member of an aliased namespace.</span></span> <span data-ttu-id="ab9ad-115">`.`Token se však používá také pro přístup k členu typu.</span><span class="sxs-lookup"><span data-stu-id="ab9ad-115">However, the `.` token is also used to access a type member.</span></span> <span data-ttu-id="ab9ad-116">`::`Kvalifikátor zajišťuje, že jeho levý identifikátor vždy odkazuje na alias oboru názvů, a to i v případě, že existuje typ nebo obor názvů se stejným názvem.</span><span class="sxs-lookup"><span data-stu-id="ab9ad-116">The `::` qualifier ensures that its left-hand identifier always references a namespace alias, even if there exists a type or namespace with the same name.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="ab9ad-117">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="ab9ad-117">C# language specification</span></span>

<span data-ttu-id="ab9ad-118">Další informace najdete v části [kvalifikátory aliasu oboru názvů](~/_csharplang/spec/namespaces.md#namespace-alias-qualifiers) v tématu [specifikace jazyka C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="ab9ad-118">For more information, see the [Namespace alias qualifiers](~/_csharplang/spec/namespaces.md#namespace-alias-qualifiers) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="ab9ad-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="ab9ad-119">See also</span></span>

- [<span data-ttu-id="ab9ad-120">Referenční dokumentace k jazyku C#</span><span class="sxs-lookup"><span data-stu-id="ab9ad-120">C# reference</span></span>](../index.md)
- [<span data-ttu-id="ab9ad-121">Operátory a výrazy v C#</span><span class="sxs-lookup"><span data-stu-id="ab9ad-121">C# operators and expressions</span></span>](index.md)
- [<span data-ttu-id="ab9ad-122">Používání oboru názvů</span><span class="sxs-lookup"><span data-stu-id="ab9ad-122">Using namespaces</span></span>](../../programming-guide/namespaces/using-namespaces.md)
