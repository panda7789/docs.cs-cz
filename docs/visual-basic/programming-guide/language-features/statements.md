---
title: Příkazy
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
ms.openlocfilehash: f63f0f0212913f95baab2a8a43c4b7f25a859cd9
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352503"
---
# <a name="statements-in-visual-basic"></a>Příkazy v jazyce Visual Basic

Příkaz v Visual Basic je ucelenou instrukcí. Může obsahovat klíčová slova, operátory, proměnné, konstanty a výrazy. Každý příkaz patří do jedné z následujících kategorií:

- **Příkazy deklarace**, které pojmenují proměnnou, konstantu nebo proceduru a mohou také určovat datový typ.

- **Spustitelné příkazy**, které iniciují akce. Tyto příkazy mohou volat metodu nebo funkci a mohou cykly nebo větvení prostřednictvím bloků kódu. Spustitelné příkazy zahrnují **příkazy přiřazení**, které přiřazují hodnotu nebo výraz proměnné nebo konstantě.

V tomto tématu jsou popsány jednotlivé kategorie. Toto téma také popisuje, jak zkombinovat více příkazů na jednom řádku a jak pokračovat v příkazu nad více řádky.

## <a name="declaration-statements"></a>Příkazy deklarace

Příkazy deklarace můžete použít k pojmenování a definování procedur, proměnných, vlastností, polí a konstant. Při deklaraci programovacího prvku můžete také definovat jeho datový typ, úroveň přístupu a rozsah. Další informace naleznete v tématu [deklarované charakteristiky elementu](./declared-elements/declared-element-characteristics.md).

Následující příklad obsahuje tři deklarace.

