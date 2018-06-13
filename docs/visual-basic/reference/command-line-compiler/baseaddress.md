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
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33650147"
---
# <a name="-baseaddress"></a>-baseaddress
Určuje výchozí základní adresu při vytváření knihovny DLL.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
-baseaddress:address  
```  
  
## <a name="arguments"></a>Arguments  
  
|Termín|Definice|  
|---|---|  
|`address`|Požadováno. Základní adresa pro knihovnu DLL. Tato adresa musí být zadán jako o hexadecimální číslo.|  
  
## <a name="remarks"></a>Poznámky  
 Výchozí základní adresy knihovny DLL se nastavuje pomocí [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].  
  
 Upozorňujeme, že se zaokrouhlí na slovo nižší pořadí v tuto adresu. Například pokud zadáte 0x11110001, je zaokrouhlen 0x11110000.  
  
 Chcete-li dokončit proces podepisování pro knihovny DLL, použijte `–R` – možnost nástroje silné názvy (Sn.exe).  
  
 Tato možnost je ignorována, pokud cíl není knihovny DLL.  
  
|Chcete-li nastavit - baseaddress v integrovaném vývojovém prostředí sady Visual Studio|  
|---|  
|1.  Máte projekt vybraný v **Průzkumníku řešení**. Na **projektu** nabídky, klikněte na tlačítko **vlastnosti**. <br />2.  Klikněte **zkompilovat** kartě.<br />3.  Klikněte na tlačítko **rozšířené**.<br />4.  Změňte hodnotu v **základní adresy knihovny DLL:** pole. **Poznámka:** **základní adresy knihovny DLL:** pole je jen pro čtení, není-li cílem knihovny DLL.|  
  
## <a name="see-also"></a>Viz také  
 [Visual Basic – kompilátor příkazového řádku](../../../visual-basic/reference/command-line-compiler/index.md)  
 [-target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)  
 [Příkazové řádky ukázkové kompilace](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [Sn.exe (nástroj pro silný název)] [Sn.exe (nástroj pro silný název)](../../../framework/tools/sn-exe-strong-name-tool.md))
