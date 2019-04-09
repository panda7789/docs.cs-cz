---
title: ServiceAuthorizationBehavior
ms.date: 03/30/2017
ms.assetid: 77dad8e8-fea4-4d1c-b366-2f01a2a87f78
ms.openlocfilehash: 51555e3357b8c33a53261c4894d97798b0a05656
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59102931"
---
# <a name="serviceauthorizationbehavior"></a><span data-ttu-id="ebfee-102">ServiceAuthorizationBehavior</span><span class="sxs-lookup"><span data-stu-id="ebfee-102">ServiceAuthorizationBehavior</span></span>
<span data-ttu-id="ebfee-103">ServiceAuthorizationBehavior</span><span class="sxs-lookup"><span data-stu-id="ebfee-103">ServiceAuthorizationBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ebfee-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ebfee-104">Syntax</span></span>  
  
```csharp
class ServiceAuthorizationBehavior : Behavior  
{  
  boolean ImpersonateCallerForAllOperations;  
  string PrincipalPermissionMode;  
  string RoleProvider;  
  string ServiceAuthorizationManager;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="ebfee-105">Metody</span><span class="sxs-lookup"><span data-stu-id="ebfee-105">Methods</span></span>  
 <span data-ttu-id="ebfee-106">Třída ServiceAuthorizationBehavior nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="ebfee-106">The ServiceAuthorizationBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="ebfee-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="ebfee-107">Properties</span></span>  
 <span data-ttu-id="ebfee-108">Třída ServiceAuthorizationBehavior má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="ebfee-108">The ServiceAuthorizationBehavior class has the following properties:</span></span>  
  
### <a name="impersonatecallerforalloperations"></a><span data-ttu-id="ebfee-109">ImpersonateCallerForAllOperations</span><span class="sxs-lookup"><span data-stu-id="ebfee-109">ImpersonateCallerForAllOperations</span></span>  
 <span data-ttu-id="ebfee-110">Datový typ: boolean</span><span class="sxs-lookup"><span data-stu-id="ebfee-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="ebfee-111">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="ebfee-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ebfee-112">Hodnota, která určuje, zda se služba pokusí o zosobnění s použitím pověření poskytnutých příchozí zprávy.</span><span class="sxs-lookup"><span data-stu-id="ebfee-112">A value that controls whether the service attempts to impersonate using the credentials provided by the incoming message.</span></span>  
  
### <a name="principalpermissionmode"></a><span data-ttu-id="ebfee-113">PrincipalPermissionMode</span><span class="sxs-lookup"><span data-stu-id="ebfee-113">PrincipalPermissionMode</span></span>  
 <span data-ttu-id="ebfee-114">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="ebfee-114">Data type: string</span></span>  
  
 <span data-ttu-id="ebfee-115">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="ebfee-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ebfee-116">Objekt zabezpečení použitý k provádění operací na serveru.</span><span class="sxs-lookup"><span data-stu-id="ebfee-116">The principal used to carry out operations on the server.</span></span>  
  
### <a name="roleprovider"></a><span data-ttu-id="ebfee-117">RoleProvider</span><span class="sxs-lookup"><span data-stu-id="ebfee-117">RoleProvider</span></span>  
 <span data-ttu-id="ebfee-118">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="ebfee-118">Data type: string</span></span>  
  
 <span data-ttu-id="ebfee-119">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="ebfee-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ebfee-120">Název poskytovatele rolí prostředí ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="ebfee-120">The name of the ASP.NET role provider.</span></span>  
  
### <a name="serviceauthorizationmanager"></a><span data-ttu-id="ebfee-121">ServiceAuthorizationManager</span><span class="sxs-lookup"><span data-stu-id="ebfee-121">ServiceAuthorizationManager</span></span>  
 <span data-ttu-id="ebfee-122">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="ebfee-122">Data type: string</span></span>  
  
 <span data-ttu-id="ebfee-123">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="ebfee-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ebfee-124">Správce autorizace použitý pro autorizace.</span><span class="sxs-lookup"><span data-stu-id="ebfee-124">The authorization manager used for custom authorization.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ebfee-125">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ebfee-125">Requirements</span></span>  
  
|<span data-ttu-id="ebfee-126">SOUBOR MOF</span><span class="sxs-lookup"><span data-stu-id="ebfee-126">MOF</span></span>|<span data-ttu-id="ebfee-127">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="ebfee-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="ebfee-128">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="ebfee-128">Namespace</span></span>|<span data-ttu-id="ebfee-129">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="ebfee-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ebfee-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ebfee-130">See also</span></span>

- <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>
