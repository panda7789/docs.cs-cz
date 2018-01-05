---
title: ServiceSecurityAuditBehavior
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2c5809e7-5364-44ce-bc71-848be4672e2a
caps.latest.revision: "8"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: ea9c04c201ff022fcea54b81a998b7020fb2a836
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="servicesecurityauditbehavior"></a><span data-ttu-id="4ac46-102">ServiceSecurityAuditBehavior</span><span class="sxs-lookup"><span data-stu-id="4ac46-102">ServiceSecurityAuditBehavior</span></span>
<span data-ttu-id="4ac46-103">ServiceSecurityAuditBehavior</span><span class="sxs-lookup"><span data-stu-id="4ac46-103">ServiceSecurityAuditBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4ac46-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4ac46-104">Syntax</span></span>  
  
```  
class ServiceSecurityAuditBehavior : Behavior  
{  
  string AuditLogLocation;  
  string MessageAuthenticationAuditLevel;  
  string ServiceAuthorizationAuditLevel;  
  boolean SuppressAuditFailure;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="4ac46-105">Metody</span><span class="sxs-lookup"><span data-stu-id="4ac46-105">Methods</span></span>  
 <span data-ttu-id="4ac46-106">Třída ServiceSecurityAuditBehavior nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="4ac46-106">The ServiceSecurityAuditBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="4ac46-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="4ac46-107">Properties</span></span>  
 <span data-ttu-id="4ac46-108">Třída ServiceSecurityAuditBehavior má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="4ac46-108">The ServiceSecurityAuditBehavior class has the following properties:</span></span>  
  
### <a name="auditloglocation"></a><span data-ttu-id="4ac46-109">auditLogLocation</span><span class="sxs-lookup"><span data-stu-id="4ac46-109">AuditLogLocation</span></span>  
 <span data-ttu-id="4ac46-110">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="4ac46-110">Data type: string</span></span>  
  
 <span data-ttu-id="4ac46-111">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="4ac46-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4ac46-112">Umístění protokolu auditu.</span><span class="sxs-lookup"><span data-stu-id="4ac46-112">The location of the audit log.</span></span>  
  
### <a name="messageauthenticationauditlevel"></a><span data-ttu-id="4ac46-113">messageAuthenticationAuditLevel</span><span class="sxs-lookup"><span data-stu-id="4ac46-113">MessageAuthenticationAuditLevel</span></span>  
 <span data-ttu-id="4ac46-114">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="4ac46-114">Data type: string</span></span>  
  
 <span data-ttu-id="4ac46-115">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="4ac46-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4ac46-116">Typ zprávy úroveň ověřování, která se používá k protokolování událostí auditu.</span><span class="sxs-lookup"><span data-stu-id="4ac46-116">The type of message authentication level that is used to log audit events.</span></span>  
  
### <a name="serviceauthorizationauditlevel"></a><span data-ttu-id="4ac46-117">serviceAuthorizationAuditLevel</span><span class="sxs-lookup"><span data-stu-id="4ac46-117">ServiceAuthorizationAuditLevel</span></span>  
 <span data-ttu-id="4ac46-118">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="4ac46-118">Data type: string</span></span>  
  
 <span data-ttu-id="4ac46-119">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="4ac46-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4ac46-120">Typy událostí autorizace, které se zaznamenávají v protokolu auditu.</span><span class="sxs-lookup"><span data-stu-id="4ac46-120">The types of authorization events that are recorded in the audit log.</span></span>  
  
### <a name="suppressauditfailure"></a><span data-ttu-id="4ac46-121">suppressAuditFailure</span><span class="sxs-lookup"><span data-stu-id="4ac46-121">SuppressAuditFailure</span></span>  
 <span data-ttu-id="4ac46-122">Datový typ: logická hodnota</span><span class="sxs-lookup"><span data-stu-id="4ac46-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="4ac46-123">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="4ac46-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4ac46-124">Logická hodnota, která určuje chování pro potlačení chyb při zápisu do protokolu auditování.</span><span class="sxs-lookup"><span data-stu-id="4ac46-124">A boolean value that specifies the behavior for suppressing failures of writing to the audit log.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4ac46-125">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4ac46-125">Requirements</span></span>  
  
|<span data-ttu-id="4ac46-126">MOF</span><span class="sxs-lookup"><span data-stu-id="4ac46-126">MOF</span></span>|<span data-ttu-id="4ac46-127">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="4ac46-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="4ac46-128">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="4ac46-128">Namespace</span></span>|<span data-ttu-id="4ac46-129">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="4ac46-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4ac46-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="4ac46-130">See Also</span></span>  
 <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior>
