---
title: DeliveryRequirementsAttribute
ms.date: 03/30/2017
ms.assetid: 40c5435c-a325-4cf8-9dd0-d6e24b4a56a3
ms.openlocfilehash: 7bfc03299fffc8070a7d8a4b3885706ea861bdf6
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/28/2018
ms.locfileid: "50198508"
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
  
### <a name="queueddeliveryrequirements"></a>Atribut QueuedDeliveryRequirements  
 Datový typ: řetězec  
  
 Přístup k typu: jen pro čtení  
  
 Určuje, zda vazba pro službu podporuje kontrakty.  
  
### <a name="requireordereddelivery"></a>RequireOrderedDelivery  
 Datový typ: boolean  
  
 Přístup k typu: jen pro čtení  
  
 Určuje, zda vazba podporuje objednané zprávy.  
  
### <a name="targetcontract"></a>TargetContract  
 Datový typ: řetězec  
  
 Přístup k typu: jen pro čtení  
  
 Kontrakt, ke kterému se vztahuje.  
  
## <a name="requirements"></a>Požadavky  
  
|SOUBOR MOF|Deklarované v Servicemodel.mof.|  
|---------|-----------------------------------|  
|Obor názvů|Definované v root\ServiceModel|  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.DeliveryRequirementsAttribute>
