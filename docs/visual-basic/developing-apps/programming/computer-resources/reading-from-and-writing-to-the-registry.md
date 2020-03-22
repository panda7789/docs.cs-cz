---
title: Čtení z registru a zápis do něj
ms.date: 07/20/2015
helpviewer_keywords:
- My.Computer.Registry object, tasks
- registry [Visual Basic], writing to
- registry [Visual Basic], reading
ms.assetid: a13da106-185b-41d7-b23c-416da65e21e4
ms.openlocfilehash: 89db9ef9db4235c069d6239d32e4f8679fbabf0b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "74349752"
---
# <a name="reading-from-and-writing-to-the-registry-visual-basic"></a><span data-ttu-id="8c48f-102">Čtení z registru a zápis do něj pomocí oboru názvů My (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8c48f-102">Reading from and Writing to the Registry (Visual Basic)</span></span>

<span data-ttu-id="8c48f-103">Toto téma popisuje témata úkolů a koncepční témata, která jsou přidružena k registru.</span><span class="sxs-lookup"><span data-stu-id="8c48f-103">This topic describes task and conceptual topics that are associated with the registry.</span></span>  
  
 <span data-ttu-id="8c48f-104">Při programování v jazyce Visual Basic můžete zvolit přístup k registru pomocí funkcí poskytovaných jazykem Visual Basic nebo tříd registru rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="8c48f-104">When programming in Visual Basic, you can choose to access the registry by means of either the functions provided by Visual Basic or the registry classes of the .NET Framework.</span></span> <span data-ttu-id="8c48f-105">Registr hostuje informace z operačního systému, stejně jako informace z aplikací hostovaných v počítači.</span><span class="sxs-lookup"><span data-stu-id="8c48f-105">The registry hosts information from the operating system as well as information from applications hosted on the machine.</span></span> <span data-ttu-id="8c48f-106">Práce s registrem může ohrozit zabezpečení povolením nevhodného přístupu k systémovým prostředkům nebo chráněným informacím.</span><span class="sxs-lookup"><span data-stu-id="8c48f-106">Working with the registry may compromise security by allowing inappropriate access to system resources or protected information.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="8c48f-107">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="8c48f-107">In This Section</span></span>  

 [<span data-ttu-id="8c48f-108">Postupy: Vytvoření klíče registru a nastavení jeho hodnoty</span><span class="sxs-lookup"><span data-stu-id="8c48f-108">How to: Create a Registry Key and Set Its Value</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-create-a-registry-key-and-set-its-value.md)  
 <span data-ttu-id="8c48f-109">Popisuje, jak pomocí `CreateSubKey` `SetValue` metody a `My.Computer.Registry` objektu vytvořit klíč registru a nastavit jeho hodnotu.</span><span class="sxs-lookup"><span data-stu-id="8c48f-109">Describes how to use the `CreateSubKey` and `SetValue` methods of the `My.Computer.Registry` object to create a registry key and set its value.</span></span>  
  
 [<span data-ttu-id="8c48f-110">Postupy: Načtení hodnoty z klíče registru</span><span class="sxs-lookup"><span data-stu-id="8c48f-110">How to: Read a Value from a Registry Key</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-read-a-value-from-a-registry-key.md)  
 <span data-ttu-id="8c48f-111">Popisuje způsob použití `GetValue` metody objektu `My.Computer.Registry` ke čtení hodnoty z klíče registru.</span><span class="sxs-lookup"><span data-stu-id="8c48f-111">Describes how to use the `GetValue` method of the `My.Computer.Registry` object to read a value from a registry key.</span></span>  
  
 [<span data-ttu-id="8c48f-112">Postupy: Odstranění klíče z registru</span><span class="sxs-lookup"><span data-stu-id="8c48f-112">How to: Delete a Registry Key</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-delete-a-registry-key.md)  
 <span data-ttu-id="8c48f-113">Popisuje způsob použití `DeleteSubKey` metody vlastnosti `My.Computer.Registry.CurrentUser` k odstranění klíče registru.</span><span class="sxs-lookup"><span data-stu-id="8c48f-113">Describes how to use the `DeleteSubKey` method of the `My.Computer.Registry.CurrentUser` property to delete a registry key.</span></span>  
  
 [<span data-ttu-id="8c48f-114">Čtení z registru a zápis do něj s použitím oboru názvů Microsoft.Win32</span><span class="sxs-lookup"><span data-stu-id="8c48f-114">Reading from and Writing to the Registry Using the Microsoft.Win32 Namespace</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/reading-from-and-writing-to-the-registry-using-the-microsoft-win32-namespace.md)  
 <span data-ttu-id="8c48f-115">Popisuje způsob použití `Registry` `RegistryKey` a třídy rozhraní .NET Framework pro přístup k registru.</span><span class="sxs-lookup"><span data-stu-id="8c48f-115">Describes how to use the `Registry` and `RegistryKey` classes of the .NET Framework to access the registry.</span></span>  
  
 [<span data-ttu-id="8c48f-116">Zabezpečení a registr</span><span class="sxs-lookup"><span data-stu-id="8c48f-116">Security and the Registry</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/security-and-the-registry.md)  
 <span data-ttu-id="8c48f-117">Popisuje problémy se zabezpečením týkající se registru.</span><span class="sxs-lookup"><span data-stu-id="8c48f-117">Discusses security issues involving the registry.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="8c48f-118">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="8c48f-118">Related Sections</span></span>  

 <xref:Microsoft.VisualBasic.MyServices.RegistryProxy>  
 <span data-ttu-id="8c48f-119">Uvádí a vysvětluje členy `My.Computer.Registry` objektu.</span><span class="sxs-lookup"><span data-stu-id="8c48f-119">Lists and explains members of the `My.Computer.Registry` object.</span></span>  
  
 <xref:Microsoft.Win32.Registry>  
 <span data-ttu-id="8c48f-120">Představuje přehled třídy, `Registry` spolu s odkazy na jednotlivé klíče a členy.</span><span class="sxs-lookup"><span data-stu-id="8c48f-120">Presents an overview of the `Registry` class, along with links to individual keys and members.</span></span>
