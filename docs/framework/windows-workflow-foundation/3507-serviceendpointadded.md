---
title: 3507 - ServiceEndpointAdded
ms.date: 03/30/2017
ms.assetid: c068fc0e-07ee-4551-9824-ea7216e1fe37
ms.openlocfilehash: c787a1a5af752a3d08e2049cfa0b600b7739e56c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="3507---serviceendpointadded"></a>3507 - ServiceEndpointAdded
## <a name="properties"></a>Vlastnosti  
  
|||  
|-|-|  
|ID|3507|  
|Klíčová slova|WFServices|  
|úroveň|Informace o|  
|Kanál|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>Popis  
 Označuje, že byl přidán koncový bod služby.  
  
## <a name="message"></a>Zpráva  
 Koncový bod služby byla přidána ke adresu '%1', vazby: %2' a kontrakt '%3'.  
  
## <a name="details"></a>Podrobnosti  
  
|Název položky dat|Datová položka – Typ|Popis|  
|--------------------|--------------------|-----------------|  
|Adresa|xs:String|Adresa koncového bodu.|  
|Vazba|xs:String|Vazba koncového bodu.|  
|Kontrakt|xs:String|Kontrakt koncového bodu.|  
|Domény aplikace|xs:String|Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.|
