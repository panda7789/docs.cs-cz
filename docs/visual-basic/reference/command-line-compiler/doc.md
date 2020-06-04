---
title: -doc
ms.date: 03/10/2018
helpviewer_keywords:
- doc compiler option [Visual Basic]
- -doc compiler option [Visual Basic]
- /doc compiler option [Visual Basic]
ms.assetid: 5fc32ec9-a149-4648-994c-a8d0cccd0a65
ms.openlocfilehash: 57a81983278c26090c62995f4da55c5cbfd66047
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84408670"
---
# <a name="-doc"></a>-doc
Zpracuje komentáře dokumentace do souboru XML.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-doc[+ | -]  
```

nebo  

```console
-doc:file  
```  
  
## <a name="arguments"></a>Argumenty  
  
|Pojem|Definice|  
|---|---|  
|`+`&#124;`-`|Nepovinný parametr. Zadáním + nebo pouhci `-doc` způsobí, že kompilátor vygeneruje informace o dokumentaci a umístí je do souboru XML. Určení `-` je ekvivalent nespecifikující `-doc` , což nezpůsobuje vytváření informací o dokumentaci.|  
|`file`|Vyžaduje `-doc:` se, pokud se používá. Určuje výstupní soubor XML, který je vyplněn komentáři ze souborů zdrojového kódu kompilace. Pokud název souboru obsahuje mezeru, uzavřete název do uvozovek ("").|  
  
## <a name="remarks"></a>Poznámky  
 `-doc`Možnost určuje, zda kompilátor generuje soubor XML obsahující dokumentační komentáře. Použijete-li `-doc:file` syntaxi, `file` parametr určuje název souboru XML. Použijete `-doc` -li nebo `-doc+` , kompilátor převezme název souboru XML ze spustitelného souboru nebo knihovny, kterou vytvořil kompilátor. Použijete `-doc-` -li nebo nezadáte `-doc` možnost, kompilátor nevytvoří soubor XML.  
  
 V souborech zdrojového kódu mohou komentáře k dokumentaci předcházet následující definice:  
  
- Uživatelsky definované typy, jako je [Třída](../../language-reference/statements/class-statement.md) nebo [rozhraní](../../language-reference/statements/interface-statement.md)  
  
- Členy, jako je pole, [událost](../../language-reference/statements/event-statement.md), [vlastnost](../../language-reference/statements/property-statement.md), [funkce](../../language-reference/statements/function-statement.md)nebo [subrutina](../../language-reference/statements/sub-statement.md).  
  
 Chcete-li použít vygenerovaný soubor XML s funkcí Visual Studio [IntelliSense](/visualstudio/ide/using-intellisense) , nechte název souboru XML stejný jako sestavení, které chcete podporovat. Ujistěte se, že soubor XML je ve stejném adresáři jako sestavení, takže pokud je na sestavení odkazováno v projektu sady Visual Studio, je nalezen soubor. XML také. Soubory dokumentace XML nejsou vyžadovány, aby technologie IntelliSense pracovala pro kód v rámci projektu nebo v rámci projektů, na které se odkazuje v projektu.  
  
 Pokud kompilujete s `-target:module` , soubor XML obsahuje značky `<assembly></assembly>` . Tyto značky určují název souboru obsahujícího manifest sestavení pro výstupní soubor kompilace.  
  
 Způsoby, jak generovat dokumentaci z komentářů v kódu, naleznete v tématu [značky komentářů XML](../../language-reference/xmldoc/index.md) .  
  
|Nastavení-doc v integrovaném vývojovém prostředí sady Visual Studio|  
|---|  
|1. v **Průzkumník řešení**mít vybraný projekt. V nabídce **projekt** klikněte na příkaz **vlastnosti**. <br />2. klikněte na kartu **kompilovat** .<br />3. Nastavte hodnotu v poli **Generovat soubor dokumentace XML** .|  
  
## <a name="example"></a>Příklad  
 Ukázku naleznete v tématu [dokumentování kódu pomocí XML](../../programming-guide/program-structure/documenting-your-code-with-xml.md) .  
  
## <a name="see-also"></a>Viz také

- [Visual Basic Kompilátor příkazového řádku](index.md)
- [Dokumentace kódu s XML](../../programming-guide/program-structure/documenting-your-code-with-xml.md)
