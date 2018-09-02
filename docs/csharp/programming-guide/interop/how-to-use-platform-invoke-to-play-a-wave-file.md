---
title: 'Postupy: Použití vyvolání platformy pro přehrání souboru wave (Průvodce programováním v C#)'
ms.date: 07/20/2015
helpviewer_keywords:
- platform invoke, sound files
- interoperability [C#], playing WAV files using pinvoke
- wav files
- .wav files
ms.assetid: f7f62f53-e026-4c40-b221-3a26adb0c2c5
ms.openlocfilehash: 6b20877e54722b338c9905445a39c42350c7f7d7
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43384866"
---
# <a name="how-to-use-platform-invoke-to-play-a-wave-file-c-programming-guide"></a>Postupy: Použití vyvolání platformy pro přehrání souboru wave (Průvodce programováním v C#)
Následující příklad kódu jazyka C# ukazuje, jak používat platformu vyvolání služby pro přehrání souboru wave zvuku v operačním systému Windows.  
  
## <a name="example"></a>Příklad  
 Tento příklad kódu používá `DllImport` import `winmm.dll`společnosti `PlaySound` metodu vstupního bodu jako `Form1 PlaySound()`. V příkladu je jednoduchý formulář Windows s tlačítkem. Kliknutím na tlačítko otevře standardní windows <xref:System.Windows.Forms.OpenFileDialog> dialogové okno, aby mohli otevřít soubor přehrávat. Při výběru souboru wave přehrání s použitím `PlaySound()` metodu `winmm.dll` knihovny. Další informace o této metodě naleznete v tématu [pomocí funkce PlaySound zvukového průběhu, zvukové soubory](https://docs.microsoft.com/windows/desktop/multimedia/using-playsound-to-play-waveform-audio-files). Procházet a vyberte soubor, který má příponu .wav a potom klikněte na **otevřít** k přehrání souboru wave pomocí platformy vyvolat. Textové pole zobrazí úplnou cestu vybraný soubor.  
  
 **Otevřených souborů** dialogové okno se vyfiltruje a zobrazí pouze soubory, které mají příponu .wav prostřednictvím nastavení filtru:  
  
 [!code-csharp[csProgGuideInterop#5](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-platform-invoke-to-play-a-wave-file_1.cs)]  
  
 [!code-csharp[csProgGuideInterop#3](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-platform-invoke-to-play-a-wave-file_2.cs)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
  
### <a name="to-compile-the-code"></a>Chcete-li zkompilovat kód  
  
1.  Vytvořte nový projekt aplikace Windows v C# v sadě Visual Studio s názvem **WinSound**.  
  
2.  Výše uvedený kód zkopírujte a vložte ji místo obsah `Form1.cs` souboru.  
  
3.  Zkopírujte následující kód a vložte ji `Form1.Designer.cs` souboru `InitializeComponent()` metoda za existující kód.  
  
     [!code-csharp[csProgGuideInterop#4](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-platform-invoke-to-play-a-wave-file_3.cs)]  
  
4.  Kompilace a spuštění kódu.  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  
 Další informace najdete v tématu [zabezpečení v rozhraní .NET](../../../standard/security/index.md).  
  
## <a name="see-also"></a>Viz také  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [Přehled interoperability](../../../csharp/programming-guide/interop/interoperability-overview.md)  
 [Bližší pohled na vyvolání platformy](../../../framework/interop/consuming-unmanaged-dll-functions.md#a-closer-look-at-platform-invoke)  
 [Zařazování dat s voláním platformy](../../../framework/interop/marshaling-data-with-platform-invoke.md)
