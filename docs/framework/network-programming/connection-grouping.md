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
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71048648"
---
# <a name="connection-grouping"></a>Seskupení připojení
Seskupení připojení přidružuje konkrétní požadavky v rámci jedné aplikace do definovaného fondu připojení. To může být vyžadováno aplikací střední vrstvy, která se připojuje k back-end serveru jménem uživatele a používá ověřovací protokol, který podporuje delegování, jako je například Kerberos nebo aplikace střední vrstvy, které poskytuje vlastní přihlašovací údaje, jako je například Níže uvedený příklad. Předpokládejme například, že uživatel, Jana, navštíví interní web, který zobrazuje informace o mzdách. Po ověření Jana server aplikace střední vrstvy použije přihlašovací údaje Jana k připojení k back-end serveru, aby získal informace o mzdách. V dalším kroku Zuzana navštíví web a požádá o jeho mzdové údaje. Vzhledem k tomu, že aplikace střední vrstvy již provedla připojení pomocí přihlašovacích údajů uživatele Jana, vrátí back-end server informace Jana. Pokud ale aplikace přiřadí každý požadavek odeslaný back-end serveru do skupiny připojení vytvořené z uživatelského jména, pak každý uživatel patří do samostatného fondu připojení a nemůže náhodně sdílet ověřovací informace s jiným uživatelem.  
  
 Chcete-li přiřadit požadavek na konkrétní skupinu připojení, musíte před vytvořením žádosti přiřadit název <xref:System.Net.WebRequest.ConnectionGroupName%2A> vlastnosti svého. <xref:System.Net.WebRequest>  
  
## <a name="see-also"></a>Viz také:

- [Správa připojení](managing-connections.md)
- [Postupy: Přiřazení uživatelských informací k seskupení připojení](how-to-assign-user-information-to-group-connections.md)
