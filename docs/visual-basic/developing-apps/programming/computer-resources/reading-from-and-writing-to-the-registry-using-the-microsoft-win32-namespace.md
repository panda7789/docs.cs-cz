---
title: "Čtení z registru a zápis do něj s použitím oboru názvů Microsoft.Win32 (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- registry [Visual Basic]
ms.assetid: 4a0dcce0-c27b-4199-baa8-ee4528da6a56
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 462cc5c3854035cfc04c7c5df6905c2cfbd486ed
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="reading-from-and-writing-to-the-registry-using-the-microsoftwin32-namespace-visual-basic"></a>Čtení z registru a zápis do něj s použitím oboru názvů Microsoft.Win32 (Visual Basic)
I když `My.Computer.Registry` by měla zahrnovat základní potřeb při programové ošetření registru, můžete také použít <xref:Microsoft.Win32.Registry> a <xref:Microsoft.Win32.RegistryKey> třídy v <xref:Microsoft.Win32> obor názvů [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].  
  
## <a name="keys-in-the-registry-class"></a>Klíče v registru – třída  
 <xref:Microsoft.Win32.Registry> Třída poskytuje základní registru klíčů, které lze použít pro přístup k podklíče a jejich hodnoty. Základní klíče jsou jen pro čtení. Následující tabulka uvádí a popisuje sedm klíčů vystavené <xref:Microsoft.Win32.Registry> třídy.  
  
|**Klíč**|**Popis**|  
|-------------|---------------------|  
|<xref:Microsoft.Win32.Registry.ClassesRoot>|Definuje typy dokumentů a vlastnosti související s těmito typy.|  
|<xref:Microsoft.Win32.Registry.CurrentConfig>|Obsahuje informace o konfiguraci hardwaru, které nejsou specifické pro uživatele.|  
|<xref:Microsoft.Win32.Registry.CurrentUser>|Obsahuje informace o aktuální uživatelské předvolby, například proměnné prostředí.|  
|<xref:Microsoft.Win32.Registry.DynData>|Obsahuje dynamické registru data, jako je například použité virtuální ovladače zařízení.|  
|<xref:Microsoft.Win32.Registry.LocalMachine>|Obsahuje pět podklíčů (Hardware, SAM, zabezpečení, softwaru a systému), které obsahují konfigurační data pro místní počítač.|  
|<xref:Microsoft.Win32.Registry.PerformanceData>|Obsahuje informace o výkonu pro softwarové součásti.|  
|<xref:Microsoft.Win32.Registry.Users>|Obsahuje informace o uživatelských předvoleb výchozí.|  
  
> [!IMPORTANT]
>  Je bezpečnější zapsat data do aktuální uživatel (<xref:Microsoft.Win32.Registry.CurrentUser>) než k místnímu počítači (<xref:Microsoft.Win32.Registry.LocalMachine>). Podmínku, která se obvykle označuje jako "obsazení" nastane, když klíč, který vytváříte byl dříve vytvořen v jiné, potenciálně škodlivý, procesu. Chcete-li tomu zabránit, použijte metodu, jako například <xref:Microsoft.Win32.RegistryKey.GetValue%2A>, který vrátí `Nothing` Pokud klíč ještě neexistuje.  
  
## <a name="reading-a-value-from-the-registry"></a>Čtení hodnoty z registru  
 Následující kód ukazuje, jak číst řetězce z HKEY_CURRENT_USER.  
  
 [!code-vb[VbResourceTasks#20](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/reading-from-and-writing-to-the-registry-using-the-microsoft-win32-namespace_1.vb)]  
  
 Následující kód čte, se zvýší a pak zapíše řetězec do HKEY_CURRENT_USER.  
  
 [!code-vb[VbResourceTasks#21](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/reading-from-and-writing-to-the-registry-using-the-microsoft-win32-namespace_2.vb)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.SystemException>  
 <xref:System.ApplicationException>  
 <xref:Microsoft.VisualBasic.MyServices.RegistryProxy>  
 [Try... Catch... Finally – příkaz](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)  
 [Čtení a zápis do registru](../../../../visual-basic/developing-apps/programming/computer-resources/reading-from-and-writing-to-the-registry.md)  
 [Zabezpečení a registr](../../../../visual-basic/developing-apps/programming/computer-resources/security-and-the-registry.md)
