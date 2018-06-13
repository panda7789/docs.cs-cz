---
title: 'Koncový bod: Počet neautorizovaných volání zabezpečení'
ms.date: 03/30/2017
ms.assetid: d25095ff-9ff0-4c69-a674-4e6a9fe3f4dc
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: b449aaad65f01a5f4835f8335543220383543984
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33471253"
---
# <a name="endpoint-security-calls-not-authorized"></a>Koncový bod: Počet neautorizovaných volání zabezpečení
Název čítače: Neautorizovaných volání zabezpečení.  
  
## <a name="description"></a>Popis  
 Hodnota tohoto čítače se zvýší, když <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> metoda vrátí `false`. Znamená příchozí zprávu od platného uživatele a správně chráněný, ale uživatel není autorizovaný k provést určité úlohy.
