---
title: /libpath
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- libpath compiler option [Visual Basic]
- /libpath compiler option [Visual Basic]
- -libpath compiler option [Visual Basic]
ms.assetid: 5f1c26c9-3455-4e89-bdf3-b12d6c2e655b
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4f8a87ea3f3e551dfc84212e92f1409ef61bcba2
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="libpath"></a>/libpath
Určuje umístění odkazované sestavení.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/libpath:dirList  
```  
  
## <a name="arguments"></a>Arguments  
  
|Termín|Definice|  
|---|---|  
|`dirList`|Požadováno. Seznam oddělený středníkem adresářů pro kompilátor hledat v případě odkazované sestavení nebyl nalezen v některém aktuální pracovní adresář (adresář, ze kterého je vyvolán kompilátor) nebo modul common language runtime systémového adresáře. Pokud název adresáře obsahuje mezery, uzavřete název v uvozovkách ("").|  
  
## <a name="remarks"></a>Poznámky  
 `/libpath` Možnost určuje umístění sestavení odkazuje [/reference](../../../visual-basic/reference/command-line-compiler/reference.md) možnost.  
  
 Hledání kompilátoru pro odkazy na sestavení, které nejsou plně kvalifikovaný v následujícím pořadí:  
  
1.  Aktuální pracovní adresář. Toto je adresář, ze kterého je vyvolán kompilátor.  
  
2.  Common language runtime systémového adresáře.  
  
3.  Adresáře určené `/libpath`.  
  
4.  Adresáře určené proměnná prostředí LIB.  
  
 `/libpath` Možnost je sčítání; zadání je více než jednou připojí k jakékoli předchozí hodnoty.  
  
 Použití `/reference` zadat odkaz na sestavení.  
  
|Chcete-li nastavit/Libpath v sadě Visual Studio integrované vývojové prostředí|  
|---|  
|1.  Máte projekt vybraný v **Průzkumníku řešení**. Na **projektu** nabídky, klikněte na tlačítko **vlastnosti**. <br />2.  Klikněte **odkazy** kartě.<br />3.  Klikněte **odkazovat cesty...**  tlačítko.<br />4.  V **cesty odkazů** dialogovém okně zadejte název adresáře v **složky:** pole.<br />5.  Klikněte na tlačítko **přidat složku**.|  
  
## <a name="example"></a>Příklad  
 Následující kód zkompiluje `T2.vb` k vytvoření souboru s příponou .exe. Kompilátor vyhledá v pracovním adresáři, v kořenovém adresáři jednotky C: a v adresáři nové sestavení jednotky C: odkazy na sestavení.  
  
```  
vbc /libpath:c:\;"c:\New Assemblies" /reference:t2.dll t2.vb  
```  
  
## <a name="see-also"></a>Viz také  
 [Sestavení a globální mezipaměť sestavení (GAC)](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)  
 [Visual Basic – kompilátor příkazového řádku](../../../visual-basic/reference/command-line-compiler/index.md)  
 [Příkazové řádky ukázkové kompilace](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
