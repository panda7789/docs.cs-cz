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
ms.openlocfilehash: 4848dec148bc528e7a30940643e3364f1bb5f805
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69939203"
---
# <a name="-optioninfer"></a>-optioninfer
Povoluje použití odvození místního typu v deklaracích proměnných.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
-optioninfer[+ | -]  
```  
  
## <a name="arguments"></a>Arguments  
  
|Termín|Definice|  
|---|---|  
|`+` &#124; `-`|Volitelný parametr. Zadejte `-optioninfer+` , chcete-li povolit odvození místního `-optioninfer-` typu, nebo jej zablokovat. Možnost bez zadané hodnoty je stejná jako `-optioninfer+`. `-optioninfer` Výchozí hodnota, pokud `-optioninfer` není k dispozici přepínač, je také. `-optioninfer+` Výchozí hodnota je nastavena v souboru odpovědí Vbc. rsp.|  
  
> [!NOTE]
> Můžete použít `-noconfig` možnost pro zachování vnitřních výchozích hodnot kompilátoru místo těch, které jsou určeny v Vbc. rsp. Výchozí hodnota kompilátoru pro tuto možnost je `-optioninfer-`.  
  
## <a name="remarks"></a>Poznámky  
 Pokud soubor zdrojového kódu obsahuje [příkaz Option](../../../visual-basic/language-reference/statements/option-infer-statement.md), přepíše `-optioninfer` příkaz nastavení kompilátoru příkazového řádku.  
  
### <a name="to-set--optioninfer-in-the-visual-studio-ide"></a>Nastavení-optioninfer – v integrovaném vývojovém prostředí sady Visual Studio  
  
1. Vyberte projekt v **Průzkumník řešení**. V nabídce **projekt** klikněte na příkaz **vlastnosti**.  
  
2. Na kartě **kompilovat** upravte hodnotu v poli **možnost odvodit** .  
  
## <a name="example"></a>Příklad  
 Následující kód je zkompilován `test.vb` s povoleným odvozením lokálního typu.  
  
```console
vbc -optioninfer+ test.vb  
```  
  
## <a name="see-also"></a>Viz také:

- [Visual Basic Kompilátor příkazového řádku](../../../visual-basic/reference/command-line-compiler/index.md)
- [-optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md)
- [-optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)
- [-optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md)
- [Příkazové řádky ukázkové kompilace](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [Příkaz Option Infer](../../../visual-basic/language-reference/statements/option-infer-statement.md)
- [Odvození místního typu](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [Výchozí hodnoty pro Visual Basic, Projekty, dialogové okno Možnosti](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
- [Stránka Kompilovat, Návrhář projektu (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)
- [/noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md)
- [Sestavení z příkazového řádku](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md)
