---
title: Postup vytvoření klíče v registru – C# Průvodce programováním
ms.date: 07/20/2015
helpviewer_keywords:
- registry, adding keys and values [C#]
- registry keys, creating [C#]
- keys, creating in registry
ms.assetid: 8fa475b0-e01f-483a-9327-fd03488fdf5d
ms.openlocfilehash: 16974db950a3a460416cfb917147439707e1d007
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/03/2020
ms.locfileid: "75635441"
---
# <a name="how-to-create-a-key-in-the-registry-c-programming-guide"></a>Postup vytvoření klíče v registru (C# Průvodce programováním)
Tento příklad přidá dvojici hodnot "Name" a "Isabella" do registru aktuálního uživatele v klíči "Names".  
  
## <a name="example"></a>Příklad  
  
```csharp  
Microsoft.Win32.RegistryKey key;  
key = Microsoft.Win32.Registry.CurrentUser.CreateSubKey("Names");  
key.SetValue("Name", "Isabella");  
key.Close();  
```  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
  
- Zkopírujte kód a vložte ho do metody `Main` konzolové aplikace.  
  
- Nahraďte parametr `Names` názvem klíče, který existuje přímo pod uzlem HKEY_CURRENT_USER registru.  
  
- Nahraďte parametr `Name` názvem hodnoty, která existuje přímo pod uzlem Names.  
  
## <a name="robust-programming"></a>Robustní programování  
 Projděte si strukturu registru, kde najdete vhodné umístění pro váš klíč. Můžete například chtít otevřít softwarový klíč aktuálního uživatele a vytvořit klíč s názvem vaší společnosti. Pak přidejte hodnoty registru do klíče vaší společnosti.  
  
 Následující podmínky mohou způsobit výjimku:  
  
- Název klíče je null.  
  
- Uživatel nemá oprávnění k vytváření klíčů registru.  
  
- Název klíče překračuje limit 255 znaků.  
  
- Klíč je uzavřený.  
  
- Klíč registru je jen pro čtení.  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  
 Je bezpečnější zapsat data do složky uživatele – `Microsoft.Win32.Registry.CurrentUser`, nikoli do místního počítače – `Microsoft.Win32.Registry.LocalMachine`.  
  
 Když vytváříte hodnotu registru, musíte se rozhodnout, co dělat, pokud tato hodnota již existuje. Jiný proces, pravděpodobně škodlivý, již mohl vytvořit hodnotu a mít k ní přístup. Při vložení dat do hodnoty registru jsou data k dispozici pro druhý proces. Chcete-li tomu zabránit, použijte.`Overload:Microsoft.Win32.RegistryKey.GetValue` Metoda. Vrátí hodnotu null, pokud klíč ještě neexistuje.  
  
 Není bezpečné ukládat tajné klíče, jako jsou hesla, v registru jako prostý text, a to i v případě, že je klíč registru chráněný pomocí seznamů řízení přístupu (ACL).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.IO?displayProperty=nameWithType>
- [Průvodce programováním v jazyce C#](../index.md)
- [Systém souborů a registr (C# Průvodce programováním)](./index.md)
- [Čtení, zápis a odstranění z registru pomocíC#](https://www.codeproject.com/Articles/3389/Read-write-and-delete-from-registry-with-C)
