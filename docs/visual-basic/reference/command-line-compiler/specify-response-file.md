---
title: '@ (Určení souboru odezvy) (Visual Basic)'
ms.date: 03/13/2018
helpviewer_keywords:
- '@ (Specify Response File) compiler option [Visual Basic]'
ms.assetid: a6847eaa-e5f9-4303-9421-45b55484b9ca
ms.openlocfilehash: 6b993a6399eec4e203821109db153aadf246cbac
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61639019"
---
# <a name="-specify-response-file-visual-basic"></a>@ (Určení souboru odezvy) (Visual Basic)
Určuje soubor, který obsahuje možnosti kompilátoru a soubory zdrojového kódu ke kompilaci.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
@response_file  
```  
  
## <a name="arguments"></a>Arguments  
 `response_file`  
 Povinný parametr. Soubor se seznamem – možnosti kompilátoru nebo soubory zdrojového kódu pro kompilaci. Název souboru uzavřete do uvozovek ("") Pokud obsahuje mezery.  
  
## <a name="remarks"></a>Poznámky  
 Kompilátor zpracovává možnosti kompilátoru a soubory zdrojového kódu jakoby kdyby byly zadány v příkazovém řádku zadané v souboru odpovědí.  
  
 Chcete-li zadat více než jeden soubor odpovědí do kompilace, zadejte více možností soubor odpovědí, jako je následující.  
  
```  
@file1.rsp @file2.rsp  
```  
  
 V odpovědi na soubor, více možností kompilátoru a soubory zdrojového kódu může zobrazit na jednom řádku. Specifikace jediné-– možnost kompilátoru se musí nacházet na jednom řádku (nemůžou zahrnovat více řádků). Soubory odpovědí může mít komentáře, které začínají `#` symbol.  
  
 Můžete kombinovat možnosti zadané v příkazovém řádku pomocí volby zadané v jeden nebo více souborů odezvy. Kompilátor zpracovává možnosti příkazu při jejich výskytu. Argumenty příkazového řádku můžete přepsat, proto výše uvedených možností v souborech odpovědí. Možnosti v souboru odpovědí a naopak, přepsat možnosti uvedené dříve v příkazovém řádku nebo v jiné soubory odpovědí.  
  
 Visual Basic poskytuje soubor Vbc.rsp, který je umístěn ve stejném adresáři jako soubor Vbc.exe. Soubor Vbc.rsp je zahrnuté ve výchozím nastavení, pokud `-noconfig` možnost se používá. Další informace najdete v tématu [- noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md).  
  
> [!NOTE]
>  `@` Možnost není k dispozici v rámci vývojového prostředí sady Visual Studio; je k dispozici jenom při kompilaci z příkazového řádku.  
  
## <a name="example"></a>Příklad  
 Následující řádky jsou z ukázkového souboru odpovědí.  
  
```console
# build the first output file  
-target:exe   
-out:MyExe.exe  
source1.vb   
source2.vb  
```  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje způsob použití `@` možnost pomocí souboru odpovědí s názvem `File1.rsp`.  
  
```console
vbc @file1.rsp  
```  
  
## <a name="see-also"></a>Viz také:

- [Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md)
- [-noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md)
- [Příkazové řádky ukázkové kompilace](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
