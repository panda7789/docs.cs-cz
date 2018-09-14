---
title: Protokol PNRP
ms.date: 03/30/2017
ms.assetid: 11940511-c124-4d91-ae31-d4ed6e81ee58
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 70c49198c0198610eaa5001971b7de7efd2951aa
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/13/2018
ms.locfileid: "45518136"
---
# <a name="peer-name-resolution-protocol"></a>Protokol PNRP
V prostředích peer-to-peer partnerské uzly použít konkrétní název řešení systémy druhé strany umístění v síti (adresy, protokoly a porty) z názvů nebo jiných typů identifikátorů. V minulosti má bylo složité peer name resolution Protocol ze své podstaty přechodné připojení, stejně jako ostatní nedostatky v v systému DNS (Domain Name).  
  
 Microsoft® Windows® sítě Peer-to-Peer platforma řeší tento problém se řešení protokolu PNRP (Peer Name), zabezpečené, škálovatelné a dynamické registraci a protokol nejdřív vyvinutý pro systém Windows XP a pak upgradovat v Windows Vista™. PNRP funguje nějak významně odlišně, než tradiční název řešení systémy, otevírá zajímavé nové možnosti pro vývojáře aplikací.  
  
 S protokolem PNRP můžete použít názvy partnerských uzlů do počítače, nebo jednotlivých aplikací nebo služeb v počítači. Peer name resolution Protocol obsahuje adresu, port a případně rozšířené datové části. Mezi výhody tohoto systému patří odolnost proti chybám, žádné kritické body a název řešení, které nikdy vrátí zastaralé adresy; provádění protokolu vynikající řešení pro hledání mobilních uživatelů.  
  
 Z hlediska zabezpečení, názvy partnerských uzlů může být publikován jako zabezpečené (chráněný) nebo nezabezpečené (bez ochrany). Protokol PNRP používá kryptografii využívající veřejného klíče k ochraně názvy partnerských uzlů zabezpečené proti falšování identity; s protokolem PNRP může mít název počítače a služby.  
  
-   Protokol Peer Name Resolution demonstruje následující vlastnosti:  
  
-   Distribuované a téměř zcela bez serveru. Servery jsou pouze potřeba samozaváděcí procesu.  
  
-   Zabezpečené publikování názvů bez zapojení třetím stranám. Na rozdíl od publikace název DNS je název publikace PNRP okamžité a bez finančních nákladů.  
  
-   PNRP aktualizace v reálném čase, se zabránilo zastaralé adres.  
  
-   Řešení názvů pomocí protokolu PNRP se rozpíná za počítače tím, že také překlad názvů pro služby.  
  
-  
  
## <a name="the-systemnetpeertopeer-namespace"></a>Namespace System.Net.PeerToPeer  
  
-   Je definována funkce PNRP <xref:System.Net.PeerToPeer> oboru názvů v rámci rozhraní .NET Framework verze 3.5. Poskytuje sadu typů, které je možné registrovat a překládat názvy partnerských uzlů dostupné službou PNRP.  
  
-  
  
-   (PNRP a překladače vlastní partnerských uzlů může být vytvořen a instance pomocí typů součástí <xref:System.ServiceModel.PeerResolvers> oboru názvů.)  
  
-  
  
-   Základní typy, které slouží k registraci a řešení názvů pomocí protokolu PNRP služby k dispozici jsou následující:  
  
-  
  
-   <xref:System.Net.PeerToPeer.Cloud>: Definuje informace, které popisují dostupné cloudu PNRP, včetně jeho rozsahu.  
  
-   <xref:System.Net.PeerToPeer.PeerName>: Definuje název partnera, který slouží k registraci a následně vyřešit sdílené v rámci cloudu.  
  
-   <xref:System.Net.PeerToPeer.PeerNameRecord>: Definuje záznamu v cloudu PNRP, který obsahuje informace o registraci pro partnerský uzel, který obsahuje koncové body sítě, na kterých mohou kontaktovat partnerský uzel.  
  
-   <xref:System.Net.PeerToPeer.PeerNameRegistration>: Definuje proces registrace pro název partnerského zařízení, včetně metod ke spuštění a zastavení registrace názvu partnera.  
  
-   <xref:System.Net.PeerToPeer.PeerNameResolver>: Definuje procesu k vyřešení název partnerského zařízení do jeho koncových bodů sítě, včetně synchronní a asynchronní metody pro překlad.  
  
-  
  
-  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.PeerResolvers>  
 <xref:System.Net.PeerToPeer>  
 [Ukázky programování sítě](../../../docs/framework/network-programming/network-programming-samples.md)  
 [Ukázka technologie PeerToPeer](https://go.microsoft.com/fwlink/?LinkID=179571)
