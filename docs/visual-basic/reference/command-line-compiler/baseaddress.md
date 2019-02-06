---
title: -baseaddress
ms.date: 08/09/2018
f1_keywords:
- /baseaddress
- baseaddress
helpviewer_keywords:
- -baseaddress compiler option [Visual Basic]
- /baseaddress compiler option [Visual Basic]
- baseaddress compiler option [Visual Basic]
ms.assetid: c982bcf2-46e5-47a2-bc8f-a5cc32b7dc47
ms.openlocfilehash: 733013c8eca75bad0dc0bdf1d76f1468b1d903a8
ms.sourcegitcommit: 01ea420eaa4bf76d5fc47673294c8881379b3369
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/06/2019
ms.locfileid: "55759389"
---
# <a name="-baseaddress"></a>-baseaddress
Určuje výchozí základní adresa, při vytváření knihovny DLL.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
-baseaddress:address  
```  
  
## <a name="arguments"></a>Arguments  
  
|Termín|Definice|  
|---|---|  
|`address`|Povinný parametr. Základní adresa pro knihovnu DLL. Tato adresa musí být zadán jako šestnáctkové číslo.|  
  
## <a name="remarks"></a>Poznámky  
 Výchozí základní adresa pro knihovnu DLL se nastavuje [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].  
  
 Mějte na paměti, že se zaokrouhlí nižší řád slova v této adrese. Například pokud chcete zadat 0x11110001, to se zaokrouhlí na 0x11110000.  
  
 Chcete-li dokončit proces podepisování pro knihovnu DLL, použijte `–R` – možnost Nástroje pro silné pojmenovávání (Sn.exe).  
  
 Tato možnost se ignoruje, pokud cíl není knihovny DLL.  
  
|Chcete-li nastavit - baseaddress v integrovaném vývojovém prostředí sady Visual Studio|  
|---|  
|1.  Mají projekt vybraný v **Průzkumníka řešení**. Na **projektu** nabídky, klikněte na tlačítko **vlastnosti**. <br />2.  Klikněte na tlačítko **kompilaci** kartu.<br />3.  Klikněte na tlačítko **Advanced**.<br />4.  Upravte hodnotu v **základní adresa knihovny DLL:** pole. **Poznámka:**      **Základní adresa knihovny DLL:** pole je jen pro čtení, pokud cíl není knihovny DLL.|  
  
## <a name="see-also"></a>Viz také:
- [Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md)
- [-target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)
- [Příkazové řádky ukázkové kompilace](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [Sn.exe (nástroj pro silný název)](../../../framework/tools/sn-exe-strong-name-tool.md))
