---
title: Počet neautorizovaných volání zabezpečení
ms.date: 03/30/2017
ms.assetid: cb6acdcd-7336-42e1-9ae8-ac891336cd58
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 3554644a7f73894703cc26ad11e4f7b9d58cab60
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="security-calls-not-authorized"></a>Počet neautorizovaných volání zabezpečení
Název čítače: Neautorizovaných volání zabezpečení.  
  
## <a name="description"></a>Popis  
 Hodnota tohoto čítače se zvýší, když <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> metoda vrátí `false`. Znamená příchozí zprávu od platného uživatele a správně chráněný, ale uživatel není autorizovaný k provést určité úlohy.
