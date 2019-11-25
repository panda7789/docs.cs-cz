---
title: 'Postupy: Načtení hodnoty z klíče registru'
ms.date: 07/20/2015
helpviewer_keywords:
- registry keys [Visual Basic], determining if a value exists in
- My.Computer.Registry object, examples
- registry [Visual Basic], determining if values exist
- registry keys [Visual Basic], reading from
- registry [Visual Basic], reading
ms.assetid: 775d0a57-68c9-464e-8949-9a39bd29cc64
ms.openlocfilehash: 73c32aefe06a68bb42fcb5f4615da0927e57e892
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345605"
---
# <a name="how-to-read-a-value-from-a-registry-key-in-visual-basic"></a><span data-ttu-id="0cdd5-102">Postupy: Načtení hodnoty z klíče registru v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="0cdd5-102">How to: Read a Value from a Registry Key in Visual Basic</span></span>

<span data-ttu-id="0cdd5-103">The `GetValue` method of the `My.Computer.Registry` object can be used to read values in the Windows registry.</span><span class="sxs-lookup"><span data-stu-id="0cdd5-103">The `GetValue` method of the `My.Computer.Registry` object can be used to read values in the Windows registry.</span></span>  
  
 <span data-ttu-id="0cdd5-104">If the key, "Software\MyApp" in the following example, does not exist, an exception is thrown.</span><span class="sxs-lookup"><span data-stu-id="0cdd5-104">If the key, "Software\MyApp" in the following example, does not exist, an exception is thrown.</span></span> <span data-ttu-id="0cdd5-105">If the `ValueName`,  "Name" in the following example, does not exist, `Nothing` is returned.</span><span class="sxs-lookup"><span data-stu-id="0cdd5-105">If the `ValueName`,  "Name" in the following example, does not exist, `Nothing` is returned.</span></span>  
  
 <span data-ttu-id="0cdd5-106">The `GetValue` method can also be used to determine whether a given value exists in a specific registry key.</span><span class="sxs-lookup"><span data-stu-id="0cdd5-106">The `GetValue` method can also be used to determine whether a given value exists in a specific registry key.</span></span>  
  
 <span data-ttu-id="0cdd5-107">When code reads the registry from a Web application, the current user is determined by the authentication and impersonation that is implemented in the Web application.</span><span class="sxs-lookup"><span data-stu-id="0cdd5-107">When code reads the registry from a Web application, the current user is determined by the authentication and impersonation that is implemented in the Web application.</span></span>  
  
### <a name="to-read-a-value-from-a-registry-key"></a><span data-ttu-id="0cdd5-108">To read a value from a registry key</span><span class="sxs-lookup"><span data-stu-id="0cdd5-108">To read a value from a registry key</span></span>  
  
