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
# <a name="reading-from-and-writing-to-the-registry-visual-basic"></a>Čtení z registru a zápis do něj pomocí oboru názvů My (Visual Basic)

Toto téma popisuje témata úkolů a koncepční témata, která jsou přidružena k registru.  
  
 Při programování v jazyce Visual Basic můžete zvolit přístup k registru pomocí funkcí poskytovaných jazykem Visual Basic nebo tříd registru rozhraní .NET Framework. Registr hostuje informace z operačního systému, stejně jako informace z aplikací hostovaných v počítači. Práce s registrem může ohrozit zabezpečení povolením nevhodného přístupu k systémovým prostředkům nebo chráněným informacím.  
  
## <a name="in-this-section"></a>V tomto oddílu  

 [Postupy: Vytvoření klíče registru a nastavení jeho hodnoty](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-create-a-registry-key-and-set-its-value.md)  
 Popisuje, jak pomocí `CreateSubKey` `SetValue` metody a `My.Computer.Registry` objektu vytvořit klíč registru a nastavit jeho hodnotu.  
  
 [Postupy: Načtení hodnoty z klíče registru](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-read-a-value-from-a-registry-key.md)  
 Popisuje způsob použití `GetValue` metody objektu `My.Computer.Registry` ke čtení hodnoty z klíče registru.  
  
 [Postupy: Odstranění klíče z registru](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-delete-a-registry-key.md)  
 Popisuje způsob použití `DeleteSubKey` metody vlastnosti `My.Computer.Registry.CurrentUser` k odstranění klíče registru.  
  
 [Čtení z registru a zápis do něj s použitím oboru názvů Microsoft.Win32](../../../../visual-basic/developing-apps/programming/computer-resources/reading-from-and-writing-to-the-registry-using-the-microsoft-win32-namespace.md)  
 Popisuje způsob použití `Registry` `RegistryKey` a třídy rozhraní .NET Framework pro přístup k registru.  
  
 [Zabezpečení a registr](../../../../visual-basic/developing-apps/programming/computer-resources/security-and-the-registry.md)  
 Popisuje problémy se zabezpečením týkající se registru.  
  
## <a name="related-sections"></a>Související oddíly  

 <xref:Microsoft.VisualBasic.MyServices.RegistryProxy>  
 Uvádí a vysvětluje členy `My.Computer.Registry` objektu.  
  
 <xref:Microsoft.Win32.Registry>  
 Představuje přehled třídy, `Registry` spolu s odkazy na jednotlivé klíče a členy.
