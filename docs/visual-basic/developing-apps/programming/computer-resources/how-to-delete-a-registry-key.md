---
title: 'Postupy: Odstranění klíče z registru v jazyce Visual Basic'
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
ms.openlocfilehash: 7ff6ba8e31638b64fa7100b1807303c61a454c81
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56981670"
---
# <a name="how-to-delete-a-registry-key-in-visual-basic"></a>Postupy: Odstranění klíče z registru v jazyce Visual Basic
<xref:Microsoft.Win32.RegistryKey.DeleteSubKey%28System.String%29> a <xref:Microsoft.Win32.RegistryKey.DeleteSubKey%28System.String%2CSystem.Boolean%29> metody slouží k odstranění klíče registru.  
  
## <a name="procedure"></a>Postup  
  
#### <a name="to-delete-a-registry-key"></a>Odstranit klíč registru  
  
-   Použití `DeleteSubKey` metodu k odstranění klíče z registru. Tento příklad odstraní klíč softwaru/TestApp v CurrentUser hive. Můžete změnit v kódu na odpovídající řetězec nebo vycházet z uživatelem zadané informace.  
  
     [!code-vb[VbResourceTasks#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#19)]  
  
## <a name="robust-programming"></a>Robustní programování  
 `DeleteSubKey` Metoda vrátí prázdný řetězec, pokud je dvojice klíč/hodnota neexistuje.  
  
 Následující podmínky mohou způsobit výjimku:  
  
-   Název klíče je `Nothing` (<xref:System.ArgumentNullException>).  
  
-   Uživatel nemá oprávnění k odstranění klíče registru (<xref:System.Security.SecurityException>).  
  
-   Název klíče překračuje limit 255 znaků (<xref:System.ArgumentException>).  
  
-   Klíč registru je jen pro čtení (<xref:System.UnauthorizedAccessException>).  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  
 Volání registru selhat, pokud nejsou udělena buď dostatečná oprávnění za běhu (<xref:System.Security.Permissions.RegistryPermission>) nebo pokud uživatel nemá správný přístup (jako seznamy ACL) pro vytvoření nebo zápis do nastavení. Místní aplikace, který má oprávnění zabezpečení přístupu kódu například nemusí mít oprávnění operačního systému.  
  
## <a name="see-also"></a>Viz také:
- <xref:Microsoft.Win32.RegistryKey.DeleteSubKey%2A>
- <xref:Microsoft.Win32.RegistryKey.DeleteSubKey%2A>
- <xref:Microsoft.Win32.RegistryKey>
- [Zabezpečení a registr](../../../../visual-basic/developing-apps/programming/computer-resources/security-and-the-registry.md)
- [Čtení z registru a zápis do něj](../../../../visual-basic/developing-apps/programming/computer-resources/reading-from-and-writing-to-the-registry.md)