- <span data-ttu-id="0cdd5-109">Use the `GetValue` method, specifying the path and name) to read a value from registry key.</span><span class="sxs-lookup"><span data-stu-id="0cdd5-109">Use the `GetValue` method, specifying the path and name) to read a value from registry key.</span></span> <span data-ttu-id="0cdd5-110">The following example reads the value `Name` from `HKEY_CURRENT_USER\Software\MyApp` and displays it in a message box.</span><span class="sxs-lookup"><span data-stu-id="0cdd5-110">The following example reads the value `Name` from `HKEY_CURRENT_USER\Software\MyApp` and displays it in a message box.</span></span>  
  
     [!code-vb[VbResourceTasks#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#4)]  
  
 <span data-ttu-id="0cdd5-111">This code example is also available as an IntelliSense code snippet.</span><span class="sxs-lookup"><span data-stu-id="0cdd5-111">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="0cdd5-112">In the code snippet picker, it is located in **Windows Operating System > Registry**.</span><span class="sxs-lookup"><span data-stu-id="0cdd5-112">In the code snippet picker, it is located in **Windows Operating System > Registry**.</span></span> <span data-ttu-id="0cdd5-113">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span><span class="sxs-lookup"><span data-stu-id="0cdd5-113">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
### <a name="to-determine-whether-a-value-exists-in-a-registry-key"></a><span data-ttu-id="0cdd5-114">To determine whether a value exists in a registry key</span><span class="sxs-lookup"><span data-stu-id="0cdd5-114">To determine whether a value exists in a registry key</span></span>  
  
- <span data-ttu-id="0cdd5-115">Use the `GetValue` method to retrieve the value.</span><span class="sxs-lookup"><span data-stu-id="0cdd5-115">Use the `GetValue` method to retrieve the value.</span></span> <span data-ttu-id="0cdd5-116">The following code checks whether the value exists and returns a message if it does not.</span><span class="sxs-lookup"><span data-stu-id="0cdd5-116">The following code checks whether the value exists and returns a message if it does not.</span></span>  
  
     [!code-vb[VbResourceTasks#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#12)]  
  
## <a name="robust-programming"></a><span data-ttu-id="0cdd5-117">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="0cdd5-117">Robust Programming</span></span>  

 <span data-ttu-id="0cdd5-118">The registry holds top-level, or root, keys that are used to store data.</span><span class="sxs-lookup"><span data-stu-id="0cdd5-118">The registry holds top-level, or root, keys that are used to store data.</span></span> <span data-ttu-id="0cdd5-119">For instance, the HKEY_LOCAL_MACHINE root key is used for storing machine-level settings used by all users, while HKEY_CURRENT_USER is used for storing data specific to an individual user.</span><span class="sxs-lookup"><span data-stu-id="0cdd5-119">For instance, the HKEY_LOCAL_MACHINE root key is used for storing machine-level settings used by all users, while HKEY_CURRENT_USER is used for storing data specific to an individual user.</span></span>  
  
 <span data-ttu-id="0cdd5-120">Následující podmínky mohou způsobit výjimku:</span><span class="sxs-lookup"><span data-stu-id="0cdd5-120">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="0cdd5-121">The name of the key is `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="0cdd5-121">The name of the key is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
- <span data-ttu-id="0cdd5-122">The user does not have permissions to read from registry keys (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="0cdd5-122">The user does not have permissions to read from registry keys (<xref:System.Security.SecurityException>).</span></span>  
  
- <span data-ttu-id="0cdd5-123">The key name exceeds the 255-character limit (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="0cdd5-123">The key name exceeds the 255-character limit (<xref:System.ArgumentException>).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="0cdd5-124">Zabezpečení rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="0cdd5-124">.NET Framework Security</span></span>  

 <span data-ttu-id="0cdd5-125">To run this process, your assembly requires a privilege level granted by the <xref:System.Security.Permissions.RegistryPermission> class.</span><span class="sxs-lookup"><span data-stu-id="0cdd5-125">To run this process, your assembly requires a privilege level granted by the <xref:System.Security.Permissions.RegistryPermission> class.</span></span> <span data-ttu-id="0cdd5-126">If you are running in a partial-trust context, the process might throw an exception due to insufficient privileges.</span><span class="sxs-lookup"><span data-stu-id="0cdd5-126">If you are running in a partial-trust context, the process might throw an exception due to insufficient privileges.</span></span> <span data-ttu-id="0cdd5-127">Similarly, the user must have the correct ACLs for creating or writing to settings.</span><span class="sxs-lookup"><span data-stu-id="0cdd5-127">Similarly, the user must have the correct ACLs for creating or writing to settings.</span></span> <span data-ttu-id="0cdd5-128">For example, a local application that has the code access security permission might not have operating system permission.</span><span class="sxs-lookup"><span data-stu-id="0cdd5-128">For example, a local application that has the code access security permission might not have operating system permission.</span></span> <span data-ttu-id="0cdd5-129">For more information, see [Code Access Security Basics](../../../../framework/misc/code-access-security-basics.md).</span><span class="sxs-lookup"><span data-stu-id="0cdd5-129">For more information, see [Code Access Security Basics](../../../../framework/misc/code-access-security-basics.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0cdd5-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0cdd5-130">See also</span></span>

- <xref:Microsoft.VisualBasic.MyServices.RegistryProxy>
- <xref:Microsoft.Win32.RegistryHive>
- [<span data-ttu-id="0cdd5-131">Čtení z registru a zápis do něj</span><span class="sxs-lookup"><span data-stu-id="0cdd5-131">Reading from and Writing to the Registry</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/reading-from-and-writing-to-the-registry.md)
