---
title: Příkazy v jazyce Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], declaring
- colons (:) [Visual Basic]
- constants [Visual Basic], defining
- underlines
- constants [Visual Basic], statements
- blue underline [Visual Basic]
- procedures [Visual Basic], statements
- variables [Visual Basic], assigning
- line breaks [Visual Basic], in code
- executable statements [Visual Basic]
- variables [Visual Basic], defining
- statements [Visual Basic], about statements
ms.assetid: fcfdee1a-82b7-4846-98f7-9ca3f5160089
ms.openlocfilehash: e66acae5e98d561883f4ad59853dfd862c8ebfee
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43506287"
---
# <a name="statements-in-visual-basic"></a>Příkazy v jazyce Visual Basic

Příkaz v jazyce Visual Basic je kompletní instrukce. Může obsahovat klíčová slova, operátory, proměnné, konstanty a výrazy. Každý příkaz patří k jednomu z následujících kategorií:

- **Příkazy deklarace**, název proměnné, konstanty nebo postupu a můžete také zadat datový typ.

- **Spustitelné příkazy**, který zahájení akce. Tyto příkazy může volat metody nebo funkce, a můžete opakovat nebo prostřednictvím bloky kódu. Spustitelné příkazy zahrnují **přiřazovací příkazy**, který přiřadit hodnota nebo výraz proměnnou nebo konstantu.

Toto téma popisuje každou kategorii. Toto téma popisuje taky, jak kombinovat více příkazů na jednom řádku a pokračujte příkaz více řádcích.

## <a name="declaration-statements"></a>Příkazy deklarace

Příkazy deklarace použijete název a definovat postupy, proměnných, vlastností, polí a konstanty. Když deklarujete programový element, můžete také definovat jeho datový typ, úroveň přístupu a rozsahu. Další informace najdete v tématu [deklarované charakteristiky elementu](./declared-elements/declared-element-characteristics.md).

Následující příklad obsahuje tři deklarace.

