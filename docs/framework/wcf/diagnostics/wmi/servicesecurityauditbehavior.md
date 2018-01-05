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
