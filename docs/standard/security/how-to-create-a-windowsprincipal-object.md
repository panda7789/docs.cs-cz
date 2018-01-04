---
title: "Postupy: Vytvoření objektu WindowsPrincipal"
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
- WindowsPrincipal objects, creating
- security [.NET Framework], creating a WindowsPrincipal object
- security [.NET Framework], principals
- principal objects, creating
ms.assetid: 56eb10ca-e61d-4ed2-af7a-555fc4c25a25
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: c4eb890696162af61f1355bfca50ce5dd2a615ad
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-create-a-windowsprincipal-object"></a><span data-ttu-id="9163b-102">Postupy: Vytvoření objektu WindowsPrincipal</span><span class="sxs-lookup"><span data-stu-id="9163b-102">How to: Create a WindowsPrincipal Object</span></span>
<span data-ttu-id="9163b-103">Existují dva způsoby, jak vytvořit <xref:System.Security.Principal.WindowsPrincipal> objektu, v závislosti na tom, zda kód musí opakovaně provádět ověřování na základě rolí nebo musí provést pouze jednou.</span><span class="sxs-lookup"><span data-stu-id="9163b-103">There are two ways to create a <xref:System.Security.Principal.WindowsPrincipal> object, depending on whether code must repeatedly perform role-based validation or must perform it only once.</span></span>  
  
 <span data-ttu-id="9163b-104">Pokud kód musí opakovaně provádět ověřování na základě rolí, první z následujících postupů produkuje menší režii.</span><span class="sxs-lookup"><span data-stu-id="9163b-104">If code must repeatedly perform role-based validation, the first of the following procedures produces less overhead.</span></span> <span data-ttu-id="9163b-105">Pokud kód potřebuje provést ověření na základě rolí, pouze jednou, můžete vytvořit <xref:System.Security.Principal.WindowsPrincipal> objekt pomocí druhého z následujících postupů.</span><span class="sxs-lookup"><span data-stu-id="9163b-105">When code needs to make role-based validations only once, you can create a <xref:System.Security.Principal.WindowsPrincipal> object by using the second of the following procedures.</span></span>  
  
### <a name="to-create-a-windowsprincipal-object-for-repeated-validation"></a><span data-ttu-id="9163b-106">K vytvoření objektu WindowsPrincipal pro opakované ověření</span><span class="sxs-lookup"><span data-stu-id="9163b-106">To create a WindowsPrincipal object for repeated validation</span></span>  
  
1.  <span data-ttu-id="9163b-107">Volání <xref:System.AppDomain.SetPrincipalPolicy%2A> metodu <xref:System.AppDomain> objekt, který je vrácen statickou <xref:System.AppDomain.CurrentDomain%2A?displayProperty=nameWithType> vlastnost předávání metodu <xref:System.Security.Principal.PrincipalPolicy> hodnotu výčtu, která určuje, co by měla být nové zásady.</span><span class="sxs-lookup"><span data-stu-id="9163b-107">Call the <xref:System.AppDomain.SetPrincipalPolicy%2A> method on the <xref:System.AppDomain> object that is returned by the static <xref:System.AppDomain.CurrentDomain%2A?displayProperty=nameWithType> property, passing the method a <xref:System.Security.Principal.PrincipalPolicy> enumeration value that indicates what the new policy should be.</span></span> <span data-ttu-id="9163b-108">Podporované hodnoty jsou <xref:System.Security.Principal.PrincipalPolicy.NoPrincipal>, <xref:System.Security.Principal.PrincipalPolicy.UnauthenticatedPrincipal>, a <xref:System.Security.Principal.PrincipalPolicy.WindowsPrincipal>.</span><span class="sxs-lookup"><span data-stu-id="9163b-108">Supported values are <xref:System.Security.Principal.PrincipalPolicy.NoPrincipal>, <xref:System.Security.Principal.PrincipalPolicy.UnauthenticatedPrincipal>, and <xref:System.Security.Principal.PrincipalPolicy.WindowsPrincipal>.</span></span> <span data-ttu-id="9163b-109">Následující kód ukazuje volání této metody.</span><span class="sxs-lookup"><span data-stu-id="9163b-109">The following code demonstrates this method call.</span></span>  
  
    ```csharp  
    AppDomain.CurrentDomain.SetPrincipalPolicy(  
        PrincipalPolicy.WindowsPrincipal);  
    ```  
  
    ```vb  
    AppDomain.CurrentDomain.SetPrincipalPolicy( _  
        PrincipalPolicy.WindowsPrincipal)  
    ```  
  
