---
title: Přístup k prostředkům počítače (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- computer resources [Visual Basic]
- My.Computer object [Visual Basic], tasks
- computer resources [Visual Basic], accessing
ms.assetid: 75b81c88-f7c0-46e0-95c8-0c006d2120f9
ms.openlocfilehash: 7128a71f28d1755a14fcda5f09bee11202ab4154
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2018
ms.locfileid: "43001858"
---
# <a name="accessing-computer-resources-visual-basic"></a><span data-ttu-id="347d7-102">Přístup k prostředkům počítače (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="347d7-102">Accessing computer resources (Visual Basic)</span></span>

<span data-ttu-id="347d7-103">`My.Computer` Objektu je jednou tři centrální objektů v `My`, poskytuje přístup k informacím a běžně používané funkce.</span><span class="sxs-lookup"><span data-stu-id="347d7-103">The `My.Computer` object is one of the three central objects in `My`, providing access to information and commonly used functionality.</span></span> <span data-ttu-id="347d7-104">`My.Computer` poskytuje metody, vlastnosti a události pro přístup k počítači, na kterém je aplikace spuštěna.</span><span class="sxs-lookup"><span data-stu-id="347d7-104">`My.Computer` provides methods, properties, and events for accessing the computer on which the application is running.</span></span> <span data-ttu-id="347d7-105">Jeho objekty patří:</span><span class="sxs-lookup"><span data-stu-id="347d7-105">Its objects include:</span></span>  
  
-   <xref:Microsoft.VisualBasic.Devices.Audio>
-   <span data-ttu-id="347d7-106">Schránka (<xref:Microsoft.VisualBasic.MyServices.ClipboardProxy>)</span><span class="sxs-lookup"><span data-stu-id="347d7-106">Clipboard (<xref:Microsoft.VisualBasic.MyServices.ClipboardProxy>)</span></span>
-   <xref:Microsoft.VisualBasic.Devices.Clock>
-   <xref:Microsoft.VisualBasic.FileIO.FileSystem>
-   <xref:Microsoft.VisualBasic.Devices.ServerComputer.Info%2A>
-   <xref:Microsoft.VisualBasic.Devices.Keyboard>
-   <xref:Microsoft.VisualBasic.Devices.Mouse>
-   <xref:Microsoft.VisualBasic.Devices.Network>
-   <xref:Microsoft.VisualBasic.Devices.Ports>
-   <span data-ttu-id="347d7-107">Registr (<xref:Microsoft.VisualBasic.MyServices.RegistryProxy>)</span><span class="sxs-lookup"><span data-stu-id="347d7-107">Registry (<xref:Microsoft.VisualBasic.MyServices.RegistryProxy>)</span></span>
  
## <a name="in-this-section"></a><span data-ttu-id="347d7-108">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="347d7-108">In this section</span></span>

<span data-ttu-id="347d7-109">[Přehrávání zvuků](../../../../visual-basic/developing-apps/programming/computer-resources/playing-sounds.md) </span><span class="sxs-lookup"><span data-stu-id="347d7-109">[Playing Sounds](../../../../visual-basic/developing-apps/programming/computer-resources/playing-sounds.md) </span></span>  
<span data-ttu-id="347d7-110">Obsahuje seznam úloh přidružených k `My.Computer.Audio`, jako je přehrávání zvuku na pozadí.</span><span class="sxs-lookup"><span data-stu-id="347d7-110">Lists tasks associated with `My.Computer.Audio`, such as playing a sound in the background.</span></span>

<span data-ttu-id="347d7-111">[Ukládání dat do schránky a čtení ze schránky](../../../../visual-basic/developing-apps/programming/computer-resources/storing-data-to-and-reading-from-the-clipboard.md) </span><span class="sxs-lookup"><span data-stu-id="347d7-111">[Storing Data to and Reading from the Clipboard](../../../../visual-basic/developing-apps/programming/computer-resources/storing-data-to-and-reading-from-the-clipboard.md) </span></span>  
<span data-ttu-id="347d7-112">Obsahuje seznam úloh přidružených k `My.Computer.Clipboard`, jako je čtení dat z nebo zápis dat do schránky.</span><span class="sxs-lookup"><span data-stu-id="347d7-112">Lists tasks associated with `My.Computer.Clipboard`, such as reading data from or writing data to the Clipboard.</span></span>

<span data-ttu-id="347d7-113">[Získání informací o počítači](../../../../visual-basic/developing-apps/programming/computer-resources/getting-information-about-the-computer.md) </span><span class="sxs-lookup"><span data-stu-id="347d7-113">[Getting Information about the Computer](../../../../visual-basic/developing-apps/programming/computer-resources/getting-information-about-the-computer.md) </span></span>  
<span data-ttu-id="347d7-114">Obsahuje seznam úloh přidružených k `My.Computer.Info`, jako je například určení úplný název počítače nebo IP adresy.</span><span class="sxs-lookup"><span data-stu-id="347d7-114">Lists tasks associated with `My.Computer.Info`, such as determining a computer's full name or IP addresses.</span></span>

<span data-ttu-id="347d7-115">[Přístup ke klávesnici](../../../../visual-basic/developing-apps/programming/computer-resources/accessing-the-keyboard.md) </span><span class="sxs-lookup"><span data-stu-id="347d7-115">[Accessing the Keyboard](../../../../visual-basic/developing-apps/programming/computer-resources/accessing-the-keyboard.md) </span></span>  
<span data-ttu-id="347d7-116">Obsahuje seznam úloh přidružených k `My.Computer.Keyboard`, jako je například určení, zda CAPS LOCK je aktivní.</span><span class="sxs-lookup"><span data-stu-id="347d7-116">Lists tasks associated with `My.Computer.Keyboard`, such as determining whether CAPS LOCK is on.</span></span>

<span data-ttu-id="347d7-117">[Přístup k myši](../../../../visual-basic/developing-apps/programming/computer-resources/accessing-the-mouse.md) </span><span class="sxs-lookup"><span data-stu-id="347d7-117">[Accessing the Mouse](../../../../visual-basic/developing-apps/programming/computer-resources/accessing-the-mouse.md) </span></span>  
<span data-ttu-id="347d7-118">Obsahuje seznam úloh přidružených k `My.Computer.Mouse`, jako je například určování, zda je k dispozici myši.</span><span class="sxs-lookup"><span data-stu-id="347d7-118">Lists tasks associated with `My.Computer.Mouse`, such as determining whether a mouse is present.</span></span>

<span data-ttu-id="347d7-119">[Provádění síťových operací](../../../../visual-basic/developing-apps/programming/computer-resources/performing-network-operations.md) </span><span class="sxs-lookup"><span data-stu-id="347d7-119">[Performing Network Operations](../../../../visual-basic/developing-apps/programming/computer-resources/performing-network-operations.md) </span></span>  
<span data-ttu-id="347d7-120">Obsahuje seznam úloh přidružených k `My.Computer.Network`, jako jsou nahrávání nebo stahování souborů.</span><span class="sxs-lookup"><span data-stu-id="347d7-120">Lists tasks associated with `My.Computer.Network`, such as uploading or downloading files.</span></span>

<span data-ttu-id="347d7-121">[Přístup k portům počítače](../../../../visual-basic/developing-apps/programming/computer-resources/accessing-the-computer-s-ports.md) </span><span class="sxs-lookup"><span data-stu-id="347d7-121">[Accessing the Computer's Ports](../../../../visual-basic/developing-apps/programming/computer-resources/accessing-the-computer-s-ports.md) </span></span>  
<span data-ttu-id="347d7-122">Obsahuje seznam úloh přidružených k `My.Computer.Ports`, jako je například zobrazení dostupných sériových portů nebo odesílání řetězců na sériové porty.</span><span class="sxs-lookup"><span data-stu-id="347d7-122">Lists tasks associated with `My.Computer.Ports`, such as showing available serial ports or sending strings to serial ports.</span></span>

<span data-ttu-id="347d7-123">[Čtení a zápis do registru](../../../../visual-basic/developing-apps/programming/computer-resources/reading-from-and-writing-to-the-registry.md) </span><span class="sxs-lookup"><span data-stu-id="347d7-123">[Reading from and Writing to the Registry](../../../../visual-basic/developing-apps/programming/computer-resources/reading-from-and-writing-to-the-registry.md) </span></span>  
<span data-ttu-id="347d7-124">Obsahuje seznam úloh přidružených k `My.Computer.Registry`, jako je čtení dat z nebo zápis dat do klíče registru.</span><span class="sxs-lookup"><span data-stu-id="347d7-124">Lists tasks associated with `My.Computer.Registry`, such as reading data from or writing data to registry keys.</span></span>
