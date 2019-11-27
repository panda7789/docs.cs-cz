---
title: Příkaz Imports – obor názvů a typ .NET
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
ms.openlocfilehash: 39fa4e74f973bcb575b5751c387c0b879f4e398d
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351071"
---
# <a name="imports-statement-net-namespace-and-type"></a>Imports – příkaz (obor názvů a typ rozhraní .NET)

Povoluje odkazování na názvy typů bez kvalifikace oboru názvů.

## <a name="syntax"></a>Syntaxe

```vb
Imports [ aliasname = ] namespace
' -or-
Imports [ aliasname = ] namespace.element
```

## <a name="parts"></a>Součásti

|Termín|Definice|
|---|---|
|`aliasname`|Volitelná. Alias nebo název *importu* , pomocí kterého může kód odkazovat `namespace` místo úplného řetězce kvalifikace. Viz [deklarované názvy elementů](../../programming-guide/language-features/declared-elements/declared-element-names.md).|
|`namespace`|Požadováno. Plně kvalifikovaný název oboru názvů, který se má importovat Může to být řetězec oborů názvů vnořený do libovolné úrovně.|
|`element`|Volitelná. Název programovacího prvku deklarovaného v oboru názvů. Může to být libovolný element kontejneru.|

## <a name="remarks"></a>Poznámky

Příkaz `Imports` umožňuje, aby typy, které jsou obsaženy v daném oboru názvů, odkazovaly přímo.

Můžete dodat jeden název oboru názvů nebo řetězec pro vnořené obory názvů. Každý vnořený obor názvů je oddělený od dalšího oboru názvů vyšší úrovně o periodě (`.`), jak ukazuje následující příklad:

```vb
Imports System.Collections.Generic
```

Každý zdrojový soubor může obsahovat libovolný počet příkazů `Imports`. Ty musí splňovat jakékoli deklarace možností, jako je například příkaz `Option Strict`, a musí předcházet deklaraci všech programovacích prvků, jako jsou například `Module` nebo `Class` příkazy.

`Imports` můžete použít pouze na úrovni souborů. To znamená, že kontext deklarace pro import musí být zdrojový soubor a nemůže být obor názvů, třída, struktura, modul, rozhraní, procedura nebo blok.

Všimněte si, že příkaz `Imports` nezpřístupňuje prvky z jiných projektů a sestavení, která jsou k dispozici pro váš projekt. Import nebere v úvahu místo nastavení odkazu. Pouze odebere nutnost kvalifikovat názvy, které jsou již k dispozici pro váš projekt. Další informace naleznete v tématu "Import obsahující prvky" v [odkazech na deklarované elementy](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md).

> [!NOTE]
> Můžete definovat implicitní příkazy `Imports` pomocí [stránky odkazy, Návrháře projektu (Visual Basic)](/visualstudio/ide/reference/references-page-project-designer-visual-basic). Další informace najdete v tématu [Postup: Přidání nebo odebrání importovaných oborů názvů (Visual Basic)](/visualstudio/ide/how-to-add-or-remove-imported-namespaces-visual-basic).

## <a name="import-aliases"></a>Importovat aliasy

*Alias importu* definuje alias pro obor názvů nebo typ. Importovat aliasy jsou užitečné v případě, že potřebujete použít položky se stejným názvem, které jsou deklarovány v jednom nebo více oborech názvů. Další informace a příklad naleznete v tématu "získání názvu elementu" v [odkazech na deklarované elementy](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md).

Člena byste neměli deklarovat na úrovni modulu se stejným názvem jako `aliasname`. Pokud tak učiníte, Visual Basic kompilátor používá `aliasname` pouze pro deklarovaný člen a již jej nerozezná jako alias pro import.

I když syntaxe použitá pro deklarování aliasu importu je stejná jako ta, která se používá pro import předpony oboru názvů XML, výsledky se liší. Alias importu lze použít jako výraz v kódu, zatímco předponu oboru názvů XML lze použít pouze v literálech XML nebo ve vlastnostech osy XML jako předponu pro kvalifikovaný element nebo název atributu.

### <a name="element-names"></a>Názvy elementů

Pokud zadáte `element`, musí reprezentovat *prvek kontejneru*, to znamená, že programovací prvek, který může obsahovat další prvky. Prvky kontejneru zahrnují třídy, struktury, moduly, rozhraní a výčty.

Rozsah prvků, které byly k dispozici v příkazu `Imports`, závisí na tom, zda zadáte `element`. Zadáte-li pouze `namespace`, jsou k dispozici všechny jedinečně pojmenované členy tohoto oboru názvů a členy prvků kontejneru v rámci tohoto oboru názvů bez kvalifikace. Pokud zadáte jak `namespace`, tak `element`, jsou k dispozici pouze členové tohoto prvku bez kvalifikace.

## <a name="example"></a>Příklad

Následující příklad vrátí všechny složky v adresáři *C:\\* pomocí <xref:System.IO.DirectoryInfo> třídy:

Kód neobsahuje žádné příkazy `Imports` v horní části souboru. Proto jsou odkazy <xref:System.IO.DirectoryInfo>, <xref:System.Text.StringBuilder>a <xref:Microsoft.VisualBasic.ControlChars.CrLf> plně kvalifikované s obory názvů.

[!code-vb[VbVbalrStatements#152](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class12.vb#152)]

## <a name="example"></a>Příklad

Následující příklad obsahuje příkazy `Imports` pro odkazované obory názvů. Proto nemusí být typy plně kvalifikované pro obory názvů.

[!code-vb[VbVbalrStatements#153](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class12.vb#153)]

[!code-vb[VbVbalrStatements#154](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class12.vb#154)]
  
## <a name="example"></a>Příklad

Následující příklad obsahuje příkazy `Imports`, které vytvářejí aliasy pro odkazované obory názvů. Typy jsou kvalifikovány s aliasy.

[!code-vb[VbVbalrStatements#155](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class12.vb#155)]

[!code-vb[VbVbalrStatements#156](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class12.vb#156)]

## <a name="example"></a>Příklad

Následující příklad obsahuje příkazy `Imports`, které vytvářejí aliasy pro odkazované typy. Aliasy slouží k určení typů.

[!code-vb[VbVbalrStatements#157](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class12.vb#157)]

[!code-vb[VbVbalrStatements#158](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class12.vb#158)]
  
## <a name="see-also"></a>Viz také:

- [Příkaz Namespace](namespace-statement.md)
- [Obory názvů v Visual Basic](../../programming-guide/program-structure/namespaces.md)
- [Odkazy a příkaz Imports](../../programming-guide/program-structure/references-and-the-imports-statement.md)
- [Příkaz Imports (obor názvů XML)](imports-statement-xml-namespace.md)
- [Odkazy na deklarované elementy](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md)
