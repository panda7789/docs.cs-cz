---
title: "Postupy: Vytvoření klíče registru a nastavení jeho hodnoty v jazyce Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "30"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b6e71c106592490b92cf6f2dc02e59cddb28b95d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-registry-key-and-set-its-value-in-visual-basic"></a><span data-ttu-id="296b1-102">Postupy: Vytvoření klíče registru a nastavení jeho hodnoty v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="296b1-102">How to: Create a Registry Key and Set Its Value in Visual Basic</span></span>
<span data-ttu-id="296b1-103">`CreateSubKey` Metodu `My.Computer.Registry` objekt můžete použít k vytvoření klíče registru.</span><span class="sxs-lookup"><span data-stu-id="296b1-103">The `CreateSubKey` method of the `My.Computer.Registry` object can be used to create a registry key.</span></span>  
  
## <a name="procedure"></a><span data-ttu-id="296b1-104">Postup</span><span class="sxs-lookup"><span data-stu-id="296b1-104">Procedure</span></span>  
  
#### <a name="to-create-a-registry-key"></a><span data-ttu-id="296b1-105">Vytvoření klíče registru</span><span class="sxs-lookup"><span data-stu-id="296b1-105">To create a registry key</span></span>  
  
-   <span data-ttu-id="296b1-106">Použití `CreateSubKey` metoda, zadání kterého podregistru umístíte klíč v části, jakož i název klíče.</span><span class="sxs-lookup"><span data-stu-id="296b1-106">Use the `CreateSubKey` method, specifying which hive to place the key under as well as the name of the key.</span></span> <span data-ttu-id="296b1-107">Parametr `Subkey` není malá a velká písmena.</span><span class="sxs-lookup"><span data-stu-id="296b1-107">The parameter `Subkey` is not case-sensitive.</span></span> <span data-ttu-id="296b1-108">Tento příklad vytvoří klíč registru `MyTestKey` HKEY_CURRENT_USER.</span><span class="sxs-lookup"><span data-stu-id="296b1-108">This example creates the registry key `MyTestKey` under HKEY_CURRENT_USER.</span></span>  
  
     [!code-vb[VbResourceTasks#17](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-create-a-registry-key-and-set-its-value_1.vb)]  
  
#### <a name="to-create-a-registry-key-and-set-a-value-in-it"></a><span data-ttu-id="296b1-109">Vytvořte klíč registru a nastavte hodnotu v ní</span><span class="sxs-lookup"><span data-stu-id="296b1-109">To create a registry key and set a value in it</span></span>  
  
1.  <span data-ttu-id="296b1-110">Použití `CreateSubkey` metoda, zadání kterého podregistru umístíte klíč v části, jakož i název klíče.</span><span class="sxs-lookup"><span data-stu-id="296b1-110">Use the `CreateSubkey` method, specifying which hive to place the key under as well as the name of the key.</span></span> <span data-ttu-id="296b1-111">Tento příklad vytvoří klíč registru `MyTestKey` HKEY_CURRENT_USER.</span><span class="sxs-lookup"><span data-stu-id="296b1-111">This example creates the registry key `MyTestKey` under HKEY_CURRENT_USER.</span></span>  
  
     [!code-vb[VbResourceTasks#17](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-create-a-registry-key-and-set-its-value_1.vb)]  
  
2.  <span data-ttu-id="296b1-112">Nastavte hodnotu pomocí `SetValue` metoda.</span><span class="sxs-lookup"><span data-stu-id="296b1-112">Set the value with the `SetValue` method.</span></span> <span data-ttu-id="296b1-113">Tento příklad nastaví řetězcovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="296b1-113">This example sets the string value.</span></span> <span data-ttu-id="296b1-114">"MyTestKeyValue" na "Toto je testovací hodnota".</span><span class="sxs-lookup"><span data-stu-id="296b1-114">"MyTestKeyValue" to "This is a test value".</span></span>  
  
     [!code-vb[VbResourceTasks#14](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-create-a-registry-key-and-set-its-value_2.vb)]  
  
## <a name="example"></a><span data-ttu-id="296b1-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="296b1-115">Example</span></span>  
 <span data-ttu-id="296b1-116">Tento příklad vytvoří klíč registru `MyTestKey` HKEY_CURRENT_USER a poté nastaví řetězcovou hodnotu `MyTestKeyValue` k `This is a test value`.</span><span class="sxs-lookup"><span data-stu-id="296b1-116">This example creates the registry key `MyTestKey` under HKEY_CURRENT_USER and then sets the string value `MyTestKeyValue` to `This is a test value`.</span></span>  
  
 [!code-vb[VbResourceTasks#15](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-create-a-registry-key-and-set-its-value_3.vb)]  
  
## <a name="robust-programming"></a><span data-ttu-id="296b1-117">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="296b1-117">Robust Programming</span></span>  
 <span data-ttu-id="296b1-118">Zkontrolujte strukturu registru se najít vhodného místa pro váš klíč.</span><span class="sxs-lookup"><span data-stu-id="296b1-118">Examine the registry structure to find a suitable location for your key.</span></span> <span data-ttu-id="296b1-119">Například můžete chtít otevřít klíč HKEY_CURRENT_USER\Software aktuálního uživatele a vytvořte klíč s názvem vaší společnosti.</span><span class="sxs-lookup"><span data-stu-id="296b1-119">For example, you may want to open the HKEY_CURRENT_USER\Software key of the current user, and create a key with your company's name.</span></span> <span data-ttu-id="296b1-120">Přidejte do vaší společnosti klíč hodnoty registru.</span><span class="sxs-lookup"><span data-stu-id="296b1-120">Then add the registry values to your company's key.</span></span>  
  
 <span data-ttu-id="296b1-121">Při čtení registru z webové aplikace, je aktuální uživatel závisí na ověřování a zosobnění implementována ve webové aplikaci.</span><span class="sxs-lookup"><span data-stu-id="296b1-121">When reading the registry from a Web application, the current user depends on the authentication and impersonation implemented in the Web application.</span></span>  
  
 <span data-ttu-id="296b1-122">Je bezpečnější zapsat data do složky uživatele (<xref:Microsoft.Win32.Registry.CurrentUser>) a nikoli k místnímu počítači (<xref:Microsoft.Win32.Registry.LocalMachine>).</span><span class="sxs-lookup"><span data-stu-id="296b1-122">It is more secure to write data to the user folder (<xref:Microsoft.Win32.Registry.CurrentUser>) rather than to the local computer (<xref:Microsoft.Win32.Registry.LocalMachine>).</span></span>  
  
 <span data-ttu-id="296b1-123">Když vytvoříte hodnotu registru, budete muset rozhodnout, co dělat v případě, že hodnota již existuje.</span><span class="sxs-lookup"><span data-stu-id="296b1-123">When you create a registry value, you need to decide what to do if that value already exists.</span></span> <span data-ttu-id="296b1-124">Jiný proces, případně škodlivý jeden už možná máte vytvořené hodnota a mít přístup k němu.</span><span class="sxs-lookup"><span data-stu-id="296b1-124">Another process, perhaps a malicious one, may have already created the value and have access to it.</span></span> <span data-ttu-id="296b1-125">Když vložíte dat v hodnotě registru, data jsou k dispozici pro jiný proces.</span><span class="sxs-lookup"><span data-stu-id="296b1-125">When you put data in the registry value, the data is available to the other process.</span></span> <span data-ttu-id="296b1-126">Chcete-li tomu zabránit, použijte <xref:Microsoft.Win32.RegistryKey.GetValue%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="296b1-126">To prevent this, use the <xref:Microsoft.Win32.RegistryKey.GetValue%2A> method.</span></span> <span data-ttu-id="296b1-127">Vrátí `Nothing` Pokud klíč ještě neexistuje.</span><span class="sxs-lookup"><span data-stu-id="296b1-127">It returns `Nothing` if the key does not already exist.</span></span>  
  
 <span data-ttu-id="296b1-128">Není bezpečné uchovávat tajné údaje, jako jsou hesla, v registru jako prostý text, i v případě, že je klíč registru chráněn pomocí seznamů řízení přístupu (ACL).</span><span class="sxs-lookup"><span data-stu-id="296b1-128">It is not secure to store secrets, such as passwords, in the registry as plain text, even if the registry key is protected by ACLs (Access Control Lists).</span></span>  
  
 <span data-ttu-id="296b1-129">Následující podmínky mohou způsobit výjimku:</span><span class="sxs-lookup"><span data-stu-id="296b1-129">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="296b1-130">Název klíče je `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="296b1-130">The name of the key is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
-   <span data-ttu-id="296b1-131">Uživatel nemá oprávnění k vytvoření klíče registru (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="296b1-131">The user does not have permissions to create registry keys (<xref:System.Security.SecurityException>).</span></span>  
  
-   <span data-ttu-id="296b1-132">Název klíče překračuje limit 255 znaků (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="296b1-132">The key name exceeds the 255-character limit (<xref:System.ArgumentException>).</span></span>  
  
-   <span data-ttu-id="296b1-133">Klíč je uzavřen (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="296b1-133">The key is closed (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="296b1-134">Klíč registru je jen pro čtení (<xref:System.UnauthorizedAccessException>).</span><span class="sxs-lookup"><span data-stu-id="296b1-134">The registry key is read-only (<xref:System.UnauthorizedAccessException>).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="296b1-135">Zabezpečení rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="296b1-135">.NET Framework Security</span></span>  
 <span data-ttu-id="296b1-136">Pokud chcete spustit tento proces, vaše sestavení vyžaduje úroveň oprávnění udělenou <xref:System.Security.Permissions.RegistryPermission> třídy.</span><span class="sxs-lookup"><span data-stu-id="296b1-136">To run this process, your assembly requires a privilege level granted by the <xref:System.Security.Permissions.RegistryPermission> class.</span></span> <span data-ttu-id="296b1-137">Pokud používáte v kontextu částečným vztahem důvěryhodnosti, proces může vyvolat výjimku z důvodu nedostatečných oprávnění.</span><span class="sxs-lookup"><span data-stu-id="296b1-137">If you are running in a partial-trust context, the process might throw an exception due to insufficient privileges.</span></span> <span data-ttu-id="296b1-138">Podobně uživatel musí mít správné seznamy řízení přístupu pro vytvoření nebo zápis k nastavení.</span><span class="sxs-lookup"><span data-stu-id="296b1-138">Similarly, the user must have the correct ACLs for creating or writing to settings.</span></span> <span data-ttu-id="296b1-139">Například místní aplikace, který má oprávnění zabezpečení přístupu kódu, nemusí mít oprávnění operačního systému.</span><span class="sxs-lookup"><span data-stu-id="296b1-139">For example, a local application that has the code access security permission might not have operating system permission.</span></span> <span data-ttu-id="296b1-140">Další informace najdete v tématu [Základy zabezpečení přístupu kódu](https://msdn.microsoft.com/library/33tceax8).</span><span class="sxs-lookup"><span data-stu-id="296b1-140">For more information, see [Code Access Security Basics](https://msdn.microsoft.com/library/33tceax8).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="296b1-141">Viz také</span><span class="sxs-lookup"><span data-stu-id="296b1-141">See Also</span></span>  
 <xref:Microsoft.VisualBasic.MyServices.RegistryProxy>  
 <xref:Microsoft.VisualBasic.MyServices.RegistryProxy.CurrentUser%2A>  
 <xref:Microsoft.Win32.RegistryKey.CreateSubKey%2A>  
 [<span data-ttu-id="296b1-142">Čtení a zápis do registru</span><span class="sxs-lookup"><span data-stu-id="296b1-142">Reading from and Writing to the Registry</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/reading-from-and-writing-to-the-registry.md)  
 [<span data-ttu-id="296b1-143">Základy zabezpečení přístupu kódu</span><span class="sxs-lookup"><span data-stu-id="296b1-143">Code Access Security Basics</span></span>](https://msdn.microsoft.com/library/33tceax8)
