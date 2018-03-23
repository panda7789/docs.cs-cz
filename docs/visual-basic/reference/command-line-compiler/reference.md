---
title: -reference (Visual Basic)
ms.date: 03/13/2018
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
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
ms.openlocfilehash: ba879dd7079b35bea50c4a6c1d67da7aa57110f6
ms.sourcegitcommit: 498799639937c89de777361aab74261efe7b79ea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/22/2018
---
# <a name="-reference-visual-basic"></a>-reference (Visual Basic)
Způsobí, že kompilátor zpřístupnění informací o typu v zadaném sestavení do projektu, které jsou aktuálně kompilace.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
-reference:fileList  
' -or-  
-r:fileList  
```  
  
## <a name="arguments"></a>Arguments  
  
|Termín|Definice|  
|---|---|  
|`fileList`|Požadováno. Čárkami oddělený seznam názvů souborů sestavení. Pokud název souboru obsahuje mezery, uzavřete název v uvozovkách.|  
  
## <a name="remarks"></a>Poznámky  
 Soubory, které importujete musí obsahovat metadata sestavení. Pouze veřejné typy jsou viditelné mimo sestavení. [/Addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md) možnost Importuje metadata z modulu.  
  
 Pokud odkazujete na sestavení (sestavení A) které se odkazuje na sestavení (sestavení B), budete muset odkaz na sestavení B, pokud:  
  
-   Typu ze sestavení A dědí z typu nebo implementuje rozhraní ze sestavení B.  
  
-   Pole, vlastnost, události nebo metodu, která má návratový typ nebo parametr typu ze sestavení B je volána.  
  
 Použití [- libpath](../../../visual-basic/reference/command-line-compiler/libpath.md) na adresář, ve kterém se nachází jeden nebo více odkazů na sestavení.  
  
 Kompilátor rozpoznat typu v sestavení (není modul) musí být vynutit pro vyřešení typu. Jeden příklad, jak můžete k tomu je k definování instance typu. Další způsoby jsou k dispozici pro překlad názvů typu v sestavení pro kompilátor. Například pokud jste dědí od typu v sestavení, název typu pak určen kompilátoru.  
  
 Soubor odpovědí Vbc.rsp, jehož odkazy běžně používají [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] sestavení, se používá ve výchozím nastavení. Použít `-noconfig` Pokud nechcete, aby kompilátor používal Vbc.rsp.  
  
 Zkratka pro `-reference` je `/r`.  
  
## <a name="example"></a>Příklad  
 Následující příkaz zkompiluje zdrojový soubor `Input.vb` a odkaz na sestavení z `Metad1.dll` a `Metad2.dll` k vytvoření `Out.exe`.  
  
```console
vbc -reference:metad1.dll,metad2.dll -out:out.exe input.vb  
```  
  
## <a name="see-also"></a>Viz také  
 [Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md)  
 [-noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md)  
 [-target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)  
 [Public](../../../visual-basic/language-reference/modifiers/public.md)  
 [Příkazové řádky ukázkové kompilace](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
