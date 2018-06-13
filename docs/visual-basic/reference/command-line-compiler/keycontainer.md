---
title: -keycontainer
ms.date: 03/10/2018
helpviewer_keywords:
- -keycontainer compiler option [Visual Basic]
- keycontainer compiler option [Visual Basic]
- /keycontainer compiler option [Visual Basic]
ms.assetid: 6a9bc861-1752-4db1-9f64-b5252f0482cc
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d682533f96b5fb56430a0826d37a9794dc8c5d8f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33655307"
---
# <a name="-keycontainer"></a>-keycontainer
Určuje název kontejneru klíčů pro pár klíčů umožnit sestavení silným názvem.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
-keycontainer:container  
```  
  
## <a name="arguments"></a>Arguments  
  
|Termín|Definice|  
|---|---|  
|`container`|Požadováno. Soubor kontejneru, který obsahuje klíč. Uzavřete název souboru v uvozovkách ("") Pokud název obsahuje mezeru.|  
  
## <a name="remarks"></a>Poznámky  
 Kompilátor vytvoří komponentu lze sdílet vložením veřejný klíč do manifestu a podepíše konečné sestavení s privátním klíčem. Chcete-li vygenerovat soubor klíče, zadejte `sn -k``file` na příkazovém řádku. `-i` Možnost nainstaluje pár klíčů do kontejneru. Další informace najdete v tématu [Sn.exe (nástroj silným názvem)][Sn.exe (nástroj silným názvem)](../../../framework/tools/sn-exe-strong-name-tool.md)).  
  
 Pokud je kompilovat s `-target:module`, název souboru klíče je udržován v modulu a součástí sestavení, které se vytvoří při kompilaci sestavení s [- addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md).  
  
 Tuto možnost můžete také určit jako vlastní atribut (<xref:System.Reflection.AssemblyKeyNameAttribute>) ve zdrojovém kódu pro libovolný modul (MSIL intermediate language) společnosti Microsoft.  
  
 Vaše informace šifrování můžete předat také kompilátoru s [- keyfile](../../../visual-basic/reference/command-line-compiler/keyfile.md). Použití [- delaysign](../../../visual-basic/reference/command-line-compiler/delaysign.md) Pokud chcete, aby částečně podepsané sestavení.  
  
 V tématu [vytvoření a použití sestavení](../../../framework/app-domains/create-and-use-strong-named-assemblies.md) Další informace o podepisování sestavení.  
  
> [!NOTE]
>  `-keycontainer` Možnost není k dispozici ve vývojovém prostředí sady Visual Studio, je k dispozici pouze při kompilaci z příkazového řádku.  
  
## <a name="example"></a>Příklad  
 Následující kód zkompiluje zdrojový soubor `Input.vb` a určuje kontejneru klíčů.  
  
```  
vbc -keycontainer:key1 input.vb  
```  
  
## <a name="see-also"></a>Viz také  
 [Sestavení a globální mezipaměť sestavení (GAC)](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)  
 [Visual Basic – kompilátor příkazového řádku](../../../visual-basic/reference/command-line-compiler/index.md)  
 [-keyfile](../../../visual-basic/reference/command-line-compiler/keyfile.md)  
 [Příkazové řádky ukázkové kompilace](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
