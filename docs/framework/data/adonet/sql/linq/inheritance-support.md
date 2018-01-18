---
title: "Podpora dědičnosti"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 19bb2794-b4e7-402e-8307-1d1517381a08
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: e15f0194586cc8d4e069f04a95089cbef709581f
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
---
# <a name="inheritance-support"></a><span data-ttu-id="7dfb8-102">Podpora dědičnosti</span><span class="sxs-lookup"><span data-stu-id="7dfb8-102">Inheritance Support</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="7dfb8-103">podporuje *mapování jedné tabulky*.</span><span class="sxs-lookup"><span data-stu-id="7dfb8-103"> supports *single-table mapping*.</span></span> <span data-ttu-id="7dfb8-104">Hierarchie dědičnosti dokončení je jinými slovy, uložené v tabulce jedné databáze.</span><span class="sxs-lookup"><span data-stu-id="7dfb8-104">In other words, a complete inheritance hierarchy is stored in a single database table.</span></span> <span data-ttu-id="7dfb8-105">Tabulka obsahuje plochou sjednocení všechny možné datové sloupce pro celou hierarchii.</span><span class="sxs-lookup"><span data-stu-id="7dfb8-105">The table contains the flattened union of all possible data columns for the whole hierarchy.</span></span> <span data-ttu-id="7dfb8-106">(Spojení je výsledkem kombinace dvou tabulek do jedné tabulky, který má na řádky, které existovaly v některém z původní tabulky.) Každý řádek obsahuje hodnoty Null do sloupce, které se nevztahují na typ instance reprezentována řádek.</span><span class="sxs-lookup"><span data-stu-id="7dfb8-106">(A union is the result of combining two tables into one table that has the rows that were present in either of the original tables.) Each row has nulls in the columns that do not apply to the type of the instance represented by the row.</span></span>  
  
 <span data-ttu-id="7dfb8-107">Strategie mapování jedné tabulky je nejjednodušší reprezentace dědičnosti a poskytuje charakteristiky dobrý výkon pro řadu různých kategorií dotazů.</span><span class="sxs-lookup"><span data-stu-id="7dfb8-107">The single-table mapping strategy is the simplest representation of inheritance and provides good performance characteristics for many different categories of queries.</span></span>  
  
 <span data-ttu-id="7dfb8-108">K implementaci toto mapování v [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], je nutné zadat atributy a vlastností atributu na kořenová třída hierarchie dědičnosti.</span><span class="sxs-lookup"><span data-stu-id="7dfb8-108">To implement this mapping in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], you must specify the attributes and attribute properties on the root class of the inheritance hierarchy.</span></span> <span data-ttu-id="7dfb8-109">Další informace najdete v tématu [postupy: mapování hierarchie dědičnosti](../../../../../../docs/framework/data/adonet/sql/linq/how-to-map-inheritance-hierarchies.md).</span><span class="sxs-lookup"><span data-stu-id="7dfb8-109">For more information, see [How to: Map Inheritance Hierarchies](../../../../../../docs/framework/data/adonet/sql/linq/how-to-map-inheritance-hierarchies.md).</span></span>  
  
 <span data-ttu-id="7dfb8-110">Vývojáře, kteří používají [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] můžete použít také [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] k mapování hierarchie dědičnosti.</span><span class="sxs-lookup"><span data-stu-id="7dfb8-110">Developers using [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] can also use the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] to map inheritance hierarchies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7dfb8-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="7dfb8-111">See Also</span></span>  
 [<span data-ttu-id="7dfb8-112">Základní informace</span><span class="sxs-lookup"><span data-stu-id="7dfb8-112">Background Information</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
