---
title: -definovat (Visual Basic)
ms.date: 03/10/2018
helpviewer_keywords:
- -d compiler option [Visual Basic]
- /d compiler option [Visual Basic]
- -define compiler option [Visual Basic]
- d compiler option [Visual Basic]
- /define compiler option [Visual Basic]
- define compiler option [Visual Basic]
ms.assetid: f735c57d-1cf9-4f2f-a26f-0de630fd4077
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4de37c58543aed9ed13be8b0d2bcec9830ca9082
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="-define-visual-basic"></a>-definovat (Visual Basic)
Definuje podmíněného kompilátoru konstanty.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
-define:["]symbol[=value][,symbol[=value]]["]  
' -or-  
-d:["]symbol[=value][,symbol[=value]]["]  
```  
  
## <a name="arguments"></a>Arguments  
  
|Termín|Definice|  
|---|---|  
|`symbol`|Požadováno. Symbol, který se má definovat.|  
|`value`|Volitelné. Hodnota pro přiřazení `symbol`. Pokud `value` je řetězec, musí být uzavřena tak pro pořadí zpětné lomítko /-dvojité uvozovky (\\") namísto uvozovky. Pokud není zadaná žádná hodnota, pak se provede na hodnotu True.|  
  
## <a name="remarks"></a>Poznámky  
 `-define` Má vliv podobný používání `#Const` direktivy preprocesoru zdrojový soubor, s výjimkou tohoto konstanty definovaný s `-define` jsou veřejné a platí pro všechny soubory v projektu.  
  
 Můžete použít symboly, které jsou vytvořené pomocí této možnosti `#If`... `Then`... `#Else` direktiva k Podmíněná kompilace zdrojové soubory.  
  
 `-d` je zkratka pro `-define`.  
  
 Můžete definovat více symbolů s `-define` oddělte čárkou oddělit definice symbolu.  
  
|Chcete-li nastavena / definovat v integrovaném vývojovém prostředí sady Visual Studio|  
|---|  
|1.  Máte projekt vybraný v **Průzkumníku řešení**. Na **projektu** nabídky, klikněte na tlačítko **vlastnosti**. <br />2.  Klikněte **zkompilovat** kartě.<br />3.  Klikněte na tlačítko **rozšířené**.<br />4.  Změňte hodnotu v **vlastní konstanty** pole.|  
  
## <a name="example"></a>Příklad  
 Následující kód definuje a pak používá dvě konstanty podmíněného kompilátoru.  
  
 [!code-vb[VbVbalrCompiler#45](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/define_1.vb)]  
  
## <a name="see-also"></a>Viz také  
 [Visual Basic – kompilátor příkazového řádku](../../../visual-basic/reference/command-line-compiler/index.md)  
 [Direktivy #If...Then...#Else](../../../visual-basic/language-reference/directives/if-then-else-directives.md)  
 [Direktiva #Const](../../../visual-basic/language-reference/directives/const-directive.md)  
 [Příkazové řádky ukázkové kompilace](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
