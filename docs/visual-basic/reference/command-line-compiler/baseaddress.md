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
ms.openlocfilehash: 6331a55bb1d20b5804605db103dcfd2997e348d9
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/26/2018
ms.locfileid: "42930439"
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
|`address`|Požadováno. Základní adresa pro knihovnu DLL. Tato adresa musí být zadán jako šestnáctkové číslo.|  
  
## <a name="remarks"></a>Poznámky  
 Výchozí základní adresa pro knihovnu DLL se nastavuje [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].  
  
 Mějte na paměti, že se zaokrouhlí nižší řád slova v této adrese. Například pokud chcete zadat 0x11110001, to se zaokrouhlí na 0x11110000.  
  
 Chcete-li dokončit proces podepisování pro knihovnu DLL, použijte `–R` – možnost Nástroje pro silné pojmenovávání (Sn.exe).  
  
 Tato možnost se ignoruje, pokud cíl není knihovny DLL.  
  
|Chcete-li nastavit - baseaddress v integrovaném vývojovém prostředí sady Visual Studio|  
|---|  
|1.  Mají projekt vybraný v **Průzkumníka řešení**. Na **projektu** nabídky, klikněte na tlačítko **vlastnosti**. <br />2.  Klikněte na tlačítko **kompilaci** kartu.<br />3.  Klikněte na tlačítko **Advanced**.<br />4.  Upravte hodnotu v **základní adresa knihovny DLL:** pole. **Poznámka:** **základní adresa knihovny DLL:** pole je jen pro čtení, pokud cíl není knihovny DLL.|  
  
## <a name="see-also"></a>Viz také  
 [Kompilátor příkazového řádku jazyka Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)  
 [-target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)  
 [Příkazové řádky ukázkové kompilace](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [Sn.exe (nástroj pro silný název)] [Sn.exe (nástroj pro silný název)](../../../framework/tools/sn-exe-strong-name-tool.md))
