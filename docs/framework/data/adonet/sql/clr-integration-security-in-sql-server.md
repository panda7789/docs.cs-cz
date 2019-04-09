---
title: Zabezpečení integrace CLR na SQL Serveru
ms.date: 03/30/2017
ms.assetid: 489fe096-fd1d-42de-8438-bf7aed46aea2
ms.openlocfilehash: 946401211d515df9ba5b9e38d7cfd10730973b64
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59165812"
---
# <a name="clr-integration-security-in-sql-server"></a><span data-ttu-id="c2be2-102">Zabezpečení integrace CLR na SQL Serveru</span><span class="sxs-lookup"><span data-stu-id="c2be2-102">CLR Integration Security in SQL Server</span></span>
<span data-ttu-id="c2be2-103">Microsoft SQL Server poskytuje integraci běžné součásti modulu runtime (CLR) jazyk rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c2be2-103">Microsoft SQL Server provides the integration of the common language runtime (CLR) component of the .NET Framework.</span></span> <span data-ttu-id="c2be2-104">Integrace modulu CLR umožňuje psát uložené procedury, aktivační události, uživatelem definovaných typů, uživatelem definované funkce, uživatelem definovaných agregacích a datových proudů funkce vracející tabulku, pomocí libovolného jazyka, rozhraní .NET Framework, jako je například Microsoft Visual Basic .NET nebo Microsoft Visual C#.</span><span class="sxs-lookup"><span data-stu-id="c2be2-104">CLR integration allows you to write stored procedures, triggers, user-defined types, user-defined functions, user-defined aggregates, and streaming table-valued functions, using any .NET Framework language, such as Microsoft Visual Basic .NET or Microsoft Visual C#.</span></span>  
  
 <span data-ttu-id="c2be2-105">Modul CLR podporuje model zabezpečení pro spravovaný kód volá zabezpečení přístupu kódu (CAS).</span><span class="sxs-lookup"><span data-stu-id="c2be2-105">The CLR supports a security model called code access security (CAS) for managed code.</span></span> <span data-ttu-id="c2be2-106">V tomto modelu jsou udělena oprávnění pro sestavení založená na důkaz, kód v metadatech.</span><span class="sxs-lookup"><span data-stu-id="c2be2-106">In this model, permissions are granted to assemblies based on evidence supplied by the code in metadata.</span></span> <span data-ttu-id="c2be2-107">SQL Server integruje model zabezpečení založený na uživatele systému SQL Server s použitím modelu zabezpečení přístupu kódu modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="c2be2-107">SQL Server integrates the user-based security model of SQL Server with the code access-based security model of the CLR.</span></span>  
  
## <a name="external-resources"></a><span data-ttu-id="c2be2-108">Externí zdroje</span><span class="sxs-lookup"><span data-stu-id="c2be2-108">External Resources</span></span>  
 <span data-ttu-id="c2be2-109">Další informace o integraci modulu CLR SQL serveru najdete v následující prostředky.</span><span class="sxs-lookup"><span data-stu-id="c2be2-109">For more information on CLR integration with SQL Server, see the following resources.</span></span>  
  
|<span data-ttu-id="c2be2-110">Prostředek</span><span class="sxs-lookup"><span data-stu-id="c2be2-110">Resource</span></span>|<span data-ttu-id="c2be2-111">Popis</span><span class="sxs-lookup"><span data-stu-id="c2be2-111">Description</span></span>|  
|--------------|-----------------|  
|[<span data-ttu-id="c2be2-112">Zabezpečení přístupu kódu</span><span class="sxs-lookup"><span data-stu-id="c2be2-112">Code Access Security</span></span>](../../../../../docs/framework/misc/code-access-security.md)|<span data-ttu-id="c2be2-113">Obsahuje témata popisující certifikační Autority v rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c2be2-113">Contains topics describing CAS in the .NET Framework.</span></span>|  
|[<span data-ttu-id="c2be2-114">Zabezpečení integrace CLR</span><span class="sxs-lookup"><span data-stu-id="c2be2-114">CLR Integration Security</span></span>](/sql/relational-databases/clr-integration/security/clr-integration-security)|<span data-ttu-id="c2be2-115">Tento článek popisuje model zabezpečení pro spravovaný kód spuštění v rámci služby SQL Server.</span><span class="sxs-lookup"><span data-stu-id="c2be2-115">Discusses the security model for managed code executing inside of SQL Server.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c2be2-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c2be2-116">See also</span></span>

- [<span data-ttu-id="c2be2-117">Zabezpečení aplikací ADO.NET</span><span class="sxs-lookup"><span data-stu-id="c2be2-117">Securing ADO.NET Applications</span></span>](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)
- [<span data-ttu-id="c2be2-118">Scénáře zabezpečení aplikací na SQL Serveru</span><span class="sxs-lookup"><span data-stu-id="c2be2-118">Application Security Scenarios in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/application-security-scenarios-in-sql-server.md)
- [<span data-ttu-id="c2be2-119">Integrace CLR (Common Language Runtime) na SQL Serveru</span><span class="sxs-lookup"><span data-stu-id="c2be2-119">SQL Server Common Language Runtime Integration</span></span>](../../../../../docs/framework/data/adonet/sql/sql-server-common-language-runtime-integration.md)
- [<span data-ttu-id="c2be2-120">Přehled ADO.NET</span><span class="sxs-lookup"><span data-stu-id="c2be2-120">ADO.NET Overview</span></span>](../../../../../docs/framework/data/adonet/ado-net-overview.md)