[!code-vb[VbVbalrStatements#80](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#80)]

První deklarace `Sub` příkazu. Společně s jeho odpovídajícím `End Sub` příkazu deklaruje proceduru s názvem `applyFormat`. Také určuje, že `applyFormat` je `Public`, což znamená, že veškerý kód, který na ni můžete odkazovat lze volat.

Druhý deklarace je `Const` příkazu, který deklaruje konstanty `limit`, zadání `Integer` datový typ a hodnotu 33.

Třetí deklarace je `Dim` příkazu, který deklaruje proměnnou `thisWidget`. Datový typ je s určitým objektem, konkrétně vytvoří objekt z `Widget` třídy. Můžete deklarovat proměnnou typu základní datové nebo libovolný typ objektu, který je přístupný v aplikaci, kterou používáte.

### <a name="initial-values"></a>Počáteční hodnoty

Při spuštění kódu obsahující příkazu deklarace, Visual Basic rezervuje paměť potřebnou pro element deklarovaný. Pokud element obsahuje hodnotu, Visual Basic se inicializuje na výchozí hodnotu pro daný datový typ. Další informace najdete v tématu "Chování" [příkazu Dim](../../language-reference/statements/dim-statement.md).

Počáteční hodnotu můžete přiřadit k proměnné jako součást její deklarace, jak ukazuje následující příklad.

[!code-vb[VbVbalrStatements#81](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#81)]

Pokud je proměnná proměnné objektu, můžete explicitně vytvořit instance své třídy při deklaraci pomocí [operátor New](../../../visual-basic/language-reference/operators/new-operator.md) – klíčové slovo, jako následující příklad ukazuje.

[!code-vb[VbVbalrStatements#82](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#82)]

Všimněte si, že počáteční hodnotu, kterou jste zadali v příkazu deklarace není přiřazen k proměnné, dokud provádění dosáhne příkazu jeho deklarace. Do té doby proměnná obsahuje výchozí hodnotu pro jeho datového typu.

## <a name="executable-statements"></a>Spustitelné příkazy

Byl spustitelný příkaz provede akci. Dokáže volání procedury, větve na jiné místo v kódu, projděte několik příkazů nebo vyhodnocení výrazu. Přiřazovací příkaz je zvláštní případ byl spustitelný příkaz.

Následující příklad používá `If...Then...Else` řízení struktury spustit různé bloky kódu na základě hodnoty proměnné. V rámci každého bloku kódu `For...Next` cyklu zadaného počtu opakování.

[!code-vb[VbVbalrStatements#83](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#83)]

`If` Příkaz v předchozím příkladu zkontroluje hodnotu parametru `clockwise`. Pokud je hodnota `True`, zavolá `spinClockwise` metoda `aWidget`. Pokud je hodnota `False`, zavolá `spinCounterClockwise` metoda `aWidget`. `If...Then...Else` Řídicí struktura končí `End If`.

`For...Next` Smyčky v rámci každého bloku volá příslušnou metodu s počtem opakování rovná hodnotě `revolutions` parametru.

## <a name="assignment-statements"></a>Příkazy přiřazení

Přiřazovací příkazy provádějí operace přiřazení, které tvoří převodu hodnoty na pravé straně operátoru přiřazení (`=`) a jeho uložení v elementu na levé straně, jako v následujícím příkladu.

[!code-vb[VbVbalrStatements#73](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#73)]

V předchozím příkladu přiřazovací příkaz uloží hodnotu literálu 42 v proměnné `v`.

### <a name="eligible-programming-elements"></a>Oprávněné programovací prvky

Programovací element na levé straně operátoru přiřazení musí být schopen přijmout a uložit hodnotu. To znamená, že musí být proměnná nebo vlastnost, která není [jen pro čtení](../../../visual-basic/language-reference/modifiers/readonly.md), nebo musí být k elementu pole. V rámci příkazu přiřazení, se někdy označuje jako takový prvek *l-hodnoty*, pro "vlevo hodnota".

Výraz, který může obsahovat libovolnou kombinaci literály, konstant, proměnných, vlastnosti, prvky pole, další výrazy nebo volání funkce vygeneruje hodnotu na pravé straně operátoru přiřazení. Toto dokládá následující příklad.

[!code-vb[VbVbalrStatements#74](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#74)]

Předchozí příklad přidá hodnotu obsaženou referenčním proměnné `y` hodnoty uložené v proměnné `z`a pak přidá hodnoty vrácené z volání funkce `findResult`. Celková hodnota tohoto výrazu se pak ukládá v proměnné `x`.

### <a name="data-types-in-assignment-statements"></a>Datové typy v příkazy přiřazení

Kromě číselných hodnot, můžete také přiřadit operátor přiřazení `String` hodnoty, jak ukazuje následující příklad.

[!code-vb[VbVbalrStatements#75](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#75)]

Můžete také přiřadit `Boolean` hodnoty, buď pomocí `Boolean` literálu nebo `Boolean` ukazuje výraz, stejně jako v následujícím příkladu.

[!code-vb[VbVbalrStatements#76](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#76)]

Podobně můžete přiřadit příslušné hodnoty pro programovací prvky `Char`, `Date`, nebo `Object` datového typu. Můžete také přiřadit instance objektu na element deklarovaný jako třídy, ze kterého se vytvoří tuto instanci.

### <a name="compound-assignment-statements"></a>Příkazy složeného přiřazení

*Složené příkazy přiřazení* nejprve provádění operací na výrazu před přiřazením na programovací prvek. Následující příklad ukazuje jednu z těchto operátorů `+=`, který zvýší hodnotu proměnné na levé straně operátoru podle hodnoty výrazu na pravé straně.

[!code-vb[VbVbalrStatements#77](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#77)]

V předchozím příkladu přičte 1 k hodnotě `n`a pak uloží novou hodnotu v `n`. Je sdružená vlastnost ekvivalentem následujícího příkazu:

[!code-vb[VbVbalrStatements#78](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#78)]

Různé operace složeného přiřazení je možné provádět pomocí operátorů tohoto typu. Seznam těchto operátorů a další informace o nich najdete v tématu [operátory přiřazení](../../../visual-basic/language-reference/operators/assignment-operators.md).

Operátor přiřazení zřetězení (`&=`) je užitečné pro přidání řetězce na konec objektu již existující řetězce, jak ukazuje následující příklad.

[!code-vb[VbVbalrStatements#79](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#79)]

### <a name="type-conversions-in-assignment-statements"></a>Převody typů v příkazy přiřazení

Hodnota, kterou přiřadíte proměnná, vlastnost nebo element pole musí být datového typu, který je vhodný pro tento cílový element. Obecně se pokuste generuje hodnotu stejný datový typ jako cílový element. Některé typy lze převést na jiné typy, ale během přiřazování.

Informace o převodu mezi datovými typy najdete v tématu [převody typů v jazyce Visual Basic](./data-types/type-conversions.md). V krátkosti Visual Basic automaticky převede hodnotu daného typu na jiný typ, ke kterému rozšiřuje. A *rozšiřující převod* je v, který je vždy úspěšné v době běhu a neztratí žádná data. Například Visual Basic převede `Integer` hodnota, která se `Double` vhodných, protože `Integer` rozšiřuje na `Double`. Další informace najdete v tématu [Widening a zúžení převodů](./data-types/widening-and-narrowing-conversions.md).

*Zužující převody* (ty, které nejsou rozšiřující) provádět riziko selhání za běhu nebo ztráty. Je zužující převod provést explicitně pomocí funkce převodu typu, nebo může směrovat kompilátor provést všechny převody implicitně nastavením `Option Strict Off`. Další informace najdete v tématu [implicitní a explicitní převody](./data-types/implicit-and-explicit-conversions.md).

## <a name="putting-multiple-statements-on-one-line"></a>Vložení více příkazů na jednom řádku

Můžete mít více příkazů na jednom řádku oddělené dvojtečkou (`:`) znaků. Toto dokládá následující příklad.

[!code-vb[VbVbalrStatements#70](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#70)]

I když občas praktické, tato forma syntaxe díky kódu špatně čitelná a udržovat. Proto doporučujeme ponechat jeden příkaz na řádek.

## <a name="continuing-a-statement-over-multiple-lines"></a>Pokračování příkaz přes více řádků

Příkaz obvykle vešel na jeden řádek, ale když je příliš dlouhý, můžete ho pokračovat na další řádek pomocí posloupností pokračování řádku, který se skládá z mezerou následovanou znakem podtržítka (`_`) následované zalomení řádku. V následujícím příkladu `MsgBox` spustitelný příkaz pokračuje více než dva řádky.

[!code-vb[VbVbalrStatements#71](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#71)]

### <a name="implicit-line-continuation"></a>Implicitní pokračování řádku

V mnoha případech můžete příkaz pokračovat na dalším řádku za sebou bez použití znak podtržítka (`_`). Příkaz následující prvky syntaxe implicitně pokračovat na další řádek kódu.

- Za čárkou (`,`). Příklad:

   [!code-vb[VbVbalrLineContinuation#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#1)]

- Za levou (otevírací) (`(`) nebo před závorky (`)`). Příklad:

   [!code-vb[VbVbalrLineContinuation#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#2)]

- Po otevřené složené závorky (`{`) nebo před uzavírací složenou závorku (`}`). Příklad:

    [!code-vb[VbVbalrLineContinuation#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#3)]

    Další informace najdete v tématu [inicializátory objektů: pojmenované a anonymní typy](./objects-and-classes/object-initializers-named-and-anonymous-types.md) nebo [inicializátory kolekce](./collection-initializers/index.md).

- Po otevření vložený výraz (`<%=`) nebo před uzavřením vloženého výrazu (`%>`) v rámci literál XML. Příklad:

   [!code-vb[VbVbalrLineContinuation#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#4)]

   Další informace najdete v tématu [vložené výrazy v XML](./xml/embedded-expressions-in-xml.md).

- Po operátoru pro zřetězení (`&`). Příklad:

   [!code-vb[VbVbcnConventions#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/vb/Class1.vb#9)]

   Další informace najdete v tématu [operátory uvedené podle funkce](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md).

- Za operátory přiřazení (`=`, `&=`, `:=`, `+=`, `-=`, `*=`, `/=`, `\=`, `^=`, `<<=`, `>>=`). Příklad:

   [!code-vb[VbVbalrLineContinuation#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#5)]

   Další informace najdete v tématu [operátory uvedené podle funkce](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md).

- Za binární operátory (`+`, `-`, `/`, `*`, `Mod`, `<>`, `<`, `>`, `<=`, `>=`, `^`, `>>`, `<<`, `And`, `AndAlso`, `Or`, `OrElse`, `Like`, `Xor`) v rámci výrazu. Příklad:

   [!code-vb[VbVbalrLineContinuation#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#7)]

   Další informace najdete v tématu [operátory uvedené podle funkce](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md).

- Po `Is` a `IsNot` operátory. Příklad:

   [!code-vb[VbVbalrLineContinuation#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#8)]

   Další informace najdete v tématu [operátory uvedené podle funkce](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md).

- Za znakem kvalifikátor člena (`.`) a před názvem člena. Příklad:

   [!code-vb[VbVbalrLineContinuation#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#5)]

   Ale musí obsahovat znak pro pokračování řádku (`_`) následující znak kvalifikátor člen při použití `With` příkazu nebo zadáním hodnot v seznamu inicializace pro typ. Rozdělení řádku za operátor přiřazení (například `=`) při používání `With` příkazy nebo objekt inicializační seznamy. Příklad:

   [!code-vb[VbVbalrLineContinuation#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#14)]

   Další informace najdete v tématu [s... End With – příkaz](../../../visual-basic/language-reference/statements/with-end-with-statement.md) nebo [inicializátory objektů: pojmenované a anonymní typy](./objects-and-classes/object-initializers-named-and-anonymous-types.md).

- Po kvalifikátor vlastnosti osy XML (`.` nebo `.@` nebo `...`). Ale musí obsahovat znak pro pokračování řádku (`_`) při zadání člen kvalifikátor při použití `With` – klíčové slovo. Příklad:

   [!code-vb[VbVbalrLineContinuation#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#9)]

   Další informace najdete v tématu [vlastnosti osy XML](../../../visual-basic/language-reference/xml-axis/index.md).

- Po méně – znaménko (<) nebo před větší-než znaménko (`>`) Pokud zadáte atribut. Také po větší-než znaménko (`>`) Pokud zadáte atribut. Ale musí obsahovat znak pro pokračování řádku (`_`) při zadání atributy úrovně sestavení nebo na úrovni modulu. Příklad:

   [!code-vb[VbVbalrLineContinuation#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#10)]

   Další informace najdete v tématu [atributy přehled](../../../visual-basic/programming-guide/concepts/attributes/index.md).

- Před a za operátory dotazu (`Aggregate`, `Distinct`, `From`, `Group By`, `Group Join`, `Join`, `Let`, `Order By`, `Select`, `Skip`, `Skip While`, `Take`, `Take While`, `Where`, `In`, `Into`, `On`, `Ascending`, a `Descending`). Nelze přerušit čáru mezi klíčová slova operátorů dotazu, které jsou tvořeny z více klíčových slov (`Order By`, `Group Join`, `Take While`, a `Skip While`). Příklad:

   [!code-vb[VbVbalrLineContinuation#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#11)]

   Další informace najdete v tématu [dotazy](../../../visual-basic/language-reference/queries/index.md).

- Po `In` – klíčové slovo v `For Each` příkazu. Příklad:

   [!code-vb[VbVbalrLineContinuation#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#12)]

   Další informace najdete v tématu [For Each... Další příkaz](../../../visual-basic/language-reference/statements/for-each-next-statement.md).

- Po `From` – klíčové slovo v incializátoru kolekce. Příklad:

   [!code-vb[VbVbalrLineContinuation#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#13)]

   Další informace najdete v tématu [inicializátory kolekce](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md).

## <a name="adding-comments"></a>Přidávání komentářů

Zdrojový kód není vždy zřejmé, dokonce i na programátorovi, kdo ho napsal. Abychom zdokumentujte svůj kód, proto většina programátoři využít benevolentní vložené komentáře. Komentáře v kódu se vysvětlují postup nebo konkrétní pokyny, jak každý, kdo čtení nebo práce s ní později. Visual Basic ignoruje komentáře během kompilace a neovlivňují zkompilovaný kód.

Komentář řádky začínat apostrof (`'`) nebo `REM` mezeru. Je možné je přidat kdekoli v kódu, s výjimkou v rámci řetězce. Chcete-li přidat komentář k příkazu, vložte apostrof nebo `REM` po příkazu, za nímž následuje komentář. Komentáře můžete také přejít na vlastní samostatný řádek. Následující příklad ukazuje těchto možností.

[!code-vb[VbVbalrStatements#72](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#72)]

## <a name="checking-compilation-errors"></a>Kontrola chyb kompilace

Pokud po psaní jediného řádku kódu s modrou vlnovkou (zobrazit chybová zpráva může také) se zobrazí na řádku, je chyba syntaxe v příkazu. Musíte zjistit, co je špatně s příkazem (podle hledání v seznamu úkolů nebo najede myší chybu pomocí ukazatele myši a čtení chybová zpráva) a opraví ho. Dokud všechny chyby syntaxe opravily ve vašem kódu, program se nezdaří pro správnou kompilaci.

## <a name="related-sections"></a>Související oddíly

|Termín|Definice|
|---|---|
|[Operátory přiřazení](../../../visual-basic/language-reference/operators/assignment-operators.md)|Obsahuje odkazy na stránky referenční dokumentace jazyka zahrnující operátory přiřazení například `=`, `*=`, a `&=`.|
|[Operátory a výrazy](./operators-and-expressions/index.md)|Ukazuje, jak zkombinovat prvky s operátory pozastavit nové hodnoty.|
|[Postupy: Přerušení a kombinace příkazů v kódu](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)|Ukazuje, jak rozdělit jeden příkaz na více řádků a umístit na stejný řádek více příkazů.|
|[Postupy: Vytváření popisků příkazů](../../../visual-basic/programming-guide/program-structure/how-to-label-statements.md)|Ukazuje, jak označit řádek kódu.|
