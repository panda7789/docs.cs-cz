---
title: Hostování ve spravované aplikaci
ms.date: 03/30/2017
ms.assetid: af70132d-e9e1-4f32-b20f-f0014629758a
ms.openlocfilehash: c1f4d91994ba44407ff5c93dbd34aa0bdef9332b
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/14/2019
ms.locfileid: "65591732"
---
# <a name="hosting-in-a-managed-application"></a>Hostování ve spravované aplikaci
Služby Windows Communication Foundation (WCF) je možné hostovat v libovolné aplikace rozhraní .NET Framework. Služba s vlastním hostováním je flexibilní možnost hostování, protože vyžaduje minimálně infrastrukturu pro nasazení. Je však také nejméně robustní možnost hostování, protože spravovaných aplikací se neposkytuje pokročilé hostování a funkcím pro správu Další možnosti hostování ve službě WCF, jako jsou služby Internet Information Services (IIS) a Windows.  
  
 Služba v místním prostředí, vytvořte a spusťte instanci <xref:System.ServiceModel.ServiceHost>, který spouští službu pro naslouchání pro zprávy. Další informace najdete v tématu [jak: Hostování služby WCF ve spravované aplikaci](../../../../docs/framework/wcf/how-to-host-a-wcf-service-in-a-managed-application.md).  
  
 Kompletní příklad, jak definovat kontrakt, implementaci kontraktu a hostování služby v rámci spravované aplikace najdete v článku [kurz Začínáme](../../../../docs/framework/wcf/getting-started-tutorial.md) a [hostování na vlastním serveru](../../../../docs/framework/wcf/samples/self-host.md).  
  
 Běžné scénáře pomocí této možnosti hostování naleznete v následujících částech.  
  
## <a name="console-applications"></a>Konzolové aplikace  
 Běžné scénáře, které s vlastním hostováním umožňuje jsou WCF služby spuštěné v konzolové aplikace. Hostování služby WCF v konzolové aplikaci je obvykle vhodné ve vývojové fázi služby. Díky tomu je snadné ladění, snadno získat informace o trasování z a zjistěte, co se děje v rámci aplikace a snadno přesouvat jejich zkopírováním do nového umístění.  
  
## <a name="rich-client-applications"></a>Aplikace plně funkčního klienta  
 Další běžné scénáře, které s vlastním hostováním umožňuje jsou plně funkčního klienta aplikace, například algoritmů založených na Windows Presentation Foundation (WPF) nebo Windows Forms (WinForms). Tato možnost hostování také usnadňuje aplikacemi rich client, jako například [!INCLUDE[avalon2](../../../../includes/avalon2-md.md)] a WinForms aplikace komunikovat s vnějším světem. Například klient spolupráci peer-to-peer, která používá [!INCLUDE[avalon2](../../../../includes/avalon2-md.md)] pro jeho uživatelské rozhraní a také hostuje službu WCF, která umožňuje dalším klientům připojit se k němu a sdílení informací.  
  
## <a name="see-also"></a>Viz také:

- [Služby hostování](../../../../docs/framework/wcf/hosting-services.md)
- [Kurz Začínáme](../../../../docs/framework/wcf/getting-started-tutorial.md)
