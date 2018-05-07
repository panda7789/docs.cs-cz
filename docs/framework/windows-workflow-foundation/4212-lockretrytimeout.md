---
title: 4212 - LockRetryTimeout
ms.date: 03/30/2017
ms.assetid: d4ad415a-9871-49fc-85b8-8ee2ea149b1d
ms.openlocfilehash: 9b7a463851d380eba1ef7b28fbc6decd0cfc979c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="4212---lockretrytimeout"></a>4212 - LockRetryTimeout
## <a name="properties"></a>Vlastnosti  
  
|||  
|-|-|  
|ID|4212|  
|Klíčová slova|WFInstanceStore|  
|úroveň|Upozornění|  
|Kanál|Aplikaci Microsoft Windows Server – aplikace/Debug|  
  
## <a name="description"></a>Popis  
 Zprostředkovatel SQL došlo k vypršení časového limitu při pokusu o získání zámku instance.  
  
## <a name="message"></a>Zpráva  
 Časový limit pokusu o získání zámku instance.  Operace nebyla dokončena v přiděleném časovém limitu % 1. Čas přidělený tato operace mohla být část delší časový limit.  
  
## <a name="details"></a>Podrobnosti  
  
|Název položky dat|Datová položka – Typ|Popis|  
|--------------------|--------------------|-----------------|  
|Zpoždění|xs:String|Zpoždění mezi opakovanými pokusy.|  
|Domény aplikace|xs:String|Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.|
