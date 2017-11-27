---
title: "Imports – příkaz (obor názvů a typ rozhraní .NET)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "40"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 46cc78c2fd039fb56fd4d1b797f2d09cbe95d317
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="imports-statement-net-namespace-and-type"></a>Imports – příkaz (obor názvů a typ rozhraní .NET)
Umožňuje zadat názvy bude odkazovat bez kvalifikace názvů.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Imports [ aliasname = ] namespace  
-or-  
Imports [ aliasname = ] namespace.element  
```  
  
## <a name="parts"></a>Součásti  
  
|Termín|Definice|  
|---|---|  
|`aliasname`|Volitelné. *Importovat alias* nebo název, pomocí kterého může kódu odkazovat na `namespace` místo úplné kvalifikace řetězec. V tématu [deklarované názvy elementů](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).|  
|`namespace`|Požadováno. Plně kvalifikovaný název oboru názvů importována. Mohou být řetězec o délce obory názvů vnořené na libovolnou úroveň.|  
|`element`|Volitelné. Název programovací element deklarované v oboru názvů. Může být libovolný element kontejneru.|  
  
## <a name="remarks"></a>Poznámky  
 `Imports` Příkaz umožňuje typy, které jsou obsaženy v daném oboru názvů bude odkazovat přímo.  
  
 Můžete zadat název jednoho oboru názvů nebo řetězec vnořené obory názvů. Každý vnořené obor názvů je oddělená od další vyšší úrovni oboru názvů tečkou (`.`), jak ukazuje následující příklad.  
  
 `Imports System.Collections.Generic`  
  
 Každý zdrojový soubor může obsahovat libovolný počet `Imports` příkazy. Tyto postupujte deklarace všechny možnosti, jako `Option Strict` příkaz a musí předcházet jakékoli programovací element deklarace, jako například `Module` nebo `Class` příkazy.  
  
 Můžete použít `Imports` pouze na úrovni souborů. To znamená kontext deklarace pro import musí být zdrojový soubor a nemůže být obor názvů, třídy, struktury, modulu, rozhraní, postup nebo bloku.  
  
 Všimněte si, že `Imports` příkaz zpřístupnění elementy z jiných projekty a sestavení do projektu. Import nevyžaduje místní nastavení odkaz. Pouze eliminuje nutnost ke kvalifikaci názvy, které jsou již k dispozici do projektu. Další informace najdete v tématu "Import obsahující prvků" v [odkazy na deklarované elementy](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).  
  
> [!NOTE]
>  Můžete definovat implicitní `Imports` příkazy pomocí [stránka odkazy, Návrhář projektu (Visual Basic)](/visualstudio/ide/reference/references-page-project-designer-visual-basic). Další informace najdete v tématu [postupy: Přidání nebo odebrání importovaných oborů názvů (Visual Basic)](/visualstudio/ide/how-to-add-or-remove-imported-namespaces-visual-basic).  
  
## <a name="import-aliases"></a>Import aliasů  
 *Importovat alias* definuje alias oboru názvů nebo typu. Import aliasů jsou užitečné, když potřebujete použití položek se stejným názvem, které jsou deklarované v jedné nebo více oborů názvů. Další informace a příklad najdete v tématu "Kvalifikující elementu název" v [odkazy na deklarované elementy](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).  
  
 Nesmí deklarovat člena na úrovni modulu se stejným názvem jako `aliasname`. Pokud tak učiníte, Visual Basic – kompilátor používá `aliasname` pouze pro deklarované člena a už se rozpozná jako alias importu.  
  
 I když syntaxe pro deklarování import alias se používá jako je například pro import předponu oboru názvů XML, výsledky se liší. Import alias můžete použít jako výraz ve vašem kódu, zatímco předponu oboru názvů XML lze použít pouze v literálech XML nebo vlastnosti osy XML jako předpona pro kvalifikované element nebo atribut name.  
  
### <a name="element-names"></a>Názvy elementů  
 Pokud zadáte `element`, musí představovat *kontejnerový element*, který je programovací element, který může obsahovat další prvky. Elementy kontejneru zahrnují třídy, struktury, moduly, rozhraní a výčty.  
  
 Rozsah elementy, které poskytují `Imports` příkaz závisí na tom, jestli je zadat `element`. Pokud zadáte pouze `namespace`, všechny jednoznačně s názvem Členové tento obor názvů a elementy kontejneru v daném oboru názvů, jsou k dispozici bez kvalifikace. Pokud zadáte oba `namespace` a `element`jen členové tohoto elementu jsou k dispozici bez kvalifikace.  
  
## <a name="example"></a>Příklad  
 Následující příklad vrátí všechny složky v adresáři C:\ pomocí <xref:System.IO.DirectoryInfo> třídy.  
  
 Kód neobsahuje žádné `Imports` příkazy v horní části souboru. Proto `DirectoryInfo`, <xref:System.Text.StringBuilder>, a <xref:Microsoft.VisualBasic.ControlChars.CrLf> jsou odkazy na všechny plně kvalifikovaný s obory názvů.  
  
 [!code-vb[VbVbalrStatements#152](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/imports-statement-net-namespace-and-type_1.vb)]  
  
## <a name="example"></a>Příklad  
 Následující příklad obsahuje `Imports` příkazy pro odkazované obory názvů. Typy proto nemusí být plně kvalifikovaná s obory názvů.  
  
 [!code-vb[VbVbalrStatements#153](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/imports-statement-net-namespace-and-type_2.vb)]  
  
 [!code-vb[VbVbalrStatements#154](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/imports-statement-net-namespace-and-type_3.vb)]  
  
## <a name="example"></a>Příklad  
 Následující příklad obsahuje `Imports` příkazy, které vytvořit aliasy pro odkazované obory názvů. Typy jsou kvalifikovaný s aliasy.  
  
 [!code-vb[VbVbalrStatements#155](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/imports-statement-net-namespace-and-type_4.vb)]  
  
 [!code-vb[VbVbalrStatements#156](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/imports-statement-net-namespace-and-type_5.vb)]  
  
## <a name="example"></a>Příklad  
 Následující příklad obsahuje `Imports` příkazy, které vytvořit aliasy pro odkazované typy. Aliasy slouží k určení typů.  
  
 [!code-vb[VbVbalrStatements#157](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/imports-statement-net-namespace-and-type_6.vb)]  
  
 [!code-vb[VbVbalrStatements#158](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/imports-statement-net-namespace-and-type_7.vb)]  
  
## <a name="see-also"></a>Viz také  
 [Namespace – příkaz](../../../visual-basic/language-reference/statements/namespace-statement.md)  
 [Obory názvů v jazyce Visual Basic](../../../visual-basic/programming-guide/program-structure/namespaces.md)  
 [Odkazy a příkaz Imports](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md)  
 [Imports – příkaz (Namespace XML)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)  
 [Odkazy na deklarované elementy](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
