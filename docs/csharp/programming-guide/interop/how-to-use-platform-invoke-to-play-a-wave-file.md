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
# <a name="how-to-use-platform-invoke-to-play-a-wav-file-c-programming-guide"></a><span data-ttu-id="15ee2-103">Jak použít vyvolání platformy k přehrání souboru WAV (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="15ee2-103">How to use platform invoke to play a WAV file (C# Programming Guide)</span></span>

<span data-ttu-id="15ee2-104">Následující příklad kódu jazyka C# ukazuje, jak použít služby vyvolání platformy k přehrání zvukového souboru WAV v operačním systému Windows.</span><span class="sxs-lookup"><span data-stu-id="15ee2-104">The following C# code example illustrates how to use platform invoke services to play a WAV sound file on the Windows operating system.</span></span>

## <a name="example"></a><span data-ttu-id="15ee2-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="15ee2-105">Example</span></span>

<span data-ttu-id="15ee2-106">Tento příklad kódu používá <xref:System.Runtime.InteropServices.DllImportAttribute> pro import `winmm.dll` `PlaySound` vstupního bodu metody jako `Form1 PlaySound()` .</span><span class="sxs-lookup"><span data-stu-id="15ee2-106">This example code uses <xref:System.Runtime.InteropServices.DllImportAttribute> to import `winmm.dll`'s `PlaySound` method entry point as `Form1 PlaySound()`.</span></span> <span data-ttu-id="15ee2-107">Příklad obsahuje jednoduchý formulář Windows s tlačítkem.</span><span class="sxs-lookup"><span data-stu-id="15ee2-107">The example has a simple Windows Form with a button.</span></span> <span data-ttu-id="15ee2-108">Kliknutím na tlačítko otevřete standardní <xref:System.Windows.Forms.OpenFileDialog> dialogové okno systému Windows, abyste mohli otevřít soubor pro přehrávání.</span><span class="sxs-lookup"><span data-stu-id="15ee2-108">Clicking the button opens a standard windows <xref:System.Windows.Forms.OpenFileDialog> dialog box so that you can open a file to play.</span></span> <span data-ttu-id="15ee2-109">Když je vybrán soubor Wave, je přehrán pomocí `PlaySound()` metody knihovny *winmm.dll* .</span><span class="sxs-lookup"><span data-stu-id="15ee2-109">When a wave file is selected, it is played by using the `PlaySound()` method of the *winmm.dll* library.</span></span> <span data-ttu-id="15ee2-110">Další informace o této metodě najdete v tématu [použití funkce PlaySound se soubory zvuku Wave](https://docs.microsoft.com/windows/desktop/multimedia/using-playsound-to-play-waveform-audio-files).</span><span class="sxs-lookup"><span data-stu-id="15ee2-110">For more information about this method, see [Using the PlaySound function with Waveform-Audio Files](https://docs.microsoft.com/windows/desktop/multimedia/using-playsound-to-play-waveform-audio-files).</span></span> <span data-ttu-id="15ee2-111">Procházejte a vyberte soubor s příponou. wav a potom klikněte na tlačítko **otevřít** a přehrání souboru Wave pomocí vyvolání platformy.</span><span class="sxs-lookup"><span data-stu-id="15ee2-111">Browse and select a file that has a .wav extension, and then click **Open** to play the wave file by using platform invoke.</span></span> <span data-ttu-id="15ee2-112">Textové pole zobrazuje úplnou cestu k vybranému souboru.</span><span class="sxs-lookup"><span data-stu-id="15ee2-112">A text box shows the full path of the file selected.</span></span>

<span data-ttu-id="15ee2-113">Dialogové okno **otevřít soubory** je filtrováno tak, aby zobrazovalo pouze soubory s příponou. wav prostřednictvím nastavení filtru:</span><span class="sxs-lookup"><span data-stu-id="15ee2-113">The **Open Files** dialog box is filtered to show only files that have a .wav extension through the filter settings:</span></span>

[!code-csharp[csProgGuideInterop#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInterop/CS/WinSound.cs#5)]

[!code-csharp[csProgGuideInterop#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInterop/CS/WinSound.cs#3)]

## <a name="compiling-the-code"></a><span data-ttu-id="15ee2-114">Zkompilování kódu</span><span class="sxs-lookup"><span data-stu-id="15ee2-114">Compiling the code</span></span>

1. <span data-ttu-id="15ee2-115">V aplikaci Visual Studio vytvořte nový projekt C# model Windows Forms aplikace a pojmenujte ho **WinSound**.</span><span class="sxs-lookup"><span data-stu-id="15ee2-115">Create a new C# Windows Forms Application project in Visual Studio and name it **WinSound**.</span></span>

2. <span data-ttu-id="15ee2-116">Zkopírujte kód výše a vložte ho do obsahu souboru *Form1.cs* .</span><span class="sxs-lookup"><span data-stu-id="15ee2-116">Copy the code above, and paste it over the contents of the *Form1.cs* file.</span></span>

3. <span data-ttu-id="15ee2-117">Zkopírujte následující kód a vložte ho do souboru *Form1.Designer.cs* v `InitializeComponent()` metodě po jakémkoli existujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="15ee2-117">Copy the following code, and paste it in the *Form1.Designer.cs* file, in the `InitializeComponent()` method, after any existing code.</span></span>

     [!code-csharp[csProgGuideInterop#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInterop/CS/WinSound.cs#4)]

4. <span data-ttu-id="15ee2-118">Zkompilujte a spusťte kód.</span><span class="sxs-lookup"><span data-stu-id="15ee2-118">Compile and run the code.</span></span>

## <a name="see-also"></a><span data-ttu-id="15ee2-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="15ee2-119">See also</span></span>

- [<span data-ttu-id="15ee2-120">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="15ee2-120">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="15ee2-121">Přehled interoperability</span><span class="sxs-lookup"><span data-stu-id="15ee2-121">Interoperability Overview</span></span>](interoperability-overview.md)
- [<span data-ttu-id="15ee2-122">Bližší pohled na vyvolání platformy</span><span class="sxs-lookup"><span data-stu-id="15ee2-122">A Closer Look at Platform Invoke</span></span>](../../../framework/interop/consuming-unmanaged-dll-functions.md#a-closer-look-at-platform-invoke)
- [<span data-ttu-id="15ee2-123">Zařazování dat s voláním platformy</span><span class="sxs-lookup"><span data-stu-id="15ee2-123">Marshaling Data with Platform Invoke</span></span>](../../../framework/interop/marshaling-data-with-platform-invoke.md)
