---
title: -linkresource (Visual Basic)
ms.date: 03/10/2018
helpviewer_keywords:
- /linkresource compiler option [Visual Basic]
- -linkresource compiler option [Visual Basic]
- linkresource compiler option [Visual Basic]
- /linkres compiler option [Visual Basic]
- linkres compiler option [Visual Basic]
- -linkres compiler option [Visual Basic]
ms.assetid: cf4dcad8-17b7-404c-9184-29358aa05b15
ms.openlocfilehash: 4f4b3db768b5466f8912b66a0a4709d0f773c1f3
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43425515"
---
# <a name="-linkresource-visual-basic"></a>-linkresource (Visual Basic)
Vytvoří odkaz na spravovaný prostředek.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
-linkresource:filename[,identifier[,public|private]]  
' -or-  
-linkres:filename[,identifier[,public|private]]  
```  
  
## <a name="arguments"></a>Arguments  
 `filename`  
 Požadováno. Soubor prostředků odkaz na sestavení. Pokud název souboru obsahuje mezery, uzavřete název do uvozovek ("").  
  
 `identifier`  
 Volitelné. Logický název prostředku. Název, který se používá k načtení prostředku. Výchozí hodnota je název souboru. Volitelně můžete určit, zda soubor je třeba veřejných nebo privátních v manifestu sestavení: `-linkres:filename.res,myname.res,public`. Ve výchozím nastavení `filename` veřejnou v sestavení.  
  
## <a name="remarks"></a>Poznámky  
 `-linkresource` Možnost nelze vložit soubor prostředků do výstupního souboru; použijte `-resource` možnost to udělat.  
  
 `-linkresource` Možnost vyžaduje jednu z `-target` možností jiných než `-target:module`.  
  
 Pokud `filename` je [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] soubor prostředků vytvořený, například podle [Resgen.exe (Generátor zdrojových souborů)](https://msdn.microsoft.com/library/8ef159de-b660-4bec-9213-c3fbc4d1c6f4) nebo ve vývojovém prostředí, můžete přistupovat pomocí členů z <xref:System.Resources> oboru názvů. (Další informace najdete v tématu <xref:System.Resources.ResourceManager>.) Pro přístup k dalším prostředkům v době běhu, použijte metody, které začínají `GetManifestResource` v <xref:System.Reflection.Assembly> třídy.  
  
 Název souboru může být libovolný formát souboru. Můžete například vytvořit nativní knihovna DLL stane součástí sestavení, takže může být nainstalováno do globální mezipaměti sestavení a získat přístup ze spravovaného kódu v sestavení.  
  
 Krátký tvar `-linkresource` je `-linkres`.  
  
> [!NOTE]
>  `-linkresource` Možnost není k dispozici z vývojového prostředí sady Visual Studio; je k dispozici, pouze pokud kompilujete z příkazového řádku.  
  
## <a name="example"></a>Příklad  
 Následující kód zkompiluje `in.vb` a odkazy na soubor prostředků `rf.resource`.  
  
```console  
vbc -linkresource:rf.resource in.vb  
```  
  
## <a name="see-also"></a>Viz také  
 [Kompilátor příkazového řádku jazyka Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)  
 [-target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)  
 [-prostředku (Visual Basic)](../../../visual-basic/reference/command-line-compiler/resource.md)  
 [Příkazové řádky ukázkové kompilace](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
