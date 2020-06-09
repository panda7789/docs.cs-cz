---
title: Syndikace WCF – přehled
ms.date: 03/30/2017
ms.assetid: af6d4c39-e5e8-4099-aee6-5261feff9107
ms.openlocfilehash: 4f72a6d797f195108401a361cc73d74d309d5602
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84600955"
---
# <a name="wcf-syndication-overview"></a>Syndikace WCF – přehled
Windows Communication Foundation (WCF) poskytuje podporu pro zpřístupnění kanálů syndikace ze služby WCF. Syndikace je mechanismus pro integraci aplikací, ve kterém server zveřejňuje některá aplikační data v interoperabilním formátu známém jako informační kanál. Informační kanál je kolekce aplikačních dat, která se skládá z některých metadat na úrovni informačního kanálu (název, autor, adresa URL a další metadata) a řadu položek informačního kanálu. V rámci informačního kanálu jsou položky informačního kanálu obvykle časově seřazené v opačném chronologickém pořadí. Položka informačního kanálu se skládá ze standardní sady metadat na úrovni položky (název, adresa URL, datum vytvoření, kategorie a další metadata na úrovni položky) a libovolné množství dat specifických pro aplikaci. Dva nejběžnější typy kanálů syndikace jsou Really Simple Syndication (RSS) 2,0 a Atom 1,0, které podporuje WCF.  
  
## <a name="object-model"></a>Objektový model  
 WCF definuje sadu tříd, které jsou specifické pro syndikaci, které vám umožní pracovat s informačními kanály, informačními kanály a souvisejícími metadaty způsobem nezávislým na formátu: <xref:System.ServiceModel.Syndication.SyndicationFeed> , <xref:System.ServiceModel.Syndication.SyndicationItem> ,, <xref:System.ServiceModel.Syndication.SyndicationPerson> <xref:System.ServiceModel.Syndication.SyndicationLink> a dalšími třídami, které jsou specifické pro syndikaci. WCF také definuje třídy infrastruktury, které se vytvářejí na programovacím modelu WCF REST pro zajištění podpory syndikace, včetně: <xref:System.ServiceModel.Syndication.Atom10FeedFormatter> a <xref:System.ServiceModel.Syndication.Rss20FeedFormatter> . Třídy formátovacího modulu informačního kanálu podporují serializaci objektového modelu do a z kanálu RSS 2,0 a Atom 1,0.  
  
## <a name="scenarios"></a>Scénáře  
 K běžnému používání syndikace dnes slouží blog, kde autor blogu pravidelně publikuje některé informace. Může to být text, obrázky, zvuk nebo jiné typy informací. Mnoho novinek a časopisů také zveřejňuje příspěvky nebo články pomocí syndikace. Po přihlášení k odběru takového informačního kanálu může uživatel stále aktuální se všemi novými informacemi, které pocházejí z těchto webů. I když je syndikace nejčastěji přidružena k Blogy a vydavatelům, lze ji použít spolu s jakoukoli aplikací, která zpřístupňuje kolekci informací. například databáze chyb, kterou chcete zpřístupnit pomocí informačního kanálu syndikace. Můžete vytvořit službu WCF, která zveřejňuje volanou operaci `CodeDefects` . Tato operace může mít parametr, který určuje e-mailovou adresu osoby, jejíž chyby chcete načíst. Klient může pro volání operace použít následující adresu URL: `http://someserver/bugDatabase/CodeDefects?user=johndoe` .  
  
## <a name="syndication-formats"></a>Formáty syndikace  
 Syndikační Platforma WCF podporuje RSS 2,0 a Atom 1,0.  
  
## <a name="see-also"></a>Viz také

- [Programovací model webových služeb HTTP WCF](wcf-web-http-programming-model.md)
