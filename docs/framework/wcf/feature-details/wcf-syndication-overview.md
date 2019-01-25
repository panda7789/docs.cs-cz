---
title: Syndikace WCF – přehled
ms.date: 03/30/2017
ms.assetid: af6d4c39-e5e8-4099-aee6-5261feff9107
ms.openlocfilehash: 82e8e1192b791dde1ca0ea7e030c7cfc82476b76
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54718244"
---
# <a name="wcf-syndication-overview"></a>Syndikace WCF – přehled
Windows Communication Foundation (WCF) poskytuje podporu pro vystavení informační kanály syndikace ze služby WCF. Syndikace virtuálních sítí je mechanismus integrace aplikace 00Z serveru zpřístupňuje některá data aplikace v interoperabilním formátu označuje jako informační kanál. Informační kanál je kolekce dat aplikací, který se skládá z některých metadat na úrovni kanálu (nadpis, Autor, adresy URL a další metadata) a řadou položky informačních kanálů. V rámci kanálu položky informačního kanálu se obvykle časově řazenou v chronologickém pořadí reverzní. Položky informačního kanálu obsahuje standardní sadu metadat na úrovni položek (název, adresu URL, datum vytvoření, kategorie a další metadata na úrovni položek) a libovolné množství dat konkrétní aplikace. Jsou dva nejběžnější typy informační kanály syndikace syndikace RSS (Really Simple) 2.0 a Atom 1.0, které jsou podporovány službou WCF.  
  
## <a name="object-model"></a>Objektový Model  
 Definuje sadu syndikace konkrétní třídy, které umožňují pracovat s informačními kanály, položky informačních kanálů a související metadata ve formátu nezávisle WCF: <xref:System.ServiceModel.Syndication.SyndicationFeed>, <xref:System.ServiceModel.Syndication.SyndicationItem>, <xref:System.ServiceModel.Syndication.SyndicationPerson>, <xref:System.ServiceModel.Syndication.SyndicationLink>a jiné třídy specifické pro syndikace. Také definuje infrastruktury třídy, které vycházejí programovacího modelu WCF REST k poskytování, včetně podpory syndikace WCF: <xref:System.ServiceModel.Syndication.Atom10FeedFormatter>, a <xref:System.ServiceModel.Syndication.Rss20FeedFormatter>. Třídy formátovací modul informačního kanálu podporu serializace objektu modelu do a z RSS 2.0 a Atom 1.0.  
  
## <a name="scenarios"></a>Scénáře  
 Běžné použití syndikace ještě dnes je psaní blogů, kdy Autor blogu pravidelně publikuje nějaké informace. To může být text, obrázky, zvuk nebo dalších typů informací. Mnoho novinových článcích a časopisů také publikovat příspěvky článků nebo pomocí syndikace. Se přihlásíte k odběru těchto informačního kanálu, může uživatel zajištění aktuálnosti všechny nové informace pocházející z těchto serverů. I když syndikace obvykle souvisí s blogy a vydavatelích, lze použít s libovolnou aplikací, který poskytuje kolekci informace; například chyby databáze, kterou chcete zpřístupnit pomocí syndikace kanálu. Můžete vytvořit službu WCF, která uvádí operace s názvem `CodeDefects`. Tato operace může trvat parametr, který určuje e-mailovou adresu osoby, jejíž chyb, které chcete načíst. Klienta můžete použít následující adresu URL k volání operace: `http://someserver/bugDatabase/CodeDefects?user=johndoe`.  
  
## <a name="syndication-formats"></a>Syndikačních formátů  
 Platforma syndikace WCF podporuje RSS 2.0 a Atom 1.0.  
  
## <a name="see-also"></a>Viz také:
- [Programovací model webových služeb HTTP WCF](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
