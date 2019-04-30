---
title: 4202 – StartSqlCommandExecute
ms.date: 03/30/2017
ms.assetid: 4559f64f-c824-4075-9e7e-4710bf30f805
ms.openlocfilehash: 09e079864369115c773c58c451fc5e0a33a3ae9f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61774371"
---
# <a name="4202---startsqlcommandexecute"></a>4202 – StartSqlCommandExecute
## <a name="properties"></a>Vlastnosti  
  
|||  
|-|-|  
|ID|4202|  
|klíčová slova|WFInstanceStore|  
|úroveň|Podrobnosti|  
|Kanál|Aplikace Microsoft Windows Server – aplikace/Debug|  
  
## <a name="description"></a>Popis  
 Označuje, že se zpracovává příkaz SQL.  
  
## <a name="message"></a>Zpráva  
 Spuštění příkazu SQL: %1  
  
## <a name="details"></a>Podrobnosti  
  
|Název položky dat|Datový typ položky|Popis|  
|--------------------|--------------------|-----------------|  
|SqlCommand|xs:string|Příkaz SQL, který se spustil.|  
|AppDomain|xs:string|Řetězec vrácený funkcí AppDomain.CurrentDomain.FriendlyName.|
