---
title: Imports – příkaz - Namespace .NET a typ (Visual Basic)
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
ms.openlocfilehash: ecb75e71225d2b6705d6235a941ecd83b3aab75b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54699802"
---
# <a name="imports-statement-net-namespace-and-type"></a>Imports – příkaz (obor názvů a typ rozhraní .NET)
Umožňuje zadat názvy se nesmí odkazovat bez kvalifikace názvů.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Imports [ aliasname = ] namespace  
-or-  
Imports [ aliasname = ] namespace.element  
```  
  
## <a name="parts"></a>Součásti  
  
|Termín|Definice|  
|---|---|  
|`aliasname`|Volitelné. *Importovat alias* nebo název, pomocí kterého mohou kódu odkazovat na `namespace` místo úplné kvalifikace řetězce. Zobrazit [deklarované názvy elementů](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).|  
|`namespace`|Povinný parametr. Plně kvalifikovaný název oboru názvů importu. Mohou být řetězec s obory názvů vnořené na libovolné úrovni.|  
|`element`|Volitelné. Název programovací element deklarovaný v oboru názvů. Může být libovolný prvek kontejneru.|  
  
## <a name="remarks"></a>Poznámky  
 `Imports` Příkaz umožňuje typy, které jsou obsaženy v daném oboru názvů se nesmí odkazovat přímo.  
  
 Můžete zadat název jednoho oboru názvů nebo řetězec vnořené obory názvů. Každé vnořené oboru názvů je oddělen od další vyšší úroveň oboru názvů tečku (`.`), jak ukazuje následující příklad.  
  
 `Imports System.Collections.Generic`  
  
 Každý zdrojový soubor může obsahovat libovolný počet `Imports` příkazy. Tyto musí následovat deklarace všechny možnosti, jako `Option Strict` příkaz a musí předcházet jakékoli programovací element deklarace, jako například `Module` nebo `Class` příkazy.  
  
 Můžete použít `Imports` pouze na úrovni souborů. To znamená, že kontext deklarace pro import musí být zdrojový soubor a nemůže být obor názvů, třídy, struktury, modulu, rozhraní, proceduru nebo blok.  
  
 Všimněte si, `Imports` příkaz neprovede elementy z jiných projektů a sestavení k dispozici pro váš projekt. Import nepřijímá místo nastavení odkaz. Odebere pouze potřeba kvalifikovat názvy, které jsou k dispozici pro váš projekt. Další informace najdete v tématu "Import obsahující prvky" [odkazy na deklarované elementy](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).  
  
> [!NOTE]
>  Můžete definovat implicitní `Imports` příkazy pomocí [odkazy na stránky, Návrhář projektu (Visual Basic)](/visualstudio/ide/reference/references-page-project-designer-visual-basic). Další informace najdete v tématu [jak: Přidání nebo odebrání importovaných oborů názvů (Visual Basic)](/visualstudio/ide/how-to-add-or-remove-imported-namespaces-visual-basic).  
  
## <a name="import-aliases"></a>Import aliasů  
 *Importovat alias* alias pro obor názvů nebo typ definuje. Import aliasů jsou užitečné, pokud je třeba použít položky se stejným názvem, které jsou deklarovány v jedné nebo více oborů názvů. Další informace a příklad najdete v tématu "Kvalifikační Element Name" v [odkazy na deklarované elementy](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).  
  
 By neměly deklarovat člena na úrovni modulu se stejným názvem jako `aliasname`. Pokud tak učiníte, kompilátor jazyka Visual Basic používá `aliasname` pouze pro deklarovaná členská a už se rozpozná jako alias importu.  
  
 I když syntaxe pro deklarování aliasu importu se tímto způsobem používá pro import předponu oboru názvů XML, výsledky se liší. Alias importu můžete použít jako výraz ve vašem kódu, zatímco předponu oboru názvů XML lze použít pouze v literály XML a vlastnosti OS XML jako předpona pro kvalifikovaný element nebo název atributu.  
  
### <a name="element-names"></a>Názvy elementů  
 Pokud zadáte `element`, musí představovat *elementu kontejneru*, to znamená, že programový element, který může obsahovat další prvky. Elementy kontejneru zahrnují třídy, struktury, moduly, rozhraní a výčty.  
  
 Rozsah prvků, které jsou k dispozici ve `Imports` příkaz závisí na, jestli mají určovat `element`. Pokud zadáte pouze `namespace`, všechny jedinečné s názvem Členové tohoto oboru názvů a prvky kontejneru v daném oboru názvů, jsou k dispozici bez kvalifikace. Pokud zadáte obě `namespace` a `element`pouze členové tohoto prvku jsou k dispozici bez kvalifikace.  
  
## <a name="example"></a>Příklad  
 Následující příklad vrátí všechny složky v adresáři C:\ s použitím <xref:System.IO.DirectoryInfo> třídy.  
  
 Kód nemá žádné `Imports` příkazů v horní části souboru. Proto `DirectoryInfo`, <xref:System.Text.StringBuilder>, a <xref:Microsoft.VisualBasic.ControlChars.CrLf> odkazy jsou všechny plně kvalifikovaný s obory názvů.  
  
 [!code-vb[VbVbalrStatements#152](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/imports-statement-net-namespace-and-type_1.vb)]  
  
## <a name="example"></a>Příklad  
 Následující příklad obsahuje `Imports` příkazy pro odkazované obory názvů. Typy proto nemusí být plně kvalifikovaný s obory názvů.  
  
 [!code-vb[VbVbalrStatements#153](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/imports-statement-net-namespace-and-type_2.vb)]  
  
 [!code-vb[VbVbalrStatements#154](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/imports-statement-net-namespace-and-type_3.vb)]  
  
## <a name="example"></a>Příklad  
 Následující příklad obsahuje `Imports` příkazy, které vytvořit aliasy pro odkazované obory názvů. Typy jsou kvalifikované aliasy.  
  
 [!code-vb[VbVbalrStatements#155](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/imports-statement-net-namespace-and-type_4.vb)]  
  
 [!code-vb[VbVbalrStatements#156](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/imports-statement-net-namespace-and-type_5.vb)]  
  
## <a name="example"></a>Příklad  
 Následující příklad obsahuje `Imports` příkazy, které vytvořit aliasy pro odkazované typy. Aliasy slouží k určení typů.  
  
 [!code-vb[VbVbalrStatements#157](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/imports-statement-net-namespace-and-type_6.vb)]  
  
 [!code-vb[VbVbalrStatements#158](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/imports-statement-net-namespace-and-type_7.vb)]  
  
## <a name="see-also"></a>Viz také:
- [Příkaz Namespace](../../../visual-basic/language-reference/statements/namespace-statement.md)
- [Obory názvů v jazyce Visual Basic](../../../visual-basic/programming-guide/program-structure/namespaces.md)
- [Odkazy a příkaz Imports](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md)
- [Příkaz Imports (obor názvů XML)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)
- [Odkazy na deklarované elementy](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
