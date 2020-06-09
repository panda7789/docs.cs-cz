---
title: Hostování ve spravované aplikaci
ms.date: 03/30/2017
ms.assetid: af70132d-e9e1-4f32-b20f-f0014629758a
ms.openlocfilehash: 759257edf89d1af5c453bb98f41361b54cf113ae
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84597342"
---
# <a name="hosting-in-a-managed-application"></a>Hostování ve spravované aplikaci
Služby Windows Communication Foundation (WCF) je možné hostovat v jakékoli .NET Framework aplikaci. Služby pro samoobslužné hostování jsou nejpružnější možností hostování, protože pro nasazení vyžaduje minimální infrastrukturu. Je však také nejméně robustní možnost hostování, protože spravované aplikace neposkytují pokročilé funkce hostování a správy jiných možností hostování v technologii WCF, například Internetová informační služba (IIS) a služby systému Windows.  
  
 Chcete-li vytvořit samoobslužnou službu, vytvořte a otevřete instanci <xref:System.ServiceModel.ServiceHost> , která spustí službu naslouchající pro zprávy. Další informace najdete v tématu [Postup: hostování služby WCF ve spravované aplikaci](../how-to-host-a-wcf-service-in-a-managed-application.md).  
  
 Úplný příklad pro definování kontraktu, implementaci kontraktu a hostování služby ve spravované aplikaci najdete v [kurzu Začínáme](../getting-started-tutorial.md) a na [samoobslužném hostiteli](../samples/self-host.md).  
  
 V následujících částech jsou popsány běžné scénáře, které používají tuto možnost hostování.  
  
## <a name="console-applications"></a>Konzolové aplikace  
 Běžné scénáře, které umožňují samoobslužné hostování, jsou služby WCF běžící uvnitř konzolových aplikací. Hostování služby WCF v konzolové aplikaci je obvykle užitečné při vývojové fázi služby. Díky tomu se dají snadno ladit, snadno získat trasovací informace a zjistit, co se děje uvnitř aplikace, a snadno se pohybovat, když je zkopírujete do nových umístění.  
  
## <a name="rich-client-applications"></a>Bohatých klientských aplikací  
 Další běžné scénáře, které umožňují samoobslužné hostování, jsou bohatých klientských aplikací, jako jsou například aplikace založené na Windows Presentation Foundation (WPF) nebo model Windows Forms (WinForms). Tato možnost hostování také usnadňuje použití bohatých klientských aplikací, jako jsou WPF a WinForms, ke komunikaci s vnějším světem. Například klient pro spolupráci Peer-to-peer, který používá WPF pro své uživatelské rozhraní a také hostuje službu WCF, která umožňuje ostatním klientům připojit se k němu a sdílet informace.  
  
## <a name="see-also"></a>Viz také

- [Služby hostování](../hosting-services.md)
- [Kurz Začínáme](../getting-started-tutorial.md)
