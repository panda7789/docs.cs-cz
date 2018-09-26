---
title: SymmetricSecurityBindingElement
ms.date: 03/30/2017
ms.assetid: b2e182b6-c041-4d80-a926-6058068d9f79
author: BrucePerlerMS
ms.openlocfilehash: 180b64f6f37e5c765585e52b292319816618be28
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2018
ms.locfileid: "47076511"
---
# <a name="symmetricsecuritybindingelement"></a>SymmetricSecurityBindingElement
SymmetricSecurityBindingElement  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class SymmetricSecurityBindingElement : SecurityBindingElement  
{  
  string MessageProtectionOrder;  
  boolean RequireSignatureConfirmation;  
};  
```  
  
## <a name="methods"></a>Metody  
 Element SymmetricSecurityBindingElement Třída nedefinuje žádné metody.  
  
## <a name="properties"></a>Vlastnosti  
 Element SymmetricSecurityBindingElement třída má následující vlastnosti:  
  
### <a name="messageprotectionorder"></a>MessageProtectionOrder  
 Datový typ: řetězec  
  
 Přístup k typu: jen pro čtení  
  
 Pořadí zpráv šifrování a podepisování pro tuto vazbu.  
  
### <a name="requiresignatureconfirmation"></a>RequireSignatureConfirmation  
 Datový typ: boolean  
  
 Přístup k typu: jen pro čtení  
  
 Určuje, zda vytvoření vazby vyžaduje potvrzení podpisu.  
  
## <a name="requirements"></a>Požadavky  
  
|SOUBOR MOF|Deklarované v Servicemodel.mof.|  
|---------|-----------------------------------|  
|Obor názvů|Definované v root\ServiceModel|  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>
