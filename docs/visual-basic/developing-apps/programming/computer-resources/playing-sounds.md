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
ms.openlocfilehash: f303687fb86e23191727df769af52811a93fe71e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54715787"
---
# <a name="playing-sounds-visual-basic"></a>Přehrávání zvuků (Visual Basic)
`My.Computer.Audio` Objekt, který poskytuje metody pro přehrávání zvuku.  
  
## <a name="playing-sounds"></a>Přehrávání zvuků  
 Přehrávání na pozadí umožňuje aplikaci spustit další kód během přehrávání zvuku. `My.Computer.Audio.Play` Metody umožňuje, aby aplikace k přehrání zvuku pozadí pouze jeden po druhém, když aplikace přehraje zvuk nové na pozadí, zastaví přehrávání zvuku na pozadí předchozí. Můžete přehrát zvuk a počkejte na její dokončení.  
  
 V následujícím příkladu `My.Computer.Audio.Play` metoda přehraje zvuk. Když `AudioPlayMode.WaitToComplete` není zadána, `My.Computer.Audio.Play` počká, dokud nebudou zvuk až po dokončení předchozího volání kódu pokračuje. Při použití v tomto příkladu, měli byste zajistit, že název souboru odkazuje na WAV zvukový soubor, který je v počítači  
  
 [!code-vb[VbVbalrMyComputer#15](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/playing-sounds_1.vb)]  
  
 V následujícím příkladu `My.Computer.Audio.Play` metoda přehraje zvuk. Při použití v tomto příkladu, měli byste zajistit, že prostředky aplikace obsahují WAV zvukový soubor, který je pojmenován vodopádu.  
  
 [!code-vb[VbVbalrMyComputer#16](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/playing-sounds_2.vb)]  
  
## <a name="playing-looping-sounds"></a>Přehrávání zvuků opakování ve smyčce  
 V následujícím příkladu `My.Computer.Audio.Play` metoda přehraje zvuk zadaný na pozadí při `PlayMode.BackgroundLoop` je zadán. Při použití v tomto příkladu, měli byste zajistit, že název souboru odkazuje na WAV zvukový soubor, který je ve vašem počítači.  
  
 [!code-vb[VbVbalrMyComputer#11](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/playing-sounds_3.vb)]  
  
 V následujícím příkladu `My.Computer.Audio.Play` metoda přehraje zvuk zadaný na pozadí při `PlayMode.BackgroundLoop` je zadán. Při použití v tomto příkladu, měli byste zajistit, že prostředky aplikace obsahují WAV zvukový soubor, který je pojmenován vodopádu.  
  
 [!code-vb[VbVbalrMyComputer#12](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/playing-sounds_4.vb)]  
  
 V předchozím příkladu kódu je také dostupný jako fragment kódu technologie IntelliSense. V dialogu pro výběr fragmentu kódu je umístěn v **formulářových aplikací Windows > Zvuk**. Další informace najdete v tématu [fragmenty kódu](/visualstudio/ide/code-snippets).  
  
 Obecně platí když aplikace přehrává ve smyčce zvuk, měla by nakonec zastavit zvuk.  
  
## <a name="stopping-the-playing-of-sounds-in-the-background"></a>Zastavení přehrávání zvuků na pozadí  
 Použití `My.Computer.Audio.Stop` metoda zastavení aplikace přehrávaný na pozadí nebo opakování ve smyčce zvuk.  
  
 Obecně platí když aplikace přehrává ve smyčce zvuk, by se měla zastavit zvuk v určitém okamžiku.  
  
 Následující příklad zastaví zvuk, který je přehrávání na pozadí.  
  
 [!code-vb[VbVbalrMyComputer#18](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/playing-sounds_5.vb)]  
  
 V předchozím příkladu kódu je také dostupný jako fragment kódu technologie IntelliSense. V dialogu pro výběr fragmentu kódu je umístěn v **formulářových aplikací Windows > Zvuk**. Další informace najdete v tématu [fragmenty kódu](/visualstudio/ide/code-snippets).  
  
## <a name="playing-system-sounds"></a>Přehrávání zvuků systému  
 Použití `My.Computer.Audio.PlaySystemSound` metodu pro zadaný systém přehrávat zvuk.  
  
 `My.Computer.Audio.PlaySystemSound` Metoda přebírá jako parametr jeden sdílené členy z <xref:System.Media.SystemSound> třídy. Systémového zvuku <xref:System.Media.SystemSounds.Asterisk%2A> obvykle označuje chybu.  
  
 V následujícím příkladu `My.Computer.Audio.PlaySystemSound` metoda přehrát zvuk systému.  
  
 [!code-vb[VbVbalrMyComputer#17](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/playing-sounds_6.vb)]  
  
## <a name="see-also"></a>Viz také:
- <xref:Microsoft.VisualBasic.Devices.Audio>
- <xref:Microsoft.VisualBasic.Devices.Audio.Play%2A>
- <xref:Microsoft.VisualBasic.Devices.Audio.PlaySystemSound%2A>
- <xref:Microsoft.VisualBasic.Devices.Audio.Stop%2A>
- <xref:Microsoft.VisualBasic.AudioPlayMode>
