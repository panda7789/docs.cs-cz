---
title: Jak vytvořit klíč v registru - C# Programovací průvodce
ms.date: 07/20/2015
helpviewer_keywords:
- registry, adding keys and values [C#]
- registry keys, creating [C#]
- keys, creating in registry
ms.assetid: 8fa475b0-e01f-483a-9327-fd03488fdf5d
ms.openlocfilehash: 16974db950a3a460416cfb917147439707e1d007
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75635441"
---
# <a name="how-to-create-a-key-in-the-registry-c-programming-guide"></a>Jak vytvořit klíč v registru (C# Programovací průvodce)
Tento příklad přidá dvojici hodnot "Jméno" a "Isabella" do registru aktuálního uživatele pod klíčem "Jména".  
  
## <a name="example"></a>Příklad  
  
```csharp  
Microsoft.Win32.RegistryKey key;  
key = Microsoft.Win32.Registry.CurrentUser.CreateSubKey("Names");  
key.SetValue("Name", "Isabella");  
key.Close();  
```  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
  
- Zkopírujte kód a vložte jej do `Main` metody konzolové aplikace.  
  
- Nahraďte `Names` parametr názvem klíče, který existuje přímo pod HKEY_CURRENT_USER uzlu registru.  
  
- Nahraďte `Name` parametr názvem hodnoty, která existuje přímo pod názvem Název uzlu.  
  
## <a name="robust-programming"></a>Robustní programování  
 Zkontrolujte strukturu registru najít vhodné umístění pro váš klíč. Můžete například otevřít klíč Software aktuálního uživatele a vytvořit klíč s názvem vaší společnosti. Pak přidejte hodnoty registru do klíče vaší společnosti.  
  
 Následující podmínky mohou způsobit výjimku:  
  
- Název klíče je null.  
  
- Uživatel nemá oprávnění k vytváření klíčů registru.  
  
- Název klíče překračuje limit 255 znaků.  
  
- Klíč je zavřený.  
  
- Klíč registru je jen pro čtení.  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  
 Je bezpečnější zapisovat data do `Microsoft.Win32.Registry.CurrentUser` složky uživatele – `Microsoft.Win32.Registry.LocalMachine`nikoli do místního počítače .  
  
 Při vytváření hodnoty registru se musíte rozhodnout, co dělat, pokud tato hodnota již existuje. Jiný proces, možná škodlivý, může mít již vytvořilhodnotu a mají k ní přístup. Když vložíte data do hodnoty registru, data jsou k dispozici pro jiný proces. Chcete-li tomu zabránit, použijte.`Overload:Microsoft.Win32.RegistryKey.GetValue` Metoda. Vrátí hodnotu null, pokud klíč ještě neexistuje.  
  
 Není bezpečné ukládat tajné klíče, například hesla, do registru jako prostý text, i v případě, že klíč registru je chráněn seznamy řízení přístupu (ACL).  
  
## <a name="see-also"></a>Viz také

- <xref:System.IO?displayProperty=nameWithType>
- [Programovací příručka jazyka C#](../index.md)
- [Systém souborů a registr (Průvodce programováním v C#)](./index.md)
- [Číst, psát a mazat z registru s C #](https://www.codeproject.com/Articles/3389/Read-write-and-delete-from-registry-with-C)
