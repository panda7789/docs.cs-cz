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
# <a name="how-to-read-a-value-from-a-registry-key-in-visual-basic"></a><span data-ttu-id="ec547-102">Postupy: Načtení hodnoty z klíče registru v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ec547-102">How to: Read a Value from a Registry Key in Visual Basic</span></span>

<span data-ttu-id="ec547-103">Metodu `GetValue` objektu `My.Computer.Registry` lze použít ke čtení hodnot v registru systému Windows.</span><span class="sxs-lookup"><span data-stu-id="ec547-103">The `GetValue` method of the `My.Computer.Registry` object can be used to read values in the Windows registry.</span></span>  
  
 <span data-ttu-id="ec547-104">Pokud klíč "Software\MyApp" v následujícím příkladu neexistuje, je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="ec547-104">If the key, "Software\MyApp" in the following example, does not exist, an exception is thrown.</span></span> <span data-ttu-id="ec547-105">Pokud `ValueName`, "Název" v následujícím příkladu `Nothing` neexistuje, je vrácena.</span><span class="sxs-lookup"><span data-stu-id="ec547-105">If the `ValueName`,  "Name" in the following example, does not exist, `Nothing` is returned.</span></span>  
  
 <span data-ttu-id="ec547-106">Metodu `GetValue` lze také použít k určení, zda daná hodnota existuje v určitém klíči registru.</span><span class="sxs-lookup"><span data-stu-id="ec547-106">The `GetValue` method can also be used to determine whether a given value exists in a specific registry key.</span></span>  
  
 <span data-ttu-id="ec547-107">Při čtení kódu z webové aplikace je aktuální uživatel určen ověřováním a zosobněním, které je implementováno ve webové aplikaci.</span><span class="sxs-lookup"><span data-stu-id="ec547-107">When code reads the registry from a Web application, the current user is determined by the authentication and impersonation that is implemented in the Web application.</span></span>  
  
### <a name="to-read-a-value-from-a-registry-key"></a><span data-ttu-id="ec547-108">Čtení hodnoty z klíče registru</span><span class="sxs-lookup"><span data-stu-id="ec547-108">To read a value from a registry key</span></span>  
  
