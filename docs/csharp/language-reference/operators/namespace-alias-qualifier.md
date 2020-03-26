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
# <a name="-operator-c-reference"></a>:: operátor (odkaz C#)

Kvalifikátor `::` aliasu oboru názvů použijte pro přístup k členovi aliasového oboru názvů. `::` Kvalifikátor lze použít pouze mezi dvěma identifikátory. Identifikátor levé ruky může být libovolný z následujících aliasů:

- Alias oboru názvů vytvořený [direktivou using alias](../keywords/using-directive.md):

  ```csharp
  using forwinforms = System.Drawing;
  using forwpf = System.Windows;
  
  public class Converters
  {
      public static forwpf::Point Convert(forwinforms::Point point) => new forwpf::Point(point.X, point.Y);
  }
  ```

- [Extern alias](../keywords/extern-alias.md).
- Alias, `global` což je globální alias oboru názvů. Globální obor názvů je obor názvů, který obsahuje obory názvů a typy, které nejsou deklarovány uvnitř pojmenovaného oboru názvů. Při použití `::` s kvalifikátorem `global` alias vždy odkazuje na globální obor `global` názvů, i když existuje uživatelem definovaný alias oboru názvů.

  Následující příklad používá `global` alias pro přístup <xref:System> k oboru názvů .NET, který je členem globálního oboru názvů. Bez `global` aliasu by byl `System` přístup k uživatelem definovanému oboru názvů, který je členem oboru `MyCompany.MyProduct` názvů:

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
  > Klíčové `global` slovo je alias globálního oboru názvů pouze v případě, `::` že se jedná o identifikátor kvalifikátoru na levostranné straně.

Token můžete také použít pro přístup k členu aliasovaného oboru názvů. [ `.` ](member-access-operators.md#member-access-expression-) Token se `.` však také používá pro přístup k členu typu. Kvalifikátor `::` zajišťuje, že jeho levý identifikátor vždy odkazuje na alias oboru názvů, i když existuje typ nebo obor názvů se stejným názvem.

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace naleznete v části [Kvalifikátory aliasu oboru názvů](~/_csharplang/spec/namespaces.md#namespace-alias-qualifiers) ve [specifikaci jazyka C#](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Viz také

- [Referenční dokumentace k jazyku C#](../index.md)
- [Operátory jazyka C#](index.md)
- [Používání oboru názvů](../../programming-guide/namespaces/using-namespaces.md)
