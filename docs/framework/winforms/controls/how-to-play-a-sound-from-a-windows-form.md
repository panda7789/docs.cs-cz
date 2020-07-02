---
title: 'Postupy: Přehrávání zvuku z formuláře Windows'
description: Přečtěte si, jak přehrát zvuk z formuláře Windows v dané cestě za běhu. Přečtěte si také informace o kompilování kódu a rozhraní .NET Security Framework.
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
ms.openlocfilehash: beb17d994e224f41b2b590ecb1401988cdad314d
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85613745"
---
# <a name="how-to-play-a-sound-from-a-windows-form"></a>Postupy: Přehrávání zvuku z formuláře Windows
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

- Název souboru nahradíte `"c:\Windows\Media\chimes.wav"` platným názvem souboru.

- Jazyk Odkaz na <xref:System.Media?displayProperty=nameWithType> obor názvů.

## <a name="robust-programming"></a>Robustní programování
 Operace se soubory by měly být uzavřeny v odpovídajících strukturovaných blocích zpracování výjimek.

 Následující podmínky mohou způsobit výjimku:

- Název cesty je poškozen. Například obsahuje neplatné znaky nebo je pouze mezera ( <xref:System.ArgumentException> třída).

- Cesta je jen pro čtení ( <xref:System.IO.IOException> třída).

- Název cesty je `null` ( <xref:System.ArgumentNullException> Class).

- Název cesty je příliš dlouhý ( <xref:System.IO.PathTooLongException> třída).

- Cesta je neplatná ( <xref:System.IO.DirectoryNotFoundException> třída).

- Cesta je pouze dvojtečka, ":" ( <xref:System.NotSupportedException> třída).

## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework
 Nečiňte rozhodnutí o obsahu souboru na základě jeho názvu. Soubor nemůže `Form1.vb` být například Visual Basic zdrojový soubor. Před použitím dat ve své aplikaci ověřte všechny vstupy.

## <a name="see-also"></a>Viz také:

- <xref:System.Media.SoundPlayer>
- [Postupy: Asynchronní načítání zvuku ve formuláři Windows Forms](how-to-load-a-sound-asynchronously-within-a-windows-form.md)
