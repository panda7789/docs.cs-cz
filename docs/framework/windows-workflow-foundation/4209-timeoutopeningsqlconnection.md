---
title: 4209 - TimeoutOpeningSqlConnection
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f0e56518-9758-41dc-a760-50d1a10fba6e
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 86d971a2e5f1257281c453e7eb0c2dc1755098d8
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="4209---timeoutopeningsqlconnection"></a>4209 - TimeoutOpeningSqlConnection
## <a name="properties"></a>Vlastnosti  
  
|||  
|-|-|  
|ID|4209|  
|Klíčová slova|WFInstanceStore|  
|úroveň|Chyba|  
|Kanál|Aplikaci Microsoft Windows Server – aplikace/Debug|  
  
## <a name="description"></a>Popis  
 Označuje, že při pokusu o otevření připojení SQL došlo k vypršení časového limitu.  
  
## <a name="message"></a>Zpráva  
 Časový limit pokusu o otevření připojení SQL. Operace nebyla dokončena v přiděleném časovém limitu % 1. Čas přidělený tato operace mohla být část delší časový limit.  
  
## <a name="details"></a>Podrobnosti  
  
|Název položky dat|Datová položka – Typ|Popis|  
|--------------------|--------------------|-----------------|  
|Časový limit|xs:String|Hodnota časového limitu pro otevření připojení SQL.|  
|Domény aplikace|xs:String|Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.|
