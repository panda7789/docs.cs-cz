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
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349203"
---
# <a name="how-to-create-a-registry-key-and-set-its-value-in-visual-basic"></a><span data-ttu-id="f395a-102">Postupy: Vytvoření klíče registru a nastavení jeho hodnoty v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f395a-102">How to: Create a Registry Key and Set Its Value in Visual Basic</span></span>

<span data-ttu-id="f395a-103">The `CreateSubKey` method of the `My.Computer.Registry` object can be used to create a registry key.</span><span class="sxs-lookup"><span data-stu-id="f395a-103">The `CreateSubKey` method of the `My.Computer.Registry` object can be used to create a registry key.</span></span>

## <a name="procedure"></a><span data-ttu-id="f395a-104">Postup</span><span class="sxs-lookup"><span data-stu-id="f395a-104">Procedure</span></span>

### <a name="to-create-a-registry-key"></a><span data-ttu-id="f395a-105">To create a registry key</span><span class="sxs-lookup"><span data-stu-id="f395a-105">To create a registry key</span></span>

- <span data-ttu-id="f395a-106">Use the `CreateSubKey` method, specifying which hive to place the key under as well as the name of the key.</span><span class="sxs-lookup"><span data-stu-id="f395a-106">Use the `CreateSubKey` method, specifying which hive to place the key under as well as the name of the key.</span></span> <span data-ttu-id="f395a-107">The parameter `Subkey` is not case-sensitive.</span><span class="sxs-lookup"><span data-stu-id="f395a-107">The parameter `Subkey` is not case-sensitive.</span></span> <span data-ttu-id="f395a-108">This example creates the registry key `MyTestKey` under HKEY_CURRENT_USER.</span><span class="sxs-lookup"><span data-stu-id="f395a-108">This example creates the registry key `MyTestKey` under HKEY_CURRENT_USER.</span></span>

    [!code-vb[VbResourceTasks#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#17)]

### <a name="to-create-a-registry-key-and-set-a-value-in-it"></a><span data-ttu-id="f395a-109">To create a registry key and set a value in it</span><span class="sxs-lookup"><span data-stu-id="f395a-109">To create a registry key and set a value in it</span></span>

1. <span data-ttu-id="f395a-110">Use the `CreateSubkey` method, specifying which hive to place the key under as well as the name of the key.</span><span class="sxs-lookup"><span data-stu-id="f395a-110">Use the `CreateSubkey` method, specifying which hive to place the key under as well as the name of the key.</span></span> <span data-ttu-id="f395a-111">This example creates the registry key `MyTestKey` under HKEY_CURRENT_USER.</span><span class="sxs-lookup"><span data-stu-id="f395a-111">This example creates the registry key `MyTestKey` under HKEY_CURRENT_USER.</span></span>

    [!code-vb[VbResourceTasks#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#17)]

2. <span data-ttu-id="f395a-112">Set the value with the `SetValue` method.</span><span class="sxs-lookup"><span data-stu-id="f395a-112">Set the value with the `SetValue` method.</span></span> <span data-ttu-id="f395a-113">This example sets the string value.</span><span class="sxs-lookup"><span data-stu-id="f395a-113">This example sets the string value.</span></span> <span data-ttu-id="f395a-114">"MyTestKeyValue" to "This is a test value".</span><span class="sxs-lookup"><span data-stu-id="f395a-114">"MyTestKeyValue" to "This is a test value".</span></span>

    [!code-vb[VbResourceTasks#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#14)]

## <a name="example"></a><span data-ttu-id="f395a-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="f395a-115">Example</span></span>

<span data-ttu-id="f395a-116">This example creates the registry key `MyTestKey` under HKEY_CURRENT_USER and then sets the string value `MyTestKeyValue` to `This is a test value`.</span><span class="sxs-lookup"><span data-stu-id="f395a-116">This example creates the registry key `MyTestKey` under HKEY_CURRENT_USER and then sets the string value `MyTestKeyValue` to `This is a test value`.</span></span>

[!code-vb[VbResourceTasks#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#15)]

## <a name="robust-programming"></a><span data-ttu-id="f395a-117">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="f395a-117">Robust Programming</span></span>

<span data-ttu-id="f395a-118">Examine the registry structure to find a suitable location for your key.</span><span class="sxs-lookup"><span data-stu-id="f395a-118">Examine the registry structure to find a suitable location for your key.</span></span> <span data-ttu-id="f395a-119">For example, you may want to open the HKEY_CURRENT_USER\Software key of the current user, and create a key with your company's name.</span><span class="sxs-lookup"><span data-stu-id="f395a-119">For example, you may want to open the HKEY_CURRENT_USER\Software key of the current user, and create a key with your company's name.</span></span> <span data-ttu-id="f395a-120">Then add the registry values to your company's key.</span><span class="sxs-lookup"><span data-stu-id="f395a-120">Then add the registry values to your company's key.</span></span>

<span data-ttu-id="f395a-121">When reading the registry from a Web application, the current user depends on the authentication and impersonation implemented in the Web application.</span><span class="sxs-lookup"><span data-stu-id="f395a-121">When reading the registry from a Web application, the current user depends on the authentication and impersonation implemented in the Web application.</span></span>

<span data-ttu-id="f395a-122">It is more secure to write data to the user folder (<xref:Microsoft.Win32.Registry.CurrentUser>) rather than to the local computer (<xref:Microsoft.Win32.Registry.LocalMachine>).</span><span class="sxs-lookup"><span data-stu-id="f395a-122">It is more secure to write data to the user folder (<xref:Microsoft.Win32.Registry.CurrentUser>) rather than to the local computer (<xref:Microsoft.Win32.Registry.LocalMachine>).</span></span>

<span data-ttu-id="f395a-123">When you create a registry value, you need to decide what to do if that value already exists.</span><span class="sxs-lookup"><span data-stu-id="f395a-123">When you create a registry value, you need to decide what to do if that value already exists.</span></span> <span data-ttu-id="f395a-124">Another process, perhaps a malicious one, may have already created the value and have access to it.</span><span class="sxs-lookup"><span data-stu-id="f395a-124">Another process, perhaps a malicious one, may have already created the value and have access to it.</span></span> <span data-ttu-id="f395a-125">When you put data in the registry value, the data is available to the other process.</span><span class="sxs-lookup"><span data-stu-id="f395a-125">When you put data in the registry value, the data is available to the other process.</span></span> <span data-ttu-id="f395a-126">To prevent this, use the <xref:Microsoft.Win32.RegistryKey.GetValue%2A> method.</span><span class="sxs-lookup"><span data-stu-id="f395a-126">To prevent this, use the <xref:Microsoft.Win32.RegistryKey.GetValue%2A> method.</span></span> <span data-ttu-id="f395a-127">It returns `Nothing` if the key does not already exist.</span><span class="sxs-lookup"><span data-stu-id="f395a-127">It returns `Nothing` if the key does not already exist.</span></span>

<span data-ttu-id="f395a-128">It is not secure to store secrets, such as passwords, in the registry as plain text, even if the registry key is protected by ACLs (Access Control Lists).</span><span class="sxs-lookup"><span data-stu-id="f395a-128">It is not secure to store secrets, such as passwords, in the registry as plain text, even if the registry key is protected by ACLs (Access Control Lists).</span></span>

<span data-ttu-id="f395a-129">Následující podmínky mohou způsobit výjimku:</span><span class="sxs-lookup"><span data-stu-id="f395a-129">The following conditions may cause an exception:</span></span>

- <span data-ttu-id="f395a-130">The name of the key is `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="f395a-130">The name of the key is `Nothing` (<xref:System.ArgumentNullException>).</span></span>

- <span data-ttu-id="f395a-131">The user does not have permissions to create registry keys (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="f395a-131">The user does not have permissions to create registry keys (<xref:System.Security.SecurityException>).</span></span>

- <span data-ttu-id="f395a-132">The key name exceeds the 255-character limit (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="f395a-132">The key name exceeds the 255-character limit (<xref:System.ArgumentException>).</span></span>

- <span data-ttu-id="f395a-133">The key is closed (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="f395a-133">The key is closed (<xref:System.IO.IOException>).</span></span>

- <span data-ttu-id="f395a-134">The registry key is read-only (<xref:System.UnauthorizedAccessException>).</span><span class="sxs-lookup"><span data-stu-id="f395a-134">The registry key is read-only (<xref:System.UnauthorizedAccessException>).</span></span>

## <a name="net-framework-security"></a><span data-ttu-id="f395a-135">Zabezpečení rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="f395a-135">.NET Framework Security</span></span>

<span data-ttu-id="f395a-136">To run this process, your assembly requires a privilege level granted by the <xref:System.Security.Permissions.RegistryPermission> class.</span><span class="sxs-lookup"><span data-stu-id="f395a-136">To run this process, your assembly requires a privilege level granted by the <xref:System.Security.Permissions.RegistryPermission> class.</span></span> <span data-ttu-id="f395a-137">If you are running in a partial-trust context, the process might throw an exception due to insufficient privileges.</span><span class="sxs-lookup"><span data-stu-id="f395a-137">If you are running in a partial-trust context, the process might throw an exception due to insufficient privileges.</span></span> <span data-ttu-id="f395a-138">Similarly, the user must have the correct ACLs for creating or writing to settings.</span><span class="sxs-lookup"><span data-stu-id="f395a-138">Similarly, the user must have the correct ACLs for creating or writing to settings.</span></span> <span data-ttu-id="f395a-139">For example, a local application that has the code access security permission might not have operating system permission.</span><span class="sxs-lookup"><span data-stu-id="f395a-139">For example, a local application that has the code access security permission might not have operating system permission.</span></span> <span data-ttu-id="f395a-140">For more information, see [Code Access Security Basics](../../../../framework/misc/code-access-security-basics.md).</span><span class="sxs-lookup"><span data-stu-id="f395a-140">For more information, see [Code Access Security Basics](../../../../framework/misc/code-access-security-basics.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f395a-141">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f395a-141">See also</span></span>

- <xref:Microsoft.VisualBasic.MyServices.RegistryProxy>
- <xref:Microsoft.VisualBasic.MyServices.RegistryProxy.CurrentUser%2A>
- <xref:Microsoft.Win32.RegistryKey.CreateSubKey%2A>
- [<span data-ttu-id="f395a-142">Čtení z registru a zápis do něj</span><span class="sxs-lookup"><span data-stu-id="f395a-142">Reading from and Writing to the Registry</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/reading-from-and-writing-to-the-registry.md)
- [<span data-ttu-id="f395a-143">Code Access Security Basics</span><span class="sxs-lookup"><span data-stu-id="f395a-143">Code Access Security Basics</span></span>](../../../../framework/misc/code-access-security-basics.md)
