---
ms.openlocfilehash: 4396ff43a48a23df29c5938b6bd2137d527b4ef5
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620011"
---
### <a name="change-in-behavior-in-data-definition-language-ddl-apis"></a>Změna chování v rozhraních API jazyka pro definici dat (DDL)

#### <a name="details"></a>Podrobnosti

Chování rozhraní API DDL při zadání AttachDBFilename se změnilo takto:<ul><li>Připojovací řetězce nemusí určovat hodnotu počátečního katalogu. Dřív byly potřeba AttachDBFilename i počáteční katalog.</li><li>Pokud jsou zadány jak AttachDBFilename, tak počáteční katalog a daný soubor MDF existuje, <xref:System.Data.Objects.ObjectContext.DatabaseExists%2A> vrátí metoda <code>true</code> . Dřív to vrátilo <code>false</code> .</li><li>Pokud je zadán jak AttachDBFilename, tak počáteční katalog a daný soubor MDF existuje, volání <xref:System.Data.Objects.ObjectContext.DeleteDatabase%2A> metody odstraní soubory.</li><li>Pokud <xref:System.Data.Objects.ObjectContext.DeleteDatabase%2A> je volána, když připojovací řetězec Určuje hodnotu AttachDBFilename s MDF, který neexistuje, a počáteční katalog, který neexistuje, metoda vyvolá <xref:System.InvalidOperationException> výjimku. Dřív to vyvolalo <xref:System.Data.SqlClient.SqlException> výjimku.</li></ul>

#### <a name="suggestion"></a>Návrh

Tyto změny můžete usnadnit vytvořením nástrojů a aplikací, které používají rozhraní API DDL. Tyto změny mohou ovlivnit kompatibilitu aplikací v následujících situacích:<ul><li>Uživatel zapíše kód, který provede <code>DROP DATABASE</code> příkaz přímo místo volání <xref:System.Data.Objects.ObjectContext.DeleteDatabase%2A> if <xref:System.Data.Objects.ObjectContext.DatabaseExists%2A> vrátí <code>true</code> . Tím je prolomen existující kód, pokud není databáze připojena, ale existuje soubor MDF.</li><li>Uživatel zapíše kód, který očekává, že <xref:System.Data.Objects.ObjectContext.DeleteDatabase%2A> Metoda bude vyvolávat <xref:System.Data.SqlClient.SqlException> místo, <xref:System.InvalidOperationException> když počáteční katalog a soubor MDF neexistují.</li></ul>

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   |Vedlejší|
|Verze|4.5|
|Typ|Modul runtime|
