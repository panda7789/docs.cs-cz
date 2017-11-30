---
title: /reference (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- /reference compiler option [Visual Basic]
- r compiler option [Visual Basic]
- -reference compiler option [Visual Basic]
- /r compiler option [Visual Basic]
- reference compiler option [Visual Basic]
- -r compiler option [Visual Basic]
ms.assetid: 66bdfced-bbf6-43d1-a554-bc0990315737
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: f8c6851802afa818cc80b3f6d7eafc2ef47ac689
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="reference-visual-basic"></a>/reference (Visual Basic)
Způsobí, že kompilátor zpřístupnění informací o typu v zadaném sestavení do projektu, které jsou aktuálně kompilace.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/reference:fileList  
' -or-  
/r:fileList  
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
  
 Použití [/Libpath](../../../visual-basic/reference/command-line-compiler/libpath.md) na adresář, ve kterém se nachází jeden nebo více odkazů na sestavení.  
  
 Kompilátor rozpoznat typu v sestavení (není modul) musí být vynutit pro vyřešení typu. Jeden příklad, jak můžete k tomu je k definování instance typu. Další způsoby jsou k dispozici pro překlad názvů typu v sestavení pro kompilátor. Například pokud jste dědí od typu v sestavení, název typu pak určen kompilátoru.  
  
 Soubor odpovědí Vbc.rsp, jehož odkazy běžně používají [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] sestavení, se používá ve výchozím nastavení. Použít `/noconfig` Pokud nechcete, aby kompilátor používal Vbc.rsp.  
  
 Zkratka pro `/reference` je `/r`.  
  
## <a name="example"></a>Příklad  
 Následující kód zkompiluje zdrojový soubor `Input.vb` a odkaz na sestavení z `Metad1.dll` a `Metad2.dll` k vytvoření `Out.exe`.  
  
```  
vbc /reference:metad1.dll,metad2.dll /out:out.exe input.vb  
```  
  
## <a name="see-also"></a>Viz také  
 [Visual Basic – kompilátor příkazového řádku](../../../visual-basic/reference/command-line-compiler/index.md)  
 [/ noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md)  
 [/ target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)  
 [Veřejné](../../../visual-basic/language-reference/modifiers/public.md)  
 [Příkazové řádky ukázkové kompilace](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
