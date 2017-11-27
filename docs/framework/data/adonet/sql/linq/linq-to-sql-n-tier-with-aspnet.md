---
title: "Technologie LINQ to SQL N-vrstvá s technologií ASP.NET"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f6cc863a-d6a6-4281-ba8b-197c01cf6c6f
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 643f38c495a57dd98c3524eaf82cdbdfe42220c2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="linq-to-sql-n-tier-with-aspnet"></a><span data-ttu-id="cb341-102">Technologie LINQ to SQL N-vrstvá s technologií ASP.NET</span><span class="sxs-lookup"><span data-stu-id="cb341-102">LINQ to SQL N-Tier with ASP.NET</span></span>
<span data-ttu-id="cb341-103">V [!INCLUDE[vstecasp](../../../../../../includes/vstecasp-md.md)] aplikace, které používají [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], můžete použít <xref:System.Web.UI.WebControls.LinqDataSource> ovládacího prvku webového serveru.</span><span class="sxs-lookup"><span data-stu-id="cb341-103">In [!INCLUDE[vstecasp](../../../../../../includes/vstecasp-md.md)] applications that use [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], you use the <xref:System.Web.UI.WebControls.LinqDataSource> Web server control.</span></span> <span data-ttu-id="cb341-104">Ovládací prvek zpracovává většinu logiky, která musí mít k dotazu vůči [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], předejte data do prohlížeče, jejich načtení a odešlete ji do [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.DataContext> který pak aktualizuje databázi.</span><span class="sxs-lookup"><span data-stu-id="cb341-104">The control handles most of the logic that it must have to query against [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], pass the data to the browser, retrieve it, and submit it to the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.DataContext> which then updates the database.</span></span> <span data-ttu-id="cb341-105">Stačí pouze nakonfigurovat ovládacího prvku do kódu a ovládací prvek zpracovává všechny přenos dat mezi [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] a v prohlížeči.</span><span class="sxs-lookup"><span data-stu-id="cb341-105">You just configure the control in the markup, and the control handles all the data transfer between [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] and the browser.</span></span> <span data-ttu-id="cb341-106">Protože ovládací prvek zpracovává interakce s prezentační vrstvou a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] zpracovává komunikaci se službou datové vrstvy, váš hlavní výběr v [!INCLUDE[vstecasp](../../../../../../includes/vstecasp-md.md)] vícevrstvé aplikace se na psaní vlastní obchodní logiku.</span><span class="sxs-lookup"><span data-stu-id="cb341-106">Because the control handles the interactions with the presentation tier, and [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] handles the communication with the data tier, your main focus in [!INCLUDE[vstecasp](../../../../../../includes/vstecasp-md.md)] multitier applications is on writing your custom business logic.</span></span>  
  
 <span data-ttu-id="cb341-107">Další informace o `LINQDataSource`, najdete v části [NIB: Přehled ovládacího prvku webového serveru LinqDataSource](http://msdn.microsoft.com/en-us/104cfc3f-7385-47d3-8a51-830dfa791136).</span><span class="sxs-lookup"><span data-stu-id="cb341-107">For more information about `LINQDataSource`, see [NIB: LinqDataSource Web Server Control Overview](http://msdn.microsoft.com/en-us/104cfc3f-7385-47d3-8a51-830dfa791136).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb341-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="cb341-108">See Also</span></span>  
 [<span data-ttu-id="cb341-109">N-vrstvá a vzdálené aplikace s dotazy LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="cb341-109">N-Tier and Remote Applications with LINQ to SQL</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/n-tier-and-remote-applications-with-linq-to-sql.md)
