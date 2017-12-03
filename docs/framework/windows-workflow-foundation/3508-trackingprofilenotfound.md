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
ms.openlocfilehash: 346cb98b1285883a9a85f2c7abb6147f42734395
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
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
