---
ms.openlocfilehash: 1f06a185939c40274adad1ceac6990719069167a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59235325"
---
### <a name="change-in-behavior-in-data-definition-language-ddl-apis"></a>Změna chování v definici jazyka DDL (Data) rozhraní API

|   |   |
|---|---|
|Podrobnosti|Chování rozhraní API DDL při AttachDBFilename změněno následovně:<ul><li>Připojovací řetězce nemusí určovat hodnotu počáteční katalog. Dříve byly zapotřebí AttachDBFilename a počáteční katalog.</li><li>Pokud AttachDBFilename a Initial Catalog určeny a daný soubor MDF existuje, <xref:System.Data.Objects.ObjectContext.DatabaseExists%2A> vrátí metoda <code>true</code>. Dříve byl vrácen <code>false</code>.</li><li>Pokud je určen jak AttachDBFilename, část Initial Catalog a daný soubor MDF existuje, volání <xref:System.Data.Objects.ObjectContext.DeleteDatabase%2A> metoda odstraní soubory.</li><li>Pokud <xref:System.Data.Objects.ObjectContext.DeleteDatabase%2A> se volá, když připojovací řetězec Určuje AttachDBFilename hodnotu s MDF, který neexistuje a počáteční katalog, který neexistuje, metoda vyvolá <xref:System.InvalidOperationException> výjimky. Dříve došlo <xref:System.Data.SqlClient.SqlException> výjimky.</li></ul>|
|Doporučení|Tyto změny můžete usnadnit vytvořením nástrojů a aplikací, které používají rozhraní API DDL. Tyto změny mohou ovlivnit kompatibilitu aplikací v následujících situacích:<ul><li>Uživatel zapíše kód, který se spustí <code>DROP DATABASE</code> příkaz přímo, bez volání <xref:System.Data.Objects.ObjectContext.DeleteDatabase%2A> Pokud <xref:System.Data.Objects.ObjectContext.DatabaseExists%2A> vrátí <code>true</code>. Tím je prolomen existující kód, pokud není databáze připojena, ale existuje soubor MDF.</li><li>Uživatel zapíše kód, který očekává, že <xref:System.Data.Objects.ObjectContext.DeleteDatabase%2A> metoda k vyvolání <xref:System.Data.SqlClient.SqlException> spíše než výjimku <xref:System.InvalidOperationException> při počáteční katalog a MDF soubor neexistují.</li></ul>|
|Rozsah|Vedlejší|
|Version|4.5|
|Type|Modul runtime|
