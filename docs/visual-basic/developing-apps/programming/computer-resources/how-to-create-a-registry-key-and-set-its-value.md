---
title: 'Postupy: Vytvořte klíč registru a nastavení jeho hodnoty v jazyce Visual Basic'
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
ms.openlocfilehash: 0cadff8b44c60041e2664b1d3b70830209014301
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59312607"
---
# <a name="how-to-create-a-registry-key-and-set-its-value-in-visual-basic"></a><span data-ttu-id="820b2-102">Postupy: Vytvořte klíč registru a nastavení jeho hodnoty v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="820b2-102">How to: Create a Registry Key and Set Its Value in Visual Basic</span></span>
<span data-ttu-id="820b2-103">`CreateSubKey` Metodu `My.Computer.Registry` objekt slouží k vytvoření klíče registru.</span><span class="sxs-lookup"><span data-stu-id="820b2-103">The `CreateSubKey` method of the `My.Computer.Registry` object can be used to create a registry key.</span></span>  
  
## <a name="procedure"></a><span data-ttu-id="820b2-104">Postup</span><span class="sxs-lookup"><span data-stu-id="820b2-104">Procedure</span></span>  
  
#### <a name="to-create-a-registry-key"></a><span data-ttu-id="820b2-105">Vytvoření klíče registru</span><span class="sxs-lookup"><span data-stu-id="820b2-105">To create a registry key</span></span>  
  
