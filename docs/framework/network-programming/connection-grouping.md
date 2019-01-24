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
ms.openlocfilehash: 28d8771b4535c20a2b65fc8dbbe45407eb041a34
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54658062"
---
# <a name="connection-grouping"></a><span data-ttu-id="0dbcb-102">Seskupení připojení</span><span class="sxs-lookup"><span data-stu-id="0dbcb-102">Connection Grouping</span></span>
<span data-ttu-id="0dbcb-103">Seskupení připojení přidruží konkrétní požadavky v rámci jedné aplikace do fondu definovaná připojení.</span><span class="sxs-lookup"><span data-stu-id="0dbcb-103">Connection grouping associates specific requests within a single application to a defined connection pool.</span></span> <span data-ttu-id="0dbcb-104">To může být požadované aplikace střední vrstvy, která se připojuje k back endového serveru jménem uživatele a používá protokol ověřování, který podporuje delegování, jako je třeba Kerberos, nebo aplikace střední vrstvy, který poskytuje svoje vlastní přihlašovací údaje, jako Následující příklad.</span><span class="sxs-lookup"><span data-stu-id="0dbcb-104">This can be required by a middle-tier application that connects to a back-end server on behalf of a user and uses an authentication protocol that supports delegation, such as Kerberos, or by a middle-tier application that supplies its own credentials, as in the example below.</span></span> <span data-ttu-id="0dbcb-105">Předpokládejme například, že uživatel, Joe, navštíví interní web, který zobrazuje své mzdové informace.</span><span class="sxs-lookup"><span data-stu-id="0dbcb-105">For example, suppose a user, Joe, visits an internal Web site that displays his payroll information.</span></span> <span data-ttu-id="0dbcb-106">Po ověření Joe, server aplikace střední vrstvy používá Michalův přihlašovací údaje pro připojení k back endového serveru načíst své mzdové informace.</span><span class="sxs-lookup"><span data-stu-id="0dbcb-106">After authenticating Joe, the middle-tier application server uses Joe's credentials to connect to the back-end server to retrieve his payroll information.</span></span> <span data-ttu-id="0dbcb-107">V dalším kroku Susan navštíví web a požádá o své mzdové informace.</span><span class="sxs-lookup"><span data-stu-id="0dbcb-107">Next, Susan visits the site and requests her payroll information.</span></span> <span data-ttu-id="0dbcb-108">Vzhledem k tomu, že připojení pomocí přihlašovacích údajů Jana už vytvořil aplikace střední vrstvy, back-end server odpoví Michalův informace.</span><span class="sxs-lookup"><span data-stu-id="0dbcb-108">Because the middle-tier application has already made a connection using Joe's credentials, the back-end server responds with Joe's information.</span></span> <span data-ttu-id="0dbcb-109">Pokud ale aplikace přiřadí každého požadavku odeslaného do back-end serverů do skupiny připojení vytvořený z uživatelského jména, pak každý uživatel patří do samostatného připojení fondu a nesmí omylem sdílet ověřovací údaje s jiným uživatelem.</span><span class="sxs-lookup"><span data-stu-id="0dbcb-109">However, if the application assigns each request sent to the back-end server to a connection group formed from the user name, then each user belongs to a separate connection pool and cannot accidentally share authentication information with another user.</span></span>  
  
 <span data-ttu-id="0dbcb-110">Na žádost o přiřazení ke skupině konkrétních připojení, je nutné přiřadit název, který <xref:System.Net.WebRequest.ConnectionGroupName%2A> vlastnictví vaší <xref:System.Net.WebRequest> před provedením požadavku.</span><span class="sxs-lookup"><span data-stu-id="0dbcb-110">To assign a request to a specific connection group, you must assign a name to the <xref:System.Net.WebRequest.ConnectionGroupName%2A> property of your <xref:System.Net.WebRequest> before making the request.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0dbcb-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0dbcb-111">See also</span></span>
- [<span data-ttu-id="0dbcb-112">Správa připojení</span><span class="sxs-lookup"><span data-stu-id="0dbcb-112">Managing Connections</span></span>](../../../docs/framework/network-programming/managing-connections.md)
- [<span data-ttu-id="0dbcb-113">Postupy: Přiřazení uživatelských informací pro seskupení připojení</span><span class="sxs-lookup"><span data-stu-id="0dbcb-113">How to: Assign User Information to Group Connections</span></span>](../../../docs/framework/network-programming/how-to-assign-user-information-to-group-connections.md)
