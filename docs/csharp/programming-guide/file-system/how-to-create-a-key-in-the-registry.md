---
title: 'Postupy: Vytvoření klíče v registru (Visual C#)'
ms.date: 07/20/2015
helpviewer_keywords:
- registry, adding keys and values [C#]
- registry keys, creating [C#]
- keys, creating in registry
ms.assetid: 8fa475b0-e01f-483a-9327-fd03488fdf5d
ms.openlocfilehash: f2b2cfcb09dc0c8c4d65b64f5de55c0b72746457
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2018
ms.locfileid: "43480605"
---
# <a name="how-to-create-a-key-in-the-registry-visual-c"></a>Postupy: Vytvoření klíče v registru (Visual C#)
V tomto příkladu přidá dvojici hodnot "Name" a "Isabella" do registru aktuálního uživatele pod klíčem "Names".  
  
## <a name="example"></a>Příklad  
  
```csharp  
Microsoft.Win32.RegistryKey key;  
key = Microsoft.Win32.Registry.CurrentUser.CreateSubKey("Names");  
key.SetValue("Name", "Isabella");  
key.Close();  
```  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
  
-   Zkopírujte kód a vložte ho do `Main` metoda konzolové aplikace.  
  
-   Nahradit `Names` parametr s názvem klíče, který existuje přímo v uzlu registru HKEY_CURRENT_USER.  
  
-   Nahradit `Name` parametr s názvem hodnoty, která je uvedena přímo v uzlu názvy.  
  
## <a name="robust-programming"></a>Robustní programování  
 Zkontrolujte strukturu registrů k vyhledání příhodného místa pro váš klíč. Například můžete chtít otevřít softwarový klíč aktuálního uživatele a vytvořte klíč s názvem vaší společnosti. Hodnoty registru obnovte klíče vaší společnosti.  
  
 Následující podmínky mohou způsobit výjimku:  
  
-   Název klíče je null.  
  
-   Uživatel nemá oprávnění k vytvoření klíče registru.  
  
-   Název klíče překračuje limit 255 znaků.  
  
-   Klíč je uzavřen.  
  
-   Klíč registru je jen pro čtení.  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  
 Je bezpečnější zapsat data do složky uživatele – `Microsoft.Win32.Registry.CurrentUser` – místo na místním počítači – `Microsoft.Win32.Registry.LocalMachine`.  
  
 Když vytváříte hodnotu registru, musíte se rozhodnout, co dělat, pokud tuto hodnotu již existuje. Jiný proces, možná škodlivý ten už možná máte vytvořené hodnotu a k ní máte přístup. Když vkládáte data do hodnoty registru, data jsou k dispozici pro jiné procesy. Chcete-li tomu zabránit, použijte.`Overload:Microsoft.Win32.RegistryKey.GetValue` Metoda. Vrátí hodnotu null, pokud klíč ještě neexistuje.  
  
 Není bezpečné uchovávat tajemství, jako jsou hesla, v registrech jako prostý text, i v případě, že je klíč registru chráněn pomocí seznamů řízení přístupu (ACL).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.IO?displayProperty=nameWithType>  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [Systém souborů a registr (C# Programming Guide)](../../../csharp/programming-guide/file-system/index.md)  
 [Čtení, zápisu a odstranění z registru pomocí C#](http://www.codeproject.com/Articles/3389/Read-write-and-delete-from-registry-with-C)
