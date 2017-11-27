---
title: ServiceToEndpointAssociation
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 03c3cd15-e1b2-4dc2-bdc2-59fdccdae110
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 2d2755294ba02b4d67bd7f62cf020a44525874d4
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
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
