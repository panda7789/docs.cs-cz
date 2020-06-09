---
title: Kontrakty pro směrování
ms.date: 03/30/2017
ms.assetid: 9ceea7ae-ea19-4cf9-ba4f-d071e236546d
ms.openlocfilehash: 69dff2c82f67a16d51e11a92052c59672a054e04
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84601072"
---
# <a name="routing-contracts"></a>Kontrakty pro směrování
Kontrakty směrování definují vzory zpráv, které může služba Směrování zpracovat.  Každá kontrakta je beztypový a umožňuje službě přijímat zprávy bez znalosti schématu nebo akce zprávy. Díky tomu může směrovací služba obecně směrovat zprávy bez další konfigurace pro konkrétní směrované zdrojové zprávy.  
  
## <a name="routing-contracts"></a>Kontrakty pro směrování  
 Vzhledem k tomu, že směrovací služba akceptuje obecný objekt zprávy WCF, nejdůležitějším aspektem při výběru kontraktu je tvar kanálu, který se použije při komunikaci s klienty a službami. Služba směrování používá při zpracování zpráv symetrická čerpadla s symetrickými zprávami, takže obecně musí tvar příchozího kontraktu odpovídat tvaru odchozího kontraktu. Existují však případy, kdy může dispečer modelu služby změnit tvary, například když dispečer převede duplexní kanál do kanálu požadavku a odpovědi, nebo odebere podporu relace z kanálu, pokud není vyžadován, a není-li použit (tj. je-li **povolena vlastnost SessionMode. Allowed**převod **IInputSessionChannel** na **IInputChannel**).  
  
 Služba směrování v rámci podpory těchto zpráv zajišťuje kontrakty v <xref:System.ServiceModel.Routing> oboru názvů, který se musí použít při definování koncových bodů služby, které služba Směrování používá. Tyto kontrakty jsou bez typu, což umožňuje příjem libovolného typu nebo akce zprávy a umožňuje směrovací službě zpracovávat zprávy bez znalosti konkrétního schématu zprávy. Další informace o smlouvách používaných směrovací službou najdete v tématu [kontrakty směrování](routing-contracts.md).  
  
 Kontrakty poskytované směrovací službou jsou umístěné v <xref:System.ServiceModel.Routing> oboru názvů a jsou popsány v následující tabulce.  
  
|Kontrakt|Tvar|Obrazec kanálu|  
|--------------|-----------|-------------------|  
|<xref:System.ServiceModel.Routing.ISimplexDatagramRouter>|SessionMode = SessionMode. Allowed<br /><br /> AsyncPattern = true<br /><br /> IsOneWay = true|IInputChannel-> IOutputChannel|  
|<xref:System.ServiceModel.Routing.ISimplexSessionRouter>|SessionMode = SessionMode. Required<br /><br /> AsyncPattern = true<br /><br /> IsOneWay = true|IInputSessionChannel-> IOutputSessionChannel|  
|<xref:System.ServiceModel.Routing.IRequestReplyRouter>|SessionMode = SessionMode. Allowed<br /><br /> AsyncPattern = true|IReplyChannel-> třídu IRequestChannel|  
|<xref:System.ServiceModel.Routing.IDuplexSessionRouter>|SessionMode = SessionMode. Required<br /><br /> CallbackContract = typeof (ISimplexSession)<br /><br /> AsyncPattern = true<br /><br /> IsOneWay = true<br /><br /> TransactionFlow (TransactionFlowOption. Allowed)|IDuplexSessionChannel-> IDuplexSessionChannel|  
  
## <a name="see-also"></a>Viz také

- [Směrovací služba](routing-service.md)
- [Směrování – úvod](routing-introduction.md)
