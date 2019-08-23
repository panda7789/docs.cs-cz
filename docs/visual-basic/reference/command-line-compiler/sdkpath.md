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
ms.openlocfilehash: 25368d23c398fb3674d5c2d75d4997f917a1c3d6
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69937357"
---
# <a name="-sdkpath"></a>-sdkpath
Určuje umístění knihovny mscorlib. dll a Microsoft. VisualBasic. dll.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
-sdkpath:path  
```  
  
## <a name="arguments"></a>Arguments  
 `path`  
 Adresář obsahující verze mscorlib. dll a Microsoft. VisualBasic. dll, které mají být použity pro kompilaci. Tato cesta není ověřena, dokud není načtena. Uzavřete název adresáře v uvozovkách (""), pokud obsahuje mezeru.  
  
## <a name="remarks"></a>Poznámky  
 Tato možnost instruuje kompilátor Visual Basic, aby načetl soubory mscorlib. dll a Microsoft. VisualBasic. dll z jiného než výchozího umístění. Možnost byla navržena pro použití s parametrem [-netcf –.](../../../visual-basic/reference/command-line-compiler/netcf.md) `-sdkpath` Prostředí .NET Compact Framework používá různé verze těchto knihoven podpory, aby nedocházelo k použití typů a funkcí jazyka, které se na zařízeních nenašly.  
  
> [!NOTE]
> Tato `-sdkpath` možnost není k dispozici ve vývojovém prostředí sady Visual Studio. je k dispozici pouze při kompilaci z příkazového řádku. `-sdkpath` Možnost je nastavena při načtení projektu Visual Basic zařízení.  
  
 Můžete určit, že má být kompilátor zkompilován bez odkazu na knihovnu modulu runtime Visual Basic pomocí `-vbruntime` možnosti kompilátoru. Další informace najdete v tématu [– vbruntime –](../../../visual-basic/reference/command-line-compiler/vbruntime.md).  
  
## <a name="example"></a>Příklad  
 Následující kód `Myfile.vb` se zkompiluje s prostředí .NET Compact Framework pomocí verzí knihovny mscorlib. dll a Microsoft. VisualBasic. dll, která se nachází ve výchozím instalačním adresáři prostředí .NET Compact Framework na jednotce C. Obvykle byste použili nejnovější verzi prostředí .NET Compact Framework.  
  
```console
vbc -netcf -sdkpath:"c:\Program Files\Microsoft Visual Studio .NET 2003\CompactFrameworkSDK\v1.0.5000\Windows CE " myfile.vb  
```  
  
## <a name="see-also"></a>Viz také:

- [Visual Basic Kompilátor příkazového řádku](../../../visual-basic/reference/command-line-compiler/index.md)
- [Příkazové řádky ukázkové kompilace](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [-netcf](../../../visual-basic/reference/command-line-compiler/netcf.md)
- [-vbruntime](../../../visual-basic/reference/command-line-compiler/vbruntime.md)
