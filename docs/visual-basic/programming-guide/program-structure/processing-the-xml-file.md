---
title: Zpracování souboru XML (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- XML comments [Visual Basic], parsing [Visual Basic]
ms.assetid: 78a15cd0-7708-4e79-85d1-c154b7a14a8c
caps.latest.revision: 16
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 86dae99f2d17a506a27cf491a76083df618ba27b
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="processing-the-xml-file-visual-basic"></a>Zpracování souboru XML (Visual Basic)
Kompilátor generuje řetězec ID pro každý konstrukce ve vašem kódu, který se označí ke generování dokumentace. (Informace o tom, jak označit kódu najdete v tématu [značky pro komentáře XML](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md).) ID řetězec jednoznačně identifikuje konstruktu. Programy, které zpracovávají soubor XML můžete použít ID řetězec k identifikaci odpovídající [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] položky metadat/reflexe.  
  
 Soubor XML není znázornění hierarchické kódu; je to plochý seznam s generovaného ID pro každý prvek.  
  
 Kompilátor dodržuje následující pravidla, když ji vygeneruje ID řetězce:  
  
-   Bez mezer je umístěn v řetězci.  
  
-   První část řetězec ID identifikuje druh člen, které jsou označené pomocí jednoho znaku následovaným dvojtečkou. Se používají následující typy členů.  
  
|Znak|Popis|  
|---|---|  
|N|– obor názvů<br /><br /> Dokumentační komentáře nelze přidat do oboru názvů, ale můžete vytvořit CREF odkazy, pokud je podporována.|  
|T|Typ: `Class`, `Module`, `Interface`, `Structure`, `Enum`, `Delegate`|  
|F|pole: `Dim`|  
|P|Vlastnost: `Property` (včetně výchozí vlastnosti)|  
|M|Metoda: `Sub`, `Function`, `Declare`, `Operator`|  
|E|Události: `Event`|  
|!|Řetězec chyby.<br /><br /> Zbývající řetězec poskytuje informace o této chybě. Visual Basic – kompilátor generuje informace o chybě pro odkazy, které nelze vyřešit.|  
  
-   Druhá část `String` je plně kvalifikovaný název položky začínající na kořen oboru názvů. Název položky, jeho nadřazených typů a obor názvů jsou odděleny tečkami. Pokud název samotné položky obsahuje období, se nahrazují křížku (#). Předpokládá se, že žádná položka má znaménko čísla přímo v jeho názvu. Třeba plně kvalifikovaný název `String` konstruktor by `System.String.#ctor`.  
  
-   Pro vlastnosti a metody Pokud jsou argumenty pro metodu, seznam argumentů uzavřený v závorkách následuje. Pokud neexistují žádné argumenty, jsou k dispozici žádné závorek. Argumenty, které jsou oddělené čárkami. Kódování každý argument přímo řídí, jak je zakódován do [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] podpis.  
  
## <a name="example"></a>Příklad  
 Následující kód ukazuje, jak ID řetězce pro třídu a její členy se generují.  
  
 [!code-vb[VbVbcnXmlDocComments#10](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/processing-the-xml-file_1.vb)]  
  
## <a name="see-also"></a>Viz také  
 [/doc](../../../visual-basic/reference/command-line-compiler/doc.md)  
 [Postupy: Vytvoření dokumentace XML](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)
