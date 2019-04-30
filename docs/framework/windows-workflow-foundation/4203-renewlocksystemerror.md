---
title: 4203 – RenewLockSystemError
ms.date: 03/30/2017
ms.assetid: 6ec9ec6f-4ae2-45cf-b99b-02cdb9dc9ec9
ms.openlocfilehash: 984f7ddae8797cba17753a618d0820d21bde5eef
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61774345"
---
# <a name="4203---renewlocksystemerror"></a>4203 – RenewLockSystemError
## <a name="properties"></a>Vlastnosti  
  
|||  
|-|-|  
|ID|4203|  
|klíčová slova|WFInstanceStore|  
|úroveň|Chyba|  
|Kanál|Aplikace Microsoft Windows Server – aplikace/Debug|  
  
## <a name="description"></a>Popis  
 Určuje zprostředkovatele SQL se nezdařilo se prodloužit platnost zámku z důvodu buď platnost zámku již předaný nebo byl odstraněn vlastník zámku. Úložiště SqlWorkflowInstanceStore se přeruší.  
  
## <a name="message"></a>Zpráva  
 Nepovedlo se prodloužit platnost zámku, platnost zámku již vypršela nebo byl odstraněn vlastník zámku. Přerušení metody SqlWorkflowInstanceStore.  
  
## <a name="details"></a>Podrobnosti  
  
|Název položky dat|Datový typ položky|Popis|  
|--------------------|--------------------|-----------------|  
|AppDomain|xs:string|Řetězec vrácený funkcí AppDomain.CurrentDomain.FriendlyName.|
