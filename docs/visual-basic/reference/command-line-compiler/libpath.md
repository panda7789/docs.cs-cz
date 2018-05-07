---
title: -libpath
ms.date: 03/10/2018
helpviewer_keywords:
- libpath compiler option [Visual Basic]
- /libpath compiler option [Visual Basic]
- -libpath compiler option [Visual Basic]
ms.assetid: 5f1c26c9-3455-4e89-bdf3-b12d6c2e655b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a5044bc0093960fdf6b063450d8d3a57575ff07c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="-libpath"></a>-libpath
Určuje umístění odkazované sestavení.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
-libpath:dirList  
```  
  
## <a name="arguments"></a>Arguments  
  
|Termín|Definice|  
|---|---|  
|`dirList`|Požadováno. Seznam oddělený středníkem adresářů pro kompilátor hledat v případě odkazované sestavení nebyl nalezen v některém aktuální pracovní adresář (adresář, ze kterého je vyvolán kompilátor) nebo modul common language runtime systémového adresáře. Pokud název adresáře obsahuje mezery, uzavřete název v uvozovkách ("").|  
  
## <a name="remarks"></a>Poznámky  
 `-libpath` Možnost určuje umístění sestavení odkazuje [– referenční dokumentace](../../../visual-basic/reference/command-line-compiler/reference.md) možnost.  
  
 Hledání kompilátoru pro odkazy na sestavení, které nejsou plně kvalifikovaný v následujícím pořadí:  
  
1.  Aktuální pracovní adresář. Toto je adresář, ze kterého je vyvolán kompilátor.  
  
2.  Common language runtime systémového adresáře.  
  
3.  Adresáře určené `/libpath`.  
  
4.  Adresáře určené proměnná prostředí LIB.  
  
 `-libpath` Možnost je sčítání; zadání je více než jednou připojí k jakékoli předchozí hodnoty.  
  
 Použití `-reference` zadat odkaz na sestavení.  
  
|Chcete-li nastavit/Libpath v sadě Visual Studio integrované vývojové prostředí|  
|---|  
|1.  Máte projekt vybraný v **Průzkumníku řešení**. Na **projektu** nabídky, klikněte na tlačítko **vlastnosti**. <br />2.  Klikněte **odkazy** kartě.<br />3.  Klikněte **odkazovat cesty...**  tlačítko.<br />4.  V **cesty odkazů** dialogovém okně zadejte název adresáře v **složky:** pole.<br />5.  Klikněte na tlačítko **přidat složku**.|  
  
## <a name="example"></a>Příklad  
 Následující kód zkompiluje `T2.vb` k vytvoření souboru s příponou .exe. Kompilátor vyhledá v pracovním adresáři, v kořenovém adresáři jednotky C: a v adresáři nové sestavení jednotky C: odkazy na sestavení.  
  
```console  
vbc -libpath:c:\;"c:\New Assemblies" -reference:t2.dll t2.vb  
```  
  
## <a name="see-also"></a>Viz také  
 [Sestavení a globální mezipaměť sestavení (GAC)](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)  
 [Visual Basic – kompilátor příkazového řádku](../../../visual-basic/reference/command-line-compiler/index.md)  
 [Příkazové řádky ukázkové kompilace](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
