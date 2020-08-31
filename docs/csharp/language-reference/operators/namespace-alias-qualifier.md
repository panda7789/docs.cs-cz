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
# <a name="-operator-c-reference"></a>:: operator (Referenční dokumentace jazyka C#)

`::`Pro přístup ke členu oboru názvů s aliasem použijte Kvalifikátor aliasu oboru názvů. Kvalifikátor můžete použít `::` jenom mezi dvěma identifikátory. Levý identifikátor může být libovolný z následujících aliasů:

- Alias oboru názvů vytvořený pomocí [direktivy aliasu using](../keywords/using-directive.md):

  ```csharp
  using forwinforms = System.Drawing;
  using forwpf = System.Windows;
  
  public class Converters
  {
      public static forwpf::Point Convert(forwinforms::Point point) => new forwpf::Point(point.X, point.Y);
  }
  ```

- [Externí alias](../keywords/extern-alias.md).
- `global`Alias, který je globálním aliasem oboru názvů. Globální obor názvů je obor názvů, který obsahuje obory názvů a typy, které nejsou deklarovány uvnitř pojmenovaného oboru názvů. Při použití s `::` kvalifikátorem se `global` alias vždycky odkazuje na globální obor názvů, a to i v případě, že je k dispozici uživatelsky definovaný `global` alias oboru názvů.

  Následující příklad používá `global` alias pro přístup k <xref:System> oboru názvů .NET, který je členem globálního oboru názvů. Bez `global` aliasu `System` by byl k dispozici uživatelsky definovaný obor názvů, který je členem `MyCompany.MyProduct` oboru názvů:

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
  > `global`Klíčové slovo je globální alias oboru názvů pouze v případě, že se jedná o identifikátor pravého `::` kvalifikátoru.

[ `.` Token](member-access-operators.md#member-access-expression-) můžete použít také pro přístup ke členu oboru názvů s aliasem. `.`Token se však používá také pro přístup k členu typu. `::`Kvalifikátor zajišťuje, že jeho levý identifikátor vždy odkazuje na alias oboru názvů, a to i v případě, že existuje typ nebo obor názvů se stejným názvem.

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace najdete v části [kvalifikátory aliasu oboru názvů](~/_csharplang/spec/namespaces.md#namespace-alias-qualifiers) v tématu [specifikace jazyka C#](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Viz také

- [Referenční dokumentace k jazyku C#](../index.md)
- [Operátory a výrazy v C#](index.md)
- [Používání oboru názvů](../../programming-guide/namespaces/using-namespaces.md)
