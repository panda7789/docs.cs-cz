---
title: Zosobnění a návrat
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WindowsIdentity objects, impersonating
- security [.NET Framework], impersonating Windows accounts
- impersonating Windows accounts
ms.assetid: b93d402c-6c28-4f50-b2bc-d9607dc3e470
ms.openlocfilehash: dbfd71830ace1eb8af9f55f06c9ce35c32d592bb
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288014"
---
# <a name="impersonating-and-reverting"></a><span data-ttu-id="a8b92-102">Zosobnění a návrat</span><span class="sxs-lookup"><span data-stu-id="a8b92-102">Impersonating and Reverting</span></span>
<span data-ttu-id="a8b92-103">Někdy může být nutné získat token účtu systému Windows k zosobnění účtu systému Windows.</span><span class="sxs-lookup"><span data-stu-id="a8b92-103">Sometimes you might need to obtain a Windows account token to impersonate a Windows account.</span></span> <span data-ttu-id="a8b92-104">Například vaše aplikace založená na ASP.NET může muset v různých časech jednat jménem několika uživatelů.</span><span class="sxs-lookup"><span data-stu-id="a8b92-104">For example, your ASP.NET-based application might have to act on behalf of several users at different times.</span></span> <span data-ttu-id="a8b92-105">Vaše aplikace může přijmout token, který představuje správce z Internetová informační služba (IIS), zosobnit tohoto uživatele, provést operaci a vrátit se k předchozí identitě.</span><span class="sxs-lookup"><span data-stu-id="a8b92-105">Your application might accept a token that represents an administrator from Internet Information Services (IIS), impersonate that user, perform an operation, and revert to the previous identity.</span></span> <span data-ttu-id="a8b92-106">V dalším kroku může přijmout token ze služby IIS, který představuje uživatele s menšími právy, provede nějakou operaci a vrátí se znovu.</span><span class="sxs-lookup"><span data-stu-id="a8b92-106">Next, it might accept a token from IIS that represents a user with fewer rights, perform some operation, and revert again.</span></span>  
  
 <span data-ttu-id="a8b92-107">V situacích, kdy musí vaše aplikace zosobnit účet systému Windows, který nebyl připojen k aktuálnímu vláknu službou IIS, je nutné načíst token tohoto účtu a použít ho k aktivaci účtu.</span><span class="sxs-lookup"><span data-stu-id="a8b92-107">In situations where your application must impersonate a Windows account that has not been attached to the current thread by IIS, you must retrieve that account's token and use it to activate the account.</span></span> <span data-ttu-id="a8b92-108">Můžete to provést provedením následujících úloh:</span><span class="sxs-lookup"><span data-stu-id="a8b92-108">You can do this by performing the following tasks:</span></span>  
  
1. <span data-ttu-id="a8b92-109">Načtěte token účtu pro konkrétního uživatele voláním nespravované metody **LogonUser** .</span><span class="sxs-lookup"><span data-stu-id="a8b92-109">Retrieve an account token for a particular user by making a call to the unmanaged **LogonUser** method.</span></span> <span data-ttu-id="a8b92-110">Tato metoda není v .NET Framework základní knihovny tříd, ale je umístěna v nespravované knihovně **advapi32. dll**.</span><span class="sxs-lookup"><span data-stu-id="a8b92-110">This method is not in the .NET Framework base class library, but is located in the unmanaged **advapi32.dll**.</span></span> <span data-ttu-id="a8b92-111">Přístup k metodám v nespravovaném kódu je pokročilá operace a překračuje rozsah této diskuze.</span><span class="sxs-lookup"><span data-stu-id="a8b92-111">Accessing methods in unmanaged code is an advanced operation and is beyond the scope of this discussion.</span></span> <span data-ttu-id="a8b92-112">Další informace najdete v tématu [spolupráce s nespravovaným kódem](../../framework/interop/index.md).</span><span class="sxs-lookup"><span data-stu-id="a8b92-112">For more information, see [Interoperating with Unmanaged Code](../../framework/interop/index.md).</span></span> <span data-ttu-id="a8b92-113">Další informace o metodě **LogonUser** a **advapi32. dll**naleznete v dokumentaci k sadě SDK platformy.</span><span class="sxs-lookup"><span data-stu-id="a8b92-113">For more information about the **LogonUser** method and **advapi32.dll**, see the Platform SDK documentation.</span></span>  
  
2. <span data-ttu-id="a8b92-114">Vytvořte novou instanci třídy **WindowsIdentity** a předejte token.</span><span class="sxs-lookup"><span data-stu-id="a8b92-114">Create a new instance of the **WindowsIdentity** class, passing the token.</span></span> <span data-ttu-id="a8b92-115">Následující kód demonstruje toto volání, kde `hToken` představuje token systému Windows.</span><span class="sxs-lookup"><span data-stu-id="a8b92-115">The following code demonstrates this call, where `hToken` represents a Windows token.</span></span>  
  
    ```csharp  
    WindowsIdentity impersonatedIdentity = new WindowsIdentity(hToken);  
    ```  
  
    ```vb  
    Dim impersonatedIdentity As New WindowsIdentity(hToken)  
    ```  
  
