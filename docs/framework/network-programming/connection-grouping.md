---
title: Seskupení připojení
ms.date: 03/30/2017
helpviewer_keywords:
- Internet, connections
- connections [.NET Framework], grouping
- WebRequest class, connection grouping
- network resources, connections
- connection pooling
ms.assetid: 2ec502e8-4ba0-4c22-9410-f28eaf4eee63
ms.openlocfilehash: 007366764a7b8e1208e22ef5895e6a9093b090e4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "71048648"
---
# <a name="connection-grouping"></a>Seskupení připojení
Seskupení připojení přidruží konkrétní požadavky v rámci jedné aplikace k definovanému fondu připojení. To může vyžadovat aplikace střední vrstvy, která se připojuje k serveru back-end jménem uživatele a používá ověřovací protokol, který podporuje delegování, například Kerberos, nebo aplikace střední vrstvy, která poskytuje vlastní pověření, jako v níže. Předpokládejme například, že uživatel Joe navštíví interní web, který zobrazuje jeho mzdové informace. Po ověření Joe, střední vrstvy aplikační server používá Joe pověření pro připojení k serveru back-end načíst jeho mzdové informace. Dále Susan navštíví web a požádá o informace o mzdách. Vzhledem k tomu, že aplikace střední vrstvy již navázala připojení pomocí přihlašovacích údajů Joe, server back-end odpoví s informacemi Joe. Pokud však aplikace přiřadí každý požadavek odeslaný serveru back-end skupině připojení vytvořené z uživatelského jména, pak každý uživatel patří do samostatného fondu připojení a nemůže omylem sdílet ověřovací informace s jiným uživatelem.  
  
 Chcete-li přiřadit požadavek určité skupině připojení, musíte <xref:System.Net.WebRequest.ConnectionGroupName%2A> před <xref:System.Net.WebRequest> podáním žádosti přiřadit název vlastnosti vaší vlastnosti.  
  
## <a name="see-also"></a>Viz také

- [Správa připojení](managing-connections.md)
- [Postupy: Přiřazení uživatelských informací pro seskupení připojení](how-to-assign-user-information-to-group-connections.md)
