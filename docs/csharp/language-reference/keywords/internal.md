---
title: interní – odkaz jazyka C#
ms.date: 07/20/2015
f1_keywords:
- internal_CSharpKeyword
- internal
helpviewer_keywords:
- internal keyword [C#]
ms.assetid: 6ee0785c-d7c8-49b8-bb72-0a4dfbcb6461
ms.openlocfilehash: e5a5ca18828b689241abbb6d80c5adc51efb073c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79173598"
---
# <a name="internal-c-reference"></a>internal (Referenční dokumentace jazyka C#)
Klíčové `internal` slovo je [modifikátor přístupu](./access-modifiers.md) pro typy a členy typu.
  
 > Tato stránka `internal` se týká přístupu. Klíčové `internal` slovo je také [`protected internal`](./protected-internal.md) součástí modifikátoru přístupu.
  
Interní typy nebo členy jsou přístupné pouze v rámci souborů ve stejném sestavení, jako v tomto příkladu:  
  
```csharp  
public class BaseClass
{  
    // Only accessible within the same assembly.
    internal static int x = 0;
}  
```  

 Porovnání s `internal` ostatními modifikátory přístupu naleznete v [tématu Úrovně přístupnosti](./accessibility-levels.md) a [Modifikátory přístupu](../../programming-guide/classes-and-structs/access-modifiers.md).  
  
 Další informace o sestaveních naleznete [v tématu Sestavení v rozhraní .NET](../../../standard/assembly/index.md).  
  
 Běžné použití interního přístupu je ve vývoji založeném na součástech, protože umožňuje skupině součástí spolupracovat soukromým způsobem, aniž by byla vystavena zbytku kódu aplikace. Například rámec pro vytváření grafických uživatelských rozhraní může poskytnout `Control` a `Form` třídy, které spolupracují pomocí členů s interním přístupem. Vzhledem k tomu, že tyto členy jsou interní, nejsou vystaveny kódu, který používá rozhraní.  
  
 Je chyba odkazovat na typ nebo člen s internípřístup mimo sestavení, ve kterém byl definován.  
  
## <a name="example"></a>Příklad  
 Tento příklad obsahuje `Assembly1.cs` dva `Assembly1_a.cs`soubory a . První soubor obsahuje vnitřní základní `BaseClass`třídu . V druhém souboru dojde k vytvoření `BaseClass` instance.  
  
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
 V tomto příkladu použijte stejné soubory, které jste použili `BaseClass` `public`v příkladu 1, a změňte úroveň usnadnění na . Změňte také úroveň usnadnění `intM` `internal`přístupu člena na . V takovém případě můžete vytvořit instanci třídy, ale nelze získat přístup k interní člen.  
  
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

For more information, see [Declared accessibility](~/_csharplang/spec/basic-concepts.md#declared-accessibility) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction). Specifikace jazyka je úplným a rozhodujícím zdrojem pro syntaxi a použití jazyka C#.
  
## <a name="see-also"></a>Viz také

- [Odkaz jazyka C#](../index.md)
- [Programovací příručka jazyka C#](../../programming-guide/index.md)
- [C# Klíčová slova](./index.md)
- [Modifikátory přístupu](./access-modifiers.md)
- [Úrovně přístupnosti](./accessibility-levels.md)
- [Modifikátory](index.md)
- [Veřejné](./public.md)
- [Soukromé](./private.md)
- [protected](./protected.md)
