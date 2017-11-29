---
title: /define (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- -d compiler option [Visual Basic]
- /d compiler option [Visual Basic]
- -define compiler option [Visual Basic]
- d compiler option [Visual Basic]
- /define compiler option [Visual Basic]
- define compiler option [Visual Basic]
ms.assetid: f735c57d-1cf9-4f2f-a26f-0de630fd4077
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 8bc3056c3e2d7a4aad469d3bf2c404f5f5248384
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="define-visual-basic"></a>/define (Visual Basic)
Definuje podmíněného kompilátoru konstanty.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/define:["]symbol[=value][,symbol[=value]]["]  
' -or-  
/d:["]symbol[=value][,symbol[=value]]["]  
```  
  
## <a name="arguments"></a>Arguments  
  
|Termín|Definice|  
|---|---|  
|`symbol`|Požadováno. Symbol, který se má definovat.|  
|`value`|Volitelné. Hodnota pro přiřazení `symbol`. Pokud `value` je řetězec, musí být uzavřena tak pro pořadí zpětné lomítko /-dvojité uvozovky (\\") namísto uvozovky. Pokud není zadaná žádná hodnota, pak se provede na hodnotu True.|  
  
## <a name="remarks"></a>Poznámky  
 `/define` Má vliv podobný používání `#Const` direktivy preprocesoru zdrojový soubor, s výjimkou tohoto konstanty definovaný s `/define` jsou veřejné a platí pro všechny soubory v projektu.  
  
 Můžete použít symboly, které jsou vytvořené pomocí této možnosti `#If`... `Then`... `#Else` direktiva k Podmíněná kompilace zdrojové soubory.  
  
 `/d`je zkratka pro `/define`.  
  
 Můžete definovat více symbolů s `/define` oddělte čárkou oddělit definice symbolu.  
  
|Chcete-li nastavena / definovat v integrovaném vývojovém prostředí sady Visual Studio|  
|---|  
|1.  Máte projekt vybraný v **Průzkumníku řešení**. Na **projektu** nabídky, klikněte na tlačítko **vlastnosti**. Další informace najdete v tématu [Úvod do Návrhář projektu](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).<br />2.  Klikněte **zkompilovat** kartě.<br />3.  Klikněte na tlačítko **rozšířené**.<br />4.  Změňte hodnotu v **vlastní konstanty** pole.|  
  
## <a name="example"></a>Příklad  
 Následující kód definuje a pak používá dvě konstanty podmíněného kompilátoru.  
  
 [!code-vb[VbVbalrCompiler#45](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/define_1.vb)]  
  
## <a name="see-also"></a>Viz také  
 [Visual Basic – kompilátor příkazového řádku](../../../visual-basic/reference/command-line-compiler/index.md)  
 [#If... Then... #Else – direktivy](../../../visual-basic/language-reference/directives/if-then-else-directives.md)  
 [#Const – direktiva](../../../visual-basic/language-reference/directives/const-directive.md)  
 [Příkazové řádky ukázkové kompilace](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
