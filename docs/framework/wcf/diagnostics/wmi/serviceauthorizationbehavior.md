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
ms.openlocfilehash: fd22cd7e7783a67e7ad10371533eee680bd3af16
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="serviceauthorizationbehavior"></a><span data-ttu-id="974fd-102">ServiceAuthorizationBehavior</span><span class="sxs-lookup"><span data-stu-id="974fd-102">ServiceAuthorizationBehavior</span></span>
<span data-ttu-id="974fd-103">ServiceAuthorizationBehavior</span><span class="sxs-lookup"><span data-stu-id="974fd-103">ServiceAuthorizationBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="974fd-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="974fd-104">Syntax</span></span>  
  
```  
class ServiceAuthorizationBehavior : Behavior  
{  
  boolean ImpersonateCallerForAllOperations;  
  string PrincipalPermissionMode;  
  string RoleProvider;  
  string ServiceAuthorizationManager;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="974fd-105">Metody</span><span class="sxs-lookup"><span data-stu-id="974fd-105">Methods</span></span>  
 <span data-ttu-id="974fd-106">Třída ServiceAuthorizationBehavior nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="974fd-106">The ServiceAuthorizationBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="974fd-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="974fd-107">Properties</span></span>  
 <span data-ttu-id="974fd-108">Třída ServiceAuthorizationBehavior má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="974fd-108">The ServiceAuthorizationBehavior class has the following properties:</span></span>  
  
### <a name="impersonatecallerforalloperations"></a><span data-ttu-id="974fd-109">impersonateCallerForAllOperations</span><span class="sxs-lookup"><span data-stu-id="974fd-109">ImpersonateCallerForAllOperations</span></span>  
 <span data-ttu-id="974fd-110">Datový typ: logická hodnota</span><span class="sxs-lookup"><span data-stu-id="974fd-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="974fd-111">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="974fd-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="974fd-112">Hodnota, která určuje, zda se služba pokusí zosobnit pomocí přihlašovacích údajů zadaných příchozí zprávy.</span><span class="sxs-lookup"><span data-stu-id="974fd-112">A value that controls whether the service attempts to impersonate using the credentials provided by the incoming message.</span></span>  
  
### <a name="principalpermissionmode"></a><span data-ttu-id="974fd-113">PrincipalPermissionMode</span><span class="sxs-lookup"><span data-stu-id="974fd-113">PrincipalPermissionMode</span></span>  
 <span data-ttu-id="974fd-114">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="974fd-114">Data type: string</span></span>  
  
 <span data-ttu-id="974fd-115">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="974fd-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="974fd-116">Objekt používá k provádění operací na serveru.</span><span class="sxs-lookup"><span data-stu-id="974fd-116">The principal used to carry out operations on the server.</span></span>  
  
### <a name="roleprovider"></a><span data-ttu-id="974fd-117">RoleProvider</span><span class="sxs-lookup"><span data-stu-id="974fd-117">RoleProvider</span></span>  
 <span data-ttu-id="974fd-118">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="974fd-118">Data type: string</span></span>  
  
 <span data-ttu-id="974fd-119">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="974fd-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="974fd-120">Název poskytovatele rolí prostředí ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="974fd-120">The name of the ASP.NET role provider.</span></span>  
  
### <a name="serviceauthorizationmanager"></a><span data-ttu-id="974fd-121">ServiceAuthorizationManager</span><span class="sxs-lookup"><span data-stu-id="974fd-121">ServiceAuthorizationManager</span></span>  
 <span data-ttu-id="974fd-122">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="974fd-122">Data type: string</span></span>  
  
 <span data-ttu-id="974fd-123">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="974fd-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="974fd-124">Správce autorizací, použít pro vlastní ověřování.</span><span class="sxs-lookup"><span data-stu-id="974fd-124">The authorization manager used for custom authorization.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="974fd-125">Požadavky</span><span class="sxs-lookup"><span data-stu-id="974fd-125">Requirements</span></span>  
  
|<span data-ttu-id="974fd-126">MOF</span><span class="sxs-lookup"><span data-stu-id="974fd-126">MOF</span></span>|<span data-ttu-id="974fd-127">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="974fd-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="974fd-128">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="974fd-128">Namespace</span></span>|<span data-ttu-id="974fd-129">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="974fd-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="974fd-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="974fd-130">See Also</span></span>  
 <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>
