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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400888"
---
# <a name="statements-in-visual-basic"></a>Příkazy v jazyce Visual Basic

Příkaz v jazyce Visual Basic je úplná instrukce. Může obsahovat klíčová slova, operátory, proměnné, konstanty a výrazy. Každý příkaz patří do jedné z následujících kategorií:

- **Příkazy deklarace**, které pojmenují proměnnou, konstantu nebo proceduru a mohou také určit datový typ.

- **Spustitelné příkazy**, které iniciují akce. Tyto příkazy můžete volat metodu nebo funkci a mohou smyčky nebo větvení prostřednictvím bloků kódu. Spustitelné příkazy zahrnují **příkazy přiřazení**, které přiřazují hodnotu nebo výraz proměnné nebo konstantě.

Toto téma popisuje jednotlivé kategorie. Toto téma také popisuje, jak kombinovat více příkazů na jednom řádku a jak pokračovat v příkazu přes více řádků.

## <a name="declaration-statements"></a>Prohlášení

Příkazy deklarace slouží k pojmenování a definování procedur, proměnných, vlastností, polí a konstant. Když deklarujete programovací prvek, můžete také definovat jeho datový typ, úroveň přístupu a obor. Další informace naleznete v tématu [Deklarované charakteristiky prvků](./declared-elements/declared-element-characteristics.md).

Následující příklad obsahuje tři deklarace.