3. <span data-ttu-id="a8b92-116">Zahajte zosobnění vytvořením nové instance <xref:System.Security.Principal.WindowsImpersonationContext> třídy a inicializací s <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A?displayProperty=nameWithType> metodou inicializované třídy, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="a8b92-116">Begin impersonation by creating a new instance of the <xref:System.Security.Principal.WindowsImpersonationContext> class and initializing it with the <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A?displayProperty=nameWithType> method of the initialized class, as shown in the following code.</span></span>  
  
    ```csharp  
    WindowsImpersonationContext myImpersonation = impersonatedIdentity.Impersonate();  
    ```  
  
    ```vb  
    WindowsImpersonationContext myImpersonation = impersonatedIdentity.Impersonate()  
    ```  
  
4. <span data-ttu-id="a8b92-117">Pokud již nepotřebujete zosobnit, zavolejte <xref:System.Security.Principal.WindowsImpersonationContext.Undo%2A?displayProperty=nameWithType> metodu pro vrácení zosobnění, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="a8b92-117">When you no longer need to impersonate, call the <xref:System.Security.Principal.WindowsImpersonationContext.Undo%2A?displayProperty=nameWithType> method to revert the impersonation, as shown in the following code.</span></span>  
  
    ```csharp  
    myImpersonation.Undo();  
    ```  
  
    ```vb  
    myImpersonation.Undo()  
    ```  
  
 <span data-ttu-id="a8b92-118">Pokud důvěryhodný kód již <xref:System.Security.Principal.WindowsPrincipal> k vláknu připojen objekt, můžete zavolat metodu instance **impersonate**, která nepřijímá token účtu.</span><span class="sxs-lookup"><span data-stu-id="a8b92-118">If trusted code has already attached a <xref:System.Security.Principal.WindowsPrincipal> object to the thread, you can call the instance method **Impersonate**, which does not take an account token.</span></span> <span data-ttu-id="a8b92-119">Všimněte si, že tato operace je užitečná pouze v případě, že objekt **WindowsPrincipal** ve vlákně představuje uživatele, který není v současné době spuštěn.</span><span class="sxs-lookup"><span data-stu-id="a8b92-119">Note that this is only useful when the **WindowsPrincipal** object on the thread represents a user other than the one under which the process is currently executing.</span></span> <span data-ttu-id="a8b92-120">Například se můžete setkat s tím, že se tato situace může vyskytnout s ověřováním systému Windows, které je zapnuté a zosobněné.</span><span class="sxs-lookup"><span data-stu-id="a8b92-120">For example, you might encounter this situation using ASP.NET with Windows authentication turned on and impersonation turned off.</span></span> <span data-ttu-id="a8b92-121">V takovém případě je proces spuštěn pod účtem nakonfigurovaným ve službě Internetová informační služba (IIS), zatímco aktuální objekt zabezpečení představuje uživatele systému Windows, který přistupuje k této stránce.</span><span class="sxs-lookup"><span data-stu-id="a8b92-121">In this case, the process is running under an account configured in Internet Information Services (IIS) while the current principal represents the Windows user that is accessing the page.</span></span>  
  
 <span data-ttu-id="a8b92-122">Všimněte si, že ani nemůže **Zrušit** **zosobnění** ani zrušení změn objektu **zabezpečení** ( <xref:System.Security.Principal.IPrincipal> ) přidruženého k aktuálnímu kontextu volání.</span><span class="sxs-lookup"><span data-stu-id="a8b92-122">Note that neither **Impersonate** nor **Undo** changes the **Principal** object (<xref:System.Security.Principal.IPrincipal>)  associated with the current call context.</span></span> <span data-ttu-id="a8b92-123">Místo toho jsou zosobnění a vrácení změn tokenu přidruženého k aktuálnímu procesu operačního systému.</span><span class="sxs-lookup"><span data-stu-id="a8b92-123">Rather, impersonation and reverting change the token associated with the current operating system process..</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8b92-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="a8b92-124">See also</span></span>

- <xref:System.Security.Principal.WindowsIdentity>
- <xref:System.Security.Principal.WindowsImpersonationContext>
- [<span data-ttu-id="a8b92-125">Objekty zabezpečení a identity</span><span class="sxs-lookup"><span data-stu-id="a8b92-125">Principal and Identity Objects</span></span>](principal-and-identity-objects.md)
- [<span data-ttu-id="a8b92-126">Spolupráce s nespravovaným kódem</span><span class="sxs-lookup"><span data-stu-id="a8b92-126">Interoperating with Unmanaged Code</span></span>](../../framework/interop/index.md)
