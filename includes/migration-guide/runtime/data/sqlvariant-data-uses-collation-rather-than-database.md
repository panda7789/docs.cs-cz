---
ms.openlocfilehash: e7a5a95a5d13f3396d396ad0d74a19a0efa3a967
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59235274"
---
### <a name="sqlvariant-data-uses-sqlvariant-collation-rather-than-database-collation"></a><span data-ttu-id="86f0f-101">SQL_VARIANT data používá kolaci sql_variant spíše než řazení databáze</span><span class="sxs-lookup"><span data-stu-id="86f0f-101">Sql_variant data uses sql_variant collation rather than database collation</span></span>

|   |   |
|---|---|
|<span data-ttu-id="86f0f-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="86f0f-102">Details</span></span>|<span data-ttu-id="86f0f-103"><code>sql_variant</code> použití dat <code>sql_variant</code> spíše než řazení databáze.</span><span class="sxs-lookup"><span data-stu-id="86f0f-103"><code>sql_variant</code> data uses <code>sql_variant</code> collation rather than database collation.</span></span>|
|<span data-ttu-id="86f0f-104">Doporučení</span><span class="sxs-lookup"><span data-stu-id="86f0f-104">Suggestion</span></span>|<span data-ttu-id="86f0f-105">Tato změna adresuje možné poškození dat, pokud se řazení databáze liší od <code>sql_variant</code> kolace.</span><span class="sxs-lookup"><span data-stu-id="86f0f-105">This change addresses possible data corruption if the database collation differs from the <code>sql_variant</code> collation.</span></span> <span data-ttu-id="86f0f-106">Aplikace využívající poškozená data mohou selhat.</span><span class="sxs-lookup"><span data-stu-id="86f0f-106">Applications that rely on the corrupted data may experience failure.</span></span>|
|<span data-ttu-id="86f0f-107">Rozsah</span><span class="sxs-lookup"><span data-stu-id="86f0f-107">Scope</span></span>|<span data-ttu-id="86f0f-108">Transparentní</span><span class="sxs-lookup"><span data-stu-id="86f0f-108">Transparent</span></span>|
|<span data-ttu-id="86f0f-109">Version</span><span class="sxs-lookup"><span data-stu-id="86f0f-109">Version</span></span>|<span data-ttu-id="86f0f-110">4.5</span><span class="sxs-lookup"><span data-stu-id="86f0f-110">4.5</span></span>|
|<span data-ttu-id="86f0f-111">Type</span><span class="sxs-lookup"><span data-stu-id="86f0f-111">Type</span></span>|<span data-ttu-id="86f0f-112">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="86f0f-112">Runtime</span></span>|