[!code-vb[VbVbalrStatements#80](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#80)]

První prohlášení je `Sub` prohlášení. Spolu s `End Sub` jeho odpovídající prohlášení deklaruje proceduru s názvem `applyFormat`. Také určuje, `applyFormat` že `Public`je , což znamená, že jakýkoli kód, který může odkazovat na něj můžete volat.

Druhé prohlášení je `Const` příkaz, který deklaruje konstantu `limit`, určující `Integer` datový typ a hodnotu 33.

Třetí deklarace `Dim` je prohlášení, které `thisWidget`deklaruje proměnnou . Datový typ je specifický objekt, konkrétně objekt `Widget` vytvořený z třídy. Můžete deklarovat proměnnou být jakéhokoli elementárnídatový typ nebo libovolný typ objektu, který je vystaven v aplikaci, kterou používáte.

### <a name="initial-values"></a>Počáteční hodnoty

Při spuštění kódu obsahujícího prohlášení prohlášení Visual Basic rezervuje paměť požadovanou pro deklarovaný prvek. Pokud prvek obsahuje hodnotu, visual basic inicializuje ji na výchozí hodnotu pro jeho datový typ. Další informace naleznete v tématu "Chování" v [dim prohlášení](../../language-reference/statements/dim-statement.md).

Můžete přiřadit počáteční hodnotu proměnné jako součást jeho deklarace, jak ukazuje následující příklad.

[!code-vb[VbVbalrStatements#81](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#81)]

Pokud proměnná je proměnná objektu, můžete explicitně vytvořit instanci jeho třídy při deklarování pomocí [new operator](../../../visual-basic/language-reference/operators/new-operator.md) klíčové slovo, jak ukazuje následující příklad.

[!code-vb[VbVbalrStatements#82](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#82)]

Všimněte si, že počáteční hodnota, kterou zadáte v příkazu deklarace není přiřazena proměnné, dokud provedení nedosáhne jeho prohlášení. Do té doby proměnná obsahuje výchozí hodnotu pro svůj datový typ.

## <a name="executable-statements"></a>Spustitelné příkazy

Spustitelný příkaz provede akci. Může volat proceduru, větev na jiné místo v kódu, smyčka prostřednictvím několika příkazů nebo vyhodnotit výraz. Příkaz přiřazení je zvláštní případ spustitelného příkazu.

Následující příklad používá `If...Then...Else` řídicí strukturu ke spuštění různých bloků kódu na základě hodnoty proměnné. V rámci každého bloku `For...Next` kódu spustí smyčka zadaný počet opakování.

[!code-vb[VbVbalrStatements#83](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#83)]

Příkaz `If` v předchozím příkladu zkontroluje hodnotu parametru `clockwise`. Pokud je `True`hodnota , `spinClockwise` volá `aWidget`metodu . Pokud je `False`hodnota , `spinCounterClockwise` volá `aWidget`metodu . Řídicí `If...Then...Else` struktura končí `End If`.

Smyčka `For...Next` v rámci každého bloku volá příslušnou metodu několikrát `revolutions` rovnající se hodnotě parametru.

## <a name="assignment-statements"></a>Příkazy přiřazení

Příkazy přiřazení provádějí operace přiřazení, které spočívají v převzetí hodnoty`=`na pravé straně operátoru přiřazení ( ) a uložení v prvku vlevo, jako v následujícím příkladu.

[!code-vb[VbVbalrStatements#73](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#73)]

V předchozím příkladu příkaz přiřazení ukládá hodnotu literálu `v`42 v proměnné .

### <a name="eligible-programming-elements"></a>Způsobilé programové prvky

Programovací prvek na levé straně operátoru přiřazení musí být schopen přijmout a uložit hodnotu. To znamená, že musí být proměnná nebo vlastnost, která není [jen pro čtení](../../../visual-basic/language-reference/modifiers/readonly.md), nebo musí být prvek pole. V kontextu příkazu přiřazení se takový prvek někdy nazývá *lvalue*, pro "left value".

Hodnota na pravé straně operátoru přiřazení je generována výrazem, který se může skládat z libovolné kombinace literálů, konstant, proměnných, vlastností, prvků pole, jiných výrazů nebo volání funkcí. Toto dokládá následující příklad.

[!code-vb[VbVbalrStatements#74](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#74)]

Předchozí příklad přidá hodnotu drženou v proměnné `y` `z`k hodnotě držené v proměnné a `findResult`pak přidá hodnotu vrácenou voláním funkce . Celková hodnota tohoto výrazu je `x`pak uložena v proměnné .

### <a name="data-types-in-assignment-statements"></a>Datové typy ve výkazech přiřazení

Kromě číselných hodnot může operátor přiřazení `String` také přiřadit hodnoty, jak ukazuje následující příklad.

[!code-vb[VbVbalrStatements#75](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#75)]

Můžete také `Boolean` přiřadit hodnoty, `Boolean` pomocí literálu nebo výrazu, `Boolean` jak ukazuje následující příklad.

[!code-vb[VbVbalrStatements#76](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#76)]

Podobně můžete přiřadit příslušné hodnoty programovacím `Char` `Date`prvkům `Object` , nebo datového typu. Můžete také přiřadit instanci objektu prvku deklarovanému jako třída, ze které je tato instance vytvořena.

### <a name="compound-assignment-statements"></a>Složené příkazy přiřazení

*Příkazy složeného přiřazení* nejprve provedou operaci výrazu před jeho přiřazením k programovacímu prvku. Následující příklad ilustruje jeden z `+=`těchto operátorů , který zintenzivňuje hodnotu proměnné na levé straně operátoru hodnotou výrazu vpravo.

[!code-vb[VbVbalrStatements#77](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#77)]

Předchozí příklad přidá hodnotu `n`1 a potom uloží tuto `n`novou hodnotu v . Jedná se o zkrácený ekvivalent následujícího tvrzení:

[!code-vb[VbVbalrStatements#78](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#78)]

Různé operace složené přiřazení lze provádět pomocí operátorů tohoto typu. Seznam těchto operátorů a další informace o nich naleznete v tématu [Operátory přiřazení](../../../visual-basic/language-reference/operators/assignment-operators.md).

Operátor přiřazení zřetězení (`&=`) je užitečný pro přidání řetězce na konec již existujících řetězců, jak ukazuje následující příklad.

[!code-vb[VbVbalrStatements#79](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#79)]

### <a name="type-conversions-in-assignment-statements"></a>Zadat převody v příkazech přiřazení

Hodnota, kterou přiřadíte proměnné, vlastnosti nebo prvku pole, musí být datového typu odpovídajícího tomuto cílovému prvku. Obecně byste se měli pokusit vygenerovat hodnotu stejného datového typu jako cílový prvek. Některé typy však mohou být během přiřazení převedeny na jiné typy.

Informace o převodu mezi datovými typy naleznete [v tématu Typ převodů v jazyce Visual Basic](./data-types/type-conversions.md). Stručně řečeno, Visual Basic automaticky převede hodnotu daného typu na jakýkoli jiný typ, na který se rozšiřuje. *Rozšiřující převod* je jeden v tom, že vždy uspěje za běhu a neztratí žádná data. Například Visual Basic `Integer` převede `Double` hodnotu v `Integer` případě `Double`potřeby, protože rozšiřuje na . Další informace naleznete v [tématu Rozšíření a zúžení převody](./data-types/widening-and-narrowing-conversions.md).

*Zužující se převody* (ty, které nejsou rozšíření) nést riziko selhání v době běhu nebo ztráty dat. Zužující převod můžete provést explicitně pomocí funkce převodu typu nebo můžete nasměrovat kompilátor k provedení všech převodů implicitně nastavením `Option Strict Off`. Další informace naleznete [v tématu Implicitní a explicitní převody](./data-types/implicit-and-explicit-conversions.md).

## <a name="putting-multiple-statements-on-one-line"></a>Uvedení více příkazů na jeden řádek

Na jednom řádku můžete mít více příkazů`:`oddělených znakem dvojtečky ( ). Toto dokládá následující příklad.

[!code-vb[VbVbalrStatements#70](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#70)]

Ačkoli občas pohodlné, tato forma syntaxe je váš kód těžko číst a udržovat. Proto se doporučuje zachovat jeden příkaz na řádek.

## <a name="continuing-a-statement-over-multiple-lines"></a>Pokračování příkazu přes více řádků

Příkaz se obvykle vejde na jeden řádek, ale když je příliš dlouhý, můžete jej pokračovat na další řádek pomocí sekvence`_`pokračování řádku, která se skládá z mezery následované znakem podtržítka ( ) následovaným návratem vozíku. V následujícím příkladu `MsgBox` bude spustitelný příkaz pokračovat přes dva řádky.

[!code-vb[VbVbalrStatements#71](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#71)]

### <a name="implicit-line-continuation"></a>Implicitní pokračování řádku

V mnoha případech můžete pokračovat v příkazu na dalším řádku`_`po sobě bez použití znaku podtržítka ( ). Následující prvky syntaxe implicitně pokračovat v příkazu na další řádek kódu.

- Po čárce (`,`). Například:

   [!code-vb[VbVbalrLineContinuation#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#1)]

- Po otevřené závorce`(`( ) nebo před uzavírací závorkou (`)`). Například:

   [!code-vb[VbVbalrLineContinuation#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#2)]

- Po otevřené složené závorce (`{`) nebo`}`před uzavírací složených závorkou ( ). Například:

    [!code-vb[VbVbalrLineContinuation#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#3)]

    Další informace naleznete [v tématu Inicializátory objektů: Pojmenované a anonymní typy](./objects-and-classes/object-initializers-named-and-anonymous-types.md) nebo [Inicializátory kolekce](./collection-initializers/index.md).

- Po otevřeném vloženém`<%=`výrazu ( ) nebo před`%>`uzavřením vloženého výrazu ( ) v literálu XML. Například:

   [!code-vb[VbVbalrLineContinuation#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#4)]

   Další informace naleznete [v tématu Embedded Expressions in XML](./xml/embedded-expressions-in-xml.md).

- Po operátoru zřetězení (`&`). Například:

   [!code-vb[VbVbcnConventions#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/vb/Class1.vb#9)]

   Další informace naleznete [v tématu Operators Listed listed by Functionality](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md).

- Po operátorech`=` `&=`přiřazení `:=` `+=`( `-=` `*=`, `/=` `\=`, `^=` `<<=`, `>>=`, , , , . ). Například:

   [!code-vb[VbVbalrLineContinuation#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#5)]

   Další informace naleznete [v tématu Operators Listed listed by Functionality](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md).

- Po binárních`+` `-`operátorech ( `<>` `<`, `>` `<=`, `>=` `/` `*`, `Mod`, `And` `AndAlso`, `Or` `OrElse`, `Like` `Xor` `^`, , `>>` `<<`, , , , , , ), ) v rámci výrazu. Například:

   [!code-vb[VbVbalrLineContinuation#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#7)]

   Další informace naleznete [v tématu Operators Listed listed by Functionality](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md).

- Po `Is` a `IsNot` operátory. Například:

   [!code-vb[VbVbalrLineContinuation#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#8)]

   Další informace naleznete [v tématu Operators Listed listed by Functionality](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md).

- Za znakem kvalifikátoru člena (`.`) a před názvem člena. Například:

   [!code-vb[VbVbalrLineContinuation#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#5)]

   Musíte však zahrnout znak pokračování`_`řádku ( ) za znakem `With` kvalifikátoru člena, pokud používáte příkaz nebo zadáváte hodnoty v inicializačním seznamu pro typ. Zvažte přerušení řádku za operátorem `=`přiřazení (například) při použití `With` příkazů nebo seznamů inicializace objektu. Například:

   [!code-vb[VbVbalrLineContinuation#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#14)]

   Další informace naleznete v tématu [S... End with Statement](../../../visual-basic/language-reference/statements/with-end-with-statement.md) nebo [Object Initializers: Pojmenované a anonymní typy](./objects-and-classes/object-initializers-named-and-anonymous-types.md).

- Za kvalifikátorem `.@` `...`vlastností osy XML (`.` nebo nebo ). Při zadávání kvalifikátoru`_`člena při použití klíčového `With` slova však musíte uvést znak pokračování řádku ( ). Například:

   [!code-vb[VbVbalrLineContinuation#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#9)]

   Další informace naleznete v tématu [Vlastnosti osy XML](../../../visual-basic/language-reference/xml-axis/index.md).

- Po znaménko menší než (<) nebo`>`před znaménkem větší než ( ) při zadání atributu. Také po větší-než`>`znaménko ( ) při zadání atributu. Při zadávání atributů na úrovni`_`sestavení nebo modulu však musíte zahrnout znak pokračování řádku ( ). Například:

   [!code-vb[VbVbalrLineContinuation#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#10)]

   Další informace naleznete v [tématu Přehled atributů](../../../visual-basic/programming-guide/concepts/attributes/index.md).

- Před a po`Aggregate`operátory dotazu `Let`( `Order By` `Select`, `Skip` `Skip While` `Take` `Distinct`, `From` `Group By` `Take While`, `Where` `In` `Into` `On` `Ascending` `Group Join` `Join`, , , `Descending`, , , , , , , , , , a ). Mezi klíčovými slovy operátorů dotazů, které se skládají`Order By`z `Group Join` `Take While`více `Skip While`klíčových slov ( , , , a ). Například:

   [!code-vb[VbVbalrLineContinuation#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#11)]

   Další informace naleznete v [tématu Dotazy](../../../visual-basic/language-reference/queries/index.md).

- Po `In` klíčové slovo `For Each` v prohlášení. Například:

   [!code-vb[VbVbalrLineContinuation#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#12)]

   Další informace naleznete v tématu [Pro každý... Další prohlášení](../../../visual-basic/language-reference/statements/for-each-next-statement.md).

- Po `From` klíčové slovo v inicializátoru kolekce. Například:

   [!code-vb[VbVbalrLineContinuation#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#13)]

   Další informace naleznete v [tématu Inicializátory kolekce](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md).

## <a name="adding-comments"></a>Přidávání komentářů

Zdrojový kód není vždy samovysvětlující, a to i pro programátora, který jej napsal. Chcete-li pomoci dokumentovat jejich kód, proto většina programátorů, aby liberální využití vložené komentáře. Komentáře v kódu mohou vysvětlit postup nebo konkrétní instrukce každému, kdo s ním později čte nebo s ním pracuje. Visual Basic ignoruje komentáře během kompilace a nemají vliv na zkompilovaný kód.

Řádky komentáře začínají apostrofem`'` `REM` ( ) nebo mezerou. Mohou být přidány kdekoli v kódu, s výjimkou v rámci řetězce. Chcete-li k příkazu připojit komentář, vložte `REM` apostrof nebo za příkaz následovaný komentářem. Komentáře mohou také jít na vlastní samostatný řádek. Následující příklad ukazuje tyto možnosti.

[!code-vb[VbVbalrStatements#72](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#72)]

## <a name="checking-compilation-errors"></a>Kontrola chyb kompilace

Pokud se po zadání řádku kódu řádek zobrazí s podtržením modrou vlnovkou (může se zobrazit také chybová zpráva), je v příkazu chyba syntaxe. Musíte zjistit, co je s příkazem špatně (vyhledáním v seznamu úkolů nebo umístěním myší na chybu s ukazatelem myši a přečtením chybové zprávy) a opravit ji. Dokud neopravíte všechny chyby syntaxe v kódu, nebude se správně zkompilovat program.

## <a name="related-sections"></a>Související oddíly

|Označení|Definice|
|---|---|
|[Operátory přiřazení](../../../visual-basic/language-reference/operators/assignment-operators.md)|Obsahuje odkazy na referenční stránky jazyků `=` `*=`pokrývající `&=`operátory přiřazení, například , a .|
|[Operátory a výrazy](./operators-and-expressions/index.md)|Ukazuje, jak kombinovat prvky s operátory, aby získaly nové hodnoty.|
|[Postupy: Přerušení a kombinace příkazů v kódu](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)|Ukazuje, jak rozdělit jeden příkaz do více řádků a jak umístit více příkazů na stejném řádku.|
|[Postupy: Vytváření popisků příkazů](../../../visual-basic/programming-guide/program-structure/how-to-label-statements.md)|Ukazuje, jak označit řádek kódu.|
