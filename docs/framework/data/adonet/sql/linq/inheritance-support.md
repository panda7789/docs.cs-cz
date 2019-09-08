---
title: Podpora dědičnosti
ms.date: 03/30/2017
ms.assetid: 19bb2794-b4e7-402e-8307-1d1517381a08
ms.openlocfilehash: 034aa6e75ca304d98aa4d3e1f3023c1a6940b73c
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70781564"
---
# <a name="inheritance-support"></a><span data-ttu-id="820f1-102">Podpora dědičnosti</span><span class="sxs-lookup"><span data-stu-id="820f1-102">Inheritance Support</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="820f1-103">podporuje *mapování s jednou tabulkou*.</span><span class="sxs-lookup"><span data-stu-id="820f1-103">supports *single-table mapping*.</span></span> <span data-ttu-id="820f1-104">Jinými slovy, úplná Hierarchie dědičnosti je uložena v jedné tabulce databáze.</span><span class="sxs-lookup"><span data-stu-id="820f1-104">In other words, a complete inheritance hierarchy is stored in a single database table.</span></span> <span data-ttu-id="820f1-105">Tabulka obsahuje shrnuté sjednocení všech možných sloupců dat pro celou hierarchii.</span><span class="sxs-lookup"><span data-stu-id="820f1-105">The table contains the flattened union of all possible data columns for the whole hierarchy.</span></span> <span data-ttu-id="820f1-106">(Sjednocení je výsledkem kombinování dvou tabulek do jedné tabulky, která obsahuje řádky, které byly přítomny v některé z původních tabulek.) Každý řádek má hodnoty null ve sloupcích, které neplatí pro typ instance reprezentované řádkem.</span><span class="sxs-lookup"><span data-stu-id="820f1-106">(A union is the result of combining two tables into one table that has the rows that were present in either of the original tables.) Each row has nulls in the columns that do not apply to the type of the instance represented by the row.</span></span>  
  
 <span data-ttu-id="820f1-107">Strategie mapování s jednou tabulkou je nejjednodušší reprezentace dědičnosti a poskytuje dobré výkonnostní charakteristiky pro mnoho různých kategorií dotazů.</span><span class="sxs-lookup"><span data-stu-id="820f1-107">The single-table mapping strategy is the simplest representation of inheritance and provides good performance characteristics for many different categories of queries.</span></span>  
  
 <span data-ttu-id="820f1-108">Chcete-li implementovat toto [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]mapování v nástroji, je nutné zadat atributy a vlastnosti atributu pro kořenovou třídu Hierarchie dědičnosti.</span><span class="sxs-lookup"><span data-stu-id="820f1-108">To implement this mapping in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], you must specify the attributes and attribute properties on the root class of the inheritance hierarchy.</span></span> <span data-ttu-id="820f1-109">Další informace najdete v tématu [jak: Mapování hierarchií](how-to-map-inheritance-hierarchies.md)dědičnosti.</span><span class="sxs-lookup"><span data-stu-id="820f1-109">For more information, see [How to: Map Inheritance Hierarchies](how-to-map-inheritance-hierarchies.md).</span></span>  
  
 <span data-ttu-id="820f1-110">Vývojáři, kteří používají Visual Studio, mohou také použít Návrhář relací objektů k mapování hierarchií dědičnosti.</span><span class="sxs-lookup"><span data-stu-id="820f1-110">Developers using Visual Studio can also use the Object Relational Designer to map inheritance hierarchies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="820f1-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="820f1-111">See also</span></span>

- [<span data-ttu-id="820f1-112">Základní informace</span><span class="sxs-lookup"><span data-stu-id="820f1-112">Background Information</span></span>](background-information.md)
