---
title: -optioninfer
ms.date: 07/20/2015
f1_keywords:
- -optioninfer
helpviewer_keywords:
- -optioninfer compiler option [Visual Basic]
- /optioninfer compiler option [Visual Basic]
- optioninfer compiler option [Visual Basic]
ms.assetid: f6c09db1-0553-464a-abe3-d4510c61d6ed
ms.openlocfilehash: d7209e431b84e52e487bccbf73bd633a346efde0
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72775610"
---
# <a name="-optioninfer"></a>-optioninfer
Povoluje použití odvození místního typu v deklaracích proměnných.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-optioninfer[+ | -]  
```  
  
## <a name="arguments"></a>Argumenty  
  
|Označení|Definice|  
|---|---|  
|`+`&#124;`-`|Nepovinný parametr. Zadejte `-optioninfer+` , chcete-li povolit odvození místního `-optioninfer-` typu, nebo jej zablokovat. `-optioninfer` Možnost bez zadané hodnoty je stejná jako `-optioninfer+`. Výchozí hodnota, pokud není `-optioninfer` k dispozici přepínač, je `-optioninfer+`také. Výchozí hodnota je nastavena v souboru odpovědí Vbc. rsp.|  
  
> [!NOTE]
> Můžete použít `-noconfig` možnost pro zachování vnitřních výchozích hodnot kompilátoru místo těch, které jsou určeny v Vbc. rsp. Výchozí hodnota kompilátoru pro tuto možnost je `-optioninfer-`.  
  
## <a name="remarks"></a>Poznámky  
 Pokud soubor zdrojového kódu obsahuje [příkaz Option](../../../visual-basic/language-reference/statements/option-infer-statement.md), přepíše příkaz nastavení kompilátoru `-optioninfer` příkazového řádku.  
  
### <a name="to-set--optioninfer-in-the-visual-studio-ide"></a>Nastavení-optioninfer – v integrovaném vývojovém prostředí sady Visual Studio  
  
1. Vyberte projekt v **Průzkumník řešení**. V nabídce **projekt** klikněte na příkaz **vlastnosti**.  
  
2. Na kartě **kompilovat** upravte hodnotu v poli **možnost odvodit** .  
  
## <a name="example"></a>Příklad  
 Následující kód je zkompilován `test.vb` s povoleným odvozením lokálního typu.  
  
```console
vbc -optioninfer+ test.vb  
```  
  
## <a name="see-also"></a>Viz také

- [Visual Basic Kompilátor příkazového řádku](../../../visual-basic/reference/command-line-compiler/index.md)
- [– OptionCompare –](../../../visual-basic/reference/command-line-compiler/optioncompare.md)
- [– OptionExplicit –](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)
- [– OptionStrict –](../../../visual-basic/reference/command-line-compiler/optionstrict.md)
- [Příkazové řádky ukázkové kompilace](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [Option Infer – příkaz](../../../visual-basic/language-reference/statements/option-infer-statement.md)
- [Odvození místního typu](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [Výchozí hodnoty pro Visual Basic, Projekty, dialogové okno Možnosti](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
- [Stránka Kompilovat, návrhář projektu (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)
- [-noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md)
- [Sestavení z příkazového řádku](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md)
