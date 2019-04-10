---
ms.openlocfilehash: e7a5a95a5d13f3396d396ad0d74a19a0efa3a967
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59235274"
---
### <a name="sqlvariant-data-uses-sqlvariant-collation-rather-than-database-collation"></a>SQL_VARIANT data používá kolaci sql_variant spíše než řazení databáze

|   |   |
|---|---|
|Podrobnosti|<code>sql_variant</code> použití dat <code>sql_variant</code> spíše než řazení databáze.|
|Doporučení|Tato změna adresuje možné poškození dat, pokud se řazení databáze liší od <code>sql_variant</code> kolace. Aplikace využívající poškozená data mohou selhat.|
|Rozsah|Transparentní|
|Version|4.5|
|Type|Modul runtime|
