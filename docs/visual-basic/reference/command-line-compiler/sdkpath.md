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
ms.openlocfilehash: 85aba17b330af1b25b39f462844bc1a4856a448a
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403106"
---
# <a name="-sdkpath"></a>-sdkpath
Určuje umístění knihovny mscorlib. dll a Microsoft. VisualBasic. dll.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-sdkpath:path  
```  
  
## <a name="arguments"></a>Argumenty  
 `path`  
 Adresář obsahující verze mscorlib. dll a Microsoft. VisualBasic. dll, které mají být použity pro kompilaci. Tato cesta není ověřena, dokud není načtena. Uzavřete název adresáře v uvozovkách (""), pokud obsahuje mezeru.  
  
## <a name="remarks"></a>Poznámky  
 Tato možnost instruuje kompilátor Visual Basic, aby načetl soubory mscorlib. dll a Microsoft. VisualBasic. dll z jiného než výchozího umístění. `-sdkpath`Možnost byla navržena pro použití s parametrem [-netcf –](netcf.md). Prostředí .NET Compact Framework používá různé verze těchto knihoven podpory, aby nedocházelo k použití typů a funkcí jazyka, které se na zařízeních nenašly.  
  
> [!NOTE]
> Tato `-sdkpath` možnost není k dispozici ve vývojovém prostředí sady Visual Studio. je k dispozici pouze při kompilaci z příkazového řádku. `-sdkpath`Možnost je nastavena při načtení projektu Visual Basic zařízení.  
  
 Můžete určit, že má být kompilátor zkompilován bez odkazu na knihovnu modulu runtime Visual Basic pomocí `-vbruntime` Možnosti kompilátoru. Další informace najdete v tématu [– vbruntime –](vbruntime.md).  
  
## <a name="example"></a>Příklad  
 Následující kód `Myfile.vb` se zkompiluje s prostředí .NET Compact Framework pomocí verzí knihovny mscorlib. dll a Microsoft. VisualBasic. dll, která se nachází ve výchozím instalačním adresáři prostředí .NET Compact Framework na jednotce C. Obvykle byste použili nejnovější verzi prostředí .NET Compact Framework.  
  
```console
vbc -netcf -sdkpath:"c:\Program Files\Microsoft Visual Studio .NET 2003\CompactFrameworkSDK\v1.0.5000\Windows CE " myfile.vb  
```  
  
## <a name="see-also"></a>Viz také

- [Visual Basic Kompilátor příkazového řádku](index.md)
- [Příkazové řádky ukázkové kompilace](sample-compilation-command-lines.md)
- [-netcf](netcf.md)
- [-vbruntime](vbruntime.md)
