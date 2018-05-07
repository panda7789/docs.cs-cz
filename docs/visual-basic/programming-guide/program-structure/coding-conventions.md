---
title: Visual Basic – konvence kódování
ms.date: 07/20/2015
helpviewer_keywords:
- coding conventions [Visual Basic], Visual Basic
- examples [Visual Basic], coding conventions
- Visual Basic code, conventions
ms.assetid: c1df130b-fec6-49a5-becf-0a7e494a1d0f
ms.openlocfilehash: b686747b46529b53b0802a7deb38b5b4949f4d5e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="visual-basic-coding-conventions"></a>Visual Basic – konvence kódování
Microsoft vyvíjí ukázky a dokumentace, která postupujte podle pokynů v tomto tématu. Pokud budete postupovat podle stejné konvence psaní kódu, získáte následující výhody:  
  
-   Váš kód bude mít konzistentní vzhled, tak, aby čtečky můžete lépe zaměřit na obsah, není rozložení.  
  
-   Čtečky pochopit váš kód více rychle protože udělat předpoklady založené na předchozí zkušenosti.  
  
-   Můžete zkopírovat, změnit a snadněji spravovat kód.  
  
-   Můžete zajistit, aby váš kód ukazuje "osvědčené postupy" jazyka Visual Basic.  
  
## <a name="naming-conventions"></a>Zásady vytváření názvů  
  
-   Informace o pojmenování pokyny najdete v tématu [pokyny pro pojmenování](../../../standard/design-guidelines/naming-guidelines.md) tématu.  
  
-   Nepoužívejte "Moje" nebo "Moje" jako součást název proměnné. Tento postup vytvoří záměně se `My` objekty.  
  
-   Nemusíte měnit názvy objektů v automaticky vygenerovaný kód tak, aby byly podle pokynů.  
  
## <a name="layout-conventions"></a>Konvence rozložení  
  
-   Vložení karty prostory a používat inteligentní odsazení s odsazení čtyři místa.  
  
-   Použití **poměrně výpis (přeformátování) z kódu** k opakovanému formátování kódu v editoru kódu. Další informace najdete v tématu [možnosti, textový Editor, Basic (Visual Basic)](/visualstudio/ide/reference/options-text-editor-basic-visual-basic).  
  
-   Použijte pouze jeden příkaz na každém řádku. Nepoužívejte oddělovací znak řádku jazyka Visual Basic (:).  
  
-   Nepoužívejte znak pokračování řádku explicitní "_" považuje implicitní pokračování řádku bez ohledu na to umožňuje jazyk.  
  
-   Použijte pouze jednu deklaraci na každý řádek.  
  
-   Pokud **poměrně výpis (přeformátování) z kódu** nepodporuje řádky formátu pokračování automaticky, je nutné ručně odsazovat jeden zarážku pokračování řádků. Nicméně vždy doleva align položky v seznamu.  
  
    ```  
    a As Integer,  
    b As Integer  
    ```  
  
-   Přidejte alespoň jeden prázdný řádek mezi definice metody a vlastnosti.  
  
## <a name="commenting-conventions"></a>Konvence při psaní komentářů  
  
-   Komentáře uveďte na samostatném řádku místo na konci řádku kódu.  
  
-   Spusťte text poznámky s velkým písmenem a end text poznámky s tečkou.  
  
