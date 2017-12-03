---
title: "Hostování ve spravované aplikaci"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: af70132d-e9e1-4f32-b20f-f0014629758a
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3e6543f1faec5d3298c9a2b825b3a016eb5e7d09
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="hosting-in-a-managed-application"></a>Hostování ve spravované aplikaci
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]služby mohou být hostovány v žádném [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] aplikace. Samoobslužné služby hostování je nejpružnější hostování možnost, protože vyžaduje minimálně infrastrukturu pro nasazování. Je však také alespoň robustní hostování možnost, protože spravované aplikace neposkytují pokročilých funkcí správy a hostování další možnosti hostování v [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], jako jsou například Internetové informační služby (IIS) a služby systému Windows.  
  
 Služba s vlastním hostováním, vytvořte a spusťte instanci <xref:System.ServiceModel.ServiceHost>, který spustí službu naslouchání pro zprávy. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Postupy: hostování služby WCF ve spravované aplikaci](../../../../docs/framework/wcf/how-to-host-a-wcf-service-in-a-managed-application.md).  
  
 Úplný příklad o tom, jak definovat kontrakt, implementaci kontraktu a hostitelem služby v rámci spravované aplikace najdete v článku [kurzu Začínáme](../../../../docs/framework/wcf/getting-started-tutorial.md) a [hostování na vlastním](../../../../docs/framework/wcf/samples/self-host.md).  
  
 Následující části popisují běžné scénáře, které pomocí této možnosti hostování.  
  
## <a name="console-applications"></a>Konzolové aplikace  
 Běžné scénáře, které umožňuje samoobslužné hostování jsou [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služeb běžících v rámci konzoly aplikace. Hostování [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] službu v konzolové aplikaci je obvykle užitečné v průběhu fáze vývoje služby. Díky tomu je usnadňuje ladění, lze snadno získávat informace trasování z a zjistěte, co se děje v rámci aplikace a usnadňuje pohyb zkopírováním do nového umístění.  
  
## <a name="rich-client-applications"></a>Bohaté klientské aplikace  
 Další běžné scénáře, že umožňuje samoobslužné hostování jsou plně funkčního klienta aplikace, jako jsou na základě [!INCLUDE[avalon1](../../../../includes/avalon1-md.md)] nebo Windows Forms (WinForms). Tato možnost hostování také usnadňuje plně funkčního klienta s aplikací, například [!INCLUDE[avalon2](../../../../includes/avalon2-md.md)] a WinForms aplikace komunikovat s vnějším světem. Například peer-to-peer spolupráce klienta, který používá [!INCLUDE[avalon2](../../../../includes/avalon2-md.md)] jeho uživatelské rozhraní a také hostitelů [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] službu, která umožňuje dalším klientům připojit se k němu a sdílet informace.  
  
## <a name="see-also"></a>Viz také  
 [Služby hostování](../../../../docs/framework/wcf/hosting-services.md)  
 [Kurz Začínáme](../../../../docs/framework/wcf/getting-started-tutorial.md)
