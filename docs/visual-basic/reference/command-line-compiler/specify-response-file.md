---
title: '@ (Určení souboru odezvy) (Visual Basic)'
ms.date: 03/13/2018
helpviewer_keywords:
- '@ (Specify Response File) compiler option [Visual Basic]'
ms.assetid: a6847eaa-e5f9-4303-9421-45b55484b9ca
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4ad4201dcc094364899984e13c85f2f43a6467ff
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="-specify-response-file-visual-basic"></a>@ (Určení souboru odezvy) (Visual Basic)
Určuje soubor, který obsahuje – možnosti kompilátoru a soubory zdrojového kódu ke kompilaci.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
@response_file  
```  
  
## <a name="arguments"></a>Arguments  
 `response_file`  
 Požadováno. Soubor se seznamem – možnosti kompilátoru nebo soubory zdrojového kódu ke kompilaci. Uzavřete název souboru v uvozovkách ("") Pokud obsahuje mezeru.  
  
## <a name="remarks"></a>Poznámky  
 Kompilátor zpracovává – možnosti kompilátoru a soubory zdrojového kódu zadané v souboru odpovědí, jako kdyby kdyby byly zadány na příkazovém řádku.  
  
 Zadat více než jeden soubor odpovědi v kompilaci, zadejte více možnosti soubor odpovědí, podobně jako tento.  
  
```  
@file1.rsp @file2.rsp  
```  
  
 V odpovědi můžete soubor, více – možnosti kompilátoru a soubory zdrojového kódu zobrazí na jednom řádku. Specifikace jednoho-– možnost kompilátoru musí být uvedena na jednom řádku (nemůže zahrnovat více řádků). Soubory odezvy může mít komentáře, které začínají `#` symbol.  
  
 Zkombinováním možností na příkazovém řádku s možností v jeden nebo více souborů odpovědi. Kompilátor zpracovává možností příkazového řádku při jejich výskytu. Proto argumenty příkazového řádku můžete přepsat výše uvedených možností v souborech odpovědi. Naopak možnosti v souboru odpovědí přepsat možnosti uvedené dříve v příkazovém řádku nebo v jiné soubory odpovědi.  
  
 Visual Basic poskytuje Vbc.rsp souboru, který se nachází ve stejném adresáři jako soubor Vbc.exe. Soubor Vbc.rsp je zahrnutá ve výchozím nastavení, pokud `-noconfig` možnost se používá. Další informace najdete v tématu [- noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md).  
  
> [!NOTE]
>  `@` Možnost není k dispozici ve vývojovém prostředí sady Visual Studio, je k dispozici pouze při kompilaci z příkazového řádku.  
  
## <a name="example"></a>Příklad  
 Následující řádky představují z ukázkového souboru odpovědí.  
  
```console
# build the first output file  
-target:exe   
-out:MyExe.exe  
source1.vb   
source2.vb  
```  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak používat `@` možnost pomocí souboru odpovědí s názvem `File1.rsp`.  
  
```console
vbc @file1.rsp  
```  
  
## <a name="see-also"></a>Viz také  
 [Visual Basic – kompilátor příkazového řádku](../../../visual-basic/reference/command-line-compiler/index.md)  
 [-noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md)  
 [Příkazové řádky ukázkové kompilace](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
