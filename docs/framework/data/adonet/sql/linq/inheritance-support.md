---
title: Podpora dědičnosti
ms.date: 03/30/2017
ms.assetid: 19bb2794-b4e7-402e-8307-1d1517381a08
ms.openlocfilehash: 668f4f1dd284550e644ce6b8a4491ca47105575e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59230912"
---
# <a name="inheritance-support"></a><span data-ttu-id="4d7bb-102">Podpora dědičnosti</span><span class="sxs-lookup"><span data-stu-id="4d7bb-102">Inheritance Support</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="4d7bb-103">podporuje *jedné tabulky mapování*.</span><span class="sxs-lookup"><span data-stu-id="4d7bb-103">supports *single-table mapping*.</span></span> <span data-ttu-id="4d7bb-104">Jinými slovy hierarchie dědičnosti dokončete je uložena v tabulce izolované databáze.</span><span class="sxs-lookup"><span data-stu-id="4d7bb-104">In other words, a complete inheritance hierarchy is stored in a single database table.</span></span> <span data-ttu-id="4d7bb-105">Tabulka obsahuje sloučené sjednocení všechny možné datové sloupce pro celou hierarchii.</span><span class="sxs-lookup"><span data-stu-id="4d7bb-105">The table contains the flattened union of all possible data columns for the whole hierarchy.</span></span> <span data-ttu-id="4d7bb-106">(Sjednocení je výsledkem kombinace dvou tabulek do jedné tabulky, který má řádky, které byly k dispozici v některém z původní tabulky.) Každý řádek obsahuje hodnoty Null do sloupců, které se nevztahují na typ instance reprezentována řádku.</span><span class="sxs-lookup"><span data-stu-id="4d7bb-106">(A union is the result of combining two tables into one table that has the rows that were present in either of the original tables.) Each row has nulls in the columns that do not apply to the type of the instance represented by the row.</span></span>  
  
 <span data-ttu-id="4d7bb-107">Strategie jedné tabulky mapování je nejjednodušší reprezentace dědění a poskytuje dobré výkonové charakteristiky pro mnoho různých kategorií dotazů.</span><span class="sxs-lookup"><span data-stu-id="4d7bb-107">The single-table mapping strategy is the simplest representation of inheritance and provides good performance characteristics for many different categories of queries.</span></span>  
  
 <span data-ttu-id="4d7bb-108">Pro toto mapování v implementaci [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], je nutné zadat atributy a atribut vlastnosti ve třídě kořenové hierarchii dědičnosti.</span><span class="sxs-lookup"><span data-stu-id="4d7bb-108">To implement this mapping in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], you must specify the attributes and attribute properties on the root class of the inheritance hierarchy.</span></span> <span data-ttu-id="4d7bb-109">Další informace najdete v tématu [jak: Mapování hierarchií dědičnosti](../../../../../../docs/framework/data/adonet/sql/linq/how-to-map-inheritance-hierarchies.md).</span><span class="sxs-lookup"><span data-stu-id="4d7bb-109">For more information, see [How to: Map Inheritance Hierarchies](../../../../../../docs/framework/data/adonet/sql/linq/how-to-map-inheritance-hierarchies.md).</span></span>  
  
 <span data-ttu-id="4d7bb-110">Vývojáři, kteří používají Visual Studio můžete také použít [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] mapování hierarchií dědičnosti.</span><span class="sxs-lookup"><span data-stu-id="4d7bb-110">Developers using Visual Studio can also use the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] to map inheritance hierarchies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d7bb-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4d7bb-111">See also</span></span>

- [<span data-ttu-id="4d7bb-112">Základní informace</span><span class="sxs-lookup"><span data-stu-id="4d7bb-112">Background Information</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
