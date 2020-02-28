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
ms.openlocfilehash: 30af18b7d7b86621586c7da66eda1b37356d5565
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2020
ms.locfileid: "78159777"
---
# <a name="how-to-create-a-windowsprincipal-object"></a><span data-ttu-id="61475-102">Postupy: Vytvoření objektu WindowsPrincipal</span><span class="sxs-lookup"><span data-stu-id="61475-102">How to: Create a WindowsPrincipal Object</span></span>
<span data-ttu-id="61475-103">Existují dva způsoby, jak vytvořit objekt <xref:System.Security.Principal.WindowsPrincipal>, v závislosti na tom, zda kód musí opakovaně provádět ověřování na základě rolí, nebo musí být proveden pouze jednou.</span><span class="sxs-lookup"><span data-stu-id="61475-103">There are two ways to create a <xref:System.Security.Principal.WindowsPrincipal> object, depending on whether code must repeatedly perform role-based validation or must perform it only once.</span></span>  
  
 <span data-ttu-id="61475-104">Pokud kód musí opakovaně provádět ověřování na základě rolí, pak první z následujících postupů vytvoří méně režijních nákladů.</span><span class="sxs-lookup"><span data-stu-id="61475-104">If code must repeatedly perform role-based validation, the first of the following procedures produces less overhead.</span></span> <span data-ttu-id="61475-105">Pokud kód musí učinit ověřování na základě role pouze jednou, můžete vytvořit objekt <xref:System.Security.Principal.WindowsPrincipal> pomocí druhého z následujících postupů.</span><span class="sxs-lookup"><span data-stu-id="61475-105">When code needs to make role-based validations only once, you can create a <xref:System.Security.Principal.WindowsPrincipal> object by using the second of the following procedures.</span></span>  
  
### <a name="to-create-a-windowsprincipal-object-for-repeated-validation"></a><span data-ttu-id="61475-106">Vytvoření objektu WindowsPrincipal pro opakované ověření</span><span class="sxs-lookup"><span data-stu-id="61475-106">To create a WindowsPrincipal object for repeated validation</span></span>  
  
1. <span data-ttu-id="61475-107">Zavolejte metodu <xref:System.AppDomain.SetPrincipalPolicy%2A> u objektu <xref:System.AppDomain>, který je vrácený vlastností static <xref:System.AppDomain.CurrentDomain%2A?displayProperty=nameWithType>, předáním metody <xref:System.Security.Principal.PrincipalPolicy> hodnotu výčtu, která indikuje, co by mělo být nové zásady.</span><span class="sxs-lookup"><span data-stu-id="61475-107">Call the <xref:System.AppDomain.SetPrincipalPolicy%2A> method on the <xref:System.AppDomain> object that is returned by the static <xref:System.AppDomain.CurrentDomain%2A?displayProperty=nameWithType> property, passing the method a <xref:System.Security.Principal.PrincipalPolicy> enumeration value that indicates what the new policy should be.</span></span> <span data-ttu-id="61475-108">Podporované hodnoty jsou <xref:System.Security.Principal.PrincipalPolicy.NoPrincipal>, <xref:System.Security.Principal.PrincipalPolicy.UnauthenticatedPrincipal>a <xref:System.Security.Principal.PrincipalPolicy.WindowsPrincipal>.</span><span class="sxs-lookup"><span data-stu-id="61475-108">Supported values are <xref:System.Security.Principal.PrincipalPolicy.NoPrincipal>, <xref:System.Security.Principal.PrincipalPolicy.UnauthenticatedPrincipal>, and <xref:System.Security.Principal.PrincipalPolicy.WindowsPrincipal>.</span></span> <span data-ttu-id="61475-109">Následující kód demonstruje toto volání metody.</span><span class="sxs-lookup"><span data-stu-id="61475-109">The following code demonstrates this method call.</span></span>  
  
    ```csharp  
    AppDomain.CurrentDomain.SetPrincipalPolicy(  
        PrincipalPolicy.WindowsPrincipal);  
    ```  
  
    ```vb  
    AppDomain.CurrentDomain.SetPrincipalPolicy( _  
        PrincipalPolicy.WindowsPrincipal)  
    ```  
  
