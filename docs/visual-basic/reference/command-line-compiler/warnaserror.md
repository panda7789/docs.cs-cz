---
title: /warnaserror (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- warnaserror compiler option [Visual Basic]
- /warnaserror compiler option [Visual Basic]
- -warnaserror compiler option [Visual Basic]
ms.assetid: 49819f1d-a1bd-4201-affe-5afe6d9712e1
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d472795affe0df098d1551daf51a2f0ae20723ba
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="warnaserror-visual-basic"></a>/warnaserror (Visual Basic)
Způsobí, že kompilátor první výskyt upozornění považovat za chybu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/warnaserror[+ | -][:numberList]  
```  
  
## <a name="arguments"></a>Arguments  
  
|Termín|Definice|  
|---|---|  
|+ &#124; -|Volitelné. Ve výchozím nastavení `/warnaserror-` je v platnosti; upozornění nezabrání kompilátor vytvoření výstupního souboru. `/warnaserror` Možnost, která je stejná jako `/warnaserror+`, způsobí, že upozornění jsou považovány za chyby.|  
|`numberList`|Volitelné. Čárkami oddělený seznam ID upozornění čísla, ke kterému `/warnaserror` možnost se vztahuje. Pokud je zadáno žádné ID upozornění, `/warnaserror` možnost se vztahuje na všechny výstrahy.|  
  
## <a name="remarks"></a>Poznámky  
 `/warnaserror` Možnost zpracovává všech upozornění jako chyby. Všechny zprávy, které by obvykle hlášeny jako upozornění jsou hlášeny jako chyby. Kompilátor hlásí následné výskyty stejné upozornění jako upozornění.  
  
 Ve výchozím nastavení `/warnaserror-` je v platnosti, což způsobí, že upozornění být pouze informační. `/warnaserror` Možnost, která je stejná jako `/warnaserror+`, způsobí, že upozornění jsou považovány za chyby.  
  
 Pokud chcete pouze několik konkrétní upozornění jsou považovány za chyby, můžete určit seznam oddělený čárkami čísel upozornění považovat za chyby.  
  
> [!NOTE]
>  `/warnaserror` Možnost neřídí zobrazení upozornění. Použití [/nowarn](../../../visual-basic/reference/command-line-compiler/nowarn.md) možnost zakázat upozornění.  
  
|Chcete-li nastavit/warnaserror zachází všech upozornění jako chyby v prostředí Visual Studio IDE|  
|---|  
|1.  Máte projekt vybraný v **Průzkumníku řešení**. Na **projektu** nabídky, klikněte na tlačítko **vlastnosti**. <br />2.  Klikněte **zkompilovat** kartě.<br />3.  Zajistěte, aby **zakázat všech upozornění** zaškrtávací políčko je zaškrtnuté políčko.<br />4.  Zkontrolujte **zpracovává všechna upozornění jako chyby** zaškrtávací políčko.|  
  
|Chcete-li nastavit/warnaserror zacházet s konkrétní upozornění jako chyby v prostředí Visual Studio IDE|  
|---|  
|1.  Máte projekt vybraný v **Průzkumníku řešení**. Na **projektu** nabídky, klikněte na tlačítko **vlastnosti**.<br />2.  Klikněte **zkompilovat** kartě.<br />3.  Zajistěte, aby **zakázat všech upozornění** zaškrtávací políčko je zaškrtnuté políčko.<br />4.  Zajistěte, aby **zpracovává všechna upozornění jako chyby** zaškrtávací políčko je zaškrtnuté políčko.<br />5.  Vyberte **chyba** z **oznámení** sloupec přiléhající k upozornění, že by měl být považovat za chybu.|  
  
## <a name="example"></a>Příklad  
 Následující kód zkompiluje `In.vb` a přesměruje kompilátoru zobrazuje chybu pro první výskyt každé varování najde.  
  
```  
vbc /warnaserror in.vb  
```  
  
## <a name="example"></a>Příklad  
 Následující kód zkompiluje `T2.vb` a pouze upozornění pro místní proměnné (42024) považuje za chybu.  
  
```  
vbc /warnaserror:42024 t2.vb  
```  
  
## <a name="see-also"></a>Viz také  
 [Visual Basic – kompilátor příkazového řádku](../../../visual-basic/reference/command-line-compiler/index.md)  
 [Příkazové řádky ukázkové kompilace](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [Konfigurace upozornění v jazyce Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic)
