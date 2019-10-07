---
title: -linkresource – (Visual Basic)
ms.date: 03/10/2018
helpviewer_keywords:
- /linkresource compiler option [Visual Basic]
- -linkresource compiler option [Visual Basic]
- linkresource compiler option [Visual Basic]
- /linkres compiler option [Visual Basic]
- linkres compiler option [Visual Basic]
- -linkres compiler option [Visual Basic]
ms.assetid: cf4dcad8-17b7-404c-9184-29358aa05b15
ms.openlocfilehash: dee5384696d543442f3280b9fdb535a7d9b6f863
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005486"
---
# <a name="-linkresource-visual-basic"></a>-linkresource – (Visual Basic)
Vytvoří odkaz na spravovaný prostředek.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-linkresource:filename[,identifier[,public|private]]  
```

or  

```console
-linkres:filename[,identifier[,public|private]]  
```  
  
## <a name="arguments"></a>Arguments  
 `filename`  
 Požadováno. Soubor prostředků, který má být propojen se sestavením. Pokud název souboru obsahuje mezeru, uzavřete název do uvozovek ("").  
  
 `identifier`  
 Volitelné. Logický název prostředku. Název, který se použije k načtení prostředku. Výchozí hodnota je název souboru. Volitelně můžete určit, zda je soubor v manifestu sestavení veřejný nebo soukromý, například: `-linkres:filename.res,myname.res,public`. Ve výchozím nastavení je `filename` v sestavení veřejné.  
  
## <a name="remarks"></a>Poznámky  
 Možnost `-linkresource` nevloží soubor prostředků do výstupního souboru; k tomu slouží možnost `-resource`.  
  
 Možnost `-linkresource` vyžaduje jednu z možností `-target` Kromě `-target:module`.  
  
 Pokud je `filename` vytvořen .NET Framework soubor prostředků, například pomocí nástroje [Resgen. exe (generátor zdrojového souboru)](../../../framework/tools/resgen-exe-resource-file-generator.md) nebo ve vývojovém prostředí, lze k němu přistupovat pomocí členů v oboru názvů <xref:System.Resources>. (Další informace najdete v tématu <xref:System.Resources.ResourceManager>.) Pro přístup ke všem dalším prostředkům v době běhu použijte metody, které začínají na `GetManifestResource` ve třídě <xref:System.Reflection.Assembly>.  
  
 Název souboru může být libovolný formát souboru. Například můžete chtít vytvořit nativní knihovnu DLL součásti sestavení, aby mohla být nainstalována do globální mezipaměti sestavení (GAC) a zpřístupněna ze spravovaného kódu v sestavení.  
  
 Krátká forma `-linkresource` je `-linkres`.  
  
> [!NOTE]
> Možnost `-linkresource` není k dispozici ve vývojovém prostředí sady Visual Studio; je k dispozici pouze při kompilaci z příkazového řádku.  
  
## <a name="example"></a>Příklad  
 Následující kód zkompiluje `in.vb` a odkazuje na soubor prostředků `rf.resource`.  
  
```console  
vbc -linkresource:rf.resource in.vb  
```  
  
## <a name="see-also"></a>Viz také:

- [Visual Basic Kompilátor příkazového řádku](../../../visual-basic/reference/command-line-compiler/index.md)
- [-Target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)
- [-Resource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/resource.md)
- [Příkazové řádky ukázkové kompilace](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
