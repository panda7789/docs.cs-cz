---
title: Definování rovnosti hodnot pro C# programové průvodce
ms.date: 07/20/2015
helpviewer_keywords:
- overriding Equals method [C#]
- object equivalence [C#]
- Equals method [C#], overriding
- value equality [C#]
- equivalence [C#]
ms.assetid: 4084581e-b931-498b-9534-cf7ef5b68690
ms.openlocfilehash: 8c911dc1d0aa36ab8e57fb8a77a52d9cec20743c
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745391"
---
# <a name="how-to-define-value-equality-for-a-type-c-programming-guide"></a>Definování rovnosti hodnoty pro typ (C# Průvodce programováním)

Při definování třídy nebo struktury se rozhodujete, zda má smysl vytvořit vlastní definici hodnoty rovnosti (nebo ekvivalence) pro daný typ. Obvykle implementujete rovnost hodnot, pokud se očekává, že se objekty typu přidají do kolekce nějakého řazení, nebo když jejich primární účel ukládá sadu polí nebo vlastností. Definici rovnosti hodnot můžete založit na porovnání všech polí a vlastností v typu nebo můžete založit definici u podmnožiny. 

V obou případech a v obou třídách i strukturách by vaše implementace měla dodržovat pět záruk ekvivalence (pro následující pravidla předpokládají, že `x`, `y` a `z` nejsou null):  
  
1. `x.Equals(x)` vrátí `true`. Tato vlastnost se nazývá reflexivní.  
  
2. `x.Equals(y)` vrací stejnou hodnotu jako `y.Equals(x)`. Tato vlastnost se nazývá symetrická vlastnost.  
  
3. Pokud `(x.Equals(y) && y.Equals(z))` vrátí `true`, `x.Equals(z)` vrátí `true`. Tato vlastnost se nazývá Transitive.  
  
4. Po sobě jdoucí volání `x.Equals(y)` vracet stejnou hodnotu, pokud se objekty odkazované x a y nezmění.  
  
5. Libovolná hodnota, která není null, se nerovná hodnotě null. Modul CLR však kontroluje hodnotu null u všech volání metody a vyvolá `NullReferenceException`, pokud by odkaz `this` null. Proto `x.Equals(y)` vyvolá výjimku, pokud `x` má hodnotu null. Který přerušuje pravidla 1 nebo 2 v závislosti na argumentu pro `Equals`.
 
 Libovolná struktura, kterou definujete, již má výchozí implementaci rovnosti hodnot, kterou dědí z <xref:System.ValueType?displayProperty=nameWithType> přepsání <xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType> metody. Tato implementace používá reflexi k prohlédnutí všech polí a vlastností v typu. I když tato implementace přináší správné výsledky, je poměrně pomalé ve srovnání s vlastní implementací, kterou zapisujete konkrétně pro daný typ.  
  
 Podrobnosti implementace pro rovnost hodnot se liší pro třídy a struktury. Nicméně třídy a struktury vyžadují stejný základní postup pro implementaci rovnosti:  
  
1. Přepište metodu [virtual](../../language-reference/keywords/virtual.md) <xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType>. Ve většině případů vaše implementace `bool Equals( object obj )` by měla volat pouze do metody `Equals` specifické pro typ, která je implementací rozhraní <xref:System.IEquatable%601?displayProperty=nameWithType>. (Viz krok 2.)  
  
2. Implementujte rozhraní <xref:System.IEquatable%601?displayProperty=nameWithType> poskytnutím metody `Equals` specifické pro konkrétní typ. Je to místo, kde se provádí skutečné porovnání rovnosti. Například se můžete rozhodnout definovat rovnost porovnáním pouze jednoho nebo dvou polí v typu. Nevyvolávat výjimky z `Equals`. Pouze pro třídy: Tato metoda by měla prozkoumávat pouze pole, která jsou deklarována ve třídě. Měla by volat `base.Equals`, aby prozkoumala pole, která jsou v základní třídě. (Tuto operaci neprovádějte, pokud typ dědí přímo z <xref:System.Object>, protože <xref:System.Object> implementace <xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType> provádí kontrolu rovnosti odkazů.)  
  
3. Volitelné, ale doporučené: přetížení operátorů [==](../../language-reference/operators/equality-operators.md#equality-operator-) a [! =](../../language-reference/operators/equality-operators.md#inequality-operator-) .  
  
4. Přepsat <xref:System.Object.GetHashCode%2A?displayProperty=nameWithType> tak, aby dva objekty, které mají rovnost hodnot, vytvořily stejný kód hash.  
  
5. Volitelné: pro podporu definic pro "větší než" nebo "menší než" implementujte rozhraní <xref:System.IComparable%601> pro váš typ a také přetížení [<=](../../language-reference/operators/comparison-operators.md#less-than-or-equal-operator-) a [>=](../../language-reference/operators/comparison-operators.md#greater-than-or-equal-operator-) operátory.  
  
 První příklad, který následuje, ukazuje implementaci třídy. Druhý příklad ukazuje implementaci struktury.  

## <a name="example"></a>Příklad

 Následující příklad ukazuje, jak implementovat hodnotu rovnosti ve třídě (odkazový typ).  
  
 [!code-csharp[csProgGuideStatements#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#19)]  
  
 U tříd (odkazových typů) výchozí implementace obou <xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType> metod provádí porovnání rovnosti referencí, nikoli kontrolu rovnosti hodnot. Když implementátor přepíše virtuální metodu, účelem je poskytnout sémantiku rovnosti hodnoty.  
  
 Operátory `==` a `!=` lze použít s třídami i v případě, že je třída přetěžují. Výchozí chování je však provést kontrolu rovnosti referencí. V případě, že dojde k přetížení metody `Equals`, měli byste přetížit operátory `==` a `!=`, ale není to nutné.  

## <a name="example"></a>Příklad

 Následující příklad ukazuje, jak implementovat hodnotu rovnosti ve struktuře (typ hodnoty):  
  
 [!code-csharp[csProgGuideStatements#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#20)]  
  
 Pro struktury, výchozí implementace <xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType> (která je přepsaná verze v <xref:System.ValueType?displayProperty=nameWithType>) provede kontrolu rovnosti hodnoty pomocí reflexe pro porovnání hodnot každého pole v typu. Když implementátor přepíše metodu Virtual `Equals` ve struktuře, účelem je poskytnout efektivnější prostředky pro kontrolu rovnosti hodnoty a volitelně založit porovnání na některé podmnožině pole nebo vlastností struktury.  
  
 Operátory [==](../../language-reference/operators/equality-operators.md#equality-operator-) a [! =](../../language-reference/operators/equality-operators.md#inequality-operator-) nemohou pracovat na struktuře, pokud je struktura explicitně nenačítá.  
  
## <a name="see-also"></a>Viz také

- [Porovnání rovnosti](equality-comparisons.md)
- [C#Průvodce programováním](../index.md)
