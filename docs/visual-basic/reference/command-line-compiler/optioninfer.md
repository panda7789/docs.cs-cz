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
ms.openlocfilehash: 524660fca7c56fa490cc85169898bf2bf6d1a16e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400575"
---
# <a name="-optioninfer"></a>-optioninfer
Povoluje použití odvození místního typu v deklaracích proměnných.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-optioninfer[+ | -]  
```  
  
## <a name="arguments"></a>Argumenty  
  
|Pojem|Definice|  
|---|---|  
|`+`&#124;`-`|Nepovinný parametr. Zadejte `-optioninfer+` , chcete-li povolit odvození místního typu, nebo `-optioninfer-` jej zablokovat. `-optioninfer`Možnost bez zadané hodnoty je stejná jako `-optioninfer+` . Výchozí hodnota, pokud není k `-optioninfer` dispozici přepínač, je také `-optioninfer+` . Výchozí hodnota je nastavena v souboru odpovědí Vbc. rsp.|  
  
> [!NOTE]
> Můžete použít `-noconfig` možnost pro zachování vnitřních výchozích hodnot kompilátoru místo těch, které jsou určeny v Vbc. rsp. Výchozí hodnota kompilátoru pro tuto možnost je `-optioninfer-` .  
  
## <a name="remarks"></a>Poznámky  
 Pokud soubor zdrojového kódu obsahuje [příkaz Option](../../language-reference/statements/option-infer-statement.md), přepíše příkaz `-optioninfer` nastavení kompilátoru příkazového řádku.  
  
### <a name="to-set--optioninfer-in-the-visual-studio-ide"></a>Nastavení-optioninfer – v integrovaném vývojovém prostředí sady Visual Studio  
  
1. Vyberte projekt v **Průzkumník řešení**. V nabídce **projekt** klikněte na příkaz **vlastnosti**.  
  
2. Na kartě **kompilovat** upravte hodnotu v poli **možnost odvodit** .  
  
## <a name="example"></a>Příklad  
 Následující kód je zkompilován `test.vb` s povoleným odvozením lokálního typu.  
  
```console
vbc -optioninfer+ test.vb  
```  
  
## <a name="see-also"></a>Viz také

- [Visual Basic Kompilátor příkazového řádku](index.md)
- [-optioncompare](optioncompare.md)
- [-optionexplicit](optionexplicit.md)
- [-optionstrict](optionstrict.md)
- [Příkazové řádky ukázkové kompilace](sample-compilation-command-lines.md)
- [Option Infer – příkaz](../../language-reference/statements/option-infer-statement.md)
- [Odvození místního typu](../../programming-guide/language-features/variables/local-type-inference.md)
- [Výchozí hodnoty pro Visual Basic, Projekty, dialogové okno Možnosti](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
- [Stránka Kompilovat, návrhář projektu (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)
- [-noconfig](noconfig.md)
- [Sestavení z příkazového řádku](building-from-the-command-line.md)
