---
title: "Postupy: Přehrávání zvuku z formuláře Windows"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- playing sounds [Windows Forms], Windows Forms
- sounds [Windows Forms], playing
- sounds
- My.Computer.Audio object [Windows Forms], playing sounds
- examples [Windows Forms], sounds
ms.assetid: 3d3350b7-1ebd-4e05-a738-48ca1160a19d
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3ed5335108e010ed61d8a96e3169353133e9ddd0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-play-a-sound-from-a-windows-form"></a>Postupy: Přehrávání zvuku z formuláře Windows
Tento příklad hraje zvuk, který v dané cestě za běhu.  
  
## <a name="example"></a>Příklad  
  
```vb  
Sub PlaySimpleSound()  
    My.Computer.Audio.Play("c:\Windows\Media\chimes.wav")  
End Sub  
```  
  
```csharp  
private void playSimpleSound()  
{  
    SoundPlayer simpleSound = new SoundPlayer(@"c:\Windows\Media\chimes.wav");  
    simpleSound.Play();  
}  
```  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
-   Nahradit název souboru `"c:\Windows\Media\chimes.wav"` s platný název souboru.  
  
-   (C#) Odkaz na <xref:System.Media?displayProperty=nameWithType> oboru názvů.  
  
## <a name="robust-programming"></a>Robustní programování  
 Operace se soubory by měl být uzavřen odpovídající strukturovaného zpracování bloky výjimek.  
  
 Následující podmínky mohou způsobit výjimku:  
  
-   Název cesty je chybný. Například obsahuje neplatné znaky nebo je pouze mezera (<xref:System.ArgumentException> třídy).  
  
-   Cesta je jen pro čtení (<xref:System.IO.IOException> třídy).  
  
-   Název cesty je `null` (<xref:System.ArgumentNullException> třídy).  
  
-   Cesta je příliš dlouhý (<xref:System.IO.PathTooLongException> třídy).  
  
-   Cesta je neplatná (<xref:System.IO.DirectoryNotFoundException> třídy).  
  
-   Cesta je pouze středník ":" (<xref:System.NotSupportedException> třídy).  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  
 Nečiňte rozhodnutí o obsahu souboru na základě jeho názvu. Například soubor `Form1.vb` nemusí být zdrojový soubor jazyka Visual Basic. Před použitím dat ve své aplikaci ověřte všechny vstupy.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Media.SoundPlayer>  
 [Postupy: načítání zvuku asynchronně ve formuláři Windows](../../../../docs/framework/winforms/controls/how-to-load-a-sound-asynchronously-within-a-windows-form.md)  
 