-   <span data-ttu-id="820b2-106">Použití `CreateSubKey` metoda, která hive umístí klíč v rámci, jakož i název klíče zadáte.</span><span class="sxs-lookup"><span data-stu-id="820b2-106">Use the `CreateSubKey` method, specifying which hive to place the key under as well as the name of the key.</span></span> <span data-ttu-id="820b2-107">Parametr `Subkey` není malá a velká písmena.</span><span class="sxs-lookup"><span data-stu-id="820b2-107">The parameter `Subkey` is not case-sensitive.</span></span> <span data-ttu-id="820b2-108">Tento příklad vytvoří klíče registru `MyTestKey` HKEY_CURRENT_USER.</span><span class="sxs-lookup"><span data-stu-id="820b2-108">This example creates the registry key `MyTestKey` under HKEY_CURRENT_USER.</span></span>  
  
     [!code-vb[VbResourceTasks#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#17)]  
  
#### <a name="to-create-a-registry-key-and-set-a-value-in-it"></a><span data-ttu-id="820b2-109">Vytvořte klíč registru a nastavit hodnotu v ní</span><span class="sxs-lookup"><span data-stu-id="820b2-109">To create a registry key and set a value in it</span></span>  
  
1. <span data-ttu-id="820b2-110">Použití `CreateSubkey` metoda, která hive umístí klíč v rámci, jakož i název klíče zadáte.</span><span class="sxs-lookup"><span data-stu-id="820b2-110">Use the `CreateSubkey` method, specifying which hive to place the key under as well as the name of the key.</span></span> <span data-ttu-id="820b2-111">Tento příklad vytvoří klíče registru `MyTestKey` HKEY_CURRENT_USER.</span><span class="sxs-lookup"><span data-stu-id="820b2-111">This example creates the registry key `MyTestKey` under HKEY_CURRENT_USER.</span></span>  
  
     [!code-vb[VbResourceTasks#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#17)]  
  
2. <span data-ttu-id="820b2-112">Nastavte hodnoty `SetValue` metody.</span><span class="sxs-lookup"><span data-stu-id="820b2-112">Set the value with the `SetValue` method.</span></span> <span data-ttu-id="820b2-113">V tomto příkladu nastaví řetězcovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="820b2-113">This example sets the string value.</span></span> <span data-ttu-id="820b2-114">"MyTestKeyValue" na "Toto je testovací hodnota".</span><span class="sxs-lookup"><span data-stu-id="820b2-114">"MyTestKeyValue" to "This is a test value".</span></span>  
  
     [!code-vb[VbResourceTasks#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#14)]  
  
## <a name="example"></a><span data-ttu-id="820b2-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="820b2-115">Example</span></span>  
 <span data-ttu-id="820b2-116">Tento příklad vytvoří klíče registru `MyTestKey` HKEY_CURRENT_USER a pak nastaví řetězcovou hodnotu `MyTestKeyValue` k `This is a test value`.</span><span class="sxs-lookup"><span data-stu-id="820b2-116">This example creates the registry key `MyTestKey` under HKEY_CURRENT_USER and then sets the string value `MyTestKeyValue` to `This is a test value`.</span></span>  
  
 [!code-vb[VbResourceTasks#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#15)]  
  
## <a name="robust-programming"></a><span data-ttu-id="820b2-117">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="820b2-117">Robust Programming</span></span>  
 <span data-ttu-id="820b2-118">Zkontrolujte strukturu registrů k vyhledání příhodného místa pro váš klíč.</span><span class="sxs-lookup"><span data-stu-id="820b2-118">Examine the registry structure to find a suitable location for your key.</span></span> <span data-ttu-id="820b2-119">Můžete například otevřít HKEY_CURRENT_USER\Software klíč aktuálního uživatele a vytvořte klíč s názvem vaší společnosti.</span><span class="sxs-lookup"><span data-stu-id="820b2-119">For example, you may want to open the HKEY_CURRENT_USER\Software key of the current user, and create a key with your company's name.</span></span> <span data-ttu-id="820b2-120">Hodnoty registru obnovte klíče vaší společnosti.</span><span class="sxs-lookup"><span data-stu-id="820b2-120">Then add the registry values to your company's key.</span></span>  
  
 <span data-ttu-id="820b2-121">Při čtení registru z webové aplikace, je aktuální uživatel závisí na ověřování a zosobnění implementované ve webové aplikaci.</span><span class="sxs-lookup"><span data-stu-id="820b2-121">When reading the registry from a Web application, the current user depends on the authentication and impersonation implemented in the Web application.</span></span>  
  
 <span data-ttu-id="820b2-122">Je bezpečnější zapsat data do složky uživatele (<xref:Microsoft.Win32.Registry.CurrentUser>), nikoli do místního počítače (<xref:Microsoft.Win32.Registry.LocalMachine>).</span><span class="sxs-lookup"><span data-stu-id="820b2-122">It is more secure to write data to the user folder (<xref:Microsoft.Win32.Registry.CurrentUser>) rather than to the local computer (<xref:Microsoft.Win32.Registry.LocalMachine>).</span></span>  
  
 <span data-ttu-id="820b2-123">Když vytváříte hodnotu registru, musíte se rozhodnout, co dělat, pokud tuto hodnotu již existuje.</span><span class="sxs-lookup"><span data-stu-id="820b2-123">When you create a registry value, you need to decide what to do if that value already exists.</span></span> <span data-ttu-id="820b2-124">Jiný proces, možná škodlivý ten už možná máte vytvořené hodnotu a k ní máte přístup.</span><span class="sxs-lookup"><span data-stu-id="820b2-124">Another process, perhaps a malicious one, may have already created the value and have access to it.</span></span> <span data-ttu-id="820b2-125">Když vkládáte data do hodnoty registru, data jsou k dispozici pro jiné procesy.</span><span class="sxs-lookup"><span data-stu-id="820b2-125">When you put data in the registry value, the data is available to the other process.</span></span> <span data-ttu-id="820b2-126">Chcete-li tomu zabránit, použijte <xref:Microsoft.Win32.RegistryKey.GetValue%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="820b2-126">To prevent this, use the <xref:Microsoft.Win32.RegistryKey.GetValue%2A> method.</span></span> <span data-ttu-id="820b2-127">Vrátí `Nothing` Pokud klíč ještě neexistuje.</span><span class="sxs-lookup"><span data-stu-id="820b2-127">It returns `Nothing` if the key does not already exist.</span></span>  
  
 <span data-ttu-id="820b2-128">Není bezpečné uchovávat tajemství, jako jsou hesla, v registrech jako prostý text, i v případě, že klíč registru je chráněn pomocí ACL (seznamy řízení přístupu).</span><span class="sxs-lookup"><span data-stu-id="820b2-128">It is not secure to store secrets, such as passwords, in the registry as plain text, even if the registry key is protected by ACLs (Access Control Lists).</span></span>  
  
 <span data-ttu-id="820b2-129">Následující podmínky mohou způsobit výjimku:</span><span class="sxs-lookup"><span data-stu-id="820b2-129">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="820b2-130">Název klíče je `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="820b2-130">The name of the key is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
-   <span data-ttu-id="820b2-131">Uživatel nemá oprávnění k vytvoření klíče registru (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="820b2-131">The user does not have permissions to create registry keys (<xref:System.Security.SecurityException>).</span></span>  
  
-   <span data-ttu-id="820b2-132">Název klíče překračuje limit 255 znaků (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="820b2-132">The key name exceeds the 255-character limit (<xref:System.ArgumentException>).</span></span>  
  
-   <span data-ttu-id="820b2-133">Klíč je uzavřen (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="820b2-133">The key is closed (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="820b2-134">Klíč registru je jen pro čtení (<xref:System.UnauthorizedAccessException>).</span><span class="sxs-lookup"><span data-stu-id="820b2-134">The registry key is read-only (<xref:System.UnauthorizedAccessException>).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="820b2-135">Zabezpečení rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="820b2-135">.NET Framework Security</span></span>  
 <span data-ttu-id="820b2-136">Pokud chcete spustit tento proces, vaše sestavení vyžaduje úroveň oprávnění udělenou <xref:System.Security.Permissions.RegistryPermission> třídy.</span><span class="sxs-lookup"><span data-stu-id="820b2-136">To run this process, your assembly requires a privilege level granted by the <xref:System.Security.Permissions.RegistryPermission> class.</span></span> <span data-ttu-id="820b2-137">Pokud používáte v kontextu částečným vztahem důvěryhodnosti, proces může vyvolat výjimku, protože nedostatečná oprávnění.</span><span class="sxs-lookup"><span data-stu-id="820b2-137">If you are running in a partial-trust context, the process might throw an exception due to insufficient privileges.</span></span> <span data-ttu-id="820b2-138">Podobně uživatel musí mít správné seznamy ACL pro vytvoření nebo zápis do nastavení.</span><span class="sxs-lookup"><span data-stu-id="820b2-138">Similarly, the user must have the correct ACLs for creating or writing to settings.</span></span> <span data-ttu-id="820b2-139">Místní aplikace, který má oprávnění zabezpečení přístupu kódu například nemusí mít oprávnění operačního systému.</span><span class="sxs-lookup"><span data-stu-id="820b2-139">For example, a local application that has the code access security permission might not have operating system permission.</span></span> <span data-ttu-id="820b2-140">Další informace najdete v tématu [Základy zabezpečení přístupu kódu](../../../../framework/misc/code-access-security-basics.md).</span><span class="sxs-lookup"><span data-stu-id="820b2-140">For more information, see [Code Access Security Basics](../../../../framework/misc/code-access-security-basics.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="820b2-141">Viz také:</span><span class="sxs-lookup"><span data-stu-id="820b2-141">See also</span></span>

- <xref:Microsoft.VisualBasic.MyServices.RegistryProxy>
- <xref:Microsoft.VisualBasic.MyServices.RegistryProxy.CurrentUser%2A>
- <xref:Microsoft.Win32.RegistryKey.CreateSubKey%2A>
- [<span data-ttu-id="820b2-142">Čtení z registru a zápis do něj</span><span class="sxs-lookup"><span data-stu-id="820b2-142">Reading from and Writing to the Registry</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/reading-from-and-writing-to-the-registry.md)
- [<span data-ttu-id="820b2-143">Základy zabezpečení přístupu kódu</span><span class="sxs-lookup"><span data-stu-id="820b2-143">Code Access Security Basics</span></span>](../../../../framework/misc/code-access-security-basics.md)
