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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: bec065e2a78551b85fe766f1b81590b18f4679d7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54516821"
---
# <a name="impersonating-and-reverting"></a><span data-ttu-id="2dbee-102">Zosobnění a návrat</span><span class="sxs-lookup"><span data-stu-id="2dbee-102">Impersonating and Reverting</span></span>
<span data-ttu-id="2dbee-103">Někdy můžete potřebovat k získání tokenu účtu Windows zosobnit účet Windows.</span><span class="sxs-lookup"><span data-stu-id="2dbee-103">Sometimes you might need to obtain a Windows account token to impersonate a Windows account.</span></span> <span data-ttu-id="2dbee-104">Aplikace založená na technologii ASP.NET například může mít jednat jménem několika uživatelů v různých časech.</span><span class="sxs-lookup"><span data-stu-id="2dbee-104">For example, your ASP.NET-based application might have to act on behalf of several users at different times.</span></span> <span data-ttu-id="2dbee-105">Vaše aplikace může přijmout token, který představuje správce z Internetové informační služby (IIS), zosobnit uživatele, provedení určité operace a vrátit k předchozí identitu.</span><span class="sxs-lookup"><span data-stu-id="2dbee-105">Your application might accept a token that represents an administrator from Internet Information Services (IIS), impersonate that user, perform an operation, and revert to the previous identity.</span></span> <span data-ttu-id="2dbee-106">V dalším kroku ji může přijmout token ze služby IIS, který reprezentuje uživatele s menším počtem práv, provádět některé operace a znovu vrátit.</span><span class="sxs-lookup"><span data-stu-id="2dbee-106">Next, it might accept a token from IIS that represents a user with fewer rights, perform some operation, and revert again.</span></span>  
  
 <span data-ttu-id="2dbee-107">V situacích, kdy vaše aplikace musí zosobnit účet Windows, která nebyla připojena k aktuálnímu vláknu službou IIS je nutné získat token tohoto účtu a použít ho k aktivaci účtu.</span><span class="sxs-lookup"><span data-stu-id="2dbee-107">In situations where your application must impersonate a Windows account that has not been attached to the current thread by IIS, you must retrieve that account's token and use it to activate the account.</span></span> <span data-ttu-id="2dbee-108">Uděláte to tak provádění těchto úkolů:</span><span class="sxs-lookup"><span data-stu-id="2dbee-108">You can do this by performing the following tasks:</span></span>  
  
1.  <span data-ttu-id="2dbee-109">Získat token účtu pro určitého uživatele tím, že zavoláte na nespravovanou **LogonUser** metody.</span><span class="sxs-lookup"><span data-stu-id="2dbee-109">Retrieve an account token for a particular user by making a call to the unmanaged **LogonUser** method.</span></span> <span data-ttu-id="2dbee-110">Tato metoda není v knihovně základních tříd rozhraní .NET Framework, ale je umístěn v nespravovanou **advapi32.dll**.</span><span class="sxs-lookup"><span data-stu-id="2dbee-110">This method is not in the .NET Framework base class library, but is located in the unmanaged **advapi32.dll**.</span></span> <span data-ttu-id="2dbee-111">Přístup k metodám v nespravovaném kódu je pokročilá operace a je nad rámec této diskuse.</span><span class="sxs-lookup"><span data-stu-id="2dbee-111">Accessing methods in unmanaged code is an advanced operation and is beyond the scope of this discussion.</span></span> <span data-ttu-id="2dbee-112">Další informace najdete v tématu [spolupráce s nespravovaným kódem](../../../docs/framework/interop/index.md).</span><span class="sxs-lookup"><span data-stu-id="2dbee-112">For more information, see [Interoperating with Unmanaged Code](../../../docs/framework/interop/index.md).</span></span> <span data-ttu-id="2dbee-113">Další informace o **LogonUser** metoda a **advapi32.dll**, naleznete v dokumentaci Platform SDK.</span><span class="sxs-lookup"><span data-stu-id="2dbee-113">For more information about the **LogonUser** method and **advapi32.dll**, see the Platform SDK documentation.</span></span>  
  
2.  <span data-ttu-id="2dbee-114">Vytvořit novou instanci třídy **WindowsIdentity** třídy, prochází token.</span><span class="sxs-lookup"><span data-stu-id="2dbee-114">Create a new instance of the **WindowsIdentity** class, passing the token.</span></span> <span data-ttu-id="2dbee-115">Následující kód ukazuje toto volání, kde `hToken` představuje Windows token.</span><span class="sxs-lookup"><span data-stu-id="2dbee-115">The following code demonstrates this call, where `hToken` represents a Windows token.</span></span>  
  
    ```csharp  
    WindowsIdentity ImpersonatedIdentity = new WindowsIdentity(hToken);  
    ```  
  
    ```vb  
    Dim ImpersonatedIdentity As New WindowsIdentity(hToken)  
    ```  
  
