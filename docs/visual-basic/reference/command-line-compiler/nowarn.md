---
title: -nowarn
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- nowarn compiler option [Visual Basic]
- /nowarn compiler option [Visual Basic]
- -nowarn compiler option [Visual Basic]
ms.assetid: 7ebf2106-0652-4fdc-bf60-70fc86465d83
caps.latest.revision: ''
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d2f3f15ef12b24b8baedc9db59e772aa9eb073bc
ms.sourcegitcommit: 498799639937c89de777361aab74261efe7b79ea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/22/2018
---
# <a name="-nowarn"></a>-nowarn
Potlačí schopnost kompilátoru generovat upozornění.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
-nowarn[:numberList]  
```  
  
## <a name="arguments"></a>Arguments  
  
|Termín|Definice|  
|---|---|  
|`numberList`|Volitelné. Čárkami oddělený seznam ID čísla upozornění, která by měla potlačit kompilátoru. Pokud nejsou zadané ID upozornění, jsou potlačovány všech upozornění.|  
  
## <a name="remarks"></a>Poznámky  
 `-nowarn` Způsobí, že kompilátor negeneruje upozornění. Chcete-li potlačit jednotlivých upozornění, zadat ID upozornění na `-nowarn` možnost za dvojtečkou. Více čísel upozornění oddělujte čárkami.  
  
 Je třeba zadat pouze číselnou část identifikátor upozornění. Například pokud chcete potlačit BC42024 upozornění pro místní proměnné, zadejte `-nowarn:42024`.  
  
 Další informace o čísla ID upozornění najdete v tématu [Konfigurace upozornění v jazyce Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
|Chcete-li nastavit - nowarn v integrovaném vývojovém prostředí sady Visual Studio|  
|---|  
|1.  Máte projekt vybraný v **Průzkumníku řešení**. Na **projektu** nabídky, klikněte na tlačítko **vlastnosti**. <br />2.  Klikněte **zkompilovat** kartě.<br />3.  Vyberte **zakázat všech upozornění** zaškrtávací políčko Zakázat všech upozornění.<br />     - nebo -<br />     Chcete-li zakázat konkrétní upozornění, klikněte na tlačítko **žádné** v rozevíracím seznamu přiléhající k upozornění.|  
  
## <a name="example"></a>Příklad  
 Následující kód zkompiluje `T2.vb` a nezobrazí žádné upozornění.  
  
```console
vbc -nowarn t2.vb  
```  
  
## <a name="example"></a>Příklad  
 Následující kód zkompiluje `T2.vb` a nezobrazí upozornění pro místní proměnné (42024).  
  
```console
vbc -nowarn:42024 t2.vb  
```  
  
## <a name="see-also"></a>Viz také  
 [Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md)  
 [Příkazové řádky ukázkové kompilace](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [Konfigurace upozornění v jazyce Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic)
