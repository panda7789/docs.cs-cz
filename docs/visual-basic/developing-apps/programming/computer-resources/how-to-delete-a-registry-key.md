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
ms.openlocfilehash: ea537d302f64933176f1a44fec2e27b804ff5809
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84363316"
---
# <a name="how-to-delete-a-registry-key-in-visual-basic"></a>Postupy: Odstranění klíče z registru v jazyce Visual Basic

<xref:Microsoft.Win32.RegistryKey.DeleteSubKey%28System.String%29>Metody a <xref:Microsoft.Win32.RegistryKey.DeleteSubKey%28System.String%2CSystem.Boolean%29> lze použít k odstranění klíčů registru.  
  
## <a name="procedure"></a>Postup  
  
#### <a name="to-delete-a-registry-key"></a>Odstranění klíče registru  
  
- Použijte `DeleteSubKey` metodu k odstranění klíče registru. Tento příklad odstraní klíč Software/TestApp v podregistru CurrentUser. Můžete to změnit v kódu na příslušný řetězec nebo se musí spoléhat na informace zadané uživatelem.  
  
     [!code-vb[VbResourceTasks#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#19)]  
  
## <a name="robust-programming"></a>Robustní programování  

 `DeleteSubKey`Metoda vrátí prázdný řetězec, pokud dvojice klíč/hodnota neexistuje.  
  
 Následující podmínky mohou způsobit výjimku:  
  
- Název klíče je `Nothing` ( <xref:System.ArgumentNullException> ).  
  
- Uživatel nemá oprávnění k odstranění klíčů registru ( <xref:System.Security.SecurityException> ).  
  
- Název klíče překračuje limit 255 znaků ( <xref:System.ArgumentException> ).  
  
- Klíč registru je jen pro čtení ( <xref:System.UnauthorizedAccessException> ).  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  

 Volání registru selže, pokud buď nejsou udělena dostatečná oprávnění za běhu ( <xref:System.Security.Permissions.RegistryPermission> ), nebo pokud uživatel nemá správný přístup (podle určení seznamů ACL) pro vytvoření nebo zápis do nastavení. Například místní aplikace, která má oprávnění zabezpečení přístupu kódu, nemusí mít oprávnění operačního systému.  
  
## <a name="see-also"></a>Viz také

- <xref:Microsoft.Win32.RegistryKey.DeleteSubKey%2A>
- <xref:Microsoft.Win32.RegistryKey>
- [Zabezpečení a registr](security-and-the-registry.md)
- [Čtení z registru a zápis do něj](reading-from-and-writing-to-the-registry.md)
