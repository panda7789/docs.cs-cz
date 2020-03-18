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
# <a name="how-to-use-platform-invoke-to-play-a-wav-file-c-programming-guide"></a><span data-ttu-id="c6008-102">Jak používat platformu vyvolat hrát soubor WAV (C# Programovací průvodce)</span><span class="sxs-lookup"><span data-stu-id="c6008-102">How to use platform invoke to play a WAV file (C# Programming Guide)</span></span>

<span data-ttu-id="c6008-103">Následující příklad kódu Jazyka C# ukazuje, jak pomocí služby vyvolání platformy přehrát zvukový soubor WAV v operačním systému Windows.</span><span class="sxs-lookup"><span data-stu-id="c6008-103">The following C# code example illustrates how to use platform invoke services to play a WAV sound file on the Windows operating system.</span></span>

## <a name="example"></a><span data-ttu-id="c6008-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="c6008-104">Example</span></span>

<span data-ttu-id="c6008-105">Tento příklad <xref:System.Runtime.InteropServices.DllImportAttribute> kódu `winmm.dll`používá `PlaySound` k importu `Form1 PlaySound()`vstupního bodu metody jako .</span><span class="sxs-lookup"><span data-stu-id="c6008-105">This example code uses <xref:System.Runtime.InteropServices.DllImportAttribute> to import `winmm.dll`'s `PlaySound` method entry point as `Form1 PlaySound()`.</span></span> <span data-ttu-id="c6008-106">Příklad má jednoduchý formulář systému Windows s tlačítkem.</span><span class="sxs-lookup"><span data-stu-id="c6008-106">The example has a simple Windows Form with a button.</span></span> <span data-ttu-id="c6008-107">Kliknutím na tlačítko se <xref:System.Windows.Forms.OpenFileDialog> otevře standardní dialogové okno systému Windows, abyste mohli otevřít soubor, který chcete přehrát.</span><span class="sxs-lookup"><span data-stu-id="c6008-107">Clicking the button opens a standard windows <xref:System.Windows.Forms.OpenFileDialog> dialog box so that you can open a file to play.</span></span> <span data-ttu-id="c6008-108">Pokud je vybrán soubor vlny, přehraje se pomocí `PlaySound()` metody knihovny *winmm.dll.*</span><span class="sxs-lookup"><span data-stu-id="c6008-108">When a wave file is selected, it is played by using the `PlaySound()` method of the *winmm.dll* library.</span></span> <span data-ttu-id="c6008-109">Další informace o této metodě naleznete [v tématu Použití funkce PlaySound s waveform-audio soubory](https://docs.microsoft.com/windows/desktop/multimedia/using-playsound-to-play-waveform-audio-files).</span><span class="sxs-lookup"><span data-stu-id="c6008-109">For more information about this method, see [Using the PlaySound function with Waveform-Audio Files](https://docs.microsoft.com/windows/desktop/multimedia/using-playsound-to-play-waveform-audio-files).</span></span> <span data-ttu-id="c6008-110">Procházejte a vyberte soubor s příponou WAV a klepnutím na tlačítko **Otevřít** přehrajte soubor vlny pomocí vyvolání platformy.</span><span class="sxs-lookup"><span data-stu-id="c6008-110">Browse and select a file that has a .wav extension, and then click **Open** to play the wave file by using platform invoke.</span></span> <span data-ttu-id="c6008-111">V textovém poli se zobrazí úplná cesta k vybranému souboru.</span><span class="sxs-lookup"><span data-stu-id="c6008-111">A text box shows the full path of the file selected.</span></span>

<span data-ttu-id="c6008-112">Dialogové okno **Otevřít soubory** je filtrováno tak, aby zobrazovalo pouze soubory, které mají příponu WAV, a to v nastavení filtru:</span><span class="sxs-lookup"><span data-stu-id="c6008-112">The **Open Files** dialog box is filtered to show only files that have a .wav extension through the filter settings:</span></span>

[!code-csharp[csProgGuideInterop#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInterop/CS/WinSound.cs#5)]

[!code-csharp[csProgGuideInterop#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInterop/CS/WinSound.cs#3)]

## <a name="compiling-the-code"></a><span data-ttu-id="c6008-113">Zkompilování kódu</span><span class="sxs-lookup"><span data-stu-id="c6008-113">Compiling the code</span></span>

1. <span data-ttu-id="c6008-114">Vytvořte nový projekt aplikace C# Windows Forms Application v sadě Visual Studio a pojmenujte jej **WinSound**.</span><span class="sxs-lookup"><span data-stu-id="c6008-114">Create a new C# Windows Forms Application project in Visual Studio and name it **WinSound**.</span></span>

2. <span data-ttu-id="c6008-115">Zkopírujte výše uvedený kód a vložte jej přes obsah *Form1.cs* souboru.</span><span class="sxs-lookup"><span data-stu-id="c6008-115">Copy the code above, and paste it over the contents of the *Form1.cs* file.</span></span>

3. <span data-ttu-id="c6008-116">Zkopírujte následující kód a vložte jej do `InitializeComponent()` *Form1.Designer.cs* souboru, v metodě, za libovolný existující kód.</span><span class="sxs-lookup"><span data-stu-id="c6008-116">Copy the following code, and paste it in the *Form1.Designer.cs* file, in the `InitializeComponent()` method, after any existing code.</span></span>

     [!code-csharp[csProgGuideInterop#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInterop/CS/WinSound.cs#4)]

4. <span data-ttu-id="c6008-117">Zkompilujte a spusťte kód.</span><span class="sxs-lookup"><span data-stu-id="c6008-117">Compile and run the code.</span></span>

## <a name="see-also"></a><span data-ttu-id="c6008-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="c6008-118">See also</span></span>

- [<span data-ttu-id="c6008-119">Programovací příručka jazyka C#</span><span class="sxs-lookup"><span data-stu-id="c6008-119">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="c6008-120">Přehled interoperability</span><span class="sxs-lookup"><span data-stu-id="c6008-120">Interoperability Overview</span></span>](interoperability-overview.md)
- [<span data-ttu-id="c6008-121">Bližší pohled na vyvolání platformy</span><span class="sxs-lookup"><span data-stu-id="c6008-121">A Closer Look at Platform Invoke</span></span>](../../../framework/interop/consuming-unmanaged-dll-functions.md#a-closer-look-at-platform-invoke)
- [<span data-ttu-id="c6008-122">Zařazování dat s voláním platformy</span><span class="sxs-lookup"><span data-stu-id="c6008-122">Marshaling Data with Platform Invoke</span></span>](../../../framework/interop/marshaling-data-with-platform-invoke.md)
