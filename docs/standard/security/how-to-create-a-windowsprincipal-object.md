---
title: 'Postupy: Vytvoření objektu WindowsPrincipal'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WindowsPrincipal objects, creating
- security [.NET Framework], creating a WindowsPrincipal object
- security [.NET Framework], principals
- principal objects, creating
ms.assetid: 56eb10ca-e61d-4ed2-af7a-555fc4c25a25
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8f298a7b036857e783efa128ce45ee8634ce993d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59314451"
---
# <a name="how-to-create-a-windowsprincipal-object"></a><span data-ttu-id="6bacb-102">Postupy: Vytvoření objektu WindowsPrincipal</span><span class="sxs-lookup"><span data-stu-id="6bacb-102">How to: Create a WindowsPrincipal Object</span></span>
<span data-ttu-id="6bacb-103">Existují dva způsoby, jak vytvořit <xref:System.Security.Principal.WindowsPrincipal> objekt, v závislosti na tom, zda kód nutné opakovaně provádět ověřování na základě rolí nebo musí provést pouze jednou.</span><span class="sxs-lookup"><span data-stu-id="6bacb-103">There are two ways to create a <xref:System.Security.Principal.WindowsPrincipal> object, depending on whether code must repeatedly perform role-based validation or must perform it only once.</span></span>  
  
 <span data-ttu-id="6bacb-104">Pokud kód musí opakovaně provádět ověřování na základě rolí, první z těchto postupů vytváří menší nároky.</span><span class="sxs-lookup"><span data-stu-id="6bacb-104">If code must repeatedly perform role-based validation, the first of the following procedures produces less overhead.</span></span> <span data-ttu-id="6bacb-105">Pokud kód potřebuje provést ověření na základě rolí pouze jednou, můžete vytvořit <xref:System.Security.Principal.WindowsPrincipal> s použitím sekundu z následujících postupů.</span><span class="sxs-lookup"><span data-stu-id="6bacb-105">When code needs to make role-based validations only once, you can create a <xref:System.Security.Principal.WindowsPrincipal> object by using the second of the following procedures.</span></span>  
  
### <a name="to-create-a-windowsprincipal-object-for-repeated-validation"></a><span data-ttu-id="6bacb-106">K vytvoření objektu WindowsPrincipal pro opakované ověření</span><span class="sxs-lookup"><span data-stu-id="6bacb-106">To create a WindowsPrincipal object for repeated validation</span></span>  
  
1. <span data-ttu-id="6bacb-107">Volání <xref:System.AppDomain.SetPrincipalPolicy%2A> metodu na <xref:System.AppDomain> objekt, který je vrácený statické <xref:System.AppDomain.CurrentDomain%2A?displayProperty=nameWithType> vlastnost předávání metodu <xref:System.Security.Principal.PrincipalPolicy> hodnotu výčtu, která určuje, co by měl být nové zásady.</span><span class="sxs-lookup"><span data-stu-id="6bacb-107">Call the <xref:System.AppDomain.SetPrincipalPolicy%2A> method on the <xref:System.AppDomain> object that is returned by the static <xref:System.AppDomain.CurrentDomain%2A?displayProperty=nameWithType> property, passing the method a <xref:System.Security.Principal.PrincipalPolicy> enumeration value that indicates what the new policy should be.</span></span> <span data-ttu-id="6bacb-108">Podporované hodnoty jsou <xref:System.Security.Principal.PrincipalPolicy.NoPrincipal>, <xref:System.Security.Principal.PrincipalPolicy.UnauthenticatedPrincipal>, a <xref:System.Security.Principal.PrincipalPolicy.WindowsPrincipal>.</span><span class="sxs-lookup"><span data-stu-id="6bacb-108">Supported values are <xref:System.Security.Principal.PrincipalPolicy.NoPrincipal>, <xref:System.Security.Principal.PrincipalPolicy.UnauthenticatedPrincipal>, and <xref:System.Security.Principal.PrincipalPolicy.WindowsPrincipal>.</span></span> <span data-ttu-id="6bacb-109">Následující kód ukazuje volání této metody.</span><span class="sxs-lookup"><span data-stu-id="6bacb-109">The following code demonstrates this method call.</span></span>  
  
    ```csharp  
    AppDomain.CurrentDomain.SetPrincipalPolicy(  
        PrincipalPolicy.WindowsPrincipal);  
    ```  
  
    ```vb  
    AppDomain.CurrentDomain.SetPrincipalPolicy( _  
        PrincipalPolicy.WindowsPrincipal)  
    ```  
  
