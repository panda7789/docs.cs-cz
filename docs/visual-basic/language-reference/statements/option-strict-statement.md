---
title: Option Strict – příkaz (Visual Basic)
ms.date: 07/20/2015
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
ms.openlocfilehash: 8b7dfcfa394ed2c45adec9661ee1ea5823435223
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72775445"
---
# <a name="option-strict-statement"></a>Option Strict – příkaz
Omezuje implicitní převody datových typů pouze na rozšiřování převodů, nepovoluje pozdní vazbu a nepovoluje implicitní psaní, které má za následek `Object` typ.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
Option Strict { On | Off }  
```  
  
## <a name="parts"></a>Součásti  
  
|Termín|Definice|  
|---|---|  
|`On`|Volitelné. Povolí `Option Strict` kontrolu.|  
|`Off`|Volitelné. Zakáže kontrolu `Option Strict`.|  
  
## <a name="remarks"></a>Poznámky  
 Pokud se `Option Strict On` nebo `Option Strict` objeví v souboru, následující podmínky způsobí chybu při kompilaci:  
  
- Implicitní zužující převody  
  
- Pozdní vazba  
  
- Implicitní zadání, které má za následek `Object` typ  
  
> [!NOTE]
> V konfiguracích upozornění, které lze nastavit na [stránce kompilovat, Návrháře projektu (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)existují tři nastavení, která odpovídají třem podmínkám, které způsobují chybu při kompilaci. Informace o tom, jak použít tato nastavení, najdete v tématu [nastavení konfigurací upozornění v integrovaném vývojovém prostředí](../../../visual-basic/language-reference/statements/option-strict-statement.md#conditions) dále v tomto tématu.  
  
 Příkaz `Option Strict Off` vypne chybu a kontrolu upozornění pro všechny tři podmínky, a to i v případě, že nastavení přidruženého IDE Určuje, že se mají tyto chyby nebo upozornění zapnout. Příkaz `Option Strict On` zapne kontrolu chyb a varování pro všechny tři podmínky, a to i v případě, že se k vypnutí těchto chyb nebo upozornění mají zadat přidružená nastavení IDE.  
  
 Při použití musí být příkaz `Option Strict` uveden před jinými příkazy kódu v souboru.  
  
 Když nastavíte `Option Strict` na `On`, Visual Basic zkontroluje, jestli jsou zadané datové typy pro všechny programovací prvky. Datové typy lze explicitně zadat nebo zadat pomocí odvození místního typu. Doporučuje se zadat datové typy pro všechny vaše programovací prvky, a to z následujících důvodů:  
  
- Umožňuje podporu technologie IntelliSense pro vaše proměnné a parametry. To umožňuje zobrazit jejich vlastnosti a další členy při psaní kódu.  
  
- Umožňuje kompilátoru provést kontrolu typu. Kontrola typu pomáhá najít příkazy, které mohou selhat v době běhu z důvodu chyb konverze typu. Také identifikuje volání metod pro objekty, které tyto metody nepodporují.  
  
- Zrychluje spouštění kódu. Jedním z důvodů je, že pokud neurčíte datový typ pro programovací prvek, Visual Basic kompilátor přiřadí typ `Object`. Zkompilovaný kód může být nutné převést mezi `Object` a jinými datovými typy, což snižuje výkon.  
  
## <a name="implicit-narrowing-conversion-errors"></a>Implicitní zužující chyby převodu  
 K implicitnímu zužujícímu chybám konverze dojde, pokud je k dispozici implicitní převod datového typu, který představuje zužující převod.  
  
 Visual Basic může převést mnoho datových typů na jiné datové typy. Pokud je hodnota jednoho datového typu převedena na datový typ, který má menší přesnost nebo menší kapacitu, může dojít ke ztrátě dat. V případě, že takový zužující převod neproběhne úspěšně, dojde k chybě v době běhu. `Option Strict` zajišťuje při kompilaci oznámení o těchto zužujících převodech, abyste je mohli vyhnout. Další informace naleznete v tématu [implicitní a explicitní převody](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md) a [rozšiřování a zúžení převodů](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).  
  
 Převody, které mohou způsobit chyby, zahrnují implicitní převody, ke kterým dochází ve výrazech. Další informace naleznete v následujících tématech:  
  
- [Operátor +](../../../visual-basic/language-reference/operators/addition-operator.md)  
  
- [Operátor +=](../../../visual-basic/language-reference/operators/addition-assignment-operator.md)  
  
- [\ – Operátor (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md)  
  
- [/= – Operátor (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-assignment-operator.md)  
  
- [Datový typ Char](../../../visual-basic/language-reference/data-types/char-data-type.md)  
  
 Při zřetězení řetězců pomocí [operátoru &](../../../visual-basic/language-reference/operators/concatenation-operator.md)jsou všechny převody na řetězce považovány za rozšiřující. Proto tyto převody negenerují implicitní zužující chybu převodu, i když `Option Strict`.  
  
 Při volání metody, která má argument, který má datový typ jiný než odpovídající parametr, zužující převod způsobí chybu při kompilaci, pokud je `Option Strict` zapnutá. Můžete se vyhnout chybě při kompilaci pomocí rozšiřujícího převodu nebo explicitního převodu.  
  
 Implicitní zužující chyby převodu jsou potlačeny v době kompilace pro převody z prvků v kolekci `For Each…Next` do řídicí proměnné smyčky. K tomu dojde i v případě, že je `Option Strict` zapnutá. Další informace najdete v části "zúžené převody" v tématu [... Další příkaz](../../../visual-basic/language-reference/statements/for-each-next-statement.md).  
  
## <a name="late-binding-errors"></a>Chyby pozdní vazby  
 Objekt je pozdní vazbou, je-li přiřazen k vlastnosti nebo metodě proměnné, která je deklarována jako typu `Object`. Další informace najdete v tématu [počáteční a pozdní vazba](../../../visual-basic/programming-guide/language-features/early-late-binding/index.md).  
  
## <a name="implicit-object-type-errors"></a>Chyby implicitního typu objektu  
 K chybám implicitního typu objektu dojde v případě, že příslušný typ nelze odvodit pro deklarovanou proměnnou, takže typ `Object` je odvozený. K tomu primárně dochází, když použijete příkaz `Dim` k deklaraci proměnné bez použití klauzule `As` a `Option Infer` je vypnutá. Další informace naleznete v tématu [příkaz Option include](../../../visual-basic/language-reference/statements/option-infer-statement.md) a [specifikace jazyka Visual Basic](../../../visual-basic/reference/language-specification/index.md).  
  
 V případě parametrů metody je klauzule `As` volitelná, pokud je `Option Strict` vypnutá. Nicméně, pokud některý z parametrů používá klauzuli `As`, všichni je musí použít. Pokud je `Option Strict` zapnutý, klauzule `As` je vyžadována pro každou definici parametru.  
  
 Pokud deklarujete proměnnou bez použití klauzule `As` a nastavíte ji na `Nothing`, proměnná má typ `Object`. V takovém případě se v případě, že je zapnutá `Option Strict` a `Option Infer`, neobjeví žádná chyba při kompilaci. Příkladem je `Dim something = Nothing`.  
  
### <a name="default-data-types-and-values"></a>Výchozí datové typy a hodnoty  
 Následující tabulka popisuje výsledky různých kombinací určení datového typu a inicializátoru v [příkazu Dim](../../../visual-basic/language-reference/statements/dim-statement.md).  
  
|Byl zadán datový typ?|Byl určen inicializátor?|Příklad|Výsledek|  
|---|---|---|---|  
|Ne|Ne|`Dim qty`|Pokud je `Option Strict` vypnuto (výchozí nastavení), proměnná je nastavena na hodnotu `Nothing`.<br /><br /> Pokud je `Option Strict` zapnutý, dojde k chybě při kompilaci.|  
|Ne|Ano|`Dim qty = 5`|Pokud je `Option Infer` zapnuto (výchozí), proměnná převezme datový typ inicializátoru. Viz [odvození místního typu](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).<br /><br /> Pokud je `Option Infer` vypnuto a `Option Strict` je vypnutý, proměnná převezme datový typ `Object`.<br /><br /> Pokud je `Option Infer` vypnuto a `Option Strict` je zapnutá, dojde k chybě při kompilaci.|  
|Ano|Ne|`Dim qty As Integer`|Proměnná je inicializována na výchozí hodnotu pro datový typ. Další informace naleznete v tématu [Dim – příkaz](../../../visual-basic/language-reference/statements/dim-statement.md).|  
|Ano|Ano|`Dim qty  As Integer = 5`|Pokud datový typ inicializátoru nelze převést na zadaný datový typ, dojde k chybě při kompilaci.|  
  
## <a name="when-an-option-strict-statement-is-not-present"></a>Pokud není k dispozici příkaz Option Strict  
 Pokud zdrojový kód neobsahuje příkaz `Option Strict`, je použita **možnost striktní** nastavení na [stránce kompilovat, návrhář projektu (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) . **Stránka kompilace** obsahuje nastavení, která poskytují další kontrolu nad podmínkami, které generují chybu.  
  
 Pokud používáte kompilátor příkazového řádku, můžete použít možnost kompilátoru [-OptionStrict –](../../../visual-basic/reference/command-line-compiler/optionstrict.md) k určení nastavení pro `Option Strict`.  
  
### <a name="to-set-option-strict-in-the-ide"></a>Nastavení možnosti Strict v integrovaném vývojovém prostředí  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
1. V **Průzkumník řešení**vyberte projekt. V nabídce **projekt** klikněte na příkaz **vlastnosti**.  
  
2. Na kartě **kompilovat** nastavte hodnotu v poli **Option Strict** .  
  
### <a name="conditions"></a>Nastavení konfigurace upozornění v integrovaném vývojovém prostředí  
 Když použijete [stránku kompilovat, Návrhář projektu (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) místo příkazu `Option Strict`, budete mít větší kontrolu nad podmínkami, které generují chyby. Oddíl **Konfigurace upozornění** **stránky kompilace** obsahuje nastavení, která odpovídají třem podmínkám, které způsobují chybu při kompilaci, pokud je `Option Strict` zapnutá. Tato nastavení jsou následující:  
  
- **Implicitní převod**  
  
- **Pozdní vazba; volání může v době běhu selhat.**  
  
- **Implicitní typ; Předpokládá se objekt**  
  
 Pokud nastavíte **možnost Strict** na **zapnuto**, všechna tři tato nastavení konfigurace upozornění jsou nastavená na hodnotu **Chyba**. Pokud nastavíte **možnost Strict** na **vypnuto**, všechna tři nastavení budou nastavena na **hodnotu žádná**.  
  
 Každé nastavení konfigurace upozornění můžete jednotlivě změnit na **žádné**, **varování**nebo **Chyba**. Pokud jsou všechna tři nastavení konfigurace upozornění nastavená na hodnotu **Chyba**, `On` se zobrazí v poli `Option strict`. Pokud jsou všechny tři nastaveny na **hodnotu None**, `Off` se zobrazí v tomto poli. Pro jakoukoli jinou kombinaci těchto nastavení se zobrazí **(vlastní)** .  
  
### <a name="to-set-the-option-strict-default-setting-for-new-projects"></a>Nastavení možnosti striktní výchozí nastavení pro nové projekty  
 Při vytváření projektu je **možnost Option Strict** na kartě **kompilovat** nastavena na hodnotu **Option Strict** v dialogovém okně **Možnosti** .  
  
 Chcete-li nastavit `Option Strict` v tomto dialogovém okně, v nabídce **nástroje** klikněte na položku **Možnosti**. V dialogovém okně **Možnosti** rozbalte **projekty a řešení**a potom klikněte na **výchozí hodnoty VB**. Počáteční výchozí nastavení ve **výchozích hodnotách VB** je `Off`.  
  
### <a name="to-set-option-strict-on-the-command-line"></a>Nastavení možnosti Strict na příkazovém řádku  
 Do příkazu **Vbc** zahrňte možnost kompilátoru [-OptionStrict –](../../../visual-basic/reference/command-line-compiler/optionstrict.md) .  
  
## <a name="example"></a>Příklad  
 Následující příklady demonstrují chyby při kompilaci způsobené implicitními převody typů, které jsou zužující převody. Tato kategorie chyb odpovídá **implicitní podmíněné konverzi** na **stránce kompilace**.  
  
 [!code-vb[VbVbalrStatements#161](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class13.vb#161)]  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje chybu při kompilaci způsobenou pozdní vazbou. Tato kategorie chyb odpovídá **pozdní vazbě. volání může za běhu selhat** na **stránce kompilovat**.  
  
 [!code-vb[VbVbalrStatements#162](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class13.vb#162)]  
  
## <a name="example"></a>Příklad  
 Následující příklady ukazují chyby způsobené proměnnými, které jsou deklarovány pomocí implicitního typu `Object`. Tato kategorie chyb odpovídá **implicitnímu typu; předpokládá** se stav objektu na **stránce kompilace**.  
  
 [!code-vb[VbVbalrStatements#163](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class13.vb#163)]  
  
 [!code-vb[VbVbalrStatements#164](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class13.vb#164)]  
  
## <a name="see-also"></a>Viz také:

- [Rozšíření a zúžení převodů](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [Implicitní a explicitní převody](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [Stránka Kompilovat, Návrhář projektu (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)
- [Příkaz Option Explicit](../../../visual-basic/language-reference/statements/option-explicit-statement.md)
- [Funkce pro převod typů](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Postupy: Přístup ke členům v objektu](../../../visual-basic/programming-guide/language-features/variables/how-to-access-members-of-an-object.md)
- [Vložené výrazy v XML](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)
- [Volný převod delegáta](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
- [Pozdní vazba v řešeních pro systém Office](/visualstudio/vsto/late-binding-in-office-solutions)
- [-optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md)
- [Výchozí hodnoty pro Visual Basic, Projekty, dialogové okno Možnosti](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
