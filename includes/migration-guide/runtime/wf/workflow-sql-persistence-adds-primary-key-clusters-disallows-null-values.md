---
ms.openlocfilehash: 566a3e0455b30e901b09be88b4256ffe67bdc2b5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "67802511"
---
### <a name="workflow-sql-persistence-adds-primary-key-clusters-and-disallows-null-values-in-some-columns"></a>Trvalosti SQL pracovního postupu přidá clustery primárního klíče a v některých sloupcích zakáže hodnoty null.

|   |   |
|---|---|
|Podrobnosti|Počínaje rozhraním .NET Framework 4.7 používají tabulky vytvořené pro úložiště instancí pracovního postupu SQL (SWIS) skriptem SqlWorkflowInstanceStoreSchema.sql primární klíče. Z tohoto důvodu identity <code>null</code> nepodporují hodnoty. Provoz SWIS není touto změnou ovlivněn. Aktualizace byly provedeny pro podporu transakční replikace serveru SQL Server.|
|Návrh|Aby bylo možné tuto změnu provést, musí být soubor SQL SqlWorkflowInstanceStoreSchemaUpgrade.sql použit pro existující instalace. Nové instalace databáze budou mít automaticky změnu.|
|Rozsah|Edge|
|Version|4.7|
|Typ|Modul runtime|
