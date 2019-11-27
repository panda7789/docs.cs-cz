---
title: Čtení z registru a zápis do něj s použitím oboru názvů Microsoft.Win32
ms.date: 07/20/2015
helpviewer_keywords:
- registry [Visual Basic]
ms.assetid: 4a0dcce0-c27b-4199-baa8-ee4528da6a56
ms.openlocfilehash: 841344186b8e56717b81e90397aabc608bdc6dab
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345488"
---
# <a name="reading-from-and-writing-to-the-registry-using-the-microsoftwin32-namespace-visual-basic"></a>Čtení z registru a zápis do něj s použitím oboru názvů Microsoft.Win32 (Visual Basic)

I když `My.Computer.Registry` by měl pokrývat vaše základní potřeby při programování v registru, můžete také použít třídy <xref:Microsoft.Win32.Registry> a <xref:Microsoft.Win32.RegistryKey> v oboru názvů <xref:Microsoft.Win32> .NET Framework.  
  
## <a name="keys-in-the-registry-class"></a>Klíče v třídě registru  

 Třída <xref:Microsoft.Win32.Registry> poskytuje základní klíče registru, které lze použít pro přístup k podklíčům a jejich hodnotám. Základní klíče jsou jen pro čtení. Následující tabulka uvádí a popisuje sedm klíčů vystavených <xref:Microsoft.Win32.Registry> třídou.  
  
|**Key**|**Popis**|  
|-------------|---------------------|  
|<xref:Microsoft.Win32.Registry.ClassesRoot>|Definuje typy dokumentů a vlastnosti, které jsou k těmto typům přidruženy.|  
|<xref:Microsoft.Win32.Registry.CurrentConfig>|Obsahuje informace o konfiguraci hardwaru, které nejsou specifické pro uživatele.|  
|<xref:Microsoft.Win32.Registry.CurrentUser>|Obsahuje informace o uživatelských preferencích, jako jsou proměnné prostředí.|  
|<xref:Microsoft.Win32.Registry.DynData>|Obsahuje dynamická data registru, například ta, která používají ovladače virtuálních zařízení.|  
|<xref:Microsoft.Win32.Registry.LocalMachine>|Obsahuje pět podklíčů (hardware, SAM, zabezpečení, software a systém), které obsahují konfigurační data pro místní počítač.|  
|<xref:Microsoft.Win32.Registry.PerformanceData>|Obsahuje informace o výkonu pro softwarové součásti.|  
|<xref:Microsoft.Win32.Registry.Users>|Obsahuje informace o výchozích uživatelských preferencích.|  
  
> [!IMPORTANT]
> Je bezpečnější zapsat data do aktuálního uživatele (<xref:Microsoft.Win32.Registry.CurrentUser>) než do místního počítače (<xref:Microsoft.Win32.Registry.LocalMachine>). Podmínka, která se obvykle označuje jako "squatting", nastane, když se vytvářený klíč dřív vytvořil jiným, možná škodlivým procesem. Chcete-li tomu zabránit, použijte metodu, například <xref:Microsoft.Win32.RegistryKey.GetValue%2A>, která vrátí `Nothing`, pokud klíč ještě neexistuje.  
  
## <a name="reading-a-value-from-the-registry"></a>Čtení hodnoty z registru  

 Následující kód ukazuje, jak číst řetězec z HKEY_CURRENT_USER.  
  
 [!code-vb[VbResourceTasks#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#20)]  
  
 Následující kód přečte, zvýší a pak zapíše řetězec pro HKEY_CURRENT_USER.  
  
 [!code-vb[VbResourceTasks#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#21)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.SystemException>
- <xref:System.ApplicationException>
- <xref:Microsoft.VisualBasic.MyServices.RegistryProxy>
- [Příkaz Try...Catch...Finally](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
- [Čtení z registru a zápis do něj](../../../../visual-basic/developing-apps/programming/computer-resources/reading-from-and-writing-to-the-registry.md)
- [Zabezpečení a registr](../../../../visual-basic/developing-apps/programming/computer-resources/security-and-the-registry.md)
