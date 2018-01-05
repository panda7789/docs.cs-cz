---
title: "CLR Integration zabezpečení v systému SQL Server"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 489fe096-fd1d-42de-8438-bf7aed46aea2
caps.latest.revision: "5"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: aa211005f13fca2c55ff693a12b3e37629e39ad3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="clr-integration-security-in-sql-server"></a><span data-ttu-id="953c0-102">CLR Integration zabezpečení v systému SQL Server</span><span class="sxs-lookup"><span data-stu-id="953c0-102">CLR Integration Security in SQL Server</span></span>
<span data-ttu-id="953c0-103">Microsoft SQL Server poskytuje integraci součást společné language runtime (CLR) rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="953c0-103">Microsoft SQL Server provides the integration of the common language runtime (CLR) component of the .NET Framework.</span></span> <span data-ttu-id="953c0-104">Integrace modulu CLR umožňuje psát uložené procedury, triggery, uživatelem definované typy, uživatelem definované funkce, uživatelem definovaných agregacích a streamování funkce vracející tabulku, pomocí žádný jazyk rozhraní .NET Framework, jako je například Microsoft Visual Basic .NET nebo Microsoft Visual C#.</span><span class="sxs-lookup"><span data-stu-id="953c0-104">CLR integration allows you to write stored procedures, triggers, user-defined types, user-defined functions, user-defined aggregates, and streaming table-valued functions, using any .NET Framework language, such as Microsoft Visual Basic .NET or Microsoft Visual C#.</span></span>  
  
 <span data-ttu-id="953c0-105">Modul CLR podporuje model zabezpečení pro spravovaný kód volat zabezpečení přístupu kódu (CAS).</span><span class="sxs-lookup"><span data-stu-id="953c0-105">The CLR supports a security model called code access security (CAS) for managed code.</span></span> <span data-ttu-id="953c0-106">V tomto modelu jsou udělena oprávnění pro sestavení založená na důkaz, kód v metadatech.</span><span class="sxs-lookup"><span data-stu-id="953c0-106">In this model, permissions are granted to assemblies based on evidence supplied by the code in metadata.</span></span> <span data-ttu-id="953c0-107">SQL Server integruje model zabezpečení založený na uživatele systému SQL Server s modelem zabezpečení přístupu kódu modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="953c0-107">SQL Server integrates the user-based security model of SQL Server with the code access-based security model of the CLR.</span></span>  
  
## <a name="external-resources"></a><span data-ttu-id="953c0-108">Externí zdroje</span><span class="sxs-lookup"><span data-stu-id="953c0-108">External Resources</span></span>  
 <span data-ttu-id="953c0-109">Další informace o integraci modulu CLR s SQL serverem najdete v následujících zdrojích informací.</span><span class="sxs-lookup"><span data-stu-id="953c0-109">For more information on CLR integration with SQL Server, see the following resources.</span></span>  
  
|<span data-ttu-id="953c0-110">Prostředek</span><span class="sxs-lookup"><span data-stu-id="953c0-110">Resource</span></span>|<span data-ttu-id="953c0-111">Popis</span><span class="sxs-lookup"><span data-stu-id="953c0-111">Description</span></span>|  
|--------------|-----------------|  
|[<span data-ttu-id="953c0-112">Zabezpečení přístupu kódu</span><span class="sxs-lookup"><span data-stu-id="953c0-112">Code Access Security</span></span>](http://msdn.microsoft.com/en-us/23a20143-241d-4fe5-9d9f-3933fd594c03)|<span data-ttu-id="953c0-113">Obsahuje témata s popisem certifikační Autority v rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="953c0-113">Contains topics describing CAS in the .NET Framework.</span></span>|  
|[<span data-ttu-id="953c0-114">Zabezpečení integrace modulu CLR</span><span class="sxs-lookup"><span data-stu-id="953c0-114">CLR Integration Security</span></span>](http://go.microsoft.com/fwlink/?LinkId=59998)|<span data-ttu-id="953c0-115">Popisuje model zabezpečení pro spravovaný kód provádění v systému SQL Server.</span><span class="sxs-lookup"><span data-stu-id="953c0-115">Discusses the security model for managed code executing inside of SQL Server.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="953c0-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="953c0-116">See Also</span></span>  
 [<span data-ttu-id="953c0-117">Zabezpečení aplikací ADO.NET</span><span class="sxs-lookup"><span data-stu-id="953c0-117">Securing ADO.NET Applications</span></span>](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 [<span data-ttu-id="953c0-118">Scénáře zabezpečení aplikací na SQL Serveru</span><span class="sxs-lookup"><span data-stu-id="953c0-118">Application Security Scenarios in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/application-security-scenarios-in-sql-server.md)  
 [<span data-ttu-id="953c0-119">Integrace CLR (Common Language Runtime) na SQL Serveru</span><span class="sxs-lookup"><span data-stu-id="953c0-119">SQL Server Common Language Runtime Integration</span></span>](../../../../../docs/framework/data/adonet/sql/sql-server-common-language-runtime-integration.md)  
 [<span data-ttu-id="953c0-120">ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady</span><span class="sxs-lookup"><span data-stu-id="953c0-120">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
