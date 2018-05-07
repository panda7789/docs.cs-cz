---
title: Konstanty (Průvodce programováním v C#)
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, constants
- constants [C#]
ms.assetid: 1fb39621-1738-49b1-a1b3-8587f109123f
ms.openlocfilehash: 90423c868ca303f8e94c16f44bc5e0b23615fc17
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="constants-c-programming-guide"></a>Konstanty (Průvodce programováním v C#)
Konstanty jsou neměnné hodnoty, kterých se ví, že v době kompilace a nemění po celou dobu životnosti program. Konstanty jsou deklarovány s [const](../../../csharp/language-reference/keywords/const.md) modifikátor. Pouze C# předdefinované typy (s výjimkou <xref:System.Object?displayProperty=nameWithType>) může být deklarována jako `const`. Seznam předdefinovaných typů najdete v tématu [tabulka předdefinovaných typů](../../../csharp/language-reference/keywords/built-in-types-table.md). Uživatelem definované typy, včetně tříd, struktur a pole, nelze `const`. Použití [jen pro čtení](../../../csharp/language-reference/keywords/readonly.md) modifikátor vytvořit třída, struktura nebo pole, které se inicializuje jednou za běhu (například v konstruktoru) a následně se nedá změnit.  
  
 C# nepodporuje `const` metody, vlastnosti nebo události.  
  
 Typ výčtu umožňuje definovat pojmenované konstanty pro integrální předdefinovaných typů (například `int`, `uint`, `long`a tak dále). Další informace najdete v tématu [výčtu](../../../csharp/language-reference/keywords/enum.md).  
  
 Konstanty musí být inicializován, jako jsou deklarovány. Příklad:  
  
 [!code-csharp[csProgGuideObjects#64](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/constants_1.cs)]  
  
 V tomto příkladu konstanta `months` je vždy 12 a nelze ji změnit, i pomocí vlastní třídy. Ve skutečnosti, když kompilátor zaznamená identifikátor konstantní ve zdrojovém kódu C# (například `months`), se nahradí hodnotu literálu přímo do převodní jazyk (IL) kód, který vytváří. Vzhledem k tomu, že není žádná proměnné adresa přidružená konstanta za běhu, `const` pole nelze předat odkazem a nemůže být použit jako hodnotu l ve výrazu.  
  
> [!NOTE]
>  Buďte opatrní při odkazu na konstantní hodnoty, které jsou definované v jiný kód, například knihovny DLL. Pokud novou verzi knihovny DLL definuje novou hodnotu pro konstantu, váš program stále podržte stará hodnota literálu, dokud ho znovu zkompiluje proti na novou verzi.  
  
 Více konstanty stejného typu lze deklarovat na stejnou dobu, například:  
  
 [!code-csharp[csProgGuideObjects#65](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/constants_2.cs)]  
  
 Výraz, který se používá k chybě při inicializaci konstanta mohou odkazovat na jiné konstanta, pokud nedojde k vytvoření cyklický odkaz. Příklad:  
  
 [!code-csharp[csProgGuideObjects#66](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/constants_3.cs)]  
  
 Konstanty může být označen jako [veřejné](../../../csharp/language-reference/keywords/public.md), [privátní](../../../csharp/language-reference/keywords/private.md), [chráněné](../../../csharp/language-reference/keywords/protected.md), [interní](../../../csharp/language-reference/keywords/internal.md), [chráněné interní](../../../csharp/language-reference/keywords/protected-internal.md)nebo [privátní chráněné](../../../csharp/language-reference/keywords/private-protected.md). Tyto modifikátory přístupu definovat třídy pro přístup uživatelů konstanta. Další informace najdete v tématu [modifikátory přístupu](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).  
  
 Konstanty jsou přístupné, jako kdyby byly [statické](../../../csharp/language-reference/keywords/static.md) pole, protože hodnota konstanty je stejný pro všechny instance typu. Nepoužívejte `static` – klíčové slovo je deklarovat. Výrazy, které nejsou ve třídě, která definuje konstantu musí používat název třídy, dobou a název konstanty pro přístup konstanta. Příklad:  
  
 [!code-csharp[csProgGuideObjects#67](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/constants_4.cs)]  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [Třídy a struktury](../../../csharp/programming-guide/classes-and-structs/index.md)  
 [Vlastnosti](../../../csharp/programming-guide/classes-and-structs/properties.md)  
 [Typy](../../../csharp/programming-guide/types/index.md)  
 [readonly](../../../csharp/language-reference/keywords/readonly.md)  
 [První část neměnitelnosti v jazyce C#: druhy neměnitelnosti](https://blogs.msdn.microsoft.com/ericlippert/2007/11/13/immutability-in-c-part-one-kinds-of-immutability)
