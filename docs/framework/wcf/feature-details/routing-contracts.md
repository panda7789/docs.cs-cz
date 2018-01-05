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
ms.workload: dotnet
ms.openlocfilehash: 3d70368f7514b64d67a186b328b1f19d231fe0c1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
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
 [Úvod do směrování](../../../../docs/framework/wcf/feature-details/routing-introduction.md)
