---
title: Kanonické funkce
ms.date: 03/30/2017
ms.assetid: bbcc9928-36ea-4dff-9e31-96549ffed958
ms.openlocfilehash: f8ca9e2027e82db89e91287fda02d2014d53f325
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854510"
---
# <a name="canonical-functions"></a><span data-ttu-id="8a308-102">Kanonické funkce</span><span class="sxs-lookup"><span data-stu-id="8a308-102">Canonical Functions</span></span>
<span data-ttu-id="8a308-103">Tato část popisuje kanonické funkce, které jsou podporovány všemi zprostředkovateli dat, a lze je použít všemi technologiemi pro dotazování.</span><span class="sxs-lookup"><span data-stu-id="8a308-103">This section discusses canonical functions that are supported by all data providers, and can be used by all querying technologies.</span></span> <span data-ttu-id="8a308-104">Kanonické funkce nelze od poskytovatele rozšířit.</span><span class="sxs-lookup"><span data-stu-id="8a308-104">Canonical functions cannot be extended by a provider.</span></span>  
  
 <span data-ttu-id="8a308-105">Tyto kanonické funkce budou přeloženy na odpovídající funkce zdroje dat pro poskytovatele.</span><span class="sxs-lookup"><span data-stu-id="8a308-105">These canonical functions will be translated to the corresponding data source functionality for the provider.</span></span> <span data-ttu-id="8a308-106">To umožňuje vyvolání funkcí vyjádřené ve společném formuláři napříč zdroji dat.</span><span class="sxs-lookup"><span data-stu-id="8a308-106">This allows for function invocations expressed in a common form across data sources.</span></span>  
  
 <span data-ttu-id="8a308-107">Vzhledem k tomu, že tyto kanonické funkce jsou nezávislé na zdrojích dat, argumenty a návratové typy kanonických funkcí jsou definovány v koncepčním modelu.</span><span class="sxs-lookup"><span data-stu-id="8a308-107">Because these canonical functions are independent of data sources, argument and return types of canonical functions are defined in terms of types in the conceptual model.</span></span> <span data-ttu-id="8a308-108">Některé zdroje dat však nemusí podporovat všechny typy v koncepčním modelu.</span><span class="sxs-lookup"><span data-stu-id="8a308-108">However, some data sources might not support all types in the conceptual model.</span></span>  
  
 <span data-ttu-id="8a308-109">Pokud jsou v [!INCLUDE[esql](../../../../../../includes/esql-md.md)] dotazu použity kanonické funkce, příslušná funkce bude volána ve zdroji dat.</span><span class="sxs-lookup"><span data-stu-id="8a308-109">When canonical functions are used in an [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query, the appropriate function will be called at the data source.</span></span>  
  
 <span data-ttu-id="8a308-110">Všechny kanonické funkce mají jak chování vstupu null, tak i chybové stavy, které jsou explicitně určeny.</span><span class="sxs-lookup"><span data-stu-id="8a308-110">All canonical functions have both null-input behavior and error conditions explicitly specified.</span></span> <span data-ttu-id="8a308-111">Poskytovatelé úložiště by měli dodržovat toto chování, ale Entity Framework toto chování neuplatní.</span><span class="sxs-lookup"><span data-stu-id="8a308-111">Store providers should comply with that behavior, but Entity Framework does not enforce this behavior.</span></span>  
  
 <span data-ttu-id="8a308-112">Pro scénáře LINQ dotazy na Entity Framework zahrnují mapování metod CLR na metody v podkladovém zdroji dat.</span><span class="sxs-lookup"><span data-stu-id="8a308-112">For LINQ scenarios, queries against the Entity Framework involve mapping CLR methods to methods in the underlying data source.</span></span> <span data-ttu-id="8a308-113">Metody CLR se mapují na kanonické funkce, takže konkrétní sada metod bude správně namapována, bez ohledu na zdroj dat.</span><span class="sxs-lookup"><span data-stu-id="8a308-113">The CLR methods map to canonical functions, so that a specific set of methods will correctly map, regardless of the data source.</span></span>  
  
## <a name="canonical-functions-namespace"></a><span data-ttu-id="8a308-114">Obor názvů kanonických funkcí</span><span class="sxs-lookup"><span data-stu-id="8a308-114">Canonical Functions Namespace</span></span>  
 <span data-ttu-id="8a308-115">Obor názvů pro kanonickou funkci <xref:System.Data.Metadata.Edm>je.</span><span class="sxs-lookup"><span data-stu-id="8a308-115">The namespace for canonical function is <xref:System.Data.Metadata.Edm>.</span></span> <span data-ttu-id="8a308-116"><xref:System.Data.Metadata.Edm> Obor názvů je automaticky zahrnutý ve všech dotazech.</span><span class="sxs-lookup"><span data-stu-id="8a308-116">The <xref:System.Data.Metadata.Edm> namespace is automatically included in all queries.</span></span> <span data-ttu-id="8a308-117">Pokud je však importován jiný obor názvů, který obsahuje funkci se stejným názvem jako kanonická funkce (v <xref:System.Data.Metadata.Edm> oboru názvů), je nutné zadat obor názvů.</span><span class="sxs-lookup"><span data-stu-id="8a308-117">However, if another namespace is imported that contains a function with the same name as a canonical function (in the <xref:System.Data.Metadata.Edm> namespace), you must specify the namespace.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="8a308-118">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="8a308-118">In This Section</span></span>  
 [<span data-ttu-id="8a308-119">Agregační kanonické funkce</span><span class="sxs-lookup"><span data-stu-id="8a308-119">Aggregate Canonical Functions</span></span>](aggregate-canonical-functions.md)  
 <span data-ttu-id="8a308-120">Popisuje agregační [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kanonické funkce.</span><span class="sxs-lookup"><span data-stu-id="8a308-120">Discusses aggregate [!INCLUDE[esql](../../../../../../includes/esql-md.md)] canonical functions.</span></span>  
  
 [<span data-ttu-id="8a308-121">Matematické kanonické funkce</span><span class="sxs-lookup"><span data-stu-id="8a308-121">Math Canonical Functions</span></span>](math-canonical-functions.md)  
 <span data-ttu-id="8a308-122">Popisuje matematické [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kanonické funkce.</span><span class="sxs-lookup"><span data-stu-id="8a308-122">Discusses math [!INCLUDE[esql](../../../../../../includes/esql-md.md)] canonical functions.</span></span>  
  
 [<span data-ttu-id="8a308-123">Řetězcové kanonické funkce</span><span class="sxs-lookup"><span data-stu-id="8a308-123">String Canonical Functions</span></span>](string-canonical-functions.md)  
 <span data-ttu-id="8a308-124">Popisuje řetězcové [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kanonické funkce.</span><span class="sxs-lookup"><span data-stu-id="8a308-124">Discusses string [!INCLUDE[esql](../../../../../../includes/esql-md.md)] canonical functions.</span></span>  
  
 [<span data-ttu-id="8a308-125">Kanonické funkce pro datum a čas</span><span class="sxs-lookup"><span data-stu-id="8a308-125">Date and Time Canonical Functions</span></span>](date-and-time-canonical-functions.md)  
 <span data-ttu-id="8a308-126">Popisuje kanonické funkce [!INCLUDE[esql](../../../../../../includes/esql-md.md)] data a času.</span><span class="sxs-lookup"><span data-stu-id="8a308-126">Discusses date and time [!INCLUDE[esql](../../../../../../includes/esql-md.md)] canonical functions.</span></span>  
  
 [<span data-ttu-id="8a308-127">Bitové kanonické funkce</span><span class="sxs-lookup"><span data-stu-id="8a308-127">Bitwise Canonical Functions</span></span>](bitwise-canonical-functions.md)  
 <span data-ttu-id="8a308-128">Popisuje bitové [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kanonické funkce.</span><span class="sxs-lookup"><span data-stu-id="8a308-128">Discusses bitwise [!INCLUDE[esql](../../../../../../includes/esql-md.md)] canonical functions.</span></span>  
  
 [<span data-ttu-id="8a308-129">Prostorové funkce</span><span class="sxs-lookup"><span data-stu-id="8a308-129">Spatial Functions</span></span>](spatial-functions.md)  
 <span data-ttu-id="8a308-130">Popisuje prostorové [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kanonické funkce.</span><span class="sxs-lookup"><span data-stu-id="8a308-130">Discusses Spatial [!INCLUDE[esql](../../../../../../includes/esql-md.md)] canonical functions.</span></span>  
  
 [<span data-ttu-id="8a308-131">Jiné kanonické funkce</span><span class="sxs-lookup"><span data-stu-id="8a308-131">Other Canonical Functions</span></span>](other-canonical-functions.md)  
 <span data-ttu-id="8a308-132">Popisuje funkce, které nejsou klasifikovány jako bitové, datum a čas, řetězec, matematika nebo agregace.</span><span class="sxs-lookup"><span data-stu-id="8a308-132">Discusses functions not classified as bitwise, date/time, string, math, or aggregate.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a308-133">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8a308-133">See also</span></span>

- [<span data-ttu-id="8a308-134">Přehled Entity SQL</span><span class="sxs-lookup"><span data-stu-id="8a308-134">Entity SQL Overview</span></span>](entity-sql-overview.md)
- [<span data-ttu-id="8a308-135">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="8a308-135">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="8a308-136">Konceptuální model v kanonickém formátu pro mapování funkcí SQL Serveru</span><span class="sxs-lookup"><span data-stu-id="8a308-136">Conceptual Model Canonical to SQL Server Functions Mapping</span></span>](../conceptual-model-canonical-to-sql-server-functions-mapping.md)
- [<span data-ttu-id="8a308-137">Uživatelem definované funkce</span><span class="sxs-lookup"><span data-stu-id="8a308-137">User-Defined Functions</span></span>](user-defined-functions-entity-sql.md)
