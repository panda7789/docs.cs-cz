---
title: '@ (Možnosti kompilátoru C#)'
ms.date: 07/20/2015
f1_keywords:
- '@'
helpviewer_keywords:
- response files, specifying for compilation [C#]
- '@ compiler option'
ms.assetid: dda4fa9f-a02c-400f-8b6a-d58834e13d7f
ms.openlocfilehash: d8e5c0ec148754c3e4cebfa32ad9f44a0bb0119e
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/31/2019
ms.locfileid: "70202909"
---
# <a name="-c-compiler-options"></a>@ (Možnosti kompilátoru C#)
Možnost @ umožňuje zadat soubor, který obsahuje možnosti kompilátoru a soubory zdrojového kódu ke kompilaci.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
@response_file  
```  
  
## <a name="arguments"></a>Arguments  
 `response_file`  
 Soubor se seznamem možností kompilátoru nebo souborů zdrojového kódu, které mají být zkompilovány.  
  
## <a name="remarks"></a>Poznámky  
 Možnosti kompilátoru a soubory zdrojového kódu budou zpracovány kompilátorem stejně, jako kdyby byly zadány v příkazovém řádku.  
  
 Chcete-li v kompilaci zadat více než jeden soubor odpovědí, zadejte více možností souboru odezvy. Příklad:  
  
```console  
@file1.rsp @file2.rsp  
```  
  
 V souboru odpovědí se může na jednom řádku objevit více možností kompilátoru a souborů zdrojového kódu. Jedna specifikace možnosti kompilátoru se musí vyskytovat na jednom řádku (nemůže zasahovat do více řádků). Soubory odpovědí můžou obsahovat komentáře, které začínají symbolem #.  
  
 Zadání možností kompilátoru ze souboru odpovědí je stejně jako vydávání těchto příkazů na příkazovém řádku. Další informace naleznete v tématu sestavování [z příkazového řádku](./how-to-set-environment-variables-for-the-visual-studio-command-line.md) .  
  
 Kompilátor zpracuje možnosti příkazu, jak jsou zjištěny. Proto argumenty příkazového řádku mohou přepsat dříve uvedené možnosti v souborech odpovědí. Naopak možnosti v souboru odpovědí budou přepisovat možnosti uvedené dříve na příkazovém řádku nebo v jiných souborech odpovědí.  
  
 C#poskytuje soubor csc. rsp, který je umístěn ve stejném adresáři jako soubor csc. exe. Další informace o souboru CSc. rsp najdete v článku o [konfiguraci](./noconfig-compiler-option.md) .  
  
 Tuto možnost kompilátoru nelze nastavit ve vývojovém prostředí sady Visual Studio, ani jej nelze změnit programově.  
  
## <a name="example"></a>Příklad  
 Následuje několik řádků z ukázkového souboru odezvy:  
  
```console  
# build the first output file  
-target:exe -out:MyExe.exe source1.cs source2.cs  
```  
  
## <a name="see-also"></a>Viz také:

- [Možnosti kompilátoru jazyka C#](./index.md)
