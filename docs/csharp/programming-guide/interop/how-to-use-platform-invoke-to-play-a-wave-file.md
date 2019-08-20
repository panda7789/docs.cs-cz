---
title: 'Postupy: Použít vyvolání platformy k přehrání souboru Wave – C# Průvodce programováním'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- platform invoke, sound files
- interoperability [C#], playing WAV files using pinvoke
- wav files
- .wav files
ms.assetid: f7f62f53-e026-4c40-b221-3a26adb0c2c5
ms.openlocfilehash: cf8415b2d501ae2394fa76170eb232da33c3e308
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69589109"
---
# <a name="how-to-use-platform-invoke-to-play-a-wave-file-c-programming-guide"></a>Postupy: Použít vyvolání platformy k přehrání souboru Wave (C# Průvodce programováním)
Následující C# příklad kódu ukazuje, jak použít služby vyvolání platformy k přehrání zvukového souboru Wave v operačním systému Windows.  
  
## <a name="example"></a>Příklad  
 Tento příklad kódu používá `DllImport` pro `PlaySound` import `winmm.dll`vstupního bodu metody jako `Form1 PlaySound()`. Příklad obsahuje jednoduchý formulář Windows s tlačítkem. Kliknutím na tlačítko otevřete standardní dialogové okno <xref:System.Windows.Forms.OpenFileDialog> systému Windows, abyste mohli otevřít soubor pro přehrávání. Když je vybrán soubor Wave, je přehrán pomocí `PlaySound()` metody `winmm.dll` knihovny. Další informace o této metodě najdete v tématu [použití funkce PlaySound se soubory zvuku Wave](https://docs.microsoft.com/windows/desktop/multimedia/using-playsound-to-play-waveform-audio-files). Procházejte a vyberte soubor s příponou. wav a potom klikněte na tlačítko **otevřít** a přehrání souboru Wave pomocí vyvolání platformy. Textové pole zobrazuje úplnou cestu k vybranému souboru.  
  
 Dialogové okno **otevřít soubory** je filtrováno tak, aby zobrazovalo pouze soubory s příponou. wav prostřednictvím nastavení filtru:  
  
 [!code-csharp[csProgGuideInterop#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInterop/CS/WinSound.cs#5)]  
  
 [!code-csharp[csProgGuideInterop#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInterop/CS/WinSound.cs#3)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
  
1. Vytvořte nový C# projekt aplikace pro Windows v aplikaci Visual Studio a pojmenujte ho **WinSound**.  
  
2. Zkopírujte kód výše a vložte ho do obsahu `Form1.cs` souboru.  
  
3. Zkopírujte následující kód a vložte jej do `Form1.Designer.cs` souboru, `InitializeComponent()` v metodě, po jakémkoli existujícím kódu.  
  
     [!code-csharp[csProgGuideInterop#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInterop/CS/WinSound.cs#4)]  
  
4. Zkompilujte a spusťte kód.  
  
## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce C#](../index.md)
- [Přehled interoperability](./interoperability-overview.md)
- [Bližší pohled na vyvolání platformy](../../../framework/interop/consuming-unmanaged-dll-functions.md#a-closer-look-at-platform-invoke)
- [Zařazování dat s voláním platformy](../../../framework/interop/marshaling-data-with-platform-invoke.md)
