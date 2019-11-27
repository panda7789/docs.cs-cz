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
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345525"
---
# <a name="playing-sounds-visual-basic"></a>Přehrávání zvuků (Visual Basic)

Objekt `My.Computer.Audio` poskytuje metody pro přehrávání zvuků.  
  
## <a name="playing-sounds"></a>Přehrávání zvuků  

 Přehrávání na pozadí umožňuje aplikaci při přehrávání zvuku provést jiný kód. Metoda `My.Computer.Audio.Play` umožňuje, aby aplikace současně hrála pouze jeden zvuk na pozadí. Když aplikace přehraje nový zvuk na pozadí, zastaví se přehrávání předchozího zvuku na pozadí. Můžete také přehrát zvuk a počkat na jeho dokončení.  
  
 V následujícím příkladu metoda `My.Computer.Audio.Play` přehrává zvuk. Pokud je zadána `AudioPlayMode.WaitToComplete`, `My.Computer.Audio.Play` počká, dokud se zvuk nedokončí, než pokračuje v volání kódu. Při použití tohoto příkladu byste měli zkontrolovat, že název souboru odkazuje na zvukový soubor. wav, který je ve vašem počítači.  
  
 [!code-vb[VbVbalrMyComputer#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class1.vb#15)]  
  
 V následujícím příkladu metoda `My.Computer.Audio.Play` přehrává zvuk. Při použití tohoto příkladu byste měli zajistit, aby prostředky aplikace zahrnovaly zvukový soubor. wav s názvem vodopád.  
  
 [!code-vb[VbVbalrMyComputer#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class1.vb#16)]  
  
## <a name="playing-looping-sounds"></a>Přehrávání zvukových smyček  

 V následujícím příkladu metoda `My.Computer.Audio.Play` při určení `PlayMode.BackgroundLoop` přehrává zadaný zvuk na pozadí. Při použití tohoto příkladu byste měli zkontrolovat, že název souboru odkazuje na zvukový soubor. wav, který je ve vašem počítači.  
  
 [!code-vb[VbVbalrMyComputer#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class1.vb#11)]  
  
 V následujícím příkladu metoda `My.Computer.Audio.Play` při určení `PlayMode.BackgroundLoop` přehrává zadaný zvuk na pozadí. Při použití tohoto příkladu byste měli zajistit, aby prostředky aplikace zahrnovaly zvukový soubor. wav s názvem vodopád.  
  
 [!code-vb[VbVbalrMyComputer#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class1.vb#12)]  
  
 Předchozí příklad kódu je také k dispozici jako fragment kódu technologie IntelliSense. Ve výběru fragmentu kódu se nachází v **model Windows Forms aplikace > zvuku**. Další informace naleznete v tématu [fragmenty kódu](/visualstudio/ide/code-snippets).  
  
 Obecně platí, že když aplikace přehraje zvuk ve smyčce, měl by nakonec zastavit zvuk.  
  
## <a name="stopping-the-playing-of-sounds-in-the-background"></a>Zastavování přehrávání zvuků na pozadí  

 Pomocí metody `My.Computer.Audio.Stop` zastavte aktuálně přehrávání zvuku na pozadí nebo ve smyčce.  
  
 Obecně platí, že když aplikace přehraje zvuk ve smyčce, měl by zastavit zvuk v nějakém okamžiku.  
  
 Následující příklad zastaví zvuk, který se přehrává na pozadí.  
  
 [!code-vb[VbVbalrMyComputer#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class1.vb#18)]  
  
 Předchozí příklad kódu je také k dispozici jako fragment kódu technologie IntelliSense. Ve výběru fragmentu kódu se nachází v **model Windows Forms aplikace > zvuku**. Další informace naleznete v tématu [fragmenty kódu](/visualstudio/ide/code-snippets).  
  
## <a name="playing-system-sounds"></a>Přehrávání systémových zvuků  

 K přehrání zadaného systémového zvuku použijte metodu `My.Computer.Audio.PlaySystemSound`.  
  
 Metoda `My.Computer.Audio.PlaySystemSound` přebírá jako parametr jeden ze sdílených členů z třídy <xref:System.Media.SystemSound>. Systémový zvukový <xref:System.Media.SystemSounds.Asterisk%2A> obecně označuje chyby.  
  
 Následující příklad používá metodu `My.Computer.Audio.PlaySystemSound` k přehrání systémového zvuku.  
  
 [!code-vb[VbVbalrMyComputer#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class1.vb#17)]  
  
## <a name="see-also"></a>Viz také:

- <xref:Microsoft.VisualBasic.Devices.Audio>
- <xref:Microsoft.VisualBasic.Devices.Audio.Play%2A>
- <xref:Microsoft.VisualBasic.Devices.Audio.PlaySystemSound%2A>
- <xref:Microsoft.VisualBasic.Devices.Audio.Stop%2A>
- <xref:Microsoft.VisualBasic.AudioPlayMode>
