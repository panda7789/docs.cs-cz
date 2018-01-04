---
title: "For Each...Next – příkaz (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.ForEach
- vb.ForEachNext
- vb.Each
- ForEachNext
helpviewer_keywords:
- infinite loops
- Next statement [Visual Basic], For Each...Next
- endless loops
- loop structures [Visual Basic], For Each...Next
- loops, endless
- Each keyword [Visual Basic]
- instructions, repeating
- For Each statement [Visual Basic]
- collections, instruction repetition
- loops, infinite
- For Each...Next statements
- For keyword [Visual Basic], For Each...Next statements
- Exit statement [Visual Basic], For Each...Next statements
- iteration
ms.assetid: ebce3120-95c3-42b1-b70b-fa7da40c75e2
caps.latest.revision: "56"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 11601eb1caad1c6cc6d9898f590436a977a78fa1
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="for-eachnext-statement-visual-basic"></a>For Each...Next – příkaz (Visual Basic)
Opakuje skupinu příkazů pro jednotlivé elementy v kolekci.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
For Each element [ As datatype ] In group  
    [ statements ]  
    [ Continue For ]  
    [ statements ]  
    [ Exit For ]  
    [ statements ]  
Next [ element ]  
```  
  
## <a name="parts"></a>Součásti  
  
|Termín|Definice|  
|---|---|  
|`element`|V požadované `For Each` příkaz. Volitelné v `Next` příkaz. Proměnná. Použít k iteraci v rámci prvků kolekce.|  
|`datatype`|Požadováno pokud `element` již není deklarovaný. Datový typ `element`.|  
|`group`|Požadováno. Proměnná s typem, který je typu kolekce nebo objekt. Odkazuje na kolekci, za které `statements` k opakování.|  
|`statements`|Volitelné. Jeden nebo více příkazů mezi `For Each` a `Next` , spusťte na každou položku v `group`.|  
|`Continue For`|Volitelné. Přenosy ovládacího prvku na spuštění `For Each` smyčky.|  
|`Exit For`|Volitelné. Přenosy ovládacího prvku mimo `For Each` smyčky.|  
|`Next`|Požadováno. Ukončí definice `For Each` smyčky.|  
  
## <a name="simple-example"></a>Jednoduchý příklad  
 Použití `For Each`... `Next` cykly, pokud chcete sadu příkazů opakujte pro každý prvek kolekce nebo pole.  
  
> [!TIP]
>  A [pro... Další příkaz](../../../visual-basic/language-reference/statements/for-next-statement.md) dobře funguje při každé iteraci smyčky přidružit řídicí proměnná a určit hodnoty počáteční a finální tuto proměnnou. Ale když pracujete s kolekcí, koncept počáteční a finální hodnoty není smysluplný a neznáte nutně kolik elementů v kolekci nachází. V tento druh případě `For Each`... `Next` smyčka je často lepší volbou.  
  
 V následujícím příkladu `For Each`...`Next` příkaz iteruje všechny elementy kolekce seznamu.  
  
 [!code-vb[VbVbalrStatements#121](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/for-each-next-statement_1.vb)]  
  
 Další příklady najdete v tématu [kolekce](../../../standard/collections/index.md) a [pole](../../../visual-basic/programming-guide/language-features/arrays/index.md).  
  
## <a name="nested-loops"></a>Vnořené smyčky  
 Lze vnořit `For Each` smyčky umístěním jednoho smyčky v rámci jiného.  
  
 Následující příklad ukazuje vnořené `For Each`...`Next` struktury.  
  
 [!code-vb[VbVbalrStatements#122](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/for-each-next-statement_2.vb)]  
  
 Pokud je vnořovat smyčky, každou smyčku musí mít jedinečnou `element` proměnné.  
  
 Můžete také vnořovat různé druhy řídicí struktury v rámci navzájem. Další informace najdete v tématu [vnořené řídicí struktury](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md).  
  
## <a name="exit-for-and-continue-for"></a>Pro ukončení a pokračovat pro  
 [Ukončení pro](../../../visual-basic/language-reference/statements/exit-statement.md) příkaz způsobuje provádění ukončíte `For`...`Next` smyčky a přenosy ovládacího prvku do příkazu, který odpovídá `Next` příkaz.  
  
 `Continue For` Řízení příkaz okamžitě přenese do další iterace smyčky. Další informace najdete v tématu [pokračovat příkaz](../../../visual-basic/language-reference/statements/continue-statement.md).  
  
 Následující příklad ukazuje, jak používat `Continue For` a `Exit For` příkazy.  
  
 [!code-vb[VbVbalrStatements#123](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/for-each-next-statement_3.vb)]  
  
 Můžete použít a zadat libovolný počet `Exit For` příkazy v `For Each` smyčky. Při použití uvnitř vnořené `For Each` smyčky, `Exit For` způsobí, že provádění ukončíte nejvnitřnější smyčky a přenosy ovládacího prvku na další vyšší úroveň vnoření.  
  
 `Exit For`se často používá po vyhodnocení některé podmínky, například v `If`... `Then`... `Else` struktura. Můžete chtít použít `Exit For` byly splněny následující podmínky:  
  
-   Pokračovat v procházení je zbytečné nebo dokonce znemožňují. Příčinou může být chybná hodnota nebo žádost o ukončení.  
  
-   Výjimka zachycena v `Try`... `Catch`... `Finally`. Můžete použít `Exit For` na konci `Finally` bloku.  
  
-   Zde nekonečnou smyčku, což je smyčku, který by mohl spustit velký, nebo i nekonečné stanovený počet. Pokud zjistíte takové podmínky, můžete použít `Exit For` abyste se vyhnuli smyčky. Další informace najdete v tématu [provést... Cykly příkaz](../../../visual-basic/language-reference/statements/do-loop-statement.md).  
  
## <a name="iterators"></a>Iterátory  
 Můžete použít *iterator* k provedení vlastní iteraci přes kolekci. Iterace může být funkce nebo `Get` přistupujícího objektu. Použije `Yield` příkaz vrátit každý prvek kolekce, jeden v čase.  
  
 Volání iterovat pomocí `For Each...Next` příkaz. Každé iteraci `For Each` volá iteraci smyčky. Při `Yield` příkaz je dosaženo v iterator, výraz ve `Yield` se vrátí příkaz a zůstane aktuální umístění v kódu. Provádění restartování z tohoto umístění příštím iteraci je volána.  
  
 Následující příklad používá funkci iterator. Funkce iterator má `Yield` příkaz, který je uvnitř [pro... Další](../../../visual-basic/language-reference/statements/for-next-statement.md) smyčky. V `ListEvenNumbers` metoda, každé iteraci `For Each` těla příkazu vytvoří volání funkce iterator, který bude pokračovat na další `Yield` příkaz.  
  
 [!code-vb[VbVbalrStatements#127](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/for-each-next-statement_4.vb)]  
  
 Další informace najdete v tématu [iterátory](../../programming-guide/concepts/iterators.md), [Yield – příkaz](../../../visual-basic/language-reference/statements/yield-statement.md), a [Iterator](../../../visual-basic/language-reference/modifiers/iterator.md).  
  
## <a name="technical-implementation"></a>Technická implementace  
 Když `For Each`...`Next` příkaz spustí, Visual Basic vyhodnotí kolekce pouze jednou, před zahájením smyčky. Pokud se změní váš příkaz bloku `element` nebo `group`, tyto změny neovlivňují iteraci smyčky.  
  
 Pokud všechny elementy v kolekci se postupně přiřadily `element`, `For Each` cykly zastaví a řídit předává pro následující příkaz `Next` příkaz.  
  
 Pokud `element` nebyla deklarována mimo tento ve smyčce, je potřeba deklarovat v `For Each` příkaz. Je možné deklarovat typ `element` explicitně pomocí `As` prohlášení, nebo můžete spoléhat na odvození typu přiřadit typu. V obou případech oboru `element` je do těla smyčky. Však nelze deklarovat `element` mimo i uvnitř smyčky.  
  
 Volitelně můžete zadat `element` v `Next` příkaz. Tím se zlepšuje čitelnost vašeho programu, zejména v případě, že budete mít člověk vnořené `For Each` smyčky. Musíte zadat stejnou proměnnou jako ten, který se zobrazí v odpovídající `For Each` příkaz.  
  
 Můžete chtít vyhnout změně hodnotu `element` uvnitř smyčku. To může být obtížné číst a ladění kódu. Změna hodnoty `group` nemá vliv kolekci nebo jeho prvky, které se zjistilo, že při prvním zadání smyčky.  
  
 Pokud jste vnoření smyčky, pokud `Next` příkaz vnější úrovně vnoření je zjistil před `Next` vnitřní úrovně kompilátor nevydá signál k chybě. Ale kompilátor to zjistit překrývající se chyby pouze v případě, že zadáte `element` v každé `Next` příkaz.  
  
 Pokud váš kód závisí na procházející kolekci v určitém pořadí, `For Each`... `Next` smyčky není nejlepší volbou, pokud si nejste jisti charakteristiky objekt enumerator zpřístupní kolekce. Pořadí traversal není určeno jazyka Visual Basic, ale pomocí <xref:System.Collections.IEnumerator.MoveNext%2A> metodu objektu enumerátor. Proto není možné předpovědět, který element kolekce je první, vrátí se `element`, nebo které mají být vráceny po daného elementu na další. Může dosáhnout větší spolehlivost výsledky pomocí struktury různých smyčky, například `For`... `Next` nebo `Do`... `Loop`.  
  
 Datový typ `element` musí být tak, že datový typ elementů `group` lze převést na ni.  
  
 Datový typ `group` musí být typu odkaz, který odkazuje na kolekci nebo pole, které je vyčíslitelná. Nejčastěji to znamená, že `group` odkazuje na objekt, který implementuje <xref:System.Collections.IEnumerable> rozhraní `System.Collections` oboru názvů nebo <xref:System.Collections.Generic.IEnumerable%601> rozhraní `System.Collections.Generic` oboru názvů. `System.Collections.IEnumerable`definuje <xref:System.Collections.IEnumerable.GetEnumerator%2A> metodu, která vrací objekt enumerátoru pro kolekci. Implementuje objekt enumerator `System.Collections.IEnumerator` rozhraní `System.Collections` obor názvů a zveřejňuje <xref:System.Collections.IEnumerator.Current%2A> vlastnost a <xref:System.Collections.IEnumerator.Reset%2A> a <xref:System.Collections.IEnumerator.MoveNext%2A> metody. Visual Basic používá následující procházení kolekce.  
  
### <a name="narrowing-conversions"></a>Zužující převody  
 Když `Option Strict` je nastaven na `On`, zužující převody normálně způsobit chyby kompilátoru. V `For Each` příkaz, ale převody z elementů v `group` k `element` jsou vyhodnotit a provést v době běhu, a jsou potlačeny chyby kompilátoru způsobené zužující převody.  
  
 V následujícím příkladu, přiřazení `m` jako počáteční hodnotu pro `n` není při kompilaci `Option Strict` totiž na převod `Long` k `Integer` je zužující převod. V `For Each` příkaz, ale je žádná chyba kompilátoru nahlásí, i když přiřazení `number` vyžaduje stejné převod `Long` k `Integer`. V `For Each` nastane chyba spuštění příkazu, který obsahuje hodně, když <xref:Microsoft.VisualBasic.CompilerServices.Conversions.ToInteger%2A> se použije pro velký počet.  
  
 [!code-vb[VbVbalrStatements#89](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/for-each-next-statement_5.vb)]  
  
### <a name="ienumerator-calls"></a>IEnumerator volání  
 Při provádění `For Each`... `Next` spuštění cyklu, Visual Basic ověřuje, že `group` odkazuje na objekt platnou kolekci. Pokud ne, vyvolá výjimku. Jinak, zavolá <xref:System.Collections.IEnumerator.MoveNext%2A> metoda a <xref:System.Collections.IEnumerator.Current%2A> vlastnost objekt enumerator vrátit první prvek. Pokud `MoveNext` Určuje, že neexistuje žádná další prvek, to znamená, pokud je kolekce prázdná, `For Each` cykly zastaví a řídit předává pro následující příkaz `Next` příkaz. Jinak, nastaví jazyka Visual Basic `element` první prvek a spustí příkaz bloku.  
  
 Pokaždé, když komunikaci jazyka Visual Basic `Next` příkaz vrátí `For Each` příkaz. Znovu volá `MoveNext` a `Current` vrátí na další prvek a znovu ji buď běží bloku nebo zastaví smyčky v závislosti na výsledku. Tento proces pokračuje, dokud `MoveNext` Určuje, že neexistuje žádná další prvek nebo `Exit For` příkaz je zjistil.  
  
 **Úpravy kolekce.** Objekt enumerator vrácený <xref:System.Collections.IEnumerable.GetEnumerator%2A> obvykle není umožňují změnit kolekci přidáním, odstraněním, nahraďte nebo změna žádné elementy. Pokud změníte kolekci po spuštění `For Each`... `Next` smyčky, objekt enumerator stává neplatným a další pokus o přístup k elementu způsobí, že <xref:System.InvalidOperationException> výjimka.  
  
 Toto blokování změny ale není určen podle [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)], ale spíše implementace <xref:System.Collections.IEnumerable> rozhraní. Je možné implementovat `IEnumerable` způsobem, který umožňuje upravovat během iterace. Pokud uvažujete o provádění takových dynamické úpravy, ujistěte se, že rozumíte charakteristika `IEnumerable` implementace na kolekci, kterou používáte.  
  
 **Úpravy elementy z kolekce.** <xref:System.Collections.IEnumerator.Current%2A> Vlastností objektu enumerátor je [jen pro čtení](../../../visual-basic/language-reference/modifiers/readonly.md), a vrátí místní kopii každého prvku kolekce. To znamená, že nelze upravovat samotné prvky v `For Each`... `Next` smyčky. Všechny úpravy provedete ovlivňují jenom místní kopie z `Current` a nereflektují zpět do základní kolekce. Ale pokud element je typu odkaz, můžete upravit členy instance, na kterou odkazuje. Následující příklad změní `BackColor` členem všech `thisControl` elementu. Nelze, ale upravovat `thisControl` sám sebe.  
  
```vb  
Sub lightBlueBackground(ByVal thisForm As System.Windows.Forms.Form)  
    For Each thisControl As System.Windows.Forms.Control In thisForm.Controls  
        thisControl.BackColor = System.Drawing.Color.LightBlue  
    Next thisControl  
