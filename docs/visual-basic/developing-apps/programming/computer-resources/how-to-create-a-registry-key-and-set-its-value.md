---
title: 'Postupy: Vytvoření klíče registru a nastavení jeho hodnoty'
ms.date: 07/20/2015
f1_keywords:
- RegistryKey.CreateSubKey
- RegistryKey.SetValue
helpviewer_keywords:
- registry keys [Visual Basic], creating
- registry [Visual Basic], adding values
- registry [Visual Basic], adding keys
- registry keys [Visual Basic], setting values
- examples [Visual Basic], registry
ms.assetid: d3e40f74-c283-480c-ab18-e5e9052cd814
ms.openlocfilehash: 459c4b3f971009ee4b6b669c55bc058db0826595
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "74349203"
---
# <a name="how-to-create-a-registry-key-and-set-its-value-in-visual-basic"></a><span data-ttu-id="d0bb7-102">Postupy: Vytvoření klíče registru a nastavení jeho hodnoty v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d0bb7-102">How to: Create a Registry Key and Set Its Value in Visual Basic</span></span>

<span data-ttu-id="d0bb7-103">`CreateSubKey` Metodu `My.Computer.Registry` objektu lze použít k vytvoření klíče registru.</span><span class="sxs-lookup"><span data-stu-id="d0bb7-103">The `CreateSubKey` method of the `My.Computer.Registry` object can be used to create a registry key.</span></span>

## <a name="procedure"></a><span data-ttu-id="d0bb7-104">Postup</span><span class="sxs-lookup"><span data-stu-id="d0bb7-104">Procedure</span></span>

### <a name="to-create-a-registry-key"></a><span data-ttu-id="d0bb7-105">Vytvoření klíče registru</span><span class="sxs-lookup"><span data-stu-id="d0bb7-105">To create a registry key</span></span>

