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
---
# <a name="servicesecurityauditbehavior"></a>ServiceSecurityAuditBehavior
ServiceSecurityAuditBehavior  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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
  
### <a name="auditloglocation"></a>auditLogLocation  
 Datový typ: řetězec  
  
 Přístup k typu: jen pro čtení  
  
 Umístění protokolu auditu.  
  
### <a name="messageauthenticationauditlevel"></a>messageAuthenticationAuditLevel  
 Datový typ: řetězec  
  
 Přístup k typu: jen pro čtení  
  
 Typ zprávy úroveň ověřování, která se používá k protokolování událostí auditu.  
  
### <a name="serviceauthorizationauditlevel"></a>serviceAuthorizationAuditLevel  
 Datový typ: řetězec  
  
 Přístup k typu: jen pro čtení  
  
 Typy událostí autorizace, které se zaznamenávají v protokolu auditu.  
  
### <a name="suppressauditfailure"></a>suppressAuditFailure  
 Datový typ: logická hodnota  
  
 Přístup k typu: jen pro čtení  
  
 Logická hodnota, která určuje chování pro potlačení chyb při zápisu do protokolu auditování.  
  
## <a name="requirements"></a>Požadavky  
  
|MOF|Deklarované v Servicemodel.mof.|  
|---------|-----------------------------------|  
|Obor názvů|Definované v root\ServiceModel|  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior>
