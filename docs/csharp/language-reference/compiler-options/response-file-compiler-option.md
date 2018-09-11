---
title: '@ (Možnosti kompilátoru C#)'
ms.date: 07/20/2015
f1_keywords:
- '@'
helpviewer_keywords:
- response files, specifying for compilation [C#]
- '@ compiler option'
ms.assetid: dda4fa9f-a02c-400f-8b6a-d58834e13d7f
ms.openlocfilehash: f342f26ee8abe29e6c5a1477469c8b7292cd702e
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2018
ms.locfileid: "44259805"
---
# <a name="-c-compiler-options"></a>@ (Možnosti kompilátoru C#)
@ – Možnost umožňují určit soubor obsahující možnosti kompilátoru a soubory zdrojového kódu pro kompilaci.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
@response_file  
```  
  
## <a name="arguments"></a>Arguments  
 `response_file`  
 Soubor se seznamem – možnosti kompilátoru nebo souborů se zdrojovým kódem, chcete-li zkompilovat.  
  
## <a name="remarks"></a>Poznámky  
 Možnosti kompilátoru a soubory zdrojového kódu budou zpracovány kompilátorem tak, jako kdyby kdyby byly zadány v příkazovém řádku.  
  
 Pokud chcete zadat více než jeden soubor odpovědí do kompilace, zadejte více možnosti soubor odpovědi. Příklad:  
  
```  
@file1.rsp @file2.rsp  
```  
  
 V odpovědi na soubor, více možností kompilátoru a soubory zdrojového kódu může zobrazit na jednom řádku. Specifikace jediné kompilátoru možnost se musí nacházet na jednom řádku (nemůžou zahrnovat více řádků). Soubory odpovědí může mít komentáře, které začínají symbolem #.  
  
 Určení možností kompilátoru ze souboru odpovědí je stejně jako vydávání těchto příkazů na příkazovém řádku. Zobrazit [sestavení z příkazového řádku](../../../csharp/language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md) Další informace.  
  
 Kompilátor zpracovává možnosti příkazu v průběhu jejich výskytu. Argumenty příkazového řádku můžete přepsat, proto výše uvedených možností v souborech odpovědí. Možnosti v souboru odpovědí a naopak, přepíše možnosti uvedené dříve v příkazovém řádku nebo v jiné soubory odpovědí.  
  
 C# obsahuje soubor csc.rsp, který je umístěn ve stejném adresáři jako soubor csc.exe. Zobrazit [- noconfig](../../../csharp/language-reference/compiler-options/noconfig-compiler-option.md) Další informace o souboru csc.rsp.  
  
 Tato možnost kompilátoru nelze nastavit ve vývojovém prostředí sady Visual Studio ani ji není možné změnit prostřednictvím kódu programu.  
  
## <a name="example"></a>Příklad  
 Následují po zadání několika řádků z ukázkového souboru odpovědí:  
  
```console  
# build the first output file  
-target:exe -out:MyExe.exe source1.cs source2.cs  
```  
  
## <a name="see-also"></a>Viz také  

- [Možnosti kompilátoru jazyka C#](../../../csharp/language-reference/compiler-options/index.md)
