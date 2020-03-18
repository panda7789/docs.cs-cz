---
title: Konstanty – programovací průvodce C#
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, constants
- constants [C#]
ms.assetid: 1fb39621-1738-49b1-a1b3-8587f109123f
ms.openlocfilehash: 85f6684617b893bdd85eb5b530aa2481941fbc5d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "77093549"
---
# <a name="constants-c-programming-guide"></a>Konstanty (Průvodce programováním v C#)
Konstanty jsou neměnné hodnoty, které jsou známy v době kompilace a nemění po dobu životnosti programu. Konstanty jsou deklarovány s modifikátorem [const.](../../language-reference/keywords/const.md) Pouze c# [předdefinované typy](../../language-reference/builtin-types/built-in-types.md) <xref:System.Object?displayProperty=nameWithType>(kromě) mohou `const`být deklarovány jako . Uživatelem definované typy, včetně tříd, struktur a polí, nemohou být `const`. Modifikátor [jen pro čtení](../../language-reference/keywords/readonly.md) použijte k vytvoření třídy, struktury nebo pole, která je inicializována jednou za běhu (například v konstruktoru) a poté nemůže být změněna.  
  
 C# nepodporuje `const` metody, vlastnosti nebo události.  
  
 Typ výčtu umožňuje definovat pojmenované konstanty pro integrované předdefinované `uint` `long`typy (například `int`, , a tak dále). Další informace naleznete [v tématu výčet](../../language-reference/builtin-types/enum.md).  
  
 Konstanty musí být inicializovány při jejich deklaraci. Například:  
  
 [!code-csharp[csProgGuideObjects#64](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#64)]  
  
 V tomto příkladu `months` konstanta je vždy 12 a nelze změnit ani třídy samotné. Ve skutečnosti když kompilátor narazí konstantní identifikátor ve zdrojovém `months`kódu Jazyka C# (například ), nahradí hodnotu literálu přímo do kódu zprostředkujícího jazyka (IL), který vytváří. Vzhledem k tomu, že neexistuje žádná `const` proměnná adresa přidružená k konstantě za běhu, pole nelze předat odkazem a nemohou se ve výrazu zobrazit jako hodnota l.  
  
> [!NOTE]
> Buďte opatrní, pokud odkazujete na konstantní hodnoty definované v jiném kódu, například v knihovnách DLL. Pokud nová verze dll definuje novou hodnotu pro konstantu, program bude stále obsahovat staré literál hodnotu, dokud je znovu zkompilován proti nové verzi.  
  
 Současně lze deklarovat více konstant stejného typu, například:  
  
 [!code-csharp[csProgGuideObjects#65](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#65)]  
  
 Výraz, který se používá k inicializaci konstanty může odkazovat na jinou konstantu, pokud nevytvoří cyklický odkaz. Například:  
  
 [!code-csharp[csProgGuideObjects#66](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#66)]  
  
 Konstanty mohou být označeny jako [veřejné](../../language-reference/keywords/public.md), [soukromé](../../language-reference/keywords/private.md), [chráněné](../../language-reference/keywords/protected.md), [interní](../../language-reference/keywords/internal.md), [chráněné vnitřní](../../language-reference/keywords/protected-internal.md) nebo soukromé [chráněné](../../language-reference/keywords/private-protected.md). Tyto modifikátory přístupu definují, jak mohou uživatelé třídy přistupovat k konstantě. Další informace naleznete [v tématu Access Modifiers](./access-modifiers.md).  
  
 Konstanty jsou přístupné, jako by byly [statická](../../language-reference/keywords/static.md) pole, protože hodnota konstanty je stejná pro všechny instance typu. Klíčové `static` slovo nelze použít k jejich deklarování. Výrazy, které nejsou ve třídě, která definuje konstantu, musí pro přístup k konstantě používat název třídy, tečku a název konstanty. Například:  
  
 [!code-csharp[csProgGuideObjects#67](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#67)]  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Programovací příručka jazyka C#](../index.md)
- [Třídy a struky](./index.md)
- [Vlastnosti](./properties.md)
- [Typy](../types/index.md)
- [Readonly](../../language-reference/keywords/readonly.md)
- [Neměnnost v C# část první: Druhy neměnnosti](https://docs.microsoft.com/archive/blogs/ericlippert/immutability-in-c-part-one-kinds-of-immutability)
