---
title: Zabezpečení integrace CLR na SQL serveru
ms.date: 03/30/2017
ms.assetid: 489fe096-fd1d-42de-8438-bf7aed46aea2
ms.openlocfilehash: 953982045574cc62b1da46c5d763693b9d9d89ff
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43516190"
---
# <a name="clr-integration-security-in-sql-server"></a><span data-ttu-id="4eb63-102">Zabezpečení integrace CLR na SQL serveru</span><span class="sxs-lookup"><span data-stu-id="4eb63-102">CLR Integration Security in SQL Server</span></span>
<span data-ttu-id="4eb63-103">Microsoft SQL Server poskytuje integraci běžné součásti modulu runtime (CLR) jazyk rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="4eb63-103">Microsoft SQL Server provides the integration of the common language runtime (CLR) component of the .NET Framework.</span></span> <span data-ttu-id="4eb63-104">Integrace modulu CLR umožňuje psát uložené procedury, aktivační události, uživatelem definovaných typů, uživatelem definované funkce, uživatelem definovaných agregacích a datových proudů funkce vracející tabulku, pomocí libovolného jazyka, rozhraní .NET Framework, jako je například Microsoft Visual Basic .NET nebo Microsoft Visual C#.</span><span class="sxs-lookup"><span data-stu-id="4eb63-104">CLR integration allows you to write stored procedures, triggers, user-defined types, user-defined functions, user-defined aggregates, and streaming table-valued functions, using any .NET Framework language, such as Microsoft Visual Basic .NET or Microsoft Visual C#.</span></span>  
  
 <span data-ttu-id="4eb63-105">Modul CLR podporuje model zabezpečení pro spravovaný kód volá zabezpečení přístupu kódu (CAS).</span><span class="sxs-lookup"><span data-stu-id="4eb63-105">The CLR supports a security model called code access security (CAS) for managed code.</span></span> <span data-ttu-id="4eb63-106">V tomto modelu jsou udělena oprávnění pro sestavení založená na důkaz, kód v metadatech.</span><span class="sxs-lookup"><span data-stu-id="4eb63-106">In this model, permissions are granted to assemblies based on evidence supplied by the code in metadata.</span></span> <span data-ttu-id="4eb63-107">SQL Server integruje model zabezpečení založený na uživatele systému SQL Server s použitím modelu zabezpečení přístupu kódu modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="4eb63-107">SQL Server integrates the user-based security model of SQL Server with the code access-based security model of the CLR.</span></span>  
  
## <a name="external-resources"></a><span data-ttu-id="4eb63-108">Externí zdroje</span><span class="sxs-lookup"><span data-stu-id="4eb63-108">External Resources</span></span>  
 <span data-ttu-id="4eb63-109">Další informace o integraci modulu CLR SQL serveru najdete v následující prostředky.</span><span class="sxs-lookup"><span data-stu-id="4eb63-109">For more information on CLR integration with SQL Server, see the following resources.</span></span>  
  
|<span data-ttu-id="4eb63-110">Prostředek</span><span class="sxs-lookup"><span data-stu-id="4eb63-110">Resource</span></span>|<span data-ttu-id="4eb63-111">Popis</span><span class="sxs-lookup"><span data-stu-id="4eb63-111">Description</span></span>|  
|--------------|-----------------|  
|[<span data-ttu-id="4eb63-112">Zabezpečení přístupu kódu</span><span class="sxs-lookup"><span data-stu-id="4eb63-112">Code Access Security</span></span>](https://msdn.microsoft.com/library/23a20143-241d-4fe5-9d9f-3933fd594c03)|<span data-ttu-id="4eb63-113">Obsahuje témata popisující certifikační Autority v rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="4eb63-113">Contains topics describing CAS in the .NET Framework.</span></span>|  
|[<span data-ttu-id="4eb63-114">Zabezpečení integrace CLR</span><span class="sxs-lookup"><span data-stu-id="4eb63-114">CLR Integration Security</span></span>](https://go.microsoft.com/fwlink/?LinkId=59998)|<span data-ttu-id="4eb63-115">Tento článek popisuje model zabezpečení pro spravovaný kód spuštění v rámci služby SQL Server.</span><span class="sxs-lookup"><span data-stu-id="4eb63-115">Discusses the security model for managed code executing inside of SQL Server.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4eb63-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="4eb63-116">See Also</span></span>  
 [<span data-ttu-id="4eb63-117">Zabezpečení aplikací ADO.NET</span><span class="sxs-lookup"><span data-stu-id="4eb63-117">Securing ADO.NET Applications</span></span>](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 [<span data-ttu-id="4eb63-118">Scénáře zabezpečení aplikací na SQL Serveru</span><span class="sxs-lookup"><span data-stu-id="4eb63-118">Application Security Scenarios in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/application-security-scenarios-in-sql-server.md)  
 [<span data-ttu-id="4eb63-119">Integrace CLR (Common Language Runtime) na SQL Serveru</span><span class="sxs-lookup"><span data-stu-id="4eb63-119">SQL Server Common Language Runtime Integration</span></span>](../../../../../docs/framework/data/adonet/sql/sql-server-common-language-runtime-integration.md)  
 [<span data-ttu-id="4eb63-120">ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="4eb63-120">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
