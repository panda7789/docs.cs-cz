---
title: 'Postupy: Vytvoření klíče v registru (Visual C#)'
ms.date: 07/20/2015
helpviewer_keywords:
- registry, adding keys and values [C#]
- registry keys, creating [C#]
- keys, creating in registry
ms.assetid: 8fa475b0-e01f-483a-9327-fd03488fdf5d
ms.openlocfilehash: 0982baea2327daf23726ef269d53388d6011703d
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64596150"
---
# <a name="how-to-create-a-key-in-the-registry-visual-c"></a><span data-ttu-id="0118c-102">Postupy: Vytvoření klíče v registru (Visual C#)</span><span class="sxs-lookup"><span data-stu-id="0118c-102">How to: Create a Key In the Registry (Visual C#)</span></span>
<span data-ttu-id="0118c-103">V tomto příkladu přidá dvojici hodnot "Name" a "Isabella" do registru aktuálního uživatele pod klíčem "Names".</span><span class="sxs-lookup"><span data-stu-id="0118c-103">This example adds the value pair, "Name" and "Isabella", to the current user's registry, under the key "Names".</span></span>  
  
## <a name="example"></a><span data-ttu-id="0118c-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="0118c-104">Example</span></span>  
  
```csharp  
Microsoft.Win32.RegistryKey key;  
key = Microsoft.Win32.Registry.CurrentUser.CreateSubKey("Names");  
key.SetValue("Name", "Isabella");  
key.Close();  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="0118c-105">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="0118c-105">Compiling the Code</span></span>  
  
- <span data-ttu-id="0118c-106">Zkopírujte kód a vložte ho do `Main` metoda konzolové aplikace.</span><span class="sxs-lookup"><span data-stu-id="0118c-106">Copy the code and paste it into the `Main` method of a console application.</span></span>  
  
- <span data-ttu-id="0118c-107">Nahradit `Names` parametr s názvem klíče, který existuje přímo v uzlu registru HKEY_CURRENT_USER.</span><span class="sxs-lookup"><span data-stu-id="0118c-107">Replace the `Names` parameter with the name of a key that exists directly under the HKEY_CURRENT_USER node of the registry.</span></span>  
  
- <span data-ttu-id="0118c-108">Nahradit `Name` parametr s názvem hodnoty, která je uvedena přímo v uzlu názvy.</span><span class="sxs-lookup"><span data-stu-id="0118c-108">Replace the `Name` parameter with the name of a value that exists directly under the Names node.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="0118c-109">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="0118c-109">Robust Programming</span></span>  
 <span data-ttu-id="0118c-110">Zkontrolujte strukturu registrů k vyhledání příhodného místa pro váš klíč.</span><span class="sxs-lookup"><span data-stu-id="0118c-110">Examine the registry structure to find a suitable location for your key.</span></span> <span data-ttu-id="0118c-111">Například můžete chtít otevřít softwarový klíč aktuálního uživatele a vytvořte klíč s názvem vaší společnosti.</span><span class="sxs-lookup"><span data-stu-id="0118c-111">For example, you might want to open the Software key of the current user, and create a key with your company's name.</span></span> <span data-ttu-id="0118c-112">Hodnoty registru obnovte klíče vaší společnosti.</span><span class="sxs-lookup"><span data-stu-id="0118c-112">Then add the registry values to your company's key.</span></span>  
  
 <span data-ttu-id="0118c-113">Následující podmínky mohou způsobit výjimku:</span><span class="sxs-lookup"><span data-stu-id="0118c-113">The following conditions might cause an exception:</span></span>  
  
- <span data-ttu-id="0118c-114">Název klíče je null.</span><span class="sxs-lookup"><span data-stu-id="0118c-114">The name of the key is null.</span></span>  
  
- <span data-ttu-id="0118c-115">Uživatel nemá oprávnění k vytvoření klíče registru.</span><span class="sxs-lookup"><span data-stu-id="0118c-115">The user does not have permissions to create registry keys.</span></span>  
  
- <span data-ttu-id="0118c-116">Název klíče překračuje limit 255 znaků.</span><span class="sxs-lookup"><span data-stu-id="0118c-116">The key name exceeds the 255-character limit.</span></span>  
  
- <span data-ttu-id="0118c-117">Klíč je uzavřen.</span><span class="sxs-lookup"><span data-stu-id="0118c-117">The key is closed.</span></span>  
  
- <span data-ttu-id="0118c-118">Klíč registru je jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="0118c-118">The registry key is read-only.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="0118c-119">Zabezpečení rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="0118c-119">.NET Framework Security</span></span>  
 <span data-ttu-id="0118c-120">Je bezpečnější zapsat data do složky uživatele – `Microsoft.Win32.Registry.CurrentUser` – místo na místním počítači – `Microsoft.Win32.Registry.LocalMachine`.</span><span class="sxs-lookup"><span data-stu-id="0118c-120">It is more secure to write data to the user folder — `Microsoft.Win32.Registry.CurrentUser` — rather than to the local computer — `Microsoft.Win32.Registry.LocalMachine`.</span></span>  
  
 <span data-ttu-id="0118c-121">Když vytváříte hodnotu registru, musíte se rozhodnout, co dělat, pokud tuto hodnotu již existuje.</span><span class="sxs-lookup"><span data-stu-id="0118c-121">When you create a registry value, you need to decide what to do if that value already exists.</span></span> <span data-ttu-id="0118c-122">Jiný proces, možná škodlivý ten už možná máte vytvořené hodnotu a k ní máte přístup.</span><span class="sxs-lookup"><span data-stu-id="0118c-122">Another process, perhaps a malicious one, may have already created the value and have access to it.</span></span> <span data-ttu-id="0118c-123">Když vkládáte data do hodnoty registru, data jsou k dispozici pro jiné procesy.</span><span class="sxs-lookup"><span data-stu-id="0118c-123">When you put data in the registry value, the data is available to the other process.</span></span> <span data-ttu-id="0118c-124">Chcete-li tomu zabránit, použijte.`Overload:Microsoft.Win32.RegistryKey.GetValue`</span><span class="sxs-lookup"><span data-stu-id="0118c-124">To prevent this, use the.`Overload:Microsoft.Win32.RegistryKey.GetValue`</span></span> <span data-ttu-id="0118c-125">Metoda.</span><span class="sxs-lookup"><span data-stu-id="0118c-125">method.</span></span> <span data-ttu-id="0118c-126">Vrátí hodnotu null, pokud klíč ještě neexistuje.</span><span class="sxs-lookup"><span data-stu-id="0118c-126">It returns null if the key does not already exist.</span></span>  
  
 <span data-ttu-id="0118c-127">Není bezpečné uchovávat tajemství, jako jsou hesla, v registrech jako prostý text, i v případě, že je klíč registru chráněn pomocí seznamů řízení přístupu (ACL).</span><span class="sxs-lookup"><span data-stu-id="0118c-127">It is not secure to store secrets, such as passwords, in the registry as plain text, even if the registry key is protected by access control lists (ACL).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0118c-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0118c-128">See also</span></span>

- <xref:System.IO?displayProperty=nameWithType>
- [<span data-ttu-id="0118c-129">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="0118c-129">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="0118c-130">Systém souborů a registr (C# Programming Guide)</span><span class="sxs-lookup"><span data-stu-id="0118c-130">File System and the Registry (C# Programming Guide)</span></span>](../../../csharp/programming-guide/file-system/index.md)
- [<span data-ttu-id="0118c-131">Čtení, zápisu a odstranění z registru pomocí C#</span><span class="sxs-lookup"><span data-stu-id="0118c-131">Read, write and delete from the registry with C#</span></span>](https://www.codeproject.com/Articles/3389/Read-write-and-delete-from-registry-with-C)
