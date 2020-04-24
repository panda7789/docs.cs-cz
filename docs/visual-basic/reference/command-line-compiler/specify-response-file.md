---
title: '@ (určení souboru odezvy)'
ms.date: 03/13/2018
helpviewer_keywords:
- '@ (Specify Response File) compiler option [Visual Basic]'
ms.assetid: a6847eaa-e5f9-4303-9421-45b55484b9ca
ms.openlocfilehash: c578495bbba0efee79f02da284c7feffb8c12fab
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348554"
---
# <a name="-specify-response-file-visual-basic"></a>@ (Určení souboru odezvy) (Visual Basic)

Určuje soubor, který obsahuje možnosti kompilátoru a soubory zdrojového kódu ke kompilaci.

## <a name="syntax"></a>Syntaxe

```console
@response_file
```

## <a name="arguments"></a>Argumenty

`response_file`  
Povinná hodnota. Soubor se seznamem možností kompilátoru nebo souborů zdrojového kódu, které mají být zkompilovány. Uzavřete název souboru do uvozovek (""), pokud obsahuje mezeru.

## <a name="remarks"></a>Poznámky

Kompilátor zpracovává možnosti kompilátoru a soubory zdrojového kódu zadané v souboru odpovědí, jako kdyby byly zadány v příkazovém řádku.

Chcete-li v kompilaci zadat více než jeden soubor odpovědí, zadejte více možností souboru odpovědi, například následující.

```console
@file1.rsp @file2.rsp
```

V souboru odpovědí se může na jednom řádku objevit více možností kompilátoru a souborů zdrojového kódu. Jedna specifikace možnosti kompilátoru se musí vyskytovat na jednom řádku (nemůže zabírat více řádků). Soubory odpovědí mohou obsahovat komentáře, které začínají `#` symbolem.

Můžete kombinovat možnosti zadané v příkazovém řádku s možnostmi určenými v jednom nebo více souborech odpovědí. Kompilátor zpracuje možnosti příkazu, jak je nalezne. Proto argumenty příkazového řádku mohou přepsat dříve uvedené možnosti v souborech odpovědí. Naopak možnosti v parametrech přepsání souboru odpovědí uvedených dříve na příkazovém řádku nebo v jiných souborech odpovědí.

Visual Basic poskytuje soubor Vbc. rsp, který je umístěn ve stejném adresáři jako soubor Vbc. exe. Soubor Vbc. rsp je ve výchozím nastavení zahrnut, pokud `-noconfig` se nepoužívá možnost. Další informace najdete v tématu [-config](../../../visual-basic/reference/command-line-compiler/noconfig.md).

> [!NOTE]
> Tato `@` možnost není k dispozici ve vývojovém prostředí sady Visual Studio; je k dispozici pouze při kompilaci z příkazového řádku.

## <a name="example"></a>Příklad

Následující řádky jsou z ukázkového souboru odezvy.

```console
# build the first output file
-target:exe
-out:MyExe.exe
source1.vb
source2.vb
```

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak použít `@` možnost se souborem odpovědí s názvem. `File1.rsp`

```console
vbc @file1.rsp
```

## <a name="see-also"></a>Viz také

- [Visual Basic Kompilátor příkazového řádku](../../../visual-basic/reference/command-line-compiler/index.md)
- [-noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md)
- [Příkazové řádky ukázkové kompilace](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
