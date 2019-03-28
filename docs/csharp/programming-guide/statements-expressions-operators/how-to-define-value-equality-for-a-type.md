---
title: 'Postupy: Definování rovnosti hodnoty pro typ - C# Průvodce programováním'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- overriding Equals method [C#]
- object equivalence [C#]
- Equals method [C#], overriding
- value equality [C#]
- equivalence [C#]
ms.assetid: 4084581e-b931-498b-9534-cf7ef5b68690
ms.openlocfilehash: 6ee44cb58033e0e235222fb3f74302f84092dbcb
ms.sourcegitcommit: 4a8c2b8d0df44142728b68ebc842575840476f6d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/28/2019
ms.locfileid: "58545439"
---
# <a name="how-to-define-value-equality-for-a-type-c-programming-guide"></a>Postupy: Definování rovnosti hodnoty pro typ (C# Průvodce programováním v)
Při definování třídy nebo struktury, rozhodnete se, zda je vhodné vytvořit vlastní definici rovnosti hodnoty (nebo ekvivalence) pro typ. Rovnost hodnot se obvykle, implementují se očekává, že objekty tohoto typu přidána do kolekce s nějakým nebo při jejich hlavním účelem je uložit sadu pole nebo vlastnosti. Vaše definici rovnosti hodnot daného můžete založit na porovnání všech polí a vlastností v typu, nebo můžete založit definice v podmnožině. Ale v obou případech a ve třídách a strukturách pět záruky ekvivalence postupujte podle vaší implementace:  
  
1.  `x.Equals(x)` Vrátí `true`. Tomu se říká reflexivní vlastnost.  
  
2.  `x.Equals(y)` vrátí stejnou hodnotu jako `y.Equals(x)`. Tomu se říká symetrický vlastnost.  
  
3.  Pokud `(x.Equals(y) && y.Equals(z))` vrátí `true`, pak `x.Equals(z)` vrátí `true`. Tomu se říká vlastnost tranzitivní.  
  
4.  Po sobě jdoucích vyvolání `x.Equals(y)` vrátí stejnou hodnotu jako objekty odkazuje x a y nezmění.  
  
5.  `x.Equals(null)` Vrátí `false`. Ale `null.Equals(null)` vyvolá výjimku; neřídí číslo pravidla dvě výše.  
  
 Všechny struktury, které definujete již má výchozí implementaci třídy rovnost hodnot, která dědí z <xref:System.ValueType?displayProperty=nameWithType> přepsání <xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType> metody. Tato implementace používá reflexi ke kontrole všech polí a vlastností v typu. I když tato implementace produkuje správné výsledky, je poměrně pomalé ve srovnání s vlastní implementaci, který píšete speciálně pro typ.  
  
 Podrobnosti implementace pro hodnotu rovnosti se liší u tříd a struktur. Třídy a struktury ale vyžadují stejný základní postup pro implementaci rovnosti:  
  
1.  Přepsat [virtuální](../../../csharp/language-reference/keywords/virtual.md) <xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType> metody. Ve většině případů implementace `bool Equals( object obj )` by měly volat pouze na konkrétní typ `Equals` metodu, která je provádění <xref:System.IEquatable%601?displayProperty=nameWithType> rozhraní. (Viz krok 2.)  
  
2.  Implementace <xref:System.IEquatable%601?displayProperty=nameWithType> rozhraní tím, že poskytuje určitého typu `Equals` metody. To je, kde se provádí porovnání skutečné ekvivalence. Například můžete rozhodnout k definování rovnosti porovnáním pouze jednu nebo dvě pole v typu. Nevyvolají výjimky z `Equals`. Pro pouze třídy: Tato metoda by měla prozkoumat pouze pole, které jsou deklarovány ve třídě. Měla by volat `base.Equals` prozkoumat pole, která jsou v základní třídě. (Není to provést, pokud typ dědí přímo z <xref:System.Object>, protože <xref:System.Object> provádění <xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType> provádí kontrolu rovnosti reference.)  
  
3.  Nepovinné – ale doporučené: Přetěžování [ == ](../../../csharp/language-reference/operators/equality-operators.md#equality-operator-) a [! =](../../../csharp/language-reference/operators/equality-operators.md#inequality-operator-) operátory.  
  
4.  Přepsat <xref:System.Object.GetHashCode%2A?displayProperty=nameWithType> tak, aby dva objekty, které se mají vytvořit stejný rovnost hodnot hash kód.  
  
5.  Volitelné: Pro podporu definic pro "větší než" nebo "menší než", implementovat <xref:System.IComparable%601> rozhraní pro typ a také přetížit [ <= ](../../../csharp/language-reference/operators/less-than-equal-operator.md) a [ >= ](../../../csharp/language-reference/operators/greater-than-equal-operator.md) operátory.  
  
 Který následuje první příklad ukazuje implementaci třídy. Druhý příklad ukazuje implementaci struktury.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak implementovat rovnost hodnot ve třídě (odkaz).  
  
 [!code-csharp[csProgGuideStatements#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#19)]  
  
 Na třídy (typy odkazů) výchozí implementaci i <xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType> metody provádí porovnání rovnosti reference, ne kontroly rovnosti hodnoty. Když implementátora přepíše virtuální metody, účelem je pro ni sémantiku rovnosti hodnoty.  
  
 `==` a `!=` operátory lze používat s třídami, i když je přetížení není třída. Výchozí chování je však provést kontrolu rovnosti reference. Ve třídě, pokud přetížíte `Equals` metodu, můžete přetížit `==` a `!=` operátory, ale není povinné.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak implementovat rovnost hodnot ve struktuře (ValueType):  
  
 [!code-csharp[csProgGuideStatements#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#20)]  
  
 Pro struktury, výchozí implementaci <xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType> (což je přepsaná verze <xref:System.ValueType?displayProperty=nameWithType>) provádí kontroly rovnosti hodnoty pomocí reflexe pro porovnání hodnot každé pole v typu. Při přepsání virtuální implementátora `Equals` metody struktury účelem je poskytovat efektivnější způsob provedení kontroly rovnosti hodnoty a volitelně založit porovnání na určitou podmnožinu struktura, obsahovat pole nebo vlastnosti.  
  
 [ == ](../../../csharp/language-reference/operators/equality-operators.md#equality-operator-) a [! =](../../../csharp/language-reference/operators/equality-operators.md#inequality-operator-) operátory nejde použít pro struktury, pokud struktury explicitně přetížení.  
  
## <a name="see-also"></a>Viz také:

- [Porovnání rovnosti](../../../csharp/programming-guide/statements-expressions-operators/equality-comparisons.md)
- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)
