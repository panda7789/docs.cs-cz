---
title: "Služba: Počet neautorizovaných volání zabezpečení"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3024b20a-5250-4bd1-a38c-c6d79f89610b
caps.latest.revision: "5"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 5dae370d90082c9efe89f9d523740fc25ece21ab
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="service-security-calls-not-authorized"></a><span data-ttu-id="c9d45-102">Služba: Počet neautorizovaných volání zabezpečení</span><span class="sxs-lookup"><span data-stu-id="c9d45-102">Service: Security Calls Not Authorized</span></span>
<span data-ttu-id="c9d45-103">Název čítače: Neautorizovaných volání zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="c9d45-103">Counter Name: Security Calls Not Authorized.</span></span>  
  
## <a name="description"></a><span data-ttu-id="c9d45-104">Popis</span><span class="sxs-lookup"><span data-stu-id="c9d45-104">Description</span></span>  
 <span data-ttu-id="c9d45-105">Hodnota tohoto čítače se zvýší, když <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> metoda vrátí `false`.</span><span class="sxs-lookup"><span data-stu-id="c9d45-105">This counter is incremented when the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> method returns `false`.</span></span> <span data-ttu-id="c9d45-106">Znamená příchozí zprávu od platného uživatele a správně chráněný, ale uživatel není autorizovaný k provést určité úlohy.</span><span class="sxs-lookup"><span data-stu-id="c9d45-106">It indicates that the incoming message is from a valid user and protected properly, but the user is not authorized to do specific tasks.</span></span>
