---
title: interní C# odkaz
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- internal_CSharpKeyword
- internal
helpviewer_keywords:
- internal keyword [C#]
ms.assetid: 6ee0785c-d7c8-49b8-bb72-0a4dfbcb6461
ms.openlocfilehash: 7d97b7b05645b02a31af848c97758c7a1f6423b9
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69602084"
---
# <a name="internal-c-reference"></a>internal (Referenční dokumentace jazyka C#)
Klíčové slovo je [modifikátor přístupu](./access-modifiers.md) pro typy a členy typů. `internal` 
  
 > Tato stránka se `internal` zabývá přístupem. Klíčové slovo je také součástí [`protected internal`](./protected-internal.md) modifikátoru přístupu. `internal`
  
Interní typy nebo členy jsou přístupné pouze v rámci souborů ve stejném sestavení, jako v tomto příkladu:  
  
```csharp  
public class BaseClass   
{  
    // Only accessible within the same assembly.
    internal static int x = 0;
}  
```  

 Porovnání `internal` s dalšími modifikátory přístupu najdete v tématu [úrovně](./accessibility-levels.md) přístupnosti a [modifikátory přístupu](../../programming-guide/classes-and-structs/access-modifiers.md).  
  
 Další informace o sestaveních naleznete [v tématu sestavení v rozhraní .NET](../../../standard/assembly/index.md).  
  
 Běžné použití interního přístupu je v rámci vývoje založeného na komponentách, protože umožňuje skupině komponent, aby spolupracovaly soukromě, aniž by bylo zveřejněno pro zbytek kódu aplikace. Například architektura pro sestavování grafického uživatelského rozhraní může poskytovat `Control` a `Form` třídy, které spolupracují pomocí členů s interním přístupem. Vzhledem k tomu, že jsou tyto členy interní, nejsou vystaveny kódu, který používá rozhraní.  
  
 Jedná se o chybu, která odkazuje na typ nebo člen s vnitřním přístupem mimo sestavení, ve kterém byla definována.  
  
## <a name="example"></a>Příklad  
 Tento příklad obsahuje dva soubory, `Assembly1.cs` a `Assembly1_a.cs`. První soubor obsahuje interní základní třídu `BaseClass`. Při pokusu o vytvoření instance `BaseClass` v druhém souboru dojde k chybě.  
  
```csharp  
// Assembly1.cs  
// Compile with: /target:library  
internal class BaseClass   
{  
   public static int intM = 0;  
}  
```  
  
```csharp  
// Assembly1_a.cs  
// Compile with: /reference:Assembly1.dll  
class TestAccess   
{  
   static void Main()   
   {  
      var myBase = new BaseClass();   // CS0122  
   }  
}  
```  
  
## <a name="example"></a>Příklad  
 V tomto příkladu použijte stejné soubory, které jste použili v příkladu 1, a změňte úroveň `BaseClass` přístupnosti na. `public` Změňte také úroveň přístupnosti člena `intM` na. `internal` V takovém případě můžete vytvořit instanci třídy, ale nemůžete získat přístup k internímu členu.  
  
```csharp  
// Assembly2.cs  
// Compile with: /target:library  
public class BaseClass   
{  
   internal static int intM = 0;  
}  
```  
  
```csharp  
// Assembly2_a.cs  
// Compile with: /reference:Assembly2.dll  
public class TestAccess   
{  
   static void Main()   
   {  
      var myBase = new BaseClass();   // Ok.  
      BaseClass.intM = 444;    // CS0117  
   }  
}  
```  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  

Další informace najdete v tématu [deklarované](~/_csharplang/spec/basic-concepts.md#declared-accessibility) přístupnosti ve [ C# specifikaci jazyka](../language-specification/index.md). Specifikace jazyka je úplným a rozhodujícím zdrojem pro syntaxi a použití jazyka C#.
  
## <a name="see-also"></a>Viz také:

- [C#Odkaz](../index.md)
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)
- [Klíčová slova jazyka C#](./index.md)
- [Modifikátory přístupu](./access-modifiers.md)
- [Úrovně přístupnosti](./accessibility-levels.md)
- [Modifikátory](./modifiers.md)
- [public](./public.md)
- [private](./private.md)
- [protected](./protected.md)
