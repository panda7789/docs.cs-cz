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
# <a name="connection-grouping"></a><span data-ttu-id="5cf25-102">Seskupení připojení</span><span class="sxs-lookup"><span data-stu-id="5cf25-102">Connection Grouping</span></span>
<span data-ttu-id="5cf25-103">Seskupení připojení přidružuje konkrétní požadavky v rámci jedné aplikace do definovaného fondu připojení.</span><span class="sxs-lookup"><span data-stu-id="5cf25-103">Connection grouping associates specific requests within a single application to a defined connection pool.</span></span> <span data-ttu-id="5cf25-104">To může být vyžadováno aplikací střední vrstvy, která se připojuje k back-end serveru jménem uživatele a používá ověřovací protokol, který podporuje delegování, jako je například Kerberos nebo aplikace střední vrstvy, které poskytuje vlastní přihlašovací údaje, jako je například Níže uvedený příklad.</span><span class="sxs-lookup"><span data-stu-id="5cf25-104">This can be required by a middle-tier application that connects to a back-end server on behalf of a user and uses an authentication protocol that supports delegation, such as Kerberos, or by a middle-tier application that supplies its own credentials, as in the example below.</span></span> <span data-ttu-id="5cf25-105">Předpokládejme například, že uživatel, Jana, navštíví interní web, který zobrazuje informace o mzdách.</span><span class="sxs-lookup"><span data-stu-id="5cf25-105">For example, suppose a user, Joe, visits an internal Web site that displays his payroll information.</span></span> <span data-ttu-id="5cf25-106">Po ověření Jana server aplikace střední vrstvy použije přihlašovací údaje Jana k připojení k back-end serveru, aby získal informace o mzdách.</span><span class="sxs-lookup"><span data-stu-id="5cf25-106">After authenticating Joe, the middle-tier application server uses Joe's credentials to connect to the back-end server to retrieve his payroll information.</span></span> <span data-ttu-id="5cf25-107">V dalším kroku Zuzana navštíví web a požádá o jeho mzdové údaje.</span><span class="sxs-lookup"><span data-stu-id="5cf25-107">Next, Susan visits the site and requests her payroll information.</span></span> <span data-ttu-id="5cf25-108">Vzhledem k tomu, že aplikace střední vrstvy již provedla připojení pomocí přihlašovacích údajů uživatele Jana, vrátí back-end server informace Jana.</span><span class="sxs-lookup"><span data-stu-id="5cf25-108">Because the middle-tier application has already made a connection using Joe's credentials, the back-end server responds with Joe's information.</span></span> <span data-ttu-id="5cf25-109">Pokud ale aplikace přiřadí každý požadavek odeslaný back-end serveru do skupiny připojení vytvořené z uživatelského jména, pak každý uživatel patří do samostatného fondu připojení a nemůže náhodně sdílet ověřovací informace s jiným uživatelem.</span><span class="sxs-lookup"><span data-stu-id="5cf25-109">However, if the application assigns each request sent to the back-end server to a connection group formed from the user name, then each user belongs to a separate connection pool and cannot accidentally share authentication information with another user.</span></span>  
  
 <span data-ttu-id="5cf25-110">Chcete-li přiřadit požadavek na konkrétní skupinu připojení, musíte před vytvořením žádosti přiřadit název <xref:System.Net.WebRequest.ConnectionGroupName%2A> vlastnosti svého. <xref:System.Net.WebRequest></span><span class="sxs-lookup"><span data-stu-id="5cf25-110">To assign a request to a specific connection group, you must assign a name to the <xref:System.Net.WebRequest.ConnectionGroupName%2A> property of your <xref:System.Net.WebRequest> before making the request.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5cf25-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5cf25-111">See also</span></span>

- [<span data-ttu-id="5cf25-112">Správa připojení</span><span class="sxs-lookup"><span data-stu-id="5cf25-112">Managing Connections</span></span>](managing-connections.md)
- [<span data-ttu-id="5cf25-113">Postupy: Přiřazení uživatelských informací k seskupení připojení</span><span class="sxs-lookup"><span data-stu-id="5cf25-113">How to: Assign User Information to Group Connections</span></span>](how-to-assign-user-information-to-group-connections.md)
