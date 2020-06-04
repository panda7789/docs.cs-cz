---
title: -linkresource
ms.date: 03/10/2018
helpviewer_keywords:
- /linkresource compiler option [Visual Basic]
- -linkresource compiler option [Visual Basic]
- linkresource compiler option [Visual Basic]
- /linkres compiler option [Visual Basic]
- linkres compiler option [Visual Basic]
- -linkres compiler option [Visual Basic]
ms.assetid: cf4dcad8-17b7-404c-9184-29358aa05b15
ms.openlocfilehash: 43ebb61efa26ed11af573e2c4e73a6fd71ac0902
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403197"
---
# <a name="-linkresource-visual-basic"></a>-linkresource – (Visual Basic)
Vytvoří odkaz na spravovaný prostředek.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-linkresource:filename[,identifier[,public|private]]  
```

nebo  

```console
-linkres:filename[,identifier[,public|private]]  
```  
  
## <a name="arguments"></a>Arguments  
 `filename`  
 Povinná hodnota. Soubor prostředků, který má být propojen se sestavením. Pokud název souboru obsahuje mezeru, uzavřete název do uvozovek ("").  
  
 `identifier`  
 Nepovinný parametr. Logický název prostředku. Název, který se použije k načtení prostředku. Výchozí hodnota je název souboru. Volitelně můžete určit, zda je soubor v manifestu sestavení veřejný nebo soukromý, například: `-linkres:filename.res,myname.res,public` . Ve výchozím nastavení `filename` je v sestavení veřejné.  
  
## <a name="remarks"></a>Poznámky  
 `-linkresource`Možnost nevloží soubor prostředků do výstupního souboru. použijte `-resource` k tomu možnost.  
  
 `-linkresource`Možnost vyžaduje jednu z `-target` možností kromě `-target:module` .  
  
 Pokud `filename` je vytvořen soubor prostředků .NET Framework, například pomocí nástroje [Resgen. exe (generátor zdrojového souboru)](../../../framework/tools/resgen-exe-resource-file-generator.md) nebo ve vývojovém prostředí, lze k němu přistupovat pomocí členů v <xref:System.Resources> oboru názvů. (Další informace najdete v tématu <xref:System.Resources.ResourceManager> .) Pro přístup ke všem dalším prostředkům v době běhu použijte metody, které začínají `GetManifestResource` ve <xref:System.Reflection.Assembly> třídě.  
  
 Název souboru může být libovolný formát souboru. Například můžete chtít vytvořit nativní knihovnu DLL součásti sestavení, aby mohla být nainstalována do globální mezipaměti sestavení (GAC) a zpřístupněna ze spravovaného kódu v sestavení.  
  
 Krátká forma `-linkresource` je `-linkres` .  
  
> [!NOTE]
> Tato `-linkresource` možnost není k dispozici ve vývojovém prostředí sady Visual Studio. je k dispozici pouze při kompilaci z příkazového řádku.  
  
## <a name="example"></a>Příklad  
 Následující kód zkompiluje a vytvoří `in.vb` odkazy na soubor prostředků `rf.resource` .  
  
```console  
vbc -linkresource:rf.resource in.vb  
```  
  
## <a name="see-also"></a>Viz také

- [Visual Basic Kompilátor příkazového řádku](index.md)
- [-Target (Visual Basic)](target.md)
- [-Resource (Visual Basic)](resource.md)
- [Příkazové řádky ukázkové kompilace](sample-compilation-command-lines.md)
