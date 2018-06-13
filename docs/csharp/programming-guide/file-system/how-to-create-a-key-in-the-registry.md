---
title: 'Postupy: Vytvoření klíče v registru (Visual C#)'
ms.date: 07/20/2015
helpviewer_keywords:
- registry, adding keys and values [C#]
- registry keys, creating [C#]
- keys, creating in registry
ms.assetid: 8fa475b0-e01f-483a-9327-fd03488fdf5d
ms.openlocfilehash: a1643310740a472ad0a1df978fa41f674f3dbcb5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33331464"
---
# <a name="how-to-create-a-key-in-the-registry-visual-c"></a>Postupy: Vytvoření klíče v registru (Visual C#)
Tento příklad přidá dvojice hodnot, "Název" a "Isabella", do aktuálního uživatele registru pod klíčem "Názvy".  
  
## <a name="example"></a>Příklad  
  
```  
Microsoft.Win32.RegistryKey key;  
key = Microsoft.Win32.Registry.CurrentUser.CreateSubKey("Names");  
key.SetValue("Name", "Isabella");  
key.Close();  
```  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
  
-   Zkopírovat kód a vložte ji do `Main` metoda konzolové aplikace.  
  
-   Nahraďte `Names` parametr s názvem klíče, který existuje přímo v uzlu HKEY_CURRENT_USER registru.  
  
-   Nahraďte `Name` parametr s názvem hodnotu, která existuje přímo v uzlu názvy.  
  
## <a name="robust-programming"></a>Robustní programování  
 Zkontrolujte strukturu registru se najít vhodného místa pro váš klíč. Například můžete chtít otevřít klíč softwaru aktuálního uživatele a vytvořte klíč s názvem vaší společnosti. Přidejte do vaší společnosti klíč hodnoty registru.  
  
 Následujících podmínek může způsobit výjimku:  
  
-   Název klíče, má hodnotu null.  
  
-   Uživatel nemá oprávnění k vytvoření klíče registru.  
  
-   Název klíče překračuje limit 255 znaků.  
  
-   Klíč je uzavřen.  
  
-   Klíč registru je jen pro čtení.  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  
 Je bezpečnější zapsat data do složky uživatele – `Microsoft.Win32.Registry.CurrentUser` – místo na místním počítači – `Microsoft.Win32.Registry.LocalMachine`.  
  
 Když vytvoříte hodnotu registru, budete muset rozhodnout, co dělat v případě, že hodnota již existuje. Jiný proces, případně škodlivý jeden už možná máte vytvořené hodnota a mít přístup k němu. Když vložíte dat v hodnotě registru, data jsou k dispozici pro jiný proces. Chcete-li tomu zabránit, použijte.`Overload:Microsoft.Win32.RegistryKey.GetValue` Metoda. Vrátí hodnotu null, pokud klíč ještě neexistuje.  
  
 Není bezpečné uchovávat tajné údaje, jako jsou hesla, v registru jako prostý text, i v případě, že je klíč registru chráněn pomocí seznamů řízení přístupu (ACL).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.IO?displayProperty=nameWithType>  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [Systém souborů a registr (C# Průvodce programováním)](../../../csharp/programming-guide/file-system/index.md)  
 [Čtení, zápis a odstranění z registru pomocí C#](http://www.codeproject.com/Articles/3389/Read-write-and-delete-from-registry-with-C)
