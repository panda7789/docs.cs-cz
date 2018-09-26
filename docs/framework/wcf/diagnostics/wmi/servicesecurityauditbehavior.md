---
title: ServiceSecurityAuditBehavior
ms.date: 03/30/2017
ms.assetid: 2c5809e7-5364-44ce-bc71-848be4672e2a
author: BrucePerlerMS
ms.openlocfilehash: 8f43ee752830d95db6bbbdbe311b6d77735e31b5
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/26/2018
ms.locfileid: "47196887"
---
# <a name="servicesecurityauditbehavior"></a><span data-ttu-id="a48e7-102">ServiceSecurityAuditBehavior</span><span class="sxs-lookup"><span data-stu-id="a48e7-102">ServiceSecurityAuditBehavior</span></span>
<span data-ttu-id="a48e7-103">ServiceSecurityAuditBehavior</span><span class="sxs-lookup"><span data-stu-id="a48e7-103">ServiceSecurityAuditBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a48e7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a48e7-104">Syntax</span></span>  
  
```  
class ServiceSecurityAuditBehavior : Behavior  
{  
  string AuditLogLocation;  
  string MessageAuthenticationAuditLevel;  
  string ServiceAuthorizationAuditLevel;  
  boolean SuppressAuditFailure;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="a48e7-105">Metody</span><span class="sxs-lookup"><span data-stu-id="a48e7-105">Methods</span></span>  
 <span data-ttu-id="a48e7-106">Třída ServiceSecurityAuditBehavior nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="a48e7-106">The ServiceSecurityAuditBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="a48e7-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="a48e7-107">Properties</span></span>  
 <span data-ttu-id="a48e7-108">Třída ServiceSecurityAuditBehavior má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="a48e7-108">The ServiceSecurityAuditBehavior class has the following properties:</span></span>  
  
### <a name="auditloglocation"></a><span data-ttu-id="a48e7-109">AuditLogLocation</span><span class="sxs-lookup"><span data-stu-id="a48e7-109">AuditLogLocation</span></span>  
 <span data-ttu-id="a48e7-110">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="a48e7-110">Data type: string</span></span>  
  
 <span data-ttu-id="a48e7-111">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="a48e7-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a48e7-112">Umístění auditovacího protokolu.</span><span class="sxs-lookup"><span data-stu-id="a48e7-112">The location of the audit log.</span></span>  
  
### <a name="messageauthenticationauditlevel"></a><span data-ttu-id="a48e7-113">MessageAuthenticationAuditLevel</span><span class="sxs-lookup"><span data-stu-id="a48e7-113">MessageAuthenticationAuditLevel</span></span>  
 <span data-ttu-id="a48e7-114">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="a48e7-114">Data type: string</span></span>  
  
 <span data-ttu-id="a48e7-115">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="a48e7-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a48e7-116">Typ úrovně ověření zprávy, která se používá k zaznamenání událostí auditu.</span><span class="sxs-lookup"><span data-stu-id="a48e7-116">The type of message authentication level that is used to log audit events.</span></span>  
  
### <a name="serviceauthorizationauditlevel"></a><span data-ttu-id="a48e7-117">ServiceAuthorizationAuditLevel</span><span class="sxs-lookup"><span data-stu-id="a48e7-117">ServiceAuthorizationAuditLevel</span></span>  
 <span data-ttu-id="a48e7-118">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="a48e7-118">Data type: string</span></span>  
  
 <span data-ttu-id="a48e7-119">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="a48e7-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a48e7-120">Typy událostí autorizace, které jsou zaznamenány v protokolu auditu.</span><span class="sxs-lookup"><span data-stu-id="a48e7-120">The types of authorization events that are recorded in the audit log.</span></span>  
  
### <a name="suppressauditfailure"></a><span data-ttu-id="a48e7-121">SuppressAuditFailure</span><span class="sxs-lookup"><span data-stu-id="a48e7-121">SuppressAuditFailure</span></span>  
 <span data-ttu-id="a48e7-122">Datový typ: boolean</span><span class="sxs-lookup"><span data-stu-id="a48e7-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="a48e7-123">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="a48e7-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a48e7-124">Logická hodnota, která určuje vlastnosti pro zamlčené chyby psaní do auditovacího protokolu.</span><span class="sxs-lookup"><span data-stu-id="a48e7-124">A boolean value that specifies the behavior for suppressing failures of writing to the audit log.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a48e7-125">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a48e7-125">Requirements</span></span>  
  
|<span data-ttu-id="a48e7-126">SOUBOR MOF</span><span class="sxs-lookup"><span data-stu-id="a48e7-126">MOF</span></span>|<span data-ttu-id="a48e7-127">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="a48e7-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="a48e7-128">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="a48e7-128">Namespace</span></span>|<span data-ttu-id="a48e7-129">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="a48e7-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a48e7-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="a48e7-130">See Also</span></span>  
 <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior>
