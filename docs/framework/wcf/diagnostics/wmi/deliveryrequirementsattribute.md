---
title: DeliveryRequirementsAttribute
ms.date: 03/30/2017
ms.assetid: 40c5435c-a325-4cf8-9dd0-d6e24b4a56a3
ms.openlocfilehash: 809e9d809bce456c831aab83c7ac19a882b2959b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54571321"
---
# <a name="deliveryrequirementsattribute"></a>DeliveryRequirementsAttribute
DeliveryRequirementsAttribute  
  
## <a name="syntax"></a>Syntaxe  
  
```csharp
class DeliveryRequirementsAttribute : Behavior  
{  
  string QueuedDeliveryRequirements;  
  boolean RequireOrderedDelivery;  
  string TargetContract;  
};  
```  
  
## <a name="methods"></a>Metody  
 Atribut DeliveryRequirementsAttribute Třída nedefinuje žádné metody.  
  
## <a name="properties"></a>Vlastnosti  
 Atribut DeliveryRequirementsAttribute třída má následující vlastnosti:  
  
### <a name="queueddeliveryrequirements"></a>QueuedDeliveryRequirements  
 Datový typ: řetězec  
  
 Typ přístupu: jen pro čtení  
  
 Určuje, zda vazba pro službu podporuje kontrakty.  
  
### <a name="requireordereddelivery"></a>RequireOrderedDelivery  
 Datový typ: boolean  
  
 Typ přístupu: jen pro čtení  
  
 Určuje, zda vazba podporuje objednané zprávy.  
  
### <a name="targetcontract"></a>TargetContract  
 Datový typ: řetězec  
  
 Typ přístupu: jen pro čtení  
  
 Kontrakt, ke kterému se vztahuje.  
  
## <a name="requirements"></a>Požadavky  
  
|SOUBOR MOF|Deklarované v Servicemodel.mof.|  
|---------|-----------------------------------|  
|Obor názvů|Definované v root\ServiceModel|  
  
## <a name="see-also"></a>Viz také:
- <xref:System.ServiceModel.DeliveryRequirementsAttribute>
