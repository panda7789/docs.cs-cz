---
title: 4208 - RetryingSqlCommandDueToSqlError
ms.date: 03/30/2017
ms.assetid: a8e6483a-a6e4-4bbf-82ec-cd8b6e711aad
ms.openlocfilehash: a97336f12ccfe041b79328bcb48f4e7214a05b63
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="4208---retryingsqlcommandduetosqlerror"></a>4208 - RetryingSqlCommandDueToSqlError
## <a name="properties"></a>Vlastnosti  
  
|||  
|-|-|  
|ID|4208|  
|Klíčová slova|WFInstanceStore|  
|úroveň|Informace o|  
|Kanál|Aplikaci Microsoft Windows Server – aplikace/Debug|  
  
## <a name="description"></a>Popis  
 Označuje, že zprostředkovatel SQL je opakováním příkazu SQL z důvodu chyby systému SQL.  
  
## <a name="message"></a>Zpráva  
 Opakováním příkazu SQL z důvodu SQL číslo chyby %1.  
  
## <a name="details"></a>Podrobnosti  
  
|Název položky dat|Datová položka – Typ|Popis|  
|--------------------|--------------------|-----------------|  
|Argument číslo chyby|xs:String|Číslo chyby SQL.|  
|Domény aplikace|xs:String|Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.|
