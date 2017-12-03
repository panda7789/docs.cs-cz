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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: cd942658229c7c70cf6a8b6bcac79f17a1a2db14
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="debugging-on-the-client"></a><span data-ttu-id="fd3e2-102">Ladění na klientovi</span><span class="sxs-lookup"><span data-stu-id="fd3e2-102">Debugging on the Client</span></span>
<span data-ttu-id="fd3e2-103">Aby bylo snazší pro uživatele pro psaní aplikací klienta pro vaše [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] služby, můžete přidat [ \<serviceDebug >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicedebug.md) služby chování do konfiguračního souboru služby.</span><span class="sxs-lookup"><span data-stu-id="fd3e2-103">To make it easier for users to write client applications for your [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] service, you can add the [\<serviceDebug>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicedebug.md) service behavior to the configuration file of your service.</span></span> <span data-ttu-id="fd3e2-104">Toto chování lze použít k publikování stránky nápovědy a vrátí informace o spravovaných výjimce v podrobnostech chyb SOAP vrácen do klienta.</span><span class="sxs-lookup"><span data-stu-id="fd3e2-104">This behavior can be used to publish help pages, and return managed exception information in the details of SOAP faults returned to the client.</span></span>
