---
title: Jak použít vyvolání platformy k přehrání souboru WAV – Průvodce programováním v C#
description: Tento příklad kódu v jazyce C# ukazuje, jak použít služby vyvolání platformy k přehrání zvukového souboru WAV v operačním systému Windows.
ms.date: 07/20/2015
helpviewer_keywords:
- platform invoke, sound files
- interoperability [C#], playing WAV files using pinvoke
- wav files
- .wav files
ms.assetid: f7f62f53-e026-4c40-b221-3a26adb0c2c5
ms.openlocfilehash: b30cb08e2dcde0eb85e8d88a690ae24bf7ae7f22
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302981"
---
# <a name="how-to-use-platform-invoke-to-play-a-wav-file-c-programming-guide"></a>Jak použít vyvolání platformy k přehrání souboru WAV (Průvodce programováním v C#)

Následující příklad kódu jazyka C# ukazuje, jak použít služby vyvolání platformy k přehrání zvukového souboru WAV v operačním systému Windows.

## <a name="example"></a>Příklad

Tento příklad kódu používá <xref:System.Runtime.InteropServices.DllImportAttribute> pro import `winmm.dll` `PlaySound` vstupního bodu metody jako `Form1 PlaySound()` . Příklad obsahuje jednoduchý formulář Windows s tlačítkem. Kliknutím na tlačítko otevřete standardní <xref:System.Windows.Forms.OpenFileDialog> dialogové okno systému Windows, abyste mohli otevřít soubor pro přehrávání. Když je vybrán soubor Wave, je přehrán pomocí `PlaySound()` metody knihovny *winmm.dll* . Další informace o této metodě najdete v tématu [použití funkce PlaySound se soubory zvuku Wave](https://docs.microsoft.com/windows/desktop/multimedia/using-playsound-to-play-waveform-audio-files). Procházejte a vyberte soubor s příponou. wav a potom klikněte na tlačítko **otevřít** a přehrání souboru Wave pomocí vyvolání platformy. Textové pole zobrazuje úplnou cestu k vybranému souboru.

Dialogové okno **otevřít soubory** je filtrováno tak, aby zobrazovalo pouze soubory s příponou. wav prostřednictvím nastavení filtru:

[!code-csharp[csProgGuideInterop#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInterop/CS/WinSound.cs#5)]

[!code-csharp[csProgGuideInterop#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInterop/CS/WinSound.cs#3)]

## <a name="compiling-the-code"></a>Zkompilování kódu

1. V aplikaci Visual Studio vytvořte nový projekt C# model Windows Forms aplikace a pojmenujte ho **WinSound**.

2. Zkopírujte kód výše a vložte ho do obsahu souboru *Form1.cs* .

3. Zkopírujte následující kód a vložte ho do souboru *Form1.Designer.cs* v `InitializeComponent()` metodě po jakémkoli existujícím kódu.

     [!code-csharp[csProgGuideInterop#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInterop/CS/WinSound.cs#4)]

4. Zkompilujte a spusťte kód.

## <a name="see-also"></a>Viz také:

- [Průvodce programováním v C#](../index.md)
- [Přehled interoperability](interoperability-overview.md)
- [Bližší pohled na vyvolání platformy](../../../framework/interop/consuming-unmanaged-dll-functions.md#a-closer-look-at-platform-invoke)
- [Zařazování dat s voláním platformy](../../../framework/interop/marshaling-data-with-platform-invoke.md)
