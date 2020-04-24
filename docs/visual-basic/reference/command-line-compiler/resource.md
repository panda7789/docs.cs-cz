---
title: -resource
ms.date: 03/13/2018
helpviewer_keywords:
- /resource compiler option [Visual Basic]
- -resource compiler option [Visual Basic]
- /res compiler option [Visual Basic]
- res compiler option [Visual Basic]
- -res compiler option [Visual Basic]
- resource compiler option [Visual Basic]
ms.assetid: eee2f227-91f2-4f2b-a9d6-1c51c5320858
ms.openlocfilehash: a781d543dd32ffb3d0ac0b11c544dbfd8cd5d806
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348556"
---
# <a name="-resource-visual-basic"></a>-Resource (Visual Basic)
Vloží spravovaný prostředek do sestavení.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-resource:filename[,identifier[,public|private]]  
```

– nebo –  

```console
-res:filename[,identifier[,public|private]]  
```  
  
## <a name="arguments"></a>Argumenty  
  
|Označení|Definice|  
|---|---|  
|`filename`|Povinná hodnota. Název souboru prostředků, který má být vložen do výstupního souboru. Ve výchozím nastavení `filename` je v sestavení veřejné. Uzavřete název souboru do uvozovek (""), pokud obsahuje mezeru.|  
|`identifier`|Nepovinný parametr. Logický název prostředku; název, který se používá k načtení. Výchozí hodnota je název souboru. Volitelně můžete určit, zda je prostředek v manifestu sestavení veřejný nebo privátní, jako následující:`-res:filename.res, myname.res, public`|  
  
## <a name="remarks"></a>Poznámky  
 Slouží `-linkresource` k propojení prostředku se sestavením bez umístění souboru prostředků do výstupního souboru.  
  
 Pokud `filename` je vytvořen soubor prostředků .NET Framework například pomocí nástroje [Resgen. exe (generátor zdrojového souboru)](../../../framework/tools/resgen-exe-resource-file-generator.md) nebo ve vývojovém prostředí, lze k němu získat pøístup pomocí členů <xref:System.Resources> oboru názvů (Další informace najdete v tématu <xref:System.Resources.ResourceManager> ). Chcete-li získat přístup ke všem dalším prostředkům za běhu, použijte jednu z následujících <xref:System.Reflection.Assembly.GetManifestResourceInfo%2A>metod <xref:System.Reflection.Assembly.GetManifestResourceNames%2A>:, <xref:System.Reflection.Assembly.GetManifestResourceStream%2A>nebo.  
  
 Krátká forma `-resource` je `-res`.  
  
 Informace o tom, jak nastavit `-resource` v integrovaném vývojovém prostředí sady Visual Studio, najdete v tématu [Správa prostředků aplikace (.NET)](/visualstudio/ide/managing-application-resources-dotnet).  
  
## <a name="example"></a>Příklad  
 Následující kód zkompiluje `In.vb` a připojí soubor `Rf.resource`prostředků.  
  
```console
vbc -res:rf.resource in.vb  
```  
  
## <a name="see-also"></a>Viz také

- [Visual Basic Kompilátor příkazového řádku](../../../visual-basic/reference/command-line-compiler/index.md)
- [– win32resource](../../../visual-basic/reference/command-line-compiler/win32resource.md)
- [-linkresource – (Visual Basic)](../../../visual-basic/reference/command-line-compiler/linkresource.md)
- [-Target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)
- [Příkazové řádky ukázkové kompilace](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
