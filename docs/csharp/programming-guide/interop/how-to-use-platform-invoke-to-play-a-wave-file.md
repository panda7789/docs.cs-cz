---
title: 'Postupy: Použití vyvolání platformy pro přehrání souboru wave (Průvodce programováním v C#)'
ms.date: 07/20/2015
helpviewer_keywords:
- platform invoke, sound files
- interoperability [C#], playing WAV files using pinvoke
- wav files
- .wav files
ms.assetid: f7f62f53-e026-4c40-b221-3a26adb0c2c5
ms.openlocfilehash: f2234acb9d4eb3b436f3ccdad19525a5ebf26f7c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-use-platform-invoke-to-play-a-wave-file-c-programming-guide"></a>Postupy: Použití vyvolání platformy pro přehrání souboru wave (Průvodce programováním v C#)
Následující příklad kódu C#, ukazuje, jak používat platformu vyvolání služby pro přehrání souboru wave zvukové operačního systému Windows.  
  
## <a name="example"></a>Příklad  
 Tento příklad kódu používá `DllImport` import `winmm.dll`na `PlaySound` metoda vstupního bodu jako `Form1 PlaySound()`. V příkladu má jednoduché Windows Form pomocí tlačítka. Kliknutím na tlačítko otevře standardní windows <xref:System.Windows.Forms.OpenFileDialog> dialogu, aby mohli otevřít soubor k přehrání. Pokud je vybraná souboru wave, se přehrávají pomocí `PlaySound()` metoda winmm. Metoda sestavení knihovny DLL. Další informace o společnosti winmm.dll `PlaySound` metodu, najdete v části [pomocí funkce PlaySound zvukového průběhu, zvukové soubory](https://msdn.microsoft.com/library/aa910379.aspx). Procházet a vyberte soubor, který má příponu WAV a pak klikněte na tlačítko **otevřete** pro přehrání souboru wave pomocí platformy vyvolání. Textové pole zobrazuje úplnou cestu vybraný soubor.  
  
 **Otevřených souborů** dialogové okno je vyfiltrovány a zobrazí se pouze soubory, které mají příponu WAV prostřednictvím nastavení filtru:  
  
 [!code-csharp[csProgGuideInterop#5](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-platform-invoke-to-play-a-wave-file_1.cs)]  
  
 [!code-csharp[csProgGuideInterop#3](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-platform-invoke-to-play-a-wave-file_2.cs)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
  
### <a name="to-compile-the-code"></a>Kompilace kódu  
  
1.  Vytvořte nový projekt aplikace Windows v C# v sadě Visual Studio a pojmenujte ji **WinSound**.  
  
2.  Výše uvedený kód zkopírujte a vložte ho přes obsah `Form1.cs` souboru.  
  
3.  Zkopírujte následující kód a vložte jej do `Form1.Designer.cs` v souboru `InitializeComponent()` metoda po existující kód.  
  
     [!code-csharp[csProgGuideInterop#4](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-platform-invoke-to-play-a-wave-file_3.cs)]  
  
4.  Zkompilování a spuštění kódu.  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  
 Další informace najdete v tématu [zabezpečení rozhraní .NET Framework](https://technet.microsoft.com/en-us/security/).  
  
## <a name="see-also"></a>Viz také  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [Přehled interoperability](../../../csharp/programming-guide/interop/interoperability-overview.md)  
 [Vyvolání bližší pohled na platformy](../../../framework/interop/consuming-unmanaged-dll-functions.md#a-closer-look-at-platform-invoke)  
 [Zařazování dat s voláním platformy](../../../framework/interop/marshaling-data-with-platform-invoke.md)
