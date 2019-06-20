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
ms.openlocfilehash: 91f64756b2fbf14dc96550420cd936973e6bec87
ms.sourcegitcommit: 4c41ec195caf03d98b7900007c3c8e24eba20d34
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/20/2019
ms.locfileid: "67268293"
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
 Tato možnost informuje kompilátor jazyka Visual Basic se načíst knihovnu mscorlib.dll a Microsoft.VisualBasic.dll soubory z jiné než výchozí umístění. `-sdkpath` Možnost byla navržena pro použití s [- netcf](../../../visual-basic/reference/command-line-compiler/netcf.md). Různé verze rozhraní .NET Compact Framework používá tyto podpůrné knihovny vyhnout se použití typů a jazykových funkcí na zařízeních, nebyla nalezena.  
  
> [!NOTE]
>  `-sdkpath` Možnost není k dispozici v rámci vývojového prostředí sady Visual Studio; je k dispozici jenom při kompilaci z příkazového řádku. `-sdkpath` Nastavena možnost při načtení projektu Visual Basic zařízení.  
  
 Můžete určit, že kompilátor by měl kompilovat bez odkazu na knihovnu Runtime jazyka Visual Basic pomocí `-vbruntime` – možnost kompilátoru. Další informace najdete v tématu [- vbruntime](../../../visual-basic/reference/command-line-compiler/vbruntime.md).  
  
## <a name="example"></a>Příklad  
 Následující kód zkompiluje `Myfile.vb` s rozhraním .NET Compact Framework, použití verze knihovny Mscorlib.dll a Microsoft.VisualBasic.dll najde v adresáři výchozí instalace rozhraní .NET Compact Framework na jednotce C:. Obvykle byste použili nejnovější verzi rozhraní .NET Compact Framework.  
  
```console
vbc -netcf -sdkpath:"c:\Program Files\Microsoft Visual Studio .NET 2003\CompactFrameworkSDK\v1.0.5000\Windows CE " myfile.vb  
```  
  
## <a name="see-also"></a>Viz také:

- [Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md)
- [Příkazové řádky ukázkové kompilace](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [-netcf](../../../visual-basic/reference/command-line-compiler/netcf.md)
- [-vbruntime](../../../visual-basic/reference/command-line-compiler/vbruntime.md)
