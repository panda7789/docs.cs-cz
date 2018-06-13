---
title: ServiceSecurityAuditBehavior
ms.date: 03/30/2017
ms.assetid: 2c5809e7-5364-44ce-bc71-848be4672e2a
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 3adc721dd8ad0fb706e172373e5da70fe6032db6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33485892"
---
# <a name="servicesecurityauditbehavior"></a><span data-ttu-id="7eb29-102">ServiceSecurityAuditBehavior</span><span class="sxs-lookup"><span data-stu-id="7eb29-102">ServiceSecurityAuditBehavior</span></span>
<span data-ttu-id="7eb29-103">ServiceSecurityAuditBehavior</span><span class="sxs-lookup"><span data-stu-id="7eb29-103">ServiceSecurityAuditBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7eb29-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7eb29-104">Syntax</span></span>  
  
```  
class ServiceSecurityAuditBehavior : Behavior  
{  
  string AuditLogLocation;  
  string MessageAuthenticationAuditLevel;  
  string ServiceAuthorizationAuditLevel;  
  boolean SuppressAuditFailure;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="7eb29-105">Metody</span><span class="sxs-lookup"><span data-stu-id="7eb29-105">Methods</span></span>  
 <span data-ttu-id="7eb29-106">Třída ServiceSecurityAuditBehavior nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="7eb29-106">The ServiceSecurityAuditBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="7eb29-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="7eb29-107">Properties</span></span>  
 <span data-ttu-id="7eb29-108">Třída ServiceSecurityAuditBehavior má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="7eb29-108">The ServiceSecurityAuditBehavior class has the following properties:</span></span>  
  
### <a name="auditloglocation"></a><span data-ttu-id="7eb29-109">auditLogLocation</span><span class="sxs-lookup"><span data-stu-id="7eb29-109">AuditLogLocation</span></span>  
 <span data-ttu-id="7eb29-110">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="7eb29-110">Data type: string</span></span>  
  
 <span data-ttu-id="7eb29-111">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="7eb29-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="7eb29-112">Umístění protokolu auditu.</span><span class="sxs-lookup"><span data-stu-id="7eb29-112">The location of the audit log.</span></span>  
  
### <a name="messageauthenticationauditlevel"></a><span data-ttu-id="7eb29-113">messageAuthenticationAuditLevel</span><span class="sxs-lookup"><span data-stu-id="7eb29-113">MessageAuthenticationAuditLevel</span></span>  
 <span data-ttu-id="7eb29-114">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="7eb29-114">Data type: string</span></span>  
  
 <span data-ttu-id="7eb29-115">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="7eb29-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="7eb29-116">Typ zprávy úroveň ověřování, která se používá k protokolování událostí auditu.</span><span class="sxs-lookup"><span data-stu-id="7eb29-116">The type of message authentication level that is used to log audit events.</span></span>  
  
### <a name="serviceauthorizationauditlevel"></a><span data-ttu-id="7eb29-117">serviceAuthorizationAuditLevel</span><span class="sxs-lookup"><span data-stu-id="7eb29-117">ServiceAuthorizationAuditLevel</span></span>  
 <span data-ttu-id="7eb29-118">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="7eb29-118">Data type: string</span></span>  
  
 <span data-ttu-id="7eb29-119">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="7eb29-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="7eb29-120">Typy událostí autorizace, které se zaznamenávají v protokolu auditu.</span><span class="sxs-lookup"><span data-stu-id="7eb29-120">The types of authorization events that are recorded in the audit log.</span></span>  
  
### <a name="suppressauditfailure"></a><span data-ttu-id="7eb29-121">suppressAuditFailure</span><span class="sxs-lookup"><span data-stu-id="7eb29-121">SuppressAuditFailure</span></span>  
 <span data-ttu-id="7eb29-122">Datový typ: logická hodnota</span><span class="sxs-lookup"><span data-stu-id="7eb29-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="7eb29-123">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="7eb29-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="7eb29-124">Logická hodnota, která určuje chování pro potlačení chyb při zápisu do protokolu auditování.</span><span class="sxs-lookup"><span data-stu-id="7eb29-124">A boolean value that specifies the behavior for suppressing failures of writing to the audit log.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7eb29-125">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7eb29-125">Requirements</span></span>  
  
|<span data-ttu-id="7eb29-126">MOF</span><span class="sxs-lookup"><span data-stu-id="7eb29-126">MOF</span></span>|<span data-ttu-id="7eb29-127">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="7eb29-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="7eb29-128">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="7eb29-128">Namespace</span></span>|<span data-ttu-id="7eb29-129">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="7eb29-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7eb29-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="7eb29-130">See Also</span></span>  
 <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior>
