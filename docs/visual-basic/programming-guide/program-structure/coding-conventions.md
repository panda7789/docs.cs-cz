---
title: Visual Basic – konvence kódování
ms.date: 07/20/2015
helpviewer_keywords:
- coding conventions [Visual Basic], Visual Basic
- examples [Visual Basic], coding conventions
- Visual Basic code, conventions
ms.assetid: c1df130b-fec6-49a5-becf-0a7e494a1d0f
ms.openlocfilehash: f2b1676ae959c5426af3021bbd340980115c5da6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54724879"
---
# <a name="visual-basic-coding-conventions"></a>Visual Basic – konvence kódování
Microsoft vyvíjí vzorky a dokumentaci, postupujte podle pokynů v tomto tématu. Pokud budete postupovat podle stejné konvence psaní kódu, může získat následující výhody:  
  
-   Váš kód bude mít jednotný vzhled tak, aby se čtenáři mohli lépe soustředit na obsah ne na rozložení.  
  
-   Čtenáři pochopí váš kód rychle vzhledem k tomu, že budou mít předpoklady na základě předchozích zkušeností.  
  
-   Můžete zkopírovat, změnit a mnohem snazší údržbu kódu.  
  
-   Zajistíte, že váš kód ukazuje "osvědčené postupy" v jazyce Visual Basic.  
  
## <a name="naming-conventions"></a>Zásady vytváření názvů  
  
-   Informace o pokyny pro pojmenování naleznete v tématu [pokyny pro pojmenování](../../../standard/design-guidelines/naming-guidelines.md) tématu.  
  
-   Nepoužívejte "My" nebo "my" jako součást názvu proměnné. Tento postup vytvoří zmatení s `My` objekty.  
  
-   Nemusíte změnit názvy objektů v automaticky vygenerovaném kódu, aby se daly přizpůsobit pokynům.  
  
## <a name="layout-conventions"></a>Konvence rozložení  
  
-   Vložte tabulátory mezer a použijte inteligentní odsazení o čtyři místa.  
  
-   Použití **Hezký výpis (přeformátování) kódu** k přeformátování kódu v editoru kódu. Další informace najdete v tématu [možnosti, textový Editor, Basic (Visual Basic)](/visualstudio/ide/reference/options-text-editor-basic-visual-basic).  
  
-   Použijte pouze jeden příkaz na každém řádku. Nepoužívejte znak oddělovače řádku jazyka Visual Basic (:).  
  
-   Nepoužívejte znak pokračování explicitní řádku "_" ve prospěch implicitní pokračování řádku bez ohledu na to jazyk umožňuje.  
  
-   Použijte pouze jednu deklaraci na každém řádku.  
  
-   Pokud **Hezký výpis (přeformátování) kódu** nebude pokračovací řádky automaticky, ručně je odsaďte pokračování řádků jednu zarážku tabulátoru. Nicméně vždy vlevo zarovnávejte položky v seznamu.  
  
    ```  
    a As Integer,  
    b As Integer  
    ```  
  
-   Přidejte alespoň jeden prázdný řádek mezi definice metody a vlastnosti.  
  
## <a name="commenting-conventions"></a>Konvence při psaní komentářů  
  
-   Vložte poznámky na samostatný řádek místo na konci řádku kódu.  
  
-   Začněte text komentáře velkým písmenem a ukončit komentář tečkou.  
  
