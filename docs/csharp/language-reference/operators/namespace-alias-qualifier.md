---
title: ':: operator- C# reference'
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
ms.openlocfilehash: a18e52ea05d49bf2b3a468923f1433f09fff9a8b
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75712673"
---
# <a name="-operator-c-reference"></a>:: – operátorC# (Referenční dokumentace)

Pro přístup ke členu oboru názvů s aliasem použijte Kvalifikátor aliasu oboru názvů `::`. Kvalifikátor `::` můžete použít jenom mezi dvěma identifikátory. Levý identifikátor může být libovolný z následujících aliasů:

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
- Alias `global`, který je globálním aliasem oboru názvů. Globální obor názvů je obor názvů, který obsahuje obory názvů a typy, které nejsou deklarovány uvnitř pojmenovaného oboru názvů. Při použití s kvalifikátorem `::` se alias `global` vždycky odkazuje na globální obor názvů, a to i v případě, že je k dispozici uživatelsky definovaný `global` alias oboru názvů.

  Následující příklad používá alias `global` pro přístup k oboru názvů .NET <xref:System>, který je členem globálního oboru názvů. Bez aliasu `global` by byl k dispozici uživatelsky definovaný `System` obor názvů, který je členem `MyCompany.MyProduct` oboru názvů:

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
  > Klíčové slovo `global` je globální alias oboru názvů pouze v případě, že se jedná o identifikátor pravého kvalifikátoru `::`.

Pro přístup ke členu oboru názvů s aliasem můžete také použít [operátor přístupu členů `.`](member-access-operators.md#member-access-operator-) . Nicméně operátor `.` slouží také pro přístup k členu typu. Kvalifikátor `::` zajišťuje, že jeho levý identifikátor vždy odkazuje na alias oboru názvů, i když existuje typ nebo obor názvů se stejným názvem.

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace najdete v části [kvalifikátory aliasu oboru názvů](~/_csharplang/spec/namespaces.md#namespace-alias-qualifiers) ve [ C# specifikaci jazyka](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Viz také:

- [C#odkaz](../index.md)
- [Operátory jazyka C#](index.md)
- [Používání oborů názvů](../../programming-guide/namespaces/using-namespaces.md)
