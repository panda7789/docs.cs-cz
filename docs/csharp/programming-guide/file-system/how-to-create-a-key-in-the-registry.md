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
# <a name="how-to-create-a-key-in-the-registry-c-programming-guide"></a><span data-ttu-id="83db3-104">Postup vytvoření klíče v registru (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="83db3-104">How to create a key in the registry (C# Programming Guide)</span></span>
<span data-ttu-id="83db3-105">Tento příklad přidá dvojici hodnot "Name" a "Isabella" do registru aktuálního uživatele v klíči "Names".</span><span class="sxs-lookup"><span data-stu-id="83db3-105">This example adds the value pair, "Name" and "Isabella", to the current user's registry, under the key "Names".</span></span>  
  
## <a name="example"></a><span data-ttu-id="83db3-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="83db3-106">Example</span></span>  
  
```csharp  
Microsoft.Win32.RegistryKey key;  
key = Microsoft.Win32.Registry.CurrentUser.CreateSubKey("Names");  
key.SetValue("Name", "Isabella");  
key.Close();  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="83db3-107">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="83db3-107">Compiling the Code</span></span>  
  
- <span data-ttu-id="83db3-108">Zkopírujte kód a vložte ho do `Main` metody konzolové aplikace.</span><span class="sxs-lookup"><span data-stu-id="83db3-108">Copy the code and paste it into the `Main` method of a console application.</span></span>  
  
- <span data-ttu-id="83db3-109">Nahraďte `Names` parametr názvem klíče, který existuje přímo pod uzlem HKEY_CURRENT_USER registru.</span><span class="sxs-lookup"><span data-stu-id="83db3-109">Replace the `Names` parameter with the name of a key that exists directly under the HKEY_CURRENT_USER node of the registry.</span></span>  
  
- <span data-ttu-id="83db3-110">Nahraďte `Name` parametr názvem hodnoty, která existuje přímo pod uzlem Names.</span><span class="sxs-lookup"><span data-stu-id="83db3-110">Replace the `Name` parameter with the name of a value that exists directly under the Names node.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="83db3-111">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="83db3-111">Robust Programming</span></span>  
 <span data-ttu-id="83db3-112">Projděte si strukturu registru, kde najdete vhodné umístění pro váš klíč.</span><span class="sxs-lookup"><span data-stu-id="83db3-112">Examine the registry structure to find a suitable location for your key.</span></span> <span data-ttu-id="83db3-113">Můžete například chtít otevřít softwarový klíč aktuálního uživatele a vytvořit klíč s názvem vaší společnosti.</span><span class="sxs-lookup"><span data-stu-id="83db3-113">For example, you might want to open the Software key of the current user, and create a key with your company's name.</span></span> <span data-ttu-id="83db3-114">Pak přidejte hodnoty registru do klíče vaší společnosti.</span><span class="sxs-lookup"><span data-stu-id="83db3-114">Then add the registry values to your company's key.</span></span>  
  
 <span data-ttu-id="83db3-115">Následující podmínky mohou způsobit výjimku:</span><span class="sxs-lookup"><span data-stu-id="83db3-115">The following conditions might cause an exception:</span></span>  
  
- <span data-ttu-id="83db3-116">Název klíče je null.</span><span class="sxs-lookup"><span data-stu-id="83db3-116">The name of the key is null.</span></span>  
  
- <span data-ttu-id="83db3-117">Uživatel nemá oprávnění k vytváření klíčů registru.</span><span class="sxs-lookup"><span data-stu-id="83db3-117">The user does not have permissions to create registry keys.</span></span>  
  
- <span data-ttu-id="83db3-118">Název klíče překračuje limit 255 znaků.</span><span class="sxs-lookup"><span data-stu-id="83db3-118">The key name exceeds the 255-character limit.</span></span>  
  
- <span data-ttu-id="83db3-119">Klíč je uzavřený.</span><span class="sxs-lookup"><span data-stu-id="83db3-119">The key is closed.</span></span>  
  
- <span data-ttu-id="83db3-120">Klíč registru je jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="83db3-120">The registry key is read-only.</span></span>  
  
## <a name="net-security"></a><span data-ttu-id="83db3-121">Zabezpečení .NET</span><span class="sxs-lookup"><span data-stu-id="83db3-121">.NET Security</span></span>  
 <span data-ttu-id="83db3-122">Je bezpečnější zapsat data do složky uživatele – `Microsoft.Win32.Registry.CurrentUser` místo do místního počítače – `Microsoft.Win32.Registry.LocalMachine` .</span><span class="sxs-lookup"><span data-stu-id="83db3-122">It is more secure to write data to the user folder — `Microsoft.Win32.Registry.CurrentUser` — rather than to the local computer — `Microsoft.Win32.Registry.LocalMachine`.</span></span>  
  
 <span data-ttu-id="83db3-123">Když vytváříte hodnotu registru, musíte se rozhodnout, co dělat, pokud tato hodnota již existuje.</span><span class="sxs-lookup"><span data-stu-id="83db3-123">When you create a registry value, you need to decide what to do if that value already exists.</span></span> <span data-ttu-id="83db3-124">Jiný proces, pravděpodobně škodlivý, již mohl vytvořit hodnotu a mít k ní přístup.</span><span class="sxs-lookup"><span data-stu-id="83db3-124">Another process, perhaps a malicious one, may have already created the value and have access to it.</span></span> <span data-ttu-id="83db3-125">Při vložení dat do hodnoty registru jsou data k dispozici pro druhý proces.</span><span class="sxs-lookup"><span data-stu-id="83db3-125">When you put data in the registry value, the data is available to the other process.</span></span> <span data-ttu-id="83db3-126">Chcete-li tomu zabránit, použijte.`Overload:Microsoft.Win32.RegistryKey.GetValue`</span><span class="sxs-lookup"><span data-stu-id="83db3-126">To prevent this, use the.`Overload:Microsoft.Win32.RegistryKey.GetValue`</span></span> <span data-ttu-id="83db3-127">Metoda.</span><span class="sxs-lookup"><span data-stu-id="83db3-127">method.</span></span> <span data-ttu-id="83db3-128">Vrátí hodnotu null, pokud klíč ještě neexistuje.</span><span class="sxs-lookup"><span data-stu-id="83db3-128">It returns null if the key does not already exist.</span></span>  
  
 <span data-ttu-id="83db3-129">Není bezpečné ukládat tajné klíče, jako jsou hesla, v registru jako prostý text, a to i v případě, že je klíč registru chráněný pomocí seznamů řízení přístupu (ACL).</span><span class="sxs-lookup"><span data-stu-id="83db3-129">It is not secure to store secrets, such as passwords, in the registry as plain text, even if the registry key is protected by access control lists (ACL).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83db3-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="83db3-130">See also</span></span>

- <xref:System.IO?displayProperty=nameWithType>
- [<span data-ttu-id="83db3-131">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="83db3-131">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="83db3-132">Systém souborů a registr (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="83db3-132">File System and the Registry (C# Programming Guide)</span></span>](./index.md)
- [<span data-ttu-id="83db3-133">Čtení, zápis a odstranění z registru pomocí jazyka C #</span><span class="sxs-lookup"><span data-stu-id="83db3-133">Read, write and delete from the registry with C#</span></span>](https://www.codeproject.com/Articles/3389/Read-write-and-delete-from-registry-with-C)
