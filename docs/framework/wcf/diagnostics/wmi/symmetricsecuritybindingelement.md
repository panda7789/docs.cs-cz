---
title: SymmetricSecurityBindingElement
ms.date: 03/30/2017
ms.assetid: b2e182b6-c041-4d80-a926-6058068d9f79
ms.openlocfilehash: f6effd533a205d0e8fd1421119e325f06b340dd1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61956712"
---
# <a name="symmetricsecuritybindingelement"></a>SymmetricSecurityBindingElement
SymmetricSecurityBindingElement  
  
## <a name="syntax"></a>Syntaxe  
  
```csharp
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

- <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>
