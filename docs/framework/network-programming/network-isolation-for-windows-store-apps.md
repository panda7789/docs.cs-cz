---
title: "Izolace sítě pro aplikace Windows Store"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b064497c-d956-46b8-838d-7a0223c7e200
caps.latest.revision: "7"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: b6c0665a379f02a74bd0f3631aa26b41dd6ece5a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="network-isolation-for-windows-store-apps"></a>Izolace sítě pro aplikace Windows Store
Třídy v <xref:System.Net>, <xref:System.Net.Http>, a <xref:System.Net.Http.Headers> obory názvů lze použít k vývoji aplikací pro Windows Store nebo desktopových aplikacích. Pokud se použije v aplikaci Windows Store, třídy v tyto obory názvů jsou ovlivněné součástí modelu zabezpečení aplikací používá při izolaci sítě [!INCLUDE[win8](../../../includes/win8-md.md)]. Možnosti příslušné sítě musí být povolen v manifest aplikace pro aplikace pro Windows Store pro systém umožňující přístup k síti.  
  
## <a name="checklist-for-network-isolation"></a>Kontrolní seznam pro izolaci sítě  
 Kontrolní seznam použijte Ujistěte se, že izolace sítě je nakonfigurován pro aplikace pro Windows Store.  
  
1.  Určuje směr požadavků na přístup sítě vyžaduje aplikaci. To může být odchozí požadavky iniciované klientem nebo nevyžádaných příchozích požadavků nebo jejich kombinaci těchto typů požadavku sítě může být.  
  
2.  Určuje typ síťové prostředky, které tuto aplikaci bude komunikovat se. Aplikace může vyžadovat ke komunikaci s důvěryhodné prostředky v síti domácí nebo pracovní. Aplikace může být potřeba komunikovat s prostředky v Internetu. Aplikace může vyžadovat přístup k oba typy síťových prostředků.  
  
3.  Konfigurace možností sítě minimální požadovaná izolace v manifest aplikace.  
  
4.  Nasazení a spuštění aplikace otestovat pomocí nástrojů izolace sítě pro řešení potíží.  
  
 Podrobnější informace o tom, jak konfigurovat možnosti sítě a nástroje pro izolaci používají k řešení potíží izolace sítě najdete v tématu [jak nakonfigurovat možnosti izolace sítě](http://go.microsoft.com/fwlink/?LinkID=228265) v [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] vývojáře dokumentace.  
  
## <a name="see-also"></a>Viz také  
 [Připojení k webové službě](http://go.microsoft.com/fwlink/?LinkID=245696)  
 [Pokyny a kontrolní seznam pro izolaci sítě](http://go.microsoft.com/fwlink/?LinkID=228265)  
 [Rychlý úvod: Připojení pomocí položky HttpClient](http://go.microsoft.com/fwlink/?LinkId=245697)  
 [Jak používat HttpClient obslužné rutiny](http://go.microsoft.com/fwlink/?LinkId=245699)  
 [Jak zabezpečit připojení HttpClient](http://go.microsoft.com/fwlink/?LinkId=245698)  
 [Ukázka HttpClient](http://go.microsoft.com/fwlink/?LinkId=242550)
