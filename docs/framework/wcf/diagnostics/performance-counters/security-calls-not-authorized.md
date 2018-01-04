---
title: "Počet neautorizovaných volání zabezpečení"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cb6acdcd-7336-42e1-9ae8-ac891336cd58
caps.latest.revision: "6"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 641d627868c69a5ec63e1acc3f262d315341d0ad
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="security-calls-not-authorized"></a><span data-ttu-id="40cf1-102">Počet neautorizovaných volání zabezpečení</span><span class="sxs-lookup"><span data-stu-id="40cf1-102">Security Calls Not Authorized</span></span>
<span data-ttu-id="40cf1-103">Název čítače: Neautorizovaných volání zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="40cf1-103">Counter Name: Security Calls Not Authorized.</span></span>  
  
## <a name="description"></a><span data-ttu-id="40cf1-104">Popis</span><span class="sxs-lookup"><span data-stu-id="40cf1-104">Description</span></span>  
 <span data-ttu-id="40cf1-105">Hodnota tohoto čítače se zvýší, když <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> metoda vrátí `false`.</span><span class="sxs-lookup"><span data-stu-id="40cf1-105">This counter is incremented when the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> method returns `false`.</span></span> <span data-ttu-id="40cf1-106">Znamená příchozí zprávu od platného uživatele a správně chráněný, ale uživatel není autorizovaný k provést určité úlohy.</span><span class="sxs-lookup"><span data-stu-id="40cf1-106">It indicates that the incoming message is from a valid user and protected properly, but the user is not authorized to do specific tasks.</span></span>
