---
title: -prostředku (Visual Basic)
ms.date: 03/13/2018
helpviewer_keywords:
- /resource compiler option [Visual Basic]
- -resource compiler option [Visual Basic]
- /res compiler option [Visual Basic]
- res compiler option [Visual Basic]
- -res compiler option [Visual Basic]
- resource compiler option [Visual Basic]
ms.assetid: eee2f227-91f2-4f2b-a9d6-1c51c5320858
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ab5593455546e65bdd760d9e60532031dc1f12a9
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/26/2018
ms.locfileid: "42931443"
---
# <a name="-resource-visual-basic"></a>-prostředku (Visual Basic)
Vloží spravovaný prostředek sestavení.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
-resource:filename[,identifier[,public|private]]  
' -or-  
-res:filename[,identifier[,public|private]]  
```  
  
## <a name="arguments"></a>Arguments  
  
|Termín|Definice|  
|---|---|  
|`filename`|Požadováno. Název souboru prostředků pro vložení do výstupního souboru. Ve výchozím nastavení `filename` veřejnou v sestavení. Název souboru uzavřete do uvozovek ("") Pokud obsahuje mezery.|  
|`identifier`|Volitelné. Logický název prostředku. Název používaný k načtení. Výchozí hodnota je název souboru. Volitelně můžete určit, zda je prostředek veřejné nebo soukromé v manifestu sestavení, stejně jako u následující: `-res:filename.res, myname.res, public`|  
  
## <a name="remarks"></a>Poznámky  
 Použití `-linkresource` pro propojení prostředku do sestavení bez umístění souboru prostředků do výstupního souboru.  
  
 Pokud `filename` je [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] soubor prostředků vytvořený, například podle [Resgen.exe (Generátor zdrojových souborů)](http://msdn.microsoft.com/library/8ef159de-b660-4bec-9213-c3fbc4d1c6f4) nebo ve vývojovém prostředí, můžete přistupovat pomocí členů z <xref:System.Resources> obor názvů (viz <xref:System.Resources.ResourceManager> Další informace). Pro přístup k dalším prostředkům v době běhu, použijte jednu z následujících metod: <xref:System.Reflection.Assembly.GetManifestResourceInfo%2A>, <xref:System.Reflection.Assembly.GetManifestResourceNames%2A>, nebo <xref:System.Reflection.Assembly.GetManifestResourceStream%2A>.  
  
 Krátký tvar `-resource` je `-res`.  
  
 Informace o tom, jak nastavit `-resource` v sadě Visual Studio IDE, naleznete v tématu [Správa prostředků aplikace (.NET)](/visualstudio/ide/managing-application-resources-dotnet).  
  
## <a name="example"></a>Příklad  
 Následující kód zkompiluje `In.vb` a soubor prostředků bude k obrazci `Rf.resource`.  
  
```console
vbc -res:rf.resource in.vb  
```  
  
## <a name="see-also"></a>Viz také  
 [Kompilátor příkazového řádku jazyka Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)  
 [-win32resource](../../../visual-basic/reference/command-line-compiler/win32resource.md)  
 [-linkresource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/linkresource.md)  
 [-target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)  
 [Příkazové řádky ukázkové kompilace](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
