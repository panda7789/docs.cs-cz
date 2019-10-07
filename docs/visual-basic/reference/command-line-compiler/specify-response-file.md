---
title: '@ (Určení souboru odezvy) (Visual Basic)'
ms.date: 03/13/2018
helpviewer_keywords:
- '@ (Specify Response File) compiler option [Visual Basic]'
ms.assetid: a6847eaa-e5f9-4303-9421-45b55484b9ca
ms.openlocfilehash: deab111cc669941a1cd7dc143dd699b6521221bb
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004989"
---
# <a name="-specify-response-file-visual-basic"></a>@ (Určení souboru odezvy) (Visual Basic)
Určuje soubor, který obsahuje možnosti kompilátoru a soubory zdrojového kódu ke kompilaci.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
@response_file  
```  
  
## <a name="arguments"></a>Arguments  
 `response_file`  
 Požadováno. Soubor se seznamem možností kompilátoru nebo souborů zdrojového kódu, které mají být zkompilovány. Uzavřete název souboru do uvozovek (""), pokud obsahuje mezeru.  
  
## <a name="remarks"></a>Poznámky  
 Kompilátor zpracovává možnosti kompilátoru a soubory zdrojového kódu zadané v souboru odpovědí, jako kdyby byly zadány v příkazovém řádku.  
  
 Chcete-li v kompilaci zadat více než jeden soubor odpovědí, zadejte více možností souboru odpovědi, například následující.  
  
```console  
@file1.rsp @file2.rsp  
```  
  
 V souboru odpovědí se může na jednom řádku objevit více možností kompilátoru a souborů zdrojového kódu. Jedna specifikace možnosti kompilátoru se musí vyskytovat na jednom řádku (nemůže zabírat více řádků). Soubory odpovědí mohou obsahovat komentáře, které začínají symbolem `#`.  
  
 Můžete kombinovat možnosti zadané v příkazovém řádku s možnostmi určenými v jednom nebo více souborech odpovědí. Kompilátor zpracuje možnosti příkazu, jak je nalezne. Proto argumenty příkazového řádku mohou přepsat dříve uvedené možnosti v souborech odpovědí. Naopak možnosti v parametrech přepsání souboru odpovědí uvedených dříve na příkazovém řádku nebo v jiných souborech odpovědí.  
  
 Visual Basic poskytuje soubor Vbc. rsp, který je umístěn ve stejném adresáři jako soubor Vbc. exe. Pokud není použita možnost `-noconfig`, je soubor Vbc. rsp součástí výchozího nastavení. Další informace najdete v tématu [-config](../../../visual-basic/reference/command-line-compiler/noconfig.md).  
  
> [!NOTE]
> Možnost `@` není k dispozici ve vývojovém prostředí sady Visual Studio; je k dispozici pouze při kompilaci z příkazového řádku.  
  
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
 Následující příklad ukazuje, jak použít možnost `@` se souborem odpovědí s názvem `File1.rsp`.  
  
```console
vbc @file1.rsp  
```  
  
## <a name="see-also"></a>Viz také:

- [Visual Basic Kompilátor příkazového řádku](../../../visual-basic/reference/command-line-compiler/index.md)
- [-noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md)
- [Příkazové řádky ukázkové kompilace](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