-   Vložte jeden mezer mezi oddělovač komentář (') a text poznámky.  
  
     [!code-vb[VbVbalrGuidelines#2](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_1.vb)]  
  
-   Není nutné uvést komentáře s formátovaný bloky hvězdičky.  
  
## <a name="program-structure"></a>Struktura programu  
  
-   Při použití `Main` metoda, použít konstrukce výchozí pro nové konzolové aplikace a používat `My` pro argumenty příkazového řádku.  
  
     [!code-vb[VbVbalrGuidelines#3](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_2.vb)]  
  
## <a name="language-guidelines"></a>Pokyny pro jazyk  
  
### <a name="string-data-type"></a>Datový typ String  
  
-   Zřetězení řetězců, použijte znak ampersand (&).  
  
     [!code-vb[VbVbalrGuidelines#4](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_3.vb)]  
  
-   Chcete-li připojit řetězců v smyčky, použijte <xref:System.Text.StringBuilder> objektu.  
  
     [!code-vb[VbVbalrGuidelines#5](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_4.vb)]  
  
### <a name="relaxed-delegates-in-event-handlers"></a>Volný Delegáti v obslužné rutiny událostí  
 Nemohou být explicitně argumenty (objekt a EventArgs) do obslužné rutiny událostí. Pokud nepoužíváte argumenty událostí, které se budou předávat událost (například odesílatel jako objekt, jako EventArgs e), použijte volný Delegáti a vynechte argumenty událostí v kódu:  
  
 [!code-vb[VbVbalrGuidelines#7](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_5.vb)]  
  
### <a name="unsigned-data-type"></a>Nepodepsaný datový typ  
  
-   Použití `Integer` místo typy bez znaménka, s výjimkou tam, kde jsou nezbytné.  
  
### <a name="arrays"></a>Pole  
  
-   Při inicializaci pole na ose deklarace, použijte krátký syntaxi. Například použijte následující syntaxi.  
  
     [!code-vb[VbVbalrGuidelines#8](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_6.vb)]  
  
     Nepoužívejte následující syntaxi.  
  
     [!code-vb[VbVbalrGuidelines#9](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_7.vb)]  
  
-   Uveďte označení pole na typu, nikoli na proměnnou. Například použijte následující syntaxi:  
  
     [!code-vb[VbVbalrGuidelines#11](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_8.vb)]  
  
     Nepoužívejte následující syntaxi:  
  
     [!code-vb[VbVbalrGuidelines#10](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_9.vb)]  
  
-   Pokud deklarace a inicializace pole základní datové typy, použijte syntaxi {}. Například použijte následující syntaxi:  
  
     [!code-vb[VbVbalrGuidelines#12](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_10.vb)]  
  
     Nepoužívejte následující syntaxi:  
  
     [!code-vb[VbVbalrGuidelines#13](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_11.vb)]  
  
### <a name="use-the-with-keyword"></a>Použití s – klíčové slovo  
 Pokud provedete řadu volání jeden objekt, zvažte použití `With` – klíčové slovo:  
  
 [!code-vb[VbVbalrGuidelines#15](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_12.vb)]  
  
### <a name="use-the-trycatch-and-using-statements-when-you-use-exception-handling"></a>Použijte Try... Catch a pomocí příkazy při použití zpracování výjimek  
 Nepoužívejte `On Error Goto`.  
  
### <a name="use-the-isnot-keyword"></a>Použití klíčového slova IsNot  
 Použití `IsNot` – klíčové slovo místo `Not...Is Nothing`.  
  
### <a name="new-keyword"></a>New – klíčové slovo  
  
-   Použijte krátký vytváření instancí. Například použijte následující syntaxi:  
  
     [!code-vb[VbVbalrGuidelines#21](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_13.vb)]  
  
     Předchozí řádek je ekvivalentní k tomuto:  
  
     [!code-vb[VbVbalrGuidelines#22](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_14.vb)]  
  
-   Inicializátory objektů použijte pro všechny nové objekty místo konstruktor bez parametrů:  
  
     [!code-vb[VbVbalrGuidelines#23](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_15.vb)]  
  
### <a name="event-handling"></a>Zpracování událostí  
  
-   Použití `Handles` místo `AddHandler`:  
  
     [!code-vb[VbVbalrGuidelines#24](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_16.vb)]  
  
-   Použití `AddressOf`a ne doložit explicitně delegát:  
  
     [!code-vb[VbVbalrGuidelines#25](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_17.vb)]  
  
-   Když definujete událost, použijte krátký syntaxe a nechat kompilátoru definovat delegát:  
  
     [!code-vb[VbVbalrGuidelines#26](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_18.vb)]  
  
-   Neověřovat, zda je událost `Nothing` (null) před voláním `RaiseEvent` metoda. `RaiseEvent` zkontroluje `Nothing` předtím, než se vyvolá událost.  
  
### <a name="using-shared-members"></a>Pomocí sdílení členové  
 Volání `Shared` členy pomocí názvu třídy, ne z proměnnou instance.  
  
### <a name="use-xml-literals"></a>Použití XML – literály  
 XML – literály zjednodušit běžné úkoly, které dojde při práci s XML (například zatížení, dotazů a transformace). Při vývoji s XML, postupujte podle těchto pokynů:  
  
-   XML – literály použijte k vytvoření dokumentů XML a fragmenty místo přímé volání rozhraní API XML.  
  
-   Importujte obory názvů XML na úrovni souboru nebo projektu chcete využít výhod optimalizací výkonu pro literály XML.  
  
-   Pomocí vlastnosti osy XML pro přístup k elementů a atributů v dokumentu XML.  
  
-   Použít vložené výrazy zahrnout hodnoty a vytvářet XML z existující hodnoty namísto volání rozhraní API, jako `Add` metoda:  
  
     [!code-vb[VbVbalrGuidelines#27](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_19.vb)]  
  
### <a name="linq-queries"></a>Dotazů LINQ  
  
-   Použijte smysluplné názvy proměnných dotazu:  
  
     [!code-vb[VbVbalrGuidelines#28](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_20.vb)]  
  
-   Zadejte názvy elementů v dotazu, abyste měli jistotu, že jsou názvy vlastností anonymní typů správně písmeno pomocí Pascal velká a malá písmena:  
  
     [!code-vb[VbVbalrGuidelines#29](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_21.vb)]  
  
-   Přejmenujte vlastnosti názvy vlastností, které ve výsledku by být nejednoznačný. Například pokud dotaz vrátí zákazníka, název a ID pořadí, přejmenujte je místo necháte jako `Name` a `ID` ve výsledku:  
  
     [!code-vb[VbVbalrGuidelines#30](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_22.vb)]  
  
-   V deklaraci proměnné dotazu a proměnné rozsahu používejte odvození typu:  
  
     [!code-vb[VbVbalrGuidelines#31](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_23.vb)]  
  
-   Zarovnat klauzule dotazu v části `From` příkaz:  
  
     [!code-vb[VbVbalrGuidelines#32](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_24.vb)]  
  
-   Použití `Where` klauzule před ostatními dotaz klauzule tak, aby novější klauzule dotazu pracovat na filtrovanou sadu dat:  
  
     [!code-vb[VbVbalrGuidelines#33](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_25.vb)]  
  
-   Použití `Join` klauzule explicitně definujte operace spojení místo použití `Where` klauzule implicitně definovat operace spojení:  
  
     [!code-vb[VbVbalrGuidelines#34](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_26.vb)]  
  
## <a name="see-also"></a>Viz také  
 [Pokyny pro zabezpečené kódování](../../../standard/security/secure-coding-guidelines.md)
