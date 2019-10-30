---
title: ':: operator- C# reference'
ms.custom: seodec18
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
ms.openlocfilehash: 97ed24b050f79cf44ffd1c03c213ffcf91758260
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/29/2019
ms.locfileid: "73038982"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="1d660-102">:: – operátorC# (Referenční dokumentace)</span><span class="sxs-lookup"><span data-stu-id="1d660-102">:: operator (C# reference)</span></span>

<span data-ttu-id="1d660-103">Pro přístup ke členu oboru názvů s aliasem použijte Kvalifikátor aliasu oboru názvů `::`.</span><span class="sxs-lookup"><span data-stu-id="1d660-103">Use the namespace alias qualifier `::` to access a member of an aliased namespace.</span></span> <span data-ttu-id="1d660-104">Kvalifikátor `::` můžete použít jenom mezi dvěma identifikátory.</span><span class="sxs-lookup"><span data-stu-id="1d660-104">You can use the `::` qualifier only between two identifiers.</span></span> <span data-ttu-id="1d660-105">Levý identifikátor může být libovolný z následujících aliasů:</span><span class="sxs-lookup"><span data-stu-id="1d660-105">The left-hand identifier can be any of the following aliases:</span></span>

- <span data-ttu-id="1d660-106">Alias oboru názvů vytvořený pomocí [direktivy aliasu using](../keywords/using-directive.md):</span><span class="sxs-lookup"><span data-stu-id="1d660-106">A namespace alias created with a [using alias directive](../keywords/using-directive.md):</span></span>

  ```csharp
  using forwinforms = System.Drawing;
  using forwpf = System.Windows;
  
  public class Converters
  {
      public static forwpf::Point Convert(forwinforms::Point point) => new forwpf::Point(point.X, point.Y);
  }
  ```

- <span data-ttu-id="1d660-107">[Externí alias](../keywords/extern-alias.md).</span><span class="sxs-lookup"><span data-stu-id="1d660-107">An [extern alias](../keywords/extern-alias.md).</span></span>
- <span data-ttu-id="1d660-108">Alias `global`, který je globálním aliasem oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="1d660-108">The `global` alias, which is the global namespace alias.</span></span> <span data-ttu-id="1d660-109">Globální obor názvů je obor názvů, který obsahuje obory názvů a typy, které nejsou deklarovány uvnitř pojmenovaného oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="1d660-109">The global namespace is the namespace that contains namespaces and types that are not declared inside a named namespace.</span></span> <span data-ttu-id="1d660-110">Při použití s kvalifikátorem `::` se alias `global` vždycky odkazuje na globální obor názvů, a to i v případě, že je k dispozici uživatelsky definovaný `global` alias oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="1d660-110">When used with the `::` qualifier, the `global` alias always references the global namespace, even if there is the user-defined `global` namespace alias.</span></span>

  <span data-ttu-id="1d660-111">Následující příklad používá alias `global` pro přístup k oboru názvů .NET <xref:System>, který je členem globálního oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="1d660-111">The following example uses the `global` alias to access the .NET <xref:System> namespace, which is a member of the global namespace.</span></span> <span data-ttu-id="1d660-112">Bez aliasu `global` by byl k dispozici uživatelsky definovaný `System` obor názvů, který je členem `MyCompany.MyProduct` oboru názvů:</span><span class="sxs-lookup"><span data-stu-id="1d660-112">Without the `global` alias, the user-defined `System` namespace, which is a member of the `MyCompany.MyProduct` namespace, would be accessed:</span></span>

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
  > <span data-ttu-id="1d660-113">Klíčové slovo `global` je globální alias oboru názvů pouze v případě, že se jedná o identifikátor pravého kvalifikátoru `::`.</span><span class="sxs-lookup"><span data-stu-id="1d660-113">The `global` keyword is the global namespace alias only when it's the left-hand identifier of the `::` qualifier.</span></span>

<span data-ttu-id="1d660-114">Pro přístup ke členu oboru názvů s aliasem můžete také použít [operátor přístupu členů `.`](member-access-operators.md#member-access-operator-) .</span><span class="sxs-lookup"><span data-stu-id="1d660-114">You can also use the [member access `.` operator](member-access-operators.md#member-access-operator-) to access a member of an aliased namespace.</span></span> <span data-ttu-id="1d660-115">Nicméně operátor `.` slouží také pro přístup k členu typu.</span><span class="sxs-lookup"><span data-stu-id="1d660-115">However, the `.` operator is also used to access a type member.</span></span> <span data-ttu-id="1d660-116">Kvalifikátor `::` zajišťuje, že jeho levý identifikátor vždy odkazuje na alias oboru názvů, i když existuje typ nebo obor názvů se stejným názvem.</span><span class="sxs-lookup"><span data-stu-id="1d660-116">The `::` qualifier ensures that its left-hand identifier always references a namespace alias, even if there exists a type or namespace with the same name.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="1d660-117">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="1d660-117">C# language specification</span></span>

<span data-ttu-id="1d660-118">Další informace najdete v části [kvalifikátory aliasu oboru názvů](~/_csharplang/spec/namespaces.md#namespace-alias-qualifiers) ve [ C# specifikaci jazyka](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="1d660-118">For more information, see the [Namespace alias qualifiers](~/_csharplang/spec/namespaces.md#namespace-alias-qualifiers) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="1d660-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1d660-119">See also</span></span>

- [<span data-ttu-id="1d660-120">C#odkaz</span><span class="sxs-lookup"><span data-stu-id="1d660-120">C# reference</span></span>](../index.md)
- [<span data-ttu-id="1d660-121">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="1d660-121">C# operators</span></span>](index.md)
- [<span data-ttu-id="1d660-122">Používání oborů názvů</span><span class="sxs-lookup"><span data-stu-id="1d660-122">Using namespaces</span></span>](../../programming-guide/namespaces/using-namespaces.md)
