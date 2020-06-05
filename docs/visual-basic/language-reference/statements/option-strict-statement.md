---
title: Option Strict – příkaz
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
ms.openlocfilehash: 9c86ae6be86591445dde3cc4e7bdd38aa4a7f0fa
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404340"
---
# <a name="option-strict-statement"></a>Option Strict – příkaz
Omezuje implicitní převody datových typů pouze na rozšiřování převodů, nepovoluje pozdní vazbu a nepovoluje implicitní psaní, které má za následek `Object` typ.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
Option Strict { On | Off }  
```  
  
## <a name="parts"></a>Součásti  
  
|Pojem|Definice|  
|---|---|  
|`On`|Nepovinný parametr. Povoluje `Option Strict` kontrolu.|  
|`Off`|Nepovinný parametr. Zakáže `Option Strict` kontrolu.|  
  
## <a name="remarks"></a>Poznámky  
 Při `Option Strict On` nebo `Option Strict` zobrazení v souboru, následující podmínky způsobí chybu při kompilaci:  
  
- Implicitní zužující převody  
  
- Pozdní vazba  
  
- Implicitní zadání, které má za následek `Object` typ  
  
> [!NOTE]
> V konfiguracích upozornění, které lze nastavit na [stránce kompilovat, Návrháře projektu (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)existují tři nastavení, která odpovídají třem podmínkám, které způsobují chybu při kompilaci. Informace o tom, jak použít tato nastavení, najdete v tématu [nastavení konfigurací upozornění v integrovaném vývojovém prostředí](option-strict-statement.md#conditions) dále v tomto tématu.  
  
 `Option Strict Off`Příkaz vypne chybu a kontrolu upozornění pro všechny tři podmínky, a to i v případě, že nastavení přidruženého IDE Určuje, aby se tyto chyby nebo upozornění zapnuly. `Option Strict On`Příkaz zapne kontrolu chyb a varování pro všechny tři podmínky, a to i v případě, že se k vypnutí těchto chyb nebo upozornění mají zadat přidružená nastavení IDE.  
  
 Je-li použit, `Option Strict` příkaz musí být uveden před jinými příkazy kódu v souboru.  
  
 Když nastavíte `Option Strict` na `On` , Visual Basic kontroluje, zda jsou pro všechny programovací prvky zadány datové typy. Datové typy lze explicitně zadat nebo zadat pomocí odvození místního typu. Doporučuje se zadat datové typy pro všechny vaše programovací prvky, a to z následujících důvodů:  
  
- Umožňuje podporu technologie IntelliSense pro vaše proměnné a parametry. To umožňuje zobrazit jejich vlastnosti a další členy při psaní kódu.  
  
- Umožňuje kompilátoru provést kontrolu typu. Kontrola typu pomáhá najít příkazy, které mohou selhat v době běhu z důvodu chyb konverze typu. Také identifikuje volání metod pro objekty, které tyto metody nepodporují.  
  
- Zrychluje spouštění kódu. Jedním z důvodů je, že pokud neurčíte datový typ pro programovací prvek, Visual Basic kompilátor přiřadí `Object` typ. Zkompilovaný kód může být nutné převádět mezi `Object` a jinými datovými typy, což snižuje výkon.  
  
## <a name="implicit-narrowing-conversion-errors"></a>Implicitní zužující chyby převodu  
 K implicitnímu zužujícímu chybám konverze dojde, pokud je k dispozici implicitní převod datového typu, který představuje zužující převod.  
  
 Visual Basic může převést mnoho datových typů na jiné datové typy. Pokud je hodnota jednoho datového typu převedena na datový typ, který má menší přesnost nebo menší kapacitu, může dojít ke ztrátě dat. V případě, že takový zužující převod neproběhne úspěšně, dojde k chybě v době běhu. `Option Strict`zajišťuje při kompilaci oznámení o těchto zužujících převodech, abyste je mohli vyhnout. Další informace naleznete v tématu [implicitní a explicitní převody](../../programming-guide/language-features/data-types/implicit-and-explicit-conversions.md) a [rozšiřování a zúžení převodů](../../programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).  
  
 Převody, které mohou způsobit chyby, zahrnují implicitní převody, ke kterým dochází ve výrazech. Další informace najdete v následujících tématech:  
  
- [+ – Operátor](../operators/addition-operator.md)  
  
- [+ = – Operátor](../operators/addition-assignment-operator.md)  
  
- [\ – Operátor (Visual Basic)](../operators/integer-division-operator.md)  
  
- [/= – Operátor (Visual Basic)](../operators/floating-point-division-assignment-operator.md)  
  
- [Char – datový typ](../data-types/char-data-type.md)  
  
 Při zřetězení řetězců pomocí [operátoru&](../operators/concatenation-operator.md)jsou všechny převody na řetězce považovány za rozšiřující. Proto tyto převody negenerují implicitní zužující chybu převodu, i když `Option Strict` je zapnutý.  
  
 Při volání metody, která má argument, který má datový typ jiný než odpovídající parametr, zúžený převod způsobí chybu kompilace, pokud `Option Strict` je zapnut. Můžete se vyhnout chybě při kompilaci pomocí rozšiřujícího převodu nebo explicitního převodu.  
  
 Implicitní zužující chyby převodu jsou potlačeny v době kompilace pro převody z prvků v `For Each…Next` kolekci do řídicí proměnné smyčky. K tomu dojde i `Option Strict` v případě, že je zapnutá. Další informace najdete v části "zúžené převody" v tématu [... Další příkaz](for-each-next-statement.md).  
  
## <a name="late-binding-errors"></a>Chyby pozdní vazby  
 Objekt je pozdní vazbou, je-li přiřazen k vlastnosti nebo metodě proměnné, která je deklarována jako typ `Object` . Další informace najdete v tématu [počáteční a pozdní vazba](../../programming-guide/language-features/early-late-binding/index.md).  
  
## <a name="implicit-object-type-errors"></a>Chyby implicitního typu objektu  
 K chybám implicitního typu objektu dojde v případě, že příslušný typ nelze odvodit pro deklarovanou proměnnou, takže typ `Object` je odvozený. K tomu primárně dochází, když použijete `Dim` příkaz k deklaraci proměnné bez použití `As` klauzule a `Option Infer` je vypnuta. Další informace naleznete v tématu [příkaz Option include](option-infer-statement.md) a [specifikace jazyka Visual Basic](../../reference/language-specification/index.md).  
  
 V případě parametrů metody `As` je klauzule volitelná, pokud `Option Strict` je vypnuta. Nicméně, pokud některý z parametrů používá `As` klauzuli, všichni je musí použít. Pokud `Option Strict` je na, `As` klauzule je vyžadována pro každou definici parametru.  
  
 Pokud deklarujete proměnnou bez použití `As` klauzule a nastavíte ji na `Nothing` , proměnná má typ `Object` . V tomto případě v případě, že je zapnutý `Option Strict` a je zapnutá, nedošlo k žádné chybě v době kompilace `Option Infer` . Příkladem je `Dim something = Nothing` .  
  
### <a name="default-data-types-and-values"></a>Výchozí datové typy a hodnoty  
 Následující tabulka popisuje výsledky různých kombinací určení datového typu a inicializátoru v [příkazu Dim](dim-statement.md).  
  
|Byl zadán datový typ?|Byl určen inicializátor?|Příklad|Výsledek|  
|---|---|---|---|  
|Ne|Ne|`Dim qty`|Pokud `Option Strict` je vypnuto (výchozí nastavení), proměnná je nastavena na `Nothing` .<br /><br /> Pokud `Option Strict` je, dojde k chybě při kompilaci.|  
|No|Ano|`Dim qty = 5`|Pokud `Option Infer` je zapnuto (výchozí), proměnná převezme datový typ inicializátoru. Viz [odvození místního typu](../../programming-guide/language-features/variables/local-type-inference.md).<br /><br /> Pokud `Option Infer` je vypnutý a `Option Strict` je vypnutý, proměnná vezme datový typ `Object` .<br /><br /> Pokud `Option Infer` je vypnutý a `Option Strict` je zapnutý, dojde k chybě při kompilaci.|  
|Ano|Ne|`Dim qty As Integer`|Proměnná je inicializována na výchozí hodnotu pro datový typ. Další informace naleznete v tématu [Dim – příkaz](dim-statement.md).|  
|Ano|Ano|`Dim qty  As Integer = 5`|Pokud datový typ inicializátoru nelze převést na zadaný datový typ, dojde k chybě při kompilaci.|  
  
## <a name="when-an-option-strict-statement-is-not-present"></a>Pokud není k dispozici příkaz Option Strict  
 Pokud zdrojový kód neobsahuje `Option Strict` příkaz, je použita **možnost Strict** nastavení na [stránce kompilovat, Návrhář projektu (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) . **Stránka kompilace** obsahuje nastavení, která poskytují další kontrolu nad podmínkami, které generují chybu.  
  
 Pokud používáte kompilátor příkazového řádku, můžete použít možnost kompilátoru [-OptionStrict –](../../reference/command-line-compiler/optionstrict.md) a zadat nastavení pro `Option Strict` .  
  
### <a name="to-set-option-strict-in-the-ide"></a>Nastavení možnosti Strict v integrovaném vývojovém prostředí  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
1. V **Průzkumník řešení**vyberte projekt. V nabídce **projekt** klikněte na příkaz **vlastnosti**.  
  
2. Na kartě **kompilovat** nastavte hodnotu v poli **Option Strict** .  
  
### <a name="to-set-warning-configurations-in-the-ide"></a><a name="conditions"></a>Nastavení konfigurace upozornění v integrovaném vývojovém prostředí  
 Když použijete [stránku kompilovat, Návrhář projektu (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) místo `Option Strict` příkazu, budete mít větší kontrolu nad podmínkami, které generují chyby. Oddíl **Konfigurace upozornění** **stránky kompilace** obsahuje nastavení, která odpovídají třem podmínkám, které způsobují chybu při kompilaci, pokud `Option Strict` je zapnutá. Tato nastavení jsou následující:  
  
- **Implicitní převod**  
  
- **Pozdní vazba; volání může v době běhu selhat.**  
  
- **Implicitní typ; Předpokládá se objekt**  
  
 Pokud nastavíte **možnost Strict** na **zapnuto**, všechna tři tato nastavení konfigurace upozornění jsou nastavená na hodnotu **Chyba**. Pokud nastavíte **možnost Strict** na **vypnuto**, všechna tři nastavení budou nastavena na **hodnotu žádná**.  
  
 Každé nastavení konfigurace upozornění můžete jednotlivě změnit na **žádné**, **varování**nebo **Chyba**. Pokud jsou všechna tři nastavení konfigurace upozornění nastavena na hodnotu **Chyba**, `On` zobrazí se v `Option strict` poli. Pokud jsou všechny tři nastaveny na **možnost žádné**, `Off` zobrazí se v tomto poli. Pro jakoukoli jinou kombinaci těchto nastavení se zobrazí **(vlastní)** .  
  
### <a name="to-set-the-option-strict-default-setting-for-new-projects"></a>Nastavení možnosti striktní výchozí nastavení pro nové projekty  
 Při vytváření projektu je **možnost Option Strict** na kartě **kompilovat** nastavena na hodnotu **Option Strict** v dialogovém okně **Možnosti** .  
  
 Chcete-li nastavit `Option Strict` v tomto dialogovém okně, klikněte v nabídce **nástroje** na příkaz **Možnosti**. V dialogovém okně **Možnosti** rozbalte **projekty a řešení**a potom klikněte na **výchozí hodnoty VB**. Výchozí výchozí nastavení ve výchozím nastavení **jazyka VB** je `Off` .  
  
### <a name="to-set-option-strict-on-the-command-line"></a>Nastavení možnosti Strict na příkazovém řádku  
 Do příkazu **Vbc** zahrňte možnost kompilátoru [-OptionStrict –](../../reference/command-line-compiler/optionstrict.md) .  
  
## <a name="example"></a>Příklad  
 Následující příklady demonstrují chyby při kompilaci způsobené implicitními převody typů, které jsou zužující převody. Tato kategorie chyb odpovídá **implicitní podmíněné konverzi** na **stránce kompilace**.  
  
 [!code-vb[VbVbalrStatements#161](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class13.vb#161)]  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje chybu při kompilaci způsobenou pozdní vazbou. Tato kategorie chyb odpovídá **pozdní vazbě. volání může za běhu selhat** na **stránce kompilovat**.  
  
 [!code-vb[VbVbalrStatements#162](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class13.vb#162)]  
  
## <a name="example"></a>Příklad  
 Následující příklady ukazují chyby způsobené proměnnými, které jsou deklarovány s implicitním typem `Object` . Tato kategorie chyb odpovídá **implicitnímu typu; předpokládá** se stav objektu na **stránce kompilace**.  
  
 [!code-vb[VbVbalrStatements#163](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class13.vb#163)]  
  
 [!code-vb[VbVbalrStatements#164](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class13.vb#164)]  
  
## <a name="see-also"></a>Viz také

- [Rozšíření a zúžení převodů](../../programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [Implicitní a explicitní převody](../../programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [Stránka Kompilovat, návrhář projektu (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)
- [Option Explicit – příkaz](option-explicit-statement.md)
- [Funkce pro převod typů](../functions/type-conversion-functions.md)
- [Postupy: Přístup ke členům v objektu](../../programming-guide/language-features/variables/how-to-access-members-of-an-object.md)
- [Vložené výrazy v XML](../../programming-guide/language-features/xml/embedded-expressions-in-xml.md)
- [Volný převod delegáta](../../programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
- [Pozdní vazba v řešeních pro systém Office](/visualstudio/vsto/late-binding-in-office-solutions)
- [-optionstrict](../../reference/command-line-compiler/optionstrict.md)
- [Výchozí hodnoty pro Visual Basic, Projekty, dialogové okno Možnosti](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