3.  <span data-ttu-id="2dbee-116">Začněte tím, že vytvoříte novou instanci třídy zosobnění <xref:System.Security.Principal.WindowsImpersonationContext> třídy a inicializuje ji <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A?displayProperty=nameWithType> metoda inicializovaného třídy, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="2dbee-116">Begin impersonation by creating a new instance of the <xref:System.Security.Principal.WindowsImpersonationContext> class and initializing it with the <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A?displayProperty=nameWithType> method of the initialized class, as shown in the following code.</span></span>  
  
    ```csharp  
    WindowsImpersonationContext MyImpersonation = ImpersonatedIdentity.Impersonate();  
    ```  
  
    ```vb  
    WindowsImpersonationContext MyImpersonation = ImpersonatedIdentity.Impersonate()  
    ```  
  
4.  <span data-ttu-id="2dbee-117">Pokud už nepotřebujete k zosobnění, zavolejte <xref:System.Security.Principal.WindowsImpersonationContext.Undo%2A?displayProperty=nameWithType> metoda Obnova zosobnění, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="2dbee-117">When you no longer need to impersonate, call the <xref:System.Security.Principal.WindowsImpersonationContext.Undo%2A?displayProperty=nameWithType> method to revert the impersonation, as shown in the following code.</span></span>  
  
    ```csharp  
    MyImpersonation.Undo();  
    ```  
  
    ```vb  
    MyImpersonation.Undo()  
    ```  
  
 <span data-ttu-id="2dbee-118">Pokud je důvěryhodné, kód se už připojilo <xref:System.Security.Principal.WindowsPrincipal> objekt vlákna, můžete volat metodu instance **zosobnit**, které nepřijímá token účtu.</span><span class="sxs-lookup"><span data-stu-id="2dbee-118">If trusted code has already attached a <xref:System.Security.Principal.WindowsPrincipal> object to the thread, you can call the instance method **Impersonate**, which does not take an account token.</span></span> <span data-ttu-id="2dbee-119">Všimněte si, že se jedná pouze užitečné, když **WindowsPrincipal** objektu ve vlákně představuje uživatele, než pod kterým proces aktuálně spouští.</span><span class="sxs-lookup"><span data-stu-id="2dbee-119">Note that this is only useful when the **WindowsPrincipal** object on the thread represents a user other than the one under which the process is currently executing.</span></span> <span data-ttu-id="2dbee-120">Například může dojít k této situaci pomocí technologie ASP.NET s ověřováním Windows zapnutý a zosobnění vypnuté.</span><span class="sxs-lookup"><span data-stu-id="2dbee-120">For example, you might encounter this situation using ASP.NET with Windows authentication turned on and impersonation turned off.</span></span> <span data-ttu-id="2dbee-121">V takovém případě je proces spuštěn pod účtem nakonfigurovat v Internetové informační služby (IIS), pokud je aktuální objekt zabezpečení představuje uživatele Windows, který je přistoupit ke stránce.</span><span class="sxs-lookup"><span data-stu-id="2dbee-121">In this case, the process is running under an account configured in Internet Information Services (IIS) while the current principal represents the Windows user that is accessing the page.</span></span>  
  
 <span data-ttu-id="2dbee-122">Všimněte si, že ani jeden **zosobnit** ani **zpět** změny **hlavní** objektu (<xref:System.Security.Principal.IPrincipal>) přidružené k aktuálnímu kontextu volání.</span><span class="sxs-lookup"><span data-stu-id="2dbee-122">Note that neither **Impersonate** nor **Undo** changes the **Principal** object (<xref:System.Security.Principal.IPrincipal>)  associated with the current call context.</span></span> <span data-ttu-id="2dbee-123">Místo toho zosobnění a vracení změn token spojený s aktuální proces operačního systému...</span><span class="sxs-lookup"><span data-stu-id="2dbee-123">Rather, impersonation and reverting change the token associated with the current operating system process..</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2dbee-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2dbee-124">See also</span></span>

- <xref:System.Security.Principal.WindowsIdentity>
- <xref:System.Security.Principal.WindowsImpersonationContext>
- [<span data-ttu-id="2dbee-125">Objekty zabezpečení a identity</span><span class="sxs-lookup"><span data-stu-id="2dbee-125">Principal and Identity Objects</span></span>](../../../docs/standard/security/principal-and-identity-objects.md)
- [<span data-ttu-id="2dbee-126">Spolupráce s nespravovaným kódem</span><span class="sxs-lookup"><span data-stu-id="2dbee-126">Interoperating with Unmanaged Code</span></span>](../../../docs/framework/interop/index.md)
