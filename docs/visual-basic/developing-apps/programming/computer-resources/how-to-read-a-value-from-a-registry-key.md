---
title: "Postupy: Načtení hodnoty z klíče registru v jazyce Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- registry keys [Visual Basic], determining if a value exists in
- My.Computer.Registry object, examples
- registry [Visual Basic], determining if values exist
- registry keys [Visual Basic], reading from
- registry [Visual Basic], reading
ms.assetid: 775d0a57-68c9-464e-8949-9a39bd29cc64
caps.latest.revision: "31"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4aa939d7b2d89bd878705ac67f2b6f37838f6ea2
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-read-a-value-from-a-registry-key-in-visual-basic"></a><span data-ttu-id="914e9-102">Postupy: Načtení hodnoty z klíče registru v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="914e9-102">How to: Read a Value from a Registry Key in Visual Basic</span></span>
<span data-ttu-id="914e9-103">`GetValue` Metodu `My.Computer.Registry` objekt můžete použít ke čtení hodnoty v registru systému Windows.</span><span class="sxs-lookup"><span data-stu-id="914e9-103">The `GetValue` method of the `My.Computer.Registry` object can be used to read values in the Windows registry.</span></span>  
  
 <span data-ttu-id="914e9-104">Pokud není k dispozici klíč, "Software\MyApp" v následujícím příkladu, je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="914e9-104">If the key, "Software\MyApp" in the following example, does not exist, an exception is thrown.</span></span> <span data-ttu-id="914e9-105">Pokud `ValueName`, "Název" v následujícím příkladu neexistuje, `Nothing` je vrácen.</span><span class="sxs-lookup"><span data-stu-id="914e9-105">If the `ValueName`,  "Name" in the following example, does not exist, `Nothing` is returned.</span></span>  
  
 <span data-ttu-id="914e9-106">`GetValue` Metoda slouží také k určení, zda daná hodnota existuje v klíči registru.</span><span class="sxs-lookup"><span data-stu-id="914e9-106">The `GetValue` method can also be used to determine whether a given value exists in a specific registry key.</span></span>  
  
 <span data-ttu-id="914e9-107">Když kód čte registru z webové aplikace, je aktuální uživatel je dáno ověřování a zosobnění, která je implementována ve webové aplikaci.</span><span class="sxs-lookup"><span data-stu-id="914e9-107">When code reads the registry from a Web application, the current user is determined by the authentication and impersonation that is implemented in the Web application.</span></span>  
  
### <a name="to-read-a-value-from-a-registry-key"></a><span data-ttu-id="914e9-108">K načtení hodnoty z klíče registru</span><span class="sxs-lookup"><span data-stu-id="914e9-108">To read a value from a registry key</span></span>  
  