- <span data-ttu-id="d0bb7-106">Použijte `CreateSubKey` metodu, která určuje, který podregistr umístit klíč, a také název klíče.</span><span class="sxs-lookup"><span data-stu-id="d0bb7-106">Use the `CreateSubKey` method, specifying which hive to place the key under as well as the name of the key.</span></span> <span data-ttu-id="d0bb7-107">V parametru `Subkey` se nerozlišují malá a velká písmena.</span><span class="sxs-lookup"><span data-stu-id="d0bb7-107">The parameter `Subkey` is not case-sensitive.</span></span> <span data-ttu-id="d0bb7-108">Tento příklad vytvoří klíč `MyTestKey` registru v rámci HKEY_CURRENT_USER.</span><span class="sxs-lookup"><span data-stu-id="d0bb7-108">This example creates the registry key `MyTestKey` under HKEY_CURRENT_USER.</span></span>

    [!code-vb[VbResourceTasks#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#17)]

### <a name="to-create-a-registry-key-and-set-a-value-in-it"></a><span data-ttu-id="d0bb7-109">Vytvoření klíče registru a nastavení jeho hodnoty</span><span class="sxs-lookup"><span data-stu-id="d0bb7-109">To create a registry key and set a value in it</span></span>

1. <span data-ttu-id="d0bb7-110">Použijte `CreateSubkey` metodu, která určuje, který podregistr umístit klíč, a také název klíče.</span><span class="sxs-lookup"><span data-stu-id="d0bb7-110">Use the `CreateSubkey` method, specifying which hive to place the key under as well as the name of the key.</span></span> <span data-ttu-id="d0bb7-111">Tento příklad vytvoří klíč `MyTestKey` registru v rámci HKEY_CURRENT_USER.</span><span class="sxs-lookup"><span data-stu-id="d0bb7-111">This example creates the registry key `MyTestKey` under HKEY_CURRENT_USER.</span></span>

    [!code-vb[VbResourceTasks#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#17)]

2. <span data-ttu-id="d0bb7-112">Nastavte hodnotu pomocí `SetValue` metody.</span><span class="sxs-lookup"><span data-stu-id="d0bb7-112">Set the value with the `SetValue` method.</span></span> <span data-ttu-id="d0bb7-113">V tomto příkladu se nastaví hodnota řetězce.</span><span class="sxs-lookup"><span data-stu-id="d0bb7-113">This example sets the string value.</span></span> <span data-ttu-id="d0bb7-114">"MyTestKeyValue" na "Toto je testovací hodnota".</span><span class="sxs-lookup"><span data-stu-id="d0bb7-114">"MyTestKeyValue" to "This is a test value".</span></span>

    [!code-vb[VbResourceTasks#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#14)]

## <a name="example"></a><span data-ttu-id="d0bb7-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="d0bb7-115">Example</span></span>

<span data-ttu-id="d0bb7-116">Tento příklad vytvoří klíč `MyTestKey` registru v rámci HKEY_CURRENT_USER a poté nastaví hodnotu `MyTestKeyValue` řetězce na. `This is a test value`</span><span class="sxs-lookup"><span data-stu-id="d0bb7-116">This example creates the registry key `MyTestKey` under HKEY_CURRENT_USER and then sets the string value `MyTestKeyValue` to `This is a test value`.</span></span>

[!code-vb[VbResourceTasks#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#15)]

## <a name="robust-programming"></a><span data-ttu-id="d0bb7-117">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="d0bb7-117">Robust Programming</span></span>

<span data-ttu-id="d0bb7-118">Projděte si strukturu registru, kde najdete vhodné umístění pro váš klíč.</span><span class="sxs-lookup"><span data-stu-id="d0bb7-118">Examine the registry structure to find a suitable location for your key.</span></span> <span data-ttu-id="d0bb7-119">Například můžete chtít otevřít HKEY_CURRENT_USER klíč \Software aktuálního uživatele a vytvořit klíč s názvem vaší společnosti.</span><span class="sxs-lookup"><span data-stu-id="d0bb7-119">For example, you may want to open the HKEY_CURRENT_USER\Software key of the current user, and create a key with your company's name.</span></span> <span data-ttu-id="d0bb7-120">Pak přidejte hodnoty registru do klíče vaší společnosti.</span><span class="sxs-lookup"><span data-stu-id="d0bb7-120">Then add the registry values to your company's key.</span></span>

<span data-ttu-id="d0bb7-121">Při čtení registru z webové aplikace závisí aktuální uživatel na ověřování a zosobnění implementované ve webové aplikaci.</span><span class="sxs-lookup"><span data-stu-id="d0bb7-121">When reading the registry from a Web application, the current user depends on the authentication and impersonation implemented in the Web application.</span></span>

<span data-ttu-id="d0bb7-122">Je bezpečnější zapsat data do složky uživatele (<xref:Microsoft.Win32.Registry.CurrentUser>) místo do místního počítače (<xref:Microsoft.Win32.Registry.LocalMachine>).</span><span class="sxs-lookup"><span data-stu-id="d0bb7-122">It is more secure to write data to the user folder (<xref:Microsoft.Win32.Registry.CurrentUser>) rather than to the local computer (<xref:Microsoft.Win32.Registry.LocalMachine>).</span></span>

<span data-ttu-id="d0bb7-123">Když vytváříte hodnotu registru, musíte se rozhodnout, co dělat, pokud tato hodnota již existuje.</span><span class="sxs-lookup"><span data-stu-id="d0bb7-123">When you create a registry value, you need to decide what to do if that value already exists.</span></span> <span data-ttu-id="d0bb7-124">Jiný proces, pravděpodobně škodlivý, již mohl vytvořit hodnotu a mít k ní přístup.</span><span class="sxs-lookup"><span data-stu-id="d0bb7-124">Another process, perhaps a malicious one, may have already created the value and have access to it.</span></span> <span data-ttu-id="d0bb7-125">Při vložení dat do hodnoty registru jsou data k dispozici pro druhý proces.</span><span class="sxs-lookup"><span data-stu-id="d0bb7-125">When you put data in the registry value, the data is available to the other process.</span></span> <span data-ttu-id="d0bb7-126">Chcete-li tomu zabránit, <xref:Microsoft.Win32.RegistryKey.GetValue%2A> použijte metodu.</span><span class="sxs-lookup"><span data-stu-id="d0bb7-126">To prevent this, use the <xref:Microsoft.Win32.RegistryKey.GetValue%2A> method.</span></span> <span data-ttu-id="d0bb7-127">Vrátí `Nothing` , pokud klíč ještě neexistuje.</span><span class="sxs-lookup"><span data-stu-id="d0bb7-127">It returns `Nothing` if the key does not already exist.</span></span>

<span data-ttu-id="d0bb7-128">Není bezpečné ukládat tajné klíče, jako jsou hesla, v registru jako prostý text, a to i v případě, že je klíč registru chráněný pomocí seznamů ACL (seznamy Access Control).</span><span class="sxs-lookup"><span data-stu-id="d0bb7-128">It is not secure to store secrets, such as passwords, in the registry as plain text, even if the registry key is protected by ACLs (Access Control Lists).</span></span>

<span data-ttu-id="d0bb7-129">Následující podmínky mohou způsobit výjimku:</span><span class="sxs-lookup"><span data-stu-id="d0bb7-129">The following conditions may cause an exception:</span></span>

- <span data-ttu-id="d0bb7-130">Název klíče je `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="d0bb7-130">The name of the key is `Nothing` (<xref:System.ArgumentNullException>).</span></span>

- <span data-ttu-id="d0bb7-131">Uživatel nemá oprávnění k vytváření klíčů registru (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="d0bb7-131">The user does not have permissions to create registry keys (<xref:System.Security.SecurityException>).</span></span>

- <span data-ttu-id="d0bb7-132">Název klíče překračuje limit 255 znaků (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="d0bb7-132">The key name exceeds the 255-character limit (<xref:System.ArgumentException>).</span></span>

- <span data-ttu-id="d0bb7-133">Klíč je uzavřený (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="d0bb7-133">The key is closed (<xref:System.IO.IOException>).</span></span>

- <span data-ttu-id="d0bb7-134">Klíč registru je jen pro čtení (<xref:System.UnauthorizedAccessException>).</span><span class="sxs-lookup"><span data-stu-id="d0bb7-134">The registry key is read-only (<xref:System.UnauthorizedAccessException>).</span></span>

## <a name="net-framework-security"></a><span data-ttu-id="d0bb7-135">Zabezpečení rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="d0bb7-135">.NET Framework Security</span></span>

<span data-ttu-id="d0bb7-136">Pro spuštění tohoto procesu vaše sestavení vyžaduje úroveň oprávnění udělené <xref:System.Security.Permissions.RegistryPermission> třídou.</span><span class="sxs-lookup"><span data-stu-id="d0bb7-136">To run this process, your assembly requires a privilege level granted by the <xref:System.Security.Permissions.RegistryPermission> class.</span></span> <span data-ttu-id="d0bb7-137">Pokud používáte v kontextu s částečným vztahem důvěryhodnosti, proces může vyvolat výjimku z důvodu nedostatečných oprávnění.</span><span class="sxs-lookup"><span data-stu-id="d0bb7-137">If you are running in a partial-trust context, the process might throw an exception due to insufficient privileges.</span></span> <span data-ttu-id="d0bb7-138">Podobně uživatel musí mít správné seznamy ACL pro vytvoření nebo zápis do nastavení.</span><span class="sxs-lookup"><span data-stu-id="d0bb7-138">Similarly, the user must have the correct ACLs for creating or writing to settings.</span></span> <span data-ttu-id="d0bb7-139">Například místní aplikace, která má oprávnění zabezpečení přístupu kódu, nemusí mít oprávnění operačního systému.</span><span class="sxs-lookup"><span data-stu-id="d0bb7-139">For example, a local application that has the code access security permission might not have operating system permission.</span></span> <span data-ttu-id="d0bb7-140">Další informace najdete v tématu [Základy zabezpečení přístupu ke kódu](../../../../framework/misc/code-access-security-basics.md).</span><span class="sxs-lookup"><span data-stu-id="d0bb7-140">For more information, see [Code Access Security Basics](../../../../framework/misc/code-access-security-basics.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d0bb7-141">Viz také</span><span class="sxs-lookup"><span data-stu-id="d0bb7-141">See also</span></span>

- <xref:Microsoft.VisualBasic.MyServices.RegistryProxy>
- <xref:Microsoft.VisualBasic.MyServices.RegistryProxy.CurrentUser%2A>
- <xref:Microsoft.Win32.RegistryKey.CreateSubKey%2A>
- [<span data-ttu-id="d0bb7-142">Čtení z registru a zápis do něj</span><span class="sxs-lookup"><span data-stu-id="d0bb7-142">Reading from and Writing to the Registry</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/reading-from-and-writing-to-the-registry.md)
- [<span data-ttu-id="d0bb7-143">Základy zabezpečení přístupu kódu</span><span class="sxs-lookup"><span data-stu-id="d0bb7-143">Code Access Security Basics</span></span>](../../../../framework/misc/code-access-security-basics.md)
