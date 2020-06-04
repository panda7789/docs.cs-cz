---
title: -win32icon
ms.date: 03/13/2018
helpviewer_keywords:
- win32icon compiler option [Visual Basic]
- -win32icon compiler option [Visual Basic]
- /win32icon compiler option [Visual Basic]
ms.assetid: aecaab01-9353-46c5-941c-6edabd4eff92
ms.openlocfilehash: 52ef0b991554c800dba4320b0c64c81ddd1b0ff4
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84414282"
---
# <a name="-win32icon"></a>-win32icon
Vloží soubor. ico do výstupního souboru. Tento soubor. ico představuje výstupní soubor v **Průzkumníkovi souborů**.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-win32icon:filename  
```  
  
## <a name="arguments"></a>Argumenty  
  
|Pojem|Definice|  
|---|---|  
|`filename`|Soubor. ico, který se má přidat do výstupního souboru. Uzavřete název souboru do uvozovek (""), pokud obsahuje mezeru.|  
  
## <a name="remarks"></a>Poznámky  
 Soubor. ico můžete vytvořit pomocí kompilátoru Microsoft Windows Resource Compiler (RC). Kompilátor prostředků je vyvolán při kompilování Visual C++ programu; soubor. ico je vytvořen ze souboru. rc. `-win32icon`Možnosti a `-win32resource` se vzájemně vylučují.  
  
 Viz [-linkresource – (Visual Basic)](linkresource.md) pro odkazování na soubor prostředků .NET Framework nebo [prostředku (Visual Basic)](resource.md) pro připojení souboru prostředků .NET Framework. Viz [– Win32Resource](win32resource.md) pro import souboru. res.  
  
|Nastavení-win32icon v integrovaném vývojovém prostředí sady Visual Studio|  
|---|  
|1. v **Průzkumník řešení**mít vybraný projekt. V nabídce **projekt** klikněte na příkaz **vlastnosti**. <br />2. klikněte na kartu **aplikace** .<br />3. upravte hodnotu v poli s **ikonami** .|  
  
## <a name="example"></a>Příklad  
 Následující kód zkompiluje `In.vb` a připojí soubor. ico, `Rf.ico` .  
  
```console
vbc -win32icon:rf.ico in.vb  
```  
  
## <a name="see-also"></a>Viz také

- [Visual Basic Kompilátor příkazového řádku](index.md)
- [Příkazové řádky ukázkové kompilace](sample-compilation-command-lines.md)
