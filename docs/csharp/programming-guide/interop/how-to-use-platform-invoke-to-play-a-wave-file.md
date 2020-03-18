---
title: Jak používat vyvolání platformy k přehrání souboru WAV - C# Programming Guide
ms.date: 07/20/2015
helpviewer_keywords:
- platform invoke, sound files
- interoperability [C#], playing WAV files using pinvoke
- wav files
- .wav files
ms.assetid: f7f62f53-e026-4c40-b221-3a26adb0c2c5
ms.openlocfilehash: 3ea90f0739ad45c31e4f25836c9de8e708dff2cc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75700819"
---
# <a name="how-to-use-platform-invoke-to-play-a-wav-file-c-programming-guide"></a>Jak používat platformu vyvolat hrát soubor WAV (C# Programovací průvodce)

Následující příklad kódu Jazyka C# ukazuje, jak pomocí služby vyvolání platformy přehrát zvukový soubor WAV v operačním systému Windows.

## <a name="example"></a>Příklad

Tento příklad <xref:System.Runtime.InteropServices.DllImportAttribute> kódu `winmm.dll`používá `PlaySound` k importu `Form1 PlaySound()`vstupního bodu metody jako . Příklad má jednoduchý formulář systému Windows s tlačítkem. Kliknutím na tlačítko se <xref:System.Windows.Forms.OpenFileDialog> otevře standardní dialogové okno systému Windows, abyste mohli otevřít soubor, který chcete přehrát. Pokud je vybrán soubor vlny, přehraje se pomocí `PlaySound()` metody knihovny *winmm.dll.* Další informace o této metodě naleznete [v tématu Použití funkce PlaySound s waveform-audio soubory](https://docs.microsoft.com/windows/desktop/multimedia/using-playsound-to-play-waveform-audio-files). Procházejte a vyberte soubor s příponou WAV a klepnutím na tlačítko **Otevřít** přehrajte soubor vlny pomocí vyvolání platformy. V textovém poli se zobrazí úplná cesta k vybranému souboru.

Dialogové okno **Otevřít soubory** je filtrováno tak, aby zobrazovalo pouze soubory, které mají příponu WAV, a to v nastavení filtru:

[!code-csharp[csProgGuideInterop#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInterop/CS/WinSound.cs#5)]

[!code-csharp[csProgGuideInterop#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInterop/CS/WinSound.cs#3)]

## <a name="compiling-the-code"></a>Zkompilování kódu

1. Vytvořte nový projekt aplikace C# Windows Forms Application v sadě Visual Studio a pojmenujte jej **WinSound**.

2. Zkopírujte výše uvedený kód a vložte jej přes obsah *Form1.cs* souboru.

3. Zkopírujte následující kód a vložte jej do `InitializeComponent()` *Form1.Designer.cs* souboru, v metodě, za libovolný existující kód.

     [!code-csharp[csProgGuideInterop#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInterop/CS/WinSound.cs#4)]

4. Zkompilujte a spusťte kód.

## <a name="see-also"></a>Viz také

- [Programovací příručka jazyka C#](../index.md)
- [Přehled interoperability](interoperability-overview.md)
- [Bližší pohled na vyvolání platformy](../../../framework/interop/consuming-unmanaged-dll-functions.md#a-closer-look-at-platform-invoke)
- [Zařazování dat s voláním platformy](../../../framework/interop/marshaling-data-with-platform-invoke.md)
