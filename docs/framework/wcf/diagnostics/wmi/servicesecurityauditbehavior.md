---
title: ServiceSecurityAuditBehavior
ms.date: 03/30/2017
ms.assetid: 2c5809e7-5364-44ce-bc71-848be4672e2a
ms.openlocfilehash: 30679e1f67c6943bf674a6bbd8bf12be090765a8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61956894"
---
# <a name="servicesecurityauditbehavior"></a>ServiceSecurityAuditBehavior
ServiceSecurityAuditBehavior  
  
## <a name="syntax"></a>Syntaxe  
  
```csharp  
class ServiceSecurityAuditBehavior : Behavior  
{  
  string AuditLogLocation;  
  string MessageAuthenticationAuditLevel;  
  string ServiceAuthorizationAuditLevel;  
  boolean SuppressAuditFailure;  
};  
```  
  
## <a name="methods"></a>Metody  
 Třída ServiceSecurityAuditBehavior nedefinuje žádné metody.  
  
## <a name="properties"></a>Vlastnosti  
 Třída ServiceSecurityAuditBehavior má následující vlastnosti:  
  
### <a name="auditloglocation"></a>AuditLogLocation  
 Datový typ: řetězec  
  
 Typ přístupu: jen pro čtení  
  
 Umístění auditovacího protokolu.  
  
### <a name="messageauthenticationauditlevel"></a>MessageAuthenticationAuditLevel  
 Datový typ: řetězec  
  
 Typ přístupu: jen pro čtení  
  
 Typ úrovně ověření zprávy, která se používá k zaznamenání událostí auditu.  
  
### <a name="serviceauthorizationauditlevel"></a>ServiceAuthorizationAuditLevel  
 Datový typ: řetězec  
  
 Typ přístupu: jen pro čtení  
  
 Typy událostí autorizace, které jsou zaznamenány v protokolu auditu.  
  
### <a name="suppressauditfailure"></a>SuppressAuditFailure  
 Datový typ: boolean  
  
 Typ přístupu: jen pro čtení  
  
 Logická hodnota, která určuje vlastnosti pro zamlčené chyby psaní do auditovacího protokolu.  
  
## <a name="requirements"></a>Požadavky  
  
|SOUBOR MOF|Deklarované v Servicemodel.mof.|  
|---------|-----------------------------------|  
|Obor názvů|Definované v root\ServiceModel|  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior>
