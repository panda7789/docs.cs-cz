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
ms.openlocfilehash: ec4722cb7088819dae95ca1b7cbc1469d957a7aa
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400471"
---
# <a name="-removeintchecks"></a>-removeintchecks
Zapne nebo vypne kontrolu chyb pro celočíselné operace.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-removeintchecks[+ | -]  
```  
  
## <a name="arguments"></a>Argumenty  
  
|Pojem|Definice|  
|---|---|  
|`+`&#124;`-`|Nepovinný parametr. `-removeintchecks-`Možnost způsobí, že kompilátor zkontroluje všechny celočíselné výpočty pro chyby přetečení. Výchozí formát je `-removeintchecks-`.<br /><br /> Určení `-removeintchecks` nebo `-removeintchecks+` zabránění v kontrole chyb a rychlejší provádění výpočtů v celých číslech Bez kontroly chyb a v případě, že dojde k přetečení kapacit datových typů, mohou být uloženy nesprávné výsledky bez vyvolání chyby.|  
  
|Nastavení-removeintchecks – v integrovaném vývojovém prostředí sady Visual Studio|  
|---|  
|1. v **Průzkumník řešení**mít vybraný projekt. V nabídce **projekt** klikněte na příkaz **vlastnosti**. <br />2. klikněte na kartu **kompilovat** .<br />3. klikněte na tlačítko **Upřesnit** .<br />4. Změňte hodnotu pole **Odebrat kontroly přetečení celých čísel** .|  
  
## <a name="example"></a>Příklad  
 Následující kód zkompiluje `Test.vb` a vypne přetečení celého čísla – kontrola chyb.  
  
```console
vbc -removeintchecks+ test.vb  
```  
  
## <a name="see-also"></a>Viz také

- [Visual Basic Kompilátor příkazového řádku](index.md)
- [Příkazové řádky ukázkové kompilace](sample-compilation-command-lines.md)
