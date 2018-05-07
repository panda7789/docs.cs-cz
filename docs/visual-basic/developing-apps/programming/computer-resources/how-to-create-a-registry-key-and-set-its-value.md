---
title: 'Postupy: Vytvoření klíče registru a nastavení jeho hodnoty v jazyce Visual Basic'
ms.date: 07/20/2015
f1_keywords:
- RegistryKey.CreateSubKey
- RegistryKey.SetValue
helpviewer_keywords:
- registry keys [Visual Basic], creating
- registry [Visual Basic], adding values
- registry [Visual Basic], adding keys
- registry keys [Visual Basic], setting values
- examples [Visual Basic], registry
ms.assetid: d3e40f74-c283-480c-ab18-e5e9052cd814
ms.openlocfilehash: 4f74d41aa8055e26f5a707829449ddd310ff576f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-create-a-registry-key-and-set-its-value-in-visual-basic"></a>Postupy: Vytvoření klíče registru a nastavení jeho hodnoty v jazyce Visual Basic
`CreateSubKey` Metodu `My.Computer.Registry` objekt můžete použít k vytvoření klíče registru.  
  
## <a name="procedure"></a>Postup  
  
#### <a name="to-create-a-registry-key"></a>Vytvoření klíče registru  
  
-   Použití `CreateSubKey` metoda, zadání kterého podregistru umístíte klíč v části, jakož i název klíče. Parametr `Subkey` není malá a velká písmena. Tento příklad vytvoří klíč registru `MyTestKey` HKEY_CURRENT_USER.  
  
     [!code-vb[VbResourceTasks#17](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-create-a-registry-key-and-set-its-value_1.vb)]  
  
#### <a name="to-create-a-registry-key-and-set-a-value-in-it"></a>Vytvořte klíč registru a nastavte hodnotu v ní  
  
1.  Použití `CreateSubkey` metoda, zadání kterého podregistru umístíte klíč v části, jakož i název klíče. Tento příklad vytvoří klíč registru `MyTestKey` HKEY_CURRENT_USER.  
  
     [!code-vb[VbResourceTasks#17](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-create-a-registry-key-and-set-its-value_1.vb)]  
  
2.  Nastavte hodnotu pomocí `SetValue` metoda. Tento příklad nastaví řetězcovou hodnotu. "MyTestKeyValue" na "Toto je testovací hodnota".  
  
     [!code-vb[VbResourceTasks#14](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-create-a-registry-key-and-set-its-value_2.vb)]  
  
## <a name="example"></a>Příklad  
 Tento příklad vytvoří klíč registru `MyTestKey` HKEY_CURRENT_USER a poté nastaví řetězcovou hodnotu `MyTestKeyValue` k `This is a test value`.  
  
 [!code-vb[VbResourceTasks#15](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-create-a-registry-key-and-set-its-value_3.vb)]  
  
## <a name="robust-programming"></a>Robustní programování  
 Zkontrolujte strukturu registru se najít vhodného místa pro váš klíč. Například můžete chtít otevřít klíč HKEY_CURRENT_USER\Software aktuálního uživatele a vytvořte klíč s názvem vaší společnosti. Přidejte do vaší společnosti klíč hodnoty registru.  
  
 Při čtení registru z webové aplikace, je aktuální uživatel závisí na ověřování a zosobnění implementována ve webové aplikaci.  
  
 Je bezpečnější zapsat data do složky uživatele (<xref:Microsoft.Win32.Registry.CurrentUser>) a nikoli k místnímu počítači (<xref:Microsoft.Win32.Registry.LocalMachine>).  
  
 Když vytvoříte hodnotu registru, budete muset rozhodnout, co dělat v případě, že hodnota již existuje. Jiný proces, případně škodlivý jeden už možná máte vytvořené hodnota a mít přístup k němu. Když vložíte dat v hodnotě registru, data jsou k dispozici pro jiný proces. Chcete-li tomu zabránit, použijte <xref:Microsoft.Win32.RegistryKey.GetValue%2A> metoda. Vrátí `Nothing` Pokud klíč ještě neexistuje.  
  
 Není bezpečné uchovávat tajné údaje, jako jsou hesla, v registru jako prostý text, i v případě, že je klíč registru chráněn pomocí seznamů řízení přístupu (ACL).  
  
 Následující podmínky mohou způsobit výjimku:  
  
-   Název klíče je `Nothing` (<xref:System.ArgumentNullException>).  
  
-   Uživatel nemá oprávnění k vytvoření klíče registru (<xref:System.Security.SecurityException>).  
  
-   Název klíče překračuje limit 255 znaků (<xref:System.ArgumentException>).  
  
-   Klíč je uzavřen (<xref:System.IO.IOException>).  
  
-   Klíč registru je jen pro čtení (<xref:System.UnauthorizedAccessException>).  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  
 Pokud chcete spustit tento proces, vaše sestavení vyžaduje úroveň oprávnění udělenou <xref:System.Security.Permissions.RegistryPermission> třídy. Pokud používáte v kontextu částečným vztahem důvěryhodnosti, proces může vyvolat výjimku z důvodu nedostatečných oprávnění. Podobně uživatel musí mít správné seznamy řízení přístupu pro vytvoření nebo zápis k nastavení. Například místní aplikace, který má oprávnění zabezpečení přístupu kódu, nemusí mít oprávnění operačního systému. Další informace najdete v tématu [Základy zabezpečení přístupu kódu](../../../../framework/misc/code-access-security-basics.md).  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualBasic.MyServices.RegistryProxy>  
 <xref:Microsoft.VisualBasic.MyServices.RegistryProxy.CurrentUser%2A>  
 <xref:Microsoft.Win32.RegistryKey.CreateSubKey%2A>  
 [Čtení z registru a zápis do něj](../../../../visual-basic/developing-apps/programming/computer-resources/reading-from-and-writing-to-the-registry.md)  
 [Základy zabezpečení přístupu kódu](../../../../framework/misc/code-access-security-basics.md)
