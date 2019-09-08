---
title: Zabezpečení integrace CLR na SQL Serveru
ms.date: 03/30/2017
ms.assetid: 489fe096-fd1d-42de-8438-bf7aed46aea2
ms.openlocfilehash: 4756d13ff52a4c55b48c3ea56d26111029c8a7e4
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70794570"
---
# <a name="clr-integration-security-in-sql-server"></a><span data-ttu-id="5bf59-102">Zabezpečení integrace CLR na SQL Serveru</span><span class="sxs-lookup"><span data-stu-id="5bf59-102">CLR Integration Security in SQL Server</span></span>
<span data-ttu-id="5bf59-103">Microsoft SQL Server poskytuje integraci komponenty modulu CLR (Common Language Runtime) .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="5bf59-103">Microsoft SQL Server provides the integration of the common language runtime (CLR) component of the .NET Framework.</span></span> <span data-ttu-id="5bf59-104">Integrace CLR umožňuje psát uložené procedury, triggery, uživatelsky definované typy, uživatelsky definované funkce, uživatelsky definované agregace a streamovat funkce vracející tabulku pomocí libovolného .NET Framework jazyka, jako je Microsoft Visual Basic .NET nebo Microsoft. Vizuál C#.</span><span class="sxs-lookup"><span data-stu-id="5bf59-104">CLR integration allows you to write stored procedures, triggers, user-defined types, user-defined functions, user-defined aggregates, and streaming table-valued functions, using any .NET Framework language, such as Microsoft Visual Basic .NET or Microsoft Visual C#.</span></span>  
  
 <span data-ttu-id="5bf59-105">CLR podporuje model zabezpečení, který se nazývá zabezpečení přístupu kódu (CAS) pro spravovaný kód.</span><span class="sxs-lookup"><span data-stu-id="5bf59-105">The CLR supports a security model called code access security (CAS) for managed code.</span></span> <span data-ttu-id="5bf59-106">V tomto modelu jsou oprávnění udělena sestavením na základě legitimace poskytnuté kódem v metadatech.</span><span class="sxs-lookup"><span data-stu-id="5bf59-106">In this model, permissions are granted to assemblies based on evidence supplied by the code in metadata.</span></span> <span data-ttu-id="5bf59-107">SQL Server integruje model zabezpečení založený na uživatelích SQL Server s modelem zabezpečení založeném na přístupu kódu CLR.</span><span class="sxs-lookup"><span data-stu-id="5bf59-107">SQL Server integrates the user-based security model of SQL Server with the code access-based security model of the CLR.</span></span>  
  
## <a name="external-resources"></a><span data-ttu-id="5bf59-108">Externí zdroje</span><span class="sxs-lookup"><span data-stu-id="5bf59-108">External Resources</span></span>  
 <span data-ttu-id="5bf59-109">Další informace o integraci modulu CLR s SQL Server naleznete v následujících zdrojích informací.</span><span class="sxs-lookup"><span data-stu-id="5bf59-109">For more information on CLR integration with SQL Server, see the following resources.</span></span>  
  
|<span data-ttu-id="5bf59-110">Resource</span><span class="sxs-lookup"><span data-stu-id="5bf59-110">Resource</span></span>|<span data-ttu-id="5bf59-111">Popis</span><span class="sxs-lookup"><span data-stu-id="5bf59-111">Description</span></span>|  
|--------------|-----------------|  
|[<span data-ttu-id="5bf59-112">Zabezpečení přístupu kódu</span><span class="sxs-lookup"><span data-stu-id="5bf59-112">Code Access Security</span></span>](../../../misc/code-access-security.md)|<span data-ttu-id="5bf59-113">Obsahuje témata popisující certifikační autority v .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="5bf59-113">Contains topics describing CAS in the .NET Framework.</span></span>|  
|[<span data-ttu-id="5bf59-114">Zabezpečení integrace CLR</span><span class="sxs-lookup"><span data-stu-id="5bf59-114">CLR Integration Security</span></span>](/sql/relational-databases/clr-integration/security/clr-integration-security)|<span data-ttu-id="5bf59-115">Popisuje model zabezpečení pro spravovaný kód spouštěný uvnitř SQL Server.</span><span class="sxs-lookup"><span data-stu-id="5bf59-115">Discusses the security model for managed code executing inside of SQL Server.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5bf59-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5bf59-116">See also</span></span>

- [<span data-ttu-id="5bf59-117">Zabezpečení aplikací ADO.NET</span><span class="sxs-lookup"><span data-stu-id="5bf59-117">Securing ADO.NET Applications</span></span>](../securing-ado-net-applications.md)
- [<span data-ttu-id="5bf59-118">Scénáře zabezpečení aplikací na SQL Serveru</span><span class="sxs-lookup"><span data-stu-id="5bf59-118">Application Security Scenarios in SQL Server</span></span>](application-security-scenarios-in-sql-server.md)
- [<span data-ttu-id="5bf59-119">Integrace CLR (Common Language Runtime) na SQL Serveru</span><span class="sxs-lookup"><span data-stu-id="5bf59-119">SQL Server Common Language Runtime Integration</span></span>](sql-server-common-language-runtime-integration.md)
- [<span data-ttu-id="5bf59-120">Přehled ADO.NET</span><span class="sxs-lookup"><span data-stu-id="5bf59-120">ADO.NET Overview</span></span>](../ado-net-overview.md)
