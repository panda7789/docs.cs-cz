---
title: 3507 – ServiceEndpointAdded
ms.date: 03/30/2017
ms.assetid: c068fc0e-07ee-4551-9824-ea7216e1fe37
ms.openlocfilehash: c787a1a5af752a3d08e2049cfa0b600b7739e56c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62009835"
---
# <a name="3507---serviceendpointadded"></a>3507 – ServiceEndpointAdded
## <a name="properties"></a>Vlastnosti  
  
|||  
|-|-|  
|ID|3507|  
|klíčová slova|WFServices|  
|úroveň|Informace o|  
|Kanál|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>Popis  
 Označuje, že byl přidán koncový bod služby.  
  
## <a name="message"></a>Zpráva  
 Byl přidán koncový bod služby pro adresu '%1', '%2' vazba a kontrakt '%3'.  
  
## <a name="details"></a>Podrobnosti  
  
|Název položky dat|Datový typ položky|Popis|  
|--------------------|--------------------|-----------------|  
|Adresa|xs:string|Adresa koncového bodu.|  
|Vazba|xs:string|Vazba koncového bodu.|  
|Kontrakt|xs:string|Kontrakt koncového bodu.|  
|AppDomain|xs:string|Řetězec vrácený funkcí AppDomain.CurrentDomain.FriendlyName.|
