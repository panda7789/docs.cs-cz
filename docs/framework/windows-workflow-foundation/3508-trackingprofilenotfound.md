---
title: 3508 - TrackingProfileNotFound
ms.date: 03/30/2017
ms.assetid: 4cee3c4a-0490-4c94-aa19-ef7ce7287c02
ms.openlocfilehash: 94c7ce231df241778f7c6ec5fe5998eae364750d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="3508---trackingprofilenotfound"></a>3508 - TrackingProfileNotFound
## <a name="properties"></a>Vlastnosti  
  
|||  
|-|-|  
|ID|3508|  
|Klíčová slova|WFServices|  
|úroveň|Verbose|  
|Kanál|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>Popis  
 Označuje TrackingProfile nebyl nalezen v konfiguračním souboru nebo ActivityDefinitionId neodpovídá profil.  
  
## <a name="message"></a>Zpráva  
 '%1' TrackingProfile ActivityDefinitionId '%2' nebyla nalezena. Buď TrackingProfile nebyl nalezen v konfiguračním souboru nebo ActivityDefinitionId neodpovídá.  
  
## <a name="details"></a>Podrobnosti  
  
|Název položky dat|Datová položka – Typ|Popis|  
|--------------------|--------------------|-----------------|  
|TrackingProfile|xs:String|Název profilu sledování.|  
|ActivityDefinitionId|xs:String|Id definice aktivity.|  
|Domény aplikace|xs:String|Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.|
