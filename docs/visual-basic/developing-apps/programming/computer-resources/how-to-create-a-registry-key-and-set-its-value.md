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
# <a name="how-to-create-a-registry-key-and-set-its-value-in-visual-basic"></a><span data-ttu-id="96f37-102">Postupy: Vytvoření klíče registru a nastavení jeho hodnoty v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="96f37-102">How to: Create a Registry Key and Set Its Value in Visual Basic</span></span>

<span data-ttu-id="96f37-103">Metodu `CreateSubKey` objektu `My.Computer.Registry` lze použít k vytvoření klíče registru.</span><span class="sxs-lookup"><span data-stu-id="96f37-103">The `CreateSubKey` method of the `My.Computer.Registry` object can be used to create a registry key.</span></span>

## <a name="procedure"></a><span data-ttu-id="96f37-104">Postup</span><span class="sxs-lookup"><span data-stu-id="96f37-104">Procedure</span></span>

### <a name="to-create-a-registry-key"></a><span data-ttu-id="96f37-105">Vytvoření klíče registru</span><span class="sxs-lookup"><span data-stu-id="96f37-105">To create a registry key</span></span>

- <span data-ttu-id="96f37-106">Použijte `CreateSubKey` metodu určující, podapod pod který podají klíč, a také název klíče.</span><span class="sxs-lookup"><span data-stu-id="96f37-106">Use the `CreateSubKey` method, specifying which hive to place the key under as well as the name of the key.</span></span> <span data-ttu-id="96f37-107">Parametr `Subkey` není rozlišována malá a velká písmena.</span><span class="sxs-lookup"><span data-stu-id="96f37-107">The parameter `Subkey` is not case-sensitive.</span></span> <span data-ttu-id="96f37-108">Tento příklad vytvoří `MyTestKey` klíč registru v části HKEY_CURRENT_USER.</span><span class="sxs-lookup"><span data-stu-id="96f37-108">This example creates the registry key `MyTestKey` under HKEY_CURRENT_USER.</span></span>

    [!code-vb[VbResourceTasks#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#17)]

### <a name="to-create-a-registry-key-and-set-a-value-in-it"></a><span data-ttu-id="96f37-109">Vytvoření klíče registru a nastavení hodnoty v něm</span><span class="sxs-lookup"><span data-stu-id="96f37-109">To create a registry key and set a value in it</span></span>

1. <span data-ttu-id="96f37-110">Použijte `CreateSubkey` metodu určující, podapod pod který podají klíč, a také název klíče.</span><span class="sxs-lookup"><span data-stu-id="96f37-110">Use the `CreateSubkey` method, specifying which hive to place the key under as well as the name of the key.</span></span> <span data-ttu-id="96f37-111">Tento příklad vytvoří `MyTestKey` klíč registru v části HKEY_CURRENT_USER.</span><span class="sxs-lookup"><span data-stu-id="96f37-111">This example creates the registry key `MyTestKey` under HKEY_CURRENT_USER.</span></span>

    [!code-vb[VbResourceTasks#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#17)]

2. <span data-ttu-id="96f37-112">Nastavte hodnotu `SetValue` pomocí metody.</span><span class="sxs-lookup"><span data-stu-id="96f37-112">Set the value with the `SetValue` method.</span></span> <span data-ttu-id="96f37-113">Tento příklad nastaví hodnotu řetězce.</span><span class="sxs-lookup"><span data-stu-id="96f37-113">This example sets the string value.</span></span> <span data-ttu-id="96f37-114">"MyTestKeyValue" na "Toto je testovací hodnota".</span><span class="sxs-lookup"><span data-stu-id="96f37-114">"MyTestKeyValue" to "This is a test value".</span></span>

    [!code-vb[VbResourceTasks#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#14)]

## <a name="example"></a><span data-ttu-id="96f37-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="96f37-115">Example</span></span>

<span data-ttu-id="96f37-116">Tento příklad vytvoří `MyTestKey` klíč registru pod HKEY_CURRENT_USER `MyTestKeyValue` a `This is a test value`potom nastaví hodnotu řetězce na .</span><span class="sxs-lookup"><span data-stu-id="96f37-116">This example creates the registry key `MyTestKey` under HKEY_CURRENT_USER and then sets the string value `MyTestKeyValue` to `This is a test value`.</span></span>

[!code-vb[VbResourceTasks#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#15)]

## <a name="robust-programming"></a><span data-ttu-id="96f37-117">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="96f37-117">Robust Programming</span></span>

<span data-ttu-id="96f37-118">Zkontrolujte strukturu registru najít vhodné umístění pro váš klíč.</span><span class="sxs-lookup"><span data-stu-id="96f37-118">Examine the registry structure to find a suitable location for your key.</span></span> <span data-ttu-id="96f37-119">Můžete například otevřít klíč HKEY_CURRENT_USER\Software aktuálního uživatele a vytvořit klíč s názvem vaší společnosti.</span><span class="sxs-lookup"><span data-stu-id="96f37-119">For example, you may want to open the HKEY_CURRENT_USER\Software key of the current user, and create a key with your company's name.</span></span> <span data-ttu-id="96f37-120">Pak přidejte hodnoty registru do klíče vaší společnosti.</span><span class="sxs-lookup"><span data-stu-id="96f37-120">Then add the registry values to your company's key.</span></span>

<span data-ttu-id="96f37-121">Při čtení registru z webové aplikace závisí aktuální uživatel na ověřování a zosobnění implementovaném ve webové aplikaci.</span><span class="sxs-lookup"><span data-stu-id="96f37-121">When reading the registry from a Web application, the current user depends on the authentication and impersonation implemented in the Web application.</span></span>

<span data-ttu-id="96f37-122">Je bezpečnější zapisovat data do<xref:Microsoft.Win32.Registry.CurrentUser>uživatelské složky (<xref:Microsoft.Win32.Registry.LocalMachine>) spíše než do místního počítače ( ).</span><span class="sxs-lookup"><span data-stu-id="96f37-122">It is more secure to write data to the user folder (<xref:Microsoft.Win32.Registry.CurrentUser>) rather than to the local computer (<xref:Microsoft.Win32.Registry.LocalMachine>).</span></span>

<span data-ttu-id="96f37-123">Při vytváření hodnoty registru se musíte rozhodnout, co dělat, pokud tato hodnota již existuje.</span><span class="sxs-lookup"><span data-stu-id="96f37-123">When you create a registry value, you need to decide what to do if that value already exists.</span></span> <span data-ttu-id="96f37-124">Jiný proces, možná škodlivý, může mít již vytvořilhodnotu a mají k ní přístup.</span><span class="sxs-lookup"><span data-stu-id="96f37-124">Another process, perhaps a malicious one, may have already created the value and have access to it.</span></span> <span data-ttu-id="96f37-125">Když vložíte data do hodnoty registru, data jsou k dispozici pro jiný proces.</span><span class="sxs-lookup"><span data-stu-id="96f37-125">When you put data in the registry value, the data is available to the other process.</span></span> <span data-ttu-id="96f37-126">Chcete-li tomu <xref:Microsoft.Win32.RegistryKey.GetValue%2A> zabránit, použijte metodu.</span><span class="sxs-lookup"><span data-stu-id="96f37-126">To prevent this, use the <xref:Microsoft.Win32.RegistryKey.GetValue%2A> method.</span></span> <span data-ttu-id="96f37-127">Vrátí, `Nothing` pokud klíč ještě neexistuje.</span><span class="sxs-lookup"><span data-stu-id="96f37-127">It returns `Nothing` if the key does not already exist.</span></span>

<span data-ttu-id="96f37-128">Není bezpečné ukládat tajné klíče, například hesla, do registru jako prostý text, a to i v případě, že klíč registru je chráněn seznamy ACL (seznamy řízení přístupu).</span><span class="sxs-lookup"><span data-stu-id="96f37-128">It is not secure to store secrets, such as passwords, in the registry as plain text, even if the registry key is protected by ACLs (Access Control Lists).</span></span>

<span data-ttu-id="96f37-129">Následující podmínky mohou způsobit výjimku:</span><span class="sxs-lookup"><span data-stu-id="96f37-129">The following conditions may cause an exception:</span></span>

- <span data-ttu-id="96f37-130">Název klíče je `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="96f37-130">The name of the key is `Nothing` (<xref:System.ArgumentNullException>).</span></span>

- <span data-ttu-id="96f37-131">Uživatel nemá oprávnění k vytváření klíčů<xref:System.Security.SecurityException>registru ( ).</span><span class="sxs-lookup"><span data-stu-id="96f37-131">The user does not have permissions to create registry keys (<xref:System.Security.SecurityException>).</span></span>

- <span data-ttu-id="96f37-132">Název klíče překračuje limit 255 znaků<xref:System.ArgumentException>( ).</span><span class="sxs-lookup"><span data-stu-id="96f37-132">The key name exceeds the 255-character limit (<xref:System.ArgumentException>).</span></span>

- <span data-ttu-id="96f37-133">Klíč je zavřený<xref:System.IO.IOException>( ).</span><span class="sxs-lookup"><span data-stu-id="96f37-133">The key is closed (<xref:System.IO.IOException>).</span></span>

- <span data-ttu-id="96f37-134">Klíč registru je jen<xref:System.UnauthorizedAccessException>pro čtení ( ).</span><span class="sxs-lookup"><span data-stu-id="96f37-134">The registry key is read-only (<xref:System.UnauthorizedAccessException>).</span></span>

## <a name="net-framework-security"></a><span data-ttu-id="96f37-135">Zabezpečení rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="96f37-135">.NET Framework Security</span></span>

<span data-ttu-id="96f37-136">Chcete-li spustit tento proces, vaše sestavení <xref:System.Security.Permissions.RegistryPermission> vyžaduje úroveň oprávnění udělené třídou.</span><span class="sxs-lookup"><span data-stu-id="96f37-136">To run this process, your assembly requires a privilege level granted by the <xref:System.Security.Permissions.RegistryPermission> class.</span></span> <span data-ttu-id="96f37-137">Pokud jsou spuštěny v kontextu částečné důvěryhodnosti, proces může vyvolat výjimku z důvodu nedostatečných oprávnění.</span><span class="sxs-lookup"><span data-stu-id="96f37-137">If you are running in a partial-trust context, the process might throw an exception due to insufficient privileges.</span></span> <span data-ttu-id="96f37-138">Podobně musí mít uživatel správné akly pro vytváření nebo zápis do nastavení.</span><span class="sxs-lookup"><span data-stu-id="96f37-138">Similarly, the user must have the correct ACLs for creating or writing to settings.</span></span> <span data-ttu-id="96f37-139">Například místní aplikace, která má oprávnění zabezpečení přístupu kódu, nemusí mít oprávnění operačního systému.</span><span class="sxs-lookup"><span data-stu-id="96f37-139">For example, a local application that has the code access security permission might not have operating system permission.</span></span> <span data-ttu-id="96f37-140">Další informace naleznete v [tématu Základy zabezpečení přístupu kódu](../../../../framework/misc/code-access-security-basics.md).</span><span class="sxs-lookup"><span data-stu-id="96f37-140">For more information, see [Code Access Security Basics](../../../../framework/misc/code-access-security-basics.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="96f37-141">Viz také</span><span class="sxs-lookup"><span data-stu-id="96f37-141">See also</span></span>

- <xref:Microsoft.VisualBasic.MyServices.RegistryProxy>
- <xref:Microsoft.VisualBasic.MyServices.RegistryProxy.CurrentUser%2A>
- <xref:Microsoft.Win32.RegistryKey.CreateSubKey%2A>
- [<span data-ttu-id="96f37-142">Čtení z registru a zápis do něj</span><span class="sxs-lookup"><span data-stu-id="96f37-142">Reading from and Writing to the Registry</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/reading-from-and-writing-to-the-registry.md)
- [<span data-ttu-id="96f37-143">Základy zabezpečení přístupu kódu</span><span class="sxs-lookup"><span data-stu-id="96f37-143">Code Access Security Basics</span></span>](../../../../framework/misc/code-access-security-basics.md)
