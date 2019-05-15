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
# <a name="reading-from-and-writing-to-the-registry-visual-basic"></a>Čtení z registru a zápis do něj pomocí oboru názvů My (Visual Basic)
Toto téma popisuje úlohy a koncepční témata, které jsou spojeny s registrem.  
  
 Při programování v jazyce Visual Basic, můžete získat přístup k registru pomocí funkce poskytované jazyka Visual Basic nebo registru třídy rozhraní .NET Framework. Informace registru hostitele z operačního systému, stejně jako informace z aplikací hostovaných na počítači. Práce s registrem může ohrozit zabezpečení tím, že nevhodný přístup k systémovým prostředkům nebo chráněné informace.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Postupy: Vytvořte klíč registru a nastavení jeho hodnoty](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-create-a-registry-key-and-set-its-value.md)  
 Popisuje způsob použití `CreateSubKey` a `SetValue` metody `My.Computer.Registry` objekt k vytvoření klíče registru a nastavení jeho hodnoty.  
  
 [Postupy: Načtení hodnoty z klíče registru](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-read-a-value-from-a-registry-key.md)  
 Popisuje způsob použití `GetValue` metodu `My.Computer.Registry` objektu k načtení hodnoty z klíče registru.  
  
 [Postupy: Odstranění klíče z registru](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-delete-a-registry-key.md)  
 Popisuje způsob použití `DeleteSubKey` metodu `My.Computer.Registry.CurrentUser` vlastnosti k odstranění klíče z registru.  
  
 [Čtení z registru a zápis do něj s použitím oboru názvů Microsoft.Win32](../../../../visual-basic/developing-apps/programming/computer-resources/reading-from-and-writing-to-the-registry-using-the-microsoft-win32-namespace.md)  
 Popisuje způsob použití `Registry` a `RegistryKey` tříd rozhraní .NET Framework pro přístup k registru.  
  
 [Zabezpečení a registr](../../../../visual-basic/developing-apps/programming/computer-resources/security-and-the-registry.md)  
 Tento článek popisuje problémy se zabezpečením týkajících se registru.  
  
## <a name="related-sections"></a>Související oddíly  
 <xref:Microsoft.VisualBasic.MyServices.RegistryProxy>  
 Uvádí a vysvětluje členů `My.Computer.Registry` objektu.  
  
 <xref:Microsoft.Win32.Registry>  
 Obsahuje přehled nástroje `Registry` třídy společně s odkazy na jednotlivé klíče a členy.
