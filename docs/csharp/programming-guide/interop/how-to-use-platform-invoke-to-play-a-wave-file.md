---
title: 'Postupy: použití vyvolání platformy pro přehrání souboru Wave – C# Průvodce programováním'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- platform invoke, sound files
- interoperability [C#], playing WAV files using pinvoke
- wav files
- .wav files
ms.assetid: f7f62f53-e026-4c40-b221-3a26adb0c2c5
ms.openlocfilehash: 6c2313f7b600bc1670c944f6a93868c1bc4c7c16
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/29/2019
ms.locfileid: "73039330"
---
# <a name="how-to-use-platform-invoke-to-play-a-wave-file-c-programming-guide"></a>Postupy: Použití vyvolání platformy pro přehrání souboru wave (Průvodce programováním v C#)

Následující C# příklad kódu ukazuje, jak použít služby vyvolání platformy k přehrání zvukového souboru Wave v operačním systému Windows.

## <a name="example"></a>Příklad

Tento příklad kódu používá <xref:System.Runtime.InteropServices.DllImportAttribute> k importu vstupního bodu `PlaySound` metody `winmm.dll`jako `Form1 PlaySound()`. Příklad obsahuje jednoduchý formulář Windows s tlačítkem. Kliknutím na tlačítko otevřete standardní dialogové okno Windows <xref:System.Windows.Forms.OpenFileDialog>, abyste mohli otevřít soubor pro přehrávání. Když je vybrán soubor Wave, je přehrán pomocí metody `PlaySound()` knihovny *winmm. dll* . Další informace o této metodě najdete v tématu [použití funkce PlaySound se soubory zvuku Wave](https://docs.microsoft.com/windows/desktop/multimedia/using-playsound-to-play-waveform-audio-files). Procházejte a vyberte soubor s příponou. wav a potom klikněte na tlačítko **otevřít** a přehrání souboru Wave pomocí vyvolání platformy. Textové pole zobrazuje úplnou cestu k vybranému souboru.

Dialogové okno **otevřít soubory** je filtrováno tak, aby zobrazovalo pouze soubory s příponou. wav prostřednictvím nastavení filtru:

[!code-csharp[csProgGuideInterop#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInterop/CS/WinSound.cs#5)]

[!code-csharp[csProgGuideInterop#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInterop/CS/WinSound.cs#3)]

## <a name="compiling-the-code"></a>Kompilování kódu

1. V aplikaci Visual C# Studio vytvořte nový projekt aplikace model Windows Forms a pojmenujte ho **WinSound**.

2. Zkopírujte kód výše a vložte ho do obsahu souboru *Form1.cs* .

3. Zkopírujte následující kód a vložte ho do souboru *Form1.Designer.cs* v metodě `InitializeComponent()` po jakémkoli existujícím kódu.

     [!code-csharp[csProgGuideInterop#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInterop/CS/WinSound.cs#4)]

4. Zkompilujte a spusťte kód.

## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce C#](../index.md)
- [Přehled interoperability](interoperability-overview.md)
- [Bližší pohled na vyvolání platformy](../../../framework/interop/consuming-unmanaged-dll-functions.md#a-closer-look-at-platform-invoke)
- [Zařazování dat s voláním platformy](../../../framework/interop/marshaling-data-with-platform-invoke.md)
