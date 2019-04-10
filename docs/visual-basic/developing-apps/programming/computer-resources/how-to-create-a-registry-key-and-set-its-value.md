---
title: 'Postupy: Vytvořte klíč registru a nastavení jeho hodnoty v jazyce Visual Basic'
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
ms.openlocfilehash: 0cadff8b44c60041e2664b1d3b70830209014301
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59312607"
---
# <a name="how-to-create-a-registry-key-and-set-its-value-in-visual-basic"></a>Postupy: Vytvořte klíč registru a nastavení jeho hodnoty v jazyce Visual Basic
`CreateSubKey` Metodu `My.Computer.Registry` objekt slouží k vytvoření klíče registru.  
  
## <a name="procedure"></a>Postup  
  
#### <a name="to-create-a-registry-key"></a>Vytvoření klíče registru  
  
-   Použití `CreateSubKey` metoda, která hive umístí klíč v rámci, jakož i název klíče zadáte. Parametr `Subkey` není malá a velká písmena. Tento příklad vytvoří klíče registru `MyTestKey` HKEY_CURRENT_USER.  
  
     [!code-vb[VbResourceTasks#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#17)]  
  
#### <a name="to-create-a-registry-key-and-set-a-value-in-it"></a>Vytvořte klíč registru a nastavit hodnotu v ní  
  
1. Použití `CreateSubkey` metoda, která hive umístí klíč v rámci, jakož i název klíče zadáte. Tento příklad vytvoří klíče registru `MyTestKey` HKEY_CURRENT_USER.  
  
     [!code-vb[VbResourceTasks#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#17)]  
  
2. Nastavte hodnoty `SetValue` metody. V tomto příkladu nastaví řetězcovou hodnotu. "MyTestKeyValue" na "Toto je testovací hodnota".  
  
     [!code-vb[VbResourceTasks#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#14)]  
  
## <a name="example"></a>Příklad  
 Tento příklad vytvoří klíče registru `MyTestKey` HKEY_CURRENT_USER a pak nastaví řetězcovou hodnotu `MyTestKeyValue` k `This is a test value`.  
  
 [!code-vb[VbResourceTasks#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#15)]  
  
## <a name="robust-programming"></a>Robustní programování  
 Zkontrolujte strukturu registrů k vyhledání příhodného místa pro váš klíč. Můžete například otevřít HKEY_CURRENT_USER\Software klíč aktuálního uživatele a vytvořte klíč s názvem vaší společnosti. Hodnoty registru obnovte klíče vaší společnosti.  
  
 Při čtení registru z webové aplikace, je aktuální uživatel závisí na ověřování a zosobnění implementované ve webové aplikaci.  
  
 Je bezpečnější zapsat data do složky uživatele (<xref:Microsoft.Win32.Registry.CurrentUser>), nikoli do místního počítače (<xref:Microsoft.Win32.Registry.LocalMachine>).  
  
 Když vytváříte hodnotu registru, musíte se rozhodnout, co dělat, pokud tuto hodnotu již existuje. Jiný proces, možná škodlivý ten už možná máte vytvořené hodnotu a k ní máte přístup. Když vkládáte data do hodnoty registru, data jsou k dispozici pro jiné procesy. Chcete-li tomu zabránit, použijte <xref:Microsoft.Win32.RegistryKey.GetValue%2A> metody. Vrátí `Nothing` Pokud klíč ještě neexistuje.  
  
 Není bezpečné uchovávat tajemství, jako jsou hesla, v registrech jako prostý text, i v případě, že klíč registru je chráněn pomocí ACL (seznamy řízení přístupu).  
  
 Následující podmínky mohou způsobit výjimku:  
  
-   Název klíče je `Nothing` (<xref:System.ArgumentNullException>).  
  
-   Uživatel nemá oprávnění k vytvoření klíče registru (<xref:System.Security.SecurityException>).  
  
-   Název klíče překračuje limit 255 znaků (<xref:System.ArgumentException>).  
  
-   Klíč je uzavřen (<xref:System.IO.IOException>).  
  
-   Klíč registru je jen pro čtení (<xref:System.UnauthorizedAccessException>).  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  
 Pokud chcete spustit tento proces, vaše sestavení vyžaduje úroveň oprávnění udělenou <xref:System.Security.Permissions.RegistryPermission> třídy. Pokud používáte v kontextu částečným vztahem důvěryhodnosti, proces může vyvolat výjimku, protože nedostatečná oprávnění. Podobně uživatel musí mít správné seznamy ACL pro vytvoření nebo zápis do nastavení. Místní aplikace, který má oprávnění zabezpečení přístupu kódu například nemusí mít oprávnění operačního systému. Další informace najdete v tématu [Základy zabezpečení přístupu kódu](../../../../framework/misc/code-access-security-basics.md).  
  
## <a name="see-also"></a>Viz také:

- <xref:Microsoft.VisualBasic.MyServices.RegistryProxy>
- <xref:Microsoft.VisualBasic.MyServices.RegistryProxy.CurrentUser%2A>
- <xref:Microsoft.Win32.RegistryKey.CreateSubKey%2A>
- [Čtení z registru a zápis do něj](../../../../visual-basic/developing-apps/programming/computer-resources/reading-from-and-writing-to-the-registry.md)
- [Základy zabezpečení přístupu kódu](../../../../framework/misc/code-access-security-basics.md)
