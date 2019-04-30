---
title: 4205 – FoundProcessingError
ms.date: 03/30/2017
ms.assetid: f2235a15-dd87-439e-8cb9-8b1b89a3dacf
ms.openlocfilehash: 732632ddc9a7712169ace984c1d6d0098a7ae608
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61774332"
---
# <a name="4205---foundprocessingerror"></a>4205 – FoundProcessingError
## <a name="properties"></a>Vlastnosti  
  
|||  
|-|-|  
|ID|4205|  
|klíčová slova|WFInstanceStore|  
|úroveň|Chyba|  
|Kanál|Aplikace Microsoft Windows Server – aplikace/Debug|  
  
## <a name="description"></a>Popis  
 Označuje, že příkaz zprostředkovatele SQL se nezdařilo.  
  
## <a name="message"></a>Zpráva  
 Příkaz se nezdařil: %1  
  
## <a name="details"></a>Podrobnosti  
  
|Název položky dat|Datový typ položky|Popis|  
|--------------------|--------------------|-----------------|  
|ExceptionMessage|xs:string|Zpráva z výjimky SQL.|  
|Výjimka|xs:string|Podrobnosti o výjimce pro výjimku|  
|AppDomain|xs:string|Řetězec vrácený funkcí AppDomain.CurrentDomain.FriendlyName.|
