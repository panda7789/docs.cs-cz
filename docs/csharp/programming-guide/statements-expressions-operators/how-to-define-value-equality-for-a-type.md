---
title: Definování rovnosti hodnoty pro typ – Průvodce programováním v C#
description: Naučte se definovat rovnost hodnot pro určitý typ. Podívejte se na příklady kódu a zobrazte další dostupné prostředky.
ms.date: 07/20/2015
helpviewer_keywords:
- overriding Equals method [C#]
- object equivalence [C#]
- Equals method [C#], overriding
- value equality [C#]
- equivalence [C#]
ms.assetid: 4084581e-b931-498b-9534-cf7ef5b68690
ms.openlocfilehash: cf4449618c2b57f21855354f2250d41a403b4d57
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/29/2020
ms.locfileid: "87381642"
---
# <a name="how-to-define-value-equality-for-a-type-c-programming-guide"></a>Definování rovnosti hodnoty pro typ (Průvodce programováním v C#)

Při definování třídy nebo struktury se rozhodujete, zda má smysl vytvořit vlastní definici hodnoty rovnosti (nebo ekvivalence) pro daný typ. Obvykle implementujete rovnost hodnot, pokud se očekává, že se objekty typu přidají do kolekce nějakého řazení, nebo když jejich primární účel ukládá sadu polí nebo vlastností. Definici rovnosti hodnot můžete založit na porovnání všech polí a vlastností v typu nebo můžete založit definici u podmnožiny.

V obou případech a v obou třídách i strukturách by vaše implementace měla dodržovat pět záruk ekvivalence (pro následující pravidla předpokládají, že `x` `y` a `z` nejsou null):  
  
1. `x.Equals(x)`Vrátí `true` . Tato vlastnost se nazývá reflexivní.  
  
2. `x.Equals(y)`vrací stejnou hodnotu jako `y.Equals(x)` . Tato vlastnost se nazývá symetrická vlastnost.  
  
3. Pokud `(x.Equals(y) && y.Equals(z))` vrátí `true` , vrátí `x.Equals(z)` `true` . Tato vlastnost se nazývá Transitive.  
  
4. Po sobě jdoucí volání `x.Equals(y)` vracet stejnou hodnotu, pokud se objekty odkazované x a y nezmění.  
  
5. Libovolná hodnota, která není null, se nerovná hodnotě null. Modul CLR však kontroluje hodnotu null u všech volání metody a vyvolá výjimku, `NullReferenceException` Pokud `this` by měl odkaz hodnotu null. Proto `x.Equals(y)` vyvolá výjimku, pokud `x` má hodnotu null. Který přerušuje pravidla 1 nebo 2 v závislosti na argumentu `Equals` .

 Libovolná struktura, kterou definujete, již má výchozí implementaci rovnosti hodnot, kterou dědí z <xref:System.ValueType?displayProperty=nameWithType> přepsání <xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType> metody. Tato implementace používá reflexi k prohlédnutí všech polí a vlastností v typu. I když tato implementace přináší správné výsledky, je poměrně pomalé ve srovnání s vlastní implementací, kterou zapisujete konkrétně pro daný typ.  
  
 Podrobnosti implementace pro rovnost hodnot se liší pro třídy a struktury. Nicméně třídy a struktury vyžadují stejný základní postup pro implementaci rovnosti:  
  
1. Přepsat [virtuální](../../language-reference/keywords/virtual.md) <xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType> metodu. Ve většině případů vaše implementace `bool Equals( object obj )` by měla volat pouze do metody specifické pro typ `Equals` , který je implementací <xref:System.IEquatable%601?displayProperty=nameWithType> rozhraní. (Viz krok 2.)  
  
2. Implementujte <xref:System.IEquatable%601?displayProperty=nameWithType> rozhraní zadáním metody specifické pro typ `Equals` . Je to místo, kde se provádí skutečné porovnání rovnosti. Například se můžete rozhodnout definovat rovnost porovnáním pouze jednoho nebo dvou polí v typu. Negenerovat výjimky z `Equals` . Pouze pro třídy: Tato metoda by měla prozkoumávat pouze pole, která jsou deklarována ve třídě. Měla by volat `base.Equals` , aby prozkoumala pole, která jsou v základní třídě. (Tuto operaci neprovádějte, pokud typ dědí přímo z <xref:System.Object> , protože <xref:System.Object> implementace <xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType> provede kontrolu rovnosti referencí.)  
  
3. Volitelné, ale doporučené: přetížení [==](../../language-reference/operators/equality-operators.md#equality-operator-) operátorů a [! =](../../language-reference/operators/equality-operators.md#inequality-operator-) .  
  
4. Přepsat <xref:System.Object.GetHashCode%2A?displayProperty=nameWithType> tak, aby dva objekty, které mají rovnost hodnot, vytvořily stejný kód hash.  
  
5. Volitelné: pro podporu definic pro "větší než" nebo "menší než", implementujte <xref:System.IComparable%601> rozhraní pro váš typ a také [<=](../../language-reference/operators/comparison-operators.md#less-than-or-equal-operator-) [>=](../../language-reference/operators/comparison-operators.md#greater-than-or-equal-operator-) operátory a.  
  
 První příklad, který následuje, ukazuje implementaci třídy. Druhý příklad ukazuje implementaci struktury.  

## <a name="example"></a>Příklad

 Následující příklad ukazuje, jak implementovat hodnotu rovnosti ve třídě (odkazový typ).  
  
 [!code-csharp[csProgGuideStatements#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#19)]  
  
 Ve třídách (odkazových typech) provede výchozí implementace obou <xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType> metod porovnání rovnosti referencí, nikoli kontrolu rovnosti hodnoty. Když implementátor přepíše virtuální metodu, účelem je poskytnout sémantiku rovnosti hodnoty.  
  
 `==`Operátory a `!=` lze použít s třídami i v případě, že třída je přetěžují. Výchozí chování je však provést kontrolu rovnosti referencí. V případě třídy, pokud jste převedli `Equals` metodu, byste měli přetížit `==` `!=` operátory a, ale není to vyžadováno.  

## <a name="example"></a>Příklad

 Následující příklad ukazuje, jak implementovat hodnotu rovnosti ve struktuře (typ hodnoty):  
  
 [!code-csharp[csProgGuideStatements#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#20)]  
  
 Pro struktury, výchozí implementace <xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType> (která je přepsaná verze v <xref:System.ValueType?displayProperty=nameWithType> ) provede kontrolu rovnosti hodnoty pomocí reflexe pro porovnání hodnot každého pole v typu. Když implementátor přepíše virtuální `Equals` metodu ve struktuře, účelem je poskytnout efektivnější způsob provedení kontroly rovnosti hodnoty a volitelně založit porovnání na některé podmnožině pole nebo vlastností struktury.  
  
 [==](../../language-reference/operators/equality-operators.md#equality-operator-)Operátory and [! =](../../language-reference/operators/equality-operators.md#inequality-operator-) nelze použít pro strukturu, pokud je struktura explicitně nepřetěžuje.  
  
## <a name="see-also"></a>Viz také:

- [Porovnání rovnosti](equality-comparisons.md)
- [Průvodce programováním v C#](../index.md)
