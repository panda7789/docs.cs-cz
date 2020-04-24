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
ms.openlocfilehash: cee06adec89aac4b3e3f170df3bf932e466f3070
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004960"
---
# <a name="-win32resource"></a>-win32resource
Vloží soubor prostředků Win32 do výstupního souboru.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-win32resource:filename  
```  
  
## <a name="arguments"></a>Argumenty  
 `filename`  
 Název souboru prostředků, který se má přidat do výstupního souboru. Uzavřete název souboru do uvozovek (""), pokud obsahuje mezeru.  
  
## <a name="remarks"></a>Poznámky  
 Soubor prostředků Win32 můžete vytvořit pomocí kompilátoru Microsoft Windows Resource Compiler (RC).  
  
 Prostředek Win32 může obsahovat informace o verzi nebo bitmapě (ikona), které pomáhají identifikovat vaši aplikaci v **Průzkumníkovi souborů**. Pokud nezadáte `-win32resource`, kompilátor vygeneruje informace o verzi na základě verze sestavení. Možnosti `-win32resource` a `-win32icon` se vzájemně vylučují.  
  
 Viz [-linkresource – (Visual Basic)](../../../visual-basic/reference/command-line-compiler/linkresource.md) pro odkazování na soubor prostředků .NET Framework nebo [prostředku (Visual Basic)](../../../visual-basic/reference/command-line-compiler/resource.md) pro připojení souboru prostředků .NET Framework.  
  
> [!NOTE]
> Tato `-win32resource` možnost není k dispozici ve vývojovém prostředí sady Visual Studio; je k dispozici pouze při kompilaci z příkazového řádku.  
  
## <a name="example"></a>Příklad  
 Následující kód zkompiluje `In.vb` a připojí soubor prostředků Win32 `Rf.res`:  
  
```console  
vbc -win32resource:rf.res in.vb  
```  
  
## <a name="see-also"></a>Viz také

- [Visual Basic Kompilátor příkazového řádku](../../../visual-basic/reference/command-line-compiler/index.md)
- [Příkazové řádky ukázkové kompilace](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
