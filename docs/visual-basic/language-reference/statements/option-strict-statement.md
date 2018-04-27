---
title: Option Strict – příkaz
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Strict
- vb.OptionStrict
helpviewer_keywords:
- Strict keyword [Visual Basic]
- Option Strict statement [Visual Basic]
- conversions [Visual Basic], implicit
- late binding [Visual Basic]
- implicit conversions [Visual Basic]
ms.assetid: 5883e0c1-a920-4274-8e46-b0ff047eaee5
caps.latest.revision: 49
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 0e49c8f64d38b7f8d2dc1a34cf22925c15e3a505
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="option-strict-statement"></a>Option Strict – příkaz
Omezuje převody typu implicitní data do pouze rozšiřující převody zakáže pozdní vazby a zakáže implicitní zadáte, která způsobí, že `Object` typu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Option Strict { On | Off }  
```  
  
## <a name="parts"></a>Součásti  
  
|Termín|Definice|  
|---|---|  
|`On`|Volitelné. Umožňuje `Option Strict` kontrola.|  
|`Off`|Volitelné. Zakáže `Option Strict` kontrola.|  
  
## <a name="remarks"></a>Poznámky  
 Když `Option Strict On` nebo `Option Strict` se zobrazí v souboru, způsobit chybu kompilace následující podmínky:  
  
-   Implicitní zužující převody  
  
-   Pozdní vazba  
  
-   Implicitní zadáte, která způsobí, že `Object` typu  
  
> [!NOTE]
>  V Konfigurace upozornění, které můžete nastavit [stránka kompilovat, Návrhář projektu (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic), existují tři nastavení, které odpovídají tři podmínky, které způsobí chyby kompilace. Informace o tom, jak pomocí tohoto nastavení najdete v tématu [nastavit upozornění konfigurace v prostředí IDE](../../../visual-basic/language-reference/statements/option-strict-statement.md#conditions) dál v tomto tématu.  
  
 `Option Strict Off` Příkaz vypne chyby a upozornění kontrolu pro všechny tři podmínky, i když související nastavení IDE zadejte zapnutí tyto chyby nebo upozornění. `Option Strict On` Příkaz zapne chyby a upozornění kontrolu pro všechny tři podmínky, i když přidružené nastavení IDE určují, chcete-li vypnout tyto chyby nebo upozornění.  
  
 Pokud se používá, `Option Strict` příkaz musíte vložit před jiné příkazy kód v souboru.  
  
 Když nastavíte `Option Strict` k `On`, Visual Basic ověří, že datové typy jsou zadané pro všechny programovací elementy. Datové typy můžete explicitně zadané nebo zadat pomocí odvození místního typu. Určení typů dat pro všechny programovací elementy se doporučuje, z následujících důvodů:  
  
-   Umožňuje podporu technologie IntelliSense pro proměnné a parametry. To vám umožní zobrazit jejich vlastnosti a ostatní členové při psaní kódu.  
  
-   Umožňuje kompilátoru provést kontrola typu. Kontrola typu vám pomůže najít příkazy, které může selhat v době běhu z důvodu chyby při převodu typu. Také identifikuje volání metod pro objekty, které nepodporují těchto metod.  
  
-   Urychluje spuštění kódu. Jeden důvodem je to, že pokud nezadáte datový typ pro programovací element, Visual Basic – kompilátor přiřadí ji `Object` typu. Zkompilovaný kód možná muset převést přepínat mezi `Object` a dalších typů dat, které sníží výkon.  
  
## <a name="implicit-narrowing-conversion-errors"></a>Implicitní zužující převod chyby  
 Implicitní zužující převod chyby nastane, když je převod typu implicitní data, která je zužující převod.  
  
 Visual Basic můžete převést mnoho typů dat na jiné datové typy. Ztráty dat může dojít, když hodnota jednoho datového typu je převést na datový typ, který má menší přesnost nebo menší kapacitu. Chyba spuštění dojde, pokud se nezdaří zužující převod. `Option Strict` kompilace oznámení o těchto zužující převody zajistí tak, aby je se můžete vyhnout. Další informace najdete v tématu [implicitní a explicitní převody](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md) a [Widening a zužující převody](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).  
  
 Převody, které mohou způsobit chyby zahrnout implicitní převody, ke kterým dochází ve výrazech. Další informace naleznete v následujících tématech:  
  
-   [+ – operátor](../../../visual-basic/language-reference/operators/addition-operator.md)  
  
-   [+= – operátor](../../../visual-basic/language-reference/operators/addition-assignment-operator.md)  
  
-   [\ – Operátor (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md)  
  
-   [/ = – Operátor (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-assignment-operator.md)  
  
-   [Datový typ Char](../../../visual-basic/language-reference/data-types/char-data-type.md)  
  
 Když zřetězení řetězců pomocí [& operátor](../../../visual-basic/language-reference/operators/concatenation-operator.md), všechny konverze na řetězce jsou považovány za být rozšíření. Proto tyto převody nevydávají implicitní narrowing Chyba převodu, i když `Option Strict` zapnutý.  
  
 Při volání metody, která má argument, který má datový typ, který se liší od odpovídajícího parametru zužující převod dojde k chybě kompilace, pokud se `Option Strict` na. Chyba kompilace můžete vyhnout použitím rozšiřující převod nebo explicitní převod.  
  
 Implicitní zužující převod chyby, které jsou potlačovány při kompilaci pro převody z elementů v `For Each…Next` kolekce řídicí proměnná smyčky. K tomu dojde i v případě `Option Strict` zapnutý. Další informace najdete v části "Zužující převody" v [For Each... Další příkaz](../../../visual-basic/language-reference/statements/for-each-next-statement.md).  
  
## <a name="late-binding-errors"></a>Pozdní vazba chyby  
 Objekt je pozdní vazba, když je přiřazen k vlastnosti nebo metody proměnné, která je deklarován jako typ `Object`. Další informace najdete v tématu [Early a pozdní vazby](../../../visual-basic/programming-guide/language-features/early-late-binding/index.md).  
  
## <a name="implicit-object-type-errors"></a>Implicitní objekt typ chyby  
 Dochází k chybám typu implicitní objekt když příslušného typu nelze odvodit deklarované proměnné, takže typ `Object` je odvodit. Především proběhne, když používáte `Dim` příkaz deklarovat proměnnou bez použití `As` klauzuli a `Option Infer` je vypnutý. Další informace najdete v tématu [Option Infer – příkaz](../../../visual-basic/language-reference/statements/option-infer-statement.md) a [specifikace jazyka Visual Basic](../../../visual-basic/reference/language-specification/index.md).  
  
 Pro parametry metody `As` klauzule je volitelný Pokud `Option Strict` je vypnutý. Ale pokud žádné jeden parametr používá `As` klauzuli všechny musí používat ho. Pokud `Option Strict` je na serveru, `As` klauzule se vyžaduje pro každý parametr definici.  
  
 Pokud je deklarovat proměnnou bez použití `As` klauzule a nastavte ji na `Nothing`, proměnná má typ `Object`. V takovém případě nedojde k žádné chybě kompilace při `Option Strict` na a `Option Infer` zapnutý. Příkladem je `Dim something = Nothing`.  
  
### <a name="default-data-types-and-values"></a>Typy a hodnoty výchozí Data  
 Následující tabulka popisuje výsledky datový typ a inicializátoru v různých kombinacích [Dim – příkaz](../../../visual-basic/language-reference/statements/dim-statement.md).  
  
|Datový typ zadaný?|Zadaný inicializační?|Příklad|Výsledek|  
|---|---|---|---|  
|Ne|Ne|`Dim qty`|Pokud `Option Strict` je vypnuto (výchozí), proměnná je nastavená na `Nothing`.<br /><br /> Pokud `Option Strict` zapnutý, dojde k chybě kompilace.|  
|Ne|Ano|`Dim qty = 5`|Pokud `Option Infer` je na (výchozí), typ inicializátoru proměnné přijímá data. V tématu [odvození místního typu](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).<br /><br /> Pokud `Option Infer` vypnuté a `Option Strict` je vypnutý, nabývá datový typ `Object`.<br /><br /> Pokud `Option Infer` vypnuté a `Option Strict` zapnutý, dojde k chybě kompilace.|  
|Ano|Ne|`Dim qty As Integer`|Výchozí hodnota pro typ dat je inicializováno proměnnou. Další informace najdete v tématu [Dim – příkaz](../../../visual-basic/language-reference/statements/dim-statement.md).|  
|Ano|Ano|`Dim qty  As Integer = 5`|Pokud datový typ inicializátoru není převést na zadaný datový typ, dojde k chybě kompilace.|  
  
## <a name="when-an-option-strict-statement-is-not-present"></a>Když se nenachází Option Strict – příkaz  
 Pokud zdrojový kód neobsahuje `Option Strict` příkaz, **možnost striktní** nastavení na [stránka kompilovat, Návrhář projektu (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) se používá. **Stránka kompilovat** má nastavení, které poskytují další kontrolu nad podmínky, které k chybě.  
  
 Pokud používáte kompilátoru příkazového řádku, můžete použít [/optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md) – možnost kompilátoru zadat nastavení pro `Option Strict`.  
  
### <a name="to-set-option-strict-in-the-ide"></a>Chcete-li nastavit možnost striktní v prostředí IDE  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
1.  V **Průzkumníku**, vyberte projektu. Na **projektu** nabídky, klikněte na tlačítko **vlastnosti**.  
  
2.  Na **zkompilovat** kartě, nastavte hodnotu v **možnost striktní** pole.  
  
###  <a name="conditions"></a> Chcete-li nastavit upozornění konfigurace v prostředí IDE  
 Při použití [stránka kompilovat, Návrhář projektu (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) místo `Option Strict` prohlášení, budete mít další kontrolu nad podmínky, které generují chyby. **Upozornění konfigurace** části **stránka kompilovat** má nastavení, které odpovídají tři podmínky, které způsobí chybu kompilace při `Option Strict` na. Tato nastavení jsou následující:  
  
-   **Implicitní převod**  
  
-   **Pozdní vazba; volání by mohlo selhat v době běhu**  
  
-   **Implicitní typ; předpokládá, že objekt**  
  
 Když nastavíte **možnost striktní** k **na**, všechny tři z těchto nastavení upozornění konfigurace jsou nastaveny na **chyba**. Když nastavíte **možnost striktní** k **vypnout**, všechny tři nastavení **žádné**.  
  
 Jednotlivě můžete změnit nastavení každou upozornění konfigurace **žádné**, **upozornění**, nebo **chyba**. Pokud mají všechny tři nastavení konfigurace upozornění **chyba**, `On` se zobrazí v `Option strict` pole. Pokud mají všechny tři **žádné**, `Off` se zobrazí v tomto poli. Pro libovolnou kombinací těchto nastavení **(vlastní)** se zobrazí.  
  
### <a name="to-set-the-option-strict-default-setting-for-new-projects"></a>Chcete-li nastavit možnost striktní výchozí nastavení pro nové projekty  
 Při vytváření projektu, **možnost striktní** nastavení na **zkompilovat** karta je nastaven na **možnost striktní** nastavení v **možnosti** Dialogové okno.  
  
 Chcete-li nastavit `Option Strict` v tomto dialogovém na **nástroje** nabídky, klikněte na tlačítko **možnosti**. V **možnosti** dialogové okno, rozbalte seznam **projekty a řešení**a potom klikněte na **VB výchozí**. Počáteční výchozí nastavení v **VB výchozí** je `Off`.  
  
### <a name="to-set-option-strict-on-the-command-line"></a>Chcete-li nastavit možnost striktní na příkazovém řádku  
 Zahrnout [/optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md) – možnost kompilátoru v **Vbc –** příkaz.  
  
## <a name="example"></a>Příklad  
 Následující příklady ukazují způsobené převody implicitní typů, které jsou zužující převody chyby při kompilaci. Tuto kategorii chyb odpovídá **implicitní převod** podmínek na **stránka kompilovat**.  
  
 [!code-vb[VbVbalrStatements#161](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/option-strict-statement_1.vb)]  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje na chybu kompilace způsobené pozdní vazby. Tuto kategorii chyb odpovídá **opožděno vazby; volání by mohlo selhat v době běhu** podmínek na **stránka kompilovat**.  
  
 [!code-vb[VbVbalrStatements#162](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/option-strict-statement_2.vb)]  
  
## <a name="example"></a>Příklad  
 Následující příklady ukazují chyby způsobené proměnné, které jsou deklarovány s implicitní typ `Object`. Tuto kategorii chyb odpovídá **implicitní typ; objektu předpokládá, že** podmínek na **stránka kompilovat**.  
  
 [!code-vb[VbVbalrStatements#163](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/option-strict-statement_3.vb)]  
  
 [!code-vb[VbVbalrStatements#164](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/option-strict-statement_4.vb)]  
  
## <a name="see-also"></a>Viz také  
 [Rozšíření a zúžení převodů](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)  
 [Implicitní a explicitní převody](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)  
 [Stránka Kompilovat, Návrhář projektu (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)  
 [Příkaz Option Explicit](../../../visual-basic/language-reference/statements/option-explicit-statement.md)  
 [Funkce pro převod typů](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [Postupy: Přístup ke členům v objektu](../../../visual-basic/programming-guide/language-features/variables/how-to-access-members-of-an-object.md)  
 [Vložené výrazy v XML](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)  
 [Volný převod delegáta](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)  
 [Pozdní vazba v řešeních pro systém Office](https://msdn.microsoft.com/library/3xxe951d)  
 [/optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md)  
 [Dialogové okno Možnosti výchozí hodnoty, projekty, Visual Basic](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
