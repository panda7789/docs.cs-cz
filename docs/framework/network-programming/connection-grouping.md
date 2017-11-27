---
title: "Seskupení připojení"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Internet, connections
- connections [.NET Framework], grouping
- WebRequest class, connection grouping
- network resources, connections
- connection pooling
ms.assetid: 2ec502e8-4ba0-4c22-9410-f28eaf4eee63
caps.latest.revision: "7"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: b947051d809d5e8f5be3410b269c872bfc108ec8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="connection-grouping"></a>Seskupení připojení
Připojení seskupení přidruží konkrétní požadavky v rámci jedné aplikace do fondu definované připojení. To může být požadované aplikace střední vrstvy, která se připojuje k serveru back-end jménem uživatele a používá ověřovací protokol, který podporuje delegování, jako je třeba Kerberos, nebo aplikací střední vrstvy, který poskytuje svoje vlastní přihlašovací údaje, jako v Následující příklad. Předpokládejme například, že uživatel, Jan, navštíví interní web, který zobrazí informace o jeho mzdy. Po ověření Jan střední vrstvy aplikační server používá Michalův pověření pro připojení k back-end serverů se načíst informace o jeho mzdy. V dalším kroku Susan navštíví web a požádá o jeho mzdy informace. Protože aplikace střední vrstvy je již k připojení pomocí přihlašovacích údajů Michalův, odpoví back-end serverů Michalův informacemi. Ale pokud je přiřazena každý požadavek odeslaný back-end serverů do skupiny připojení vytvořen z uživatelské jméno, pak každý uživatel patří do fondu samostatného připojení a nesmí omylem sdílet informace o ověřování s jiným uživatelem.  
  
 Žádost o přiřadit ke skupině pro konkrétní připojení, je nutné přiřadit název, který <xref:System.Net.WebRequest.ConnectionGroupName%2A> vlastnost vaší <xref:System.Net.WebRequest> před provedením požadavku.  
  
## <a name="see-also"></a>Viz také  
 [Správa připojení](../../../docs/framework/network-programming/managing-connections.md)  
 [Postupy: informace o uživateli přiřadit skupiny připojení](../../../docs/framework/network-programming/how-to-assign-user-information-to-group-connections.md)
