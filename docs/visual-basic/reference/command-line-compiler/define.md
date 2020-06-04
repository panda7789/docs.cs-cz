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
ms.openlocfilehash: d0d1b03d9ab98f28a0112198f1ecc1e928d6d4a7
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84408709"
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
  
## <a name="arguments"></a>Argumenty  
  
|Pojem|Definice|  
|---|---|  
|`symbol`|Povinná hodnota. Symbol, který má být definován.|  
|`value`|Nepovinný parametr. Hodnota, která má být přiřazena `symbol` . Pokud `value` je řetězec, musí být ohraničen znakem zpětného lomítka nebo posloupnosti uvozovek ( \\ ") místo uvozovek. Pokud není zadána žádná hodnota, bude provedena hodnota true.|  
  
## <a name="remarks"></a>Poznámky  
 `-define`Možnost má podobný efekt jako použití `#Const` direktivy preprocesoru ve zdrojovém souboru s tím rozdílem, že konstanty definované s `-define` jsou veřejné a platí pro všechny soubory v projektu.  
  
 Můžete použít symboly vytvořené pomocí této možnosti s `#If` ... `Then` ...`#Else` Direktiva podmíněného kompilování zdrojových souborů.  
  
 `-d`je krátký tvar `-define` .  
  
 Můžete definovat více symbolů pomocí `-define` čárky pro oddělení definic symbolů.  
  
|Nastavení – definice v integrovaném vývojovém prostředí sady Visual Studio|  
|---|  
|1. v **Průzkumník řešení**mít vybraný projekt. V nabídce **projekt** klikněte na příkaz **vlastnosti**. <br />2. klikněte na kartu **kompilovat** .<br />3. klikněte na tlačítko **Upřesnit**.<br />4. upravte hodnotu v poli **vlastní konstanty** .|  
  
## <a name="example"></a>Příklad  
 Následující kód definuje a poté používá dvě podmíněné konstanty kompilátoru.  
  
 [!code-vb[VbVbalrCompiler#45](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/Class1.vb#45)]  
  
## <a name="see-also"></a>Viz také

- [Visual Basic Kompilátor příkazového řádku](index.md)
- [#If... Then... #Else – direktivy](../../language-reference/directives/if-then-else-directives.md)
- [#Const direktiva](../../language-reference/directives/const-directive.md)
- [Příkazové řádky ukázkové kompilace](sample-compilation-command-lines.md)
