---
title: "Zosobnění a návrat"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WindowsIdentity objects, impersonating
- security [.NET Framework], impersonating Windows accounts
- impersonating Windows accounts
ms.assetid: b93d402c-6c28-4f50-b2bc-d9607dc3e470
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 869b9aadfa236a39d9807062e61046922e382d13
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="impersonating-and-reverting"></a><span data-ttu-id="380bc-102">Zosobnění a návrat</span><span class="sxs-lookup"><span data-stu-id="380bc-102">Impersonating and Reverting</span></span>
<span data-ttu-id="380bc-103">V některých případech budete muset získat token účtu Windows zosobnit účet systému Windows.</span><span class="sxs-lookup"><span data-stu-id="380bc-103">Sometimes you might need to obtain a Windows account token to impersonate a Windows account.</span></span> <span data-ttu-id="380bc-104">Například aplikace založený na technologii ASP.NET může mít zastupovat několika uživatelům v různých časech.</span><span class="sxs-lookup"><span data-stu-id="380bc-104">For example, your ASP.NET-based application might have to act on behalf of several users at different times.</span></span> <span data-ttu-id="380bc-105">Aplikace může přijmout token, který představuje správce z Internetové informační služby (IIS), zosobnit uživatele, provedení určité operace a vrátit k předchozí identitu.</span><span class="sxs-lookup"><span data-stu-id="380bc-105">Your application might accept a token that represents an administrator from Internet Information Services (IIS), impersonate that user, perform an operation, and revert to the previous identity.</span></span> <span data-ttu-id="380bc-106">V dalším kroku ji může přijmout token ze služby IIS, který reprezentuje uživatele s menším počtem práv, provádět některé operace a vracet znovu.</span><span class="sxs-lookup"><span data-stu-id="380bc-106">Next, it might accept a token from IIS that represents a user with fewer rights, perform some operation, and revert again.</span></span>  
  
 <span data-ttu-id="380bc-107">V situacích, kde vaše aplikace musí zosobnit účet Windows, který nebyl přidán do aktuální vlákno službou IIS je nutné získat token tohoto účtu a použít ho k aktivaci účtu.</span><span class="sxs-lookup"><span data-stu-id="380bc-107">In situations where your application must impersonate a Windows account that has not been attached to the current thread by IIS, you must retrieve that account's token and use it to activate the account.</span></span> <span data-ttu-id="380bc-108">To provedete tak, že provedete následující úlohy:</span><span class="sxs-lookup"><span data-stu-id="380bc-108">You can do this by performing the following tasks:</span></span>  
  
1.  <span data-ttu-id="380bc-109">Získat token účtu pro určitého uživatele tím, že zavoláte na nespravovanou **LogonUser** metoda.</span><span class="sxs-lookup"><span data-stu-id="380bc-109">Retrieve an account token for a particular user by making a call to the unmanaged **LogonUser** method.</span></span> <span data-ttu-id="380bc-110">Tato metoda není v knihovně základní třídy rozhraní .NET Framework, ale je umístěn v nespravovanou **advapi32.dll**.</span><span class="sxs-lookup"><span data-stu-id="380bc-110">This method is not in the .NET Framework base class library, but is located in the unmanaged **advapi32.dll**.</span></span> <span data-ttu-id="380bc-111">Přístup k metodám v nespravovaném kódu je pokročilá operace a je nad rámec této diskuse.</span><span class="sxs-lookup"><span data-stu-id="380bc-111">Accessing methods in unmanaged code is an advanced operation and is beyond the scope of this discussion.</span></span> <span data-ttu-id="380bc-112">Další informace najdete v tématu [spolupráce s nespravovaným kódem](../../../docs/framework/interop/index.md).</span><span class="sxs-lookup"><span data-stu-id="380bc-112">For more information, see [Interoperating with Unmanaged Code](../../../docs/framework/interop/index.md).</span></span> <span data-ttu-id="380bc-113">Další informace o **LogonUser** metoda a **advapi32.dll**, naleznete v dokumentaci k sadě SDK pro platformu.</span><span class="sxs-lookup"><span data-stu-id="380bc-113">For more information about the **LogonUser** method and **advapi32.dll**, see the Platform SDK documentation.</span></span>  
  
2.  <span data-ttu-id="380bc-114">Vytvořit novou instanci třídy **WindowsIdentity** třídy a předejte token.</span><span class="sxs-lookup"><span data-stu-id="380bc-114">Create a new instance of the **WindowsIdentity** class, passing the token.</span></span> <span data-ttu-id="380bc-115">Následující kód ukazuje toto volání, kde `hToken` představuje tokenu systému Windows.</span><span class="sxs-lookup"><span data-stu-id="380bc-115">The following code demonstrates this call, where `hToken` represents a Windows token.</span></span>  
  
    ```csharp  
    WindowsIdentity ImpersonatedIdentity = new WindowsIdentity(hToken);  
    ```  
  
    ```vb  
    Dim ImpersonatedIdentity As New WindowsIdentity(hToken)  
    ```  
  