2. <span data-ttu-id="6bacb-110">Nastavit zásady, použijte statické <xref:System.Threading.Thread.CurrentPrincipal%2A?displayProperty=nameWithType> vlastnost pro načtení instanční objekt, který zapouzdřuje aktuálního uživatele Windows.</span><span class="sxs-lookup"><span data-stu-id="6bacb-110">With the policy set, use the static <xref:System.Threading.Thread.CurrentPrincipal%2A?displayProperty=nameWithType> property to retrieve the principal that encapsulates the current Windows user.</span></span> <span data-ttu-id="6bacb-111">Vzhledem k tomu, že vlastnost návratový typ <xref:System.Security.Principal.IPrincipal>, musíte přetypovat výsledek, který má <xref:System.Security.Principal.WindowsPrincipal> typu.</span><span class="sxs-lookup"><span data-stu-id="6bacb-111">Because the property return type is <xref:System.Security.Principal.IPrincipal>, you must cast the result to a <xref:System.Security.Principal.WindowsPrincipal> type.</span></span> <span data-ttu-id="6bacb-112">Následující kód inicializuje novou <xref:System.Security.Principal.WindowsPrincipal> objektu na hodnotu objektu spojené s aktuálním vláknem.</span><span class="sxs-lookup"><span data-stu-id="6bacb-112">The following code initializes a new <xref:System.Security.Principal.WindowsPrincipal> object to the value of the principal associated with the current thread.</span></span>  
  
    ```csharp  
    WindowsPrincipal myPrincipal =   
        (WindowsPrincipal) Thread.CurrentPrincipal;  
    ```  
  
    ```vb  
    Dim myPrincipal As WindowsPrincipal = _  
        CType(Thread.CurrentPrincipal, WindowsPrincipal)   
    ```  
  
3. <span data-ttu-id="6bacb-113">Po vytvoření objektu zabezpečení, můžete použít některou z několika metod abyste ověřili, že.</span><span class="sxs-lookup"><span data-stu-id="6bacb-113">When the principal object has been created, you can use one of several methods to validate it.</span></span>  
  
### <a name="to-create-a-windowsprincipal-object-for-a-single-validation"></a><span data-ttu-id="6bacb-114">K vytvoření objektu WindowsPrincipal pro jedno ověření</span><span class="sxs-lookup"><span data-stu-id="6bacb-114">To create a WindowsPrincipal object for a single validation</span></span>  
  
1. <span data-ttu-id="6bacb-115">Inicializovat nový <xref:System.Security.Principal.WindowsIdentity> objektu voláním statické <xref:System.Security.Principal.WindowsIdentity.GetCurrent%2A?displayProperty=nameWithType> metodu, která vyhledá aktuální účet Windows a uvádí informace o tento účet do nově vytvořeného identity objektu.</span><span class="sxs-lookup"><span data-stu-id="6bacb-115">Initialize a new <xref:System.Security.Principal.WindowsIdentity> object by calling the static <xref:System.Security.Principal.WindowsIdentity.GetCurrent%2A?displayProperty=nameWithType> method, which queries the current Windows account and places information about that account into the newly created identity object.</span></span> <span data-ttu-id="6bacb-116">Následující kód vytvoří novou <xref:System.Security.Principal.WindowsIdentity> objektu a inicializuje ji aktuálně ověřeného uživatele.</span><span class="sxs-lookup"><span data-stu-id="6bacb-116">The following code creates a new <xref:System.Security.Principal.WindowsIdentity> object and initializes it to the current authenticated user.</span></span>  
  
    ```csharp  
    WindowsIdentity myIdentity = WindowsIdentity.GetCurrent();  
    ```  
  
    ```vb  
    Dim myIdentity As WindowsIdentity = WindowsIdentity.GetCurrent()  
    ```  
  
2. <span data-ttu-id="6bacb-117">Vytvořte nový <xref:System.Security.Principal.WindowsPrincipal> objektu a předejte jí hodnotu <xref:System.Security.Principal.WindowsIdentity> objekt vytvořený v předchozím kroku.</span><span class="sxs-lookup"><span data-stu-id="6bacb-117">Create a new <xref:System.Security.Principal.WindowsPrincipal> object and pass it the value of the <xref:System.Security.Principal.WindowsIdentity> object created in the preceding step.</span></span>  
  
    ```csharp  
    WindowsPrincipal myPrincipal = new WindowsPrincipal(myIdentity);  
    ```  
  
    ```vb  
    Dim myPrincipal As New WindowsPrincipal(myIdentity)  
    ```  
  
3. <span data-ttu-id="6bacb-118">Po vytvoření objektu zabezpečení, můžete použít některou z několika metod abyste ověřili, že.</span><span class="sxs-lookup"><span data-stu-id="6bacb-118">When the principal object has been created, you can use one of several methods to validate it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6bacb-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6bacb-119">See also</span></span>

- [<span data-ttu-id="6bacb-120">Objekty zabezpečení a identity</span><span class="sxs-lookup"><span data-stu-id="6bacb-120">Principal and Identity Objects</span></span>](../../../docs/standard/security/principal-and-identity-objects.md)
