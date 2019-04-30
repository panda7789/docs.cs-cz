---
title: -nowarn
ms.date: 07/20/2015
helpviewer_keywords:
- nowarn compiler option [Visual Basic]
- /nowarn compiler option [Visual Basic]
- -nowarn compiler option [Visual Basic]
ms.assetid: 7ebf2106-0652-4fdc-bf60-70fc86465d83
ms.openlocfilehash: 31f7a2b771cfa1bcc6581d720aa0de3505aec826
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61788983"
---
# <a name="-nowarn"></a>-nowarn
Potlačí umožňuje kompilátoru generovat upozornění.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
-nowarn[:numberList]  
```  
  
## <a name="arguments"></a>Arguments  
  
|Termín|Definice|  
|---|---|  
|`numberList`|Volitelné. Čárkami oddělený seznam ID čísla upozornění, které kompilátor potlačit. Pokud nejsou zadané ID upozornění, jsou potlačeny všechny výstrahy.|  
  
## <a name="remarks"></a>Poznámky  
 `-nowarn` Možnost způsobí, že kompilátor negeneruje upozornění. Pro potlačení jednotlivých upozornění, zadejte ID upozornění `-nowarn` možnost za dvojtečkou. Více čísel upozornění oddělte čárkami.  
  
 Je třeba zadat pouze číselnou část identifikátoru upozornění. Například pokud chcete potlačit BC42024 upozornění pro nepoužívané místní proměnné, zadejte `-nowarn:42024`.  
  
 Další informace o ID čísla upozornění, najdete v části [Konfigurace upozornění v jazyce Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
|Chcete-li nastavit - nowarn v integrovaném vývojovém prostředí sady Visual Studio|  
|---|  
|1.  Mají projekt vybraný v **Průzkumníka řešení**. Na **projektu** nabídky, klikněte na tlačítko **vlastnosti**. <br />2.  Klikněte na tlačítko **kompilaci** kartu.<br />3.  Vyberte **zakázat všechna upozornění** zaškrtávací políčko Zakázat všechna upozornění.<br />     - nebo -<br />     Chcete-li zakázat konkrétní upozornění, klikněte na tlačítko **žádný** z rozevíracího seznamu vedle upozornění.|  
  
## <a name="example"></a>Příklad  
 Následující kód zkompiluje `T2.vb` a nezobrazí žádné upozornění.  
  
```console
vbc -nowarn t2.vb  
```  
  
## <a name="example"></a>Příklad  
 Následující kód zkompiluje `T2.vb` a nezobrazí upozornění pro nepoužívané místní proměnné (42024).  
  
```console
vbc -nowarn:42024 t2.vb  
```  
  
## <a name="see-also"></a>Viz také:

- [Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md)
- [Příkazové řádky ukázkové kompilace](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [Konfigurace upozornění v jazyce Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic)