2. <span data-ttu-id="61475-110">Pomocí sady zásad použijte vlastnost statického <xref:System.Threading.Thread.CurrentPrincipal%2A?displayProperty=nameWithType> k načtení objektu zabezpečení, který zapouzdřuje aktuálního uživatele systému Windows.</span><span class="sxs-lookup"><span data-stu-id="61475-110">With the policy set, use the static <xref:System.Threading.Thread.CurrentPrincipal%2A?displayProperty=nameWithType> property to retrieve the principal that encapsulates the current Windows user.</span></span> <span data-ttu-id="61475-111">Vzhledem k tomu, že návratový typ vlastnosti je <xref:System.Security.Principal.IPrincipal>, musíte přetypovat výsledek na typ <xref:System.Security.Principal.WindowsPrincipal>.</span><span class="sxs-lookup"><span data-stu-id="61475-111">Because the property return type is <xref:System.Security.Principal.IPrincipal>, you must cast the result to a <xref:System.Security.Principal.WindowsPrincipal> type.</span></span> <span data-ttu-id="61475-112">Následující kód inicializuje nový objekt <xref:System.Security.Principal.WindowsPrincipal> k hodnotě objektu zabezpečení přidruženého k aktuálnímu vláknu.</span><span class="sxs-lookup"><span data-stu-id="61475-112">The following code initializes a new <xref:System.Security.Principal.WindowsPrincipal> object to the value of the principal associated with the current thread.</span></span>  
  
    ```csharp  
    WindowsPrincipal myPrincipal =
        (WindowsPrincipal) Thread.CurrentPrincipal;  
    ```  
  
    ```vb  
    Dim myPrincipal As WindowsPrincipal = _  
        CType(Thread.CurrentPrincipal, WindowsPrincipal)
    ```  
  
3. <span data-ttu-id="61475-113">Po vytvoření objektu zabezpečení můžete použít některou z několika metod k jeho ověření.</span><span class="sxs-lookup"><span data-stu-id="61475-113">When the principal object has been created, you can use one of several methods to validate it.</span></span>  
  
### <a name="to-create-a-windowsprincipal-object-for-a-single-validation"></a><span data-ttu-id="61475-114">Vytvoření objektu WindowsPrincipal pro jedno ověření</span><span class="sxs-lookup"><span data-stu-id="61475-114">To create a WindowsPrincipal object for a single validation</span></span>  
  
1. <span data-ttu-id="61475-115">Inicializujte nový objekt <xref:System.Security.Principal.WindowsIdentity> voláním statické metody <xref:System.Security.Principal.WindowsIdentity.GetCurrent%2A?displayProperty=nameWithType>, která se dotazuje na aktuální účet systému Windows a umístí informace o tomto účtu do nově vytvořeného objektu identity.</span><span class="sxs-lookup"><span data-stu-id="61475-115">Initialize a new <xref:System.Security.Principal.WindowsIdentity> object by calling the static <xref:System.Security.Principal.WindowsIdentity.GetCurrent%2A?displayProperty=nameWithType> method, which queries the current Windows account and places information about that account into the newly created identity object.</span></span> <span data-ttu-id="61475-116">Následující kód vytvoří nový objekt <xref:System.Security.Principal.WindowsIdentity> a inicializuje jej na aktuálně ověřeného uživatele.</span><span class="sxs-lookup"><span data-stu-id="61475-116">The following code creates a new <xref:System.Security.Principal.WindowsIdentity> object and initializes it to the current authenticated user.</span></span>  
  
    ```csharp  
    WindowsIdentity myIdentity = WindowsIdentity.GetCurrent();  
    ```  
  
    ```vb  
    Dim myIdentity As WindowsIdentity = WindowsIdentity.GetCurrent()  
    ```  
  
2. <span data-ttu-id="61475-117">Vytvořte nový objekt <xref:System.Security.Principal.WindowsPrincipal> a předejte mu hodnotu objektu <xref:System.Security.Principal.WindowsIdentity> vytvořeného v předchozím kroku.</span><span class="sxs-lookup"><span data-stu-id="61475-117">Create a new <xref:System.Security.Principal.WindowsPrincipal> object and pass it the value of the <xref:System.Security.Principal.WindowsIdentity> object created in the preceding step.</span></span>  
  
    ```csharp  
    WindowsPrincipal myPrincipal = new WindowsPrincipal(myIdentity);  
    ```  
  
    ```vb  
    Dim myPrincipal As New WindowsPrincipal(myIdentity)  
    ```  
  
3. <span data-ttu-id="61475-118">Po vytvoření objektu zabezpečení můžete použít některou z několika metod k jeho ověření.</span><span class="sxs-lookup"><span data-stu-id="61475-118">When the principal object has been created, you can use one of several methods to validate it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61475-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="61475-119">See also</span></span>

- [<span data-ttu-id="61475-120">Objekty zabezpečení a identity</span><span class="sxs-lookup"><span data-stu-id="61475-120">Principal and Identity Objects</span></span>](../../../docs/standard/security/principal-and-identity-objects.md)
