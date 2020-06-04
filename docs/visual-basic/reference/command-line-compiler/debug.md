---
title: -debug
ms.date: 03/10/2018
helpviewer_keywords:
- debug compiler switches
- /debug compiler option [Visual Basic]
- -debug compiler option [Visual Basic]
- debug compiler option [Visual Basic]
ms.assetid: c2b0bea5-1d5e-499f-9bd5-4f6c6b715ea2
ms.openlocfilehash: 60c6e512a648f093bb9c70b5af86d5719e544adc
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84408722"
---
# <a name="-debug-visual-basic"></a>-Debug (Visual Basic)

Způsobí, že kompilátor vygeneruje ladicí informace a umístí je do výstupních souborů.

## <a name="syntax"></a>Syntaxe

```console
-debug[+ | -]
```

nebo

```console
-debug:[full | pdbonly]
```

## <a name="arguments"></a>Argumenty

|Pojem|Definice|
|---|---|
|`+`&#124;`-`|Nepovinný parametr. Zadání `+` nebo `-debug` způsobí, že kompilátor generuje ladicí informace a umístí je do souboru. pdb. Zadání `-` má stejný účinek jako nespecifikující `-debug` .|
|`full`&#124;`pdbonly`|Nepovinný parametr. Určuje typ ladicích informací generovaných kompilátorem. Pokud nezadáte `-debug:pdbonly` , použije se výchozí hodnota `full` , která umožňuje připojit k běžícímu programu ladicí program. `pdbonly`Argument umožňuje ladění zdrojového kódu, když je program spuštěn v ladicím programu, ale zobrazuje kód jazyka sestavení pouze v případě, že je spuštěný program připojen k ladicímu programu.|

## <a name="remarks"></a>Poznámky

Tuto možnost použijte k vytvoření sestavení ladění. Pokud nezadáte `-debug` , nebo, `-debug+` `-debug:full` nebudete moci ladit výstupní soubor programu.

Ve výchozím nastavení nejsou informace o ladění generovány ( `-debug-` ). Chcete-li vygenerovat ladicí informace, zadejte `-debug` nebo `-debug+` .

Informace o tom, jak nakonfigurovat výkon ladění aplikace, najdete v tématu [Vytvoření obrázku pro snadnější ladění](../../../framework/debug-trace-profile/making-an-image-easier-to-debug.md).

|Nastavení ladění v integrovaném vývojovém prostředí sady Visual Studio|
|---|
|1. s projektem vybraným v **Průzkumník řešení**v nabídce **projekt** klikněte na **vlastnosti**. <br />2. klikněte na kartu **kompilovat** .<br />3. klikněte na možnost **Pokročilé možnosti kompilace**.<br />4. upravte hodnotu v poli **generovat ladicí informace** .|

## <a name="example"></a>Příklad

Následující příklad vloží informace o ladění do výstupního souboru `App.exe` .

```console
vbc -debug -out:app.exe test.vb
```

## <a name="see-also"></a>Viz také

- [Visual Basic Kompilátor příkazového řádku](index.md)
- [-bugreport](bugreport.md)
- [Příkazové řádky ukázkové kompilace](sample-compilation-command-lines.md)
