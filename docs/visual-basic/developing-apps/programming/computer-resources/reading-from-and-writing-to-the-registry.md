---
title: Čtení z registru a zápis do něj pomocí oboru názvů My (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- My.Computer.Registry object, tasks
- registry [Visual Basic], writing to
- registry [Visual Basic], reading
ms.assetid: a13da106-185b-41d7-b23c-416da65e21e4
ms.openlocfilehash: 6ce05b956ebf9a544eb8c95165b0f709c694f334
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33584615"
---
# <a name="reading-from-and-writing-to-the-registry-visual-basic"></a>Čtení z registru a zápis do něj pomocí oboru názvů My (Visual Basic)
Toto téma popisuje úlohy a koncepční témata, které jsou přidruženy registru.  
  
 Při programování v jazyce Visual Basic, můžete získat přístup k registru formou funkce poskytované jazyka Visual Basic nebo registru tříd rozhraní .NET Framework. Registru hostuje informace z operačního systému a informace z aplikace hostované na počítači. Práce s registrem může ohrozit zabezpečení tím, že nevhodný přístup k systémovým prostředkům nebo chráněný informace.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Postupy: Vytvoření klíče registru a nastavení jeho hodnoty](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-create-a-registry-key-and-set-its-value.md)  
 Popisuje postup použití `CreateSubKey` a `SetValue` metody `My.Computer.Registry` objekt k vytvoření klíče registru a nastavení jeho hodnoty.  
  
 [Postupy: Načtení hodnoty z klíče registru](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-read-a-value-from-a-registry-key.md)  
 Popisuje postup použití `GetValue` metodu `My.Computer.Registry` objekt k načtení hodnoty z klíče registru.  
  
 [Postupy: Odstranění klíče z registru](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-delete-a-registry-key.md)  
 Popisuje postup použití `DeleteSubKey` metodu `My.Computer.Registry.CurrentUser` vlastnost odstranit klíč registru.  
  
 [Čtení z registru a zápis do něj s použitím oboru názvů Microsoft.Win32](../../../../visual-basic/developing-apps/programming/computer-resources/reading-from-and-writing-to-the-registry-using-the-microsoft-win32-namespace.md)  
 Popisuje postup použití `Registry` a `RegistryKey` třídy [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] pro přístup k registru.  
  
 [Zabezpečení a registr](../../../../visual-basic/developing-apps/programming/computer-resources/security-and-the-registry.md)  
 Popisuje problémy se zabezpečením zahrnující registru.  
  
## <a name="related-sections"></a>Související oddíly  
 <xref:Microsoft.VisualBasic.MyServices.RegistryProxy>  
 Uvádí a vysvětluje členy `My.Computer.Registry` objektu.  
  
 <xref:Microsoft.Win32.Registry>  
 Obsahuje přehled nástroje `Registry` třída, spolu s odkazy na jednotlivé klíče a členy.