[!code-vb[VbVbalrStatements#80](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#80)]

První deklarace je příkaz `Sub`. Spolu s odpovídajícím příkazem `End Sub` deklaruje procedura s názvem `applyFormat`. Určuje také, že `applyFormat` je `Public`, což znamená, že může zavolat libovolný kód, který na něj může odkazovat.

Druhá deklarace je příkaz `Const`, který deklaruje konstantu `limit`a určuje `Integer` datový typ a hodnotu 33.

Třetí deklarace je příkaz `Dim`, který deklaruje proměnnou `thisWidget`. Datový typ je konkrétní objekt, konkrétně objekt vytvořený z třídy `Widget`. Můžete deklarovat proměnnou, která bude mít jakýkoli základní datový typ nebo jakýkoli typ objektu, který je zveřejněn v aplikaci, kterou používáte.

### <a name="initial-values"></a>Počáteční hodnoty

Při spuštění kódu obsahujícího příkaz deklarace Visual Basic vyhrazuje paměť potřebnou pro deklarovaný element. Pokud element obsahuje hodnotu, Visual Basic ji inicializuje na výchozí hodnotu pro svůj datový typ. Další informace naleznete v tématu "Behavior" v [příkazu Dim](../../language-reference/statements/dim-statement.md).

Můžete přiřadit počáteční hodnotu proměnné jako součást její deklarace, jak ukazuje následující příklad.

[!code-vb[VbVbalrStatements#81](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#81)]

Pokud je proměnná objektovou proměnnou, můžete explicitně vytvořit instanci své třídy při jejím deklaraci pomocí klíčového slova [New operátor](../../../visual-basic/language-reference/operators/new-operator.md) , jak ukazuje následující příklad.

[!code-vb[VbVbalrStatements#82](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#82)]

Všimněte si, že počáteční hodnota, kterou zadáte v příkazu deklarace, není přiřazena proměnné, dokud spuštění nedosáhne příkazu deklarace. Do této doby proměnná obsahuje výchozí hodnotu pro svůj datový typ.

## <a name="executable-statements"></a>Spustitelné příkazy

Spustitelný příkaz provede akci. Může zavolat proceduru, větvení na jiné místo v kódu, projít několik příkazů nebo vyhodnotit výraz. Příkaz přiřazení je zvláštní případ spustitelného příkazu.

Následující příklad používá strukturu ovládacího prvku `If...Then...Else` ke spouštění různých bloků kódu na základě hodnoty proměnné. V rámci každého bloku kódu spouští cyklus `For...Next` zadaný počet opakování.

[!code-vb[VbVbalrStatements#83](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#83)]

Příkaz `If` v předchozím příkladu kontroluje hodnotu parametru `clockwise`. Pokud je hodnota `True`, zavolá metodu `spinClockwise` `aWidget`. Pokud je hodnota `False`, zavolá metodu `spinCounterClockwise` `aWidget`. Struktura ovládacího prvku `If...Then...Else` končí `End If`.

Smyčka `For...Next` v rámci každého bloku volá odpovídající metodu tolikrát, kolikrát se rovná hodnotě parametru `revolutions`.

## <a name="assignment-statements"></a>Příkazy přiřazení

Příkazy přiřazení provádějí operace přiřazení, které se skládají z převzetí hodnoty na pravé straně operátoru přiřazení (`=`) a jejich uložení do elementu vlevo, jako v následujícím příkladu.

[!code-vb[VbVbalrStatements#73](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#73)]

V předchozím příkladu příkaz přiřazení ukládá hodnotu literálu 42 v proměnné `v`.

### <a name="eligible-programming-elements"></a>Oprávněné programovací prvky

Programovací element na levé straně operátoru přiřazení musí být schopný přijmout a uložit hodnotu. To znamená, že musí být proměnná nebo vlastnost, která není [jen pro čtení](../../../visual-basic/language-reference/modifiers/readonly.md), nebo musí být prvkem pole. V kontextu příkazu přiřazení se takový prvek někdy označuje jako *l*-hodnota, například "hodnota" Left.

Hodnota na pravé straně operátoru přiřazení je vygenerována výrazem, který se může skládat z jakékoli kombinace literálů, konstant, proměnných, vlastností, prvků pole, jiných výrazů nebo volání funkcí. Toto dokládá následující příklad.

[!code-vb[VbVbalrStatements#74](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#74)]

Předchozí příklad přidá hodnotu drženou v proměnné `y` k hodnotě uchovávané v proměnné `z`a poté přidá hodnotu vrácenou voláním funkce `findResult`. Celková hodnota tohoto výrazu je pak uložena v proměnné `x`.

### <a name="data-types-in-assignment-statements"></a>Datové typy v příkazech přiřazení

Kromě číselných hodnot operátor přiřazení také může přiřadit `String` hodnoty, jak ukazuje následující příklad.

[!code-vb[VbVbalrStatements#75](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#75)]

Můžete také přiřadit `Boolean` hodnoty pomocí literálu `Boolean` nebo výrazu `Boolean`, jak ukazuje následující příklad.

[!code-vb[VbVbalrStatements#76](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#76)]

Podobně můžete přiřadit příslušné hodnoty pro programové prvky `Char`, `Date`nebo `Object` datový typ. Instanci objektu lze také přiřadit elementu, který je deklarován jako třída, ze které je vytvořena instance.

### <a name="compound-assignment-statements"></a>Složené příkazy přiřazení

*Složené příkazy přiřazení* nejprve provede operaci na výrazu před přiřazením k programovacímu prvku. Následující příklad ilustruje jeden z těchto operátorů `+=`, který zvyšuje hodnotu proměnné na levé straně operátoru hodnotou výrazu na pravé straně.

[!code-vb[VbVbalrStatements#77](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#77)]

Předchozí příklad přidá 1 k hodnotě `n`a poté uloží tuto novou hodnotu do `n`. Jedná se o zkrácený ekvivalent následujícího příkazu:

[!code-vb[VbVbalrStatements#78](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#78)]

Pomocí operátorů tohoto typu lze provádět různé operace složeného přiřazení. Seznam těchto operátorů a další informace o těchto operátorech naleznete v tématu [operátory přiřazení](../../../visual-basic/language-reference/operators/assignment-operators.md).

Operátor přiřazení zřetězení (`&=`) je vhodný pro přidání řetězce na konec již existujících řetězců, jak ukazuje následující příklad.

[!code-vb[VbVbalrStatements#79](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#79)]

### <a name="type-conversions-in-assignment-statements"></a>Převody typů v příkazech přiřazení

Hodnota, kterou přiřadíte proměnné, vlastnosti nebo prvku pole musí být datového typu, který je vhodný pro daný cílový element. Obecně byste se měli pokusit vygenerovat hodnotu stejného datového typu jako cílový element. Některé typy však lze v průběhu přiřazení převést na jiné typy.

Informace o převodu mezi datovými typy naleznete [v tématu převody typu v Visual Basic](./data-types/type-conversions.md). V krátkém Visual Basic automaticky převede hodnotu daného typu na jiný typ, na který se rozšíří. *Rozšiřující převod* je jeden v, který se vždy zdaří za běhu a neztratí žádná data. Visual Basic například převede hodnotu `Integer` na `Double`, pokud je to vhodné, protože se `Integer` rozšiřuje na `Double`. Další informace najdete v tématu [rozšiřování a zúžení převodů](./data-types/widening-and-narrowing-conversions.md).

*Zúžení převodů* (těch, které nejsou rozšiřující) mají riziko selhání za běhu nebo ztrátu dat. Můžete provést zužující převod explicitně pomocí funkce pro převod typu nebo můžete kompilátor přímo nasměrovat tak, aby se všechny převody prováděly nastavením `Option Strict Off`. Další informace naleznete v tématu [implicitní a explicitní převody](./data-types/implicit-and-explicit-conversions.md).

## <a name="putting-multiple-statements-on-one-line"></a>Vložení více příkazů na jeden řádek

Na jednom řádku, který je oddělen znakem dvojtečky (`:`), můžete mít více příkazů. Toto dokládá následující příklad.

[!code-vb[VbVbalrStatements#70](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#70)]

V některých případech je to možné, že tato forma syntaxe má těžko čitelný a udržovatelný kód. Proto se doporučuje uchovávat jeden příkaz na řádek.

## <a name="continuing-a-statement-over-multiple-lines"></a>Pokračování příkazu nad více řádky

Příkaz se obvykle vejde na jeden řádek, ale pokud je příliš dlouhý, můžete pokračovat na další řádek pomocí sekvence pokračování řádku, která se skládá z mezery následovaného znakem podtržítka (`_`) následovaným návratem na začátek řádku. V následujícím příkladu `MsgBox` spustitelný příkaz pokračuje více než dvěma řádky.

[!code-vb[VbVbalrStatements#71](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#71)]

### <a name="implicit-line-continuation"></a>Implicitní pokračování řádku

V mnoha případech můžete pokračovat v příkazu na dalším po sobě jdoucích řádcích bez použití znaku podtržítka (`_`). Následující elementy syntaxe implicitně pokračují v příkazu na dalším řádku kódu.

- Za čárkou (`,`). Příklad:

   [!code-vb[VbVbalrLineContinuation#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#1)]

- Po otevírací závorce (`(`) nebo před pravou závorkou (`)`). Příklad:

   [!code-vb[VbVbalrLineContinuation#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#2)]

- Za levou složenou závorku (`{`) nebo před pravou složenou závorkou (`}`). Příklad:

    [!code-vb[VbVbalrLineContinuation#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#3)]

    Další informace naleznete v tématu [Inicializátory objektů: pojmenované a anonymní typy](./objects-and-classes/object-initializers-named-and-anonymous-types.md) nebo [inicializátory kolekce](./collection-initializers/index.md).

- Po otevřeném vloženém výrazu (`<%=`) nebo před ukončením vloženého výrazu (`%>`) v rámci literálu XML. Příklad:

   [!code-vb[VbVbalrLineContinuation#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#4)]

   Další informace najdete v tématu [vložené výrazy v XML](./xml/embedded-expressions-in-xml.md).

- Po operátoru zřetězení (`&`). Příklad:

   [!code-vb[VbVbcnConventions#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/vb/Class1.vb#9)]

   Další informace najdete v tématu [operátory uvedené podle funkcí](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md).

- Po přiřazení operátory (`=`, `&=`, `:=`, `+=`, `-=`, `*=`, `/=`, `\=`, `^=`, `<<=`, `>>=`). Příklad:

   [!code-vb[VbVbalrLineContinuation#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#5)]

   Další informace najdete v tématu [operátory uvedené podle funkcí](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md).

- Po binárních operátorech (`+`, `-`, `/`, `*`, `Mod`, `<>`, `<`, `>`, `<=`, `>=`, `^`, `>>`, `<<`) v rámci výrazu.`And``AndAlso``Or``OrElse``Like``Xor` Příklad:

   [!code-vb[VbVbalrLineContinuation#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#7)]

   Další informace najdete v tématu [operátory uvedené podle funkcí](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md).

- Za operátory `Is` a `IsNot`. Příklad:

   [!code-vb[VbVbalrLineContinuation#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#8)]

   Další informace najdete v tématu [operátory uvedené podle funkcí](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md).

- Po znaku kvalifikátoru členu (`.`) a před názvem členu. Příklad:

   [!code-vb[VbVbalrLineContinuation#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#5)]

   Při použití příkazu `With` nebo zadání hodnot do inicializačního seznamu pro daný typ je však nutné zahrnout znak pro pokračování řádku (`_`) za znak kvalifikátoru členu. Zvažte rozdělení řádku za operátor přiřazení (například `=`) při použití příkazů `With` nebo seznamů inicializace objektů. Příklad:

   [!code-vb[VbVbalrLineContinuation#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#14)]

   Další informace najdete v tématu [s... Ukončete příkazy](../../../visual-basic/language-reference/statements/with-end-with-statement.md) nebo [Inicializátory objektů: pojmenované a anonymní typy](./objects-and-classes/object-initializers-named-and-anonymous-types.md).

- Po kvalifikátoru Vlastnosti osy XML (`.` nebo `.@` nebo `...`). Při použití klíčového slova `With` však musíte zahrnout znak pro pokračování řádku (`_`) při zadání kvalifikátoru člena. Příklad:

   [!code-vb[VbVbalrLineContinuation#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#9)]

   Další informace najdete v tématu [Vlastnosti osy XML](../../../visual-basic/language-reference/xml-axis/index.md).

- Za znaménkem menší než (<) nebo před symbolem větším než (`>`) při určení atributu. I po označení větší než (`>`) při určení atributu. Při zadání atributů na úrovni sestavení nebo modulu je však nutné zahrnout znak pro pokračování řádku (`_`). Příklad:

   [!code-vb[VbVbalrLineContinuation#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#10)]

   Další informace najdete v tématu [Přehled atributů](../../../visual-basic/programming-guide/concepts/attributes/index.md).

- Před a po operátorech dotazů (`Aggregate`, `Distinct`, `From`, `Group By`, `Group Join`, `Join`, `Let`, `Order By`, `Select`, `Skip`, `Skip While`, `Take`, `Take While`, `Where`, `In`, `Into`, `On`, `Ascending`a `Descending`). Mezi klíčovými slovy operátorů dotazu, které se skládají z více klíčových slov (`Order By`, `Group Join`, `Take While`a `Skip While`), nelze rozdělit čáru. Příklad:

   [!code-vb[VbVbalrLineContinuation#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#11)]

   Další informace najdete v tématu [dotazy](../../../visual-basic/language-reference/queries/index.md).

- Za klíčovým slovem `In` v příkazu `For Each`. Příklad:

   [!code-vb[VbVbalrLineContinuation#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#12)]

   Další informace najdete v tématu [for each... Další příkaz](../../../visual-basic/language-reference/statements/for-each-next-statement.md).

- Za klíčovým slovem `From` v inicializátoru kolekce. Příklad:

   [!code-vb[VbVbalrLineContinuation#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#13)]

   Další informace najdete v tématu [inicializátory kolekce](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md).

## <a name="adding-comments"></a>Přidávání komentářů

Zdrojový kód není vždy samozřejmý ani programátorovi, který ho vytvořil. Aby bylo možné dokumentovat v kódu, proto většina programátorů využívá vložené komentáře. Komentáře v kódu mohou vysvětlit postup nebo konkrétní instrukci pro někoho, kdo nebo s ním pracují později. Visual Basic ignoruje komentáře během kompilace a nemá vliv na zkompilovaný kód.

Řádky komentářů začínají apostrofem (`'`) nebo `REM` následovaným mezerou. Lze je přidat kdekoli v kódu, s výjimkou v rámci řetězce. Chcete-li do příkazu připojit komentář, vložte apostrof nebo `REM` za příkazem následovaným komentářem. Komentáře mohou také jít na vlastní samostatný řádek. Následující příklad znázorňuje tyto možnosti.

[!code-vb[VbVbalrStatements#72](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#72)]

## <a name="checking-compilation-errors"></a>Kontrola chyb kompilace

Pokud po zadání řádku kódu se řádek zobrazí s modrou vlnovkou (může se zobrazit i chybová zpráva), v příkazu se zobrazí chyba syntaxe. Je třeba zjistit, co je v příkazu chybné, a to tak, že v seznamu úkolů vyhledáte ukazatel myši nebo najedete myší na chybu a napíšete chybovou zprávu) a opravíte ji. Dokud neopravíte všechny chyby syntaxe v kódu, program se nepodaří zkompilovat správně.

## <a name="related-sections"></a>Související oddíly

|Termín|Definice|
|---|---|
|[Operátory přiřazení](../../../visual-basic/language-reference/operators/assignment-operators.md)|Obsahuje odkazy na jazykové referenční stránky, které kryjí operátory přiřazení, jako `=`, `*=`a `&=`.|
|[Operátory a výrazy](./operators-and-expressions/index.md)|Ukazuje, jak kombinovat prvky s operátory, aby se zadávaly nové hodnoty.|
|[Postupy: Přerušení a kombinace příkazů v kódu](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)|Ukazuje, jak rozdělit jeden příkaz na více řádků a jak umístit více příkazů na stejný řádek.|
|[Postupy: Vytváření popisků příkazů](../../../visual-basic/programming-guide/program-structure/how-to-label-statements.md)|Ukazuje, jak označit řádek kódu.|
