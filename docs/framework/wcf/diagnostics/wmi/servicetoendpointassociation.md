---
title: ServiceToEndpointAssociation
ms.date: 03/30/2017
ms.assetid: 03c3cd15-e1b2-4dc2-bdc2-59fdccdae110
ms.openlocfilehash: 3d23a3ee10c47e04ea7bdba202ea5063c0d84fac
ms.sourcegitcommit: b22705f1540b237c566721018f974822d5cd8758
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2018
ms.locfileid: "49452706"
---
# <a name="servicetoendpointassociation"></a>ServiceToEndpointAssociation
Služba se mapuje na koncový bod.  
  
## <a name="syntax"></a>Syntaxe  
  
```csharp
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
 Datový typ: Služba  
  
 Přístup k typu: jen pro čtení  
Kvalifikátory: klíč  
  
 Služba spojená s koncovým bodem.  
  
### <a name="ref"></a>ref  
 Datový typ: koncového bodu  
  
 Přístup k typu: jen pro čtení  
Kvalifikátory: klíč  
  
 Koncový bod, související se službou.  
  
## <a name="requirements"></a>Požadavky  
  
|SOUBOR MOF|Deklarované v Servicemodel.mof.|  
|---------|-----------------------------------|  
|Obor názvů|Definované v root\ServiceModel|
