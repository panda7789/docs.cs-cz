---
title: System.ServiceModel.Channels.HttpChannelMessageReceiveFailed
ms.date: 03/30/2017
ms.assetid: 9eb311da-fdcc-4dd3-9d85-05b3280dfdda
ms.openlocfilehash: e11b376924ee74e5d0d67da0cac59af41655dc44
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84594072"
---
# <a name="systemservicemodelchannelshttpchannelmessagereceivefailed"></a>System.ServiceModel.Channels.HttpChannelMessageReceiveFailed
Nepodařilo se přijmout zprávu přes kanál HTTP.  
  
## <a name="description"></a>Popis  
 Toto trasování je možné vygenerovat jako upozornění nebo chybu. V obou případech se trasování vygeneruje, když se pro příchozí požadavek HTTP nenajde kompatibilní naslouchací proces a požadavek HTTP se zahodí. Důvodem může být to, že příkaz HTTP požadavku nebyl rozpoznán jakýmkoli naslouchacím rozhraním protokolu HTTP, nebo protože na adrese, pro kterou byl požadavek cílen, nebyl naslouchá žádný naslouchací proces. Trasování je vygenerováno jako upozornění v případě místního hostitele a jako chyba, pokud je služba hostována službou IIS.  
  
## <a name="see-also"></a>Viz také

- [Trasování](index.md)
- [Řešení potíží s aplikací pomocí trasování](using-tracing-to-troubleshoot-your-application.md)
- [Správa a diagnostika](../index.md)
