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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "70202909"
---
# <a name="-c-compiler-options"></a>@ (Možnosti kompilátoru C#)
Možnost @ umožňuje zadat soubor, který obsahuje možnosti kompilátoru a soubory zdrojového kódu ke kompilaci.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
@response_file  
```  
  
## <a name="arguments"></a>Argumenty  
 `response_file`  
 Soubor, který obsahuje seznam možností kompilátoru nebo souborů zdrojového kódu ke kompilaci.  
  
## <a name="remarks"></a>Poznámky  
 Možnosti kompilátoru a soubory zdrojového kódu budou zpracovány kompilátorem stejně jako v případě, že byly zadány na příkazovém řádku.  
  
 Chcete-li v kompilaci zadat více než jeden soubor odpovědí, zadejte více možností souboru odpovědí. Například:  
  
```console  
@file1.rsp @file2.rsp  
```  
  
 V souboru odpovědí se na jednom řádku může objevit více možností kompilátoru a souborů zdrojového kódu. Na jednom řádku se musí objevit jedna specifikace možnosti kompilátoru (nelze přehoupnout více řádků). Soubory odpovědí mohou mít komentáře, které začínají symbolem # .  
  
 Určení možností kompilátoru ze souboru odpovědí je stejné jako vydávání těchto příkazů na příkazovém řádku. Další informace naleznete [v tématu Vytváření z příkazového řádku.](./how-to-set-environment-variables-for-the-visual-studio-command-line.md)  
  
 Kompilátor zpracuje možnosti příkazu tak, jak jsou zjištěny. Argumenty příkazového řádku proto mohou přepsat dříve uvedené možnosti v souborech odpovědí. Naopak možnosti v souboru odpovědí přepíší možnosti uvedené dříve na příkazovém řádku nebo v jiných souborech odpovědí.  
  
 C# poskytuje soubor csc.rsp, který je umístěn ve stejném adresáři jako soubor csc.exe. Viz [-noconfig](./noconfig-compiler-option.md) pro více informací o csc.rsp.  
  
 Tuto možnost kompilátoru nelze nastavit ve vývojovém prostředí sady Visual Studio, ani ji nelze programově změnit.  
  
## <a name="example"></a>Příklad  
 Následuje několik řádků z ukázkového souboru odpovědí:  
  
```console  
# build the first output file  
-target:exe -out:MyExe.exe source1.cs source2.cs  
```  
  
## <a name="see-also"></a>Viz také

- [Možnosti kompilátoru jazyka C#](./index.md)
