---
title: Ladění na klientovi
ms.date: 03/30/2017
ms.assetid: 56f9ad05-ea1b-4ef6-85f2-890f7ed71567
ms.openlocfilehash: 21598b84d0d493bad29a77adf31b85f4989afdc7
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
ms.locfileid: "33809001"
---
# <a name="debugging-on-the-client"></a><span data-ttu-id="4e9da-102">Ladění na klientovi</span><span class="sxs-lookup"><span data-stu-id="4e9da-102">Debugging on the Client</span></span>
<span data-ttu-id="4e9da-103">Aby bylo snazší pro uživatele pro psaní aplikací klienta služby WCF, můžete přidat [ \<serviceDebug >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicedebug.md) služby chování do konfiguračního souboru služby.</span><span class="sxs-lookup"><span data-stu-id="4e9da-103">To make it easier for users to write client applications for your WCF service, you can add the [\<serviceDebug>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicedebug.md) service behavior to the configuration file of your service.</span></span> <span data-ttu-id="4e9da-104">Toto chování lze použít k publikování stránky nápovědy a vrátí informace o spravovaných výjimce v podrobnostech chyb SOAP vrácen do klienta.</span><span class="sxs-lookup"><span data-stu-id="4e9da-104">This behavior can be used to publish help pages, and return managed exception information in the details of SOAP faults returned to the client.</span></span>
