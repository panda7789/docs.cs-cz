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
ms.openlocfilehash: d66e700aa3aee0e577955a978cff0f5cedd84851
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="security-calls-not-authorized"></a><span data-ttu-id="e56fe-102">Počet neautorizovaných volání zabezpečení</span><span class="sxs-lookup"><span data-stu-id="e56fe-102">Security Calls Not Authorized</span></span>
<span data-ttu-id="e56fe-103">Název čítače: Neautorizovaných volání zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="e56fe-103">Counter Name: Security Calls Not Authorized.</span></span>  
  
## <a name="description"></a><span data-ttu-id="e56fe-104">Popis</span><span class="sxs-lookup"><span data-stu-id="e56fe-104">Description</span></span>  
 <span data-ttu-id="e56fe-105">Hodnota tohoto čítače se zvýší, když <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> metoda vrátí `false`.</span><span class="sxs-lookup"><span data-stu-id="e56fe-105">This counter is incremented when the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> method returns `false`.</span></span> <span data-ttu-id="e56fe-106">Znamená příchozí zprávu od platného uživatele a správně chráněný, ale uživatel není autorizovaný k provést určité úlohy.</span><span class="sxs-lookup"><span data-stu-id="e56fe-106">It indicates that the incoming message is from a valid user and protected properly, but the user is not authorized to do specific tasks.</span></span>
