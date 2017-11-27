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
# <a name="how-to-create-a-key-in-the-registry-visual-c"></a><span data-ttu-id="8b8c7-102">Postupy: Vytvoření klíče v registru (Visual C#)</span><span class="sxs-lookup"><span data-stu-id="8b8c7-102">How to: Create a Key In the Registry (Visual C#)</span></span>
<span data-ttu-id="8b8c7-103">Tento příklad přidá dvojice hodnot, "Název" a "Isabella", do aktuálního uživatele registru pod klíčem "Názvy".</span><span class="sxs-lookup"><span data-stu-id="8b8c7-103">This example adds the value pair, "Name" and "Isabella", to the current user's registry, under the key "Names".</span></span>  
  
## <a name="example"></a><span data-ttu-id="8b8c7-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="8b8c7-104">Example</span></span>  
  
```  
Microsoft.Win32.RegistryKey key;  
key = Microsoft.Win32.Registry.CurrentUser.CreateSubKey("Names");  
key.SetValue("Name", "Isabella");  
key.Close();  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="8b8c7-105">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="8b8c7-105">Compiling the Code</span></span>  
  
-   <span data-ttu-id="8b8c7-106">Zkopírovat kód a vložte ji do `Main` metoda konzolové aplikace.</span><span class="sxs-lookup"><span data-stu-id="8b8c7-106">Copy the code and paste it into the `Main` method of a console application.</span></span>  
  
-   <span data-ttu-id="8b8c7-107">Nahraďte `Names` parametr s názvem klíče, který existuje přímo v uzlu HKEY_CURRENT_USER registru.</span><span class="sxs-lookup"><span data-stu-id="8b8c7-107">Replace the `Names` parameter with the name of a key that exists directly under the HKEY_CURRENT_USER node of the registry.</span></span>  
  
-   <span data-ttu-id="8b8c7-108">Nahraďte `Name` parametr s názvem hodnotu, která existuje přímo v uzlu názvy.</span><span class="sxs-lookup"><span data-stu-id="8b8c7-108">Replace the `Name` parameter with the name of a value that exists directly under the Names node.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="8b8c7-109">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="8b8c7-109">Robust Programming</span></span>  
 <span data-ttu-id="8b8c7-110">Zkontrolujte strukturu registru se najít vhodného místa pro váš klíč.</span><span class="sxs-lookup"><span data-stu-id="8b8c7-110">Examine the registry structure to find a suitable location for your key.</span></span> <span data-ttu-id="8b8c7-111">Například můžete chtít otevřít klíč softwaru aktuálního uživatele a vytvořte klíč s názvem vaší společnosti.</span><span class="sxs-lookup"><span data-stu-id="8b8c7-111">For example, you might want to open the Software key of the current user, and create a key with your company's name.</span></span> <span data-ttu-id="8b8c7-112">Přidejte do vaší společnosti klíč hodnoty registru.</span><span class="sxs-lookup"><span data-stu-id="8b8c7-112">Then add the registry values to your company's key.</span></span>  
  
 <span data-ttu-id="8b8c7-113">Následujících podmínek může způsobit výjimku:</span><span class="sxs-lookup"><span data-stu-id="8b8c7-113">The following conditions might cause an exception:</span></span>  
  
-   <span data-ttu-id="8b8c7-114">Název klíče, má hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="8b8c7-114">The name of the key is null.</span></span>  
  
-   <span data-ttu-id="8b8c7-115">Uživatel nemá oprávnění k vytvoření klíče registru.</span><span class="sxs-lookup"><span data-stu-id="8b8c7-115">The user does not have permissions to create registry keys.</span></span>  
  
-   <span data-ttu-id="8b8c7-116">Název klíče překračuje limit 255 znaků.</span><span class="sxs-lookup"><span data-stu-id="8b8c7-116">The key name exceeds the 255-character limit.</span></span>  
  
-   <span data-ttu-id="8b8c7-117">Klíč je uzavřen.</span><span class="sxs-lookup"><span data-stu-id="8b8c7-117">The key is closed.</span></span>  
  
-   <span data-ttu-id="8b8c7-118">Klíč registru je jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="8b8c7-118">The registry key is read-only.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="8b8c7-119">Zabezpečení rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="8b8c7-119">.NET Framework Security</span></span>  
 <span data-ttu-id="8b8c7-120">Je bezpečnější zapsat data do složky uživatele – `Microsoft.Win32.Registry.CurrentUser` – místo na místním počítači – `Microsoft.Win32.Registry.LocalMachine`.</span><span class="sxs-lookup"><span data-stu-id="8b8c7-120">It is more secure to write data to the user folder — `Microsoft.Win32.Registry.CurrentUser` — rather than to the local computer — `Microsoft.Win32.Registry.LocalMachine`.</span></span>  
  
 <span data-ttu-id="8b8c7-121">Když vytvoříte hodnotu registru, budete muset rozhodnout, co dělat v případě, že hodnota již existuje.</span><span class="sxs-lookup"><span data-stu-id="8b8c7-121">When you create a registry value, you need to decide what to do if that value already exists.</span></span> <span data-ttu-id="8b8c7-122">Jiný proces, případně škodlivý jeden už možná máte vytvořené hodnota a mít přístup k němu.</span><span class="sxs-lookup"><span data-stu-id="8b8c7-122">Another process, perhaps a malicious one, may have already created the value and have access to it.</span></span> <span data-ttu-id="8b8c7-123">Když vložíte dat v hodnotě registru, data jsou k dispozici pro jiný proces.</span><span class="sxs-lookup"><span data-stu-id="8b8c7-123">When you put data in the registry value, the data is available to the other process.</span></span> <span data-ttu-id="8b8c7-124">Chcete-li tomu zabránit, použijte.`Overload:Microsoft.Win32.RegistryKey.GetValue`</span><span class="sxs-lookup"><span data-stu-id="8b8c7-124">To prevent this, use the.`Overload:Microsoft.Win32.RegistryKey.GetValue`</span></span> <span data-ttu-id="8b8c7-125">Metoda.</span><span class="sxs-lookup"><span data-stu-id="8b8c7-125">method.</span></span> <span data-ttu-id="8b8c7-126">Vrátí hodnotu null, pokud klíč ještě neexistuje.</span><span class="sxs-lookup"><span data-stu-id="8b8c7-126">It returns null if the key does not already exist.</span></span>  
  
 <span data-ttu-id="8b8c7-127">Není bezpečné uchovávat tajné údaje, jako jsou hesla, v registru jako prostý text, i v případě, že je klíč registru chráněn pomocí seznamů řízení přístupu (ACL).</span><span class="sxs-lookup"><span data-stu-id="8b8c7-127">It is not secure to store secrets, such as passwords, in the registry as plain text, even if the registry key is protected by access control lists (ACL).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b8c7-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="8b8c7-128">See Also</span></span>  
 <xref:System.IO?displayProperty=nameWithType>  
 [<span data-ttu-id="8b8c7-129">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="8b8c7-129">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="8b8c7-130">Systém souborů a registr (C# Průvodce programováním)</span><span class="sxs-lookup"><span data-stu-id="8b8c7-130">File System and the Registry (C# Programming Guide)</span></span>](../../../csharp/programming-guide/file-system/index.md)  
 [<span data-ttu-id="8b8c7-131">Čtení, zápis a odstranění z registru pomocí C#</span><span class="sxs-lookup"><span data-stu-id="8b8c7-131">Read, write and delete from the registry with C#</span></span>](http://www.codeproject.com/Articles/3389/Read-write-and-delete-from-registry-with-C)
