---
title: "@ (Možnosti kompilátoru C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: '@'
helpviewer_keywords:
- response files, specifying for compilation [C#]
- '@ compiler option'
ms.assetid: dda4fa9f-a02c-400f-8b6a-d58834e13d7f
caps.latest.revision: "9"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: fbb95e0619857f38260ae74366ba4bb860779530
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="-c-compiler-options"></a>@ (Možnosti kompilátoru C#)
@ Možnost umožňuje zadat soubor, který obsahuje – možnosti kompilátoru a soubory zdrojového kódu ke kompilaci.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
@response_file  
```  
  
## <a name="arguments"></a>Arguments  
 `response_file`  
 Soubor se seznamem – možnosti kompilátoru nebo soubory zdrojového kódu ke kompilaci.  
  
## <a name="remarks"></a>Poznámky  
 Možnosti kompilátoru a soubory zdrojového kódu budou zpracovány kompilátorem stejně, jako kdyby kdyby byly zadány na příkazovém řádku.  
  
 Chcete-li zadat více než jeden soubor odpovědi v kompilaci, zadejte možnost souboru odpovědí. Příklad:  
  
```  
@file1.rsp @file2.rsp  
```  
  
 V odpovědi můžete soubor, více – možnosti kompilátoru a soubory zdrojového kódu zobrazí na jednom řádku. Specifikaci – možnost kompilátoru jeden musí být uvedena na jednom řádku (nemůže zahrnovat více řádků). Soubory odezvy může mít komentáře, které začínají symbolem #.  
  
 Určení možností kompilátoru ze souboru odpovědí je stejně jako vydávání těchto příkazů na příkazovém řádku. V tématu [sestavení z příkazového řádku](../../../csharp/language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md) Další informace.  
  
 Kompilátor zpracovává příkazy možností, jak se vyskytují. Argumenty příkazového řádku. proto můžete přepsat výše uvedených možností v souborech odpovědi. Možnosti v souboru odpovědí naopak přepíše možnosti uvedené dříve v příkazovém řádku nebo v jiné soubory odpovědi.  
  
 C# poskytuje souboru csc.rsp, který se nachází ve stejném adresáři jako soubor csc.exe. V tématu [- noconfig](../../../csharp/language-reference/compiler-options/noconfig-compiler-option.md) Další informace o souboru csc.rsp.  
  
 Tato možnost kompilátoru nelze nastavit ve vývojovém prostředí sady Visual Studio, ani ji není možné změnit prostřednictvím kódu programu.  
  
## <a name="example"></a>Příklad  
 Následuje několik řádků z ukázkového souboru odpovědí:  
  
```console  
# build the first output file  
-target:exe -out:MyExe.exe source1.cs source2.cs  
```  
  
## <a name="see-also"></a>Viz také  
 [Možnosti kompilátoru jazyka C#](../../../csharp/language-reference/compiler-options/index.md)
