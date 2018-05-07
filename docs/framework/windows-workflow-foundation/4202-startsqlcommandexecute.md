---
title: 4202 - StartSqlCommandExecute
ms.date: 03/30/2017
ms.assetid: 4559f64f-c824-4075-9e7e-4710bf30f805
ms.openlocfilehash: 09e079864369115c773c58c451fc5e0a33a3ae9f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="4202---startsqlcommandexecute"></a>4202 - StartSqlCommandExecute
## <a name="properties"></a>Vlastnosti  
  
|||  
|-|-|  
|ID|4202|  
|Klíčová slova|WFInstanceStore|  
|úroveň|Verbose|  
|Kanál|Aplikaci Microsoft Windows Server – aplikace/Debug|  
  
## <a name="description"></a>Popis  
 Označuje, že se spouští příkaz SQL.  
  
## <a name="message"></a>Zpráva  
 Spouštění provedení příkazu SQL: %1  
  
## <a name="details"></a>Podrobnosti  
  
|Název položky dat|Datová položka – Typ|Popis|  
|--------------------|--------------------|-----------------|  
|SqlCommand|xs:String|Příkaz SQL, která byla spuštěna.|  
|Domény aplikace|xs:String|Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.|
