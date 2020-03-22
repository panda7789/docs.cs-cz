---
title: Čtení z registru a zápis do něj s použitím oboru názvů Microsoft.Win32
ms.date: 07/20/2015
helpviewer_keywords:
- registry [Visual Basic]
ms.assetid: 4a0dcce0-c27b-4199-baa8-ee4528da6a56
ms.openlocfilehash: 841344186b8e56717b81e90397aabc608bdc6dab
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "74345488"
---
# <a name="reading-from-and-writing-to-the-registry-using-the-microsoftwin32-namespace-visual-basic"></a>Čtení z registru a zápis do něj s použitím oboru názvů Microsoft.Win32 (Visual Basic)

Ačkoli `My.Computer.Registry` by měl y pokrýt základní potřeby při programování <xref:Microsoft.Win32.Registry> <xref:Microsoft.Win32.RegistryKey> proti registru, můžete také použít a třídy v oboru <xref:Microsoft.Win32> názvů rozhraní .NET Framework.  
  
## <a name="keys-in-the-registry-class"></a>Klíče ve třídě registru  

 Třída <xref:Microsoft.Win32.Registry> poskytuje základní klíče registru, které lze použít pro přístup k podklíčům a jejich hodnotám. Základní klíče samy o sobě jsou jen pro čtení. V následující tabulce jsou uvedeny a <xref:Microsoft.Win32.Registry> popsány sedm klíčů vystavených třídou.  
  
|**Klíč**|**Popis**|  
|-------------|---------------------|  
|<xref:Microsoft.Win32.Registry.ClassesRoot>|Definuje typy dokumentů a vlastnosti přidružené k těmto typům.|  
|<xref:Microsoft.Win32.Registry.CurrentConfig>|Obsahuje informace o konfiguraci hardwaru, které nejsou specifické pro uživatele.|  
|<xref:Microsoft.Win32.Registry.CurrentUser>|Obsahuje informace o aktuálních uživatelských předvolbách, například proměnné prostředí.|  
|<xref:Microsoft.Win32.Registry.DynData>|Obsahuje dynamická data registru, například data používaná ovladači virtuálních zařízení.|  
|<xref:Microsoft.Win32.Registry.LocalMachine>|Obsahuje pět podklíčů (hardware, SAM, zabezpečení, software a systém), které obsahují konfigurační data pro místní počítač.|  
|<xref:Microsoft.Win32.Registry.PerformanceData>|Obsahuje informace o výkonu softwarových součástí.|  
|<xref:Microsoft.Win32.Registry.Users>|Obsahuje informace o výchozích uživatelských předvolbách.|  
  
> [!IMPORTANT]
> Je bezpečnější zapisovat data aktuálnímu uživateli (<xref:Microsoft.Win32.Registry.CurrentUser><xref:Microsoft.Win32.Registry.LocalMachine>) než místnímu počítači ( ). Podmínka, která se obvykle označuje jako "squatting" nastane, když klíč, který vytváříte byl dříve vytvořen jiným, možná škodlivý, proces. Chcete-li tomu zabránit, použijte metodu, například <xref:Microsoft.Win32.RegistryKey.GetValue%2A>, která se vrátí, `Nothing` pokud klíč ještě neexistuje.  
  
## <a name="reading-a-value-from-the-registry"></a>Čtení hodnoty z registru  

 Následující kód ukazuje, jak číst řetězec z HKEY_CURRENT_USER.  
  
 [!code-vb[VbResourceTasks#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#20)]  
  
 Následující kód čte, přírůstky a pak zapíše řetězec HKEY_CURRENT_USER.  
  
 [!code-vb[VbResourceTasks#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#21)]  
  
## <a name="see-also"></a>Viz také

- <xref:System.SystemException>
- <xref:System.ApplicationException>
- <xref:Microsoft.VisualBasic.MyServices.RegistryProxy>
- [Příkaz Try...Catch...Finally](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
- [Čtení z registru a zápis do něj](../../../../visual-basic/developing-apps/programming/computer-resources/reading-from-and-writing-to-the-registry.md)
- [Zabezpečení a registr](../../../../visual-basic/developing-apps/programming/computer-resources/security-and-the-registry.md)
