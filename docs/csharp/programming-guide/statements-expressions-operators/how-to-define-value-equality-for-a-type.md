---
title: Jak definovat rovnost hodnot pro typ - C# Programovací průvodce
ms.date: 07/20/2015
helpviewer_keywords:
- overriding Equals method [C#]
- object equivalence [C#]
- Equals method [C#], overriding
- value equality [C#]
- equivalence [C#]
ms.assetid: 4084581e-b931-498b-9534-cf7ef5b68690
ms.openlocfilehash: 140be18698a40be8f394b31fcd42b97d6685cb98
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79157088"
---
# <a name="how-to-define-value-equality-for-a-type-c-programming-guide"></a>Jak definovat rovnost hodnot pro typ (Průvodce programováním jazyka C#)

Když definujete třídu nebo strukturu, rozhodnete se, zda má smysl vytvořit vlastní definici rovnosti hodnot (nebo ekvivalence) pro typ. Rovnost hodnot obvykle implementujete, když se očekává, že objekty typu budou přidány do kolekce určitého druhu, nebo když je jejich primárním účelem uložení sady polí nebo vlastností. Definici rovnosti hodnot můžete založit na porovnání všech polí a vlastností v typu nebo můžete založit definici na podmnožině.

V obou případech a ve třídách a strukturách by měla implementace dodržovat pět záruk ekvivalence `y` `z` (Pro následující pravidla předpokládejme, že `x`a nejsou null):  
  
1. `x.Equals(x)`vrátí `true`. To se nazývá reflexivní vlastnost.  
  
2. `x.Equals(y)`vrátí stejnou hodnotu jako `y.Equals(x)`. Tomu se říká symetrická vlastnost.  
  
3. pokud `(x.Equals(y) && y.Equals(z))` `true`vrátí `x.Equals(z)` , `true`vrátí . Tento objekt se nazývá přenositná vlastnost.  
  
4. Následné vyvolání `x.Equals(y)` vrátí stejnou hodnotu, pokud objekty odkazované x a y nejsou změněny.  
  
5. Jakákoli hodnota bez hodnoty null se nerovná hodnotě null. Clr však zkontroluje null na všechna volání `NullReferenceException` metody `this` a vyvolá, pokud by odkaz byl null. Proto `x.Equals(y)` vyvolá výjimku, `x` když je null. To porušuje pravidla 1 nebo 2, `Equals`v závislosti na argumentu .

 Všechny struktury, které definujete již má výchozí implementaci rovnosti <xref:System.ValueType?displayProperty=nameWithType> hodnot, které <xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType> dědí z přepsání metody. Tato implementace používá reflexe prozkoumat všechna pole a vlastnosti v typu. Přestože tato implementace vytváří správné výsledky, je relativně pomalé ve srovnání s vlastní implementaci, kterou píšete speciálně pro typ.  
  
 Podrobnosti implementace pro rovnost hodnot se liší pro třídy a struktury. Třídy i struktury však vyžadují stejné základní kroky pro implementaci rovnosti:  
  
1. Přepsat [virtuální](../../language-reference/keywords/virtual.md) <xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType> metodu. Ve většině případů vaše `bool Equals( object obj )` implementace by měla pouze `Equals` volání do metody <xref:System.IEquatable%601?displayProperty=nameWithType> specifické pro typ, který je implementace rozhraní. (Viz krok 2.)  
  
2. Implementujte <xref:System.IEquatable%601?displayProperty=nameWithType> rozhraní poskytnutím metody `Equals` specifické pro typ. Toto je místo, kde se provádí porovnání skutečné ekvivalence. Můžete se například rozhodnout definovat rovnost porovnáním pouze jednoho nebo dvou polí v typu. Nevyvolávat výjimky z `Equals`. Pouze pro třídy: Tato metoda by měla zkoumat pouze pole, která jsou deklarována ve třídě. Měl by `base.Equals` volat zkoumat pole, která jsou v základní třídě. (Neprovádělte to, pokud <xref:System.Object>typ <xref:System.Object> dědí <xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType> přímo z , protože implementace provádí kontrolu rovnosti odkazů.)  
  
3. Volitelné, ale doporučené: Přetížení [==](../../language-reference/operators/equality-operators.md#equality-operator-) a [!=](../../language-reference/operators/equality-operators.md#inequality-operator-) operátory.  
  
4. Přepište <xref:System.Object.GetHashCode%2A?displayProperty=nameWithType> tak, aby dva objekty, které mají rovnost hodnot, vytvořily stejný kód hash.  
  
5. Volitelné: Chcete-li podporovat definice pro "větší než" <xref:System.IComparable%601> nebo "menší než", [<=](../../language-reference/operators/comparison-operators.md#less-than-or-equal-operator-) [>=](../../language-reference/operators/comparison-operators.md#greater-than-or-equal-operator-) implementujte rozhraní pro váš typ a také přetížení a operátory.  
  
 První příklad, který následuje ukazuje implementaci třídy. Druhý příklad ukazuje implementaci struktury.  

## <a name="example"></a>Příklad

 Následující příklad ukazuje, jak implementovat rovnost hodnot ve třídě (typ odkazu).  
  
 [!code-csharp[csProgGuideStatements#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#19)]  
  
 U tříd (typů odkazů) provádí <xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType> výchozí implementace obou metod porovnání rovnosti odkazů, nikoli kontrola rovnosti hodnot. Když implementátor přepíše virtuální metodu, účelem je dát hodnotu rovnosti sémantiku.  
  
 A `==` `!=` operátory lze použít s třídami i v případě, že třída není přetížení je. Výchozí chování je však provést kontrolu rovnosti odkazů. Ve třídě, pokud přetížení `Equals` metody, měli `==` byste `!=` přetížení a operátory, ale není vyžadováno.  

## <a name="example"></a>Příklad

 Následující příklad ukazuje, jak implementovat rovnost hodnot ve struktuře (typ hodnoty):  
  
 [!code-csharp[csProgGuideStatements#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#20)]  
  
 Pro struktury výchozí implementace <xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType> (což je potlačená <xref:System.ValueType?displayProperty=nameWithType>verze v ) provádí kontrolu rovnosti hodnot pomocí reflexe porovnat hodnoty každé pole v typu. Když implementátor přepíše `Equals` virtuální metodu ve struktuře, účelem je poskytnout efektivnější způsob provádění kontroly rovnosti hodnot a volitelně založit porovnání na některé podmnožině pole nebo vlastností struktury.  
  
 Operátory [==](../../language-reference/operators/equality-operators.md#equality-operator-) a [!=](../../language-reference/operators/equality-operators.md#inequality-operator-) nemohou pracovat na struktuře, pokud je struktura explicitně nepřetíží.  
  
## <a name="see-also"></a>Viz také

- [Porovnání rovnosti](equality-comparisons.md)
- [Průvodce programováním v C#](../index.md)
