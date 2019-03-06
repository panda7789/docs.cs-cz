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
ms.openlocfilehash: adfac0eebc0d50ed3c8c523c0442636b05901c18
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57355126"
---
# <a name="option-strict-statement"></a>Option Strict – příkaz
Omezí implicitní převody typů dat jenom na rozšiřující převody, nepovoluje pozdní vazby a zakazuje implicitního zápisu, která vede `Object` typu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Option Strict { On | Off }  
```  
  
## <a name="parts"></a>Součásti  
  
|Termín|Definice|  
|---|---|  
|`On`|Volitelné. Umožňuje `Option Strict` kontrolu.|  
|`Off`|Volitelné. Zakáže `Option Strict` kontrolu.|  
  
## <a name="remarks"></a>Poznámky  
 Když `Option Strict On` nebo `Option Strict` se zobrazí v souboru následujících podmínek způsobit chybu kompilace:  
  
-   Implicitní zužující převody  
  
-   Pozdní vazba  
  
-   Implicitního zápisu, která vede `Object` typu  
  
> [!NOTE]
>  V konfiguraci upozornění, které můžete nastavit na [stránka kompilovat, Návrhář projektu (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic), existují tři nastavení, které odpovídají uvedených tří podmínek, které způsobí chybu kompilace. Informace o tom, jak pomocí těchto nastavení najdete v tématu [nastavit upozornění konfigurace v integrovaném vývojovém prostředí](../../../visual-basic/language-reference/statements/option-strict-statement.md#conditions) dále v tomto tématu.  
  
 `Option Strict Off` Příkaz vypne chyby a upozornění kontrolu všech tří podmínek, i v případě, že související nastavení prostředí IDE zadat zapnout tyto chyby nebo varování. `Option Strict On` Příkaz zapne chyby a upozornění kontrolu všech tří podmínek, i v případě, že související nastavení prostředí IDE zadat vypnout tyto chyby nebo varování.  
  
 Pokud použijete, `Option Strict` příkazu musí být uvedena před další příkazy kódu v souboru.  
  
 Pokud nastavíte `Option Strict` k `On`, Visual Basic ověří, že datové typy jsou určeny pro všechny programovací prvky. Datové typy lze explicitně zadán nebo zadat pomocí odvození místního typu. Určení typů dat pro vaše programovací prvky se doporučuje, z následujících důvodů:  
  
-   Umožňuje podporu technologie IntelliSense pro proměnné a parametry. To vám umožní zobrazit jejich vlastnosti a ostatní členové při psaní kódu.  
  
-   Umožňuje kompilátoru provést kontrolu typu. Kontrola typu vám pomůže najít příkazy, které můžete v době běhu selhat z důvodu chyby převodu typu. Také identifikuje volání metod na objekty, které nepodporují tyto metody.  
  
-   Urychluje provádění kódu. Jedním z důvodů je, že pokud nezadáte datový typ pro programový element, kompilátor jazyka Visual Basic přiřadí ji `Object` typu. Zkompilovaný kód může být nutné převést vpřed a zpět mezi `Object` a ostatními datovými typy, což snižuje výkon.  
  
## <a name="implicit-narrowing-conversion-errors"></a>Implicitní zužující převod chyby  
 Implicitní zužující převod chybám dochází při konverzi typu implicitní data, která je zužující převod.  
  
 Visual Basic můžete převést mnoho datových typů na jiné datové typy. Při převodu na datový typ, který má nižší přesnost nebo menší kapacitu hodnota jednoho typu dat, může dojít ke ztrátě dat. Pokud selže zužující převod, dojde k chybě za běhu. `Option Strict` kompilace oznámení o těchto zužujících převodů zajistí tak, aby jim zabránit. Další informace najdete v tématu [implicitní a explicitní převody](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md) a [Widening a zúžení převodů](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).  
  
 Převody, které mohou způsobit chyby patří implicitních převodů, ke kterým dochází ve výrazech. Další informace naleznete v následujících tématech:  
  
-   [+ – operátor](../../../visual-basic/language-reference/operators/addition-operator.md)  
  
-   [+= – operátor](../../../visual-basic/language-reference/operators/addition-assignment-operator.md)  
  
-   [\ – Operátor (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md)  
  
-   [/ = – Operátor (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-assignment-operator.md)  
  
-   [Datový typ Char](../../../visual-basic/language-reference/data-types/char-data-type.md)  
  
 Při zřetězení řetězců s použitím [& – operátor](../../../visual-basic/language-reference/operators/concatenation-operator.md), všechny převody na řetězce jsou považovány za být rozšíření. Tak tyto převody nejsou generovány implicitní zužující převod chyby, i když `Option Strict` zapnutý.  
  
 Při volání metody, která má argument, který má datový typ, který se liší od odpovídajícího parametru zužující převod způsobí chybu kompilace, pokud `Option Strict` zapnutý. Chyba kompilace můžete vyhnout použitím rozšiřující převod nebo explicitní převod.  
  
 V době kompilace pro převod z prvků v jsou potlačeny chyby implicitní zužující převod `For Each…Next` kolekce řídicí proměnná smyčky for. K tomu dojde i v případě `Option Strict` zapnutý. Další informace najdete v části "Zužující převody" v [For Each... Další příkaz](../../../visual-basic/language-reference/statements/for-each-next-statement.md).  
  
## <a name="late-binding-errors"></a>Pozdní vazby chyby  
 Objekt je přiřazeno k vlastnosti nebo metody, která je deklarována se typ proměnné pozdní vazby `Object`. Další informace najdete v tématu [včasného a pozdní vazby](../../../visual-basic/programming-guide/language-features/early-late-binding/index.md).  
  
## <a name="implicit-object-type-errors"></a>Implicitní typ chyby  
 Implicitní typ chybám dochází, když odpovídající typ se nedá odvodit deklarované proměnné, tak typu `Object` je odvozen. To dochází především při použití `Dim` příkaz k deklaraci proměnné bez použití `As` klauzule a `Option Infer` je vypnuté. Další informace najdete v tématu [Option Infer – příkaz](../../../visual-basic/language-reference/statements/option-infer-statement.md) a [specifikace jazyka Visual Basic](../../../visual-basic/reference/language-specification/index.md).  
  
 Pro parametry metody `As` je volitelná klauzule Pokud `Option Strict` je vypnuté. Ale pokud se používá jakékoli jeden parametr `As` klauzule všechny musí používat ho. Pokud `Option Strict` zapnutý, `As` klauzule se vyžaduje pro každou definici parametru.  
  
 Pokud deklarujete proměnnou bez použití `As` klauzule a nastavte ho na `Nothing`, je proměnná typu `Object`. V tomto případě dojde k žádné chybě kompilace při `Option Strict` na a `Option Infer` zapnutý. Příkladem je `Dim something = Nothing`.  
  
### <a name="default-data-types-and-values"></a>Výchozí datové typy a hodnoty  
 Následující tabulka popisuje výsledky různých kombinací určující typ dat a obsahuje inicializační proceduru [příkazu Dim](../../../visual-basic/language-reference/statements/dim-statement.md).  
  
|Zadaný datový typ?|Inicializátor zadaný?|Příklad|Výsledek|  
|---|---|---|---|  
|Ne|Ne|`Dim qty`|Pokud `Option Strict` je vypnuto (výchozí), je proměnná nastavena `Nothing`.<br /><br /> Pokud `Option Strict` zapnutý, dojde k chybě kompilace.|  
|Ne|Ano|`Dim qty = 5`|Pokud `Option Infer` je zapnuto (výchozí), zadejte proměnné přijímá data z inicializátoru. Zobrazit [odvození místního typu](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).<br /><br /> Pokud `Option Infer` je vypnuté a `Option Strict` je vypnuté, nabývá datový typ `Object`.<br /><br /> Pokud `Option Infer` je vypnuté a `Option Strict` zapnutý, dojde k chybě kompilace.|  
|Ano|Ne|`Dim qty As Integer`|Proměnná je inicializována na výchozí hodnotu pro typ dat. Další informace najdete v tématu [příkazu Dim](../../../visual-basic/language-reference/statements/dim-statement.md).|  
|Ano|Ano|`Dim qty  As Integer = 5`|Pokud datový typ inicializátor není lze převést na zadaný datový typ, dojde k chybě kompilace.|  
  
## <a name="when-an-option-strict-statement-is-not-present"></a>Pokud není k dispozici Option Strict – příkaz  
 Pokud zdrojový kód neobsahuje `Option Strict` příkazu **možnost strict** nastavení [stránka kompilovat, Návrhář projektu (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) se používá. **Stránka kompilovat** má nastavení, které poskytují větší kontrolu nad podmínky, které vygenerují chybu.  
  
 Pokud používáte kompilátoru příkazového řádku, můžete použít [/optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md) – možnost kompilátoru zadat nastavení pro `Option Strict`.  
  
### <a name="to-set-option-strict-in-the-ide"></a>Nastavení Option Strict v integrovaném vývojovém prostředí  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
1.  V **Průzkumníka řešení**, vyberte projekt. Na **projektu** nabídky, klikněte na tlačítko **vlastnosti**.  
  
2.  Na **kompilaci** kartu, nastavte hodnotu **Option Strict** pole.  
  
### <a name="conditions"></a> Chcete-li nastavit upozornění konfigurace v prostředí IDE  
 Při použití [stránka kompilovat, Návrhář projektu (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) místo `Option Strict` prohlášení, máte větší kontrolu nad podmínky, které generují chyby. **Upozornění konfigurace** část **stránka kompilovat** má nastavení, které odpovídají uvedených tří podmínek, které způsobí chybu kompilace při `Option Strict` zapnutý. Tato nastavení jsou následující:  
  
-   **Implicitní převod**  
  
-   **Pozdní vazba. volání by mohlo selhat v době běhu**  
  
-   **Implicitní typ; převzatý objekt**  
  
 Pokud nastavíte **Option Strict** k **na**, všechna tři nastavení konfigurace upozornění jsou nastaveny na **chyba**. Pokud nastavíte **Option Strict** k **vypnout**, všechny tři nastavení **žádný**.  
  
 Samostatně můžete změnit nastavení každé upozornění konfigurace **žádný**, **upozornění**, nebo **chyba**. Pokud mají všechny tři nastavení konfigurace upozornění **chyba**, `On` se zobrazí v `Option strict` pole. Pokud mají všechny tři **žádný**, `Off` se zobrazí v tomto poli. Pro libovolnou kombinaci těchto nastavení **(vlastní)** se zobrazí.  
  
### <a name="to-set-the-option-strict-default-setting-for-new-projects"></a>Abyste nastavili možnost Option Strict výchozí pro nové projekty  
 Při vytváření projektu, **Option Strict** nastavení **kompilaci** karty nastavená na **Option Strict** nastavení **možnosti** Dialogové okno.  
  
 Chcete-li nastavit `Option Strict` v tomto dialogovém okně na **nástroje** nabídky, klikněte na tlačítko **možnosti**. V **možnosti** dialogového okna rozbalte **projekty a řešení**a potom klikněte na tlačítko **VB výchozí**. Počáteční výchozí nastavení v **výchozí hodnoty pro VB** je `Off`.  
  
### <a name="to-set-option-strict-on-the-command-line"></a>Nastavení Option Strict na příkazovém řádku  
 Zahrnout [/optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md) – možnost kompilátoru v **Vbc –** příkazu.  
  
## <a name="example"></a>Příklad  
 Následující příklady ukazují chyby při kompilaci způsobené převodům implicitních typů, které jsou zužujících převodů. Tato kategorie chyby odpovídá **implicitní převod** podmínky na **stránka kompilovat**.  
  
 [!code-vb[VbVbalrStatements#161](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class13.vb#161)]  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje chybu kompilace způsobil pozdní vazbou. Odpovídá této kategorie chyby **opožděno vazba; volání by mohlo selhat v době běhu** podmínky na **stránka kompilovat**.  
  
 [!code-vb[VbVbalrStatements#162](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class13.vb#162)]  
  
## <a name="example"></a>Příklad  
 Následující příklady ukazují chyb způsobených proměnné, které jsou deklarovány s implicitním typem `Object`. Tato kategorie chyby odpovídá **implicitní typ; převzatý objekt** podmínky na **stránka kompilovat**.  
  
 [!code-vb[VbVbalrStatements#163](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class13.vb#163)]  
  
 [!code-vb[VbVbalrStatements#164](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class13.vb#164)]  
  
## <a name="see-also"></a>Viz také:

- [Rozšíření a zúžení převodů](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [Implicitní a explicitní převody](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [Stránka Kompilovat, Návrhář projektu (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)
- [Příkaz Option Explicit](../../../visual-basic/language-reference/statements/option-explicit-statement.md)
- [Funkce pro převod typů](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Postupy: Přístup k členům v objektu](../../../visual-basic/programming-guide/language-features/variables/how-to-access-members-of-an-object.md)
- [Vložené výrazy v XML](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)
- [Volný převod delegáta](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
- [Pozdní vazba v řešeních pro systém Office](/visualstudio/vsto/late-binding-in-office-solutions)
- [/optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md)
- [Výchozí hodnoty pro Visual Basic, Projekty, dialogové okno Možnosti](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
