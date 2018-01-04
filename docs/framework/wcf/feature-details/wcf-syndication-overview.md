---
title: "Syndikace WCF – přehled"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: af6d4c39-e5e8-4099-aee6-5261feff9107
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: acc7131d02f1f4e3cde0df152bdfbc591724b600
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="wcf-syndication-overview"></a>Syndikace WCF – přehled
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]poskytuje podporu pro informační kanály syndikace z vystavení [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby. Syndikace je mechanismus integrace aplikací, ve kterém server zpřístupní data některých aplikací ve formátu, který umožňuje vzájemnou spolupráci známé jako informačního kanálu. Informační kanál je kolekce dat aplikací, která se skládá z některé informačního kanálu úroveň metadat (název, Autor, adresy URL a další metadata) a řadu položky informačních kanálů. V informačním kanálu položky informačních kanálů jsou obvykle čas seřazené v obráceném chronologickém pořadí. Položka informačního obsahuje standardní sadu úrovni položky metadat (název, URL, datum vytvoření, kategorie a další metadata na úrovni položek) a libovolné množství dat v konkrétní aplikaci. Jsou dvě nejběžnějších typů informační kanály syndikace skutečně jednoduché syndikace (RSS) 2.0 a Atom 1.0, které jsou podporovány [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
## <a name="object-model"></a>Objektový Model  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]definuje sadu syndikace konkrétní třídy, které umožňují pracovat s kanály, položky informačních kanálů a související metadata způsobem nezávislé na formát: <xref:System.ServiceModel.Syndication.SyndicationFeed>, <xref:System.ServiceModel.Syndication.SyndicationItem>, <xref:System.ServiceModel.Syndication.SyndicationPerson>, <xref:System.ServiceModel.Syndication.SyndicationLink>a další syndikace konkrétní třídy. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]také definuje infrastrukturu třídy, které vychází z programovací Model REST WCF poskytnout, včetně podpory syndikace: <xref:System.ServiceModel.Syndication.Atom10FeedFormatter>, a <!--zz <xref:System.ServiceModel.Syndication.RSS20FeedFormatter>--> `RSS20FeedFormatter`. Formátování informačního kanálu třídy podporovat serializaci objektu modelu do a z RSS 2.0 a Atom 1.0.  
  
## <a name="scenarios"></a>Scénáře  
 Běžně se používají syndikace dnes je blogování, kde Autor blog pravidelně publikuje nějaká informace. To může být text, obrázky, zvuk nebo jiné typy informací. Mnoho novinových článcích a zásobníky také publikování článků zprávy nebo pomocí syndikace. Se přihlásíte k odběru informační kanál, uživatel může průběžně aktualizovat všechny nové informace pocházející z těchto serverů. I když syndikace je nejčastěji přidružen blogy a vydavatelů, lze použít s libovolnou aplikací, který poskytuje kolekci informace; například chyb databáze, kterou chcete vystavit pomocí syndikace informačního kanálu. Můžete vytvořit [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] názvem služby, která zveřejňuje operace `CodeDefects`. Tato operace může trvat parametr, který určuje e-mailovou adresu osoby, jejíž chyby můžete obnovit. Klienta můžete použít následující adresu URL pro operaci volat: http://someserver/bugDatabase/CodeDefects?user=johndoe.  
  
## <a name="syndication-formats"></a>Syndikačních formátů  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Syndikace platforma podporuje RSS 2.0 a Atom 1.0.  
  
## <a name="see-also"></a>Viz také  
 [Programovací model webových služeb HTTP WCF](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
