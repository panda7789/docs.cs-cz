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
ms.openlocfilehash: bea6ca24ea6da9000267e754d52fe0ca152f7d7f
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005224"
---
# <a name="-removeintchecks"></a>-removeintchecks
Zapne nebo vypne kontrolu chyb pro celočíselné operace.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-removeintchecks[+ | -]  
```  
  
## <a name="arguments"></a>Arguments  
  
|Termín|Definice|  
|---|---|  
|`+` &#124; `-`|Volitelné. Možnost `-removeintchecks-` způsobí, že kompilátor zkontroluje všechny celočíselné výpočty pro chyby přetečení. Výchozí hodnota je `-removeintchecks-`.<br /><br /> Zadáním `-removeintchecks` nebo `-removeintchecks+` zabráníte kontrole chyb a rychleji můžete provádět výpočty celých čísel. Bez kontroly chyb a v případě, že dojde k přetečení kapacit datových typů, mohou být uloženy nesprávné výsledky bez vyvolání chyby.|  
  
|Nastavení-removeintchecks – v integrovaném vývojovém prostředí sady Visual Studio|  
|---|  
|1. v **Průzkumník řešení**mít vybraný projekt. V nabídce **projekt** klikněte na příkaz **vlastnosti**. <br />2. klikněte na kartu **kompilovat** .<br />3. klikněte na tlačítko **Upřesnit** .<br />4. Změňte hodnotu pole **Odebrat kontroly přetečení celých čísel** .|  
  
## <a name="example"></a>Příklad  
 Následující kód zkompiluje `Test.vb` a vypne přetečení celého čísla – kontrola chyb.  
  
```console
vbc -removeintchecks+ test.vb  
```  
  
## <a name="see-also"></a>Viz také:

- [Visual Basic Kompilátor příkazového řádku](../../../visual-basic/reference/command-line-compiler/index.md)
- [Příkazové řádky ukázkové kompilace](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
