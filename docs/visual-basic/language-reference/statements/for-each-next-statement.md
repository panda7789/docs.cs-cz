---
title: For Each...Next – příkaz (Visual Basic)
ms.date: 07/20/2015
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
ms.openlocfilehash: 269d905ad59a162af4e790e29d3753f090f511bd
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56975001"
---
# <a name="for-eachnext-statement-visual-basic"></a>For Each...Next – příkaz (Visual Basic)
Opakuje skupinu příkazů pro každý prvek v kolekci.  
  
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
|`element`|Vyžaduje `For Each` příkazu. Volitelné v `Next` příkazu. Proměnná. Použít k iteraci prvků kolekce.|  
|`datatype`|Požadováno pokud `element` již není deklarován. Datový typ `element`.|  
|`group`|Povinný parametr. Proměnná typu, který je typ kolekce nebo objekt. Odkazuje na kolekci, nad niž `statements` se bude opakovat.|  
|`statements`|Volitelné. Jeden nebo více příkazů mezi `For Each` a `Next` , která spustí pro každou položku v `group`.|  
|`Continue For`|Volitelné. Přenese ovládací prvek na začátku `For Each` smyčky.|  
|`Exit For`|Volitelné. Přenese ovládací prvek z celkového počtu `For Each` smyčky.|  
|`Next`|Povinný parametr. Ukončí definici `For Each` smyčky.|  
  
## <a name="simple-example"></a>Jednoduchý příklad  
 Použití `For Each`... `Next` smyčky, pokud má být opakován sadu příkazů pro každý prvek kolekce nebo pole.  
  
