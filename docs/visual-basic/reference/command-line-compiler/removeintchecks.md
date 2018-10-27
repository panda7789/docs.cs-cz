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
ms.openlocfilehash: f061497083dc23fd07f61108938a4129c0af5f3a
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2018
ms.locfileid: "50188524"
---
# <a name="-removeintchecks"></a>-removeintchecks
Zapne přetečení-Chyba při kontrole celočíselné operace zapnutí nebo vypnutí.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
-removeintchecks[+ | -]  
```  
  
## <a name="arguments"></a>Arguments  
  
|Termín|Definice|  
|---|---|  
|`+` &#124; `-`|Volitelné. `-removeintchecks-` Možnost způsobí, že kompilátoru, aby všechny výpočty celé číslo chyby přetečení. Výchozí hodnota je `-removeintchecks-`.<br /><br /> Určení `-removeintchecks` nebo `-removeintchecks+` brání kontroly chyb a rychlejší kvůli výpočtům celé číslo. Ale bez kontroly chyb, a pokud jsou datové kapacity. typ došlo k přetečení, nesprávné výsledky mohou být uložena bez vyvolání k chybě.|  
  
|Chcete-li nastavit - removeintchecks v integrovaném vývojovém prostředí sady Visual Studio|  
|---|  
|1.  Mají projekt vybraný v **Průzkumníka řešení**. Na **projektu** nabídky, klikněte na tlačítko **vlastnosti**. <br />2.  Klikněte na tlačítko **kompilaci** kartu.<br />3.  Klikněte na tlačítko **Upřesnit** tlačítko.<br />4.  Změnit hodnotu **odebrat kontroly přetečení celých čísel** pole.|  
  
## <a name="example"></a>Příklad  
 Následující kód zkompiluje `Test.vb` a vypne kontrolu chyb přetečení celého čísla.  
  
```console
vbc -removeintchecks+ test.vb  
```  
  
## <a name="see-also"></a>Viz také  
 [Kompilátor příkazového řádku jazyka Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)  
 [Příkazové řádky ukázkové kompilace](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
