---
title: "Postupy: Vytvoření klíče v registru (Visual C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- registry, adding keys and values [C#]
- registry keys, creating [C#]
- keys, creating in registry
ms.assetid: 8fa475b0-e01f-483a-9327-fd03488fdf5d
caps.latest.revision: "14"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: f6cc79a8a914d3ef5b7c496db4dc0d2b3eb17768
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
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
 [Průvodce programováním v C#](../../../csharp/programming-guide/index.md)  
 [Systém souborů a registr (C# Průvodce programováním)](../../../csharp/programming-guide/file-system/index.md)  
 [Čtení, zápis a odstranění z registru pomocí C#](http://www.codeproject.com/Articles/3389/Read-write-and-delete-from-registry-with-C)
