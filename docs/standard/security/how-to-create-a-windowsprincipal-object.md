---
title: 'Postupy: Vytvoření objektu WindowsPrincipal'
ms.date: 07/15/2020
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WindowsPrincipal objects, creating
- security [.NET], creating a WindowsPrincipal object
- security [.NET], principals
- principal objects, creating
ms.assetid: 56eb10ca-e61d-4ed2-af7a-555fc4c25a25
ms.openlocfilehash: d99d63dc766f37e7cc30888d2e77657595f909af
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/04/2020
ms.locfileid: "87557031"
---
# <a name="how-to-create-a-windowsprincipal-object"></a><span data-ttu-id="2dd3c-102">Postupy: Vytvoření objektu WindowsPrincipal</span><span class="sxs-lookup"><span data-stu-id="2dd3c-102">How to: Create a WindowsPrincipal Object</span></span>

> [!NOTE]
> <span data-ttu-id="2dd3c-103">Tento článek se týká systému Windows.</span><span class="sxs-lookup"><span data-stu-id="2dd3c-103">This article applies to Windows.</span></span>
>
> <span data-ttu-id="2dd3c-104">Informace o ASP.NET Core najdete v tématu [ASP.NET Core Security](/aspnet/core/security/).</span><span class="sxs-lookup"><span data-stu-id="2dd3c-104">For information about ASP.NET Core, see [ASP.NET Core Security](/aspnet/core/security/).</span></span>

<span data-ttu-id="2dd3c-105">Existují dva způsoby, jak vytvořit <xref:System.Security.Principal.WindowsPrincipal> objekt, v závislosti na tom, zda kód musí opakovaně provádět ověřování na základě rolí, nebo musí být proveden pouze jednou.</span><span class="sxs-lookup"><span data-stu-id="2dd3c-105">There are two ways to create a <xref:System.Security.Principal.WindowsPrincipal> object, depending on whether code must repeatedly perform role-based validation or must perform it only once.</span></span>  
  
<span data-ttu-id="2dd3c-106">Pokud kód musí opakovaně provádět ověřování na základě rolí, pak první z následujících postupů vytvoří méně režijních nákladů.</span><span class="sxs-lookup"><span data-stu-id="2dd3c-106">If code must repeatedly perform role-based validation, the first of the following procedures produces less overhead.</span></span> <span data-ttu-id="2dd3c-107">Pokud kód potřebuje provést ověřování na základě role pouze jednou, můžete vytvořit <xref:System.Security.Principal.WindowsPrincipal> objekt pomocí druhého z následujících postupů.</span><span class="sxs-lookup"><span data-stu-id="2dd3c-107">When code needs to make role-based validations only once, you can create a <xref:System.Security.Principal.WindowsPrincipal> object by using the second of the following procedures.</span></span>  
  
### <a name="to-create-a-windowsprincipal-object-for-repeated-validation"></a><span data-ttu-id="2dd3c-108">Vytvoření objektu WindowsPrincipal pro opakované ověření</span><span class="sxs-lookup"><span data-stu-id="2dd3c-108">To create a WindowsPrincipal object for repeated validation</span></span>  
  
1. <span data-ttu-id="2dd3c-109">Zavolejte <xref:System.AppDomain.SetPrincipalPolicy%2A> metodu u <xref:System.AppDomain> objektu, který je vrácený statickou <xref:System.AppDomain.CurrentDomain%2A?displayProperty=nameWithType> vlastností, předáním metody <xref:System.Security.Principal.PrincipalPolicy> hodnotu výčtu, která indikuje, co by mělo být nové zásady.</span><span class="sxs-lookup"><span data-stu-id="2dd3c-109">Call the <xref:System.AppDomain.SetPrincipalPolicy%2A> method on the <xref:System.AppDomain> object that is returned by the static <xref:System.AppDomain.CurrentDomain%2A?displayProperty=nameWithType> property, passing the method a <xref:System.Security.Principal.PrincipalPolicy> enumeration value that indicates what the new policy should be.</span></span> <span data-ttu-id="2dd3c-110">Podporované hodnoty jsou <xref:System.Security.Principal.PrincipalPolicy.NoPrincipal> , <xref:System.Security.Principal.PrincipalPolicy.UnauthenticatedPrincipal> a <xref:System.Security.Principal.PrincipalPolicy.WindowsPrincipal> .</span><span class="sxs-lookup"><span data-stu-id="2dd3c-110">Supported values are <xref:System.Security.Principal.PrincipalPolicy.NoPrincipal>, <xref:System.Security.Principal.PrincipalPolicy.UnauthenticatedPrincipal>, and <xref:System.Security.Principal.PrincipalPolicy.WindowsPrincipal>.</span></span> <span data-ttu-id="2dd3c-111">Následující kód demonstruje toto volání metody.</span><span class="sxs-lookup"><span data-stu-id="2dd3c-111">The following code demonstrates this method call.</span></span>  
  
    ```csharp  
    AppDomain.CurrentDomain.SetPrincipalPolicy(  
        PrincipalPolicy.WindowsPrincipal);  
    ```  
  
    ```vb  
    AppDomain.CurrentDomain.SetPrincipalPolicy( _  
        PrincipalPolicy.WindowsPrincipal)  
    ```  
  
