---
title: 4208 – RetryingSqlCommandDueToSqlError
ms.date: 03/30/2017
ms.assetid: a8e6483a-a6e4-4bbf-82ec-cd8b6e711aad
ms.openlocfilehash: a97336f12ccfe041b79328bcb48f4e7214a05b63
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61774293"
---
# <a name="4208---retryingsqlcommandduetosqlerror"></a>4208 – RetryingSqlCommandDueToSqlError
## <a name="properties"></a>Vlastnosti  
  
|||  
|-|-|  
|ID|4208|  
|klíčová slova|WFInstanceStore|  
|úroveň|Informace o|  
|Kanál|Aplikace Microsoft Windows Server – aplikace/Debug|  
  
## <a name="description"></a>Popis  
 Označuje, že zprostředkovatel SQL je opakováním příkazu SQL kvůli chybě SQL.  
  
## <a name="message"></a>Zpráva  
 Opakováním příkazu SQL kvůli chybě SQL s číslem %1.  
  
## <a name="details"></a>Podrobnosti  
  
|Název položky dat|Datový typ položky|Popis|  
|--------------------|--------------------|-----------------|  
|ErrorNumber|xs:string|Číslo chyby SQL.|  
|AppDomain|xs:string|Řetězec vrácený funkcí AppDomain.CurrentDomain.FriendlyName.|
