---
title: 'Postupy: Opakované přehrávání zvuku ve formuláři Windows'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- sound loops
- SoundPlayer class [Windows Forms], play looping
- sounds [Windows Forms], looping
- playing sounds [Windows Forms], looping
ms.assetid: ea95dd46-10a3-46c0-8263-4b205f00df7f
caps.latest.revision: 17
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: a88bf4b9dc84af8c6e81167c989943754f64b7d8
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/27/2018
---
# <a name="how-to-loop-a-sound-playing-on-a-windows-form"></a>Postupy: Opakované přehrávání zvuku ve formuláři Windows
Následující příklad kódu opakovaného hraje zvuku. Když kód v `stopPlayingButton_Click` spuštění obslužné rutiny události, zvuk, který se aktuálně přehrávání zastaví. Pokud žádné přehrávání zvuku, nedojde k žádné akci.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[System.Media.SoundPlayer.PlayLooping#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Media.SoundPlayer.PlayLooping/CS/Form1.cs#1)]
 [!code-vb[System.Media.SoundPlayer.PlayLooping#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Media.SoundPlayer.PlayLooping/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
-   Odkazy na systém a System.Windows.Forms sestavení.  
  
-   Nahradit název souboru `"c:\Windows\Media\chimes.wav"` s platný název souboru.  
  
 Informace o vytváření tento příklad z příkazového řádku pro visual Basic a Visual C# najdete v tématu [sestavení z příkazového řádku](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) nebo [vytváření pomocí příkazového řádku csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Tento příklad v sadě Visual Studio můžete také vytvořit zadáním nebo vložením kódu do nového projektu.  Viz také [postupy: zkompilování a spuštění dokončení Windows Forms kód příklad pomocí sady Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="robust-programming"></a>Robustní programování  
 Operace se soubory by měl být uzavřena v příslušné bloky zpracování výjimek.  
  
 Následující podmínky mohou způsobit výjimku:  
  
-   Název cesty je chybný. Například obsahuje znaky, které nejsou platné nebo je pouze mezera (<xref:System.ArgumentException> třídy).  
  
-   Cesta je jen pro čtení (<xref:System.IO.IOException> třídy).  
  
-   Název cesty je `Nothing` (<xref:System.ArgumentNullException> třídy).  
  
-   Cesta je příliš dlouhý (<xref:System.IO.PathTooLongException> třídy).  
  
-   Cesta je neplatná (<xref:System.IO.DirectoryNotFoundException> třídy).  
  
-   Cesta je pouze dvojtečka ":" (<xref:System.NotSupportedException> třídy).  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  
 Nečiňte rozhodnutí o obsahu souboru na základě jeho názvu. Například soubor Form1.vb nemusí být zdrojový soubor jazyka Visual Basic. Před použitím dat ve své aplikaci ověřte všechny vstupy.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Media.SoundPlayer.PlayLooping%2A>  
 [Postupy: Přehrávání zvuku z formuláře Windows Forms](../../../../docs/framework/winforms/controls/how-to-play-a-sound-from-a-windows-form.md)  
 [Přehled třídy SoundPlayer](../../../../docs/framework/winforms/controls/soundplayer-class-overview.md)
