---
title: Zpracování souboru XML (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- XML comments [Visual Basic], parsing [Visual Basic]
ms.assetid: 78a15cd0-7708-4e79-85d1-c154b7a14a8c
ms.openlocfilehash: a10255be140c7c86a435cca98cec5df7df82ffee
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58842093"
---
# <a name="processing-the-xml-file-visual-basic"></a>Zpracování souboru XML (Visual Basic)
Kompilátor generuje řetězec ID pro každý konstrukce ve vašem kódu, který je označený ke generování dokumentace. (Informace o tom, jak označit kódu najdete v tématu [značky pro komentáře XML](../../../visual-basic/language-reference/xmldoc/index.md).) Řetězec ID jednoznačně identifikuje konstrukce. Programy, které zpracování souboru XML slouží k identifikaci, odpovídající řetězec ID [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] položky metadat/reflexe.  
  
 Soubor XML není Hierarchická reprezentace kódu; je seznam bez stromové struktury s vygenerované ID pro každý prvek.  
  
 Při generování ID řetězce, kompilátor dodržuje následující pravidla:  
  
-   Žádné jiné mezery, nachází v řetězci.  
  
-   První část řetězec ID identifikuje typ členu, identifikují se jeden znak následovaný dvojtečkou. Se používají následující typy členů.  
  
|Znak|Popis|  
|---|---|  
|N|– obor názvů<br /><br /> Dokumentační komentáře nelze přidat do oboru názvů, ale může být CREF odkazy, pokud je podporována.|  
|T|Typ: `Class`, `Module`, `Interface`, `Structure`, `Enum`, `Delegate`|  
|F|pole: `Dim`|  
|P|Vlastnost: `Property` (včetně výchozí vlastnosti)|  
|M|Metoda: `Sub`, `Function`, `Declare`, `Operator`|  
|E|událost: `Event`|  
|!|Text chyby<br /><br /> Zbývající řetězec poskytuje informace o této chybě. Kompilátor jazyka Visual Basic generuje informace o chybě pro odkazy, které nelze rozpoznat.|  
  
-   Druhá část `String` je plně kvalifikovaný název položky, počínaje kořenový obor názvů. Název položky, jeho nadřazené typy a obor názvů jsou odděleny tečkami. Obsahuje-li název samotné položky období, budou nahrazeny křížku (#). Předpokládá se, že nemá žádná položka číselném znaku přímo ve svém názvu. Například plně kvalifikovaný název `String` konstruktor by `System.String.#ctor`.  
  
-   Vlastnosti a metody Pokud jsou argumenty metody, uzavřený do závorek seznamu argumentů se řídí. Pokud neexistují žádné argumenty, jsou k dispozici žádné závorky. Argumenty jsou odděleny čárkami. Kódování každý argument přímo řídí, jak je zakódován do [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] podpis.  
  
## <a name="example"></a>Příklad  
 Následující kód ukazuje, jak ID řetězce pro třídu a její členy jsou generovány.  
  
 [!code-vb[VbVbcnXmlDocComments#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#10)]  
  
## <a name="see-also"></a>Viz také:

- [/doc](../../../visual-basic/reference/command-line-compiler/doc.md)
- [Postupy: Vytvoření dokumentace XML](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)
