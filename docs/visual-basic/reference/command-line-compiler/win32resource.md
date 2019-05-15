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
ms.openlocfilehash: d8f9c9aac87fd71b61a5413386582ae660efd903
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/14/2019
ms.locfileid: "65593070"
---
# <a name="-win32resource"></a>-win32resource
Vloží soubor prostředku Win32 do výstupního souboru.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
-win32resource:filename  
```  
  
## <a name="arguments"></a>Arguments  
 `filename`  
 Název souboru prostředků pro přidání do výstupního souboru. Název souboru uzavřete do uvozovek ("") Pokud obsahuje mezery.  
  
## <a name="remarks"></a>Poznámky  
 Soubor prostředků Win32 lze vytvořit s Microsoft Windows Resource kompilátor (RC).  
  
 Prostředek systému Win32 mohou obsahovat verzi nebo rastrový obrázek (ikona) informace, které pomáhá identifikovat aplikaci v **Průzkumníka souborů**. Pokud nezadáte `-win32resource`, kompilátor generuje informace o verzi na základě verze sestavení. `-win32resource` a `-win32icon` možnosti se vzájemně vylučují.  
  
 Zobrazit [- linkresource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/linkresource.md) k odkázání na soubor prostředků rozhraní .NET Framework nebo [-prostředku (Visual Basic)](../../../visual-basic/reference/command-line-compiler/resource.md) připojit soubor prostředků rozhraní .NET Framework.  
  
> [!NOTE]
>  `-win32resource` Možnost není k dispozici v rámci vývojového prostředí sady Visual Studio; je k dispozici jenom při kompilaci z příkazového řádku.  
  
## <a name="example"></a>Příklad  
 Následující kód zkompiluje `In.vb` a připojí soubor prostředků Win32, `Rf.res`:  
  
```console  
vbc -win32resource:rf.res in.vb  
```  
  
## <a name="see-also"></a>Viz také:

- [Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md)
- [Příkazové řádky ukázkové kompilace](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
