---
title: 'Postupy: Odstranění klíče z registru'
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
ms.openlocfilehash: f38301a3a717a35b98e55804d6435d046bbbbab4
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345644"
---
# <a name="how-to-delete-a-registry-key-in-visual-basic"></a>Postupy: Odstranění klíče z registru v jazyce Visual Basic

Metody <xref:Microsoft.Win32.RegistryKey.DeleteSubKey%28System.String%29> a <xref:Microsoft.Win32.RegistryKey.DeleteSubKey%28System.String%2CSystem.Boolean%29> lze použít k odstranění klíčů registru.  
  
## <a name="procedure"></a>Postup  
  
#### <a name="to-delete-a-registry-key"></a>Odstranění klíče registru  
  
- Pomocí metody `DeleteSubKey` odstraňte klíč registru. Tento příklad odstraní klíč Software/TestApp v podregistru CurrentUser. Můžete to změnit v kódu na příslušný řetězec nebo se musí spoléhat na informace zadané uživatelem.  
  
     [!code-vb[VbResourceTasks#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#19)]  
  
## <a name="robust-programming"></a>Robustní programování  

 Metoda `DeleteSubKey` vrátí prázdný řetězec, pokud dvojice klíč/hodnota neexistuje.  
  
 Následující podmínky mohou způsobit výjimku:  
  
- Název klíče je `Nothing` (<xref:System.ArgumentNullException>).  
  
- Uživatel nemá oprávnění k odstranění klíčů registru (<xref:System.Security.SecurityException>).  
  
- Název klíče překračuje limit 255 znaků (<xref:System.ArgumentException>).  
  
- Klíč registru je jen pro čtení (<xref:System.UnauthorizedAccessException>).  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  

 Volání registru se nezdaří, pokud buď nejsou udělena dostatečná oprávnění za běhu (<xref:System.Security.Permissions.RegistryPermission>), nebo pokud uživatel nemá správný přístup (podle určení seznamů ACL) pro vytváření a zápis do nastavení. Například místní aplikace, která má oprávnění zabezpečení přístupu kódu, nemusí mít oprávnění operačního systému.  
  
## <a name="see-also"></a>Viz také:

- <xref:Microsoft.Win32.RegistryKey.DeleteSubKey%2A>
- <xref:Microsoft.Win32.RegistryKey>
- [Zabezpečení a registr](../../../../visual-basic/developing-apps/programming/computer-resources/security-and-the-registry.md)
- [Čtení z registru a zápis do něj](../../../../visual-basic/developing-apps/programming/computer-resources/reading-from-and-writing-to-the-registry.md)
