---
title: 3508 - TrackingProfileNotFound
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4cee3c4a-0490-4c94-aa19-ef7ce7287c02
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 34812b6ddefb69c053cfefa91d7227a7bf15f42e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="3508---trackingprofilenotfound"></a>3508 - TrackingProfileNotFound
## <a name="properties"></a>Vlastnosti  
  
|||  
|-|-|  
|ID|3508|  
|Klíčová slova|WFServices|  
|úroveň|Verbose|  
|Kanál|Aplikaci Microsoft Windows Server – aplikace nebo analytické|  
  
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
