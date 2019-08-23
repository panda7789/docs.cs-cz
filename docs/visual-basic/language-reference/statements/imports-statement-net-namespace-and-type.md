---
title: Příkaz Imports – obor názvů a typ .NET (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Imports
- imports
helpviewer_keywords:
- declared element names [Visual Basic], qualification
- imports [Visual Basic]
- Imports statement [Visual Basic]
- aliases [Visual Basic], Imports statement
- container elements [Visual Basic]
- namespaces [Visual Basic], importing
- Imports statement [Visual Basic], syntax
- import aliases [Visual Basic]
- aliases [Visual Basic], import
- declared elements [Visual Basic], container elements
ms.assetid: 7062f8aa-d890-4232-9eed-92836e13fb6e
ms.openlocfilehash: a0b7a6a5fd16dc0daa620e6b490ddfdeb0e7c80e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69912389"
---
# <a name="imports-statement-net-namespace-and-type"></a>Imports – příkaz (obor názvů a typ rozhraní .NET)
Povoluje odkazování na názvy typů bez kvalifikace oboru názvů.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Imports [ aliasname = ] namespace  
-or-  
Imports [ aliasname = ] namespace.element  
```  
  
## <a name="parts"></a>Součásti  
  
|Termín|Definice|  
|---|---|  
|`aliasname`|Volitelný parametr. Alias nebo název *importu* , pomocí kterého může kód odkazovat `namespace` místo úplného řetězce kvalifikace. Viz [deklarované názvy elementů](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).|  
|`namespace`|Povinný parametr. Plně kvalifikovaný název oboru názvů, který se má importovat Může to být řetězec oborů názvů vnořený do libovolné úrovně.|  
|`element`|Volitelný parametr. Název programovacího prvku deklarovaného v oboru názvů. Může to být libovolný element kontejneru.|  
  
## <a name="remarks"></a>Poznámky  
 `Imports` Příkaz umožňuje, aby typy, které jsou obsaženy v daném oboru názvů, odkazovaly přímo.  
  
 Můžete dodat jeden název oboru názvů nebo řetězec pro vnořené obory názvů. Všechny vnořené obory názvů jsou oddělené od dalšího oboru názvů vyšší úrovně o periodu (`.`), jak ukazuje následující příklad.  
  
 `Imports System.Collections.Generic`  
  
 Každý zdrojový soubor může obsahovat libovolný počet `Imports` příkazů. Ty musí následovat po deklaracích možností, jako je `Option Strict` například příkaz, a musí předcházet deklaraci všech programovacích prvků `Module` , `Class` jako jsou například příkazy nebo.  
  
 Můžete použít `Imports` pouze na úrovni souboru. To znamená, že kontext deklarace pro import musí být zdrojový soubor a nemůže být obor názvů, třída, struktura, modul, rozhraní, procedura nebo blok.  
  
 Všimněte si, `Imports` že příkaz nezpřístupňuje prvky z jiných projektů a sestavení, která jsou k dispozici pro váš projekt. Import nebere v úvahu místo nastavení odkazu. Pouze odebere nutnost kvalifikovat názvy, které jsou již k dispozici pro váš projekt. Další informace naleznete v tématu "Import obsahující prvky" v [odkazech na deklarované elementy](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).  
  
> [!NOTE]
> Můžete definovat implicitní `Imports` příkazy pomocí [stránky odkazy, Návrháře projektu (Visual Basic)](/visualstudio/ide/reference/references-page-project-designer-visual-basic). Další informace najdete v tématu [jak: Přidání nebo odebrání importovaných oborů názvů (](/visualstudio/ide/how-to-add-or-remove-imported-namespaces-visual-basic)Visual Basic)  
  
## <a name="import-aliases"></a>Importovat aliasy  
 *Alias importu* definuje alias pro obor názvů nebo typ. Importovat aliasy jsou užitečné v případě, že potřebujete použít položky se stejným názvem, které jsou deklarovány v jednom nebo více oborech názvů. Další informace a příklad naleznete v tématu "získání názvu elementu" v [odkazech na deklarované elementy](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).  
  
 Člena byste neměli deklarovat na úrovni modulu se stejným názvem jako `aliasname`. V případě, Visual Basic kompilátor používá `aliasname` pouze pro deklarovaný člen a již jej nerozezná jako alias importu.  
  
 I když syntaxe použitá pro deklarování aliasu importu je stejná jako ta, která se používá pro import předpony oboru názvů XML, výsledky se liší. Alias importu lze použít jako výraz v kódu, zatímco předponu oboru názvů XML lze použít pouze v literálech XML nebo ve vlastnostech osy XML jako předponu pro kvalifikovaný element nebo název atributu.  
  
### <a name="element-names"></a>Názvy elementů  
 Pokud zadáte `element`, musí reprezentovat *prvek kontejneru*, to znamená, že programovací prvek, který může obsahovat další prvky. Prvky kontejneru zahrnují třídy, struktury, moduly, rozhraní a výčty.  
  
 Rozsah prvků, které jsou k dispozici `Imports` příkazem, závisí na tom, zda zadáte. `element` Pokud zadáte pouze `namespace`, budou k dispozici všechny jedinečně pojmenované členy tohoto oboru názvů a členy prvků kontejneru v rámci tohoto oboru názvů, a to bez kvalifikace. Pokud zadáte obojí `namespace` a `element`, budou k dispozici pouze členové tohoto prvku bez kvalifikace.  
  
## <a name="example"></a>Příklad  
 Následující příklad vrátí všechny složky v C:\ adresáře pomocí <xref:System.IO.DirectoryInfo> třídy.  
  
 Kód neobsahuje žádné `Imports` příkazy v horní části souboru. Proto jsou odkazy <xref:System.Text.StringBuilder> <xref:Microsoft.VisualBasic.ControlChars.CrLf> , a plně kvalifikované s obory názvů. `DirectoryInfo`  
  
 [!code-vb[VbVbalrStatements#152](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class12.vb#152)]  
  
## <a name="example"></a>Příklad  
 Následující příklad obsahuje `Imports` příkazy pro odkazované obory názvů. Proto nemusí být typy plně kvalifikované pro obory názvů.  
  
 [!code-vb[VbVbalrStatements#153](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class12.vb#153)]  
  
 [!code-vb[VbVbalrStatements#154](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class12.vb#154)]  
  
## <a name="example"></a>Příklad  
 Následující příklad obsahuje `Imports` příkazy, které vytvářejí aliasy pro odkazované obory názvů. Typy jsou kvalifikovány s aliasy.  
  
 [!code-vb[VbVbalrStatements#155](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class12.vb#155)]  
  
 [!code-vb[VbVbalrStatements#156](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class12.vb#156)]  
  
## <a name="example"></a>Příklad  
 Následující příklad obsahuje `Imports` příkazy, které vytvoří aliasy pro odkazované typy. Aliasy slouží k určení typů.  
  
 [!code-vb[VbVbalrStatements#157](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class12.vb#157)]  
  
 [!code-vb[VbVbalrStatements#158](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class12.vb#158)]  
  
## <a name="see-also"></a>Viz také:

- [Příkaz Namespace](../../../visual-basic/language-reference/statements/namespace-statement.md)
- [Obory názvů v Visual Basic](../../../visual-basic/programming-guide/program-structure/namespaces.md)
- [Odkazy a příkaz Imports](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md)
- [Příkaz Imports (obor názvů XML)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)
- [Odkazy na deklarované elementy](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
