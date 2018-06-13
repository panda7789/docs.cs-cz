---
title: 'Postupy: Přehrávání zvuku z formuláře Windows'
ms.date: 03/30/2017
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
ms.openlocfilehash: 853d0f78b4f6dba2dc84109270f79f4b010c27b4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33533517"
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
 [Postupy: Asynchronní načítání zvuku ve formuláři Windows Forms](../../../../docs/framework/winforms/controls/how-to-load-a-sound-asynchronously-within-a-windows-form.md)  
 
