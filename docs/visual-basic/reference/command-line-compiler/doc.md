---
title: -doc
ms.date: 03/10/2018
helpviewer_keywords:
- doc compiler option [Visual Basic]
- -doc compiler option [Visual Basic]
- /doc compiler option [Visual Basic]
ms.assetid: 5fc32ec9-a149-4648-994c-a8d0cccd0a65
ms.openlocfilehash: 3da049b912d791f26814bb4b6cbb70998803726a
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005645"
---
# <a name="-doc"></a>-doc
Zpracuje komentáře dokumentace do souboru XML.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-doc[+ | -]  
```

or  

```console
-doc:file  
```  
  
## <a name="arguments"></a>Arguments  
  
|Termín|Definice|  
|---|---|  
|`+` &#124; `-`|Volitelné. Zadáním + nebo pouhým `-doc` způsobí, že kompilátor vygeneruje informace o dokumentaci a umístí je do souboru XML. Zadání `-` je ekvivalentem neurčení `-doc`, což nezpůsobí vytvoření informací o dokumentaci.|  
|`file`|Vyžaduje se, pokud se používá `-doc:`. Určuje výstupní soubor XML, který je vyplněn komentáři ze souborů zdrojového kódu kompilace. Pokud název souboru obsahuje mezeru, uzavřete název do uvozovek ("").|  
  
## <a name="remarks"></a>Poznámky  
 Možnost `-doc` určuje, zda kompilátor generuje soubor XML obsahující dokumentační komentáře. Použijete-li syntaxi `-doc:file`, parametr `file` určuje název souboru XML. Použijete-li `-doc` nebo `-doc+`, kompilátor převezme název souboru XML ze spustitelného souboru nebo knihovny, kterou vytvořil kompilátor. Použijete-li `-doc-` nebo nezadáte možnost `-doc`, kompilátor nevytvoří soubor XML.  
  
 V souborech zdrojového kódu mohou komentáře k dokumentaci předcházet následující definice:  
  
- Uživatelsky definované typy, jako je [Třída](../../../visual-basic/language-reference/statements/class-statement.md) nebo [rozhraní](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
- Členy, jako je pole, [událost](../../../visual-basic/language-reference/statements/event-statement.md), [vlastnost](../../../visual-basic/language-reference/statements/property-statement.md), [funkce](../../../visual-basic/language-reference/statements/function-statement.md)nebo [subrutina](../../../visual-basic/language-reference/statements/sub-statement.md).  
  
 Chcete-li použít vygenerovaný soubor XML s funkcí Visual Studio [IntelliSense](/visualstudio/ide/using-intellisense) , nechte název souboru XML stejný jako sestavení, které chcete podporovat. Ujistěte se, že soubor XML je ve stejném adresáři jako sestavení, takže pokud je na sestavení odkazováno v projektu sady Visual Studio, je nalezen soubor. XML také. Soubory dokumentace XML nejsou vyžadovány, aby technologie IntelliSense pracovala pro kód v rámci projektu nebo v rámci projektů, na které se odkazuje v projektu.  
  
 Pokud nekompilujete s `/target:module`, soubor XML obsahuje značky `<assembly></assembly>`. Tyto značky určují název souboru obsahujícího manifest sestavení pro výstupní soubor kompilace.  
  
 Způsoby, jak generovat dokumentaci z komentářů v kódu, naleznete v tématu [značky komentářů XML](../../../visual-basic/language-reference/xmldoc/index.md) .  
  
|Nastavení-doc v integrovaném vývojovém prostředí sady Visual Studio|  
|---|  
|1. v **Průzkumník řešení**mít vybraný projekt. V nabídce **projekt** klikněte na příkaz **vlastnosti**. <br />2. klikněte na kartu **kompilovat** .<br />3. Nastavte hodnotu v poli **Generovat soubor dokumentace XML** .|  
  
## <a name="example"></a>Příklad  
 Ukázku naleznete v tématu [dokumentování kódu pomocí XML](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md) .  
  
## <a name="see-also"></a>Viz také:

- [Visual Basic Kompilátor příkazového řádku](../../../visual-basic/reference/command-line-compiler/index.md)
- [Dokumentace kódu s XML](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md)