- <span data-ttu-id="ec547-109">Pomocí `GetValue` metody určující cestu a název) přečtete hodnotu z klíče registru.</span><span class="sxs-lookup"><span data-stu-id="ec547-109">Use the `GetValue` method, specifying the path and name) to read a value from registry key.</span></span> <span data-ttu-id="ec547-110">Následující příklad přečte `Name` `HKEY_CURRENT_USER\Software\MyApp` hodnotu z a zobrazí ji v poli se zprávou.</span><span class="sxs-lookup"><span data-stu-id="ec547-110">The following example reads the value `Name` from `HKEY_CURRENT_USER\Software\MyApp` and displays it in a message box.</span></span>  
  
     [!code-vb[VbResourceTasks#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#4)]  
  
 <span data-ttu-id="ec547-111">Tento příklad kódu je také k dispozici jako fragment kódu IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="ec547-111">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="ec547-112">Ve výběru fragmentu kódu je umístěn v registru **operačního systému Windows >**.</span><span class="sxs-lookup"><span data-stu-id="ec547-112">In the code snippet picker, it is located in **Windows Operating System > Registry**.</span></span> <span data-ttu-id="ec547-113">Další informace naleznete v [tématu Fragmenty kódu](/visualstudio/ide/code-snippets).</span><span class="sxs-lookup"><span data-stu-id="ec547-113">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
### <a name="to-determine-whether-a-value-exists-in-a-registry-key"></a><span data-ttu-id="ec547-114">Chcete-li zjistit, zda hodnota existuje v klíči registru</span><span class="sxs-lookup"><span data-stu-id="ec547-114">To determine whether a value exists in a registry key</span></span>  
  
- <span data-ttu-id="ec547-115">Pomocí `GetValue` metody načtěte hodnotu.</span><span class="sxs-lookup"><span data-stu-id="ec547-115">Use the `GetValue` method to retrieve the value.</span></span> <span data-ttu-id="ec547-116">Následující kód zkontroluje, zda hodnota existuje, a vrátí zprávu, pokud tomu tak není.</span><span class="sxs-lookup"><span data-stu-id="ec547-116">The following code checks whether the value exists and returns a message if it does not.</span></span>  
  
     [!code-vb[VbResourceTasks#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#12)]  
  
## <a name="robust-programming"></a><span data-ttu-id="ec547-117">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="ec547-117">Robust Programming</span></span>  

 <span data-ttu-id="ec547-118">Registr obsahuje klíče nejvyšší úrovně nebo root, které se používají k ukládání dat.</span><span class="sxs-lookup"><span data-stu-id="ec547-118">The registry holds top-level, or root, keys that are used to store data.</span></span> <span data-ttu-id="ec547-119">Například kořenový klíč HKEY_LOCAL_MACHINE se používá pro ukládání nastavení na úrovni počítače používané všemi uživateli, zatímco HKEY_CURRENT_USER se používá pro ukládání dat specifických pro jednotlivé uživatele.</span><span class="sxs-lookup"><span data-stu-id="ec547-119">For instance, the HKEY_LOCAL_MACHINE root key is used for storing machine-level settings used by all users, while HKEY_CURRENT_USER is used for storing data specific to an individual user.</span></span>  
  
 <span data-ttu-id="ec547-120">Následující podmínky mohou způsobit výjimku:</span><span class="sxs-lookup"><span data-stu-id="ec547-120">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="ec547-121">Název klíče je `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="ec547-121">The name of the key is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
- <span data-ttu-id="ec547-122">Uživatel nemá oprávnění ke čtení z<xref:System.Security.SecurityException>klíčů registru ( ).</span><span class="sxs-lookup"><span data-stu-id="ec547-122">The user does not have permissions to read from registry keys (<xref:System.Security.SecurityException>).</span></span>  
  
- <span data-ttu-id="ec547-123">Název klíče překračuje limit 255 znaků<xref:System.ArgumentException>( ).</span><span class="sxs-lookup"><span data-stu-id="ec547-123">The key name exceeds the 255-character limit (<xref:System.ArgumentException>).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="ec547-124">Zabezpečení rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="ec547-124">.NET Framework Security</span></span>  

 <span data-ttu-id="ec547-125">Chcete-li spustit tento proces, vaše sestavení <xref:System.Security.Permissions.RegistryPermission> vyžaduje úroveň oprávnění udělené třídou.</span><span class="sxs-lookup"><span data-stu-id="ec547-125">To run this process, your assembly requires a privilege level granted by the <xref:System.Security.Permissions.RegistryPermission> class.</span></span> <span data-ttu-id="ec547-126">Pokud jsou spuštěny v kontextu částečné důvěryhodnosti, proces může vyvolat výjimku z důvodu nedostatečných oprávnění.</span><span class="sxs-lookup"><span data-stu-id="ec547-126">If you are running in a partial-trust context, the process might throw an exception due to insufficient privileges.</span></span> <span data-ttu-id="ec547-127">Podobně musí mít uživatel správné akly pro vytváření nebo zápis do nastavení.</span><span class="sxs-lookup"><span data-stu-id="ec547-127">Similarly, the user must have the correct ACLs for creating or writing to settings.</span></span> <span data-ttu-id="ec547-128">Například místní aplikace, která má oprávnění zabezpečení přístupu kódu, nemusí mít oprávnění operačního systému.</span><span class="sxs-lookup"><span data-stu-id="ec547-128">For example, a local application that has the code access security permission might not have operating system permission.</span></span> <span data-ttu-id="ec547-129">Další informace naleznete v [tématu Základy zabezpečení přístupu kódu](../../../../framework/misc/code-access-security-basics.md).</span><span class="sxs-lookup"><span data-stu-id="ec547-129">For more information, see [Code Access Security Basics](../../../../framework/misc/code-access-security-basics.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec547-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="ec547-130">See also</span></span>

- <xref:Microsoft.VisualBasic.MyServices.RegistryProxy>
- <xref:Microsoft.Win32.RegistryHive>
- [<span data-ttu-id="ec547-131">Čtení z registru a zápis do něj</span><span class="sxs-lookup"><span data-stu-id="ec547-131">Reading from and Writing to the Registry</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/reading-from-and-writing-to-the-registry.md)
