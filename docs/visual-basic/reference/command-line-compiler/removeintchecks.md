---
title: /removeintchecks
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- removeintchecks
- /removeintchecks
helpviewer_keywords:
- removeintchecks compiler option [Visual Basic]
- /removeintchecks compiler option [Visual Basic]
- -removeintchecks compiler option [Visual Basic]
ms.assetid: c1835bd5-1e38-4fba-bd2f-6984774765d4
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 917977d8e5e12c231370ab3c956aca9d96e8a8a8
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="removeintchecks"></a>/removeintchecks
Změní chybu přetečení kontrola celočíselné operace zapnutí nebo vypnutí.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/removeintchecks[+ | -]  
```  
  
## <a name="arguments"></a>Arguments  
  
|Termín|Definice|  
|---|---|  
|`+` &#124; `-`|Volitelné. `/removeintchecks-` Způsobí, že kompilátor ke kontrole všech výpočtů celé číslo chyby přetečení. Výchozí hodnota je `/removeintchecks-`.<br /><br /> Určení `/removeintchecks` nebo `/removeintchecks+` zabraňuje Kontrola chyb a provádět výpočty celé číslo rychlejší. Ale bez chyby kontroly, a pokud jsou k přetečení datového typu kapacity, nesprávné výsledky mohou být uloženy bez vyvolání k chybě.|  
  
|Chcete-li nastavit/removeintchecks v sadě Visual Studio integrované vývojové prostředí|  
|---|  
|1.  Máte projekt vybraný v **Průzkumníku řešení**. Na **projektu** nabídky, klikněte na tlačítko **vlastnosti**. <br />2.  Klikněte **zkompilovat** kartě.<br />3.  Klikněte **Upřesnit** tlačítko.<br />4.  Změnit hodnotu **odebrat kontroly přetečení celých** pole.|  
  
## <a name="example"></a>Příklad  
 Následující kód zkompiluje `Test.vb` a vypne kontrolu chybu přetečení celé číslo.  
  
```  
vbc /removeintchecks+ test.vb  
```  
  
## <a name="see-also"></a>Viz také  
 [Visual Basic – kompilátor příkazového řádku](../../../visual-basic/reference/command-line-compiler/index.md)  
 [Příkazové řádky ukázkové kompilace](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
