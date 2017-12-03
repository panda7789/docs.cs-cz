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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b3bfe7547fafb17503c972646d344263117d9d86
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
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
