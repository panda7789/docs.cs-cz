---
title: Protokol PNRP
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 11940511-c124-4d91-ae31-d4ed6e81ee58
caps.latest.revision: "14"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: ba38c7e42126bb70161dcb72ffdd6965e8def044
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="peer-name-resolution-protocol"></a>Protokol PNRP
V prostředích peer-to-peer partnerské uzly používají určitý název řešení systémy přeložit vzájemně umístění v síti (adresy, protokoly a porty) z názvů nebo jiné typy identifikátorů. V minulosti má byla peer name resolution Protocol ztěžuje ze své podstaty přechodný připojení a také další nedostatků v v systému DNS (Domain Name).  
  
 Microsoft® Windows® Peer-to-Peer sítě platforma řeší tento problém s řešení protokolu PNRP (Peer Name), zabezpečená, škálovatelná a dynamické registraci a protokolu name resolution protocol nejprve vyvinuté pro systém Windows XP a pak upgradovat na Vista™ systému Windows. PNRP funguje velmi jinak, než tradiční název řešení systémy, otevírá zajímavé nové možnosti pro vývojáře aplikací.  
  
 S PNRP můžete použít sdílené názvy do počítače, nebo jednotlivých aplikací nebo služeb v počítači. Peer name resolution Protocol zahrnuje adresu, port a které by mohly mít rozšířené datové části. Příklady výhod tohoto systému odolnost proti chybám, žádné kritická místa a název řešení, které nikdy vrátí zastaralé adresy; provedení protokol vynikající řešení pro hledání mobilních uživatelů.  
  
 Z hlediska zabezpečení, může být názvy partnerů publikován jako zabezpečené (chráněné) nebo zabezpečená (nechráněné). PNRP používá kryptografie využívající veřejného klíče k ochraně zabezpečené sdílené názvy proti falšování identity; počítače a služby mohou být pojmenovány PNRP.  
  
-   Protokol Peer Name Resolution ukazuje následující vlastnosti:  
  
-   Distribuované a téměř úplně bez serveru. Servery jsou pouze požadované pro samozaváděcí proces.  
  
-   Zabezpečte název publikace bez zapojení třetích stran. Na rozdíl od publikaci název DNS je název publikace PNRP okamžitou a bez finanční náklady.  
  
-   PNRP aktualizace v v reálném čase, která brání zastaralé adres.  
  
-   Řešení názvů pomocí protokolu PNRP přesahuje počítače tím, že se také překlad názvů pro služby.  
  
-  
  
## <a name="the-systemnetpeertopeer-namespace"></a>Namespace System.Net.PeerToPeer  
  
-   Funkce PNRP je definována <xref:System.Net.PeerToPeer> oboru názvů v rozhraní .NET Framework verze 3.5. Poskytuje sadu typů, které lze použít k registraci a překladu názvů partnerů s služby k dispozici PNRP.  
  
-  
  
-   (PNRP a překladače vlastní partnerských uzlů může být vytvořen a instancí pomocí typy součástí <xref:System.ServiceModel.PeerResolvers> oboru názvů.)  
  
-  
  
-   Základní typy používá k registraci a překlad názvů s PNRP služby k dispozici jsou následující:  
  
-  
  
-   <xref:System.Net.PeerToPeer.Cloud>: Definuje informace, které popisují dostupné PNRP cloudu, včetně jeho oboru.  
  
-   <xref:System.Net.PeerToPeer.PeerName>: Definuje název partnerského zařízení, která slouží k registraci a následně vyřešit partnerského uzlu v cloudu.  
  
-   <xref:System.Net.PeerToPeer.PeerNameRecord>: Definuje záznam PNRP cloudu, který obsahuje informace o registraci pro partnerský uzel, včetně koncových bodů sítě, na kterých mohou kontaktovat partnerský uzel.  
  
-   <xref:System.Net.PeerToPeer.PeerNameRegistration>: Definuje proces registrace pro název partnerského zařízení, včetně metody pro spuštění a zastavení registrace názvu partnera.  
  
-   <xref:System.Net.PeerToPeer.PeerNameResolver>: Definuje proces překladu název partnerského zařízení na jeho koncové sítě, včetně synchronní a asynchronní metody pro řešení.  
  
-  
  
-  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.PeerResolvers>  
 <xref:System.Net.PeerToPeer>  
 [Ukázky programování sítě](../../../docs/framework/network-programming/network-programming-samples.md)  
 [Ukázka PeerToPeer technologie](http://go.microsoft.com/fwlink/?LinkID=179571)
