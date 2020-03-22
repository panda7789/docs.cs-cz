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

Objekt `My.Computer.Audio` poskytuje metody pro přehrávání zvuků.  
  
## <a name="playing-sounds"></a>Přehrávání zvuků  

 Přehrávání na pozadí umožňuje aplikaci spustit jiný kód, zatímco zvuk hraje. Metoda `My.Computer.Audio.Play` umožňuje aplikaci přehrávat pouze jeden zvuk na pozadí najednou; když aplikace přehraje nový zvuk na pozadí, přestane přehrávat předchozí zvuk na pozadí. Můžete také přehrát zvuk a počkat na jeho dokončení.  
  
 V následujícím příkladu `My.Computer.Audio.Play` metoda přehraje zvuk. Pokud `AudioPlayMode.WaitToComplete` je `My.Computer.Audio.Play` zadán, čeká na dokončení zvuku před pokračováním volání kódu. Při použití tohoto příkladu byste měli zajistit, aby název souboru odkazoval na zvukový soubor WAV, který je v počítači  
  
 [!code-vb[VbVbalrMyComputer#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class1.vb#15)]  
  
 V následujícím příkladu `My.Computer.Audio.Play` metoda přehraje zvuk. Při použití tohoto příkladu byste měli zajistit, aby prostředky aplikace obsahovaly zvukový soubor WAV s názvem Waterfall.  
  
 [!code-vb[VbVbalrMyComputer#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class1.vb#16)]  
  
## <a name="playing-looping-sounds"></a>Přehrávání zvuků smyčky  

 V následujícím příkladu `My.Computer.Audio.Play` metoda přehraje zadaný `PlayMode.BackgroundLoop` zvuk na pozadí, když je zadán. Při použití tohoto příkladu byste měli zajistit, aby název souboru odkazoval na zvukový soubor WAV, který je v počítači.  
  
 [!code-vb[VbVbalrMyComputer#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class1.vb#11)]  
  
 V následujícím příkladu `My.Computer.Audio.Play` metoda přehraje zadaný `PlayMode.BackgroundLoop` zvuk na pozadí, když je zadán. Při použití tohoto příkladu byste měli zajistit, aby prostředky aplikace obsahovaly zvukový soubor WAV s názvem Waterfall.  
  
 [!code-vb[VbVbalrMyComputer#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class1.vb#12)]  
  
 Předchozí příklad kódu je také k dispozici jako fragment kódu IntelliSense. Ve výběru fragmentu kódu je umístěn v **aplikacích Windows Forms > Sound**. Další informace naleznete v [tématu Fragmenty kódu](/visualstudio/ide/code-snippets).  
  
 Obecně platí, že když aplikace přehrává zvuk opakování, měla by nakonec zvuk zastavit.  
  
## <a name="stopping-the-playing-of-sounds-in-the-background"></a>Zastavení přehrávání zvuků na pozadí  

 Pomocí `My.Computer.Audio.Stop` této metody můžete zastavit aktuálně přehrávaný zvuk aplikace nebo zvuk opakování.  
  
 Obecně platí, že když aplikace přehrává zvuk opakování, měla by v určitém okamžiku zvuk zastavit.  
  
 Následující příklad zastaví zvuk, který se přehrává na pozadí.  
  
 [!code-vb[VbVbalrMyComputer#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class1.vb#18)]  
  
 Předchozí příklad kódu je také k dispozici jako fragment kódu IntelliSense. Ve výběru fragmentu kódu je umístěn v **aplikacích Windows Forms > Sound**. Další informace naleznete v [tématu Fragmenty kódu](/visualstudio/ide/code-snippets).  
  
## <a name="playing-system-sounds"></a>Přehrávání systémových zvuků  

 Pomocí `My.Computer.Audio.PlaySystemSound` této metody přehrajte zadaný systémový zvuk.  
  
 Metoda `My.Computer.Audio.PlaySystemSound` bere jako parametr jeden ze sdílených členů z třídy. <xref:System.Media.SystemSound> Systémový <xref:System.Media.SystemSounds.Asterisk%2A> zvuk obecně označuje chyby.  
  
 Následující příklad používá `My.Computer.Audio.PlaySystemSound` metodu k přehrávání systémového zvuku.  
  
 [!code-vb[VbVbalrMyComputer#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class1.vb#17)]  
  
## <a name="see-also"></a>Viz také

- <xref:Microsoft.VisualBasic.Devices.Audio>
- <xref:Microsoft.VisualBasic.Devices.Audio.Play%2A>
- <xref:Microsoft.VisualBasic.Devices.Audio.PlaySystemSound%2A>
- <xref:Microsoft.VisualBasic.Devices.Audio.Stop%2A>
- <xref:Microsoft.VisualBasic.AudioPlayMode>
