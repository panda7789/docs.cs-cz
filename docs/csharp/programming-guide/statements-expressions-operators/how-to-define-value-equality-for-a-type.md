---
title: "Postupy: Definování rovnosti hodnoty pro typ (Průvodce programováním v C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- overriding Equals method [C#]
- object equivalence [C#]
- Equals method [C#] , overriding
- value equality [C#]
- equivalence [C#]
ms.assetid: 4084581e-b931-498b-9534-cf7ef5b68690
caps.latest.revision: "15"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 933be6aa27b5720a9a9d8d7b45e1eed73f9cd60b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-define-value-equality-for-a-type-c-programming-guide"></a>Postupy: Definování rovnosti hodnoty pro typ (Průvodce programováním v C#)
Když definujete třídě nebo struktuře, je rozhodnout, zda má smysl k vytvoření vlastní definice rovnosti hodnoty (nebo ekvivalenční) pro typ. Obvykle byste implementovat rovnosti hodnoty, když se očekává, že objekty typu přidat do kolekce nějaká, nebo když je jejich primární účel k uložení sadu polí a vlastností. Vaše definice rovnosti hodnoty můžete založit na porovnání všechna pole a vlastnosti v typu, nebo může základní definice na podmnožinu. Ale v obou případech a v třídy a struktury vaší implementace postupujte podle pět záruky ekvivalenční:  
  
1.  x.`Equals`(x) vrátí `true.` to se označuje jako reflexivní vlastnost.  
  
2.  x.`Equals`(y) vrací stejnou hodnotu jako y.`Equals`(x). Tomu se říká symetrický vlastnost.  
  
3.  Pokud (x.`Equals`(y) & & y.`Equals`(z)) vrátí `true`, pak x.`Equals`(z) vrátí `true`. Tomu se říká přenositelné vlastnost.  
  
4.  Následných volání x.`Equals`(y) vrátit stejnou hodnotu, dokud, objekty odkazuje x a y se nemění.  
  
5.  x.`Equals`(null) vrátí `false`. Ale hodnotu null. Equals(NULL) vyvolá výjimku; ho neřídí číslo pravidla dva výše.  
  
 Všechny struktura, která definujete již má výchozí implementaci třídy rovnosti hodnoty, která dědí z <xref:System.ValueType?displayProperty=nameWithType> přepsat z <xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType> metoda. Tato implementace používá reflexe prověřit všechna pole a vlastnosti v typu. I když tato implementace produkuje správné výsledky, je relativně pomalá ve srovnání s vlastní implementace, která můžete psát speciálně pro typ.  
  
 Podrobnosti implementace rovnosti hodnoty se liší pro třídy a struktury. Třídy a struktury však vyžadovat stejný základní postup pro implementaci rovnosti:  
  
1.  Přepsání [virtuální](../../../csharp/language-reference/keywords/virtual.md) <xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType> metoda. Ve většině případů vaši implementaci `bool Equals( object obj )` by měly volat pouze na konkrétní typ `Equals` metoda, která je implementace <xref:System.IEquatable%601?displayProperty=nameWithType> rozhraní. (Viz krok 2.)  
  
2.  Implementace <xref:System.IEquatable%601?displayProperty=nameWithType> rozhraní zadáním konkrétního typu `Equals` metoda. Toto je, kde je provést porovnání skutečné ekvivalenční. Například můžete rozhodnout k definování rovnosti porovnáním pouze jednu nebo dvě pole v vašeho typu. Nevyvolá výjimku výjimky z `Equals`. Pro třídy pouze: Tato metoda by měla prozkoumat pouze pole, které jsou deklarované v třídě. Měla by volat `base.Equals` prozkoumat pole, které jsou v základní třídě. (Neprovádějte tuto akci, pokud typ dědí přímo z <xref:System.Object>, protože <xref:System.Object> implementace <xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType> provede kontrolu referenční rovnosti.)  
  
3.  Volitelné, ale doporučené: přetížení [ == ](../../../csharp/language-reference/operators/equality-comparison-operator.md) a [! =](../../../csharp/language-reference/operators/not-equal-operator.md) operátory.  
  
4.  Přepsání <xref:System.Object.GetHashCode%2A?displayProperty=nameWithType> tak, aby dva objekty, které mají stejný vytvořit rovnosti hodnoty hash kód.  
  
5.  Volitelné: Na podporu definice pro "větší než" nebo "menší než", implementovat <xref:System.IComparable%601> rozhraní pro typ vašeho a také přetížení [ <= ](../../../csharp/language-reference/operators/less-than-equal-operator.md) a [ >= ](../../../csharp/language-reference/operators/greater-than-equal-operator.md) operátory .  
  
 V prvním příkladu, který následuje, ukazuje implementaci třídy. Druhý příklad ukazuje implementaci struktura.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak implementovat rovnosti hodnoty v třídě (odkaz).  
  
 [!code-csharp[csProgGuideStatements#19](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-define-value-equality-for-a-type_1.cs)]  
  
 Na třídy (odkazové typy) výchozí implementace obou <xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType> metody provede porovnání rovnosti odkaz, kontrolu typu rovnosti hodnotu. Když implementátor přepíše metodu virtuální, účelem je umožnit sémantika rovnosti hodnoty.  
  
 `==` a `!=` operátory lze použít s třídami, i v případě, že třída není přetížení je. Výchozí chování je však provést kontrolu referenční rovnosti. Ve třídě, pokud jste přetížení `Equals` metody by měla přetížení `==` a `!=` operátory, ale se nevyžaduje.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak implementovat rovnosti hodnoty v struktury (typ hodnoty):  
  
 [!code-csharp[csProgGuideStatements#20](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-define-value-equality-for-a-type_2.cs)]  
  
 Pro struktury, výchozí implementaci <xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType> (což je přepsané verze v <xref:System.ValueType?displayProperty=nameWithType>) provede kontrolu rovnosti hodnotu pomocí reflexe pro porovnání hodnot každé pole v typu. Při přepsání virtuální implementátor `Equals` metoda v struktury účelem je poskytnout efektivnější způsob kontroly rovnosti hodnotu a volitelně provést porovnání na určitou podmnožinu vlastnosti nebo pole struktura.  
  
 [ == ](../../../csharp/language-reference/operators/equality-comparison-operator.md) a [! =](../../../csharp/language-reference/operators/not-equal-operator.md) operátory nemůže pracovat na struktury, pokud struktura explicitně přetížení.  
  
## <a name="see-also"></a>Viz také  
 [Porovnání rovnosti](../../../csharp/programming-guide/statements-expressions-operators/equality-comparisons.md)  
 [Průvodce programováním v C#](../../../csharp/programming-guide/index.md)
