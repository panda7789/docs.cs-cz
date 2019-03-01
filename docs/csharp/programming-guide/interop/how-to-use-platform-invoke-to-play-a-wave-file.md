---
title: 'Postupy: Použití vyvolání platformy pro přehrání souboru Wave – C# Průvodce programováním'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- platform invoke, sound files
- interoperability [C#], playing WAV files using pinvoke
- wav files
- .wav files
ms.assetid: f7f62f53-e026-4c40-b221-3a26adb0c2c5
ms.openlocfilehash: 209a0f03197e0f77e23be0dc1170789688f3e09a
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56967214"
---
# <a name="how-to-use-platform-invoke-to-play-a-wave-file-c-programming-guide"></a><span data-ttu-id="0f7b5-102">Postupy: Použití vyvolání platformy pro přehrání souboru Wave (C# Průvodce programováním v)</span><span class="sxs-lookup"><span data-stu-id="0f7b5-102">How to: Use Platform Invoke to Play a Wave File (C# Programming Guide)</span></span>
<span data-ttu-id="0f7b5-103">Následující příklad kódu jazyka C# ukazuje, jak používat platformu vyvolání služby pro přehrání souboru wave zvuku v operačním systému Windows.</span><span class="sxs-lookup"><span data-stu-id="0f7b5-103">The following C# code example illustrates how to use platform invoke services to play a wave sound file on the Windows operating system.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0f7b5-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="0f7b5-104">Example</span></span>  
 <span data-ttu-id="0f7b5-105">Tento příklad kódu používá `DllImport` import `winmm.dll`společnosti `PlaySound` metodu vstupního bodu jako `Form1 PlaySound()`.</span><span class="sxs-lookup"><span data-stu-id="0f7b5-105">This example code uses `DllImport` to import `winmm.dll`'s `PlaySound` method entry point as `Form1 PlaySound()`.</span></span> <span data-ttu-id="0f7b5-106">V příkladu je jednoduchý formulář Windows s tlačítkem.</span><span class="sxs-lookup"><span data-stu-id="0f7b5-106">The example has a simple Windows Form with a button.</span></span> <span data-ttu-id="0f7b5-107">Kliknutím na tlačítko otevře standardní windows <xref:System.Windows.Forms.OpenFileDialog> dialogové okno, aby mohli otevřít soubor přehrávat.</span><span class="sxs-lookup"><span data-stu-id="0f7b5-107">Clicking the button opens a standard windows <xref:System.Windows.Forms.OpenFileDialog> dialog box so that you can open a file to play.</span></span> <span data-ttu-id="0f7b5-108">Při výběru souboru wave přehrání s použitím `PlaySound()` metodu `winmm.dll` knihovny.</span><span class="sxs-lookup"><span data-stu-id="0f7b5-108">When a wave file is selected, it is played by using the `PlaySound()` method of the `winmm.dll` library.</span></span> <span data-ttu-id="0f7b5-109">Další informace o této metodě naleznete v tématu [pomocí funkce PlaySound zvukového průběhu, zvukové soubory](https://docs.microsoft.com/windows/desktop/multimedia/using-playsound-to-play-waveform-audio-files).</span><span class="sxs-lookup"><span data-stu-id="0f7b5-109">For more information about this method, see [Using the PlaySound function with Waveform-Audio Files](https://docs.microsoft.com/windows/desktop/multimedia/using-playsound-to-play-waveform-audio-files).</span></span> <span data-ttu-id="0f7b5-110">Procházet a vyberte soubor, který má příponu .wav a potom klikněte na **otevřít** k přehrání souboru wave pomocí platformy vyvolat.</span><span class="sxs-lookup"><span data-stu-id="0f7b5-110">Browse and select a file that has a .wav extension, and then click **Open** to play the wave file by using platform invoke.</span></span> <span data-ttu-id="0f7b5-111">Textové pole zobrazí úplnou cestu vybraný soubor.</span><span class="sxs-lookup"><span data-stu-id="0f7b5-111">A text box shows the full path of the file selected.</span></span>  
  
 <span data-ttu-id="0f7b5-112">**Otevřených souborů** dialogové okno se vyfiltruje a zobrazí pouze soubory, které mají příponu .wav prostřednictvím nastavení filtru:</span><span class="sxs-lookup"><span data-stu-id="0f7b5-112">The **Open Files** dialog box is filtered to show only files that have a .wav extension through the filter settings:</span></span>  
  
 [!code-csharp[csProgGuideInterop#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInterop/CS/WinSound.cs#5)]  
  
 [!code-csharp[csProgGuideInterop#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInterop/CS/WinSound.cs#3)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="0f7b5-113">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="0f7b5-113">Compiling the Code</span></span>  
  
### <a name="to-compile-the-code"></a><span data-ttu-id="0f7b5-114">Chcete-li zkompilovat kód</span><span class="sxs-lookup"><span data-stu-id="0f7b5-114">To compile the code</span></span>  
  
1.  <span data-ttu-id="0f7b5-115">Vytvořte nový projekt aplikace Windows v C# v sadě Visual Studio s názvem **WinSound**.</span><span class="sxs-lookup"><span data-stu-id="0f7b5-115">Create a new C# Windows Application project in Visual Studio and name it **WinSound**.</span></span>  
  
2.  <span data-ttu-id="0f7b5-116">Výše uvedený kód zkopírujte a vložte ji místo obsah `Form1.cs` souboru.</span><span class="sxs-lookup"><span data-stu-id="0f7b5-116">Copy the code above, and paste it over the contents of the `Form1.cs` file.</span></span>  
  
3.  <span data-ttu-id="0f7b5-117">Zkopírujte následující kód a vložte ji `Form1.Designer.cs` souboru `InitializeComponent()` metoda za existující kód.</span><span class="sxs-lookup"><span data-stu-id="0f7b5-117">Copy the following code, and paste it in the `Form1.Designer.cs` file, in the `InitializeComponent()` method, after any existing code.</span></span>  
  
     [!code-csharp[csProgGuideInterop#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInterop/CS/WinSound.cs#4)]  
  
4.  <span data-ttu-id="0f7b5-118">Kompilace a spuštění kódu.</span><span class="sxs-lookup"><span data-stu-id="0f7b5-118">Compile and run the code.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="0f7b5-119">Zabezpečení rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="0f7b5-119">.NET Framework Security</span></span>  
 <span data-ttu-id="0f7b5-120">Další informace najdete v tématu [zabezpečení v rozhraní .NET](../../../standard/security/index.md).</span><span class="sxs-lookup"><span data-stu-id="0f7b5-120">For more information, see [Security in .NET](../../../standard/security/index.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f7b5-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0f7b5-121">See also</span></span>

- [<span data-ttu-id="0f7b5-122">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="0f7b5-122">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="0f7b5-123">Přehled interoperability</span><span class="sxs-lookup"><span data-stu-id="0f7b5-123">Interoperability Overview</span></span>](../../../csharp/programming-guide/interop/interoperability-overview.md)
- [<span data-ttu-id="0f7b5-124">Bližší pohled na vyvolání platformy</span><span class="sxs-lookup"><span data-stu-id="0f7b5-124">A Closer Look at Platform Invoke</span></span>](../../../framework/interop/consuming-unmanaged-dll-functions.md#a-closer-look-at-platform-invoke)
- [<span data-ttu-id="0f7b5-125">Zařazování dat s voláním platformy</span><span class="sxs-lookup"><span data-stu-id="0f7b5-125">Marshaling Data with Platform Invoke</span></span>](../../../framework/interop/marshaling-data-with-platform-invoke.md)
