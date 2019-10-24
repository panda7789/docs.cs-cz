---
title: /debug (Visual Basic)
ms.date: 03/10/2018
helpviewer_keywords:
- debug compiler switches
- /debug compiler option [Visual Basic]
- -debug compiler option [Visual Basic]
- debug compiler option [Visual Basic]
ms.assetid: c2b0bea5-1d5e-499f-9bd5-4f6c6b715ea2
ms.openlocfilehash: 27485cda9bb2af980b300180134fd7e99ffceeba
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72775677"
---
# <a name="-debug-visual-basic"></a>-Debug (Visual Basic)

Způsobí, že kompilátor vygeneruje ladicí informace a umístí je do výstupních souborů.

## <a name="syntax"></a>Syntaxe

```console
-debug[+ | -]
```

or

```console
-debug:[full | pdbonly]
```

## <a name="arguments"></a>Arguments

|Termín|Definice|
|---|---|
|`+` &#124; `-`|Volitelné. Zadání `+` nebo `/debug` způsobí, že kompilátor vygeneruje ladicí informace a umístí je do souboru. pdb. Zadání `-` má stejný účinek jako nespecifikuje `/debug`.|
|`full` &#124; `pdbonly`|Volitelné. Určuje typ ladicích informací generovaných kompilátorem. Pokud nezadáte `/debug:pdbonly`, výchozí hodnota je `full`, což umožňuje připojit k běžícímu programu ladicí program. Argument `pdbonly` umožňuje ladění zdrojového kódu, když je program spuštěn v ladicím programu, ale zobrazuje kód jazyka sestavení pouze v případě, že je spuštěný program připojen k ladicímu programu.|

## <a name="remarks"></a>Poznámky

Tuto možnost použijte k vytvoření sestavení ladění. Pokud nezadáte `/debug`, `/debug+` nebo `/debug:full`, nebudete moct ladit výstupní soubor programu.

Ve výchozím nastavení nejsou informace o ladění generovány (`/debug-`). Chcete-li vygenerovat informace o ladění, zadejte `/debug` nebo `/debug+`.

Informace o tom, jak nakonfigurovat výkon ladění aplikace, najdete v tématu [Vytvoření obrázku pro snadnější ladění](../../../framework/debug-trace-profile/making-an-image-easier-to-debug.md).

|Nastavení ladění v integrovaném vývojovém prostředí sady Visual Studio|
|---|
|1. s projektem vybraným v **Průzkumník řešení**v nabídce **projekt** klikněte na **vlastnosti**. <br />2. klikněte na kartu **kompilovat** .<br />3. klikněte na možnost **Pokročilé možnosti kompilace**.<br />4. upravte hodnotu v poli **generovat ladicí informace** .|

## <a name="example"></a>Příklad

Následující příklad vloží informace o ladění do výstupního souboru `App.exe`.

```console
vbc -debug -out:app.exe test.vb
```

## <a name="see-also"></a>Viz také:

- [Visual Basic Kompilátor příkazového řádku](../../../visual-basic/reference/command-line-compiler/index.md)
- [-bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md)
- [Příkazové řádky ukázkové kompilace](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
