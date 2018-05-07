---
title: 4201 - EndSqlCommandExecute
ms.date: 03/30/2017
ms.assetid: ae0dbc15-f98c-4096-a8d9-fbe4dc36f1cd
ms.openlocfilehash: 75c1cdd10aca6b177911bd9d2f51468016eb9e15
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="4201---endsqlcommandexecute"></a>4201 - EndSqlCommandExecute
## <a name="properties"></a>Vlastnosti  
  
|||  
|-|-|  
|ID|4201|  
|Klíčová slova|WFInstanceStore|  
|úroveň|Verbose|  
|Kanál|Aplikaci Microsoft Windows Server – aplikace/Debug|  
  
## <a name="description"></a>Popis  
 Označuje, že příkaz SQL byl dokončen.  
  
## <a name="message"></a>Zpráva  
 Ukončení provedení příkazu SQL: %1  
  
## <a name="details"></a>Podrobnosti  
  
|Název položky dat|Datová položka – Typ|Popis|  
|--------------------|--------------------|-----------------|  
|SqlCommand|xs:String|Příkaz SQL, která byla spuštěna.|  
|Domény aplikace|xs:String|Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.|
