---
title: -Resource (Visual Basic)
ms.date: 03/13/2018
helpviewer_keywords:
- /resource compiler option [Visual Basic]
- -resource compiler option [Visual Basic]
- /res compiler option [Visual Basic]
- res compiler option [Visual Basic]
- -res compiler option [Visual Basic]
- resource compiler option [Visual Basic]
ms.assetid: eee2f227-91f2-4f2b-a9d6-1c51c5320858
ms.openlocfilehash: 5bedc346381f6de293933dce14a8c5c3044b246f
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005192"
---
# <a name="-resource-visual-basic"></a>-Resource (Visual Basic)
Vloží spravovaný prostředek do sestavení.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-resource:filename[,identifier[,public|private]]  
```

or  

```console
-res:filename[,identifier[,public|private]]  
```  
  
## <a name="arguments"></a>Arguments  
  
|Termín|Definice|  
|---|---|  
|`filename`|Požadováno. Název souboru prostředků, který má být vložen do výstupního souboru. Ve výchozím nastavení je `filename` v sestavení veřejné. Uzavřete název souboru do uvozovek (""), pokud obsahuje mezeru.|  
|`identifier`|Volitelné. Logický název prostředku; název, který se používá k načtení. Výchozí hodnota je název souboru. Volitelně můžete určit, zda je prostředek v manifestu sestavení veřejný nebo privátní, jako u následujícího: `-res:filename.res, myname.res, public`|  
  
## <a name="remarks"></a>Poznámky  
 K propojení prostředku se sestavením použijte `-linkresource` bez umístění souboru prostředků do výstupního souboru.  
  
 Pokud je `filename` vytvořen .NET Framework soubor prostředků, například pomocí nástroje [Resgen. exe (generátor zdrojového souboru)](../../../framework/tools/resgen-exe-resource-file-generator.md) nebo ve vývojovém prostředí, lze k němu získat pøístup pomocí členů v oboru názvů <xref:System.Resources> (Další informace naleznete v <xref:System.Resources.ResourceManager>). Chcete-li získat přístup ke všem dalším prostředkům v době běhu, použijte jednu z následujících metod: <xref:System.Reflection.Assembly.GetManifestResourceInfo%2A>, <xref:System.Reflection.Assembly.GetManifestResourceNames%2A> nebo <xref:System.Reflection.Assembly.GetManifestResourceStream%2A>.  
  
 Krátká forma `-resource` je `-res`.  
  
 Informace o tom, jak nastavit `-resource` v integrovaném vývojovém prostředí sady Visual Studio, najdete v tématu [Správa prostředků aplikace (.NET)](/visualstudio/ide/managing-application-resources-dotnet).  
  
## <a name="example"></a>Příklad  
 Následující kód zkompiluje `In.vb` a připojí soubor prostředků `Rf.resource`.  
  
```console
vbc -res:rf.resource in.vb  
```  
  
## <a name="see-also"></a>Viz také:

- [Visual Basic Kompilátor příkazového řádku](../../../visual-basic/reference/command-line-compiler/index.md)
- [-win32resource](../../../visual-basic/reference/command-line-compiler/win32resource.md)
- [-linkresource – (Visual Basic)](../../../visual-basic/reference/command-line-compiler/linkresource.md)
- [-Target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)
- [Příkazové řádky ukázkové kompilace](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
