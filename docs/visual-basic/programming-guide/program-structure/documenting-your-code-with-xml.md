---
title: "Dokumentace kódu s XML (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- XML [Visual Basic], documenting code
- XML comments, Visual Basic
- Visual Basic code, documenting with XML
ms.assetid: a0d35dc7-c5f9-4d74-92ff-a1c6f28d5235
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ddb1f366002c4f0c675c591d83aab1b31ef8f602
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="documenting-your-code-with-xml-visual-basic"></a>Dokumentace kódu s XML (Visual Basic)
V [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)], můžete dokumentu kódu pomocí XML  
  
## <a name="xml-documentation-comments"></a>Dokumentační komentáře XML  
 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]poskytuje snadný způsob, jak automaticky vytvoření dokumentace XML pro projekty. Můžete automaticky generovat kostru XML pro typy a členy a pak zadejte souhrny, popisný dokumentace pro jednotlivé parametry a další poznámky. V instalaci příslušné je automaticky vygenerované dokumentace XML do souboru XML se stejným názvem jako váš projekt a příponu .xml. Další informace najdete v tématu [/doc](../../../visual-basic/reference/command-line-compiler/doc.md).  
  
 Soubor XML můžete využívat nebo jinak s nimi manipulovat jako XML. Tento soubor nachází ve stejném adresáři jako výstupní soubor .exe nebo .dll projektu.  
  
 Dokumentace XML začíná `'''`. Zpracování tyto komentáře má určitá omezení:  
  
-   V dokumentaci musí být ve správném formátu XML. Pokud není ve správném formátu XML, se generuje upozornění a soubor dokumentace obsahuje komentář s informacemi o tom, že došlo k chybě.  
  
-   Vývojáři mohou vytvořit vlastní sadu značky. Existuje sada doporučené značky (viz "Související oddíly" v tomto tématu). Některé z doporučené značky mají zvláštní význam:  
  
    -   \<Param > Značka se používá k popisu parametry. Pokud se používá, kompilátor ověří, zda parametr existuje a že všechny parametry jsou popsané v dokumentaci. Pokud ověření selže, vydá upozornění.  
  
    -   `cref` Atributu může být připojen k žádné značky, které poskytují odkaz na element kódu. Kompilátor ověří, zda tento element kódu existuje. Pokud ověření selže, vydá upozornění. Kompilátor také respektuje žádné `Imports` příkazy při vyhledávání pro typ popsané v `cref` atribut.  
  
    -   \<Souhrnné > Značka je používán IntelliSense v [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] zobrazíte další informace o typ nebo člen.  
  
## <a name="related-sections"></a>Související oddíly  
 Podrobné informace o vytváření souboru XML s dokumentační komentáře najdete v následujících tématech:  
  
-   [/ DOC](../../../visual-basic/reference/command-line-compiler/doc.md)  
  
-   [Značky pro komentáře XML](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)  
  
-   [Zpracování souboru XML](../../../visual-basic/programming-guide/program-structure/processing-the-xml-file.md)  
  
-   [Postupy: vytvoření dokumentace XML](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)  
  
-   [Nástroje XML v sadě Visual Studio](/visualstudio/xml-tools/xml-tools-in-visual-studio)  
  
## <a name="see-also"></a>Viz také  
 [Vývoj aplikací v jazyce Visual Basic](../../../visual-basic/developing-apps/index.md)  
 [Průvodce programováním v jazyce Visual Basic](../../../visual-basic/programming-guide/index.md)
