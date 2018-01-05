---
title: AsymmetricSecurityBindingElement
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7bd3b6be-8f77-4927-93ae-6fa371893cca
caps.latest.revision: "8"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 82e5365a440d103727f354e682d0ebecb5f46a46
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="asymmetricsecuritybindingelement"></a>AsymmetricSecurityBindingElement
AsymmetricSecurityBindingElement  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class AsymmetricSecurityBindingElement : SecurityBindingElement  
{  
  string MessageProtectionOrder;  
  boolean RequireSignatureConfirmation;  
};  
```  
  
## <a name="methods"></a>Metody  
 Třída AsymmetricSecurityBindingElement nedefinuje žádné metody.  
  
## <a name="properties"></a>Vlastnosti  
 Třída AsymmetricSecurityBindingElement má následující vlastnosti:  
  
### <a name="messageprotectionorder"></a>MessageProtectionOrder  
 Datový typ: řetězec  
  
 Přístup k typu: jen pro čtení  
  
 Pořadí zpráva šifrování a podepisování pro tuto vazbu.  
  
### <a name="requiresignatureconfirmation"></a>RequireSignatureConfirmation  
 Datový typ: logická hodnota  
  
 Přístup k typu: jen pro čtení  
  
 Jestli vazby vyžaduje potvrzení podpisu.  
  
## <a name="requirements"></a>Požadavky  
  
|MOF|Deklarované v Servicemodel.mof.|  
|---------|-----------------------------------|  
|Obor názvů|Definované v root\ServiceModel|  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>
