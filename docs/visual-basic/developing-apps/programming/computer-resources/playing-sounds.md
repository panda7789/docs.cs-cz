---
title: Přehrávání zvuků
ms.date: 07/20/2015
helpviewer_keywords:
- system sounds, playing
- system sounds
- playing sounds, Visual Basic
- sound loops
- My.Computer.Audio object, tasks
- sounds, playing
- sounds, background
- playing sounds
ms.assetid: f0d9e4ab-57c7-47b6-86d3-99ff07078040
ms.openlocfilehash: 416fedd011ff35d2b32d1b64932e3908a73ed14e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "74345525"
---
# <a name="playing-sounds-visual-basic"></a>Přehrávání zvuků (Visual Basic)

`My.Computer.Audio` Objekt poskytuje metody pro přehrávání zvuků.  
  
## <a name="playing-sounds"></a>Přehrávání zvuků  

 Přehrávání na pozadí umožňuje aplikaci při přehrávání zvuku provést jiný kód. `My.Computer.Audio.Play` Metoda umožňuje, aby aplikace současně hrála pouze jeden zvuk na pozadí. Když aplikace přehraje nový zvuk na pozadí, zastaví se přehrávání předchozího zvuku na pozadí. Můžete také přehrát zvuk a počkat na jeho dokončení.  
  
 V následujícím příkladu `My.Computer.Audio.Play` Metoda přehrává zvuk. Když `AudioPlayMode.WaitToComplete` je zadáno, `My.Computer.Audio.Play` počká na dokončení zvuku před pokračováním volání kódu. Při použití tohoto příkladu byste měli zkontrolovat, že název souboru odkazuje na zvukový soubor. wav, který je ve vašem počítači.  
  
 [!code-vb[VbVbalrMyComputer#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class1.vb#15)]  
  
 V následujícím příkladu `My.Computer.Audio.Play` Metoda přehrává zvuk. Při použití tohoto příkladu byste měli zajistit, aby prostředky aplikace zahrnovaly zvukový soubor. wav s názvem vodopád.  
  
 [!code-vb[VbVbalrMyComputer#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class1.vb#16)]  
  
## <a name="playing-looping-sounds"></a>Přehrávání zvukových smyček  

 V následujícím příkladu `My.Computer.Audio.Play` metoda při `PlayMode.BackgroundLoop` zadání přehraje zadaný zvuk na pozadí. Při použití tohoto příkladu byste měli zkontrolovat, že název souboru odkazuje na zvukový soubor. wav, který je ve vašem počítači.  
  
 [!code-vb[VbVbalrMyComputer#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class1.vb#11)]  
  
 V následujícím příkladu `My.Computer.Audio.Play` metoda při `PlayMode.BackgroundLoop` zadání přehraje zadaný zvuk na pozadí. Při použití tohoto příkladu byste měli zajistit, aby prostředky aplikace zahrnovaly zvukový soubor. wav s názvem vodopád.  
  
 [!code-vb[VbVbalrMyComputer#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class1.vb#12)]  
  
 Předchozí příklad kódu je také k dispozici jako fragment kódu technologie IntelliSense. Ve výběru fragmentu kódu se nachází v **model Windows Forms aplikace > zvuku**. Další informace naleznete v tématu [fragmenty kódu](/visualstudio/ide/code-snippets).  
  
 Obecně platí, že když aplikace přehraje zvuk ve smyčce, měl by nakonec zastavit zvuk.  
  
## <a name="stopping-the-playing-of-sounds-in-the-background"></a>Zastavování přehrávání zvuků na pozadí  

 Použijte `My.Computer.Audio.Stop` metodu k zastavení aktuálně přehrávaného zvuku na pozadí nebo ve smyčce.  
  
 Obecně platí, že když aplikace přehraje zvuk ve smyčce, měl by zastavit zvuk v nějakém okamžiku.  
  
 Následující příklad zastaví zvuk, který se přehrává na pozadí.  
  
 [!code-vb[VbVbalrMyComputer#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class1.vb#18)]  
  
 Předchozí příklad kódu je také k dispozici jako fragment kódu technologie IntelliSense. Ve výběru fragmentu kódu se nachází v **model Windows Forms aplikace > zvuku**. Další informace naleznete v tématu [fragmenty kódu](/visualstudio/ide/code-snippets).  
  
## <a name="playing-system-sounds"></a>Přehrávání systémových zvuků  

 Použijte `My.Computer.Audio.PlaySystemSound` metodu k přehrání zadaného systémového zvuku.  
  
 `My.Computer.Audio.PlaySystemSound` Metoda přebírá jako parametr jeden ze sdílených členů z <xref:System.Media.SystemSound> třídy. Systémový zvuk <xref:System.Media.SystemSounds.Asterisk%2A> obecně označuje chyby.  
  
 Následující příklad používá `My.Computer.Audio.PlaySystemSound` metodu k přehrání systémového zvuku.  
  
 [!code-vb[VbVbalrMyComputer#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class1.vb#17)]  
  
## <a name="see-also"></a>Viz také

- <xref:Microsoft.VisualBasic.Devices.Audio>
- <xref:Microsoft.VisualBasic.Devices.Audio.Play%2A>
- <xref:Microsoft.VisualBasic.Devices.Audio.PlaySystemSound%2A>
- <xref:Microsoft.VisualBasic.Devices.Audio.Stop%2A>
- <xref:Microsoft.VisualBasic.AudioPlayMode>
