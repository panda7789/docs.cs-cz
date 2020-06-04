---
title: Přístup k prostředkům počítače
ms.date: 07/20/2015
helpviewer_keywords:
- computer resources [Visual Basic]
- My.Computer object [Visual Basic], tasks
- computer resources [Visual Basic], accessing
ms.assetid: 75b81c88-f7c0-46e0-95c8-0c006d2120f9
ms.openlocfilehash: 9595abaa1daa2b4a4436577d58856183dcb4d9ac
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401781"
---
# <a name="accessing-computer-resources-visual-basic"></a><span data-ttu-id="a6589-102">Přístup k prostředkům počítače (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a6589-102">Accessing computer resources (Visual Basic)</span></span>

<span data-ttu-id="a6589-103">`My.Computer`Objekt je jedním ze tří centrálních objektů v nástroji `My` , který poskytuje přístup k informacím a běžně používaným funkcím.</span><span class="sxs-lookup"><span data-stu-id="a6589-103">The `My.Computer` object is one of the three central objects in `My`, providing access to information and commonly used functionality.</span></span> <span data-ttu-id="a6589-104">`My.Computer`poskytuje metody, vlastnosti a události pro přístup k počítači, na kterém je aplikace spuštěná.</span><span class="sxs-lookup"><span data-stu-id="a6589-104">`My.Computer` provides methods, properties, and events for accessing the computer on which the application is running.</span></span> <span data-ttu-id="a6589-105">Mezi tyto objekty patří:</span><span class="sxs-lookup"><span data-stu-id="a6589-105">Its objects include:</span></span>

- <xref:Microsoft.VisualBasic.Devices.Audio>
- <span data-ttu-id="a6589-106">Schránka ( <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy> )</span><span class="sxs-lookup"><span data-stu-id="a6589-106">Clipboard (<xref:Microsoft.VisualBasic.MyServices.ClipboardProxy>)</span></span>
- <xref:Microsoft.VisualBasic.Devices.Clock>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:Microsoft.VisualBasic.Devices.ServerComputer.Info%2A>
- <xref:Microsoft.VisualBasic.Devices.Keyboard>
- <xref:Microsoft.VisualBasic.Devices.Mouse>
- <xref:Microsoft.VisualBasic.Devices.Network>
- <xref:Microsoft.VisualBasic.Devices.Ports>
- <span data-ttu-id="a6589-107">Registr ( <xref:Microsoft.VisualBasic.MyServices.RegistryProxy> )</span><span class="sxs-lookup"><span data-stu-id="a6589-107">Registry (<xref:Microsoft.VisualBasic.MyServices.RegistryProxy>)</span></span>

## <a name="in-this-section"></a><span data-ttu-id="a6589-108">V této části</span><span class="sxs-lookup"><span data-stu-id="a6589-108">In this section</span></span>

[<span data-ttu-id="a6589-109">Přehrávání zvuků</span><span class="sxs-lookup"><span data-stu-id="a6589-109">Playing Sounds</span></span>](playing-sounds.md)  
<span data-ttu-id="a6589-110">Zobrazí seznam úkolů, ke kterým se `My.Computer.Audio` jedná, například přehrávání zvuku na pozadí.</span><span class="sxs-lookup"><span data-stu-id="a6589-110">Lists tasks associated with `My.Computer.Audio`, such as playing a sound in the background.</span></span>

[<span data-ttu-id="a6589-111">Ukládání dat do schránky a čtení ze schránky</span><span class="sxs-lookup"><span data-stu-id="a6589-111">Storing Data to and Reading from the Clipboard</span></span>](storing-data-to-and-reading-from-the-clipboard.md)  
<span data-ttu-id="a6589-112">Obsahuje seznam úkolů přidružených k `My.Computer.Clipboard` , například čtení dat z nebo zápis dat do schránky.</span><span class="sxs-lookup"><span data-stu-id="a6589-112">Lists tasks associated with `My.Computer.Clipboard`, such as reading data from or writing data to the Clipboard.</span></span>

[<span data-ttu-id="a6589-113">Získání informací o počítači</span><span class="sxs-lookup"><span data-stu-id="a6589-113">Getting Information about the Computer</span></span>](getting-information-about-the-computer.md)  
<span data-ttu-id="a6589-114">Obsahuje seznam úkolů přidružených k, jako je například `My.Computer.Info` určení úplného názvu nebo IP adresy počítače.</span><span class="sxs-lookup"><span data-stu-id="a6589-114">Lists tasks associated with `My.Computer.Info`, such as determining a computer's full name or IP addresses.</span></span>

[<span data-ttu-id="a6589-115">Přístup ke klávesnici</span><span class="sxs-lookup"><span data-stu-id="a6589-115">Accessing the Keyboard</span></span>](accessing-the-keyboard.md)  
<span data-ttu-id="a6589-116">Obsahuje seznam úkolů přidružených k `My.Computer.Keyboard` , například určení, zda je Caps Lock zapnutá.</span><span class="sxs-lookup"><span data-stu-id="a6589-116">Lists tasks associated with `My.Computer.Keyboard`, such as determining whether CAPS LOCK is on.</span></span>

[<span data-ttu-id="a6589-117">Přístup k myši</span><span class="sxs-lookup"><span data-stu-id="a6589-117">Accessing the Mouse</span></span>](accessing-the-mouse.md)  
<span data-ttu-id="a6589-118">Zobrazí seznam úkolů `My.Computer.Mouse` , které jsou k dispozici, například určení, zda je myš přítomna.</span><span class="sxs-lookup"><span data-stu-id="a6589-118">Lists tasks associated with `My.Computer.Mouse`, such as determining whether a mouse is present.</span></span>

[<span data-ttu-id="a6589-119">Provádění síťových operací</span><span class="sxs-lookup"><span data-stu-id="a6589-119">Performing Network Operations</span></span>](performing-network-operations.md)  
<span data-ttu-id="a6589-120">Vypisuje úkoly, které jsou k `My.Computer.Network` , například nahrávání nebo stahování souborů.</span><span class="sxs-lookup"><span data-stu-id="a6589-120">Lists tasks associated with `My.Computer.Network`, such as uploading or downloading files.</span></span>

[<span data-ttu-id="a6589-121">Přístup k portům počítače</span><span class="sxs-lookup"><span data-stu-id="a6589-121">Accessing the Computer's Ports</span></span>](accessing-the-computer-s-ports.md)  
<span data-ttu-id="a6589-122">Obsahuje seznam úloh `My.Computer.Ports` , které jsou k dispozici, například zobrazení dostupných sériových portů nebo odesílání řetězců na sériové porty.</span><span class="sxs-lookup"><span data-stu-id="a6589-122">Lists tasks associated with `My.Computer.Ports`, such as showing available serial ports or sending strings to serial ports.</span></span>

[<span data-ttu-id="a6589-123">Čtení z registru a zápis do něj</span><span class="sxs-lookup"><span data-stu-id="a6589-123">Reading from and Writing to the Registry</span></span>](reading-from-and-writing-to-the-registry.md)  
<span data-ttu-id="a6589-124">Obsahuje seznam úkolů přidružených k `My.Computer.Registry` , například čtení dat z nebo zápis dat do klíčů registru.</span><span class="sxs-lookup"><span data-stu-id="a6589-124">Lists tasks associated with `My.Computer.Registry`, such as reading data from or writing data to registry keys.</span></span>
