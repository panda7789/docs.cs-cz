---
title: -sdkpath
ms.date: 07/20/2015
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
ms.openlocfilehash: 162c7d58350c381ec667e8a4cd11c03e83fcdf44
ms.sourcegitcommit: 412bbc2e43c3b6ca25b358cdf394be97336f0c24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/25/2018
ms.locfileid: "42925682"
---
# <a name="-sdkpath"></a>-sdkpath
Určuje umístění knihovny mscorlib.dll a Microsoft.VisualBasic.dll.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
-sdkpath:path  
```  
  
## <a name="arguments"></a>Arguments  
 `path`  
 Adresáře, který obsahuje verze knihovny mscorlib.dll a Microsoft.VisualBasic.dll používat pro kompilaci. Tato cesta není ověřená, dokud jej načíst. Název adresáře uzavřete do uvozovek ("") Pokud obsahuje mezery.  
  
## <a name="remarks"></a>Poznámky  
 Tato možnost informuje kompilátor jazyka Visual Basic se načíst knihovnu mscorlib.dll a Microsoft.VisualBasic.dll soubory z jiné než výchozí umístění. `-sdkpath` Možnost byla navržena pro použití s [- netcf](../../../visual-basic/reference/command-line-compiler/netcf.md). [!INCLUDE[Compact](~/includes/compact-md.md)] Používá různé verze těchto podporu knihoven a vyhněte se použití typů a jazykových funkcí na zařízeních, nebyla nalezena.  
  
> [!NOTE]
>  `-sdkpath` Možnost není k dispozici v rámci vývojového prostředí sady Visual Studio; je k dispozici jenom při kompilaci z příkazového řádku. `-sdkpath` Nastavena možnost při načtení projektu Visual Basic zařízení.  
  
 Můžete určit, že kompilátor by měl kompilovat bez odkazu na knihovnu Runtime jazyka Visual Basic pomocí `-vbruntime` – možnost kompilátoru. Další informace najdete v tématu [- vbruntime](../../../visual-basic/reference/command-line-compiler/vbruntime.md).  
  
## <a name="example"></a>Příklad  
 Následující kód zkompiluje `Myfile.vb` s [!INCLUDE[Compact](~/includes/compact-md.md)], použití verze knihovny Mscorlib.dll a Microsoft.VisualBasic.dll součástí výchozí instalační adresář [!INCLUDE[Compact](~/includes/compact-md.md)] na jednotce C:. Obvykle byste použili nejnovější verzi [!INCLUDE[Compact](~/includes/compact-md.md)].  
  
```console
vbc -netcf -sdkpath:"c:\Program Files\Microsoft Visual Studio .NET 2003\CompactFrameworkSDK\v1.0.5000\Windows CE " myfile.vb  
```  
  
## <a name="see-also"></a>Viz také  
 [Kompilátor příkazového řádku jazyka Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)  
 [Příkazové řádky ukázkové kompilace](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [-netcf](../../../visual-basic/reference/command-line-compiler/netcf.md)  
 [-vbruntime](../../../visual-basic/reference/command-line-compiler/vbruntime.md)
