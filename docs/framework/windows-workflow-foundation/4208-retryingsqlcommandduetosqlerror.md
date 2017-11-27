---
title: 4208 - RetryingSqlCommandDueToSqlError
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a8e6483a-a6e4-4bbf-82ec-cd8b6e711aad
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 01db76802b96bd32e8a01cf86b1e682defe97a06
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
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
