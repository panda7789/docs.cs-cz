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
# <a name="how-to-use-platform-invoke-to-play-a-wave-file-c-programming-guide"></a><span data-ttu-id="f8253-102">Postupy: Použít vyvolání platformy k přehrání souboru Wave (C# Průvodce programováním)</span><span class="sxs-lookup"><span data-stu-id="f8253-102">How to: Use Platform Invoke to Play a Wave File (C# Programming Guide)</span></span>
<span data-ttu-id="f8253-103">Následující C# příklad kódu ukazuje, jak použít služby vyvolání platformy k přehrání zvukového souboru Wave v operačním systému Windows.</span><span class="sxs-lookup"><span data-stu-id="f8253-103">The following C# code example illustrates how to use platform invoke services to play a wave sound file on the Windows operating system.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f8253-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="f8253-104">Example</span></span>  
 <span data-ttu-id="f8253-105">Tento příklad kódu používá `DllImport` pro `PlaySound` import `winmm.dll`vstupního bodu metody jako `Form1 PlaySound()`.</span><span class="sxs-lookup"><span data-stu-id="f8253-105">This example code uses `DllImport` to import `winmm.dll`'s `PlaySound` method entry point as `Form1 PlaySound()`.</span></span> <span data-ttu-id="f8253-106">Příklad obsahuje jednoduchý formulář Windows s tlačítkem.</span><span class="sxs-lookup"><span data-stu-id="f8253-106">The example has a simple Windows Form with a button.</span></span> <span data-ttu-id="f8253-107">Kliknutím na tlačítko otevřete standardní dialogové okno <xref:System.Windows.Forms.OpenFileDialog> systému Windows, abyste mohli otevřít soubor pro přehrávání.</span><span class="sxs-lookup"><span data-stu-id="f8253-107">Clicking the button opens a standard windows <xref:System.Windows.Forms.OpenFileDialog> dialog box so that you can open a file to play.</span></span> <span data-ttu-id="f8253-108">Když je vybrán soubor Wave, je přehrán pomocí `PlaySound()` metody `winmm.dll` knihovny.</span><span class="sxs-lookup"><span data-stu-id="f8253-108">When a wave file is selected, it is played by using the `PlaySound()` method of the `winmm.dll` library.</span></span> <span data-ttu-id="f8253-109">Další informace o této metodě najdete v tématu [použití funkce PlaySound se soubory zvuku Wave](https://docs.microsoft.com/windows/desktop/multimedia/using-playsound-to-play-waveform-audio-files).</span><span class="sxs-lookup"><span data-stu-id="f8253-109">For more information about this method, see [Using the PlaySound function with Waveform-Audio Files](https://docs.microsoft.com/windows/desktop/multimedia/using-playsound-to-play-waveform-audio-files).</span></span> <span data-ttu-id="f8253-110">Procházejte a vyberte soubor s příponou. wav a potom klikněte na tlačítko **otevřít** a přehrání souboru Wave pomocí vyvolání platformy.</span><span class="sxs-lookup"><span data-stu-id="f8253-110">Browse and select a file that has a .wav extension, and then click **Open** to play the wave file by using platform invoke.</span></span> <span data-ttu-id="f8253-111">Textové pole zobrazuje úplnou cestu k vybranému souboru.</span><span class="sxs-lookup"><span data-stu-id="f8253-111">A text box shows the full path of the file selected.</span></span>  
  
 <span data-ttu-id="f8253-112">Dialogové okno **otevřít soubory** je filtrováno tak, aby zobrazovalo pouze soubory s příponou. wav prostřednictvím nastavení filtru:</span><span class="sxs-lookup"><span data-stu-id="f8253-112">The **Open Files** dialog box is filtered to show only files that have a .wav extension through the filter settings:</span></span>  
  
 [!code-csharp[csProgGuideInterop#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInterop/CS/WinSound.cs#5)]  
  
 [!code-csharp[csProgGuideInterop#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInterop/CS/WinSound.cs#3)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="f8253-113">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="f8253-113">Compiling the Code</span></span>  
  
1. <span data-ttu-id="f8253-114">Vytvořte nový C# projekt aplikace pro Windows v aplikaci Visual Studio a pojmenujte ho **WinSound**.</span><span class="sxs-lookup"><span data-stu-id="f8253-114">Create a new C# Windows Application project in Visual Studio and name it **WinSound**.</span></span>  
  
2. <span data-ttu-id="f8253-115">Zkopírujte kód výše a vložte ho do obsahu `Form1.cs` souboru.</span><span class="sxs-lookup"><span data-stu-id="f8253-115">Copy the code above, and paste it over the contents of the `Form1.cs` file.</span></span>  
  
3. <span data-ttu-id="f8253-116">Zkopírujte následující kód a vložte jej do `Form1.Designer.cs` souboru, `InitializeComponent()` v metodě, po jakémkoli existujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="f8253-116">Copy the following code, and paste it in the `Form1.Designer.cs` file, in the `InitializeComponent()` method, after any existing code.</span></span>  
  
     [!code-csharp[csProgGuideInterop#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInterop/CS/WinSound.cs#4)]  
  
4. <span data-ttu-id="f8253-117">Zkompilujte a spusťte kód.</span><span class="sxs-lookup"><span data-stu-id="f8253-117">Compile and run the code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8253-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f8253-118">See also</span></span>

- [<span data-ttu-id="f8253-119">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="f8253-119">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="f8253-120">Přehled interoperability</span><span class="sxs-lookup"><span data-stu-id="f8253-120">Interoperability Overview</span></span>](./interoperability-overview.md)
- [<span data-ttu-id="f8253-121">Bližší pohled na vyvolání platformy</span><span class="sxs-lookup"><span data-stu-id="f8253-121">A Closer Look at Platform Invoke</span></span>](../../../framework/interop/consuming-unmanaged-dll-functions.md#a-closer-look-at-platform-invoke)
- [<span data-ttu-id="f8253-122">Zařazování dat s voláním platformy</span><span class="sxs-lookup"><span data-stu-id="f8253-122">Marshaling Data with Platform Invoke</span></span>](../../../framework/interop/marshaling-data-with-platform-invoke.md)