> [!TIP]
>  A [pro... Další příkaz](../../../visual-basic/language-reference/statements/for-next-statement.md) dobře funguje i při každé iteraci smyčky přidružit řídicí proměnná a určit tuto proměnnou počáteční a konečné hodnoty. Ale při jednání s kolekcí koncept počáteční a konečné hodnoty není smysluplné a neznáte nutně počet prvků kolekci. V takovémto případě `For Each`... `Next` smyčky je často vhodnější použít.  
  
 V následujícím příkladu `For Each`...`Next` příkaz Iteruje přes všechny prvky ze seznamu kolekce.  
  
 [!code-vb[VbVbalrStatements#121](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class9.vb#121)]  
  
 Další příklady najdete v tématu [kolekce](../../../standard/collections/index.md) a [pole](../../../visual-basic/programming-guide/language-features/arrays/index.md).  
  
## <a name="nested-loops"></a>Vnořené smyčky  
 Je možné vnořovat `For Each` smyčky vložením v jednom průchodu v rámci jiného.  
  
 Následující příklad ukazuje vnořené `For Each`...`Next` struktury.  
  
 [!code-vb[VbVbalrStatements#122](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class9.vb#122)]  
  
 Pokud byste vnořit smyčky, každé smyčce musí mít jedinečný `element` proměnné.  
  
 Lze také vnořit různé druhy řídicích struktur v sobě navzájem. Další informace najdete v tématu [vnořené řídicí struktury](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md).  
  
## <a name="exit-for-and-continue-for"></a>Pro ukončení a pokračovat pro  
 [Ukončení pro](../../../visual-basic/language-reference/statements/exit-statement.md) příkaz způsobí spuštění do ukončení `For`...`Next` řízení smyčky a přenosy příkazu, který následuje `Next` příkazu.  
  
 `Continue For` Ovládací prvek příkaz okamžitě přenese na další iteraci smyčky. Další informace najdete v tématu [pokračovat příkaz](../../../visual-basic/language-reference/statements/continue-statement.md).  
  
 Následující příklad ukazuje způsob použití `Continue For` a `Exit For` příkazy.  
  
 [!code-vb[VbVbalrStatements#123](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class9.vb#123)]  
  
 Můžete vložit libovolný počet `Exit For` příkazů v `For Each` smyčky. Při použití v rámci vnořené `For Each` smyčky, `Exit For` způsobí spuštění do ukončení vnitřní smyčky a přenosy ovládacího prvku na další vyšší úroveň vnoření.  
  
 `Exit For` často se používá po vyhodnocení některé podmínky, třeba v `If`... `Then`... `Else` struktury. Můžete chtít použít `Exit For` byly splněny následující podmínky:  
  
-   Pokračování k iteraci je zbytečné nebo nemožné. Příčinou může být chybná hodnota nebo žádost o ukončení.  
  
-   Výjimka zachycena v `Try`... `Catch`... `Finally`. Můžete použít `Exit For` na konci `Finally` bloku.  
  
-   Zde nekonečné smyčky, což je smyčku, která může běžet velká, nebo dokonce neomezený počet pokusů. Pokud zjistíte takové podmínky, můžete použít `Exit For` dostala mimo smyčku. Další informace najdete v tématu [udělat... Smyčky příkaz](../../../visual-basic/language-reference/statements/do-loop-statement.md).  
  
## <a name="iterators"></a>Iterátory  
 Můžete použít *iterátoru* k provedení vlastní iterace nad kolekcí. Iterátor může být způsobená nebo `Get` přistupujícího objektu. Použije `Yield` příkaz k vrácení každého prvku kolekce jeden po druhém.  
  
 Můžete volat iterátor pomocí `For Each...Next` příkazu. Každá iterace `For Each` smyčky volá iterátor. Když `Yield` je dosažen příkaz v iterátoru, výraz v `Yield` příkazu se vrátí, a je zachováno aktuální umístění v kódu. Provádění je restartováno z tohoto umístění při příštím volání iterátoru.  
  
 Následující příklad používá funkce iterátoru. Má funkce iterátoru `Yield` , který se nachází uvnitř [pro... Další](../../../visual-basic/language-reference/statements/for-next-statement.md) smyčky. V `ListEvenNumbers` metodě, každé iterace `For Each` tělo s příkazy vytvoří volání funkce iterátoru, který pokračuje k dalšímu `Yield` příkazu.  
  
 [!code-vb[VbVbalrStatements#127](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class9.vb#127)]  
  
 Další informace najdete v tématu [iterátory](../../programming-guide/concepts/iterators.md), [příkazu Yield](../../../visual-basic/language-reference/statements/yield-statement.md), a [iterátoru](../../../visual-basic/language-reference/modifiers/iterator.md).  
  
## <a name="technical-implementation"></a>Technická implementace  
 Když `For Each`...`Next` příkaz spustí, Visual Basic vyhodnocuje kolekce pouze jednou, než na začátku cyklu. Pokud se změní vaše blok příkazů `element` nebo `group`, tyto změny nemají vliv na iteraci smyčky.  
  
 Pokud všechny prvky v kolekci se postupně přiřadily `element`, `For Each` smyčky zastaví a řídit předá následující příkaz `Next` příkazu.  
  
 Pokud `element` nebyla deklarována mimo tuto smyčku, musíte ji deklarovat v `For Each` příkazu. Je možné deklarovat typ `element` explicitně pomocí `As` příkazu, nebo se můžete spolehnout na odvození typu na typ přiřadit. V obou případech se rozsah `element` tělo smyčky. Nelze však deklarovat `element` mimo a uvnitř smyčky.  
  
 Volitelně můžete zadat `element` v `Next` příkazu. To zlepšuje čitelnost programu, zejména v případě, že budete mít člověk vnořené `For Each` smyčky. Musíte zadat stejnou proměnnou jako ten, který se zobrazí v odpovídající `For Each` příkazu.  
  
 Můžete chtít vyhnout změnou hodnoty `element` uvnitř smyčka. To může to ztížit čtení a ladění kódu. Změna hodnoty `group` nemá vliv na kolekce nebo jeho prvky, které byly určeny při prvním zadání smyčky.  
  
 Pokud jste vnoření smyčky, pokud `Next` příkazu vnější úroveň vnoření dochází před `Next` vnitřní úrovně signály kompilátor chybu. Však kompilátor to zjistit překrývající se chyby pouze v případě, že zadáte `element` v každé `Next` příkazu.  
  
 Pokud váš kód závisí na kolekci v určitém pořadí, procházení `For Each`... `Next` smyčky není nejlepší volbou, pokud si nejste jisti charakteristiky objekt enumerator poskytuje kolekci. Pořadí procházení není určeno jazyka Visual Basic, ale podle <xref:System.Collections.IEnumerator.MoveNext%2A> metodu objektu enumerátor. Proto nebude možné předpovědět, které elementu kolekce, je první má být vrácen v `element`, nebo které je kdy má být vrácen po daného elementu. Můžete dosáhnout pomocí různých smyčce struktura, například spolehlivější výsledky `For`... `Next` nebo `Do`... `Loop`.  
  
 Datový typ `element` musí být takový, datový typ prvků `group` lze převést na ni.  
  
 Datový typ `group` musí být typ odkazu, který odkazuje na kolekci nebo pole, která je vyčíslitelná. Nejčastěji to znamená, že `group` odkazuje na objekt, který implementuje <xref:System.Collections.IEnumerable> rozhraní `System.Collections` oboru názvů nebo <xref:System.Collections.Generic.IEnumerable%601> rozhraní `System.Collections.Generic` oboru názvů. `System.Collections.IEnumerable` definuje <xref:System.Collections.IEnumerable.GetEnumerator%2A> metodu, která vrací objekt enumerátoru pro kolekci. Implementuje objekt enumerator `System.Collections.IEnumerator` rozhraní `System.Collections` obor názvů a zpřístupňuje <xref:System.Collections.IEnumerator.Current%2A> vlastnost a <xref:System.Collections.IEnumerator.Reset%2A> a <xref:System.Collections.IEnumerator.MoveNext%2A> metody. Jazyk Visual Basic používá tyto k procházení kolekce.  
  
### <a name="narrowing-conversions"></a>Zužující převody  
 Když `Option Strict` je nastavena na `On`, zužující převody obvykle způsobí chyby kompilátoru. V `For Each` příkazu, ale převody z prvků v `group` k `element` jsou vyhodnoceny a provést v době běhu a jsou potlačeny chyby kompilátoru způsobené zužujících převodů.  
  
 V následujícím příkladu se přiřazení `m` jako počáteční hodnota pro `n` není při kompilaci `Option Strict` je zapnutý, protože převod `Long` k `Integer` je zužující převod. V `For Each` příkazu, ale žádná chyba kompilátoru je hlášeny, i když přiřazení `number` vyžaduje stejný převod z `Long` k `Integer`. V `For Each` příkazu, který obsahuje velký počet chyb za běhu dochází při <xref:Microsoft.VisualBasic.CompilerServices.Conversions.ToInteger%2A> se použije na velké množství.  
  
 [!code-vb[VbVbalrStatements#89](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class3.vb#89)]  
  
### <a name="ienumerator-calls"></a>IEnumerator volání  
 Při provádění `For Each`... `Next` spuštění cyklu, Visual Basic ověřuje, že `group` odkazuje na objekt platné kolekce. V opačném případě dojde k výjimce. V opačném případě volá <xref:System.Collections.IEnumerator.MoveNext%2A> metoda a <xref:System.Collections.IEnumerator.Current%2A> vlastnost objekt enumerátoru pro vrácení prvního prvku. Pokud `MoveNext` označuje, že neexistuje žádná další prvek, to znamená, pokud kolekce je prázdná, `For Each` smyčky zastaví a řídit předá následující příkaz `Next` příkazu. Jinak, nastaví jazyka Visual Basic `element` na první element a spuštění tohoto bloku příkazů.  
  
 Pokaždé, když zjistí jazyka Visual Basic `Next` prohlášení, vrátí `For Each` příkaz. Znovu volá `MoveNext` a `Current` vrátit další prvek a znovu ho buď blok spustí nebo zastaví smyčky na základě výsledku. Tento proces pokračuje, dokud `MoveNext` označuje, že neexistuje žádná další prvek nebo `Exit For` příkaz dochází.  
  
 **Úprava kolekce.** Enumerátor objekt vrácený rutinou <xref:System.Collections.IEnumerable.GetEnumerator%2A> obvykle neumožňuje změnu kolekce pomocí přidání, odstranění, nahrazení nebo změna pořadí žádné elementy. Pokud se změní kolekce po spuštění `For Each`... `Next` smyčky, objekt enumerator stává neplatným a další pokus o přístup k prvku způsobí, že <xref:System.InvalidOperationException> výjimky.  
  
 Nicméně toto blokování úpravy nelze určit jazyka Visual Basic, ale místo toho provádění <xref:System.Collections.IEnumerable> rozhraní. Je možné implementovat `IEnumerable` způsobem, který umožňuje úpravy během iterace. Pokud uvažujete o provádění takových dynamické úpravy, ujistěte se, že se můžete seznámit s charakteristikou z `IEnumerable` implementaci na kolekce, který používáte.  
  
 **Úprava elementy z kolekce.** <xref:System.Collections.IEnumerator.Current%2A> Vlastností objektu enumerátor je [jen pro čtení](../../../visual-basic/language-reference/modifiers/readonly.md), a vrátí místní kopii každého prvku kolekce. To znamená, že nelze upravit samotné prvky v `For Each`... `Next` smyčky. Všechny změny provedené ovlivňuje pouze místní kopie z `Current` a nereflektují se zpátky do zdrojové kolekce. Ale pokud elementu je typem odkazu, můžete upravit členy instance, na kterou odkazuje. Následující příklad upravuje `BackColor` členem všech `thisControl` elementu. Nelze však změnit `thisControl` samotný.  
  
```vb  
Sub lightBlueBackground(ByVal thisForm As System.Windows.Forms.Form)  
    For Each thisControl As System.Windows.Forms.Control In thisForm.Controls  
        thisControl.BackColor = System.Drawing.Color.LightBlue  
    Next thisControl  
End Sub  
```  
  
 V předchozím příkladu můžete změnit `BackColor` členem všech `thisControl` elementu, i když ho nelze změnit `thisControl` samotný.  
  
 **Procházení pole.** Protože <xref:System.Array> implementuje třída <xref:System.Collections.IEnumerable> vystavit rozhraní, všechna pole <xref:System.Array.GetEnumerator%2A> metoda. To znamená, že můžete iterovat pole `For Each`... `Next` smyčky. Prvky pole však můžete pouze číst. Nelze je změnit.  
  
## <a name="example"></a>Příklad  
 Následující příklad vypíše všechny složky v adresáři C:\ s použitím <xref:System.IO.DirectoryInfo> třídy.  
  
 [!code-vb[VbVbalrStatements#124](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class9.vb#124)]  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje postup při řazení kolekce. Příklad řadí instance třídy `Car` třídy, které jsou uložené v <xref:System.Collections.Generic.List%601>. `Car` Implementuje třída <xref:System.IComparable%601> rozhraní, které vyžaduje, aby <xref:System.IComparable%601.CompareTo%2A> implementaci metody.  
  
 Každé volání <xref:System.IComparable%601.CompareTo%2A> metoda provádí jedno porovnání, který se používá pro řazení. Uživatelem zapsaný kód v `CompareTo` metoda vrátí hodnotu pro všechna porovnání aktuálního objektu s jiným objektem. Vrácená hodnota je menší než nula, pokud se aktuální objekt menší než druhý objekt, větší než nula, pokud je aktuální objekt větší než druhý objekt a nula jestli jsou shodné. To umožňuje v kódu definovat kritéria pro větší, menší než a rovná.  
  
 V `ListCars` metody, `cars.Sort()` příkaz Seřadí seznam. Toto volání <xref:System.Collections.Generic.List%601.Sort%2A> metodu <xref:System.Collections.Generic.List%601> způsobí, že `CompareTo` metoda bude automaticky volána pro `Car` objekty v `List`.  
  
 [!code-vb[VbVbalrStatements#125](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class9.vb#125)]  
  
## <a name="see-also"></a>Viz také:
- [Kolekce](../../../standard/collections/index.md)
- [Příkaz For...Next](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [Struktury smyčky](../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [Příkaz While...End While](../../../visual-basic/language-reference/statements/while-end-while-statement.md)
- [Příkaz Do...Loop](../../../visual-basic/language-reference/statements/do-loop-statement.md)
- [Rozšíření a zúžení převodů](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [Inicializátory objektů: Pojmenované a anonymní typy](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [Inicializátory kolekcí](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md)
- [Pole](../../../visual-basic/programming-guide/language-features/arrays/index.md)
