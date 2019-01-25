---
title: System.ServiceModel.Channels.HttpChannelMessageReceiveFailed
ms.date: 03/30/2017
ms.assetid: 9eb311da-fdcc-4dd3-9d85-05b3280dfdda
ms.openlocfilehash: 22730ef8a0c0b4706f9e267fef251014a70a58fb
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54720168"
---
# <a name="systemservicemodelchannelshttpchannelmessagereceivefailed"></a>System.ServiceModel.Channels.HttpChannelMessageReceiveFailed
Příjem zprávy přes kanál protokolu HTTP se nezdařilo.  
  
## <a name="description"></a>Popis  
 Trasování může být generována jako upozornění nebo chybu. V obou případech je vygenerován trasování pro příchozí požadavek protokolu HTTP nebyla nalezena kompatibilní naslouchací proces a tato žádost HTTP se zahodí. Může k tomu dojít, protože příkaz HTTP požadavku nebyl rozpoznán jakékoli naslouchací proces protokolu HTTP, nebo protože neposlouchal žádný posluchač na adrese požadavku je určený pro. Trasování je vygenerován jako upozornění v případě v místním prostředí a za chybu, pokud služba je hostována ve službě IIS.  
  
## <a name="see-also"></a>Viz také:
- [Trasování](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [Řešení problémů s aplikací pomocí trasování](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [Správa a diagnostika](../../../../../docs/framework/wcf/diagnostics/index.md)
