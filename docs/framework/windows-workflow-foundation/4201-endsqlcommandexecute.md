---
title: 4201 – EndSqlCommandExecute
ms.date: 03/30/2017
ms.assetid: ae0dbc15-f98c-4096-a8d9-fbe4dc36f1cd
ms.openlocfilehash: 75c1cdd10aca6b177911bd9d2f51468016eb9e15
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61774358"
---
# <a name="4201---endsqlcommandexecute"></a>4201 – EndSqlCommandExecute
## <a name="properties"></a>Vlastnosti  
  
|||  
|-|-|  
|ID|4201|  
|klíčová slova|WFInstanceStore|  
|úroveň|Podrobnosti|  
|Kanál|Aplikace Microsoft Windows Server – aplikace/Debug|  
  
## <a name="description"></a>Popis  
 Označuje, že příkaz SQL byl dokončen.  
  
## <a name="message"></a>Zpráva  
 Ukončení příkazu SQL: %1  
  
## <a name="details"></a>Podrobnosti  
  
|Název položky dat|Datový typ položky|Popis|  
|--------------------|--------------------|-----------------|  
|SqlCommand|xs:string|Příkaz SQL, který se spustil.|  
|AppDomain|xs:string|Řetězec vrácený funkcí AppDomain.CurrentDomain.FriendlyName.|
