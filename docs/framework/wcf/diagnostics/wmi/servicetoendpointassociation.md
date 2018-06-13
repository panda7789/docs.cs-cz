---
title: ServiceToEndpointAssociation
ms.date: 03/30/2017
ms.assetid: 03c3cd15-e1b2-4dc2-bdc2-59fdccdae110
ms.openlocfilehash: b1e5b87b053e947432cba9f6e716f7d1ea8f013f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33484326"
---
# <a name="servicetoendpointassociation"></a>ServiceToEndpointAssociation
Mapuje na koncový bod služby.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class ServiceToEndpointAssociation  
{  
  Service ref;  
  Endpoint ref;  
};  
```  
  
## <a name="methods"></a>Metody  
 Třída ServiceToEndpointAssociation nedefinuje žádné metody.  
  
## <a name="properties"></a>Vlastnosti  
 Třída ServiceToEndpointAssociation má následující vlastnosti:  
  
### <a name="ref"></a>ref  
 Datový typ: služby  
  
 Přístup k typu: jen pro čtení  
Kvalifikátory: klíč  
  
 Služba přiřazené ke koncovému bodu.  
  
### <a name="ref"></a>ref  
 Datový typ: koncový bod  
  
 Přístup k typu: jen pro čtení  
Kvalifikátory: klíč  
  
 Koncový bod spojené s touto službou.  
  
## <a name="requirements"></a>Požadavky  
  
|MOF|Deklarované v Servicemodel.mof.|  
|---------|-----------------------------------|  
|Obor názvů|Definované v root\ServiceModel|
