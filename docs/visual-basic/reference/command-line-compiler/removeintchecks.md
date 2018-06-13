---
title: -removeintchecks
ms.date: 03/13/2018
f1_keywords:
- removeintchecks
- -removeintchecks
helpviewer_keywords:
- removeintchecks compiler option [Visual Basic]
- /removeintchecks compiler option [Visual Basic]
- -removeintchecks compiler option [Visual Basic]
ms.assetid: c1835bd5-1e38-4fba-bd2f-6984774765d4
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 26485fe2ba3f5647266147744cbe53f978694a9d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33656123"
---
# <a name="-removeintchecks"></a>-removeintchecks
Změní chybu přetečení kontrola celočíselné operace zapnutí nebo vypnutí.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
-removeintchecks[+ | -]  
```  
  
## <a name="arguments"></a>Arguments  
  
|Termín|Definice|  
|---|---|  
|`+` &#124; `-`|Volitelné. `-removeintchecks-` Způsobí, že kompilátor ke kontrole všech výpočtů celé číslo chyby přetečení. Výchozí hodnota je `-removeintchecks-`.<br /><br /> Určení `-removeintchecks` nebo `-removeintchecks+` zabraňuje Kontrola chyb a provádět výpočty celé číslo rychlejší. Ale bez chyby kontroly, a pokud jsou k přetečení datového typu kapacity, nesprávné výsledky mohou být uloženy bez vyvolání k chybě.|  
  
|Chcete-li nastavit - removeintchecks v integrovaném vývojovém prostředí sady Visual Studio|  
|---|  
|1.  Máte projekt vybraný v **Průzkumníku řešení**. Na **projektu** nabídky, klikněte na tlačítko **vlastnosti**. <br />2.  Klikněte **zkompilovat** kartě.<br />3.  Klikněte **Upřesnit** tlačítko.<br />4.  Změnit hodnotu **odebrat kontroly přetečení celých** pole.|  
  
## <a name="example"></a>Příklad  
 Následující kód zkompiluje `Test.vb` a vypne kontrolu chybu přetečení celé číslo.  
  
```console
vbc -removeintchecks+ test.vb  
```  
  
## <a name="see-also"></a>Viz také  
 [Visual Basic – kompilátor příkazového řádku](../../../visual-basic/reference/command-line-compiler/index.md)  
 [Příkazové řádky ukázkové kompilace](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
