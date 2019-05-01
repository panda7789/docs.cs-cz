---
title: 1002 – WorkflowApplicationTerminated
ms.date: 03/30/2017
ms.assetid: 4e8b111f-79dc-4898-bb4a-e9b36f69420f
ms.openlocfilehash: 01c9aba6e863e07a1a999a28fccefbab95a34d5b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62008652"
---
# <a name="1002---workflowapplicationterminated"></a>1002 – WorkflowApplicationTerminated
## <a name="properties"></a>Vlastnosti  
  
|||  
|-|-|  
|ID|1002|  
|klíčová slova|WFRuntime|  
|úroveň|Informace o|  
|Kanál|Aplikace Microsoft Windows Server – aplikace/Debug|  
  
## <a name="description"></a>Popis  
 Označuje, že aplikace pracovního postupu byla ukončena v chybovém stavu s výjimkou.  
  
## <a name="message"></a>Zpráva  
 WorkflowApplication Id: '%1' byl ukončen. Byla dokončena v chybovém stavu s výjimkou.  
  
## <a name="details"></a>Podrobnosti  
  
|Název položky dat|Datový typ položky|Popis|  
|--------------------|--------------------|-----------------|  
|WorkflowApplicationId|`xs:string`|Id aplikace pracovního postupu|  
|Výjimka|`xs:string`|Podrobnosti o výjimce pro výjimku|  
|AppDomain|`xs:string`|Řetězec vrácený funkcí AppDomain.CurrentDomain.FriendlyName.|
