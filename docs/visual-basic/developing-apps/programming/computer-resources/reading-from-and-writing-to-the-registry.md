---
title: Čtení z registru a zápis do něj pomocí oboru názvů My (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- My.Computer.Registry object, tasks
- registry [Visual Basic], writing to
- registry [Visual Basic], reading
ms.assetid: a13da106-185b-41d7-b23c-416da65e21e4
ms.openlocfilehash: fcc13d82a2b27221c13f9277585c21196b47003d
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/14/2019
ms.locfileid: "65591475"
---
# <a name="reading-from-and-writing-to-the-registry-visual-basic"></a><span data-ttu-id="8ddda-102">Čtení z registru a zápis do něj pomocí oboru názvů My (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8ddda-102">Reading from and Writing to the Registry (Visual Basic)</span></span>
<span data-ttu-id="8ddda-103">Toto téma popisuje úlohy a koncepční témata, které jsou spojeny s registrem.</span><span class="sxs-lookup"><span data-stu-id="8ddda-103">This topic describes task and conceptual topics that are associated with the registry.</span></span>  
  
 <span data-ttu-id="8ddda-104">Při programování v jazyce Visual Basic, můžete získat přístup k registru pomocí funkce poskytované jazyka Visual Basic nebo registru třídy rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="8ddda-104">When programming in Visual Basic, you can choose to access the registry by means of either the functions provided by Visual Basic or the registry classes of the .NET Framework.</span></span> <span data-ttu-id="8ddda-105">Informace registru hostitele z operačního systému, stejně jako informace z aplikací hostovaných na počítači.</span><span class="sxs-lookup"><span data-stu-id="8ddda-105">The registry hosts information from the operating system as well as information from applications hosted on the machine.</span></span> <span data-ttu-id="8ddda-106">Práce s registrem může ohrozit zabezpečení tím, že nevhodný přístup k systémovým prostředkům nebo chráněné informace.</span><span class="sxs-lookup"><span data-stu-id="8ddda-106">Working with the registry may compromise security by allowing inappropriate access to system resources or protected information.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="8ddda-107">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="8ddda-107">In This Section</span></span>  
 [<span data-ttu-id="8ddda-108">Postupy: Vytvořte klíč registru a nastavení jeho hodnoty</span><span class="sxs-lookup"><span data-stu-id="8ddda-108">How to: Create a Registry Key and Set Its Value</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-create-a-registry-key-and-set-its-value.md)  
 <span data-ttu-id="8ddda-109">Popisuje způsob použití `CreateSubKey` a `SetValue` metody `My.Computer.Registry` objekt k vytvoření klíče registru a nastavení jeho hodnoty.</span><span class="sxs-lookup"><span data-stu-id="8ddda-109">Describes how to use the `CreateSubKey` and `SetValue` methods of the `My.Computer.Registry` object to create a registry key and set its value.</span></span>  
  
 [<span data-ttu-id="8ddda-110">Postupy: Načtení hodnoty z klíče registru</span><span class="sxs-lookup"><span data-stu-id="8ddda-110">How to: Read a Value from a Registry Key</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-read-a-value-from-a-registry-key.md)  
 <span data-ttu-id="8ddda-111">Popisuje způsob použití `GetValue` metodu `My.Computer.Registry` objektu k načtení hodnoty z klíče registru.</span><span class="sxs-lookup"><span data-stu-id="8ddda-111">Describes how to use the `GetValue` method of the `My.Computer.Registry` object to read a value from a registry key.</span></span>  
  
 [<span data-ttu-id="8ddda-112">Postupy: Odstranění klíče z registru</span><span class="sxs-lookup"><span data-stu-id="8ddda-112">How to: Delete a Registry Key</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-delete-a-registry-key.md)  
 <span data-ttu-id="8ddda-113">Popisuje způsob použití `DeleteSubKey` metodu `My.Computer.Registry.CurrentUser` vlastnosti k odstranění klíče z registru.</span><span class="sxs-lookup"><span data-stu-id="8ddda-113">Describes how to use the `DeleteSubKey` method of the `My.Computer.Registry.CurrentUser` property to delete a registry key.</span></span>  
  
 [<span data-ttu-id="8ddda-114">Čtení z registru a zápis do něj s použitím oboru názvů Microsoft.Win32</span><span class="sxs-lookup"><span data-stu-id="8ddda-114">Reading from and Writing to the Registry Using the Microsoft.Win32 Namespace</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/reading-from-and-writing-to-the-registry-using-the-microsoft-win32-namespace.md)  
 <span data-ttu-id="8ddda-115">Popisuje způsob použití `Registry` a `RegistryKey` tříd rozhraní .NET Framework pro přístup k registru.</span><span class="sxs-lookup"><span data-stu-id="8ddda-115">Describes how to use the `Registry` and `RegistryKey` classes of the .NET Framework to access the registry.</span></span>  
  
 [<span data-ttu-id="8ddda-116">Zabezpečení a registr</span><span class="sxs-lookup"><span data-stu-id="8ddda-116">Security and the Registry</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/security-and-the-registry.md)  
 <span data-ttu-id="8ddda-117">Tento článek popisuje problémy se zabezpečením týkajících se registru.</span><span class="sxs-lookup"><span data-stu-id="8ddda-117">Discusses security issues involving the registry.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="8ddda-118">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="8ddda-118">Related Sections</span></span>  
 <xref:Microsoft.VisualBasic.MyServices.RegistryProxy>  
 <span data-ttu-id="8ddda-119">Uvádí a vysvětluje členů `My.Computer.Registry` objektu.</span><span class="sxs-lookup"><span data-stu-id="8ddda-119">Lists and explains members of the `My.Computer.Registry` object.</span></span>  
  
 <xref:Microsoft.Win32.Registry>  
 <span data-ttu-id="8ddda-120">Obsahuje přehled nástroje `Registry` třídy společně s odkazy na jednotlivé klíče a členy.</span><span class="sxs-lookup"><span data-stu-id="8ddda-120">Presents an overview of the `Registry` class, along with links to individual keys and members.</span></span>
