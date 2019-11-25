---
title: Čtení z registru a zápis do něj
ms.date: 07/20/2015
helpviewer_keywords:
- My.Computer.Registry object, tasks
- registry [Visual Basic], writing to
- registry [Visual Basic], reading
ms.assetid: a13da106-185b-41d7-b23c-416da65e21e4
ms.openlocfilehash: 89db9ef9db4235c069d6239d32e4f8679fbabf0b
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349752"
---
# <a name="reading-from-and-writing-to-the-registry-visual-basic"></a>Čtení z registru a zápis do něj pomocí oboru názvů My (Visual Basic)

This topic describes task and conceptual topics that are associated with the registry.  
  
 When programming in Visual Basic, you can choose to access the registry by means of either the functions provided by Visual Basic or the registry classes of the .NET Framework. The registry hosts information from the operating system as well as information from applications hosted on the machine. Working with the registry may compromise security by allowing inappropriate access to system resources or protected information.  
  
## <a name="in-this-section"></a>V tomto oddílu  

 [Postupy: Vytvoření klíče registru a nastavení jeho hodnoty](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-create-a-registry-key-and-set-its-value.md)  
 Describes how to use the `CreateSubKey` and `SetValue` methods of the `My.Computer.Registry` object to create a registry key and set its value.  
  
 [Postupy: Načtení hodnoty z klíče registru](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-read-a-value-from-a-registry-key.md)  
 Describes how to use the `GetValue` method of the `My.Computer.Registry` object to read a value from a registry key.  
  
 [Postupy: Odstranění klíče z registru](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-delete-a-registry-key.md)  
 Describes how to use the `DeleteSubKey` method of the `My.Computer.Registry.CurrentUser` property to delete a registry key.  
  
 [Čtení z registru a zápis do něj s použitím oboru názvů Microsoft.Win32](../../../../visual-basic/developing-apps/programming/computer-resources/reading-from-and-writing-to-the-registry-using-the-microsoft-win32-namespace.md)  
 Describes how to use the `Registry` and `RegistryKey` classes of the .NET Framework to access the registry.  
  
 [Zabezpečení a registr](../../../../visual-basic/developing-apps/programming/computer-resources/security-and-the-registry.md)  
 Discusses security issues involving the registry.  
  
## <a name="related-sections"></a>Související oddíly  

 <xref:Microsoft.VisualBasic.MyServices.RegistryProxy>  
 Lists and explains members of the `My.Computer.Registry` object.  
  
 <xref:Microsoft.Win32.Registry>  
 Presents an overview of the `Registry` class, along with links to individual keys and members.
