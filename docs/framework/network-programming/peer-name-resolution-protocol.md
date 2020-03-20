---
title: Protokol PNRP (Peer Name Resolution Protocol)
ms.date: 03/30/2017
ms.assetid: 11940511-c124-4d91-ae31-d4ed6e81ee58
ms.openlocfilehash: c8b7b2190349323bf212d816a77f5f7810f6ca2c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "74428220"
---
# <a name="peer-name-resolution-protocol"></a>Protokol PNRP (Peer Name Resolution Protocol)
V prostředích typu peer-to-peer používají partneři specifické systémy pro překlad názvů k vzájemnému překladu síťových umístění (adres, protokolů a portů) z názvů nebo jiných typů identifikátorů. V minulosti bylo překlad názvů rovnocenných stran komplikováno neodmyslitelně přechodným připojením a dalšími nedostatky v systému DNS (Domain Name System).  
  
 Microsoft® Windows® Peer-to-Peer síťová platforma řeší tento problém s Peer Name Resolution Protocol (PNRP), zabezpečené, škálovatelné a dynamické registrace názvů a překlad názvů protokol nejprve vyvinut pro Windows XP a poté inovované v Windows Vista™. PNRP funguje velmi odlišně od tradičních systémů pro rozlišení názvů a otevírá vzrušující nové možnosti pro vývojáře aplikací.  
  
 S PNRP, peer jména lze použít na počítači nebo jednotlivé aplikace nebo služby v počítači. Překlad názvů partnera obsahuje adresu, port a případně rozšířenou datovou část. Mezi výhody tohoto systému patří odolnost proti chybám, žádná kritická místa a překlady názvů, které nikdy nevrátí zastaralé adresy; čímž se protokol dělá vynikajícím řešením pro vyhledávání mobilních uživatelů.  
  
 Z hlediska zabezpečení mohou být názvy rovnocenných počítačů publikovány jako zabezpečené (chráněné) nebo nezabezpečené (nechráněné). PNRP používá kryptografii s veřejným klíčem k ochraně zabezpečených názvů rovnocenných počítačů před falšováním z falšování; počítače i služby lze pojmenovat pomocí PNRP.  
  
Protokol Peer Name Resolution Protocol demonstruje následující vlastnosti:  
  
- Distribuováno a téměř výhradně bez serveru. Servery jsou vyžadovány pouze pro zaváděcí proces.  
  
- Bezpečné zveřejnění názvu bez účasti třetích stran. Na rozdíl od publikace názvu DNS je publikace názvu PNRP okamžitá a bez finančních nákladů.  
  
- PNRP aktualizace v reálném čase, což zabraňuje řešení zastaralých adres.  
  
- Rozlišení názvů prostřednictvím PNRP přesahuje počítače tím, že také umožňuje překlad názvů pro služby.  
  
## <a name="the-systemnetpeertopeer-namespace"></a>Obor názvů System.Net.PeerToPeer  
  
- Funkce PNRP je definována <xref:System.Net.PeerToPeer> oborem názvů v rámci rozhraní .NET Framework verze 3.5. Poskytuje sadu typů, které lze použít k registraci a překladu názvů rovnocenných počítačů s dostupnou službou PNRP.  
  
- (PNRP a vlastní peer překladače lze vytvořit a vytvořit instance <xref:System.ServiceModel.PeerResolvers> pomocí typů uvedených v oboru názvů.)  
  
- Základní typy používané k registraci a překladu názvů s dostupnou službou PNRP jsou následující:  
  
- <xref:System.Net.PeerToPeer.Cloud>: Definuje informace popisující dostupný cloud PNRP, včetně jeho oboru.  
  
- <xref:System.Net.PeerToPeer.PeerName>: Definuje název partnera, který lze použít k registraci a následně přeložit partnera v rámci cloudu.  
  
- <xref:System.Net.PeerToPeer.PeerNameRecord>: Definuje záznam v cloudu PNRP, který obsahuje registrační informace pro partnera, který zahrnuje koncové body sítě, ve kterých lze kontaktovat partnera.  
  
- <xref:System.Net.PeerToPeer.PeerNameRegistration>: Definuje proces registrace pro název partnera, včetně metod pro spuštění a zastavení registrace názvu partnera.  
  
- <xref:System.Net.PeerToPeer.PeerNameResolver>: Definuje proces pro překlad názvu partnera do koncového bodu (koncových bodů sítě), včetně synchronních i asynchronních metod řešení.  
  
## <a name="see-also"></a>Viz také

- <xref:System.ServiceModel.PeerResolvers>
- <xref:System.Net.PeerToPeer>
- [Ukázky programování sítě](network-programming-samples.md)

<!-- to-do: review sample links
- [PeerToPeer Technology Sample](https://go.microsoft.com/fwlink/?LinkID=179571)
-->
