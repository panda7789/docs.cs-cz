---
title: DeliveryRequirementsAttribute
ms.date: 03/30/2017
ms.assetid: 40c5435c-a325-4cf8-9dd0-d6e24b4a56a3
ms.openlocfilehash: d294ba4f14472012b9e311ee53742633b5173f54
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="deliveryrequirementsattribute"></a>DeliveryRequirementsAttribute
DeliveryRequirementsAttribute  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class DeliveryRequirementsAttribute : Behavior  
{  
  string QueuedDeliveryRequirements;  
  boolean RequireOrderedDelivery;  
  string TargetContract;  
};  
```  
  
## <a name="methods"></a>Metody  
 Třída Atribut DeliveryRequirementsAttribute nedefinuje žádné metody.  
  
## <a name="properties"></a>Vlastnosti  
 Atribut DeliveryRequirementsAttribute třída má následující vlastnosti:  
  
### <a name="queueddeliveryrequirements"></a>Atribut QueuedDeliveryRequirements  
 Datový typ: řetězec  
  
 Přístup k typu: jen pro čtení  
  
 Určuje, zda vazby pro službu podporuje kontrakty.  
  
### <a name="requireordereddelivery"></a>RequireOrderedDelivery  
 Datový typ: logická hodnota  
  
 Přístup k typu: jen pro čtení  
  
 Určuje, zda vazby podporuje seřazené zprávy.  
  
### <a name="targetcontract"></a>TargetContract  
 Datový typ: řetězec  
  
 Přístup k typu: jen pro čtení  
  
 Kontrakt, na který se vztahuje.  
  
## <a name="requirements"></a>Požadavky  
  
|MOF|Deklarované v Servicemodel.mof.|  
|---------|-----------------------------------|  
|Obor názvů|Definované v root\ServiceModel|  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.DeliveryRequirementsAttribute>
