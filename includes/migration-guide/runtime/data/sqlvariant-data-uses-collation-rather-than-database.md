---
ms.openlocfilehash: e7a5a95a5d13f3396d396ad0d74a19a0efa3a967
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
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