-   <span data-ttu-id="914e9-109">Použít `GetValue` metoda, zadáte cestu a název) k načtení hodnoty z klíče registru.</span><span class="sxs-lookup"><span data-stu-id="914e9-109">Use the `GetValue` method, specifying the path and name) to read a value from registry key.</span></span> <span data-ttu-id="914e9-110">Následující příklad načte hodnotu `Name` z `HKEY_CURRENT_USER\Software\MyApp` a zobrazí v okně se zprávou.</span><span class="sxs-lookup"><span data-stu-id="914e9-110">The following example reads the value `Name` from `HKEY_CURRENT_USER\Software\MyApp` and displays it in a message box.</span></span>  
  
     [!code-vb[VbResourceTasks#4](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-read-a-value-from-a-registry-key_1.vb)]  
  
 <span data-ttu-id="914e9-111">Tento příklad kódu je také k dispozici jako IntelliSense fragment kódu.</span><span class="sxs-lookup"><span data-stu-id="914e9-111">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="914e9-112">V Sběrač fragmentů kódu je umístěn v **operačního systému Windows > registru**.</span><span class="sxs-lookup"><span data-stu-id="914e9-112">In the code snippet picker, it is located in **Windows Operating System > Registry**.</span></span> <span data-ttu-id="914e9-113">Další informace najdete v tématu [fragmenty kódu](/visualstudio/ide/code-snippets).</span><span class="sxs-lookup"><span data-stu-id="914e9-113">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
### <a name="to-determine-whether-a-value-exists-in-a-registry-key"></a><span data-ttu-id="914e9-114">K určení, zda hodnota existuje v klíči registru</span><span class="sxs-lookup"><span data-stu-id="914e9-114">To determine whether a value exists in a registry key</span></span>  
  
-   <span data-ttu-id="914e9-115">Použití `GetValue` metodu k získání hodnoty.</span><span class="sxs-lookup"><span data-stu-id="914e9-115">Use the `GetValue` method to retrieve the value.</span></span> <span data-ttu-id="914e9-116">Následující kód ověří, zda hodnota existuje a vrátí zprávu, pokud neexistuje.</span><span class="sxs-lookup"><span data-stu-id="914e9-116">The following code checks whether the value exists and returns a message if it does not.</span></span>  
  
     [!code-vb[VbResourceTasks#12](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-read-a-value-from-a-registry-key_2.vb)]  
  
## <a name="robust-programming"></a><span data-ttu-id="914e9-117">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="914e9-117">Robust Programming</span></span>  
 <span data-ttu-id="914e9-118">Registr obsahuje nejvyšší úrovně nebo kořenové klíče, které se používají k ukládání dat.</span><span class="sxs-lookup"><span data-stu-id="914e9-118">The registry holds top-level, or root, keys that are used to store data.</span></span> <span data-ttu-id="914e9-119">Například HKEY_LOCAL_MACHINE kořenový klíč se používá pro ukládání nastavení používané všechny uživatele, i když HKEY_CURRENT_USER se používá pro ukládání dat, které jsou specifické pro jednotlivé uživatele.</span><span class="sxs-lookup"><span data-stu-id="914e9-119">For instance, the HKEY_LOCAL_MACHINE root key is used for storing machine-level settings used by all users, while HKEY_CURRENT_USER is used for storing data specific to an individual user.</span></span>  
  
 <span data-ttu-id="914e9-120">Následující podmínky mohou způsobit výjimku:</span><span class="sxs-lookup"><span data-stu-id="914e9-120">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="914e9-121">Název klíče je `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="914e9-121">The name of the key is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
-   <span data-ttu-id="914e9-122">Uživatel nemá oprávnění ke čtení z klíče registru (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="914e9-122">The user does not have permissions to read from registry keys (<xref:System.Security.SecurityException>).</span></span>  
  
-   <span data-ttu-id="914e9-123">Název klíče překračuje limit 255 znaků (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="914e9-123">The key name exceeds the 255-character limit (<xref:System.ArgumentException>).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="914e9-124">Zabezpečení rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="914e9-124">.NET Framework Security</span></span>  
 <span data-ttu-id="914e9-125">Pokud chcete spustit tento proces, vaše sestavení vyžaduje úroveň oprávnění udělenou <xref:System.Security.Permissions.RegistryPermission> třídy.</span><span class="sxs-lookup"><span data-stu-id="914e9-125">To run this process, your assembly requires a privilege level granted by the <xref:System.Security.Permissions.RegistryPermission> class.</span></span> <span data-ttu-id="914e9-126">Pokud používáte v kontextu částečným vztahem důvěryhodnosti, proces může vyvolat výjimku z důvodu nedostatečných oprávnění.</span><span class="sxs-lookup"><span data-stu-id="914e9-126">If you are running in a partial-trust context, the process might throw an exception due to insufficient privileges.</span></span> <span data-ttu-id="914e9-127">Podobně uživatel musí mít správné seznamy řízení přístupu pro vytvoření nebo zápis k nastavení.</span><span class="sxs-lookup"><span data-stu-id="914e9-127">Similarly, the user must have the correct ACLs for creating or writing to settings.</span></span> <span data-ttu-id="914e9-128">Například místní aplikace, který má oprávnění zabezpečení přístupu kódu, nemusí mít oprávnění operačního systému.</span><span class="sxs-lookup"><span data-stu-id="914e9-128">For example, a local application that has the code access security permission might not have operating system permission.</span></span> <span data-ttu-id="914e9-129">Další informace najdete v tématu [Základy zabezpečení přístupu kódu](../../../../framework/misc/code-access-security-basics.md).</span><span class="sxs-lookup"><span data-stu-id="914e9-129">For more information, see [Code Access Security Basics](../../../../framework/misc/code-access-security-basics.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="914e9-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="914e9-130">See Also</span></span>  
 <xref:Microsoft.VisualBasic.MyServices.RegistryProxy>  
 <xref:Microsoft.Win32.RegistryHive>  
 [<span data-ttu-id="914e9-131">Čtení z registru a zápis do něj</span><span class="sxs-lookup"><span data-stu-id="914e9-131">Reading from and Writing to the Registry</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/reading-from-and-writing-to-the-registry.md)
