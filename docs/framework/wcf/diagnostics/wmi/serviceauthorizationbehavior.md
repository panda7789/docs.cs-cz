---
title: ServiceAuthorizationBehavior
ms.date: 03/30/2017
ms.assetid: 77dad8e8-fea4-4d1c-b366-2f01a2a87f78
ms.openlocfilehash: c916d0820a1eae333384deab7b0619abfbdc8167
ms.sourcegitcommit: 9bd8f213b50f0e1a73e03bd1e840c917fbd6d20a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/26/2018
ms.locfileid: "49415377"
---
# <a name="serviceauthorizationbehavior"></a><span data-ttu-id="a1587-102">ServiceAuthorizationBehavior</span><span class="sxs-lookup"><span data-stu-id="a1587-102">ServiceAuthorizationBehavior</span></span>
<span data-ttu-id="a1587-103">ServiceAuthorizationBehavior</span><span class="sxs-lookup"><span data-stu-id="a1587-103">ServiceAuthorizationBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a1587-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a1587-104">Syntax</span></span>  
  
```csharp
class ServiceAuthorizationBehavior : Behavior  
{  
  boolean ImpersonateCallerForAllOperations;  
  string PrincipalPermissionMode;  
  string RoleProvider;  
  string ServiceAuthorizationManager;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="a1587-105">Metody</span><span class="sxs-lookup"><span data-stu-id="a1587-105">Methods</span></span>  
 <span data-ttu-id="a1587-106">Třída ServiceAuthorizationBehavior nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="a1587-106">The ServiceAuthorizationBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="a1587-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="a1587-107">Properties</span></span>  
 <span data-ttu-id="a1587-108">Třída ServiceAuthorizationBehavior má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="a1587-108">The ServiceAuthorizationBehavior class has the following properties:</span></span>  
  
### <a name="impersonatecallerforalloperations"></a><span data-ttu-id="a1587-109">ImpersonateCallerForAllOperations</span><span class="sxs-lookup"><span data-stu-id="a1587-109">ImpersonateCallerForAllOperations</span></span>  
 <span data-ttu-id="a1587-110">Datový typ: boolean</span><span class="sxs-lookup"><span data-stu-id="a1587-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="a1587-111">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="a1587-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a1587-112">Hodnota, která určuje, zda se služba pokusí o zosobnění s použitím pověření poskytnutých příchozí zprávy.</span><span class="sxs-lookup"><span data-stu-id="a1587-112">A value that controls whether the service attempts to impersonate using the credentials provided by the incoming message.</span></span>  
  
### <a name="principalpermissionmode"></a><span data-ttu-id="a1587-113">PrincipalPermissionMode</span><span class="sxs-lookup"><span data-stu-id="a1587-113">PrincipalPermissionMode</span></span>  
 <span data-ttu-id="a1587-114">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="a1587-114">Data type: string</span></span>  
  
 <span data-ttu-id="a1587-115">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="a1587-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a1587-116">Objekt zabezpečení použitý k provádění operací na serveru.</span><span class="sxs-lookup"><span data-stu-id="a1587-116">The principal used to carry out operations on the server.</span></span>  
  
### <a name="roleprovider"></a><span data-ttu-id="a1587-117">Třída RoleProvider</span><span class="sxs-lookup"><span data-stu-id="a1587-117">RoleProvider</span></span>  
 <span data-ttu-id="a1587-118">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="a1587-118">Data type: string</span></span>  
  
 <span data-ttu-id="a1587-119">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="a1587-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a1587-120">Název poskytovatele rolí prostředí ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="a1587-120">The name of the ASP.NET role provider.</span></span>  
  
### <a name="serviceauthorizationmanager"></a><span data-ttu-id="a1587-121">ServiceAuthorizationManager</span><span class="sxs-lookup"><span data-stu-id="a1587-121">ServiceAuthorizationManager</span></span>  
 <span data-ttu-id="a1587-122">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="a1587-122">Data type: string</span></span>  
  
 <span data-ttu-id="a1587-123">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="a1587-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a1587-124">Správce autorizace použitý pro autorizace.</span><span class="sxs-lookup"><span data-stu-id="a1587-124">The authorization manager used for custom authorization.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a1587-125">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a1587-125">Requirements</span></span>  
  
|<span data-ttu-id="a1587-126">SOUBOR MOF</span><span class="sxs-lookup"><span data-stu-id="a1587-126">MOF</span></span>|<span data-ttu-id="a1587-127">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="a1587-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="a1587-128">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="a1587-128">Namespace</span></span>|<span data-ttu-id="a1587-129">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="a1587-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a1587-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="a1587-130">See Also</span></span>  
 <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>
