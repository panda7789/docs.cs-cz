---
title: DeliveryRequirementsAttribute
ms.date: 03/30/2017
ms.assetid: 40c5435c-a325-4cf8-9dd0-d6e24b4a56a3
ms.openlocfilehash: c81e4b27969d879a70806082f48879cbf1b32ccc
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2019
ms.locfileid: "59979209"
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
