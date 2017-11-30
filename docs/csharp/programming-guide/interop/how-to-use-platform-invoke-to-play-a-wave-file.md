---
title: "Postupy: Použití vyvolání platformy pro přehrání souboru wave (Průvodce programováním v C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- platform invoke, sound files
- interoperability [C#], playing WAV files using pinvoke
- wav files
- .wav files
ms.assetid: f7f62f53-e026-4c40-b221-3a26adb0c2c5
caps.latest.revision: "30"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: d037e17ef48ebfdd5cfd860efbacf195e7b6a76d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-platform-invoke-to-play-a-wave-file-c-programming-guide"></a><span data-ttu-id="4ea16-102">Postupy: Použití vyvolání platformy pro přehrání souboru wave (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="4ea16-102">How to: Use Platform Invoke to Play a Wave File (C# Programming Guide)</span></span>
<span data-ttu-id="4ea16-103">Následující příklad kódu C#, ukazuje, jak používat platformu vyvolání služby pro přehrání souboru wave zvukové operačního systému Windows.</span><span class="sxs-lookup"><span data-stu-id="4ea16-103">The following C# code example illustrates how to use platform invoke services to play a wave sound file on the Windows operating system.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4ea16-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="4ea16-104">Example</span></span>  
 <span data-ttu-id="4ea16-105">Tento příklad kódu používá `DllImport` import `winmm.dll`na `PlaySound` metoda vstupního bodu jako `Form1 PlaySound()`.</span><span class="sxs-lookup"><span data-stu-id="4ea16-105">This example code uses `DllImport` to import `winmm.dll`'s `PlaySound` method entry point as `Form1 PlaySound()`.</span></span> <span data-ttu-id="4ea16-106">V příkladu má jednoduché Windows Form pomocí tlačítka.</span><span class="sxs-lookup"><span data-stu-id="4ea16-106">The example has a simple Windows Form with a button.</span></span> <span data-ttu-id="4ea16-107">Kliknutím na tlačítko otevře standardní windows <xref:System.Windows.Forms.OpenFileDialog> dialogu, aby mohli otevřít soubor k přehrání.</span><span class="sxs-lookup"><span data-stu-id="4ea16-107">Clicking the button opens a standard windows <xref:System.Windows.Forms.OpenFileDialog> dialog box so that you can open a file to play.</span></span> <span data-ttu-id="4ea16-108">Pokud je vybraná souboru wave, se přehrávají pomocí `PlaySound()` metoda winmm. Metoda sestavení knihovny DLL.</span><span class="sxs-lookup"><span data-stu-id="4ea16-108">When a wave file is selected, it is played by using the `PlaySound()` method of the winmm.DLL assembly method.</span></span> <span data-ttu-id="4ea16-109">Další informace o společnosti winmm.dll `PlaySound` metodu, najdete v části [pomocí funkce PlaySound zvukového průběhu, zvukové soubory](http://go.microsoft.com/fwlink/?LinkId=148553).</span><span class="sxs-lookup"><span data-stu-id="4ea16-109">For more information about winmm.dll's `PlaySound` method, see [Using the PlaySound function with Waveform-Audio Files](http://go.microsoft.com/fwlink/?LinkId=148553).</span></span> <span data-ttu-id="4ea16-110">Procházet a vyberte soubor, který má příponu WAV a pak klikněte na tlačítko **otevřete** pro přehrání souboru wave pomocí platformy vyvolání.</span><span class="sxs-lookup"><span data-stu-id="4ea16-110">Browse and select a file that has a .wav extension, and then click **Open** to play the wave file by using platform invoke.</span></span> <span data-ttu-id="4ea16-111">Textové pole zobrazuje úplnou cestu vybraný soubor.</span><span class="sxs-lookup"><span data-stu-id="4ea16-111">A text box shows the full path of the file selected.</span></span>  
  
 <span data-ttu-id="4ea16-112">**Otevřených souborů** dialogové okno je vyfiltrovány a zobrazí se pouze soubory, které mají příponu WAV prostřednictvím nastavení filtru:</span><span class="sxs-lookup"><span data-stu-id="4ea16-112">The **Open Files** dialog box is filtered to show only files that have a .wav extension through the filter settings:</span></span>  
  
 [!code-csharp[csProgGuideInterop#5](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-platform-invoke-to-play-a-wave-file_1.cs)]  
  
 [!code-csharp[csProgGuideInterop#3](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-platform-invoke-to-play-a-wave-file_2.cs)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="4ea16-113">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="4ea16-113">Compiling the Code</span></span>  
  
### <a name="to-compile-the-code"></a><span data-ttu-id="4ea16-114">Kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="4ea16-114">To compile the code</span></span>  
  
1.  <span data-ttu-id="4ea16-115">Vytvořte nový projekt aplikace Windows v C# v sadě Visual Studio a pojmenujte ji **WinSound**.</span><span class="sxs-lookup"><span data-stu-id="4ea16-115">Create a new C# Windows Application project in Visual Studio and name it **WinSound**.</span></span>  
  
2.  <span data-ttu-id="4ea16-116">Výše uvedený kód zkopírujte a vložte ho přes obsah `Form1.cs` souboru.</span><span class="sxs-lookup"><span data-stu-id="4ea16-116">Copy the code above, and paste it over the contents of the `Form1.cs` file.</span></span>  
  
3.  <span data-ttu-id="4ea16-117">Zkopírujte následující kód a vložte jej do `Form1.Designer.cs` v souboru `InitializeComponent()` metoda po existující kód.</span><span class="sxs-lookup"><span data-stu-id="4ea16-117">Copy the following code, and paste it in the `Form1.Designer.cs` file, in the `InitializeComponent()` method, after any existing code.</span></span>  
  
     [!code-csharp[csProgGuideInterop#4](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-platform-invoke-to-play-a-wave-file_3.cs)]  
  
4.  <span data-ttu-id="4ea16-118">Zkompilování a spuštění kódu.</span><span class="sxs-lookup"><span data-stu-id="4ea16-118">Compile and run the code.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="4ea16-119">Zabezpečení rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="4ea16-119">.NET Framework Security</span></span>  
 <span data-ttu-id="4ea16-120">Další informace najdete v tématu [zabezpečení rozhraní .NET Framework](http://go.microsoft.com/fwlink/?LinkId=37122).</span><span class="sxs-lookup"><span data-stu-id="4ea16-120">For more information, see [.NET Framework Security](http://go.microsoft.com/fwlink/?LinkId=37122).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ea16-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="4ea16-121">See Also</span></span>  
 [<span data-ttu-id="4ea16-122">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="4ea16-122">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="4ea16-123">Přehled interoperability</span><span class="sxs-lookup"><span data-stu-id="4ea16-123">Interoperability Overview</span></span>](../../../csharp/programming-guide/interop/interoperability-overview.md)  
 [<span data-ttu-id="4ea16-124">Přehled interoperability</span><span class="sxs-lookup"><span data-stu-id="4ea16-124">Interoperability Overview</span></span>](../../../csharp/programming-guide/interop/interoperability-overview.md)  
 [<span data-ttu-id="4ea16-125">Vyvolání bližší pohled na platformy</span><span class="sxs-lookup"><span data-stu-id="4ea16-125">A Closer Look at Platform Invoke</span></span>](http://msdn.microsoft.com/en-us/ba9dd55b-2eaa-45cd-8afd-75cb8d64d243)  
 [<span data-ttu-id="4ea16-126">Zařazování dat s voláním platformy</span><span class="sxs-lookup"><span data-stu-id="4ea16-126">Marshaling Data with Platform Invoke</span></span>](../../../framework/interop/marshaling-data-with-platform-invoke.md)
