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
# <a name="how-to-create-a-key-in-the-registry-c-programming-guide"></a><span data-ttu-id="c4afe-102">Jak vytvořit klíč v registru (C# Programovací průvodce)</span><span class="sxs-lookup"><span data-stu-id="c4afe-102">How to create a key in the registry (C# Programming Guide)</span></span>
<span data-ttu-id="c4afe-103">Tento příklad přidá dvojici hodnot "Jméno" a "Isabella" do registru aktuálního uživatele pod klíčem "Jména".</span><span class="sxs-lookup"><span data-stu-id="c4afe-103">This example adds the value pair, "Name" and "Isabella", to the current user's registry, under the key "Names".</span></span>  
  
## <a name="example"></a><span data-ttu-id="c4afe-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="c4afe-104">Example</span></span>  
  
```csharp  
Microsoft.Win32.RegistryKey key;  
key = Microsoft.Win32.Registry.CurrentUser.CreateSubKey("Names");  
key.SetValue("Name", "Isabella");  
key.Close();  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="c4afe-105">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="c4afe-105">Compiling the Code</span></span>  
  
- <span data-ttu-id="c4afe-106">Zkopírujte kód a vložte jej do `Main` metody konzolové aplikace.</span><span class="sxs-lookup"><span data-stu-id="c4afe-106">Copy the code and paste it into the `Main` method of a console application.</span></span>  
  
- <span data-ttu-id="c4afe-107">Nahraďte `Names` parametr názvem klíče, který existuje přímo pod HKEY_CURRENT_USER uzlu registru.</span><span class="sxs-lookup"><span data-stu-id="c4afe-107">Replace the `Names` parameter with the name of a key that exists directly under the HKEY_CURRENT_USER node of the registry.</span></span>  
  
- <span data-ttu-id="c4afe-108">Nahraďte `Name` parametr názvem hodnoty, která existuje přímo pod názvem Název uzlu.</span><span class="sxs-lookup"><span data-stu-id="c4afe-108">Replace the `Name` parameter with the name of a value that exists directly under the Names node.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="c4afe-109">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="c4afe-109">Robust Programming</span></span>  
 <span data-ttu-id="c4afe-110">Zkontrolujte strukturu registru najít vhodné umístění pro váš klíč.</span><span class="sxs-lookup"><span data-stu-id="c4afe-110">Examine the registry structure to find a suitable location for your key.</span></span> <span data-ttu-id="c4afe-111">Můžete například otevřít klíč Software aktuálního uživatele a vytvořit klíč s názvem vaší společnosti.</span><span class="sxs-lookup"><span data-stu-id="c4afe-111">For example, you might want to open the Software key of the current user, and create a key with your company's name.</span></span> <span data-ttu-id="c4afe-112">Pak přidejte hodnoty registru do klíče vaší společnosti.</span><span class="sxs-lookup"><span data-stu-id="c4afe-112">Then add the registry values to your company's key.</span></span>  
  
 <span data-ttu-id="c4afe-113">Následující podmínky mohou způsobit výjimku:</span><span class="sxs-lookup"><span data-stu-id="c4afe-113">The following conditions might cause an exception:</span></span>  
  
- <span data-ttu-id="c4afe-114">Název klíče je null.</span><span class="sxs-lookup"><span data-stu-id="c4afe-114">The name of the key is null.</span></span>  
  
- <span data-ttu-id="c4afe-115">Uživatel nemá oprávnění k vytváření klíčů registru.</span><span class="sxs-lookup"><span data-stu-id="c4afe-115">The user does not have permissions to create registry keys.</span></span>  
  
- <span data-ttu-id="c4afe-116">Název klíče překračuje limit 255 znaků.</span><span class="sxs-lookup"><span data-stu-id="c4afe-116">The key name exceeds the 255-character limit.</span></span>  
  
- <span data-ttu-id="c4afe-117">Klíč je zavřený.</span><span class="sxs-lookup"><span data-stu-id="c4afe-117">The key is closed.</span></span>  
  
- <span data-ttu-id="c4afe-118">Klíč registru je jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="c4afe-118">The registry key is read-only.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="c4afe-119">Zabezpečení rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="c4afe-119">.NET Framework Security</span></span>  
 <span data-ttu-id="c4afe-120">Je bezpečnější zapisovat data do `Microsoft.Win32.Registry.CurrentUser` složky uživatele – `Microsoft.Win32.Registry.LocalMachine`nikoli do místního počítače .</span><span class="sxs-lookup"><span data-stu-id="c4afe-120">It is more secure to write data to the user folder — `Microsoft.Win32.Registry.CurrentUser` — rather than to the local computer — `Microsoft.Win32.Registry.LocalMachine`.</span></span>  
  
 <span data-ttu-id="c4afe-121">Při vytváření hodnoty registru se musíte rozhodnout, co dělat, pokud tato hodnota již existuje.</span><span class="sxs-lookup"><span data-stu-id="c4afe-121">When you create a registry value, you need to decide what to do if that value already exists.</span></span> <span data-ttu-id="c4afe-122">Jiný proces, možná škodlivý, může mít již vytvořilhodnotu a mají k ní přístup.</span><span class="sxs-lookup"><span data-stu-id="c4afe-122">Another process, perhaps a malicious one, may have already created the value and have access to it.</span></span> <span data-ttu-id="c4afe-123">Když vložíte data do hodnoty registru, data jsou k dispozici pro jiný proces.</span><span class="sxs-lookup"><span data-stu-id="c4afe-123">When you put data in the registry value, the data is available to the other process.</span></span> <span data-ttu-id="c4afe-124">Chcete-li tomu zabránit, použijte.`Overload:Microsoft.Win32.RegistryKey.GetValue`</span><span class="sxs-lookup"><span data-stu-id="c4afe-124">To prevent this, use the.`Overload:Microsoft.Win32.RegistryKey.GetValue`</span></span> <span data-ttu-id="c4afe-125">Metoda.</span><span class="sxs-lookup"><span data-stu-id="c4afe-125">method.</span></span> <span data-ttu-id="c4afe-126">Vrátí hodnotu null, pokud klíč ještě neexistuje.</span><span class="sxs-lookup"><span data-stu-id="c4afe-126">It returns null if the key does not already exist.</span></span>  
  
 <span data-ttu-id="c4afe-127">Není bezpečné ukládat tajné klíče, například hesla, do registru jako prostý text, i v případě, že klíč registru je chráněn seznamy řízení přístupu (ACL).</span><span class="sxs-lookup"><span data-stu-id="c4afe-127">It is not secure to store secrets, such as passwords, in the registry as plain text, even if the registry key is protected by access control lists (ACL).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4afe-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="c4afe-128">See also</span></span>

- <xref:System.IO?displayProperty=nameWithType>
- [<span data-ttu-id="c4afe-129">Programovací příručka jazyka C#</span><span class="sxs-lookup"><span data-stu-id="c4afe-129">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="c4afe-130">Systém souborů a registr (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="c4afe-130">File System and the Registry (C# Programming Guide)</span></span>](./index.md)
- [<span data-ttu-id="c4afe-131">Číst, psát a mazat z registru s C #</span><span class="sxs-lookup"><span data-stu-id="c4afe-131">Read, write and delete from the registry with C#</span></span>](https://www.codeproject.com/Articles/3389/Read-write-and-delete-from-registry-with-C)
