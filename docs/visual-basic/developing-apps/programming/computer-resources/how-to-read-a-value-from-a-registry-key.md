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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "74345605"
---
# <a name="how-to-read-a-value-from-a-registry-key-in-visual-basic"></a><span data-ttu-id="07745-102">Postupy: Načtení hodnoty z klíče registru v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="07745-102">How to: Read a Value from a Registry Key in Visual Basic</span></span>

<span data-ttu-id="07745-103">`GetValue` Metodu `My.Computer.Registry` objektu lze použít ke čtení hodnot v registru systému Windows.</span><span class="sxs-lookup"><span data-stu-id="07745-103">The `GetValue` method of the `My.Computer.Registry` object can be used to read values in the Windows registry.</span></span>  
  
 <span data-ttu-id="07745-104">Pokud klíč "Software\MyApp" v následujícím příkladu neexistuje, je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="07745-104">If the key, "Software\MyApp" in the following example, does not exist, an exception is thrown.</span></span> <span data-ttu-id="07745-105">Pokud není `ValueName`, "Name" v následujícím příkladu neexistuje, `Nothing` je vrácena.</span><span class="sxs-lookup"><span data-stu-id="07745-105">If the `ValueName`,  "Name" in the following example, does not exist, `Nothing` is returned.</span></span>  
  
 <span data-ttu-id="07745-106">`GetValue` Metodu lze také použít k určení, zda daná hodnota existuje v určitém klíči registru.</span><span class="sxs-lookup"><span data-stu-id="07745-106">The `GetValue` method can also be used to determine whether a given value exists in a specific registry key.</span></span>  
  
 <span data-ttu-id="07745-107">Když kód přečte registr z webové aplikace, je aktuální uživatel určen ověřováním a zosobněním, které je implementováno ve webové aplikaci.</span><span class="sxs-lookup"><span data-stu-id="07745-107">When code reads the registry from a Web application, the current user is determined by the authentication and impersonation that is implemented in the Web application.</span></span>  
  
### <a name="to-read-a-value-from-a-registry-key"></a><span data-ttu-id="07745-108">Načtení hodnoty z klíče registru</span><span class="sxs-lookup"><span data-stu-id="07745-108">To read a value from a registry key</span></span>  
  
