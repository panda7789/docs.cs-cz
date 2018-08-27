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
ms.openlocfilehash: 4c77d063d64354bf4693ce82509f36be9d2e5b0c
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/26/2018
ms.locfileid: "42934476"
---
# <a name="-doc"></a>-doc
Zpracuje komentáře dokumentace do souboru XML.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
-doc[+ | -]  
' -or-  
-doc:file  
```  
  
## <a name="arguments"></a>Arguments  
  
|Termín|Definice|  
|---|---|  
|`+` &#124; `-`|Volitelné. Určení +, nebo jen `-doc`, způsobí, že kompilátor generovat informace o dokumentaci a umístěte ho do souboru XML. Určení `-` je ekvivalentem bez zadání `-doc`, způsobí žádné informace o dokumentaci má být vytvořen.|  
|`file`|Požadováno pokud `-doc:` se používá. Určuje výstupní soubor XML, který je naplněn komentáře v souborech zdrojového kódu kompilace. Pokud název souboru obsahuje mezery, uzavřete název uvozovek ("").|  
  
## <a name="remarks"></a>Poznámky  
 `-doc` Možnost řídí, zda kompilátor generuje soubor XML obsahující komentáře k dokumentaci. Pokud používáte `-doc:file` syntaxe, `file` parametr určuje název souboru XML. Pokud používáte `-doc` nebo `-doc+`, kompilátor přijímá název souboru XML ze spustitelného souboru nebo knihovny, který vytváří kompilátor. Pokud používáte `-doc-` nebo nezadávejte `-doc` možnost, kompilátor nevytváří soubor XML.  
  
 V souborech zdrojového kódu může dokumentační komentáře předcházet následující definice:  
  
-   Uživatelem definované typy, jako [třídy](../../../visual-basic/language-reference/statements/class-statement.md) nebo [rozhraní](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
-   Členy, jako je například pole, [události](../../../visual-basic/language-reference/statements/event-statement.md), [vlastnost](../../../visual-basic/language-reference/statements/property-statement.md), [funkce](../../../visual-basic/language-reference/statements/function-statement.md), nebo [podprogram](../../../visual-basic/language-reference/statements/sub-statement.md).  
  
 Pomocí sady Visual Studio vygenerovaný soubor XML [IntelliSense](/visualstudio/ide/using-intellisense) funkcí, ponechte název souboru XML být stejný jako sestavení, které chcete podporovat. Ujistěte se, že soubor XML ve stejném adresáři jako sestavení tak, aby při sestavení se odkazuje v projektu sady Visual Studio, je také najít soubor .xml. Soubory dokumentace XML nejsou nutné pro technologii IntelliSense pro kód v rámci projektu nebo v rámci projektů odkazuje projekt.  
  
 Pokud kompilujete s `/target:module`, soubor XML obsahuje značky `<assembly></assembly>`. Tyto značky zadejte název souboru obsahujícího manifest sestavení pro výstupní soubor sestavení.  
  
 Zobrazit [značky pro komentáře XML](../../../visual-basic/language-reference/xmldoc/index.md) způsoby, jak generovat dokumentaci z komentáře v kódu.  
  
|Chcete-li nastavit - doc v sadě Visual Studio integrované vývojové prostředí|  
|---|  
|1.  Mají projekt vybraný v **Průzkumníka řešení**. Na **projektu** nabídky, klikněte na tlačítko **vlastnosti**. <br />2.  Klikněte na tlačítko **kompilaci** kartu.<br />3.  Nastavte hodnotu **soubor dokumentace XML vygenerovat** pole.|  
  
## <a name="example"></a>Příklad  
 Zobrazit [dokumentace kódu s XML](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md) ukázku.  
  
## <a name="see-also"></a>Viz také  
 [Kompilátor příkazového řádku jazyka Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)  
 [Dokumentace kódu s XML](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md)
