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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: eb02a02557a88bf53ca1a8e5b30fe66d6995e545
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="serviceauthorizationbehavior"></a><span data-ttu-id="606df-102">ServiceAuthorizationBehavior</span><span class="sxs-lookup"><span data-stu-id="606df-102">ServiceAuthorizationBehavior</span></span>
<span data-ttu-id="606df-103">ServiceAuthorizationBehavior</span><span class="sxs-lookup"><span data-stu-id="606df-103">ServiceAuthorizationBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="606df-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="606df-104">Syntax</span></span>  
  
```  
class ServiceAuthorizationBehavior : Behavior  
{  
  boolean ImpersonateCallerForAllOperations;  
  string PrincipalPermissionMode;  
  string RoleProvider;  
  string ServiceAuthorizationManager;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="606df-105">Metody</span><span class="sxs-lookup"><span data-stu-id="606df-105">Methods</span></span>  
 <span data-ttu-id="606df-106">Třída ServiceAuthorizationBehavior nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="606df-106">The ServiceAuthorizationBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="606df-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="606df-107">Properties</span></span>  
 <span data-ttu-id="606df-108">Třída ServiceAuthorizationBehavior má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="606df-108">The ServiceAuthorizationBehavior class has the following properties:</span></span>  
  
### <a name="impersonatecallerforalloperations"></a><span data-ttu-id="606df-109">impersonateCallerForAllOperations</span><span class="sxs-lookup"><span data-stu-id="606df-109">ImpersonateCallerForAllOperations</span></span>  
 <span data-ttu-id="606df-110">Datový typ: logická hodnota</span><span class="sxs-lookup"><span data-stu-id="606df-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="606df-111">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="606df-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="606df-112">Hodnota, která určuje, zda se služba pokusí zosobnit pomocí přihlašovacích údajů zadaných příchozí zprávy.</span><span class="sxs-lookup"><span data-stu-id="606df-112">A value that controls whether the service attempts to impersonate using the credentials provided by the incoming message.</span></span>  
  
### <a name="principalpermissionmode"></a><span data-ttu-id="606df-113">PrincipalPermissionMode</span><span class="sxs-lookup"><span data-stu-id="606df-113">PrincipalPermissionMode</span></span>  
 <span data-ttu-id="606df-114">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="606df-114">Data type: string</span></span>  
  
 <span data-ttu-id="606df-115">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="606df-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="606df-116">Objekt používá k provádění operací na serveru.</span><span class="sxs-lookup"><span data-stu-id="606df-116">The principal used to carry out operations on the server.</span></span>  
  
### <a name="roleprovider"></a><span data-ttu-id="606df-117">RoleProvider</span><span class="sxs-lookup"><span data-stu-id="606df-117">RoleProvider</span></span>  
 <span data-ttu-id="606df-118">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="606df-118">Data type: string</span></span>  
  
 <span data-ttu-id="606df-119">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="606df-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="606df-120">Název poskytovatele rolí prostředí ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="606df-120">The name of the ASP.NET role provider.</span></span>  
  
### <a name="serviceauthorizationmanager"></a><span data-ttu-id="606df-121">ServiceAuthorizationManager</span><span class="sxs-lookup"><span data-stu-id="606df-121">ServiceAuthorizationManager</span></span>  
 <span data-ttu-id="606df-122">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="606df-122">Data type: string</span></span>  
  
 <span data-ttu-id="606df-123">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="606df-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="606df-124">Správce autorizací, použít pro vlastní ověřování.</span><span class="sxs-lookup"><span data-stu-id="606df-124">The authorization manager used for custom authorization.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="606df-125">Požadavky</span><span class="sxs-lookup"><span data-stu-id="606df-125">Requirements</span></span>  
  
|<span data-ttu-id="606df-126">MOF</span><span class="sxs-lookup"><span data-stu-id="606df-126">MOF</span></span>|<span data-ttu-id="606df-127">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="606df-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="606df-128">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="606df-128">Namespace</span></span>|<span data-ttu-id="606df-129">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="606df-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="606df-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="606df-130">See Also</span></span>  
 <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>