2.  <span data-ttu-id="9163b-110">Se zásadami, nastavit, použijte statickou <xref:System.Threading.Thread.CurrentPrincipal%2A?displayProperty=nameWithType> vlastnost načíst objekt, který zapouzdřuje aktuálního uživatele systému Windows.</span><span class="sxs-lookup"><span data-stu-id="9163b-110">With the policy set, use the static <xref:System.Threading.Thread.CurrentPrincipal%2A?displayProperty=nameWithType> property to retrieve the principal that encapsulates the current Windows user.</span></span> <span data-ttu-id="9163b-111">Vzhledem k tomu vlastnost návratový typ je <xref:System.Security.Principal.IPrincipal>, musíte vysílat výsledek, který má <xref:System.Security.Principal.WindowsPrincipal> typu.</span><span class="sxs-lookup"><span data-stu-id="9163b-111">Because the property return type is <xref:System.Security.Principal.IPrincipal>, you must cast the result to a <xref:System.Security.Principal.WindowsPrincipal> type.</span></span> <span data-ttu-id="9163b-112">Následující kód inicializuje novou <xref:System.Security.Principal.WindowsPrincipal> objektu na hodnotu objektu zabezpečení přidružené k aktuální vlákno.</span><span class="sxs-lookup"><span data-stu-id="9163b-112">The following code initializes a new <xref:System.Security.Principal.WindowsPrincipal> object to the value of the principal associated with the current thread.</span></span>  
  
    ```csharp  
    WindowsPrincipal MyPrincipal =   
        (WindowsPrincipal) Thread.CurrentPrincipal;  
    ```  
  
    ```vb  
    Dim MyPrincipal As WindowsPrincipal = _  
        CType(Thread.CurrentPrincipal, WindowsPrincipal)   
    ```  
  
3.  <span data-ttu-id="9163b-113">Po vytvoření objektu zabezpečení, můžete některou z několika metod pro jeho ověření.</span><span class="sxs-lookup"><span data-stu-id="9163b-113">When the principal object has been created, you can use one of several methods to validate it.</span></span>  
  
### <a name="to-create-a-windowsprincipal-object-for-a-single-validation"></a><span data-ttu-id="9163b-114">K vytvoření objektu WindowsPrincipal pro jedno ověření</span><span class="sxs-lookup"><span data-stu-id="9163b-114">To create a WindowsPrincipal object for a single validation</span></span>  
  
1.  <span data-ttu-id="9163b-115">Inicializace novou <xref:System.Security.Principal.WindowsIdentity> objekt voláním statické <xref:System.Security.Principal.WindowsIdentity.GetCurrent%2A?displayProperty=nameWithType> metoda, která dotazuje aktuální účet systému Windows a umístí informace o tento účet do nově vytvořené identity objektu.</span><span class="sxs-lookup"><span data-stu-id="9163b-115">Initialize a new <xref:System.Security.Principal.WindowsIdentity> object by calling the static <xref:System.Security.Principal.WindowsIdentity.GetCurrent%2A?displayProperty=nameWithType> method, which queries the current Windows account and places information about that account into the newly created identity object.</span></span> <span data-ttu-id="9163b-116">Následující kód vytvoří novou <xref:System.Security.Principal.WindowsIdentity> objektu a inicializuje aktuálně ověřeného uživatele.</span><span class="sxs-lookup"><span data-stu-id="9163b-116">The following code creates a new <xref:System.Security.Principal.WindowsIdentity> object and initializes it to the current authenticated user.</span></span>  
  
    ```csharp  
    WindowsIdentity MyIdentity = WindowsIdentity.GetCurrent();  
    ```  
  
    ```vb  
    Dim MyIdentity As WindowsIdentity = WindowsIdentity.GetCurrent()  
    ```  
  
2.  <span data-ttu-id="9163b-117">Vytvořte novou <xref:System.Security.Principal.WindowsPrincipal> objektu a předejte ji hodnotu <xref:System.Security.Principal.WindowsIdentity> objekt vytvořený v předchozím kroku.</span><span class="sxs-lookup"><span data-stu-id="9163b-117">Create a new <xref:System.Security.Principal.WindowsPrincipal> object and pass it the value of the <xref:System.Security.Principal.WindowsIdentity> object created in the preceding step.</span></span>  
  
    ```csharp  
    WindowsPrincipal MyPrincipal = new WindowsPrincipal(MyIdentity);  
    ```  
  
    ```vb  
    Dim MyPrincipal As New WindowsPrincipal(MyIdentity)  
    ```  
  
3.  <span data-ttu-id="9163b-118">Po vytvoření objektu zabezpečení, můžete některou z několika metod pro jeho ověření.</span><span class="sxs-lookup"><span data-stu-id="9163b-118">When the principal object has been created, you can use one of several methods to validate it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9163b-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="9163b-119">See Also</span></span>  
 [<span data-ttu-id="9163b-120">Objekty zabezpečení a identity</span><span class="sxs-lookup"><span data-stu-id="9163b-120">Principal and Identity Objects</span></span>](../../../docs/standard/security/principal-and-identity-objects.md)
