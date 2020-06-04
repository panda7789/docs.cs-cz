---
title: Čtení z registru a zápis do něj
ms.date: 07/20/2015
helpviewer_keywords:
- My.Computer.Registry object, tasks
- registry [Visual Basic], writing to
- registry [Visual Basic], reading
ms.assetid: a13da106-185b-41d7-b23c-416da65e21e4
ms.openlocfilehash: bb400ef89edaa4eb743aee3a7f2cc5b9dfec4534
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84360056"
---
# <a name="reading-from-and-writing-to-the-registry-visual-basic"></a>Čtení z registru a zápis do něj pomocí oboru názvů My (Visual Basic)

Toto téma popisuje úlohu a koncepční témata, která jsou přidružená k registru.  
  
 Při programování v Visual Basic můžete zvolit přístup k registru prostřednictvím funkcí poskytovaných Visual Basic nebo tříd registru .NET Framework. Registr hostuje informace z operačního systému a také informace z aplikací hostovaných v počítači. Práce s registrem může ohrozit zabezpečení tím, že umožňuje nevhodný přístup k systémovým prostředkům nebo chráněným informacím.  
  
## <a name="in-this-section"></a>V tomto oddílu  

 [Postupy: Vytvoření klíče registru a nastavení jeho hodnoty](how-to-create-a-registry-key-and-set-its-value.md)  
 Popisuje způsob použití `CreateSubKey` `SetValue` metod a `My.Computer.Registry` objektu k vytvoření klíče registru a nastavení jeho hodnoty.  
  
 [Postupy: Načtení hodnoty z klíče registru](how-to-read-a-value-from-a-registry-key.md)  
 Popisuje způsob použití `GetValue` metody `My.Computer.Registry` objektu ke čtení hodnoty z klíče registru.  
  
 [Postupy: Odstranění klíče z registru](how-to-delete-a-registry-key.md)  
 Popisuje, jak použít `DeleteSubKey` metodu `My.Computer.Registry.CurrentUser` Vlastnosti k odstranění klíče registru.  
  
 [Čtení z registru a zápis do něj s použitím oboru názvů Microsoft.Win32](reading-from-and-writing-to-the-registry-using-the-microsoft-win32-namespace.md)  
 Popisuje, jak použít `Registry` třídy a `RegistryKey` .NET Framework pro přístup k registru.  
  
 [Zabezpečení a registr](security-and-the-registry.md)  
 Popisuje problémy zabezpečení související s registrem.  
  
## <a name="related-sections"></a>Související oddíly  

 <xref:Microsoft.VisualBasic.MyServices.RegistryProxy>  
 Seznam a vysvětlení členů `My.Computer.Registry` objektu.  
  
 <xref:Microsoft.Win32.Registry>  
 Prezentuje přehled `Registry` třídy, spolu s odkazy na jednotlivé klíče a členy.
