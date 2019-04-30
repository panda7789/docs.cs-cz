---
title: 4212 – LockRetryTimeout
ms.date: 03/30/2017
ms.assetid: d4ad415a-9871-49fc-85b8-8ee2ea149b1d
ms.openlocfilehash: 9b7a463851d380eba1ef7b28fbc6decd0cfc979c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61774215"
---
# <a name="4212---lockretrytimeout"></a>4212 – LockRetryTimeout
## <a name="properties"></a>Vlastnosti  
  
|||  
|-|-|  
|ID|4212|  
|klíčová slova|WFInstanceStore|  
|úroveň|Upozornění|  
|Kanál|Aplikace Microsoft Windows Server – aplikace/Debug|  
  
## <a name="description"></a>Popis  
 Zprostředkovatel SQL došlo k pokusu o získání zámku instance vypršel časový limit.  
  
## <a name="message"></a>Zpráva  
 Časový limit pokusu o získání zámku instance.  Operace nebyla dokončena ve vyhrazeném časovém intervalu %1. Čas přidělený této operaci pravděpodobně částí delšího časového limitu.  
  
## <a name="details"></a>Podrobnosti  
  
|Název položky dat|Datový typ položky|Popis|  
|--------------------|--------------------|-----------------|  
|zpoždění|xs:string|Zpoždění mezi opakovanými pokusy.|  
|AppDomain|xs:string|Řetězec vrácený funkcí AppDomain.CurrentDomain.FriendlyName.|
