---
title: ServiceAuthorizationBehavior
ms.date: 03/30/2017
ms.assetid: 77dad8e8-fea4-4d1c-b366-2f01a2a87f78
ms.openlocfilehash: e03f83927ec5aef7f916b2262c9c8cff1db68ac9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33486470"
---
# <a name="serviceauthorizationbehavior"></a><span data-ttu-id="a83f8-102">ServiceAuthorizationBehavior</span><span class="sxs-lookup"><span data-stu-id="a83f8-102">ServiceAuthorizationBehavior</span></span>
<span data-ttu-id="a83f8-103">ServiceAuthorizationBehavior</span><span class="sxs-lookup"><span data-stu-id="a83f8-103">ServiceAuthorizationBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a83f8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a83f8-104">Syntax</span></span>  
  
```  
class ServiceAuthorizationBehavior : Behavior  
{  
  boolean ImpersonateCallerForAllOperations;  
  string PrincipalPermissionMode;  
  string RoleProvider;  
  string ServiceAuthorizationManager;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="a83f8-105">Metody</span><span class="sxs-lookup"><span data-stu-id="a83f8-105">Methods</span></span>  
 <span data-ttu-id="a83f8-106">Třída ServiceAuthorizationBehavior nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="a83f8-106">The ServiceAuthorizationBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="a83f8-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="a83f8-107">Properties</span></span>  
 <span data-ttu-id="a83f8-108">Třída ServiceAuthorizationBehavior má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="a83f8-108">The ServiceAuthorizationBehavior class has the following properties:</span></span>  
  
### <a name="impersonatecallerforalloperations"></a><span data-ttu-id="a83f8-109">impersonateCallerForAllOperations</span><span class="sxs-lookup"><span data-stu-id="a83f8-109">ImpersonateCallerForAllOperations</span></span>  
 <span data-ttu-id="a83f8-110">Datový typ: logická hodnota</span><span class="sxs-lookup"><span data-stu-id="a83f8-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="a83f8-111">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="a83f8-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a83f8-112">Hodnota, která určuje, zda se služba pokusí zosobnit pomocí přihlašovacích údajů zadaných příchozí zprávy.</span><span class="sxs-lookup"><span data-stu-id="a83f8-112">A value that controls whether the service attempts to impersonate using the credentials provided by the incoming message.</span></span>  
  
### <a name="principalpermissionmode"></a><span data-ttu-id="a83f8-113">PrincipalPermissionMode</span><span class="sxs-lookup"><span data-stu-id="a83f8-113">PrincipalPermissionMode</span></span>  
 <span data-ttu-id="a83f8-114">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="a83f8-114">Data type: string</span></span>  
  
 <span data-ttu-id="a83f8-115">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="a83f8-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a83f8-116">Objekt používá k provádění operací na serveru.</span><span class="sxs-lookup"><span data-stu-id="a83f8-116">The principal used to carry out operations on the server.</span></span>  
  
### <a name="roleprovider"></a><span data-ttu-id="a83f8-117">RoleProvider</span><span class="sxs-lookup"><span data-stu-id="a83f8-117">RoleProvider</span></span>  
 <span data-ttu-id="a83f8-118">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="a83f8-118">Data type: string</span></span>  
  
 <span data-ttu-id="a83f8-119">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="a83f8-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a83f8-120">Název poskytovatele rolí prostředí ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="a83f8-120">The name of the ASP.NET role provider.</span></span>  
  
### <a name="serviceauthorizationmanager"></a><span data-ttu-id="a83f8-121">ServiceAuthorizationManager</span><span class="sxs-lookup"><span data-stu-id="a83f8-121">ServiceAuthorizationManager</span></span>  
 <span data-ttu-id="a83f8-122">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="a83f8-122">Data type: string</span></span>  
  
 <span data-ttu-id="a83f8-123">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="a83f8-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a83f8-124">Správce autorizací, použít pro vlastní ověřování.</span><span class="sxs-lookup"><span data-stu-id="a83f8-124">The authorization manager used for custom authorization.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a83f8-125">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a83f8-125">Requirements</span></span>  
  
|<span data-ttu-id="a83f8-126">MOF</span><span class="sxs-lookup"><span data-stu-id="a83f8-126">MOF</span></span>|<span data-ttu-id="a83f8-127">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="a83f8-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="a83f8-128">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="a83f8-128">Namespace</span></span>|<span data-ttu-id="a83f8-129">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="a83f8-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a83f8-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="a83f8-130">See Also</span></span>  
 <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>
