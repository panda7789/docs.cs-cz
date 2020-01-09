---
title: -define
ms.date: 03/10/2018
helpviewer_keywords:
- -d compiler option [Visual Basic]
- /d compiler option [Visual Basic]
- -define compiler option [Visual Basic]
- d compiler option [Visual Basic]
- /define compiler option [Visual Basic]
- define compiler option [Visual Basic]
ms.assetid: f735c57d-1cf9-4f2f-a26f-0de630fd4077
ms.openlocfilehash: 5035466de4aa17c374824e1b0f02ed594731a9d3
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75716802"
---
# <a name="-define-visual-basic"></a>-define (Visual Basic)
Definuje podmíněné konstanty kompilátoru.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-define:["]symbol[=value][,symbol[=value]]["]  
```

nebo

```console  
-d:["]symbol[=value][,symbol[=value]]["]  
```  
  
## <a name="arguments"></a>Arguments  
  
|Termín|Definice|  
|---|---|  
|`symbol`|Požadováno. Symbol, který má být definován.|  
|`value`|Volitelné. Hodnota, kterou chcete přiřadit `symbol`. Pokud `value` je řetězec, musí být ohraničen znakem zpětného lomítka nebo posloupnosti uvozovek (\\") místo uvozovek. Pokud není zadána žádná hodnota, bude provedena hodnota true.|  
  
## <a name="remarks"></a>Poznámky  
 Možnost `-define` má podobný efekt jako použití direktivy preprocesoru `#Const` ve zdrojovém souboru, s tím rozdílem, že konstanty definované s `-define` jsou veřejné a platí pro všechny soubory v projektu.  
  
 Symboly vytvořené pomocí této možnosti můžete použít spolu s direktivou `#If`...`Then`...`#Else` ke podmíněnému kompilování zdrojových souborů.  
  
 `-d` je krátká forma `-define`.  
  
 Můžete definovat více symbolů pomocí `-define` čárkou pro oddělení definic symbolů.  
  
|Nastavení – definice v integrovaném vývojovém prostředí sady Visual Studio|  
|---|  
|1. v **Průzkumník řešení**mít vybraný projekt. V nabídce **projekt** klikněte na příkaz **vlastnosti**. <br />2. klikněte na kartu **kompilovat** .<br />3. klikněte na tlačítko **Upřesnit**.<br />4. upravte hodnotu v poli **vlastní konstanty** .|  
  
## <a name="example"></a>Příklad  
 Následující kód definuje a poté používá dvě podmíněné konstanty kompilátoru.  
  
 [!code-vb[VbVbalrCompiler#45](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/Class1.vb#45)]  
  
## <a name="see-also"></a>Viz také:

- [Visual Basic Kompilátor příkazového řádku](../../../visual-basic/reference/command-line-compiler/index.md)
- [Direktivy #If...Then...#Else](../../../visual-basic/language-reference/directives/if-then-else-directives.md)
- [Direktiva #Const](../../../visual-basic/language-reference/directives/const-directive.md)
- [Příkazové řádky ukázkové kompilace](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
