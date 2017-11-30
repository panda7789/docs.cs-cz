---
title: /nowarn
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- nowarn compiler option [Visual Basic]
- /nowarn compiler option [Visual Basic]
- -nowarn compiler option [Visual Basic]
ms.assetid: 7ebf2106-0652-4fdc-bf60-70fc86465d83
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 8da27ea2f9f0a4d370928d70cda1a796b822d97c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="nowarn"></a>/nowarn
Potlačí schopnost kompilátoru generovat upozornění.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/nowarn[:numberList]  
```  
  
## <a name="arguments"></a>Arguments  
  
|Termín|Definice|  
|---|---|  
|`numberList`|Volitelné. Čárkami oddělený seznam ID čísla upozornění, která by měla potlačit kompilátoru. Pokud nejsou zadané ID upozornění, jsou potlačovány všech upozornění.|  
  
## <a name="remarks"></a>Poznámky  
 `/nowarn` Způsobí, že kompilátor negeneruje upozornění. Chcete-li potlačit jednotlivých upozornění, zadat ID upozornění na `/nowarn` možnost za dvojtečkou. Více čísel upozornění oddělujte čárkami.  
  
 Je třeba zadat pouze číselnou část identifikátor upozornění. Například pokud chcete potlačit BC42024 upozornění pro místní proměnné, zadejte `/nowarn:42024`.  
  
 Další informace o čísla ID upozornění najdete v tématu [Konfigurace upozornění v jazyce Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
|Chcete-li nastavit/nowarn v sadě Visual Studio integrované vývojové prostředí|  
|---|  
|1.  Máte projekt vybraný v **Průzkumníku řešení**. Na **projektu** nabídky, klikněte na tlačítko **vlastnosti**. Další informace najdete v tématu [Úvod do Návrhář projektu](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).<br />2.  Klikněte **zkompilovat** kartě.<br />3.  Vyberte **zakázat všech upozornění** zaškrtávací políčko Zakázat všech upozornění.<br />     - nebo -<br />     Chcete-li zakázat konkrétní upozornění, klikněte na tlačítko **žádné** v rozevíracím seznamu přiléhající k upozornění.|  
  
## <a name="example"></a>Příklad  
 Následující kód zkompiluje `T2.vb` a nezobrazí žádné upozornění.  
  
```  
vbc /nowarn t2.vb  
```  
  
## <a name="example"></a>Příklad  
 Následující kód zkompiluje `T2.vb` a nezobrazí upozornění pro místní proměnné (42024).  
  
```  
vbc /nowarn:42024 t2.vb  
```  
  
## <a name="see-also"></a>Viz také  
 [Visual Basic – kompilátor příkazového řádku](../../../visual-basic/reference/command-line-compiler/index.md)  
 [Příkazové řádky ukázkové kompilace](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [Konfigurace upozornění v jazyce Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic)
