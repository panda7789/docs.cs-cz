---
title: 'Postupy: Odstranění klíče z registru v jazyce Visual Basic'
ms.date: 07/20/2015
f1_keywords:
- vb.DeleteSetting
helpviewer_keywords:
- GetSetting function [Visual Basic]
- registry [Visual Basic], deleting values
- GetAllSettings function
- registry keys [Visual Basic], deleting
- registry [Visual Basic], deleting keys
- examples [Visual Basic], registry
ms.assetid: ab9aca0e-42b0-4ff7-8ff9-845a4bfdf9f2
ms.openlocfilehash: 8a983436b8c7415f0d356d65ae7d6c5ffd1c2db5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33583848"
---
# <a name="how-to-delete-a-registry-key-in-visual-basic"></a>Postupy: Odstranění klíče z registru v jazyce Visual Basic
<xref:Microsoft.Win32.RegistryKey.DeleteSubKey%28System.String%29> a <xref:Microsoft.Win32.RegistryKey.DeleteSubKey%28System.String%2CSystem.Boolean%29> metody slouží k odstranění klíče registru.  
  
## <a name="procedure"></a>Postup  
  
#### <a name="to-delete-a-registry-key"></a>Chcete-li odstranit klíč registru  
  
-   Použití `DeleteSubKey` metodu za účelem odstranění klíče z registru. Tento příklad odstraní klíče Software/TestApp v podregistru CurrentUser. Můžete to změnit v kódu na příslušným řetězcem nebo vycházet z informací zadaných uživatelem.  
  
     [!code-vb[VbResourceTasks#19](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-delete-a-registry-key_1.vb)]  
  
## <a name="robust-programming"></a>Robustní programování  
 `DeleteSubKey` Metoda vrátí prázdný řetězec, pokud neexistuje dvojice klíč/hodnota.  
  
 Následující podmínky mohou způsobit výjimku:  
  
-   Název klíče je `Nothing` (<xref:System.ArgumentNullException>).  
  
-   Uživatel nemá oprávnění k odstranění klíče registru (<xref:System.Security.SecurityException>).  
  
-   Název klíče překračuje limit 255 znaků (<xref:System.ArgumentException>).  
  
-   Klíč registru je jen pro čtení (<xref:System.UnauthorizedAccessException>).  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  
 Volání registrů se nezdaří, pokud nejsou udělena buď dostatečná oprávnění pro spuštění (<xref:System.Security.Permissions.RegistryPermission>) nebo pokud uživatel nemá správný přístup (jako seznamy ACL) pro vytvoření nebo zápis k nastavení. Například místní aplikace, který má oprávnění zabezpečení přístupu kódu, nemusí mít oprávnění operačního systému.  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.Win32.RegistryKey.DeleteSubKey%2A>  
 <xref:Microsoft.Win32.RegistryKey.DeleteSubKey%2A>  
 <xref:Microsoft.Win32.RegistryKey>  
 [Zabezpečení a registr](../../../../visual-basic/developing-apps/programming/computer-resources/security-and-the-registry.md)  
 [Čtení z registru a zápis do něj](../../../../visual-basic/developing-apps/programming/computer-resources/reading-from-and-writing-to-the-registry.md)
