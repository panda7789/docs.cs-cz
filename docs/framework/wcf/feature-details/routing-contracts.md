---
title: "Kontrakty pro směrování"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9ceea7ae-ea19-4cf9-ba4f-d071e236546d
caps.latest.revision: "7"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.openlocfilehash: daebd84c9cef5e64ea7ed55c27b671ba01d14df0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="routing-contracts"></a>Kontrakty pro směrování
Kontrakty pro směrování definovat vzory zprávy, které služba směrování může zpracovat.  Každá smlouva je bez psaní a umožňuje služba pro příjem zprávy bez vědomí zpráva schématu nebo akce. To umožňuje obecně směrování zpráv bez další konfigurace, pro jaké jsou specifikace základní zpráv směrovány služby směrování.  
  
## <a name="routing-contracts"></a>Kontrakty pro směrování  
 Protože služba Směrování přijímá objekt obecná zpráva WCF, je nejdůležitější zvážení při výběru kontraktu obrazec kanálu, který se použije při komunikaci s klienty a služby. Při zpracování zpráv, používá službu Směrování čerpadel symetrický zpráva, proto obvykle že tvar příchozí kontraktu musí odpovídat obrazec odchozí kontrakt. Ale existují případy, kdy dispečera modelu služby můžete upravit tvary, například pokud dispečera převede duplexní kanál kanál požadavku a odpovědi, nebo na technickou podporu relace odebere kanál při není vyžadováno a není používán (tj. Pokud **SessionMode.Allowed**, převod **IInputSessionChannel** do **IInputChannel**).  
  
 Pro podporu těchto zpráv čerpadel, služba Směrování poskytuje kontrakty <xref:System.ServiceModel.Routing> obor názvů, který musí být použit při definování koncové body služby používaný službou směrování. Tyto smlouvy jsou bez psaní, který umožňuje příjmu jakéhokoli typu zprávy nebo akce a umožňuje směrovací služby pro zpracování zprávy bez znalosti o konkrétní zpráva schématu. Další informace o smlouvách, které používá služba Směrování najdete v tématu [směrování kontrakty](../../../../docs/framework/wcf/feature-details/routing-contracts.md).  
  
 Kontrakty poskytovaný službou Směrování se nacházejí v <xref:System.ServiceModel.Routing> oboru názvů a jsou popsané v následující tabulce.  
  
|Kontrakt|Obrazec|Tvar kanálu|  
|--------------|-----------|-------------------|  
|<xref:System.ServiceModel.Routing.ISimplexDatagramRouter>|SessionMode = SessionMode.Allowed<br /><br /> Parametru AsyncPattern = true<br /><br /> IsOneWay = true|IInputChannel -> IOutputChannel|  
|<xref:System.ServiceModel.Routing.ISimplexSessionRouter>|SessionMode = SessionMode.Required<br /><br /> Parametru AsyncPattern = true<br /><br /> IsOneWay = true|IInputSessionChannel -> IOutputSessionChannel|  
|<xref:System.ServiceModel.Routing.IRequestReplyRouter>|SessionMode = SessionMode.Allowed<br /><br /> Parametru AsyncPattern = true|IReplyChannel -> třídu IRequestChannel|  
|<xref:System.ServiceModel.Routing.IDuplexSessionRouter>|SessionMode=SessionMode.Required<br /><br /> CallbackContract=typeof(ISimplexSession)<br /><br /> Parametru AsyncPattern = true<br /><br /> IsOneWay = true<br /><br /> TransactionFlow(TransactionFlowOption.Allowed)|IDuplexSessionChannel -> IDuplexSessionChannel|  
  
## <a name="see-also"></a>Viz také  
 [Směrovací služba](http://msdn.microsoft.com/en-us/5ac8718c-bcef-456f-bfd5-1e60a30d6eaa)  
 [Směrování – Úvod](../../../../docs/framework/wcf/feature-details/routing-introduction.md)
