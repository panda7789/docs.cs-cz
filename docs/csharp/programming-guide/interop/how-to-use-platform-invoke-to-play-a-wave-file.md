---
title: Použití vyvolání platformy k přehrání souboru WAV – C# Průvodce programováním
ms.date: 07/20/2015
helpviewer_keywords:
- platform invoke, sound files
- interoperability [C#], playing WAV files using pinvoke
- wav files
- .wav files
ms.assetid: f7f62f53-e026-4c40-b221-3a26adb0c2c5
ms.openlocfilehash: 3ea90f0739ad45c31e4f25836c9de8e708dff2cc
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75700819"
---
# <a name="how-to-use-platform-invoke-to-play-a-wav-file-c-programming-guide"></a><span data-ttu-id="b0c77-102">Jak použít vyvolání platformy k přehrání souboru WAV (C# Průvodce programováním)</span><span class="sxs-lookup"><span data-stu-id="b0c77-102">How to use platform invoke to play a WAV file (C# Programming Guide)</span></span>

<span data-ttu-id="b0c77-103">Následující C# příklad kódu ukazuje, jak použít služby vyvolání platformy k přehrání zvukového souboru WAV v operačním systému Windows.</span><span class="sxs-lookup"><span data-stu-id="b0c77-103">The following C# code example illustrates how to use platform invoke services to play a WAV sound file on the Windows operating system.</span></span>

## <a name="example"></a><span data-ttu-id="b0c77-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="b0c77-104">Example</span></span>

<span data-ttu-id="b0c77-105">Tento příklad kódu používá <xref:System.Runtime.InteropServices.DllImportAttribute> k importu vstupního bodu `PlaySound` metody `winmm.dll`jako `Form1 PlaySound()`.</span><span class="sxs-lookup"><span data-stu-id="b0c77-105">This example code uses <xref:System.Runtime.InteropServices.DllImportAttribute> to import `winmm.dll`'s `PlaySound` method entry point as `Form1 PlaySound()`.</span></span> <span data-ttu-id="b0c77-106">Příklad obsahuje jednoduchý formulář Windows s tlačítkem.</span><span class="sxs-lookup"><span data-stu-id="b0c77-106">The example has a simple Windows Form with a button.</span></span> <span data-ttu-id="b0c77-107">Kliknutím na tlačítko otevřete standardní dialogové okno Windows <xref:System.Windows.Forms.OpenFileDialog>, abyste mohli otevřít soubor pro přehrávání.</span><span class="sxs-lookup"><span data-stu-id="b0c77-107">Clicking the button opens a standard windows <xref:System.Windows.Forms.OpenFileDialog> dialog box so that you can open a file to play.</span></span> <span data-ttu-id="b0c77-108">Když je vybrán soubor Wave, je přehrán pomocí metody `PlaySound()` knihovny *winmm. dll* .</span><span class="sxs-lookup"><span data-stu-id="b0c77-108">When a wave file is selected, it is played by using the `PlaySound()` method of the *winmm.dll* library.</span></span> <span data-ttu-id="b0c77-109">Další informace o této metodě najdete v tématu [použití funkce PlaySound se soubory zvuku Wave](https://docs.microsoft.com/windows/desktop/multimedia/using-playsound-to-play-waveform-audio-files).</span><span class="sxs-lookup"><span data-stu-id="b0c77-109">For more information about this method, see [Using the PlaySound function with Waveform-Audio Files](https://docs.microsoft.com/windows/desktop/multimedia/using-playsound-to-play-waveform-audio-files).</span></span> <span data-ttu-id="b0c77-110">Procházejte a vyberte soubor s příponou. wav a potom klikněte na tlačítko **otevřít** a přehrání souboru Wave pomocí vyvolání platformy.</span><span class="sxs-lookup"><span data-stu-id="b0c77-110">Browse and select a file that has a .wav extension, and then click **Open** to play the wave file by using platform invoke.</span></span> <span data-ttu-id="b0c77-111">Textové pole zobrazuje úplnou cestu k vybranému souboru.</span><span class="sxs-lookup"><span data-stu-id="b0c77-111">A text box shows the full path of the file selected.</span></span>

<span data-ttu-id="b0c77-112">Dialogové okno **otevřít soubory** je filtrováno tak, aby zobrazovalo pouze soubory s příponou. wav prostřednictvím nastavení filtru:</span><span class="sxs-lookup"><span data-stu-id="b0c77-112">The **Open Files** dialog box is filtered to show only files that have a .wav extension through the filter settings:</span></span>

[!code-csharp[csProgGuideInterop#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInterop/CS/WinSound.cs#5)]

[!code-csharp[csProgGuideInterop#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInterop/CS/WinSound.cs#3)]

## <a name="compiling-the-code"></a><span data-ttu-id="b0c77-113">Zkompilování kódu</span><span class="sxs-lookup"><span data-stu-id="b0c77-113">Compiling the code</span></span>

1. <span data-ttu-id="b0c77-114">V aplikaci Visual C# Studio vytvořte nový projekt aplikace model Windows Forms a pojmenujte ho **WinSound**.</span><span class="sxs-lookup"><span data-stu-id="b0c77-114">Create a new C# Windows Forms Application project in Visual Studio and name it **WinSound**.</span></span>

2. <span data-ttu-id="b0c77-115">Zkopírujte kód výše a vložte ho do obsahu souboru *Form1.cs* .</span><span class="sxs-lookup"><span data-stu-id="b0c77-115">Copy the code above, and paste it over the contents of the *Form1.cs* file.</span></span>

3. <span data-ttu-id="b0c77-116">Zkopírujte následující kód a vložte ho do souboru *Form1.Designer.cs* v metodě `InitializeComponent()` po jakémkoli existujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="b0c77-116">Copy the following code, and paste it in the *Form1.Designer.cs* file, in the `InitializeComponent()` method, after any existing code.</span></span>

     [!code-csharp[csProgGuideInterop#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInterop/CS/WinSound.cs#4)]

4. <span data-ttu-id="b0c77-117">Zkompilujte a spusťte kód.</span><span class="sxs-lookup"><span data-stu-id="b0c77-117">Compile and run the code.</span></span>

## <a name="see-also"></a><span data-ttu-id="b0c77-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b0c77-118">See also</span></span>

- [<span data-ttu-id="b0c77-119">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="b0c77-119">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="b0c77-120">Přehled interoperability</span><span class="sxs-lookup"><span data-stu-id="b0c77-120">Interoperability Overview</span></span>](interoperability-overview.md)
- [<span data-ttu-id="b0c77-121">Bližší pohled na vyvolání platformy</span><span class="sxs-lookup"><span data-stu-id="b0c77-121">A Closer Look at Platform Invoke</span></span>](../../../framework/interop/consuming-unmanaged-dll-functions.md#a-closer-look-at-platform-invoke)
- [<span data-ttu-id="b0c77-122">Zařazování dat s voláním platformy</span><span class="sxs-lookup"><span data-stu-id="b0c77-122">Marshaling Data with Platform Invoke</span></span>](../../../framework/interop/marshaling-data-with-platform-invoke.md)
