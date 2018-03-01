---
title: Typy hodnot s povolenou hodnotou Null (Visual Basic)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Nullable
helpviewer_keywords:
- nullable types [Visual Basic]
- '? [Visual Basic]'
- types [Visual Basic], nullable
- nullable types [Visual Basic]
- data types [Visual Basic], nullable
ms.assetid: 9ac3b602-6f96-4e6d-96f7-cd4e81c468a6
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 8734114b9d657066a0ef0b2d648f0290c03b1cbf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="nullable-value-types-visual-basic"></a>Typy hodnot s povolenou hodnotou Null (Visual Basic)
Někdy pracujete s typ hodnoty, který nemá hodnotu definovanou v některých případech. Například na pole v databázi pravděpodobně k rozlišení mezi s přiřazenou hodnotu, která je smysluplný a nemá přiřazenou hodnotu. Typy hodnot lze rozšířit na převedení jejich normální hodnoty, nebo hodnotu null. Toto rozšíření je volána *typ s možnou hodnotou Null*.  
  
 Každý typ s možnou hodnotou Null se vytvářejí na základě obecná <xref:System.Nullable%601> struktura. Vezměte v úvahu databázi, která sleduje aktivity související s práci. Následující příklad vytvoří s možnou hodnotou Null `Boolean` zadejte a deklaruje proměnnou daného typu. Můžete napsat deklaraci třemi způsoby:  
  
 [!code-vb[VbVbalrNullableValue#1](../../../../visual-basic/programming-guide/language-features/data-types/codesnippet/VisualBasic/nullable-value-types_1.vb)]  
  
 Proměnná `ridesBusToWork` mohou být uloženy hodnotu `True`, hodnotu `False`, nebo vůbec žádná hodnota. Počáteční výchozí hodnota je žádná hodnota, která v tomto případě by mohlo znamenat, že informace nebylo dosaženo ještě pro tohoto uživatele. Naproti tomu `False` může znamenat, že byl získán informace a osoba, která není přepravují sběrnici pracovat.  
  
 Je možné deklarovat proměnných a vlastností s typy s možnou hodnotou Null a můžou deklarovat pole elementy typu s povolenou hodnotou Null. Postupy můžou deklarovat s typy s možnou hodnotou null jako parametry, a můžete se vrátit hodnotu Null typu z `Function` postupu.  
  
 Nelze vytvořit typ s možnou hodnotou Null na odkaz na typ například pole, `String`, nebo třídy. Základní typ musí být typ hodnoty. Další informace najdete v tématu [typy hodnot a typy odkazu](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md).  
  
## <a name="using-a-nullable-type-variable"></a>Použití proměnné typ s možnou hodnotou Null  
 Nejdůležitější členy typu s povolenou hodnotou Null jsou jeho <xref:System.Nullable%601.HasValue%2A> a <xref:System.Nullable%601.Value%2A> vlastnosti. Pro proměnnou typu s povolenou hodnotou Null <xref:System.Nullable%601.HasValue%2A> zjistíte, zda proměnná obsahuje hodnotu definované. Pokud <xref:System.Nullable%601.HasValue%2A> je `True`, si můžete přečíst hodnotu z <xref:System.Nullable%601.Value%2A>. Všimněte si, že oba <xref:System.Nullable%601.HasValue%2A> a <xref:System.Nullable%601.Value%2A> jsou `ReadOnly` vlastnosti.  
  
### <a name="default-values"></a>Výchozí hodnoty  
 Když je proměnná deklarovat s typem s možnou hodnotou Null jeho <xref:System.Nullable%601.HasValue%2A> vlastnost má výchozí hodnotu `False`. To znamená, že ve výchozím nastavení proměnná nemá žádnou hodnotu definované, namísto výchozí hodnoty její základní typ hodnoty. V následujícím příkladu, proměnná `numberOfChildren` nemá původně definovanou hodnotu, i když výchozí hodnota `Integer` typ je 0.  
  
 [!code-vb[VbVbalrNullableValue#2](../../../../visual-basic/programming-guide/language-features/data-types/codesnippet/VisualBasic/nullable-value-types_2.vb)]  
  
 Lze použít ke zjištění hodnotu nebo nedefinovanou hodnotu null. Pokud `numberOfChildren` měl byla deklarována jako `Integer`, by existovat žádná hodnota, která může znamenat, že informace není aktuálně k dispozici.  
  
### <a name="storing-values"></a>Ukládání hodnot  
 Hodnotu můžete uložit v proměnné nebo vlastnost s možnou hodnotou Null typu obvyklým způsobem. Následující příklad přiřadí hodnota proměnné `numberOfChildren` deklarované v předchozím příkladu.  
  
 [!code-vb[VbVbalrNullableValue#3](../../../../visual-basic/programming-guide/language-features/data-types/codesnippet/VisualBasic/nullable-value-types_3.vb)]  
  
 Pokud proměnná nebo vlastnost s možnou hodnotou Null typu obsahuje hodnotu definovanou, může způsobit ji vrátit zpátky do původního stavu systému nemá přiřazenu hodnotu. Můžete provést nastavením proměnné nebo vlastnost, která má `Nothing`, jak ukazuje následující příklad.  
  
 [!code-vb[VbVbalrNullableValue#4](../../../../visual-basic/programming-guide/language-features/data-types/codesnippet/VisualBasic/nullable-value-types_4.vb)]  
  
> [!NOTE]
>  I když můžete přiřadit `Nothing` proměnné typu s povolenou hodnotou Null, nelze ho pro testovací `Nothing` pomocí znaménkem rovnosti. Porovnání, které používá znaménku rovná `someVar = Nothing`, vždy se vyhodnocuje `Nothing`. Můžete otestovat proměnné <xref:System.Nullable%601.HasValue%2A> vlastnost pro `False`, nebo otestovat pomocí `Is` nebo `IsNot` operátor.  
  
### <a name="retrieving-values"></a>Načítání hodnot  
 K načtení hodnoty proměnné typu s povolenou hodnotou Null, měli byste nejdřív otestovat jeho <xref:System.Nullable%601.HasValue%2A> vlastnost potvrďte, že má hodnotu. Pokud se pokusíte načíst hodnotu při <xref:System.Nullable%601.HasValue%2A> je `False`, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] vyvolá <xref:System.InvalidOperationException> výjimka. Následující příklad ukazuje doporučeným způsobem, jak načíst proměnnou `numberOfChildren` předchozí příklady.  
  
 [!code-vb[VbVbalrNullableValue#5](../../../../visual-basic/programming-guide/language-features/data-types/codesnippet/VisualBasic/nullable-value-types_5.vb)]  
  
## <a name="comparing-nullable-types"></a>Porovnání typy s možnou hodnotou Null  
 Pokud s možnou hodnotou Null `Boolean` proměnné se používají v logických výrazů, výsledkem mohou být `True`, `False`, nebo `Nothing`. Následuje tabulka pravdivosti pro `And` a `Or`. Protože `b1` a `b2` Teď máte tři možné hodnoty jsou devět kombinace k vyhodnocení.  
  
|B1|B2|B1 a b2|B1 nebo b2|  
|--------|--------|---------------|--------------|  
|`Nothing`|`Nothing`|`Nothing`|`Nothing`|  
|`Nothing`|`True`|`Nothing`|`True`|  
|`Nothing`|`False`|`False`|`Nothing`|  
|`True`|`Nothing`|`Nothing`|`True`|  
|`True`|`True`|`True`|`True`|  
|`True`|`False`|`False`|`True`|  
|`False`|`Nothing`|`False`|`Nothing`|  
|`False`|`True`|`False`|`True`|  
|`False`|`False`|`False`|`False`|  
  
 Pokud je hodnota logická hodnota proměnné nebo výrazu `Nothing`, ani je `true` ani `false`. Podívejte se na následující příklad.  
  
 [!code-vb[VbVbalrNullableValue#6](../../../../visual-basic/programming-guide/language-features/data-types/codesnippet/VisualBasic/nullable-value-types_6.vb)]  
  
 V tomto příkladu `b1 And b2` vyhodnocuje `Nothing`. V důsledku toho `Else` klauzule se spustí v každé `If` příkaz a výstup vypadá takto:  
  
 `Expression is not true`  
  
 `Expression is not false`  
  
> [!NOTE]
>  `AndAlso`a `OrElse`, kteří používají krátká smyčka – vyhodnocení, musí vyhodnotit jejich druhý operandy při první vyhodnocen jako `Nothing`.  
  
## <a name="propagation"></a>Šíření  
 Pokud jeden nebo oba operandy aritmetické, porovnání, shift nebo operaci typ s možnou hodnotou Null, je také výsledek operace s možnou hodnotou Null. Pokud oba operandy obsahují hodnoty, které nejsou `Nothing`, operace proběhne na základní hodnoty operandy, jako kdyby ani typu s povolenou hodnotou Null. V následujícím příkladu, proměnné `compare1` a `sum1` jsou implicitně typované. Pokud je ukazatel myši nad nimi, zobrazí se, že kompilátor odvodí pro oba dva typy s možnou hodnotou Null.  
  
 [!code-vb[VbVbalrNullableValue#7](../../../../visual-basic/programming-guide/language-features/data-types/codesnippet/VisualBasic/nullable-value-types_7.vb)]  
  
 Pokud jeden nebo oba operandy mít hodnotu `Nothing`, výsledkem bude `Nothing`.  
  
 [!code-vb[VbVbalrNullableValue#8](../../../../visual-basic/programming-guide/language-features/data-types/codesnippet/VisualBasic/nullable-value-types_8.vb)]  
  
## <a name="using-nullable-types-with-data"></a>Použití typů s povolenou hodnotou Null s daty  
 Databáze je jedno z vašich nejdůležitějších míst používat typy s možnou hodnotou Null. Ne všechny databázové objekty v současné době podporují typy s možnou hodnotou Null, ale provést adaptéry generované návrháře tabulky. Najdete v části "Podpora TableAdapter typy s možnou hodnotou Null" v [TableAdapter – přehled](/visualstudio/data-tools/tableadapter-overview).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.InvalidOperationException>  
 <xref:System.Nullable%601.HasValue%2A>  
 [Použití typů s povolenou hodnotou Null](../../../../csharp/programming-guide/nullable-types/using-nullable-types.md)  
 [Datové typy](../../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 [Typy hodnot a odkazové typy](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)  
 [Řešení potíží s datové typy](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 [TableAdapter – přehled](/visualstudio/data-tools/tableadapter-overview)  
 [Pokud operátor](../../../../visual-basic/language-reference/operators/if-operator.md)  
 [Odvození místního typu](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)  
 [Is – operátor](../../../../visual-basic/language-reference/operators/is-operator.md)  
 [IsNot – operátor](../../../../visual-basic/language-reference/operators/isnot-operator.md)
