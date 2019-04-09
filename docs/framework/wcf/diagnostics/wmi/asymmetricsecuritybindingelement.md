---
title: AsymmetricSecurityBindingElement
ms.date: 03/30/2017
ms.assetid: 7bd3b6be-8f77-4927-93ae-6fa371893cca
ms.openlocfilehash: 0f86fc1b410753b5ec100f0a7d43de9badd1401b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59196044"
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
  
 Typ přístupu: jen pro čtení  
  
 Pořadí zpráv šifrování a podepisování pro tuto vazbu.  
  
### <a name="requiresignatureconfirmation"></a>RequireSignatureConfirmation  
 Datový typ: boolean  
  
 Typ přístupu: jen pro čtení  
  
 Určuje, zda vytvoření vazby vyžaduje potvrzení podpisu.  
  
## <a name="requirements"></a>Požadavky  
  
|SOUBOR MOF|Deklarované v Servicemodel.mof.|  
|---------|-----------------------------------|  
|Obor názvů|Definované v root\ServiceModel|  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>
