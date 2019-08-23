---
title: -win32resource
ms.date: 03/13/2018
f1_keywords:
- -win32resource
- win32resource
helpviewer_keywords:
- /win32resource compiler option [Visual Basic]
- -win32resource compiler option [Visual Basic]
- win32resource compiler option [Visual Basic]
ms.assetid: e226946d-19ce-4cc9-91f5-aed24f77aa2b
ms.openlocfilehash: 382dcc6571aa06ecdfc32bf43080c4b7a36eb1f0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69961293"
---
# <a name="-win32resource"></a>-win32resource
Vloží soubor prostředků Win32 do výstupního souboru.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
-win32resource:filename  
```  
  
## <a name="arguments"></a>Arguments  
 `filename`  
 Název souboru prostředků, který se má přidat do výstupního souboru. Uzavřete název souboru do uvozovek (""), pokud obsahuje mezeru.  
  
## <a name="remarks"></a>Poznámky  
 Soubor prostředků Win32 můžete vytvořit pomocí kompilátoru Microsoft Windows Resource Compiler (RC).  
  
 Prostředek Win32 může obsahovat informace o verzi nebo bitmapě (ikona), které pomáhají identifikovat vaši aplikaci v **Průzkumníkovi souborů**. Pokud nezadáte `-win32resource`, kompilátor vygeneruje informace o verzi na základě verze sestavení. Možnosti `-win32resource` a`-win32icon` se vzájemně vylučují.  
  
 Viz [-linkresource – (Visual Basic)](../../../visual-basic/reference/command-line-compiler/linkresource.md) pro odkazování na soubor prostředků .NET Framework nebo [prostředku (Visual Basic)](../../../visual-basic/reference/command-line-compiler/resource.md) pro připojení souboru prostředků .NET Framework.  
  
> [!NOTE]
> Tato `-win32resource` možnost není k dispozici ve vývojovém prostředí sady Visual Studio. je k dispozici pouze při kompilaci z příkazového řádku.  
  
## <a name="example"></a>Příklad  
 Následující kód zkompiluje `In.vb` a připojí `Rf.res`soubor prostředků Win32:  
  
```console  
vbc -win32resource:rf.res in.vb  
```  
  
## <a name="see-also"></a>Viz také:

- [Visual Basic Kompilátor příkazového řádku](../../../visual-basic/reference/command-line-compiler/index.md)
- [Příkazové řádky ukázkové kompilace](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