3.  <span data-ttu-id="380bc-116">Nejprve vytvořit novou instanci třídy zosobnění <xref:System.Security.Principal.WindowsImpersonationContext> třídy a inicializací s <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A?displayProperty=nameWithType> metoda inicializované třídy, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="380bc-116">Begin impersonation by creating a new instance of the <xref:System.Security.Principal.WindowsImpersonationContext> class and initializing it with the <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A?displayProperty=nameWithType> method of the initialized class, as shown in the following code.</span></span>  
  
    ```csharp  
    WindowsImpersonationContext MyImpersonation = ImpersonatedIdentity.Impersonate();  
    ```  
  
    ```vb  
    WindowsImpersonationContext MyImpersonation = ImpersonatedIdentity.Impersonate()  
    ```  
  
4.  <span data-ttu-id="380bc-117">Pokud již nepotřebujete zosobnění, volejte <xref:System.Security.Principal.WindowsImpersonationContext.Undo%2A?displayProperty=nameWithType> metoda k uloženému zosobnění, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="380bc-117">When you no longer need to impersonate, call the <xref:System.Security.Principal.WindowsImpersonationContext.Undo%2A?displayProperty=nameWithType> method to revert the impersonation, as shown in the following code.</span></span>  
  
    ```csharp  
    MyImpersonation.Undo();  
    ```  
  
    ```vb  
    MyImpersonation.Undo()  
    ```  
  
 <span data-ttu-id="380bc-118">Pokud důvěryhodný kód již připojil <xref:System.Security.Principal.WindowsPrincipal> objektu vlákna, můžete volat metodu instance **zosobnit**, které nevyužívá token účtu.</span><span class="sxs-lookup"><span data-stu-id="380bc-118">If trusted code has already attached a <xref:System.Security.Principal.WindowsPrincipal> object to the thread, you can call the instance method **Impersonate**, which does not take an account token.</span></span> <span data-ttu-id="380bc-119">Všimněte si, že to je užitečné pouze když **WindowsPrincipal** objekt ve vlákně představuje uživatele, než ve kterém je aktuálně spuštěn proces.</span><span class="sxs-lookup"><span data-stu-id="380bc-119">Note that this is only useful when the **WindowsPrincipal** object on the thread represents a user other than the one under which the process is currently executing.</span></span> <span data-ttu-id="380bc-120">Například může dojít k této situaci ASP.NET pomocí ověřování systému Windows zapnuté a zosobnění vypnutý.</span><span class="sxs-lookup"><span data-stu-id="380bc-120">For example, you might encounter this situation using ASP.NET with Windows authentication turned on and impersonation turned off.</span></span> <span data-ttu-id="380bc-121">V takovém případě je proces spuštěný pod účtem, nakonfigurovat v Internetové informační služby (IIS), pokud je aktuální objekt zabezpečení představuje uživatele systému Windows, který je přistoupit ke stránce.</span><span class="sxs-lookup"><span data-stu-id="380bc-121">In this case, the process is running under an account configured in Internet Information Services (IIS) while the current principal represents the Windows user that is accessing the page.</span></span>  
  
 <span data-ttu-id="380bc-122">Všimněte si, že ani **zosobnit** ani **vrátit zpět** změny **hlavní** objektu (<xref:System.Security.Principal.IPrincipal>) přidružené k aktuální kontext volání.</span><span class="sxs-lookup"><span data-stu-id="380bc-122">Note that neither **Impersonate** nor **Undo** changes the **Principal** object (<xref:System.Security.Principal.IPrincipal>)  associated with the current call context.</span></span> <span data-ttu-id="380bc-123">Místo toho zosobnění a navrácení změnu token přidružené k aktuální proces operačního systému...</span><span class="sxs-lookup"><span data-stu-id="380bc-123">Rather, impersonation and reverting change the token associated with the current operating system process..</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="380bc-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="380bc-124">See Also</span></span>  
 <xref:System.Security.Principal.WindowsIdentity>  
 <xref:System.Security.Principal.WindowsImpersonationContext>  
 [<span data-ttu-id="380bc-125">Objekty zabezpečení a identity</span><span class="sxs-lookup"><span data-stu-id="380bc-125">Principal and Identity Objects</span></span>](../../../docs/standard/security/principal-and-identity-objects.md)  
 [<span data-ttu-id="380bc-126">Spolupráce s nespravovaným kódem</span><span class="sxs-lookup"><span data-stu-id="380bc-126">Interoperating with Unmanaged Code</span></span>](../../../docs/framework/interop/index.md)
