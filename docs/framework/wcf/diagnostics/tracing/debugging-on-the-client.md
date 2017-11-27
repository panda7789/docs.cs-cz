---
title: "Ladění na klientovi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 56f9ad05-ea1b-4ef6-85f2-890f7ed71567
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 38742bff446a09df5c549a87bd05177d764c63a9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="debugging-on-the-client"></a><span data-ttu-id="562c4-102">Ladění na klientovi</span><span class="sxs-lookup"><span data-stu-id="562c4-102">Debugging on the Client</span></span>
<span data-ttu-id="562c4-103">Aby bylo snazší pro uživatele pro psaní aplikací klienta pro vaše [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] služby, můžete přidat [ \<serviceDebug >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicedebug.md) služby chování do konfiguračního souboru služby.</span><span class="sxs-lookup"><span data-stu-id="562c4-103">To make it easier for users to write client applications for your [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] service, you can add the [\<serviceDebug>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicedebug.md) service behavior to the configuration file of your service.</span></span> <span data-ttu-id="562c4-104">Toto chování lze použít k publikování stránky nápovědy a vrátí informace o spravovaných výjimce v podrobnostech chyb SOAP vrácen do klienta.</span><span class="sxs-lookup"><span data-stu-id="562c4-104">This behavior can be used to publish help pages, and return managed exception information in the details of SOAP faults returned to the client.</span></span>
