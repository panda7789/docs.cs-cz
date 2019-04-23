---
title: Kontrakty pro směrování
ms.date: 03/30/2017
ms.assetid: 9ceea7ae-ea19-4cf9-ba4f-d071e236546d
ms.openlocfilehash: 660652caa804b8c19f6dd18bcba51bf4abc3ba12
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59145350"
---
# <a name="routing-contracts"></a>Kontrakty pro směrování
Kontrakty pro směrování definovat vzory zprávy, které směrovací služba může zpracovat.  Každá smlouva bez psaní a umožňuje službě a zobrazí se zpráva bez znalosti schématu zprávy nebo akce. To umožňuje službě Směrování a obecně směrování zpráv bez další konfigurace pro specifikace základní zprávy směruje.  
  
## <a name="routing-contracts"></a>Kontrakty pro směrování  
 Vzhledem k tomu, že směrovací služba přijímá obecný objekt zprávy WCF, je důležité zvážit při výběru kontrakt tvar kanál, který se použije při komunikaci s klienty a služby. Při zpracování zpráv, směrovací služba používá symetrické zpráva čerpadla, proto obvykle že tvar příchozích smlouvy musí odpovídat tvar odchozí kontraktu. Existují však případy, ve kterém modelu služby dispečer můžete upravit tvary, například když dispečer převede duplexní kanál do kanálu požadavek odpověď, nebo odebere podporu relace z kanálu, když není potřeba a nepoužívá se (to znamená Pokud **SessionMode.Allowed**, převod **IInputSessionChannel** do **IInputChannel**).  
  
 Tyto zprávy čerpadla, směrovací služba podporuje prostřednictvím smluv v <xref:System.ServiceModel.Routing> obor názvů, který musí být použit při definování koncové body služby používaný službou směrování. Tyto smlouvy jsou bez psaní, která umožňuje příjem libovolný typ zprávy nebo akce a umožňuje směrovací služba zpracovává zprávy bez znalosti schématu konkrétní zprávu. Další informace o smlouvách, které používá služba Směrování najdete v tématu [směrování kontrakty](../../../../docs/framework/wcf/feature-details/routing-contracts.md).  
  
 Kontrakty poskytovaný službou Směrování se nacházejí v <xref:System.ServiceModel.Routing> obor názvů a jsou popsány v následující tabulce.  
  
|Kontrakt|Obrazec|Tvar kanálu|  
|--------------|-----------|-------------------|  
|<xref:System.ServiceModel.Routing.ISimplexDatagramRouter>|Režim SessionMode = SessionMode.Allowed<br /><br /> AsyncPattern = true<br /><br /> IsOneWay = true|IInputChannel -> IOutputChannel|  
|<xref:System.ServiceModel.Routing.ISimplexSessionRouter>|Režim SessionMode = SessionMode.Required<br /><br /> AsyncPattern = true<br /><br /> IsOneWay = true|IInputSessionChannel -> IOutputSessionChannel|  
|<xref:System.ServiceModel.Routing.IRequestReplyRouter>|Režim SessionMode = SessionMode.Allowed<br /><br /> AsyncPattern = true|Rozhraní IReplyChannel -> třídu IRequestChannel|  
|<xref:System.ServiceModel.Routing.IDuplexSessionRouter>|SessionMode=SessionMode.Required<br /><br /> CallbackContract=typeof(ISimplexSession)<br /><br /> AsyncPattern = true<br /><br /> IsOneWay = true<br /><br /> TransactionFlow(TransactionFlowOption.Allowed)|IDuplexSessionChannel -> IDuplexSessionChannel|  
  
## <a name="see-also"></a>Viz také:

- [Směrovací služba](../../../../docs/framework/wcf/feature-details/routing-service.md)
- [Úvod do směrování](../../../../docs/framework/wcf/feature-details/routing-introduction.md)
