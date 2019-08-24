---
title: 'Postupy: Přehrávání zvuku z formuláře Windows Forms'
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
ms.openlocfilehash: 68a68f05b847877641132e540995f6b14bb6e065
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/24/2019
ms.locfileid: "70015804"
---
# <a name="how-to-play-a-sound-from-a-windows-form"></a>Postupy: Přehrávání zvuku z formuláře Windows Forms
Tento příklad hraje zvuk v dané cestě v době běhu.

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

- Název `"c:\Windows\Media\chimes.wav"` souboru nahradíte platným názvem souboru.

- (C#) Odkaz na <xref:System.Media?displayProperty=nameWithType> obor názvů.

## <a name="robust-programming"></a>Robustní programování
 Operace se soubory by měly být uzavřeny v odpovídajících strukturovaných blocích zpracování výjimek.

 Následující podmínky mohou způsobit výjimku:

- Název cesty je poškozen. Například obsahuje neplatné znaky nebo je pouze mezera (<xref:System.ArgumentException> třída).

- Cesta je jen pro čtení (<xref:System.IO.IOException> třída).

- Název cesty je `null` (<xref:System.ArgumentNullException> Class).

- Název cesty je příliš dlouhý (<xref:System.IO.PathTooLongException> třída).

- Cesta je neplatná (<xref:System.IO.DirectoryNotFoundException> třída).

- Cesta je pouze dvojtečka, ":" (<xref:System.NotSupportedException> třída).

## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework
 Nečiňte rozhodnutí o obsahu souboru na základě jeho názvu. Soubor `Form1.vb` nemůže být například Visual Basic zdrojový soubor. Před použitím dat ve své aplikaci ověřte všechny vstupy.

## <a name="see-also"></a>Viz také:

- <xref:System.Media.SoundPlayer>
- [Postupy: Asynchronní načítání zvuku ve formuláři Windows](how-to-load-a-sound-asynchronously-within-a-windows-form.md)
