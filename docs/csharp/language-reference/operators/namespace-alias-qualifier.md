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
ms.openlocfilehash: 2aceb51747708b12fb3059b097b72206c78a9d5d
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/13/2019
ms.locfileid: "68971246"
---
# <a name="-operator-c-reference"></a>:: – operátorC# (Referenční dokumentace)

`::` Pro přístup ke členům oboru názvů s aliasy použijte Kvalifikátor aliasu oboru názvů. `::` Kvalifikátor můžete použít mezi dvěma identifikátory. Levý identifikátor může být libovolný z následujících aliasů:

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
- `global` Alias, který je globálním aliasem oboru názvů. Globální obor názvů je obor názvů, který obsahuje obory názvů a typy, které nejsou deklarovány uvnitř pojmenovaného oboru názvů. Při použití s `::` kvalifikátorem `global` se alias vždycky odkazuje na globální obor názvů, a to i v případě, že je k `global` dispozici uživatelsky definovaný alias oboru názvů.
  
  Následující příklad používá `global` alias pro přístup k oboru názvů .NET <xref:System> , který je členem globálního oboru názvů. Bez aliasu by byl k dispozici `System` uživatelsky definovaný obor názvů, který `MyCompany.MyProduct` je členem oboru názvů: `global`

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
  > Klíčové slovo je globální alias oboru názvů pouze v případě, že se jedná o identifikátor `::` pravého kvalifikátoru. `global`

Můžete také použít [ `.` operátor přístupu členů](member-access-operators.md#member-access-operator-) pro přístup ke členům oboru názvů s aliasem. `.` Nicméně operátor se používá také pro přístup k členům typu. `::` Kvalifikátor zajišťuje, že jeho levý identifikátor vždy odkazuje na alias oboru názvů, a to i v případě, že existuje typ nebo obor názvů se stejným názvem.

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace najdete v části [kvalifikátory aliasu oboru názvů](~/_csharplang/spec/namespaces.md#namespace-alias-qualifiers) ve [ C# specifikaci jazyka](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Viz také:

- [C#odkaz](../index.md)
- [Operátory jazyka C#](index.md)
- [Používání oborů názvů](../../programming-guide/namespaces/using-namespaces.md)
