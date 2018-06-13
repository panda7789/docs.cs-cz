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
ms.openlocfilehash: 9953fb949c58c074169596dcf48b6df5e7b8f0af
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33655718"
---
# <a name="statements-in-visual-basic"></a>Příkazy v jazyce Visual Basic
Příkaz v jazyce Visual Basic je kompletní instrukcí. Může obsahovat klíčová slova, operátory, proměnné, konstanty a výrazy. Každý příkaz patří do jedné z následujících kategorií:  
  
-   **Deklarační příkazy**, který názvu proměnné, konstanta nebo postup a můžete také zadat datový typ.  
  
-   **Spustitelné příkazy**, který zahájení akce. Tyto příkazy můžete volat metody nebo funkce, a můžou cykly nebo větev prostřednictvím bloky kódu. Spustitelné příkazy zahrnují **příkazy přiřazení**, která hodnota nebo výraz, proměnné nebo přiřadit konstanta.  
  
 Toto téma popisuje každou kategorii. Toto téma popisuje taky, jak kombinovat více příkazů na jeden řádek a jak pokračovat příkaz na více řádků.  
  
## <a name="declaration-statements"></a>Příkazy deklarace  
 Deklarační příkazy slouží k pojmenování a definovat postupy, proměnné, vlastnosti, pole a konstanty. Po deklarování programovací element můžete také definovat jeho datový typ, úroveň přístupu a oboru. Další informace najdete v tématu [deklarované charakteristiky elementu](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md).  
  
 Následující příklad obsahuje tři deklarace.  
  
 [!code-vb[VbVbalrStatements#80](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/statements_1.vb)]  
  
 Je první deklaraci `Sub` příkaz. Společně s jeho odpovídající `End Sub` příkaz deklaruje proceduru s názvem `applyFormat`. Také určuje, že `applyFormat` je `Public`, což znamená, že kód, který může být můžete volat.  
  
 Je druhý deklaraci `Const` příkaz, který deklaruje konstanta `limit`, zadání `Integer` datový typ a hodnotu 33.  
  
 Je třetí deklaraci `Dim` příkaz, který deklaruje proměnnou `thisWidget`. Datový typ je určitý objekt, a to vytvořen objekt z `Widget` třídy. Je možné deklarovat proměnnou, do které se všechny základní datový typ nebo libovolného typu objektu, který je zveřejněný v aplikaci, kterou používáte.  
  
### <a name="initial-values"></a>Počáteční hodnoty  
 Při spuštění kódu, který obsahuje příkaz deklarace jazyka Visual Basic rezervuje paměť požadovanou ke deklarovaný element. Pokud element obsahuje hodnotu, Visual Basic inicializaci na výchozí hodnotu pro jeho datového typu. Další informace najdete v tématu "Chování" v [Dim – příkaz](../../../visual-basic/language-reference/statements/dim-statement.md).  
  
 Jak ukazuje následující příklad můžete přiřadit počáteční hodnotu proměnné jako součást jeho deklaraci.  
  
 [!code-vb[VbVbalrStatements#81](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/statements_2.vb)]  
  
 Pokud je proměnná proměnné objektu, můžete explicitně vytvořit instanci její třídy po deklarování pomocí [operátor New](../../../visual-basic/language-reference/operators/new-operator.md) – klíčové slovo, jako následující příklad znázorňuje.  
  
 [!code-vb[VbVbalrStatements#82](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/statements_3.vb)]  
  
 Všimněte si, že počáteční hodnotu, kterou zadáte v příkazu deklarace není přiřazený k proměnné, dokud nedosáhne své prohlášení deklarace provádění. Do té doby proměnná obsahuje výchozí hodnotu pro jeho datového typu.  
  
## <a name="executable-statements"></a>Spustitelné příkazy  
 Spustitelný soubor příkaz provede akci. Dokáže volání procedury, větve na jiné místo v kódu, cyklus prostřednictvím několika příkazy, nebo vyhodnocení výrazu. Příkazu přiřazení je zvláštní případ spustitelného souboru příkazu.  
  
 Následující příklad používá `If...Then...Else` řízení struktura spouštět různé bloky kódu na základě hodnoty proměnné. V rámci každého bloku kódu `For...Next` cyklu zadaného počtu opakování.  
  
 [!code-vb[VbVbalrStatements#83](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/statements_4.vb)]  
  
 `If` Příkaz v předchozím příkladu kontroluje hodnotu parametru `clockwise`. Pokud je hodnota `True`, zavolá `spinClockwise` metodu `aWidget`. Pokud je hodnota `False`, zavolá `spinCounterClockwise` metodu `aWidget`. `If...Then...Else` Řídicí struktury končí `End If`.  
  
 `For...Next` Smyčky v každém bloku volá odpovídající metodu několikrát rovná hodnotě `revolutions` parametr.  
  
## <a name="assignment-statements"></a>Příkazy přiřazení  
 Příkazy přiřazení provádět operace úloh, které se skládají z trvá hodnota na pravé straně operátoru přiřazení (`=`) a jeho uložení v elementu na levé straně, jako v následujícím příkladu.  
  
 [!code-vb[VbVbalrStatements#73](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/statements_5.vb)]  
  
 V předchozím příkladu příkaz přiřazení ukládá literálovou hodnotou 42 v proměnné `v`.  
  
### <a name="eligible-programming-elements"></a>Oprávněné programovací elementy  
 Programovací element na levé straně operátoru přiřazení musí být schopen přijmout a uložit hodnotu. To znamená, že musí být proměnná nebo vlastnost, která není [jen pro čtení](../../../visual-basic/language-reference/modifiers/readonly.md), nebo musí být k elementu pole. V kontextu příkazu přiřazení, se někdy nazývá takový prvek *lvalue*, pro "levém hodnota."  
  
 Hodnota na pravé straně operátoru přiřazení je generována pomocí výrazu, který může obsahovat libovolnou kombinaci literály, konstanty, proměnné, vlastnosti, elementy pole, jiné výrazy nebo volání funkce. Toto dokládá následující příklad.  
  
 [!code-vb[VbVbalrStatements#74](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/statements_6.vb)]  
  
 V předchozím příkladu přidá hodnotu uchovávat v proměnné `y` na hodnotu uchovávat v proměnné `z`a potom přidá hodnotu vrácenou z volání funkce `findResult`. Celková hodnota výrazu je pak uloženy v proměnné `x`.  
  
### <a name="data-types-in-assignment-statements"></a>Datové typy v příkazy přiřazení  
 Kromě číselných hodnot, můžete přiřadit také operátor přiřazení `String` hodnoty, jak ukazuje následující příklad.  
  
 [!code-vb[VbVbalrStatements#75](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/statements_7.vb)]  
  
 Je také možné přiřadit `Boolean` hodnoty, buď pomocí `Boolean` literál nebo `Boolean` výraz jako následující příklad ukazuje.  
  
 [!code-vb[VbVbalrStatements#76](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/statements_8.vb)]  
  
 Podobně můžete přiřadit odpovídající hodnoty programovací elementy `Char`, `Date`, nebo `Object` datového typu. Můžete také přiřadit instanci objektu pro element deklarované jako třída, ze kterého je vytvořen tuto instanci.  
  
### <a name="compound-assignment-statements"></a>Složené příkazy přiřazení  
 *Složené přiřazení příkazy* nejprve provést operaci s výrazu před jeho přiřazení k programovací element. Následující příklad ilustruje jeden z těchto operátorů `+=`, což zvýší hodnotu proměnné na levé straně operátoru hodnotou výraz na pravé straně.  
  
 [!code-vb[VbVbalrStatements#77](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/statements_9.vb)]  
  
 V předchozím příkladu přidá 1 na hodnotu `n`a pak uloží novou hodnotu do `n`. Je sdružená vlastnost ekvivalentní následující příkaz:  
  
 [!code-vb[VbVbalrStatements#78](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/statements_10.vb)]  
  
 Řadu složeného přiřazení operací lze provést pomocí operátorů tohoto typu. Seznam těchto operátorů a další informace o nich najdete v tématu [operátory přiřazení](../../../visual-basic/language-reference/operators/assignment-operators.md).  
  
 Operátor přiřazení zřetězení (`&=`) je vhodný pro přidávání řetězec na konec již existující řetězce, jak ukazuje následující příklad.  
  
 [!code-vb[VbVbalrStatements#79](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/statements_11.vb)]  
  
### <a name="type-conversions-in-assignment-statements"></a>Převody typů v příkazy přiřazení  
 Hodnota, kterou přiřadíte k proměnné, vlastnost nebo pole element musí být vhodné pro daný element cílového datového typu. Obecně platí pokuste se generuje hodnotu stejného typu dat, který cílový element. Některé typy lze převést na jiné typy, ale při přiřazení.  
  
 Informace o převodu mezi typy dat najdete v tématu [převody typů v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md). Stručně řečeno Visual Basic automaticky převede hodnotu daného typu na jiný typ, do které rozšiřuje. A *rozšiřující převod* je jeden v tom, že vždy úspěšné v době běhu a není ztratíte všechna data. Například jazyka Visual Basic převede `Integer` hodnotu `Double` Pokud je to vhodné, protože `Integer` rozšiřuje na `Double`. Další informace najdete v tématu [Widening a zužující převody](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).  
  
 *Zužující převody* (ty, které nejsou rozšiřující) představuje riziko selhání v době běhu nebo ztráty dat provádění. Zužující převod můžou provádět explicitně pomocí funkci pro převod typu nebo můžete nastavit kompilátoru provést všechny konverze implicitně nastavením `Option Strict Off`. Další informace najdete v tématu [implicitní a explicitní převody](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md).  
  
## <a name="putting-multiple-statements-on-one-line"></a>Vložení více příkazů na jednom řádku  
 Máte více příkazů na jediném řádku oddělené dvojtečkou (`:`) znaků. Toto dokládá následující příklad.  
  
 [!code-vb[VbVbalrStatements#70](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/statements_12.vb)]  
  
 Když příležitostně pohodlný Tato forma syntaxe bude váš kód obtížné číst a spravovat. Proto se doporučuje, abyste jeden výraz na řádku.  
  
## <a name="continuing-a-statement-over-multiple-lines"></a>Pokračováním příkaz na více řádků  
 Příkaz obvykle vejde na jeden řádek, ale pokud je příliš dlouhý, bude možné pokračovat na další řádek pomocí posloupnost pokračování řádku, který se skládá z mezeru následovanou znakem podtržítka (`_`) a potom na novém řádku. V následujícím příkladu `MsgBox` spustitelného souboru příkazu pokračuje ve dvou řádcích.  
  
 [!code-vb[VbVbalrStatements#71](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/statements_13.vb)]  
  
### <a name="implicit-line-continuation"></a>Implicitní pokračování řádku  
 V mnoha případech můžete dál příkaz na další řádek po sobě jdoucích bez použití znak podtržítka (_). Následující tabulka uvádí prvky syntaxe, které implicitně příkaz pokračovat na další řádek kódu.  
  
|Element syntaxe|Příklad|  
|---|---|  
|Za čárkou (`,`).|[!code-vb[VbVbalrLineContinuation#1](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/statements_14.vb)]|  
|Po otevřené závorky (`(`) nebo před uzavírací kulatá závorka (`)`).|[!code-vb[VbVbalrLineContinuation#2](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/statements_15.vb)]|  
|Po otevřete složené závorky (`{`) nebo před uzavírací složené závorky (`}`).|[!code-vb[VbVbalrLineContinuation#3](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/statements_16.vb)]<br /><br /> Další informace najdete v tématu [inicializátory objektů: pojmenované a anonymní typy](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md) nebo [Inicializátory kolekcí](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md).|  
|Po otevřenou vložených výraz (`<%=`) nebo před ukončení embedded výrazu (`%>`) v rámci literál XML.|[!code-vb[VbVbalrLineContinuation#4](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/statements_17.vb)]<br /><br /> Další informace najdete v tématu [vložené výrazy v XML](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md).|  
|Po výskytu operátoru zřetězení (`&`).|[!code-vb[VbVbcnConventions#9](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/statements_18.vb)]<br /><br /> Další informace najdete v tématu [operátory uvedené podle funkce](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md).|  
|Po operátory přiřazení (`=`, `&=`, `:=`, `+=`, `-=`, `*=`, `/=`, `\=`, `^=`, `<<=`, `>>=`).|[!code-vb[VbVbalrLineContinuation#5](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/statements_19.vb)]<br /><br /> Další informace najdete v tématu [operátory uvedené podle funkce](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md).|  
|Po binární operátory (`+`, `-`, `/`, `*`, `Mod`, `<>`, `<`, `>`, `<=`, `>=`, `^`, `>>`, `<<`, `And`, `AndAlso`, `Or`, `OrElse`, `Like`, `Xor`) v rámci výrazu.|[!code-vb[VbVbalrLineContinuation#7](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/statements_20.vb)]<br /><br /> Další informace najdete v tématu [operátory uvedené podle funkce](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md).|  
|Po `Is` a `IsNot` operátory.|[!code-vb[VbVbalrLineContinuation#8](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/statements_21.vb)]<br /><br /> Další informace najdete v tématu [operátory uvedené podle funkce](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md).|  
|Po znak kvalifikátor člen (`.`) a před název člena. Však musí obsahovat následující znak kvalifikátor člen, pokud používáte znak pokračování řádku (_) `With` příkaz nebo zadávání hodnot v seznamu inicializace pro typ. Vezměte v úvahu nejnovější řádek po operátor přiřazení (například `=`) při použití `With` příkazy nebo seznamy inicializace objektu.|[!code-vb[VbVbalrLineContinuation#5](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/statements_19.vb)]<br />[!code-vb[VbVbalrLineContinuation#14](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/statements_22.vb)]<br /><br /> Další informace najdete v tématu [s... End With – příkaz](../../../visual-basic/language-reference/statements/with-end-with-statement.md) nebo [inicializátory objektů: pojmenované a anonymní typy](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md).|  
|Po kvalifikátor vlastnosti osy XML (`.` nebo `.@` nebo `...`). Však musí obsahovat znak pokračování řádku (_), když zadáte kvalifikátor člen při použití `With` – klíčové slovo.|[!code-vb[VbVbalrLineContinuation#9](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/statements_23.vb)]<br /><br /> Další informace najdete v tématu [vlastnosti osy XML](../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md).|  
|Po méně – znaménko (<) nebo před více – znaménko (`>`) Pokud zadáte atribut. Také po více – znaménko (`>`) Pokud zadáte atribut. Při zadávání atributů sestavení úrovni nebo modul, ale musí obsahovat znak pokračování řádku (_).|[!code-vb[VbVbalrLineContinuation#10](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/statements_24.vb)]<br /><br /> Další informace najdete v tématu [atributy přehled](../../../visual-basic/programming-guide/concepts/attributes/index.md).|  
|Před a po operátory dotazu (`Aggregate`, `Distinct`, `From`, `Group By`, `Group Join`, `Join`, `Let`, `Order By`, `Select`, `Skip`, `Skip While`, `Take`, `Take While`, `Where`, `In`, `Into`, `On`, `Ascending`, a `Descending`). Nelze ukončit řádek mezi klíčová slova operátorů dotazu, které se skládají z více klíčových slov (`Order By`, `Group Join`, `Take While`, a `Skip While`).|[!code-vb[VbVbalrLineContinuation#11](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/statements_25.vb)]<br /><br /> Další informace najdete v tématu [dotazy](../../../visual-basic/language-reference/queries/queries.md).|  
|Po `In` – klíčové slovo v `For Each` příkaz.|[!code-vb[VbVbalrLineContinuation#12](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/statements_26.vb)]<br /><br /> Další informace najdete v tématu [For Each... Další příkaz](../../../visual-basic/language-reference/statements/for-each-next-statement.md).|  
|Po `From` – klíčové slovo v inicializátoru kolekce.|[!code-vb[VbVbalrLineContinuation#13](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/statements_27.vb)]<br /><br /> Další informace najdete v tématu [Inicializátory kolekcí](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md).|  
  
## <a name="adding-comments"></a>Přidávání komentářů  
 Zdrojový kód není vždy samovysvětlující, i pro programátory, kdo ho napsal. Pomoc při zdokumentujte svůj kód, proto většina programátory využívají volná embedded komentáře. Komentáře v kódu se vysvětlují postup či konkrétní pokyny pro každý, kdo čtení nebo ho později práce. Visual Basic ignoruje komentáře během kompilace a neovlivňují zkompilovaný kód.  
  
 Řádky poznámky začínat apostrof (`'`) nebo `REM` následované mezerou. Mohou být přidány kdekoli v kódu, s výjimkou v řetězci. Připojit komentář k výpisu, vložte apostrof nebo `REM` po příkazu, za nímž následuje komentář. Komentáře můžete také přejít na své vlastní samostatný řádek. Následující příklad ukazuje, tyto možnosti.  
  
 [!code-vb[VbVbalrStatements#72](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/statements_28.vb)]  
  
## <a name="checking-compilation-errors"></a>Kontrola chyb kompilace  
 Pokud po typ řádek kódu, se zobrazí na řádku s modrou vlnovkou (zobrazit chybová zpráva může také), je chyba syntaxe v příkazu. Musíte zjistit, co je nesprávný s příkazem (přesunutím vyhledávání v seznamu úloh nebo ukazatele myši chyba ukazatel myši a chybová zpráva pro čtení) a opravte ho. Až do opravení všechny chyby syntaxe v kódu vašeho programu se nepodaří správnou kompilaci.  
  
## <a name="related-sections"></a>Související oddíly  
  
|Termín|Definice|  
|---|---|  
|[Operátory přiřazení](../../../visual-basic/language-reference/operators/assignment-operators.md)|Obsahuje odkazy na referenční stránky jazyk pokrývajících operátory přiřazení, jako `=`, `*=`, a `&=`.|  
|[Operátory a výrazy](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)|Ukazuje, jak má být kombinován elementů s operátorům yield nové hodnoty.|  
|[Postupy: Přerušení a kombinace příkazů v kódu](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)|Ukazuje, jak rozdělit jeden příkaz na více řádků a jak umístit více příkazů na stejném řádku.|  
|[Postupy: Vytváření popisků příkazů](../../../visual-basic/programming-guide/program-structure/how-to-label-statements.md)|Ukazuje, jak pro označení řádku kódu.|
