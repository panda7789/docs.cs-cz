---
title: "Postupy: Použití vyvolání platformy pro přehrání souboru wave (Průvodce programováním v C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- platform invoke, sound files
- interoperability [C#], playing WAV files using pinvoke
- wav files
- .wav files
ms.assetid: f7f62f53-e026-4c40-b221-3a26adb0c2c5
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 10c2490255565de872396a0155bb588f9d696b24
ms.sourcegitcommit: d2da0142247ef42a219a5d2907f153e62dc6ea0d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/01/2018
---
# <a name="how-to-use-platform-invoke-to-play-a-wave-file-c-programming-guide"></a><span data-ttu-id="f2e8b-102">Postupy: Použití vyvolání platformy pro přehrání souboru wave (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="f2e8b-102">How to: Use Platform Invoke to Play a Wave File (C# Programming Guide)</span></span>
<span data-ttu-id="f2e8b-103">Následující příklad kódu C#, ukazuje, jak používat platformu vyvolání služby pro přehrání souboru wave zvukové operačního systému Windows.</span><span class="sxs-lookup"><span data-stu-id="f2e8b-103">The following C# code example illustrates how to use platform invoke services to play a wave sound file on the Windows operating system.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f2e8b-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="f2e8b-104">Example</span></span>  
 <span data-ttu-id="f2e8b-105">Tento příklad kódu používá `DllImport` import `winmm.dll`na `PlaySound` metoda vstupního bodu jako `Form1 PlaySound()`.</span><span class="sxs-lookup"><span data-stu-id="f2e8b-105">This example code uses `DllImport` to import `winmm.dll`'s `PlaySound` method entry point as `Form1 PlaySound()`.</span></span> <span data-ttu-id="f2e8b-106">V příkladu má jednoduché Windows Form pomocí tlačítka.</span><span class="sxs-lookup"><span data-stu-id="f2e8b-106">The example has a simple Windows Form with a button.</span></span> <span data-ttu-id="f2e8b-107">Kliknutím na tlačítko otevře standardní windows <xref:System.Windows.Forms.OpenFileDialog> dialogu, aby mohli otevřít soubor k přehrání.</span><span class="sxs-lookup"><span data-stu-id="f2e8b-107">Clicking the button opens a standard windows <xref:System.Windows.Forms.OpenFileDialog> dialog box so that you can open a file to play.</span></span> <span data-ttu-id="f2e8b-108">Pokud je vybraná souboru wave, se přehrávají pomocí `PlaySound()` metoda winmm. Metoda sestavení knihovny DLL.</span><span class="sxs-lookup"><span data-stu-id="f2e8b-108">When a wave file is selected, it is played by using the `PlaySound()` method of the winmm.DLL assembly method.</span></span> <span data-ttu-id="f2e8b-109">Další informace o společnosti winmm.dll `PlaySound` metodu, najdete v části [pomocí funkce PlaySound zvukového průběhu, zvukové soubory](https://msdn.microsoft.com/library/aa910379.aspx).</span><span class="sxs-lookup"><span data-stu-id="f2e8b-109">For more information about winmm.dll's `PlaySound` method, see [Using the PlaySound function with Waveform-Audio Files](https://msdn.microsoft.com/library/aa910379.aspx).</span></span> <span data-ttu-id="f2e8b-110">Procházet a vyberte soubor, který má příponu WAV a pak klikněte na tlačítko **otevřete** pro přehrání souboru wave pomocí platformy vyvolání.</span><span class="sxs-lookup"><span data-stu-id="f2e8b-110">Browse and select a file that has a .wav extension, and then click **Open** to play the wave file by using platform invoke.</span></span> <span data-ttu-id="f2e8b-111">Textové pole zobrazuje úplnou cestu vybraný soubor.</span><span class="sxs-lookup"><span data-stu-id="f2e8b-111">A text box shows the full path of the file selected.</span></span>  
  
 <span data-ttu-id="f2e8b-112">**Otevřených souborů** dialogové okno je vyfiltrovány a zobrazí se pouze soubory, které mají příponu WAV prostřednictvím nastavení filtru:</span><span class="sxs-lookup"><span data-stu-id="f2e8b-112">The **Open Files** dialog box is filtered to show only files that have a .wav extension through the filter settings:</span></span>  
  
 [!code-csharp[csProgGuideInterop#5](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-platform-invoke-to-play-a-wave-file_1.cs)]  
  
 [!code-csharp[csProgGuideInterop#3](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-platform-invoke-to-play-a-wave-file_2.cs)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="f2e8b-113">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="f2e8b-113">Compiling the Code</span></span>  
  
### <a name="to-compile-the-code"></a><span data-ttu-id="f2e8b-114">Kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="f2e8b-114">To compile the code</span></span>  
  
1.  <span data-ttu-id="f2e8b-115">Vytvořte nový projekt aplikace Windows v C# v sadě Visual Studio a pojmenujte ji **WinSound**.</span><span class="sxs-lookup"><span data-stu-id="f2e8b-115">Create a new C# Windows Application project in Visual Studio and name it **WinSound**.</span></span>  
  
2.  <span data-ttu-id="f2e8b-116">Výše uvedený kód zkopírujte a vložte ho přes obsah `Form1.cs` souboru.</span><span class="sxs-lookup"><span data-stu-id="f2e8b-116">Copy the code above, and paste it over the contents of the `Form1.cs` file.</span></span>  
  
3.  <span data-ttu-id="f2e8b-117">Zkopírujte následující kód a vložte jej do `Form1.Designer.cs` v souboru `InitializeComponent()` metoda po existující kód.</span><span class="sxs-lookup"><span data-stu-id="f2e8b-117">Copy the following code, and paste it in the `Form1.Designer.cs` file, in the `InitializeComponent()` method, after any existing code.</span></span>  
  
     [!code-csharp[csProgGuideInterop#4](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-platform-invoke-to-play-a-wave-file_3.cs)]  
  
4.  <span data-ttu-id="f2e8b-118">Zkompilování a spuštění kódu.</span><span class="sxs-lookup"><span data-stu-id="f2e8b-118">Compile and run the code.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="f2e8b-119">Zabezpečení rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="f2e8b-119">.NET Framework Security</span></span>  
 <span data-ttu-id="f2e8b-120">Další informace najdete v tématu [zabezpečení rozhraní .NET Framework](https://technet.microsoft.com/en-us/security/).</span><span class="sxs-lookup"><span data-stu-id="f2e8b-120">For more information, see [.NET Framework Security](https://technet.microsoft.com/en-us/security/).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2e8b-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="f2e8b-121">See Also</span></span>  
 [<span data-ttu-id="f2e8b-122">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="f2e8b-122">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="f2e8b-123">Přehled interoperability</span><span class="sxs-lookup"><span data-stu-id="f2e8b-123">Interoperability Overview</span></span>](../../../csharp/programming-guide/interop/interoperability-overview.md)  
 [<span data-ttu-id="f2e8b-124">Vyvolání bližší pohled na platformy</span><span class="sxs-lookup"><span data-stu-id="f2e8b-124">A Closer Look at Platform Invoke</span></span>](../../../framework/interop/consuming-unmanaged-dll-functions.md#a-closer-look-at-platform-invoke)  
 [<span data-ttu-id="f2e8b-125">Zařazování dat s voláním platformy</span><span class="sxs-lookup"><span data-stu-id="f2e8b-125">Marshaling Data with Platform Invoke</span></span>](../../../framework/interop/marshaling-data-with-platform-invoke.md)