-   Vložte jednu mezeru mezi oddělovač komentáře (') a text komentáře.  
  
     [!code-vb[VbVbalrGuidelines#2](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_1.vb)]  
  
-   Nepoužívejte k ohraničení komentářů formátované bloky hvězdičky z obou stran.  
  
## <a name="program-structure"></a>Struktura programu  
  
-   Při použití `Main` metody, použijte výchozí konstrukci pro nové aplikace konzoly a použít `My` pro argumenty příkazového řádku.  
  
     [!code-vb[VbVbalrGuidelines#3](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_2.vb)]  
  
## <a name="language-guidelines"></a>Pokyny pro jazyk  
  
### <a name="string-data-type"></a>Datový typ String  
  
-   Chcete-li řetězení řetězců, použijte znak ampersand (&).  
  
     [!code-vb[VbVbalrGuidelines#4](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_3.vb)]  
  
-   K přidání řetězce ve smyčkách použijte <xref:System.Text.StringBuilder> objektu.  
  
     [!code-vb[VbVbalrGuidelines#5](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_4.vb)]  
  
### <a name="relaxed-delegates-in-event-handlers"></a>Uvolněné delegáty v obslužných rutinách událostí  
 Nekvalifikujte explicitně argumenty (Object a EventArgs) pro obslužné rutiny událostí. Pokud nepoužíváte argumenty události, které jsou předány události (například odesílatel jako Object, e jako EventArgs), použijte uvolněné delegáty a nechte argumenty události ve vašem kódu:  
  
 [!code-vb[VbVbalrGuidelines#7](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_5.vb)]  
  
### <a name="unsigned-data-type"></a>Nepodepsaný datový typ  
  
-   Použití `Integer` místo typů bez znaménka, s výjimkou případů, kdy jsou nezbytné.  
  
### <a name="arrays"></a>Pole  
  
-   Použijte krátkou syntaxi, když inicializujete pole v řádku deklarace. Například použijte následující syntaxi.  
  
     [!code-vb[VbVbalrGuidelines#8](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_6.vb)]  
  
     Nepoužívejte následující syntaxi.  
  
     [!code-vb[VbVbalrGuidelines#9](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_7.vb)]  
  
-   Vložte pole označení typu, nikoli na proměnnou. Například použijte následující syntaxi:  
  
     [!code-vb[VbVbalrGuidelines#11](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_8.vb)]  
  
     Nepoužívejte následující syntaxi:  
  
     [!code-vb[VbVbalrGuidelines#10](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_9.vb)]  
  
-   Když deklarujete a inicializujete pole základních datových typů, použijte syntax {}. Například použijte následující syntaxi:  
  
     [!code-vb[VbVbalrGuidelines#12](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_10.vb)]  
  
     Nepoužívejte následující syntaxi:  
  
     [!code-vb[VbVbalrGuidelines#13](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_11.vb)]  
  
### <a name="use-the-with-keyword"></a>Používá s klíčovým slovem  
 Pokud provedete sérii volání jednoho objektu, zvažte použití `With` – klíčové slovo:  
  
 [!code-vb[VbVbalrGuidelines#15](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_12.vb)]  
  
### <a name="use-the-trycatch-and-using-statements-when-you-use-exception-handling"></a>Použijte Try... Catch a použití příkazů, když používáte zpracování výjimek  
 Nepoužívejte `On Error Goto`.  
  
### <a name="use-the-isnot-keyword"></a>Použijte klíčové slovo IsNot  
 Použití `IsNot` – klíčové slovo místo `Not...Is Nothing`.  
  
### <a name="new-keyword"></a>New – klíčové slovo  
  
-   Použijte krátkou instanciaci. Například použijte následující syntaxi:  
  
     [!code-vb[VbVbalrGuidelines#21](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_13.vb)]  
  
     Na každém řádku je ekvivalentem tohoto:  
  
     [!code-vb[VbVbalrGuidelines#22](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_14.vb)]  
  
-   Pro nové objekty namísto konstruktoru bez parametrů, použijte inicializátory objektů:  
  
     [!code-vb[VbVbalrGuidelines#23](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_15.vb)]  
  
### <a name="event-handling"></a>Zpracování událostí  
  
-   Použití `Handles` spíše než `AddHandler`:  
  
     [!code-vb[VbVbalrGuidelines#24](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_16.vb)]  
  
-   Použití `AddressOf`a nikoli instanci delegáta explicitně:  
  
     [!code-vb[VbVbalrGuidelines#25](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_17.vb)]  
  
-   Když definujete událost, použijte krátkou syntaxi a nechte kompilátor definovat delegáta:  
  
     [!code-vb[VbVbalrGuidelines#26](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_18.vb)]  
  
-   Nelze ověřit, zda je událost `Nothing` (null), dříve než zavoláte `RaiseEvent` metody. `RaiseEvent` Vyhledá `Nothing` předtím, než vyvolá událost.  
  
### <a name="using-shared-members"></a>Použití sdílených členů  
 Volání `Shared` členy pomocí názvu třídy, nikoli z proměnné instance.  
  
### <a name="use-xml-literals"></a>Použijte literály XML  
 Literály XML zjednodušují zvládnout běžné úkoly, které se vyskytnou při práci s XML (například načtení, dotaz a transformace). Při vývoji v XML postupujte podle následujících pokynů:  
  
-   Použijte literály XML k vytváření dokumentů XML a fragmentů namísto přímého volání rozhraní API XML.  
  
-   Importujte obory názvů XML na úrovni souboru nebo projektu, abyste mohli využít optimalizace výkonu pro literály XML.  
  
-   Použijte vlastnosti osy XML pro přístup k prvkům a atributům v dokumentu XML.  
  
-   Použijte vložené výrazy pro zahrnutí hodnota a vytvoření XML z existujících hodnot namísto použití volání rozhraní API, jako `Add` metody:  
  
     [!code-vb[VbVbalrGuidelines#27](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_19.vb)]  
  
### <a name="linq-queries"></a>Dotazy LINQ  
  
-   Použijte smysluplné názvy proměnných dotazu:  
  
     [!code-vb[VbVbalrGuidelines#28](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_20.vb)]  
  
-   Zadejte názvy prvků v dotazu a ujistěte se, že názvy vlastností anonymních typů mají správnou velikost písmen Pascal použití malých a velkých písmen:  
  
     [!code-vb[VbVbalrGuidelines#29](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_21.vb)]  
  
-   Přejmenujte vlastnosti, pokud by názvy vlastností ve výsledku nejednoznačné. Například pokud dotaz vrátí zákazníka, název a ID objednávky, přejmenujte je, než byste museli opustit jako `Name` a `ID` ve výsledku:  
  
     [!code-vb[VbVbalrGuidelines#30](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_22.vb)]  
  
-   Odvození typu použijte v deklaraci proměnné dotazu a proměnných rozsahu:  
  
     [!code-vb[VbVbalrGuidelines#31](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_23.vb)]  
  
-   Zarovnejte klauzule dotazu v `From` – příkaz:  
  
     [!code-vb[VbVbalrGuidelines#32](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_24.vb)]  
  
-   Použití `Where` klauzule před dalšími klauzulemi dotazu tak, aby pozdější klauzule dotazu pracovaly na filtrované sadě dat:  
  
     [!code-vb[VbVbalrGuidelines#33](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_25.vb)]  
  
-   Použití `Join` klauzule k explicitnímu definování operace spojení namísto použití `Where` klauzule k implicitnímu definování operace spojení:  
  
     [!code-vb[VbVbalrGuidelines#34](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_26.vb)]  
  
## <a name="see-also"></a>Viz také:
- [Pokyny pro zabezpečené kódování](../../../standard/security/secure-coding-guidelines.md)
