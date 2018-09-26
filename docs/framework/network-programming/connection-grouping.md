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
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 5d7a13172c32d7ae47cbe290587ff7620e6060da
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2018
ms.locfileid: "47084738"
---
# <a name="connection-grouping"></a>Seskupení připojení
Seskupení připojení přidruží konkrétní požadavky v rámci jedné aplikace do fondu definovaná připojení. To může být požadované aplikace střední vrstvy, která se připojuje k back endového serveru jménem uživatele a používá protokol ověřování, který podporuje delegování, jako je třeba Kerberos, nebo aplikace střední vrstvy, který poskytuje svoje vlastní přihlašovací údaje, jako Následující příklad. Předpokládejme například, že uživatel, Joe, navštíví interní web, který zobrazuje své mzdové informace. Po ověření Joe, server aplikace střední vrstvy používá Michalův přihlašovací údaje pro připojení k back endového serveru načíst své mzdové informace. V dalším kroku Susan navštíví web a požádá o své mzdové informace. Vzhledem k tomu, že připojení pomocí přihlašovacích údajů Jana už vytvořil aplikace střední vrstvy, back-end server odpoví Michalův informace. Pokud ale aplikace přiřadí každého požadavku odeslaného do back-end serverů do skupiny připojení vytvořený z uživatelského jména, pak každý uživatel patří do samostatného připojení fondu a nesmí omylem sdílet ověřovací údaje s jiným uživatelem.  
  
 Na žádost o přiřazení ke skupině konkrétních připojení, je nutné přiřadit název, který <xref:System.Net.WebRequest.ConnectionGroupName%2A> vlastnictví vaší <xref:System.Net.WebRequest> před provedením požadavku.  
  
## <a name="see-also"></a>Viz také  
 [Správa připojení](../../../docs/framework/network-programming/managing-connections.md)  
 [Postupy: Přiřazení uživatelských informací pro seskupení připojení](../../../docs/framework/network-programming/how-to-assign-user-information-to-group-connections.md)