- <span data-ttu-id="07745-109">Použijte `GetValue` metodu, zadáním cesty a názvu) načtěte hodnotu z klíče registru.</span><span class="sxs-lookup"><span data-stu-id="07745-109">Use the `GetValue` method, specifying the path and name) to read a value from registry key.</span></span> <span data-ttu-id="07745-110">Následující příklad přečte hodnotu `Name` z `HKEY_CURRENT_USER\Software\MyApp` a zobrazí ji v okně se zprávou.</span><span class="sxs-lookup"><span data-stu-id="07745-110">The following example reads the value `Name` from `HKEY_CURRENT_USER\Software\MyApp` and displays it in a message box.</span></span>  
  
     [!code-vb[VbResourceTasks#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#4)]  
  
 <span data-ttu-id="07745-111">Tento příklad kódu je také k dispozici jako fragment kódu technologie IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="07745-111">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="07745-112">Ve výběru fragmentu kódu je umístěn v **operačním systému Windows > registru**.</span><span class="sxs-lookup"><span data-stu-id="07745-112">In the code snippet picker, it is located in **Windows Operating System > Registry**.</span></span> <span data-ttu-id="07745-113">Další informace naleznete v tématu [fragmenty kódu](/visualstudio/ide/code-snippets).</span><span class="sxs-lookup"><span data-stu-id="07745-113">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
### <a name="to-determine-whether-a-value-exists-in-a-registry-key"></a><span data-ttu-id="07745-114">Určení, jestli v klíči registru existuje hodnota</span><span class="sxs-lookup"><span data-stu-id="07745-114">To determine whether a value exists in a registry key</span></span>  
  
- <span data-ttu-id="07745-115">Použijte `GetValue` metodu pro načtení hodnoty.</span><span class="sxs-lookup"><span data-stu-id="07745-115">Use the `GetValue` method to retrieve the value.</span></span> <span data-ttu-id="07745-116">Následující kód kontroluje, zda hodnota existuje, a vrátí zprávu, pokud není.</span><span class="sxs-lookup"><span data-stu-id="07745-116">The following code checks whether the value exists and returns a message if it does not.</span></span>  
  
     [!code-vb[VbResourceTasks#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#12)]  
  
## <a name="robust-programming"></a><span data-ttu-id="07745-117">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="07745-117">Robust Programming</span></span>  

 <span data-ttu-id="07745-118">Registr obsahuje klíče nejvyšší úrovně (neboli kořenové), které se používají k ukládání dat.</span><span class="sxs-lookup"><span data-stu-id="07745-118">The registry holds top-level, or root, keys that are used to store data.</span></span> <span data-ttu-id="07745-119">Například kořenový klíč HKEY_LOCAL_MACHINE slouží k ukládání nastavení na úrovni počítače používaných všemi uživateli, zatímco HKEY_CURRENT_USER se používá k ukládání dat specifických pro jednotlivé uživatele.</span><span class="sxs-lookup"><span data-stu-id="07745-119">For instance, the HKEY_LOCAL_MACHINE root key is used for storing machine-level settings used by all users, while HKEY_CURRENT_USER is used for storing data specific to an individual user.</span></span>  
  
 <span data-ttu-id="07745-120">Následující podmínky mohou způsobit výjimku:</span><span class="sxs-lookup"><span data-stu-id="07745-120">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="07745-121">Název klíče je `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="07745-121">The name of the key is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
- <span data-ttu-id="07745-122">Uživatel nemá oprávnění ke čtení z klíčů registru (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="07745-122">The user does not have permissions to read from registry keys (<xref:System.Security.SecurityException>).</span></span>  
  
- <span data-ttu-id="07745-123">Název klíče překračuje limit 255 znaků (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="07745-123">The key name exceeds the 255-character limit (<xref:System.ArgumentException>).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="07745-124">Zabezpečení rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="07745-124">.NET Framework Security</span></span>  

 <span data-ttu-id="07745-125">Pro spuštění tohoto procesu vaše sestavení vyžaduje úroveň oprávnění udělené <xref:System.Security.Permissions.RegistryPermission> třídou.</span><span class="sxs-lookup"><span data-stu-id="07745-125">To run this process, your assembly requires a privilege level granted by the <xref:System.Security.Permissions.RegistryPermission> class.</span></span> <span data-ttu-id="07745-126">Pokud používáte v kontextu s částečným vztahem důvěryhodnosti, proces může vyvolat výjimku z důvodu nedostatečných oprávnění.</span><span class="sxs-lookup"><span data-stu-id="07745-126">If you are running in a partial-trust context, the process might throw an exception due to insufficient privileges.</span></span> <span data-ttu-id="07745-127">Podobně uživatel musí mít správné seznamy ACL pro vytvoření nebo zápis do nastavení.</span><span class="sxs-lookup"><span data-stu-id="07745-127">Similarly, the user must have the correct ACLs for creating or writing to settings.</span></span> <span data-ttu-id="07745-128">Například místní aplikace, která má oprávnění zabezpečení přístupu kódu, nemusí mít oprávnění operačního systému.</span><span class="sxs-lookup"><span data-stu-id="07745-128">For example, a local application that has the code access security permission might not have operating system permission.</span></span> <span data-ttu-id="07745-129">Další informace najdete v tématu [Základy zabezpečení přístupu ke kódu](../../../../framework/misc/code-access-security-basics.md).</span><span class="sxs-lookup"><span data-stu-id="07745-129">For more information, see [Code Access Security Basics](../../../../framework/misc/code-access-security-basics.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07745-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="07745-130">See also</span></span>

- <xref:Microsoft.VisualBasic.MyServices.RegistryProxy>
- <xref:Microsoft.Win32.RegistryHive>
- [<span data-ttu-id="07745-131">Čtení z registru a zápis do něj</span><span class="sxs-lookup"><span data-stu-id="07745-131">Reading from and Writing to the Registry</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/reading-from-and-writing-to-the-registry.md)