End Sub  
```  
  
 Předchozí příklad můžete upravit `BackColor` členem všech `thisControl` elementu, i když ho nelze změnit `thisControl` sám sebe.  
  
 **Procházení pole.** Protože <xref:System.Array> třída implementuje <xref:System.Collections.IEnumerable> vystavit rozhraní, všechna pole <xref:System.Array.GetEnumerator%2A> metoda. To znamená, že můžete iterovat pole s `For Each`... `Next` smyčky. Však může číst pouze elementy pole. Nelze je změnit.  
  
## <a name="example"></a>Příklad  
 Následující příklad vypíše všechny složky v adresáři C:\ pomocí <xref:System.IO.DirectoryInfo> třídy.  
  
 [!code-vb[VbVbalrStatements#124](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/for-each-next-statement_6.vb)]  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje postup pro řazení kolekce. V příkladu seřadí instancí `Car` třídy, které jsou uložené v <xref:System.Collections.Generic.List%601>. `Car` Třída implementuje <xref:System.IComparable%601> rozhraní, které vyžaduje, aby <xref:System.IComparable%601.CompareTo%2A> být implementována metoda.  
  
 Každé volání <xref:System.IComparable%601.CompareTo%2A> metoda umožňuje jedno porovnání, který se používá pro řazení. Uživatel zapsat kód v `CompareTo` metoda vrátí hodnotu pro každou porovnání aktuální objekt s jiným objektem. Hodnota vrácená je menší než nula. Pokud je aktuální objekt menší než druhý objekt, větší než nula. Pokud se aktuální objekt větší než druhý objekt a nula. Pokud jsou stejné. To umožňuje definovat kritéria pro větší než je menší než v kódu a rovnat.  
  
 V `ListCars` metody `cars.Sort()` příkaz Seřadí seznam. Volání <xref:System.Collections.Generic.List%601.Sort%2A> metodu <xref:System.Collections.Generic.List%601> způsobí, že `CompareTo` metoda má být automaticky volána pro `Car` objekty v `List`.  
  
 [!code-vb[VbVbalrStatements#125](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/for-each-next-statement_7.vb)]  
  
## <a name="see-also"></a>Viz také  
 [Kolekce](../../../standard/collections/index.md)  
 [Příkaz For...Next](../../../visual-basic/language-reference/statements/for-next-statement.md)  
 [Struktury smyčky](../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)  
 [Příkaz While...End While](../../../visual-basic/language-reference/statements/while-end-while-statement.md)  
 [Příkaz Do...Loop](../../../visual-basic/language-reference/statements/do-loop-statement.md)  
 [Rozšíření a zúžení převodů](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)  
 [Inicializátory objektů: pojmenované a anonymní typy](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)  
 [Inicializátory kolekcí](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md)  
 [Pole](../../../visual-basic/programming-guide/language-features/arrays/index.md)
