---
title: 1002 - WorkflowApplicationTerminated
ms.date: 03/30/2017
ms.assetid: 4e8b111f-79dc-4898-bb4a-e9b36f69420f
ms.openlocfilehash: 01c9aba6e863e07a1a999a28fccefbab95a34d5b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="1002---workflowapplicationterminated"></a>1002 - WorkflowApplicationTerminated
## <a name="properties"></a>Vlastnosti  
  
|||  
|-|-|  
|ID|1002|  
|Klíčová slova|WFRuntime|  
|úroveň|Informace o|  
|Kanál|Aplikaci Microsoft Windows Server – aplikace/Debug|  
  
## <a name="description"></a>Popis  
 Označuje, že aplikace pracovního postupu byl ukončen ve stavu chybný s výjimkou.  
  
## <a name="message"></a>Zpráva  
 WorkflowApplication Id: "%1" byl ukončen. Dokončil v chybném stavu s výjimkou.  
  
## <a name="details"></a>Podrobnosti  
  
|Název položky dat|Datová položka – Typ|Popis|  
|--------------------|--------------------|-----------------|  
|WorkflowApplicationId|`xs:string`|Id aplikace pracovního postupu|  
|Výjimka|`xs:string`|Podrobnosti o výjimce pro výjimky|  
|Domény aplikace|`xs:string`|Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.|
