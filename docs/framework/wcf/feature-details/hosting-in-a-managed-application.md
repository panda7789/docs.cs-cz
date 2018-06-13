---
title: Hostování ve spravované aplikaci
ms.date: 03/30/2017
ms.assetid: af70132d-e9e1-4f32-b20f-f0014629758a
ms.openlocfilehash: f374c199fb1982ab8854e41c0c8308f46451d9d0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33489739"
---
# <a name="hosting-in-a-managed-application"></a>Hostování ve spravované aplikaci
Služby Windows Communication Foundation (WCF) může být hostovaný v žádném [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] aplikace. Samoobslužné služby hostování je nejpružnější hostování možnost, protože vyžaduje minimálně infrastrukturu pro nasazování. Je však také alespoň robustní hostování možnost, protože spravované aplikace neposkytují pokročilé hostování a funkcím pro správu Další možnosti hostování ve WCF, například služby Internetové informační služby (IIS) a Windows.  
  
 Služba s vlastním hostováním, vytvořte a spusťte instanci <xref:System.ServiceModel.ServiceHost>, který spustí službu naslouchání pro zprávy. Další informace najdete v tématu [postupy: hostování služby WCF ve spravované aplikaci](../../../../docs/framework/wcf/how-to-host-a-wcf-service-in-a-managed-application.md).  
  
 Úplný příklad o tom, jak definovat kontrakt, implementaci kontraktu a hostitelem služby v rámci spravované aplikace najdete v článku [kurzu Začínáme](../../../../docs/framework/wcf/getting-started-tutorial.md) a [hostování na vlastním](../../../../docs/framework/wcf/samples/self-host.md).  
  
 Následující části popisují běžné scénáře, které pomocí této možnosti hostování.  
  
## <a name="console-applications"></a>Konzolové aplikace  
 Běžné scénáře, které umožňuje samoobslužné hostování jsou WCF služeb běžících v rámci konzolové aplikace. Hostování služby WCF v konzolové aplikaci je obvykle užitečné v průběhu fáze vývoje služby. Díky tomu je usnadňuje ladění, lze snadno získávat informace trasování z a zjistěte, co se děje v rámci aplikace a usnadňuje pohyb zkopírováním do nového umístění.  
  
## <a name="rich-client-applications"></a>Bohaté klientské aplikace  
 Další běžné scénáře, které umožňuje samoobslužné hostování jsou plně funkčního klienta aplikace, jako jsou založené na Windows Presentation Foundation (WPF) nebo Windows Forms (WinForms). Tato možnost hostování také usnadňuje plně funkčního klienta s aplikací, například [!INCLUDE[avalon2](../../../../includes/avalon2-md.md)] a WinForms aplikace komunikovat s vnějším světem. Například peer-to-peer spolupráce klienta, který používá [!INCLUDE[avalon2](../../../../includes/avalon2-md.md)] pro jeho uživatelské rozhraní a také hostitelem služby WCF, který umožňuje dalším klientům připojit se k němu a sdílet informace.  
  
## <a name="see-also"></a>Viz také  
 [Služby hostování](../../../../docs/framework/wcf/hosting-services.md)  
 [Kurz Začínáme](../../../../docs/framework/wcf/getting-started-tutorial.md)
