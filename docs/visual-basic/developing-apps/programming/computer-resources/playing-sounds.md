---
title: Přehrávání zvuků (Visual Basic)
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
ms.openlocfilehash: decd845fde5bd4fad702cfe05fd63fcc180b63a6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33588455"
---
# <a name="playing-sounds-visual-basic"></a>Přehrávání zvuků (Visual Basic)
`My.Computer.Audio` Objekt poskytuje metody pro přehrávání zvuku.  
  
## <a name="playing-sounds"></a>Přehrávání zvuků  
 Přehrávání pozadí umožní aplikaci provést jiný kód, během přehrávání zvuku. `My.Computer.Audio.Play` Metoda umožňuje aplikaci přehrát zvuk pouze jeden pozadí najednou; aplikace na nové pozadí přehrává zvuk, zastaví, přehrávání zvuku předchozí pozadí. Také můžete přehrát zvuk a počkejte na její dokončení.  
  
 V následujícím příkladu `My.Computer.Audio.Play` metoda hraje zvuku. Když `AudioPlayMode.WaitToComplete` není zadaný, `My.Computer.Audio.Play` čeká, až do dokončení zvuk než volání kódu dál. Při použití v tomto příkladu, by měl zajistěte, že název souboru odkazovala na zvukový soubor ve formátu WAV, který je v počítači  
  
 [!code-vb[VbVbalrMyComputer#15](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/playing-sounds_1.vb)]  
  
 V následujícím příkladu `My.Computer.Audio.Play` metoda hraje zvuku. Při použití v tomto příkladu, ujistěte se, že prostředky aplikace obsahují zvukový soubor ve formátu WAV s názvem vodopádu.  
  
 [!code-vb[VbVbalrMyComputer#16](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/playing-sounds_2.vb)]  
  
## <a name="playing-looping-sounds"></a>Přehrávání zvuků ve smyčce  
 V následujícím příkladu `My.Computer.Audio.Play` metoda přehraje určený zvuk na pozadí při `PlayMode.BackgroundLoop` je zadán. Při použití v tomto příkladu, ujistěte se, že název souboru odkazuje na zvukový soubor ve formátu WAV, který je ve vašem počítači.  
  
 [!code-vb[VbVbalrMyComputer#11](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/playing-sounds_3.vb)]  
  
 V následujícím příkladu `My.Computer.Audio.Play` metoda přehraje určený zvuk na pozadí při `PlayMode.BackgroundLoop` je zadán. Při použití v tomto příkladu, ujistěte se, že prostředky aplikace obsahují zvukový soubor ve formátu WAV s názvem vodopádu.  
  
 [!code-vb[VbVbalrMyComputer#12](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/playing-sounds_4.vb)]  
  
 V předchozím příkladu kódu je také k dispozici jako IntelliSense fragment kódu. V Sběrač fragmentů kódu je umístěn v **aplikacích Windows Forms > Zvuk**. Další informace najdete v tématu [fragmenty kódu](/visualstudio/ide/code-snippets).  
  
 Obecně platí když aplikace přehraje opakování zvuk, měla by nakonec zastavit zvuk.  
  
## <a name="stopping-the-playing-of-sounds-in-the-background"></a>Zastavení přehrávání zvuků na pozadí  
 Použití `My.Computer.Audio.Stop` metoda zastavení aplikace aktuálně přehrávání pozadí nebo opakování ve smyčce zvuku.  
  
 Obecně platí když aplikace přehraje opakování zvuk, by se měla zastavit zvuk v určitém okamžiku.  
  
 Následující příklad zastaví zvuk, který je přehrávání na pozadí.  
  
 [!code-vb[VbVbalrMyComputer#18](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/playing-sounds_5.vb)]  
  
 V předchozím příkladu kódu je také k dispozici jako IntelliSense fragment kódu. V Sběrač fragmentů kódu je umístěn v **aplikacích Windows Forms > Zvuk**. Další informace najdete v tématu [fragmenty kódu](/visualstudio/ide/code-snippets).  
  
## <a name="playing-system-sounds"></a>Přehrávání zvuků systému  
 Použití `My.Computer.Audio.PlaySystemSound` metoda přehrát zvuk zadaný systém.  
  
 `My.Computer.Audio.PlaySystemSound` Metoda přebírá jako parametr jednoho sdíleného člena z <xref:System.Media.SystemSound> třídy. Systémového zvuku <xref:System.Media.SystemSounds.Asterisk%2A> obvykle označuje chybu.  
  
 Následující příklad používá `My.Computer.Audio.PlaySystemSound` metoda přehrát zvuk systému.  
  
 [!code-vb[VbVbalrMyComputer#17](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/playing-sounds_6.vb)]  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualBasic.Devices.Audio>  
 <xref:Microsoft.VisualBasic.Devices.Audio.Play%2A>  
 <xref:Microsoft.VisualBasic.Devices.Audio.PlaySystemSound%2A>  
 <xref:Microsoft.VisualBasic.Devices.Audio.Stop%2A>  
 <xref:Microsoft.VisualBasic.AudioPlayMode>
