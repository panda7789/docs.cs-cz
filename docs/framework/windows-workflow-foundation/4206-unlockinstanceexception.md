---
title: 4206 – UnlockInstanceException
ms.date: 03/30/2017
ms.assetid: 5a46dc5f-d517-4135-8905-25a42f01206b
ms.openlocfilehash: 3c981888b491f2797a431c2103ba3f5f0bd17046
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61774319"
---
# <a name="4206---unlockinstanceexception"></a>4206 – UnlockInstanceException
## <a name="properties"></a>Vlastnosti  
  
|||  
|-|-|  
|ID|4206|  
|klíčová slova|WFInstanceStore|  
|úroveň|Chyba|  
|Kanál|Aplikace Microsoft Windows Server – aplikace/Debug|  
  
## <a name="description"></a>Popis  
 Označuje, že došlo k výjimce při pokusu o odemknutí instance.  
  
## <a name="message"></a>Zpráva  
 Výjimka %1 došlo k chybě při pokusu o odemknutí instance.  
  
## <a name="details"></a>Podrobnosti  
  
|Název položky dat|Datový typ položky|Popis|  
|--------------------|--------------------|-----------------|  
|ExceptionMessage|xs:string|Zpráva z výjimky SQL.|  
|AppDomain|xs:string|Řetězec vrácený funkcí AppDomain.CurrentDomain.FriendlyName.|
