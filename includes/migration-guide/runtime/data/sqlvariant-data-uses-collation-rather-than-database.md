---
ms.openlocfilehash: e7a5a95a5d13f3396d396ad0d74a19a0efa3a967
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59235274"
---
### <a name="sqlvariant-data-uses-sqlvariant-collation-rather-than-database-collation"></a><span data-ttu-id="41792-101">SQL_VARIANT data používá kolaci sql_variant spíše než řazení databáze</span><span class="sxs-lookup"><span data-stu-id="41792-101">Sql_variant data uses sql_variant collation rather than database collation</span></span>

|   |   |
|---|---|
|<span data-ttu-id="41792-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="41792-102">Details</span></span>|<code>sql_variant</code> <span data-ttu-id="41792-103">použití dat <code>sql_variant</code> spíše než řazení databáze.</span><span class="sxs-lookup"><span data-stu-id="41792-103">data uses <code>sql_variant</code> collation rather than database collation.</span></span>|
|<span data-ttu-id="41792-104">Doporučení</span><span class="sxs-lookup"><span data-stu-id="41792-104">Suggestion</span></span>|<span data-ttu-id="41792-105">Tato změna adresuje možné poškození dat, pokud se řazení databáze liší od <code>sql_variant</code> kolace.</span><span class="sxs-lookup"><span data-stu-id="41792-105">This change addresses possible data corruption if the database collation differs from the <code>sql_variant</code> collation.</span></span> <span data-ttu-id="41792-106">Aplikace využívající poškozená data mohou selhat.</span><span class="sxs-lookup"><span data-stu-id="41792-106">Applications that rely on the corrupted data may experience failure.</span></span>|
|<span data-ttu-id="41792-107">Rozsah</span><span class="sxs-lookup"><span data-stu-id="41792-107">Scope</span></span>|<span data-ttu-id="41792-108">Transparentní</span><span class="sxs-lookup"><span data-stu-id="41792-108">Transparent</span></span>|
|<span data-ttu-id="41792-109">Version</span><span class="sxs-lookup"><span data-stu-id="41792-109">Version</span></span>|<span data-ttu-id="41792-110">4.5</span><span class="sxs-lookup"><span data-stu-id="41792-110">4.5</span></span>|
|<span data-ttu-id="41792-111">Type</span><span class="sxs-lookup"><span data-stu-id="41792-111">Type</span></span>|<span data-ttu-id="41792-112">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="41792-112">Runtime</span></span>|
