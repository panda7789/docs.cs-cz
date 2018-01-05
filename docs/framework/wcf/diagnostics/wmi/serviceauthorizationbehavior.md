---
title: ServiceAuthorizationBehavior
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 77dad8e8-fea4-4d1c-b366-2f01a2a87f78
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 62f3e32e886f49ac8dde6af5c37a4e57373c9576
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="serviceauthorizationbehavior"></a><span data-ttu-id="259b1-102">ServiceAuthorizationBehavior</span><span class="sxs-lookup"><span data-stu-id="259b1-102">ServiceAuthorizationBehavior</span></span>
<span data-ttu-id="259b1-103">ServiceAuthorizationBehavior</span><span class="sxs-lookup"><span data-stu-id="259b1-103">ServiceAuthorizationBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="259b1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="259b1-104">Syntax</span></span>  
  
```  
class ServiceAuthorizationBehavior : Behavior  
{  
  boolean ImpersonateCallerForAllOperations;  
  string PrincipalPermissionMode;  
  string RoleProvider;  
  string ServiceAuthorizationManager;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="259b1-105">Metody</span><span class="sxs-lookup"><span data-stu-id="259b1-105">Methods</span></span>  
 <span data-ttu-id="259b1-106">Třída ServiceAuthorizationBehavior nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="259b1-106">The ServiceAuthorizationBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="259b1-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="259b1-107">Properties</span></span>  
 <span data-ttu-id="259b1-108">Třída ServiceAuthorizationBehavior má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="259b1-108">The ServiceAuthorizationBehavior class has the following properties:</span></span>  
  
### <a name="impersonatecallerforalloperations"></a><span data-ttu-id="259b1-109">impersonateCallerForAllOperations</span><span class="sxs-lookup"><span data-stu-id="259b1-109">ImpersonateCallerForAllOperations</span></span>  
 <span data-ttu-id="259b1-110">Datový typ: logická hodnota</span><span class="sxs-lookup"><span data-stu-id="259b1-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="259b1-111">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="259b1-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="259b1-112">Hodnota, která určuje, zda se služba pokusí zosobnit pomocí přihlašovacích údajů zadaných příchozí zprávy.</span><span class="sxs-lookup"><span data-stu-id="259b1-112">A value that controls whether the service attempts to impersonate using the credentials provided by the incoming message.</span></span>  
  
### <a name="principalpermissionmode"></a><span data-ttu-id="259b1-113">PrincipalPermissionMode</span><span class="sxs-lookup"><span data-stu-id="259b1-113">PrincipalPermissionMode</span></span>  
 <span data-ttu-id="259b1-114">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="259b1-114">Data type: string</span></span>  
  
 <span data-ttu-id="259b1-115">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="259b1-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="259b1-116">Objekt používá k provádění operací na serveru.</span><span class="sxs-lookup"><span data-stu-id="259b1-116">The principal used to carry out operations on the server.</span></span>  
  
### <a name="roleprovider"></a><span data-ttu-id="259b1-117">RoleProvider</span><span class="sxs-lookup"><span data-stu-id="259b1-117">RoleProvider</span></span>  
 <span data-ttu-id="259b1-118">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="259b1-118">Data type: string</span></span>  
  
 <span data-ttu-id="259b1-119">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="259b1-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="259b1-120">Název poskytovatele rolí prostředí ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="259b1-120">The name of the ASP.NET role provider.</span></span>  
  
### <a name="serviceauthorizationmanager"></a><span data-ttu-id="259b1-121">ServiceAuthorizationManager</span><span class="sxs-lookup"><span data-stu-id="259b1-121">ServiceAuthorizationManager</span></span>  
 <span data-ttu-id="259b1-122">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="259b1-122">Data type: string</span></span>  
  
 <span data-ttu-id="259b1-123">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="259b1-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="259b1-124">Správce autorizací, použít pro vlastní ověřování.</span><span class="sxs-lookup"><span data-stu-id="259b1-124">The authorization manager used for custom authorization.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="259b1-125">Požadavky</span><span class="sxs-lookup"><span data-stu-id="259b1-125">Requirements</span></span>  
  
|<span data-ttu-id="259b1-126">MOF</span><span class="sxs-lookup"><span data-stu-id="259b1-126">MOF</span></span>|<span data-ttu-id="259b1-127">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="259b1-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="259b1-128">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="259b1-128">Namespace</span></span>|<span data-ttu-id="259b1-129">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="259b1-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="259b1-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="259b1-130">See Also</span></span>  
 <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>
