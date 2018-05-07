---
title: Syndikace WCF – přehled
ms.date: 03/30/2017
ms.assetid: af6d4c39-e5e8-4099-aee6-5261feff9107
ms.openlocfilehash: c059ca3ee33b254a60d6b8596b02e1f995fd2ca1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="wcf-syndication-overview"></a>Syndikace WCF – přehled
Windows Communication Foundation (WCF) poskytuje podporu pro vystavení informační kanály syndikace ze služby WCF. Syndikace je mechanismus integrace aplikací, ve kterém server zpřístupní data některých aplikací ve formátu, který umožňuje vzájemnou spolupráci známé jako informačního kanálu. Informační kanál je kolekce dat aplikací, která se skládá z některé informačního kanálu úroveň metadat (název, Autor, adresy URL a další metadata) a řadu položky informačních kanálů. V informačním kanálu položky informačních kanálů jsou obvykle čas seřazené v obráceném chronologickém pořadí. Položka informačního obsahuje standardní sadu úrovni položky metadat (název, URL, datum vytvoření, kategorie a další metadata na úrovni položek) a libovolné množství dat v konkrétní aplikaci. Nejběžnější dva druhy informační kanály syndikace jsou skutečně jednoduché syndikace (RSS) 2.0 a Atom 1.0, které jsou podporovány službou WCF.  
  
## <a name="object-model"></a>Objektový Model  
 WCF definuje sadu syndikace konkrétní třídy, které umožňují pracovat s kanály, položky informačních kanálů a související metadata způsobem nezávislé na formát: <xref:System.ServiceModel.Syndication.SyndicationFeed>, <xref:System.ServiceModel.Syndication.SyndicationItem>, <xref:System.ServiceModel.Syndication.SyndicationPerson>, <xref:System.ServiceModel.Syndication.SyndicationLink>a další syndikace konkrétní třídy. Také definuje infrastrukturu třídy, které vychází z programovací Model REST WCF poskytnout, včetně podpory syndikace WCF: <xref:System.ServiceModel.Syndication.Atom10FeedFormatter>, a <!--zz <xref:System.ServiceModel.Syndication.RSS20FeedFormatter>--> `RSS20FeedFormatter`. Formátování informačního kanálu třídy podporovat serializaci objektu modelu do a z RSS 2.0 a Atom 1.0.  
  
## <a name="scenarios"></a>Scénáře  
 Běžně se používají syndikace dnes je blogování, kde Autor blog pravidelně publikuje nějaká informace. To může být text, obrázky, zvuk nebo jiné typy informací. Mnoho novinových článcích a zásobníky také publikování článků zprávy nebo pomocí syndikace. Se přihlásíte k odběru informační kanál, uživatel může průběžně aktualizovat všechny nové informace pocházející z těchto serverů. I když syndikace je nejčastěji přidružen blogy a vydavatelů, lze použít s libovolnou aplikací, který poskytuje kolekci informace; například chyb databáze, kterou chcete vystavit pomocí syndikace informačního kanálu. Můžete vytvořit služby WCF, který zveřejňuje volat operace `CodeDefects`. Tato operace může trvat parametr, který určuje e-mailovou adresu osoby, jejíž chyby můžete obnovit. Klienta můžete použít následující adresu URL pro operaci volat: http://someserver/bugDatabase/CodeDefects?user=johndoe.  
  
## <a name="syndication-formats"></a>Syndikačních formátů  
 Platforma syndikace WCF podporuje RSS 2.0 a Atom 1.0.  
  
## <a name="see-also"></a>Viz také  
 [Programovací model webových služeb HTTP WCF](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
