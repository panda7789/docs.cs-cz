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
manager: markl
ms.openlocfilehash: bbf34f1e653e95ea30a3e9945fc74c99cfdc3a45
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33395044"
---
# <a name="connection-grouping"></a><span data-ttu-id="4227d-102">Seskupení připojení</span><span class="sxs-lookup"><span data-stu-id="4227d-102">Connection Grouping</span></span>
<span data-ttu-id="4227d-103">Připojení seskupení přidruží konkrétní požadavky v rámci jedné aplikace do fondu definované připojení.</span><span class="sxs-lookup"><span data-stu-id="4227d-103">Connection grouping associates specific requests within a single application to a defined connection pool.</span></span> <span data-ttu-id="4227d-104">To může být požadované aplikace střední vrstvy, která se připojuje k serveru back-end jménem uživatele a používá ověřovací protokol, který podporuje delegování, jako je třeba Kerberos, nebo aplikací střední vrstvy, který poskytuje svoje vlastní přihlašovací údaje, jako v Následující příklad.</span><span class="sxs-lookup"><span data-stu-id="4227d-104">This can be required by a middle-tier application that connects to a back-end server on behalf of a user and uses an authentication protocol that supports delegation, such as Kerberos, or by a middle-tier application that supplies its own credentials, as in the example below.</span></span> <span data-ttu-id="4227d-105">Předpokládejme například, že uživatel, Jan, navštíví interní web, který zobrazí informace o jeho mzdy.</span><span class="sxs-lookup"><span data-stu-id="4227d-105">For example, suppose a user, Joe, visits an internal Web site that displays his payroll information.</span></span> <span data-ttu-id="4227d-106">Po ověření Jan střední vrstvy aplikační server používá Michalův pověření pro připojení k back-end serverů se načíst informace o jeho mzdy.</span><span class="sxs-lookup"><span data-stu-id="4227d-106">After authenticating Joe, the middle-tier application server uses Joe's credentials to connect to the back-end server to retrieve his payroll information.</span></span> <span data-ttu-id="4227d-107">V dalším kroku Susan navštíví web a požádá o jeho mzdy informace.</span><span class="sxs-lookup"><span data-stu-id="4227d-107">Next, Susan visits the site and requests her payroll information.</span></span> <span data-ttu-id="4227d-108">Protože aplikace střední vrstvy je již k připojení pomocí přihlašovacích údajů Michalův, odpoví back-end serverů Michalův informacemi.</span><span class="sxs-lookup"><span data-stu-id="4227d-108">Because the middle-tier application has already made a connection using Joe's credentials, the back-end server responds with Joe's information.</span></span> <span data-ttu-id="4227d-109">Ale pokud je přiřazena každý požadavek odeslaný back-end serverů do skupiny připojení vytvořen z uživatelské jméno, pak každý uživatel patří do fondu samostatného připojení a nesmí omylem sdílet informace o ověřování s jiným uživatelem.</span><span class="sxs-lookup"><span data-stu-id="4227d-109">However, if the application assigns each request sent to the back-end server to a connection group formed from the user name, then each user belongs to a separate connection pool and cannot accidentally share authentication information with another user.</span></span>  
  
 <span data-ttu-id="4227d-110">Žádost o přiřadit ke skupině pro konkrétní připojení, je nutné přiřadit název, který <xref:System.Net.WebRequest.ConnectionGroupName%2A> vlastnost vaší <xref:System.Net.WebRequest> před provedením požadavku.</span><span class="sxs-lookup"><span data-stu-id="4227d-110">To assign a request to a specific connection group, you must assign a name to the <xref:System.Net.WebRequest.ConnectionGroupName%2A> property of your <xref:System.Net.WebRequest> before making the request.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4227d-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="4227d-111">See Also</span></span>  
 [<span data-ttu-id="4227d-112">Správa připojení</span><span class="sxs-lookup"><span data-stu-id="4227d-112">Managing Connections</span></span>](../../../docs/framework/network-programming/managing-connections.md)  
 [<span data-ttu-id="4227d-113">Postupy: Přiřazení uživatelských informací pro seskupení připojení</span><span class="sxs-lookup"><span data-stu-id="4227d-113">How to: Assign User Information to Group Connections</span></span>](../../../docs/framework/network-programming/how-to-assign-user-information-to-group-connections.md)