2. <span data-ttu-id="2dd3c-112">Pomocí sady zásad použijte statickou <xref:System.Threading.Thread.CurrentPrincipal%2A?displayProperty=nameWithType> vlastnost k načtení objektu zabezpečení, který zapouzdřuje aktuálního uživatele systému Windows.</span><span class="sxs-lookup"><span data-stu-id="2dd3c-112">With the policy set, use the static <xref:System.Threading.Thread.CurrentPrincipal%2A?displayProperty=nameWithType> property to retrieve the principal that encapsulates the current Windows user.</span></span> <span data-ttu-id="2dd3c-113">Vzhledem k tomu, že návratový typ vlastnosti je <xref:System.Security.Principal.IPrincipal> , musíte přetypovat výsledek na <xref:System.Security.Principal.WindowsPrincipal> typ.</span><span class="sxs-lookup"><span data-stu-id="2dd3c-113">Because the property return type is <xref:System.Security.Principal.IPrincipal>, you must cast the result to a <xref:System.Security.Principal.WindowsPrincipal> type.</span></span> <span data-ttu-id="2dd3c-114">Následující kód inicializuje nový <xref:System.Security.Principal.WindowsPrincipal> objekt na hodnotu objektu zabezpečení přidruženého k aktuálnímu vláknu.</span><span class="sxs-lookup"><span data-stu-id="2dd3c-114">The following code initializes a new <xref:System.Security.Principal.WindowsPrincipal> object to the value of the principal associated with the current thread.</span></span>  
  
    ```csharp  
    WindowsPrincipal myPrincipal =
        (WindowsPrincipal) Thread.CurrentPrincipal;  
    ```  
  
    ```vb  
    Dim myPrincipal As WindowsPrincipal = _  
        CType(Thread.CurrentPrincipal, WindowsPrincipal)
    ```  
  
3. <span data-ttu-id="2dd3c-115">Po vytvoření objektu zabezpečení můžete použít některou z několika metod k jeho ověření.</span><span class="sxs-lookup"><span data-stu-id="2dd3c-115">When the principal object has been created, you can use one of several methods to validate it.</span></span>  
  
### <a name="to-create-a-windowsprincipal-object-for-a-single-validation"></a><span data-ttu-id="2dd3c-116">Vytvoření objektu WindowsPrincipal pro jedno ověření</span><span class="sxs-lookup"><span data-stu-id="2dd3c-116">To create a WindowsPrincipal object for a single validation</span></span>  
  
1. <span data-ttu-id="2dd3c-117">Inicializujte nový <xref:System.Security.Principal.WindowsIdentity> objekt voláním statické <xref:System.Security.Principal.WindowsIdentity.GetCurrent%2A?displayProperty=nameWithType> metody, která se dotazuje na aktuální účet systému Windows a umístí informace o tomto účtu do nově vytvořeného objektu identity.</span><span class="sxs-lookup"><span data-stu-id="2dd3c-117">Initialize a new <xref:System.Security.Principal.WindowsIdentity> object by calling the static <xref:System.Security.Principal.WindowsIdentity.GetCurrent%2A?displayProperty=nameWithType> method, which queries the current Windows account and places information about that account into the newly created identity object.</span></span> <span data-ttu-id="2dd3c-118">Následující kód vytvoří nový <xref:System.Security.Principal.WindowsIdentity> objekt a inicializuje jej na aktuálně ověřeného uživatele.</span><span class="sxs-lookup"><span data-stu-id="2dd3c-118">The following code creates a new <xref:System.Security.Principal.WindowsIdentity> object and initializes it to the current authenticated user.</span></span>  
  
    ```csharp  
    WindowsIdentity myIdentity = WindowsIdentity.GetCurrent();  
    ```  
  
    ```vb  
    Dim myIdentity As WindowsIdentity = WindowsIdentity.GetCurrent()  
    ```  
  
2. <span data-ttu-id="2dd3c-119">Vytvořte nový <xref:System.Security.Principal.WindowsPrincipal> objekt a předejte mu hodnotu <xref:System.Security.Principal.WindowsIdentity> objektu vytvořeného v předchozím kroku.</span><span class="sxs-lookup"><span data-stu-id="2dd3c-119">Create a new <xref:System.Security.Principal.WindowsPrincipal> object and pass it the value of the <xref:System.Security.Principal.WindowsIdentity> object created in the preceding step.</span></span>  
  
    ```csharp  
    WindowsPrincipal myPrincipal = new WindowsPrincipal(myIdentity);  
    ```  
  
    ```vb  
    Dim myPrincipal As New WindowsPrincipal(myIdentity)  
    ```  
  
3. <span data-ttu-id="2dd3c-120">Po vytvoření objektu zabezpečení můžete použít některou z několika metod k jeho ověření.</span><span class="sxs-lookup"><span data-stu-id="2dd3c-120">When the principal object has been created, you can use one of several methods to validate it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2dd3c-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="2dd3c-121">See also</span></span>

- [<span data-ttu-id="2dd3c-122">Objekty zabezpečení a identity</span><span class="sxs-lookup"><span data-stu-id="2dd3c-122">Principal and Identity Objects</span></span>](principal-and-identity-objects.md)
- [<span data-ttu-id="2dd3c-123">ASP.NET Core zabezpečení</span><span class="sxs-lookup"><span data-stu-id="2dd3c-123">ASP.NET Core Security</span></span>](https://docs.microsoft.com/aspnet/core/security/)
