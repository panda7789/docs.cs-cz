---
title: interní C# odkaz
ms.date: 07/20/2015
f1_keywords:
- internal_CSharpKeyword
- internal
helpviewer_keywords:
- internal keyword [C#]
ms.assetid: 6ee0785c-d7c8-49b8-bb72-0a4dfbcb6461
ms.openlocfilehash: db653d0ed7f4835348484242b03392a8955c6392
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713430"
---
# <a name="internal-c-reference"></a>internal (Referenční dokumentace jazyka C#)
Klíčové slovo `internal` je [modifikátor přístupu](./access-modifiers.md) pro typy a členy typů. 
  
 > Tato stránka pokrývá přístup `internal`. Klíčové slovo `internal` je také součástí modifikátoru přístupu [`protected internal`](./protected-internal.md) .
  
Interní typy nebo členy jsou přístupné pouze v rámci souborů ve stejném sestavení, jako v tomto příkladu:  
  
```csharp  
public class BaseClass   
{  
    // Only accessible within the same assembly.
    internal static int x = 0;
}  
```  

 Porovnání `internal` s dalšími modifikátory přístupu najdete v tématu [úrovně přístupnosti](./accessibility-levels.md) a [modifikátory přístupu](../../programming-guide/classes-and-structs/access-modifiers.md).  
  
 Další informace o sestaveních naleznete [v tématu sestavení v rozhraní .NET](../../../standard/assembly/index.md).  
  
 Běžné použití interního přístupu je v rámci vývoje založeného na komponentách, protože umožňuje skupině komponent, aby spolupracovaly soukromě, aniž by bylo zveřejněno pro zbytek kódu aplikace. Například architektura pro sestavování grafických uživatelských rozhraní může poskytovat `Control` a `Form` třídy, které spolupracují pomocí členů s interním přístupem. Vzhledem k tomu, že jsou tyto členy interní, nejsou vystaveny kódu, který používá rozhraní.  
  
 Jedná se o chybu, která odkazuje na typ nebo člen s vnitřním přístupem mimo sestavení, ve kterém byla definována.  
  
## <a name="example"></a>Příklad  
 Tento příklad obsahuje dva soubory `Assembly1.cs` a `Assembly1_a.cs`. První soubor obsahuje interní základní třídu `BaseClass`. Ve druhém souboru se pokus o vytvoření instance `BaseClass` vytvoří chyba.  
  
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
 V tomto příkladu použijte stejné soubory, které jste použili v příkladu 1, a změňte úroveň přístupnosti `BaseClass` na `public`. Změňte také úroveň přístupnosti člena `intM` na `internal`. V takovém případě můžete vytvořit instanci třídy, ale nemůžete získat přístup k internímu členu.  
  
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
  
## <a name="c-language-specification"></a>C# – jazyková specifikace  

Další informace najdete v tématu [deklarované přístupnosti](~/_csharplang/spec/basic-concepts.md#declared-accessibility) ve [ C# specifikaci jazyka](/dotnet/csharp/language-reference/language-specification/introduction). Specifikace jazyka je úplným a rozhodujícím zdrojem pro syntaxi a použití jazyka C#.
  
## <a name="see-also"></a>Viz také:

- [C#Odkaz](../index.md)
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)
- [Klíčová slova jazyka C#](./index.md)
- [Modifikátory přístupu](./access-modifiers.md)
- [Úrovně přístupnosti](./accessibility-levels.md)
- [Modifikátory](index.md)
- [public](./public.md)
- [private](./private.md)
- [protected](./protected.md)
