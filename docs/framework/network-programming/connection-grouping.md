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
ms.openlocfilehash: 00ccc11919f0ccd4f9361bfd8f265dea1ad2390d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59184560"
---
# <a name="connection-grouping"></a>Seskupení připojení
Seskupení připojení přidruží konkrétní požadavky v rámci jedné aplikace do fondu definovaná připojení. To může být požadované aplikace střední vrstvy, která se připojuje k back endového serveru jménem uživatele a používá protokol ověřování, který podporuje delegování, jako je třeba Kerberos, nebo aplikace střední vrstvy, který poskytuje svoje vlastní přihlašovací údaje, jako Následující příklad. Předpokládejme například, že uživatel, Joe, navštíví interní web, který zobrazuje své mzdové informace. Po ověření Joe, server aplikace střední vrstvy používá Michalův přihlašovací údaje pro připojení k back endového serveru načíst své mzdové informace. V dalším kroku Susan navštíví web a požádá o své mzdové informace. Vzhledem k tomu, že připojení pomocí přihlašovacích údajů Jana už vytvořil aplikace střední vrstvy, back-end server odpoví Michalův informace. Pokud ale aplikace přiřadí každého požadavku odeslaného do back-end serverů do skupiny připojení vytvořený z uživatelského jména, pak každý uživatel patří do samostatného připojení fondu a nesmí omylem sdílet ověřovací údaje s jiným uživatelem.  
  
 Na žádost o přiřazení ke skupině konkrétních připojení, je nutné přiřadit název, který <xref:System.Net.WebRequest.ConnectionGroupName%2A> vlastnictví vaší <xref:System.Net.WebRequest> před provedením požadavku.  
  
## <a name="see-also"></a>Viz také:

- [Správa připojení](../../../docs/framework/network-programming/managing-connections.md)
- [Postupy: Přiřazení uživatelských informací pro seskupení připojení](../../../docs/framework/network-programming/how-to-assign-user-information-to-group-connections.md)
