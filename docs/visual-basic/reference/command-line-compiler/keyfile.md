---
title: /keyfile
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- /keyfile compiler option [Visual Basic]
- keyfile compiler option [Visual Basic]
- -keyfile compiler option [Visual Basic]
ms.assetid: ffa82a4b-517a-4c6c-9889-5bae7b534bb8
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: e0be7d230f16750395aaceb3c94539546716b8fd
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="keyfile"></a>/keyfile
Určuje soubor, který obsahuje klíč nebo pár klíčů umožnit sestavení silným názvem.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/keyfile:file  
```  
  
## <a name="arguments"></a>Arguments  
 `file`  
 Požadováno. Soubor, který obsahuje klíč. Pokud název souboru obsahuje mezery, uzavřete název v uvozovkách ("").  
  
## <a name="remarks"></a>Poznámky  
 Kompilátor vloží veřejný klíč do manifestu a následně podepíše konečné sestavení s privátním klíčem. Chcete-li vygenerovat soubor klíče, zadejte `sn -k file` na příkazovém řádku. Další informace najdete v tématu [Sn.exe (nástroj silným názvem)][Sn.exe (nástroj silným názvem)](../../../framework/tools/sn-exe-strong-name-tool.md)).  
  
 Pokud je kompilovat s `/target:module`, název souboru klíče je udržován v modulu a součástí sestavení, které se vytvoří při kompilaci sestavení s [/addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md).  
  
 Vaše informace šifrování můžete předat také kompilátoru s [/keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md). Použití [/delaysign](../../../visual-basic/reference/command-line-compiler/delaysign.md) Pokud chcete, aby částečně podepsané sestavení.  
  
 Tuto možnost můžete také určit jako vlastní atribut (<xref:System.Reflection.AssemblyKeyFileAttribute>) ve zdrojovém kódu pro libovolný modul převodní jazyk Microsoft.  
  
 V případě obě `/keyfile` a [/keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md) jsou zadány (pomocí parametru příkazového řádku nebo pomocí vlastního atributu) ve stejné kompilaci kompilátor poprvé pokusí kontejneru klíčů. Pokud tato operace úspěšná, je podepsaný sestavení s informacemi v kontejneru klíčů. Pokud kompilátor nenajde kontejner klíčů, se pokusí o zadaný soubor s `/keyfile`. Pokud to úspěšné, sestavení je podepsaná pomocí informací v souboru klíče a informace o klíči je nainstalován v kontejneru klíčů (podobně jako `sn -i`) tak, aby na další kompilace kontejner klíče budou platné.  
  
 Všimněte si, že soubor klíče může obsahovat pouze veřejný klíč.  
  
 V tématu [vytvoření a použití sestavení](../../../framework/app-domains/create-and-use-strong-named-assemblies.md) Další informace o podepisování sestavení.  
  
> [!NOTE]
>  `/keyfile` Možnost není k dispozici v rámci [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] vývojového prostředí; je k dispozici pouze při kompilaci z příkazového řádku.  
  
## <a name="example"></a>Příklad  
 Následující kód zkompiluje zdrojový soubor `Input.vb` a určuje soubor klíče.  
  
```  
vbc /keyfile:myfile.sn input.vb  
```  
  
## <a name="see-also"></a>Viz také  
 [Sestavení a globální mezipaměť sestavení (GAC)](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)  
 [Visual Basic – kompilátor příkazového řádku](../../../visual-basic/reference/command-line-compiler/index.md)  
 [/ Reference (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md)  
 [Příkazové řádky ukázkové kompilace](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
