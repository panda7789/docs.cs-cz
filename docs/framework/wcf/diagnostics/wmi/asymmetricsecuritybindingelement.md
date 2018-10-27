---
title: AsymmetricSecurityBindingElement
ms.date: 03/30/2017
ms.assetid: 7bd3b6be-8f77-4927-93ae-6fa371893cca
ms.openlocfilehash: 076313548828f1fbce9c68b48c0fa7db9cca095f
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2018
ms.locfileid: "50185115"
---
# <a name="asymmetricsecuritybindingelement"></a>AsymmetricSecurityBindingElement
AsymmetricSecurityBindingElement  
  
## <a name="syntax"></a>Syntaxe  
  
```csharp
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
 <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>
