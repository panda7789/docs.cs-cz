---
title: -sdkpath
ms.date: 07/20/2015
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- sdkpath
- -sdkpath
helpviewer_keywords:
- -sdkpath compiler option [Visual Basic]
- /sdkpath compiler option [Visual Basic]
- sdkpath compiler option [Visual Basic]
ms.assetid: fec8a3f1-b791-4a37-8af7-344859f8212d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 53362c2eb5517d9230ea88975745315d6db7f1ba
ms.sourcegitcommit: 498799639937c89de777361aab74261efe7b79ea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/22/2018
---
# <a name="-sdkpath"></a>-sdkpath
Určuje umístění mscorlib.dll a souboru Microsoft.VisualBasic.dll.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
-sdkpath:path  
```  
  
## <a name="arguments"></a>Arguments  
 `path`  
 Adresář obsahující verze mscorlib.dll a souboru Microsoft.VisualBasic.dll sloužící ke kompilaci. Tato cesta se neověří, dokud je načten. Uveďte název adresáře v uvozovkách ("") Pokud obsahuje mezeru.  
  
## <a name="remarks"></a>Poznámky  
 Tato možnost umožňuje [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] kompilátoru načíst mscorlib.dll a souboru Microsoft.VisualBasic.dll soubory z jiné než výchozí umístění. `-sdkpath` Možnost byla určena pro použití s [- netcf](../../../visual-basic/reference/command-line-compiler/netcf.md). [!INCLUDE[Compact](~/includes/compact-md.md)] Používá jiné verze těchto podporu knihovny nepoužívejte typy a funkce jazyka nebyla nalezena na zařízení.  
  
> [!NOTE]
>  `-sdkpath` Možnost není k dispozici ve vývojovém prostředí sady Visual Studio, je k dispozici pouze při kompilaci z příkazového řádku. `-sdkpath` Když je možnost nastavena [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] načtení projektu zařízení.  
  
 Můžete určit, že by měl kompilátor kompilovat bez odkazu na Visual Basic Runtime Library pomocí `-vbruntime` – možnost kompilátoru. Další informace najdete v tématu [- vbruntime](../../../visual-basic/reference/command-line-compiler/vbruntime.md).  
  
## <a name="example"></a>Příklad  
 Následující kód zkompiluje `Myfile.vb` s [!INCLUDE[Compact](~/includes/compact-md.md)], pomocí verze Mscorlib.dll a souboru Microsoft.VisualBasic.dll najde v adresáři výchozí instalace z [!INCLUDE[Compact](~/includes/compact-md.md)] na jednotce C. Obvykle byste použili nejnovější verzi [!INCLUDE[Compact](~/includes/compact-md.md)].  
  
```console
vbc -netcf -sdkpath:"c:\Program Files\Microsoft Visual Studio .NET 2003\CompactFrameworkSDK\v1.0.5000\Windows CE " myfile.vb  
```  
  
## <a name="see-also"></a>Viz také  
 [Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md)  
 [Příkazové řádky ukázkové kompilace](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [-netcf](../../../visual-basic/reference/command-line-compiler/netcf.md)  
 [-vbruntime](../../../visual-basic/reference/command-line-compiler/vbruntime.md)
