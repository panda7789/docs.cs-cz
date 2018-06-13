---
title: -doc
ms.date: 03/10/2018
helpviewer_keywords:
- doc compiler option [Visual Basic]
- -doc compiler option [Visual Basic]
- /doc compiler option [Visual Basic]
ms.assetid: 5fc32ec9-a149-4648-994c-a8d0cccd0a65
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6b64372d4b6063da85739e939bb33abd4650ecb4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33651554"
---
# <a name="-doc"></a>-doc
Zpracuje dokumentační komentáře do souboru XML.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
-doc[+ | -]  
' -or-  
-doc:file  
```  
  
## <a name="arguments"></a>Arguments  
  
|Termín|Definice|  
|---|---|  
|`+` &#124; `-`|Volitelné. Určení +, nebo jenom `-doc`, způsobí, že kompilátor generovat informace o dokumentaci a umístěte jej do souboru XML. Určení `-` je ekvivalentem není zadávání `-doc`, způsobuje žádné informace dokumentaci, který se má vytvořit.|  
|`file`|Požadováno pokud `-doc:` se používá. Určuje výstupního souboru XML, který se zobrazí v komentářů ze souborů zdrojového kódu kompilace. Pokud název souboru obsahuje mezery, uzavřete název uvozovek nahoře ("").|  
  
## <a name="remarks"></a>Poznámky  
 `-doc` Možnost ovládací prvky, zda kompilátor vygeneruje soubor XML obsahující dokumentační komentáře. Pokud použijete `-doc:file` syntaxi, která `file` parametr určuje název souboru XML. Pokud používáte `-doc` nebo `-doc+`, kompilátor použije název souboru XML z spustitelný soubor nebo knihovny, který vytváří kompilátoru. Pokud používáte `-doc-` nebo nezadávejte `-doc` možnost kompilátor nevytváří soubor XML.  
  
 V souborech zdrojového kódu lze předcházet dokumentační komentáře následující definice:  
  
-   Uživatelem definované typy, jako například [třída](../../../visual-basic/language-reference/statements/class-statement.md) nebo [rozhraní](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
-   Členové, jako je například pole, [událostí](../../../visual-basic/language-reference/statements/event-statement.md), [vlastnost](../../../visual-basic/language-reference/statements/property-statement.md), [funkce](../../../visual-basic/language-reference/statements/function-statement.md), nebo [podprogramu](../../../visual-basic/language-reference/statements/sub-statement.md).  
  
 Pro použití generovaný soubor XML s sady Visual Studio [IntelliSense](/visualstudio/ide/using-intellisense) funkci, ponechte název souboru XML být stejný jako sestavení, které chcete podporovat. Ujistěte se, že soubor XML je ve stejném adresáři jako sestavení tak, aby při odkazování na sestavení v projektu sady Visual Studio, je také najít soubor .xml. Soubory dokumentace XML nejsou potřeba pro technologii IntelliSense, která pracují pro kódu v rámci projektu nebo projekty odkazuje na projekt.  
  
 Pokud je kompilovat s `/target:module`, soubor XML obsahuje značek `<assembly></assembly>`. Tyto značky zadejte název souboru, který obsahuje manifest sestavení pro výstupní soubor kompilace.  
  
 V tématu [značky pro komentáře XML](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md) pro způsoby, jak generovat dokumentaci z komentářů v kódu.  
  
|Chcete-li nastavit - dokumentů v sadě Visual Studio integrované vývojové prostředí|  
|---|  
|1.  Máte projekt vybraný v **Průzkumníku řešení**. Na **projektu** nabídky, klikněte na tlačítko **vlastnosti**. <br />2.  Klikněte **zkompilovat** kartě.<br />3.  Nastavte hodnotu v **souborů dokumentace XML vygenerovat** pole.|  
  
## <a name="example"></a>Příklad  
 V tématu [dokumentace kódu s XML](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md) pro ukázku.  
  
## <a name="see-also"></a>Viz také  
 [Visual Basic – kompilátor příkazového řádku](../../../visual-basic/reference/command-line-compiler/index.md)  
 [Dokumentace kódu s XML](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md)
