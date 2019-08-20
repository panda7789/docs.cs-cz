---
title: Konstanty C# – Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, constants
- constants [C#]
ms.assetid: 1fb39621-1738-49b1-a1b3-8587f109123f
ms.openlocfilehash: d179c1b8717f4247ce745104db2d0bb4faefb8ab
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69597107"
---
# <a name="constants-c-programming-guide"></a>Konstanty (Průvodce programováním v C#)
Konstanty jsou neměnné hodnoty, které jsou známy v době kompilace a nemění se po dobu života programu. Konstanty jsou deklarovány [](../../language-reference/keywords/const.md) s modifikátorem const. Pouze C# předdefinované typy (s výjimkou <xref:System.Object?displayProperty=nameWithType>) mohou být deklarovány jako. `const` Seznam předdefinovaných typů najdete v tématu [tabulka předdefinovaných typů](../../language-reference/keywords/built-in-types-table.md). Uživatelsky definované typy, včetně tříd, struktur a polí, nemůžou být `const`. Použijte modifikátor [jen pro čtení](../../language-reference/keywords/readonly.md) k vytvoření třídy, struktury nebo pole, která je inicializována jednou za běhu (například v konstruktoru) a poté nelze změnit.  
  
 C#`const` nepodporuje metody, vlastnosti nebo události.  
  
 Typ výčtu umožňuje definovat pojmenované konstanty pro integrální předdefinované typy (například `int` `uint` `long`,, a tak dále). Další informace naleznete v tématu [Enum](../../language-reference/keywords/enum.md).  
  
 Konstanty musí být inicializovány, jakmile jsou deklarovány. Příklad:  
  
 [!code-csharp[csProgGuideObjects#64](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#64)]  
  
 V tomto příkladu je konstanta `months` vždy 12 a nemůže být změněna ani samotnou třídou. Ve skutečnosti, když kompilátor narazí na konstantní identifikátor ve C# zdrojovém kódu (například `months`), nahradí hodnotu literálu přímo do kódu přestupného jazyka (IL), který vytvoří. Vzhledem k tomu, že v době běhu není přiřazena žádná proměnná adresa, `const` nelze pole předat odkazem a nelze ji ve výrazu použít jako l-value.  
  
> [!NOTE]
>  Buďte opatrní při odkazování na konstantní hodnoty definované v jiném kódu, jako jsou knihovny DLL. Pokud nová verze knihovny DLL definuje novou hodnotu pro konstantu, program bude stále obsahovat starou hodnotu literálu, dokud nebude znovu zkompilována s novou verzí.  
  
 Současně lze deklarovat více konstant stejného typu, například:  
  
 [!code-csharp[csProgGuideObjects#65](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#65)]  
  
 Výraz, který se používá k inicializaci konstanty, může odkazovat na jinou konstantu, pokud nevytvoří cyklický odkaz. Příklad:  
  
 [!code-csharp[csProgGuideObjects#66](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#66)]  
  
 Konstanty je možné označit jako [veřejné](../../language-reference/keywords/public.md), [privátní](../../language-reference/keywords/private.md), [chráněné](../../language-reference/keywords/protected.md), [interní](../../language-reference/keywords/internal.md), [chráněné interní](../../language-reference/keywords/protected-internal.md) nebo [soukromé chráněné](../../language-reference/keywords/private-protected.md). Tyto modifikátory přístupu definují způsob, jakým uživatelé třídy mají přístup k konstantě. Další informace najdete v tématu [modifikátory přístupu](./access-modifiers.md).  
  
 Konstanty jsou dostupné, jako by se jednalo o [statická](../../language-reference/keywords/static.md) pole, protože hodnota konstanty je stejná pro všechny instance daného typu. `static` Klíčové slovo nepoužíváte k jejich deklaraci. Výrazy, které nejsou ve třídě definující konstantu, musí používat název třídy, tečku a název konstanty pro přístup k konstantě. Příklad:  
  
 [!code-csharp[csProgGuideObjects#67](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#67)]  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce C#](../index.md)
- [Třídy a struktury](./index.md)
- [Vlastnosti](./properties.md)
- [Typy](../types/index.md)
- [readonly](../../language-reference/keywords/readonly.md)
- [Neměnnosti 1 C# . část: Druhy neměnnosti](https://blogs.msdn.microsoft.com/ericlippert/2007/11/13/immutability-in-c-part-one-kinds-of-immutability)
