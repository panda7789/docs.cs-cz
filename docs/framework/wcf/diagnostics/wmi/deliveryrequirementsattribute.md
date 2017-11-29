---
title: DeliveryRequirementsAttribute
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 40c5435c-a325-4cf8-9dd0-d6e24b4a56a3
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 40bdc27337daae02795137fc3ac67575787018c1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
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
