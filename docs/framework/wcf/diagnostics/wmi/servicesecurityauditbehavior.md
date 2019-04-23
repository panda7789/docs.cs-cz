---
title: ServiceSecurityAuditBehavior
ms.date: 03/30/2017
ms.assetid: 2c5809e7-5364-44ce-bc71-848be4672e2a
ms.openlocfilehash: 30679e1f67c6943bf674a6bbd8bf12be090765a8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2019
ms.locfileid: "59979131"
---
# <a name="servicesecurityauditbehavior"></a><span data-ttu-id="d2c9f-102">ServiceSecurityAuditBehavior</span><span class="sxs-lookup"><span data-stu-id="d2c9f-102">ServiceSecurityAuditBehavior</span></span>
<span data-ttu-id="d2c9f-103">ServiceSecurityAuditBehavior</span><span class="sxs-lookup"><span data-stu-id="d2c9f-103">ServiceSecurityAuditBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d2c9f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d2c9f-104">Syntax</span></span>  
  
```csharp  
class ServiceSecurityAuditBehavior : Behavior  
{  
  string AuditLogLocation;  
  string MessageAuthenticationAuditLevel;  
  string ServiceAuthorizationAuditLevel;  
  boolean SuppressAuditFailure;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="d2c9f-105">Metody</span><span class="sxs-lookup"><span data-stu-id="d2c9f-105">Methods</span></span>  
 <span data-ttu-id="d2c9f-106">Třída ServiceSecurityAuditBehavior nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="d2c9f-106">The ServiceSecurityAuditBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="d2c9f-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="d2c9f-107">Properties</span></span>  
 <span data-ttu-id="d2c9f-108">Třída ServiceSecurityAuditBehavior má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="d2c9f-108">The ServiceSecurityAuditBehavior class has the following properties:</span></span>  
  
### <a name="auditloglocation"></a><span data-ttu-id="d2c9f-109">AuditLogLocation</span><span class="sxs-lookup"><span data-stu-id="d2c9f-109">AuditLogLocation</span></span>  
 <span data-ttu-id="d2c9f-110">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="d2c9f-110">Data type: string</span></span>  
  
 <span data-ttu-id="d2c9f-111">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="d2c9f-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d2c9f-112">Umístění auditovacího protokolu.</span><span class="sxs-lookup"><span data-stu-id="d2c9f-112">The location of the audit log.</span></span>  
  
### <a name="messageauthenticationauditlevel"></a><span data-ttu-id="d2c9f-113">MessageAuthenticationAuditLevel</span><span class="sxs-lookup"><span data-stu-id="d2c9f-113">MessageAuthenticationAuditLevel</span></span>  
 <span data-ttu-id="d2c9f-114">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="d2c9f-114">Data type: string</span></span>  
  
 <span data-ttu-id="d2c9f-115">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="d2c9f-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d2c9f-116">Typ úrovně ověření zprávy, která se používá k zaznamenání událostí auditu.</span><span class="sxs-lookup"><span data-stu-id="d2c9f-116">The type of message authentication level that is used to log audit events.</span></span>  
  
### <a name="serviceauthorizationauditlevel"></a><span data-ttu-id="d2c9f-117">ServiceAuthorizationAuditLevel</span><span class="sxs-lookup"><span data-stu-id="d2c9f-117">ServiceAuthorizationAuditLevel</span></span>  
 <span data-ttu-id="d2c9f-118">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="d2c9f-118">Data type: string</span></span>  
  
 <span data-ttu-id="d2c9f-119">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="d2c9f-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d2c9f-120">Typy událostí autorizace, které jsou zaznamenány v protokolu auditu.</span><span class="sxs-lookup"><span data-stu-id="d2c9f-120">The types of authorization events that are recorded in the audit log.</span></span>  
  
### <a name="suppressauditfailure"></a><span data-ttu-id="d2c9f-121">SuppressAuditFailure</span><span class="sxs-lookup"><span data-stu-id="d2c9f-121">SuppressAuditFailure</span></span>  
 <span data-ttu-id="d2c9f-122">Datový typ: boolean</span><span class="sxs-lookup"><span data-stu-id="d2c9f-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="d2c9f-123">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="d2c9f-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d2c9f-124">Logická hodnota, která určuje vlastnosti pro zamlčené chyby psaní do auditovacího protokolu.</span><span class="sxs-lookup"><span data-stu-id="d2c9f-124">A boolean value that specifies the behavior for suppressing failures of writing to the audit log.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d2c9f-125">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d2c9f-125">Requirements</span></span>  
  
|<span data-ttu-id="d2c9f-126">SOUBOR MOF</span><span class="sxs-lookup"><span data-stu-id="d2c9f-126">MOF</span></span>|<span data-ttu-id="d2c9f-127">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="d2c9f-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="d2c9f-128">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="d2c9f-128">Namespace</span></span>|<span data-ttu-id="d2c9f-129">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="d2c9f-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d2c9f-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d2c9f-130">See also</span></span>

- <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior>
