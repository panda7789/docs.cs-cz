---
title: 3508 – TrackingProfileNotFound
ms.date: 03/30/2017
ms.assetid: 4cee3c4a-0490-4c94-aa19-ef7ce7287c02
ms.openlocfilehash: 94c7ce231df241778f7c6ec5fe5998eae364750d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61755568"
---
# <a name="3508---trackingprofilenotfound"></a>3508 – TrackingProfileNotFound
## <a name="properties"></a>Vlastnosti  
  
|||  
|-|-|  
|ID|3508|  
|klíčová slova|WFServices|  
|úroveň|Podrobnosti|  
|Kanál|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>Popis  
 Označuje buď nebyl nalezen profil TrackingProfile v konfiguračním souboru nebo ActivityDefinitionId neodpovídá profilu.  
  
## <a name="message"></a>Zpráva  
 Profil TrackingProfile '%1' pro ActivityDefinitionId '%2' nebyl nalezen. Buď nebyl nalezen profil TrackingProfile v konfiguračním souboru nebo ActivityDefinitionId neodpovídá.  
  
## <a name="details"></a>Podrobnosti  
  
|Název položky dat|Datový typ položky|Popis|  
|--------------------|--------------------|-----------------|  
|vlastnosti TrackingProfile.|xs:string|Název profilu sledování.|  
|ActivityDefinitionId|xs:string|Id definice aktivity.|  
|AppDomain|xs:string|Řetězec vrácený funkcí AppDomain.CurrentDomain.FriendlyName.|
