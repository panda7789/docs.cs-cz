---
title: – referenční dokumentace (Visual Basic)
ms.date: 03/13/2018
helpviewer_keywords:
- /reference compiler option [Visual Basic]
- r compiler option [Visual Basic]
- -reference compiler option [Visual Basic]
- /r compiler option [Visual Basic]
- reference compiler option [Visual Basic]
- -r compiler option [Visual Basic]
ms.assetid: 66bdfced-bbf6-43d1-a554-bc0990315737
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cb5d3b4c50a9c22880bdcc8406835cf51481e3cd
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2018
ms.locfileid: "43003122"
---
# <a name="-reference-visual-basic"></a>– referenční dokumentace (Visual Basic)
Způsobí, že kompilátor pro zpřístupnění informací o typu v zadaném sestavení pro projekt, který je aktuálně kompilován.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
-reference:fileList  
' -or-  
-r:fileList  
```  
  
## <a name="arguments"></a>Arguments  
  
|Termín|Definice|  
|---|---|  
|`fileList`|Požadováno. Čárkami oddělený seznam názvů souborů sestavení. Pokud název souboru obsahuje mezery, uzavřete název do uvozovek.|  
  
## <a name="remarks"></a>Poznámky  
 Soubory, které importujete musí obsahovat metadata sestavení. Pouze veřejné typy jsou viditelné mimo sestavení. [/Addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md) možnost Importuje metadata z modulu.  
  
 Pokud odkazujete na sestavení (sestavení A) která sama odkazuje na jiné sestavení (sestavení B), budete muset odkaz na sestavení B, pokud:  
  
-   Typ v sestavení A je odvozen z typu nebo implementuje rozhraní ze sestavení B.  
  
-   Pole, vlastnosti, události nebo metodu, která má návratový typ nebo parametr typu ze sestavení B je vyvolána.  
  
 Použití [- libpath](../../../visual-basic/reference/command-line-compiler/libpath.md) určit adresář, ve kterém se nachází jeden nebo více odkazů na sestavení.  
  
 Kompilátor rozpoznával typ v sestavení (ne modul) musíte jej donutit k přeložení typu. K definování instance typu je jeden příklad, jak to udělat. Další možnosti jsou k dispozici přeložení názvů typů v sestavení pro kompilátor. Například pokud je zděděn z typu v sestavení, název typu pak stane pro kompilátor známým.  
  
 Soubor Vbc.rsp odpovědi, kterými se běžně používá odkazy [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] sestavení, se používá ve výchozím nastavení. Použít `-noconfig` Pokud nechcete, aby kompilátor používal Vbc.rsp.  
  
 Krátký tvar `-reference` je `/r`.  
  
## <a name="example"></a>Příklad  
 Následující příkaz zkompiluje zdrojový soubor `Input.vb` a odkaz na sestavení z `Metad1.dll` a `Metad2.dll` k vytvoření `Out.exe`.  
  
```console
vbc -reference:metad1.dll,metad2.dll -out:out.exe input.vb  
```  
  
## <a name="see-also"></a>Viz také  
 [Kompilátor příkazového řádku jazyka Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)  
 [-noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md)  
 [-target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)  
 [Public](../../../visual-basic/language-reference/modifiers/public.md)  
 [Příkazové řádky ukázkové kompilace](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
