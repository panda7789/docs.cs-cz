---
title: Postup vytvoření klíče v registru – Průvodce programováním v C#
description: Naučte se vytvořit klíč v registru. Podívejte se na příklad kódu, kompilování instrukcí a další dostupné prostředky.
ms.date: 07/20/2015
helpviewer_keywords:
- registry, adding keys and values [C#]
- registry keys, creating [C#]
- keys, creating in registry
ms.assetid: 8fa475b0-e01f-483a-9327-fd03488fdf5d
ms.openlocfilehash: 6db076bc22e098c285b74a8c10e8b5f456c2c55e
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/28/2020
ms.locfileid: "87299978"
---
# <a name="how-to-create-a-key-in-the-registry-c-programming-guide"></a>Postup vytvoření klíče v registru (Průvodce programováním v C#)
Tento příklad přidá dvojici hodnot "Name" a "Isabella" do registru aktuálního uživatele v klíči "Names".  
  
## <a name="example"></a>Příklad  
  
```csharp  
Microsoft.Win32.RegistryKey key;  
key = Microsoft.Win32.Registry.CurrentUser.CreateSubKey("Names");  
key.SetValue("Name", "Isabella");  
key.Close();  
```  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
  
- Zkopírujte kód a vložte ho do `Main` metody konzolové aplikace.  
  
- Nahraďte `Names` parametr názvem klíče, který existuje přímo pod uzlem HKEY_CURRENT_USER registru.  
  
- Nahraďte `Name` parametr názvem hodnoty, která existuje přímo pod uzlem Names.  
  
## <a name="robust-programming"></a>Robustní programování  
 Projděte si strukturu registru, kde najdete vhodné umístění pro váš klíč. Můžete například chtít otevřít softwarový klíč aktuálního uživatele a vytvořit klíč s názvem vaší společnosti. Pak přidejte hodnoty registru do klíče vaší společnosti.  
  
 Následující podmínky mohou způsobit výjimku:  
  
- Název klíče je null.  
  
- Uživatel nemá oprávnění k vytváření klíčů registru.  
  
- Název klíče překračuje limit 255 znaků.  
  
- Klíč je uzavřený.  
  
- Klíč registru je jen pro čtení.  
  
## <a name="net-security"></a>Zabezpečení .NET  
 Je bezpečnější zapsat data do složky uživatele – `Microsoft.Win32.Registry.CurrentUser` místo do místního počítače – `Microsoft.Win32.Registry.LocalMachine` .  
  
 Když vytváříte hodnotu registru, musíte se rozhodnout, co dělat, pokud tato hodnota již existuje. Jiný proces, pravděpodobně škodlivý, již mohl vytvořit hodnotu a mít k ní přístup. Při vložení dat do hodnoty registru jsou data k dispozici pro druhý proces. Chcete-li tomu zabránit, použijte.`Overload:Microsoft.Win32.RegistryKey.GetValue` Metoda. Vrátí hodnotu null, pokud klíč ještě neexistuje.  
  
 Není bezpečné ukládat tajné klíče, jako jsou hesla, v registru jako prostý text, a to i v případě, že je klíč registru chráněný pomocí seznamů řízení přístupu (ACL).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.IO?displayProperty=nameWithType>
- [Průvodce programováním v C#](../index.md)
- [Systém souborů a registr (Průvodce programováním v C#)](./index.md)
- [Čtení, zápis a odstranění z registru pomocí jazyka C #](https://www.codeproject.com/Articles/3389/Read-write-and-delete-from-registry-with-C)
