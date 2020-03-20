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
# <a name="connection-grouping"></a><span data-ttu-id="c0043-102">Seskupení připojení</span><span class="sxs-lookup"><span data-stu-id="c0043-102">Connection Grouping</span></span>
<span data-ttu-id="c0043-103">Seskupení připojení přidruží konkrétní požadavky v rámci jedné aplikace k definovanému fondu připojení.</span><span class="sxs-lookup"><span data-stu-id="c0043-103">Connection grouping associates specific requests within a single application to a defined connection pool.</span></span> <span data-ttu-id="c0043-104">To může vyžadovat aplikace střední vrstvy, která se připojuje k serveru back-end jménem uživatele a používá ověřovací protokol, který podporuje delegování, například Kerberos, nebo aplikace střední vrstvy, která poskytuje vlastní pověření, jako v níže.</span><span class="sxs-lookup"><span data-stu-id="c0043-104">This can be required by a middle-tier application that connects to a back-end server on behalf of a user and uses an authentication protocol that supports delegation, such as Kerberos, or by a middle-tier application that supplies its own credentials, as in the example below.</span></span> <span data-ttu-id="c0043-105">Předpokládejme například, že uživatel Joe navštíví interní web, který zobrazuje jeho mzdové informace.</span><span class="sxs-lookup"><span data-stu-id="c0043-105">For example, suppose a user, Joe, visits an internal Web site that displays his payroll information.</span></span> <span data-ttu-id="c0043-106">Po ověření Joe, střední vrstvy aplikační server používá Joe pověření pro připojení k serveru back-end načíst jeho mzdové informace.</span><span class="sxs-lookup"><span data-stu-id="c0043-106">After authenticating Joe, the middle-tier application server uses Joe's credentials to connect to the back-end server to retrieve his payroll information.</span></span> <span data-ttu-id="c0043-107">Dále Susan navštíví web a požádá o informace o mzdách.</span><span class="sxs-lookup"><span data-stu-id="c0043-107">Next, Susan visits the site and requests her payroll information.</span></span> <span data-ttu-id="c0043-108">Vzhledem k tomu, že aplikace střední vrstvy již navázala připojení pomocí přihlašovacích údajů Joe, server back-end odpoví s informacemi Joe.</span><span class="sxs-lookup"><span data-stu-id="c0043-108">Because the middle-tier application has already made a connection using Joe's credentials, the back-end server responds with Joe's information.</span></span> <span data-ttu-id="c0043-109">Pokud však aplikace přiřadí každý požadavek odeslaný serveru back-end skupině připojení vytvořené z uživatelského jména, pak každý uživatel patří do samostatného fondu připojení a nemůže omylem sdílet ověřovací informace s jiným uživatelem.</span><span class="sxs-lookup"><span data-stu-id="c0043-109">However, if the application assigns each request sent to the back-end server to a connection group formed from the user name, then each user belongs to a separate connection pool and cannot accidentally share authentication information with another user.</span></span>  
  
 <span data-ttu-id="c0043-110">Chcete-li přiřadit požadavek určité skupině připojení, musíte <xref:System.Net.WebRequest.ConnectionGroupName%2A> před <xref:System.Net.WebRequest> podáním žádosti přiřadit název vlastnosti vaší vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="c0043-110">To assign a request to a specific connection group, you must assign a name to the <xref:System.Net.WebRequest.ConnectionGroupName%2A> property of your <xref:System.Net.WebRequest> before making the request.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0043-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="c0043-111">See also</span></span>

- [<span data-ttu-id="c0043-112">Správa připojení</span><span class="sxs-lookup"><span data-stu-id="c0043-112">Managing Connections</span></span>](managing-connections.md)
- [<span data-ttu-id="c0043-113">Postupy: Přiřazení uživatelských informací pro seskupení připojení</span><span class="sxs-lookup"><span data-stu-id="c0043-113">How to: Assign User Information to Group Connections</span></span>](how-to-assign-user-information-to-group-connections.md)
